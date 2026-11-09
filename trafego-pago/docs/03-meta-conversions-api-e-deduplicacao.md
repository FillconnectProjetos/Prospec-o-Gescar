# 03 · Meta: Conversions API e deduplicação com o Pixel

| Fonte oficial | Lido em |
|---|---|
| [Conversions API, visão geral](https://developers.facebook.com/docs/marketing-api/conversions-api) | 09/11/2026 |
| [Parâmetros do evento de servidor](https://developers.facebook.com/docs/marketing-api/conversions-api/parameters/server-event) | 09/11/2026 |
| [Deduplicação entre Pixel e servidor](https://developers.facebook.com/documentation/ads-commerce/conversions-api/deduplicate-pixel-and-server-events) | 09/11/2026 |

## Resumo para o Gescar

A Conversions API (CAPI) manda eventos do **servidor ou do CRM** direto para a Meta, ligados a um **conjunto de dados (dataset)**. A Meta trata esses eventos como trata os do Pixel: servem para medir, montar públicos e otimizar. É o que permite levar para a Meta eventos que acontecem fora do site, como "demonstração realizada" e "assinatura fechada", que é exatamente o fluxo aprovado do Gescar (CRM, estoque e vendas → Conversions API → Meta Ads).

Campos que importam:

- **event_name** (obrigatório): nome do evento, padrão ou personalizado.
- **event_time** (obrigatório): horário real do evento, em Unix (segundos, GMT). Pode ter **até 7 dias no passado**. Se **um** evento do lote passar de 7 dias, **o lote inteiro é recusado**.
- **action_source** (obrigatório): onde a conversão aconteceu. Valores aceitos: `email`, `website`, `app`, `phone_call`, `chat`, `physical_store`, `system_generated`, `business_messaging`, `other`.
- **event_id** (opcional, mas recomendado): identificador único escolhido por nós. É a chave da deduplicação.
- **user_data** (obrigatório): dados do cliente para casamento. Regras de normalização e hash estão na página de parâmetros de cliente, **não lida nesta rodada: conferir antes de implementar**.

Deduplicação (quando o mesmo evento vai pelo Pixel e pela CAPI):

- O método principal é **event_id + event_name iguais** nos dois lados. No Pixel, o ID vai como quarto argumento do `fbq('track', ...)`.
- A Meta só descarta a duplicata se ela chegar **em até 48 horas** do primeiro evento com aquele event_id, no mesmo Pixel.
- Alternativa: mesmo event_name com `fbp` e/ou `external_id`. Só funciona bem quando o evento do navegador chega primeiro, e **não** remove duplicatas da mesma fonte.
- Se os dois chegam iguais, a Meta em geral fica com o que chegou primeiro.

## Regras práticas (viram checklist)

- [ ] Todo evento enviado pelos dois caminhos (Pixel + CAPI) leva o **mesmo event_id e o mesmo event_name**.
- [ ] event_id único por evento (ex.: ID do lead no CRM + etapa). Nunca reaproveitar.
- [ ] Fila de envio da CAPI roda pelo menos **diariamente**: nada pode passar de 7 dias, senão o lote cai inteiro.
- [ ] Eventos que só existem no CRM (demo realizada, venda) vão só pela CAPI, com `action_source` correto (`system_generated` ou `other` para etapa de CRM; `business_messaging` quando o lead veio do WhatsApp, ver doc 04).
- [ ] Nomes e pesos dos eventos seguem `trafego-pago/medicao/eventos.md` (fonte única do projeto). Para o canal de mensagens (doc 04), os nomes aceitos pela Meta são `LeadSubmitted`, `QualifiedLead` e `Purchase`: mapear os eventos do Gescar para eles ao enviar pela CAPI de mensagens.
- [ ] Depois de ligar, verificar no Gerenciador de Eventos se os eventos chegam, deduplicam e casam.
