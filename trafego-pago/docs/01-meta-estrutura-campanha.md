# 01 · Meta: estrutura de campanha

| Fonte oficial | Lido em |
|---|---|
| [Marketing API, visão geral](https://developers.facebook.com/docs/marketing-api) | 09/11/2026 |
| [Ad Campaign Structure](https://developers.facebook.com/docs/marketing-api/campaign-structure) | 09/11/2026 |
| [Graph API Changelog (versões)](https://developers.facebook.com/docs/graph-api/changelog) | 09/11/2026 |

## Resumo para o Gescar

A Meta organiza tudo em três níveis, e cada nível tem uma responsabilidade que não se mistura:

- **Campanha**: o contêiner de mais alto nível. Tem **um único objetivo**. A API recusa anúncios que não combinem com o objetivo da campanha.
- **Conjunto de anúncios**: onde ficam **público, orçamento, programação, lance e meta de otimização**. Todos os anúncios do conjunto compartilham a mesma segmentação e otimização. A Meta recomenda **um conjunto por público**, para controlar gasto e ler métricas por público.
- **Anúncio**: a peça que aparece em Facebook, Instagram, Messenger e WhatsApp. Vários anúncios no mesmo conjunto servem para testar imagem, texto, vídeo e posicionamento.
- **Criativo**: guarda só os elementos visuais e **não pode ser editado depois de criado** (para mudar, cria-se outro).

Versão da API na data da leitura: a página da Marketing API cita **v25.0**, mas o changelog já lista **v26.0 (lançada em 29/07/2026)**, com atualização automática de versão anunciada para a mesma data. A v24.0 da Marketing API ficou disponível só até 06/10/2026.

## Regras práticas (viram checklist)

- [ ] Uma campanha = um objetivo. Não misturar captação de revenda e remarketing na mesma campanha se o objetivo for diferente.
- [ ] Um conjunto por público (ex.: "donos de revenda MT" separado de "visitantes do site").
- [ ] Orçamento definido no conjunto, salvo decisão explícita de usar orçamento de campanha (Advantage+ campaign budget).
- [ ] Pelo menos 2 anúncios por conjunto para ter comparação, sem pulverizar o orçamento de R$500.
- [ ] Criativo errado não se edita: cria-se um novo e registra-se em `decisoes/log.md`.
- [ ] Qualquer automação via API usa a versão vigente no changelog (hoje v26.0). Conferir na rotina mensal.
- [ ] Publicar (status ACTIVE) só com aprovação do Edelson. Todo anúncio passa por revisão da Meta (status PENDING_REVIEW).
