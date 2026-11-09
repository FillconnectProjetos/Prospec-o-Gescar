---
name: gescar-politicas-anuncio
description: Revisa anúncio, texto e página de destino do Gescar contra as políticas Meta/Google e a LGPD antes de pedir aprovação de publicação. Use quando houver criativo, copy ou landing page para revisar.
---

# Revisão de política e LGPD (Gescar)

Camada específica do Gescar. Para a análise genérica de página de destino use a skill `ads-landing` do Claude Ads, e para política dentro da conta, `ads-meta` e `ads-google` (instaladas em `.claude/skills/` na raiz do repositório). Esta skill cobre o que o Claude Ads não sabe: promessas que o Gescar não entrega, regras de LGPD do Brasil e o padrão de aprovação do projeto.

## Como fazer

1. Leia os docs, não repita o conteúdo deles:
   - `trafego-pago/docs/05-meta-politicas-de-anuncios.md`
   - `trafego-pago/docs/11-google-politicas-de-anuncios.md`
   - `trafego-pago/docs/07-whatsapp-politicas-e-templates.md`
   - `trafego-pago/docs/13-lgpd-anuncios-formularios-whatsapp.md`
2. Preencha as seções 1, 3 e 4 de `trafego-pago/docs/checklist-pre-publicacao.md` para a peça.
3. Para cada item reprovado, diga o trecho exato, o doc que proíbe e uma reescrita.
4. Se um doc tiver data de leitura com mais de 60 dias ou trecho "a confirmar", avise antes de concluir.

## Regras

- Se um arquivo citado acima não existir (ele vem da branch `trafego-pago/plano-ciclo-1`), diga isso no topo da resposta e use o que está em `trafego-pago/docs/`. Nunca invente orçamento, critério ou nome de evento.

- Saída é parecer, nunca publicação. Nada vai ao ar sem aprovação explícita do Edelson, ação por ação.
- Na dúvida entre aprovar e reprovar, reprove e explique.
- Não invente regra de plataforma: se não está nos docs, marque "a confirmar na fonte oficial".
