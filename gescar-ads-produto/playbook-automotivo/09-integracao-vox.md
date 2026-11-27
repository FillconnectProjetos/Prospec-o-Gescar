# 09 · Integração com a Vox (atendimento no WhatsApp)

Base: documento técnico da Vox de 27/11/2026. A Vox é o CRM com atendente de IA da Fillconnect que atende o WhatsApp oficial de cada loja, qualifica, marca visita ou test drive e passa o cliente ao vendedor. Para lojas com Vox, o Gescar ADS **compra a conversa** e a Vox **atende**.

## Divisão de papéis

| Quem | Faz | Não faz |
| --- | --- | --- |
| Gescar ADS | Cria e ajusta campanhas clique para WhatsApp; guarda qual anúncio é de qual carro; decide verba pelo custo por visita | Não fala com o cliente final |
| Vox | Atende em segundos; grava `ctwa_clid` e `ad_id`; move etapas; registra se o cliente veio ou faltou; devolve eventos à Meta | Não cria nem muda anúncio; não simula parcela; não negocia preço |

## Canal

- Loja com Vox ligada ao número oficial: **clique para WhatsApp é o canal padrão.** Formulário instantâneo fica para quem não tem Vox.
- Mensagem pré-preenchida com o nome do carro, ex.: "Olá, tenho interesse no Hilux SRV 2021". A Vox casa o carro pelo texto do anúncio e pela mensagem.
- Código do carro na mensagem (rota C do arquivo 05) deixa de ser necessário: o `ctwa_clid` e o `ad_id` fazem a atribuição.

## Ligação anúncio → carro

A Vox não liga o `ad_id` ao veículo do Gescar. **O Gescar ADS resolve isso do próprio lado:** ao criar o anúncio, grava `ad_id → vehicle_id` em `ads_campanhas`. Com o `ad_id` que a Vox guarda em cada contato, o Gescar ADS sabe de qual carro veio cada conversa.

## Funil da Vox → decisão do agente

| Sinal da Vox | Origem | Uso no Gescar ADS |
| --- | --- | --- |
| Primeira mensagem vinda de anúncio | `lead.created` + `contacts.source_metadata` | Contato (base do custo por contato) |
| Agendado | `lead.stage_changed` para Agendado, `appointment.created` | Custo por agendamento |
| Cliente veio | `appointment.completed` | **Custo por visita: métrica principal de decisão** |
| Cliente faltou | `appointment.no_show` | Qualidade do público ou da conversa |
| Vendeu | `lead.won` | Venda atribuída ao anúncio |
| Perdido, com motivo | `lead.lost` | "Preço fora da expectativa" repetido num carro = problema de preço, não de anúncio |

**Teto de custo por visita** = custo máximo por venda × taxa de visita para venda (arquivo 06). Sem histórico, usar 20% **[HIPÓTESE]**.

## Eventos devolvidos à Meta (API de Conversões, mensagens)

Um único emissor: **a Vox envia**, porque guarda o `ctwa_clid` e já tem o motor pronto (`action_source = business_messaging`). O Gescar ADS não envia eventos de lojas com Vox, para não duplicar.

| Etapa | Evento | Observação |
| --- | --- | --- |
| Primeira mensagem de anúncio | `LeadSubmitted` | Já existe no motor |
| Agendado | `QualifiedLead` | Já existe no motor |
| Vendeu | `Purchase`, com valor da venda | **Não existe hoje: criar** |

Não usar `AddToCart`, `InitiateCheckout` ou `ViewContent` para etapas de revenda: confunde a leitura e não ajuda a Meta.

## Pré-requisitos antes de ligar

1. App "Vox Fillconnect" aprovado pela Meta e número real da loja conectado. Sem isso não há anúncio clique para WhatsApp atendido pela Vox.
2. Base legal para enviar eventos à Meta decidida com o advogado (legítimo interesse ou consentimento) e aviso de privacidade na primeira resposta. **[CONFIRMAR]**
3. Token de integração da Vox para o Gescar ADS (papel leitura) e webhooks `lead.created`, `lead.stage_changed`, `lead.won`, `lead.lost`, `appointment.completed`, `appointment.no_show` apontando para o Gescar ADS.
4. Rota de leitura de leads por `ad_id` com token (hoje `GET /api/v1/leads` só aceita sessão). Usar o MCP da Vox até lá, e para conferência diária.
5. Evento `Purchase` criado no motor da Vox.

## O que o agente diz ao lojista

O resumo semanal ganha as visitas:

> Nos últimos 7 dias: R$ 312 investidos, 18 conversas, 5 agendamentos, 3 visitas, 1 venda.
