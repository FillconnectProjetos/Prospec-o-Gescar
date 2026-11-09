# 13 · LGPD aplicada a anúncios, formulários e WhatsApp

| Fonte oficial | Lido em |
|---|---|
| [ANPD: Guia orientativo Cookies e Proteção de Dados Pessoais (out/2022)](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-orientativo-cookies-e-protecao-de-dados-pessoais.pdf/@@display-file/file) | 09/11/2026 |
| [ANPD: Guia orientativo de Legítimo Interesse (02/02/2024)](https://www.gov.br/anpd/pt-br/assuntos/noticias/anpd-lanca-guia-orientativo-sobre-legitimo-interesse) | 09/11/2026 (notícia de lançamento; [PDF do guia](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia_legitimo_interesse.pdf/@@display-file/file) a ler por completo) |
| [ANPD: Resolução CD/ANPD nº 2/2022 (agentes de pequeno porte)](https://www.gov.br/anpd/pt-br/acesso-a-informacao/institucional/atos-normativos/regulamentacoes_anpd/resolucao-cd-anpd-no-2-de-27-de-janeiro-de-2022) | 09/11/2026 (localizada; **conteúdo a confirmar**) |
| [Lei nº 13.709/2018 (LGPD), Planalto](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm) | 09/11/2026: **acesso automático bloqueado; abrir manualmente** |

> Este documento resume orientação oficial para uso operacional. Não substitui parecer jurídico.

## Resumo para o Gescar

**Cookies e rastreamento (guia da ANPD)**

- Dados coletados por cookies podem ser dados pessoais, principalmente quando formam perfil de comportamento.
- **Cookies de publicidade** (Pixel da Meta, Google Tag com remarketing) **dificilmente se apoiam em legítimo interesse**, sobretudo com cookie de terceiro e rastreamento entre sites. A base adequada costuma ser o **consentimento**.
- Cookies **estritamente necessários** tendem a se apoiar em legítimo interesse; consentimento não serve para eles.
- Medição de audiência pode usar legítimo interesse **se for agregada**, sem perfil e sem cruzamento.
- Banner, boas práticas: botão **Rejeitar** com o mesmo destaque do Aceitar; segundo nível por categoria; cookies que dependem de consentimento **desligados por padrão**; link para exercer direitos; consentimento **registrado** (o ônus da prova é do controlador).
- Banner, o que evitar: só botão "Concordo"; aceite destacado e recusa escondida; cookies já ativos; condicionar acesso ao aceite; "continuar navegando = aceite"; não ter como revogar.
- Política de cookies informa finalidade, prazo, compartilhamento com terceiros e direitos.

**Legítimo interesse (guia de 2024)**

- Base do art. 7º, IX: permite tratar dados quando necessário a interesse legítimo, **sem violar direitos do titular**. Não vale para dados sensíveis.
- O guia propõe um **teste de balanceamento em três fases**: finalidade, necessidade e balanceamento com salvaguardas.

**Aplicação ao Gescar (interpretação nossa, a validar com jurídico)**

- **Formulário de lead**: o dado é pedido para responder ao próprio interessado (contato comercial pedido por ele). Informar claramente a finalidade, quem é o controlador (Fillconnect) e o link da política de privacidade. Para enviar o dado às plataformas de anúncio (Conversions API, Data Manager), avisar isso na política e, de preferência, pedir consentimento específico no formulário.
- **WhatsApp**: a política do próprio WhatsApp já exige opt-in e política de privacidade publicada (doc 07). Guardar prova do opt-in.
- **Público B2B**: dono de revenda é pessoa física por trás de uma empresa; nome, telefone e e-mail dele **são dados pessoais**, mesmo em venda B2B.

## Regras práticas (viram checklist)

- [ ] Política de privacidade publicada no site do Gescar, em português, com: controlador, finalidades, bases legais, compartilhamento com Meta e Google, prazo de guarda, direitos e canal de contato.
- [ ] Banner de cookies conforme o guia da ANPD (rejeitar fácil, padrão desligado, registro do consentimento).
- [ ] Formulário com texto de finalidade, link da política e caixa de consentimento **não pré-marcada** para uso em publicidade.
- [ ] Opt-in do WhatsApp registrado no CRM (data, canal, texto).
- [ ] Canal para pedido de exclusão funcionando e prazo de resposta definido.
- [ ] Hash SHA-256 em e-mail e telefone antes de enviar a qualquer plataforma.
- [ ] Ler a LGPD (arts. 7º, 8º, 9º, 10, 18 e 41) e a Resolução 2/2022 manualmente e completar este doc com o que se aplica à Fillconnect (incluindo encarregado ou canal de comunicação).
