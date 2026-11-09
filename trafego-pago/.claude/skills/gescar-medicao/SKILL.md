---
name: gescar-medicao
description: Confere a medição do Gescar (Google Tag, Modo de Consentimento, Pixel, Conversions API, ctwa_clid, Data Manager e deduplicação) antes de publicar ou quando os números não batem.
---

# Conferência de medição (Gescar)

O Claude Ads já audita Pixel, Events Manager e conversões do Google de forma genérica (skills `ads-meta` e `ads-google`), mas a skill de eventos de servidor dele não está instalada. Use esta skill para o fluxo específico do Gescar: CRM → Conversions API / Data Manager, WhatsApp com `ctwa_clid` e os eventos Lead, Lead Qualificado, Demo, Venda.

## Como fazer

1. Leia:
   - `trafego-pago/docs/03-meta-conversions-api-e-deduplicacao.md`
   - `trafego-pago/docs/04-meta-clique-para-whatsapp-e-capi-mensagens.md`
   - `trafego-pago/docs/09-google-conversoes-e-importacao-offline.md`
   - `trafego-pago/docs/10-google-modo-de-consentimento-e-tag.md`
   - `trafego-pago/medicao/eventos.md` (nomes e pesos dos eventos do projeto)
2. Preencha a seção 2 de `trafego-pago/docs/checklist-pre-publicacao.md` com evidência (print, export, log). Sem evidência, o item fica "desconhecido", nunca "ok".
3. Confira em especial: `event_id` igual entre Pixel e CAPI; nada com mais de 7 dias na CAPI; `ctwa_clid` gravado no CRM; envio ao Google pelo Data Manager dentro de 63 dias; consentimento enviado junto.
4. Liste o que falta, em ordem de impacto no aprendizado da campanha.

## Regras

- Se um arquivo citado acima não existir (ele vem da branch `trafego-pago/plano-ciclo-1`), diga isso no topo da resposta e use o que está em `trafego-pago/docs/`. Nunca invente orçamento, critério ou nome de evento.

- Só leitura. Mudança em Pixel, evento, dataset ou conversão em conta real precisa de aprovação do Edelson.
- Não colar tokens ou chaves em arquivo ou conversa.
