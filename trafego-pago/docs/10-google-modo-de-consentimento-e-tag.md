# 10 · Google: Modo de Consentimento e Google Tag

| Fonte oficial | Lido em |
|---|---|
| [Visão geral do Modo de Consentimento (Tag Platform)](https://developers.google.com/tag-platform/security/concepts/consent-mode) | 09/11/2026 |
| [Sobre o Modo de Consentimento (Google Ads)](https://support.google.com/google-ads/answer/10000067) | 09/11/2026 (localizado; detalhe técnico lido na página acima) |
| [Configurar o Modo de Consentimento](https://support.google.com/google-ads/answer/14009635) | 09/11/2026 (localizado; ler ao implementar) |

## Resumo para o Gescar

O Modo de Consentimento faz a Google Tag mudar de comportamento conforme a escolha do visitante no banner de cookies. Quatro sinais, cada um "concedido" ou "negado":

- `ad_storage`: cookies de publicidade.
- `ad_user_data`: envio de dados do usuário ao Google para publicidade.
- `ad_personalization`: publicidade personalizada (remarketing).
- `analytics_storage`: cookies de análise.

Dois modos:

- **Básico**: a tag fica bloqueada até a pessoa responder ao banner. Se recusar, nada vai ao Google. A modelagem de conversões usa um modelo genérico.
- **Avançado**: a tag carrega na abertura da página com padrão "negado" e envia sinais sem cookies até haver consentimento. Permite modelagem mais precisa para a conta.

A página não diz que o modo é obrigatório fora do Espaço Econômico Europeu, mas deixa claro que **obter o consentimento é responsabilidade do anunciante**, inclusive para dados enviados por upload. No Brasil, quem define isso é a LGPD e o guia de cookies da ANPD (doc 13): **cookies de publicidade pedem consentimento**.

## Regras práticas (viram checklist)

- [ ] Site do Gescar com banner de cookies que tenha botão "Rejeitar" com o mesmo destaque de "Aceitar" (ANPD, doc 13).
- [ ] Google Tag instalada em todas as páginas, com Modo de Consentimento ligado e padrão **negado** para os quatro sinais.
- [ ] Recomendação nossa: começar no modo **básico**, que é o mais seguro diante do guia da ANPD. O avançado melhora a modelagem com volume pequeno, mas envia sinais sem cookie antes do aceite: só migrar com validação jurídica e registro em `decisoes/log.md`.
- [ ] Remarketing (`ad_personalization`) só para quem aceitou.
- [ ] Conferir a implementação pela página "Verificar o Modo de Consentimento" do Google Ads antes de publicar.
