---
name: gescar-estrutura-campanha
description: Monta rascunho de campanha Google ou Meta no padrão de nomenclatura e estrutura do Gescar, dentro do orçamento do ciclo. Use ao planejar ou montar uma campanha nova.
---

# Montagem de campanha no padrão Gescar

Para estratégia de mídia genérica, o Claude Ads já cobre (skill `ads-plan`); para contas e verba, `ads-math`. Esta skill aplica o modelo próprio do Gescar por cima.

## Como fazer

1. Leia `trafego-pago/docs/estrutura-campanhas.md` (modelo, nomenclatura e divisão do ciclo) e os docs que ele cita para a plataforma escolhida.
2. Produza o rascunho com: nome de cada nível no padrão `GESCAR | Plataforma | Objetivo | Público | Região | C<n>`, objetivo, público, região, orçamento diário, lance, conversão primária e anúncios.
3. Mostre quanto o rascunho consome do orçamento do ciclo e o saldo.
4. Rode a skill `gescar-politicas-anuncio` nos textos e anexe a seção 5 do `checklist-pre-publicacao.md`.
5. Prepare o registro em `trafego-pago/decisoes/log.md` (data, motivo, resultado esperado) para o Edelson aprovar.

## Regras

- Se um arquivo citado acima não existir (ele vem da branch `trafego-pago/plano-ciclo-1`), diga isso no topo da resposta e use o que está em `trafego-pago/docs/`. Nunca invente orçamento, critério ou nome de evento.

- Rascunho apenas. Criar, ativar, pausar ou mudar orçamento só com aprovação explícita do Edelson, ação por ação.
- Não ultrapassar o teto do ciclo definido em `trafego-pago/README.md` (ciclo 1: até R$498).
- Cada regra do rascunho cita o doc de origem.
