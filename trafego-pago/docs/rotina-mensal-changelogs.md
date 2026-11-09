# Rotina mensal: conferência de changelogs

Tarefa agendada que roda **todo dia 3, às 10h17 (horário de Cuiabá)**, no projeto Gescar ADS.

## O que confere

| Fonte | Link |
|---|---|
| Graph / Marketing API changelog | https://developers.facebook.com/docs/graph-api/changelog |
| WhatsApp changelog | https://developers.facebook.com/documentation/business-messaging/whatsapp/changelog |
| Preços do WhatsApp | https://developers.facebook.com/docs/whatsapp/pricing |
| Google Ads API, notas de versão | https://developers.google.com/google-ads/api/docs/release-notes |
| Blog de desenvolvedores Google Ads | https://ads-developers.googleblog.com/ |

## Quando avisa o Edelson

Só se algo mudou desde a última leitura **e** afeta o Gescar. Exemplos:

- Nova versão ou desativação da Marketing API ou da Google Ads API.
- Mudança em Conversions API, CAPI para mensagens, `ctwa_clid` ou deduplicação.
- Mudança de preço do WhatsApp, janela de 72h, tabela em BRL ou faturamento local no Brasil.
- Mudança em importação offline, conversões otimizadas para leads ou Data Manager.

Se nada relevante mudou, não envia mensagem. Quando algo muda, a rotina atualiza a data de leitura e o resumo do doc afetado em um PR, e cita o PR no aviso. Nada é publicado em contas de anúncio.
