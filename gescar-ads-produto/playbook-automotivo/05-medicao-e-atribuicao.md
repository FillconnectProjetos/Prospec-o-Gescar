# 05 · Medição e atribuição

Sem saber quais leads viraram test drive e venda, o agente otimiza para formulário preenchido, e formulário preenchido não paga a conta. Esse é o diferencial do Gescar: o CRM sabe o que virou venda.

## Funil padrão

| Etapa no CRM do Gescar | Evento enviado à Meta | Quem marca |
| --- | --- | --- |
| Lead | `Lead` | Automático (formulário ou WhatsApp) |
| Lead qualificado | `QualifiedLead` **[CONFIRMAR nome exato do evento por rota]** | Vendedor |
| Test drive | Evento personalizado `TestDrive` | Vendedor |
| Proposta enviada | Evento personalizado `PropostaEnviada` | Vendedor |
| Venda realizada | `Purchase`, com valor da venda | Vendedor ou baixa no estoque |

Regras técnicas (docs 03 e 04 da biblioteca): `event_time` até 7 dias atrás; `event_id` único por lead e etapa; telefone e e-mail com hash SHA-256; só de leads com base legal definida (doc 13).

## Rotas de atribuição, da melhor para a mais simples

| Rota | Como liga o lead ao anúncio | Quando usar |
| --- | --- | --- |
| **A. Formulário instantâneo** (padrão do piloto) | O lead chega com o ID do lead da Meta, que volta nos eventos da CRM | Sempre que possível |
| **B. WhatsApp com Cloud API** | O `ctwa_clid` vem no webhook da primeira mensagem e é guardado na ficha (doc 04) | Loja com número na WhatsApp Cloud API |
| **C. WhatsApp com código na mensagem** | A mensagem pré-preenchida leva o código do veículo e da campanha (ex.: "Olá! Quero saber do Corolla #C120"). O vendedor ou o Gescar registra o código no lead | Loja que usa o WhatsApp Business do celular. A Meta mede só "conversa iniciada", mas o Gescar sabe qual anúncio gerou a venda |

Na rota C, os eventos de funil não voltam para a Meta otimizar; servem para o agente e o lojista decidirem.

**Loja com Vox:** a rota B é o padrão. A Vox usa a WhatsApp Cloud API direto da Meta, guarda `ctwa_clid` e `ad_id` e é a única que envia eventos à Meta. Detalhes no arquivo 09. Sem Vox, a rota A continua sendo o padrão.

**Otimização por lead qualificado:** a Meta só otimiza por etapa do CRM (Conversion Leads) a partir de cerca de 200 leads por mês por loja. Abaixo disso, os eventos servem para medir e para o agente decidir, e o Gescar ADS não promete essa otimização.

## O que o agente faz com a qualidade da medição

| Situação | Comportamento |
| --- | --- |
| Menos de 50% dos leads da semana com etapa preenchida no CRM | Avisa o lojista que está decidindo com pouca informação e pede para o time marcar as etapas |
| Nenhum test drive registrado em 14 dias com leads entrando | Pergunta se os test drives estão sendo marcados no Gescar antes de concluir que a campanha está ruim |
| Evento de conversão com erro no envio | Registra, avisa a Fillconnect durante o piloto, não muda verba até resolver |

## Resumo semanal para o lojista

Uma linha, sempre no mesmo formato:

> Nos últimos 7 dias: R$ 312 investidos, 18 contatos, 2 test drives, 1 venda.

Se a venda não puder ser ligada a um anúncio, dizer "1 venda de cliente que veio do anúncio" só quando a atribuição existir. Caso contrário, não contar.
