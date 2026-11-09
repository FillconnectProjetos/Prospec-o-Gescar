# Conversões e pesos

| Evento | Peso (R$) | Google Ads | Meta | Como medir |
| --- | --- | --- | --- | --- |
| Clique no WhatsApp | 10 | Primária | Contact (pixel) | Já existe; trocar valor de 1 para 10 |
| Formulário enviado | 30 | Primária | Lead (pixel) | Novo evento no envio do formulário |
| Contato qualificado | 50 | Offline | Lead Qualificado (CAPI) | Marcação do comercial |
| Demonstração realizada | 100 | Offline | Demo / Test Drive (CAPI) | Marcação do comercial |
| Proposta enviada | 150 | Secundária | Proposta Enviada (CAPI) | Marcação do comercial |
| Venda | 1.000 | Offline | Venda (CAPI) | Contrato assinado |

Pesos são prioridade para o algoritmo, não receita.

## Planilha de origem (até o CRM enviar eventos)
data · revenda · cidade · código de origem · qualificado (s/n) · demo (s/n) · proposta (s/n) · venda (s/n) · plano

## Achados no site (código do repositório Gescar)
1. O formulário abre o WhatsApp via `window.open`; o rastreio só escuta cliques em `<a>`. Envio do formulário não conta.
2. Não há pixel do Meta (só verificação de domínio).
3. O site carrega GTM-N2FDXQF4 e a tag AW-18564154180 direto. Se o GTM também tiver a conversão, conta em dobro.
4. Conversão de WhatsApp com valor fixo de R$1.
5. Sem agendamento de demonstração no site.
6. Página /renave-obrigatorio com contagem até 20/11: precisa de nova mensagem a partir de 21/11.

## Correções propostas (aguardando aprovação)
1. Evento de formulário no envio, antes de abrir o WhatsApp.
2. Pixel do Meta só nas páginas públicas.
3. Uma única fonte de disparo da conversão de WhatsApp.
4. Guardar gclid/fbclid na sessão para importação offline.
5. Conversions API depois do ciclo 1 (Lead, Lead Qualificado, Proposta Enviada, Venda).

## Restrições confirmadas (docs do PR #2)
- Google offline: desde 15/06/2026 a importação de conversões offline é feita pelo **Data Manager** (arquivo na interface ou Data Manager API). Não usar `UploadClickConversions`. Prazo de envio: até 63 dias após o clique.
- Meta CAPI para mensagens exige **WhatsApp Cloud API** e o `ctwa_clid` gravado no CRM no primeiro contato. O app WhatsApp Business do celular não serve.
- Até lá, a atribuição de qualificado, demo e venda vem do código de origem na mensagem.
