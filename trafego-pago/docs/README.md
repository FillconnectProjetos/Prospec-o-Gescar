# Biblioteca de documentação oficial · Gescar ADS

Base de consulta do tráfego pago do Gescar e do futuro produto Gescar ADS. Cada arquivo traz **link oficial, data de leitura, resumo em nossas palavras e regras práticas em checklist**. Não copiamos as páginas: o texto completo fica na fonte.

**Regra fixa:** o projeto planeja e monta. Nada é publicado e nenhum gasto muda sem aprovação explícita do Edelson, ação por ação, com registro em `trafego-pago/decisoes/log.md`.

Leitura de todas as fontes: **09/11/2026**. As páginas que bloqueiam leitura automática (Padrões de Publicidade da Meta e texto da LGPD) foram lidas pelo Edelson no navegador nessa mesma data. Itens marcados "a confirmar" ou "abrir manualmente" não puderam ser lidos de forma automática e precisam de conferência humana antes da primeira publicação.

## Meta

| # | Tema | Arquivo | Status |
|---|---|---|---|
| 01 | Estrutura de campanha (campanha, conjunto, anúncio) e versão da API (v26.0) | [01-meta-estrutura-campanha.md](01-meta-estrutura-campanha.md) | Lido |
| 02 | Objetivos e Advantage+ leads | [02-meta-objetivos-e-advantage-leads.md](02-meta-objetivos-e-advantage-leads.md) | Lido via Central de Ajuda; link original bloqueado |
| 03 | Conversions API e deduplicação com o Pixel | [03-meta-conversions-api-e-deduplicacao.md](03-meta-conversions-api-e-deduplicacao.md) | Lido; hash de `user_data` a conferir |
| 04 | Clique para WhatsApp e CAPI para Business Messaging (`ctwa_clid`) | [04-meta-clique-para-whatsapp-e-capi-mensagens.md](04-meta-clique-para-whatsapp-e-capi-mensagens.md) | Lido |
| 05 | Políticas de anúncios | [05-meta-politicas-de-anuncios.md](05-meta-politicas-de-anuncios.md) | Lido (Padrões de Publicidade lidos pelo Edelson no navegador) |

## WhatsApp

| # | Tema | Arquivo | Status |
|---|---|---|---|
| 06 | Cloud API e preços (por mensagem, janela de 72h, trimestre) | [06-whatsapp-cloud-api-e-precos.md](06-whatsapp-cloud-api-e-precos.md) | Lido |
| 07 | Políticas e templates | [07-whatsapp-politicas-e-templates.md](07-whatsapp-politicas-e-templates.md) | Lido; página de opt-in a conferir |

## Google

| # | Tema | Arquivo | Status |
|---|---|---|---|
| 08 | Estrutura de conta | [08-google-estrutura-de-conta.md](08-google-estrutura-de-conta.md) | Lido |
| 09 | Conversões, conversões otimizadas para leads, importação offline e Data Manager | [09-google-conversoes-e-importacao-offline.md](09-google-conversoes-e-importacao-offline.md) | Lido; migração de 15/06/2026 **confirmada** |
| 10 | Modo de Consentimento e Google Tag | [10-google-modo-de-consentimento-e-tag.md](10-google-modo-de-consentimento-e-tag.md) | Lido |
| 11 | Políticas (atenção à Deturpação) | [11-google-politicas-de-anuncios.md](11-google-politicas-de-anuncios.md) | Lido |
| 12 | Google Ads API (v26.1) | [12-google-ads-api.md](12-google-ads-api.md) | Lido; fim do token de desenvolvedor a confirmar |

## Brasil

| # | Tema | Arquivo | Status |
|---|---|---|---|
| 13 | LGPD em anúncios, formulários e WhatsApp | [13-lgpd-anuncios-formularios-whatsapp.md](13-lgpd-anuncios-formularios-whatsapp.md) | Lido: guias da ANPD e LGPD (arts. 5º, 7º até VI, 8º, 9º, 18, 52). Falta conferir o art. 7º a partir do VII e a Resolução 2/2022. Exige validação de advogado |

## Modelo e operação Gescar

| Arquivo | Para que serve |
|---|---|
| [estrutura-campanhas.md](estrutura-campanhas.md) | Nomenclatura padrão, estrutura Google (Pesquisa) e Meta (Cadastros/WhatsApp e remarketing) e divisão do ciclo de R$500, cada regra com o doc de origem |
| [checklist-pre-publicacao.md](checklist-pre-publicacao.md) | O que conferir antes de pedir aprovação: política, medição, LGPD, página de destino, nomenclatura |
| [rotina-mensal-changelogs.md](rotina-mensal-changelogs.md) | Tarefa agendada que confere changelogs e preços e só avisa se algo afetar o Gescar |

## Skills do projeto

Ficam em `trafego-pago/.claude/skills/`. São curtas e apontam para estes docs. Complementam as skills do Claude Ads instaladas em `.claude/skills/` na raiz pela branch `trafego-pago/plano-ciclo-1` (`ads-audit`, `ads-plan`, `ads-meta`, `ads-google`, `ads-landing`, `ads-math`, `ads-dna`) sem repetir o que elas fazem.

| Skill | O que faz | O que fica com o Claude Ads |
|---|---|---|
| `gescar-politicas-anuncio` | Revisa peça e página contra docs 05, 07, 11 e 13 | Página de destino e política na conta (`ads-landing`, `ads-meta`, `ads-google`) |
| `gescar-estrutura-campanha` | Monta rascunho no padrão Gescar, dentro do ciclo | Estratégia de mídia e contas de verba (`ads-plan`, `ads-math`) |
| `gescar-medicao` | Confere Tag, Pixel, CAPI, `ctwa_clid`, Data Manager e deduplicação | Pixel, Events Manager e conversões Google em geral (`ads-meta`, `ads-google`); CAPI de servidor e `ctwa_clid` não são cobertos |
| `gescar-relatorio-ciclo` | Fecha o ciclo e recomenda escalar, manter ou cortar | Diagnóstico de conta e cálculo de custo (`ads-audit`, `ads-math`) |

Para o Claude Code carregar essas skills, abra a sessão dentro de `trafego-pago/`.

**Dependência:** as skills citam `trafego-pago/README.md` (orçamento e critério), `trafego-pago/medicao/eventos.md` (eventos), `trafego-pago/relatorios/modelo-semanal.md` e `trafego-pago/decisoes/log.md`, que vêm da branch `trafego-pago/plano-ciclo-1`. Até ela entrar na `main`, cada skill usa o que está nestes docs e avisa que o arquivo de origem está ausente.

## Pontos de atenção levantados na leitura

1. **Upload offline no Google mudou (confirmado):** desde 15/06/2026 vai pelo Data Manager; a Google Ads API recusa quem não tinha histórico. O Gescar começa direto no Data Manager.
2. **Clique para WhatsApp só mede qualidade com Cloud API:** sem ela, não há `ctwa_clid` e a campanha otimiza só para "conversa iniciada".
3. **Janela de 72h grátis exige resposta em 24h** e vale só para quem veio pelo app de celular.
4. **Deturpação no Google suspende conta sem aviso:** nenhuma promessa de resultado ou funcionalidade futura.
5. **Cookies de publicidade pedem consentimento** pelo guia da ANPD: banner e política de privacidade são pré-requisito, não detalhe.
6. **Meta: uma conta de anúncios por lojista** no Gescar ADS, e dado de publicidade da Meta só em agregado, nunca para enriquecer ficha de lead (doc 05).
7. **Consentimento precisa de prova:** o CRM guarda data, canal, texto aceito e versão da política (LGPD art. 8º, doc 13).
