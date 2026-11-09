---
name: gescar-relatorio-ciclo
description: Fecha um ciclo de orçamento do Gescar (ciclo 1 de até R$500), compara com o critério combinado e recomenda escalar, manter ou cortar. Use no fim de cada ciclo.
---

# Relatório de fechamento de ciclo (Gescar)

O Claude Ads gera o diagnóstico de conta (`ads-audit`) e as contas de custo (`ads-math`). Esta skill transforma isso na decisão de ciclo do Gescar, usando o modelo `trafego-pago/relatorios/modelo-semanal.md`.

## Como fazer

1. Junte, por campanha (nome no padrão de `trafego-pago/docs/estrutura-campanhas.md`): gasto, conversas/leads, leads qualificados, demos agendadas, demos feitas, vendas, custo do WhatsApp (doc 06).
2. Calcule custo por contato qualificado e custo por demo agendada. Diga a qualidade da medição (doc 03, 04, 09): se só houver "conversa iniciada", diga isso no topo.
3. Compare com o critério do ciclo em `trafego-pago/README.md` (ciclo 1: 3+ demos realizadas, custo por demo até R$120, custo por contato qualificado até R$60) e com `trafego-pago/decisoes/log.md`. Se não houver critério, recomende "manter sem escalar" e peça a definição.
4. Recomende uma de três: **escalar** (com valor do próximo ciclo), **manter** ou **cortar**, com o motivo em uma frase e o que muda.
5. Salve o relatório em `trafego-pago/relatorios/` e prepare o registro de decisão.

## Regras

- Recomendação, não execução. O próximo ciclo só começa com aprovação explícita do Edelson.
- Escalar só se o critério for atingido. Volume pequeno: diga a incerteza, não extrapole.
- Não somar a campanha do Renave ao Gescar sem confirmação de que ela faz parte do ciclo.
