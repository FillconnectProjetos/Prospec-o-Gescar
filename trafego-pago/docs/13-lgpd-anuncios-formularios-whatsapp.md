# 13 · LGPD aplicada a anúncios, formulários e WhatsApp

| Fonte oficial | Lido em |
|---|---|
| [Lei nº 13.709/2018 (LGPD), Planalto](https://www.planalto.gov.br/ccivil_03/_ato2015-2018/2018/lei/l13709.htm) | 09/11/2026, lida pelo Edelson no navegador (a leitura automática é bloqueada pelo site). Foram lidos os arts. 5º, 7º (até o inciso VI), 8º, 9º, 18 e 52 |
| [ANPD: Guia orientativo Cookies e Proteção de Dados Pessoais (out/2022)](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia-orientativo-cookies-e-protecao-de-dados-pessoais.pdf/@@display-file/file) | 09/11/2026 |
| [ANPD: Guia orientativo de Legítimo Interesse (02/02/2024)](https://www.gov.br/anpd/pt-br/assuntos/noticias/anpd-lanca-guia-orientativo-sobre-legitimo-interesse) | 09/11/2026 (notícia de lançamento; o [PDF do guia](https://www.gov.br/anpd/pt-br/centrais-de-conteudo/materiais-educativos-e-publicacoes/guia_legitimo_interesse.pdf/@@display-file/file) ainda falta ler por completo) |
| [ANPD: Resolução CD/ANPD nº 2/2022 (agentes de pequeno porte)](https://www.gov.br/anpd/pt-br/acesso-a-informacao/institucional/atos-normativos/regulamentacoes_anpd/resolucao-cd-anpd-no-2-de-27-de-janeiro-de-2022) | 09/11/2026 (localizada; **conteúdo a confirmar**) |

> **Não é aconselhamento jurídico.** Este documento resume a lei e os guias da ANPD para uso operacional. Antes da primeira campanha, um advogado deve validar a política de privacidade, os textos de consentimento e as bases legais escolhidas.

## Resumo para o Gescar

### O que a lei diz (texto público; aqui vai só o resumo, e o link acima é a referência)

- **Art. 5º, definições.** **Dado pessoal** é qualquer informação ligada a uma pessoa identificada ou identificável. **Dado pessoal sensível** é a categoria especial, que inclui saúde, religião, origem racial e biometria, entre outros. **Titular** é a pessoa a quem os dados se referem. **Controlador** é quem decide sobre o tratamento, que no caso do Gescar é a Fillconnect.
- **Art. 7º, bases legais.** O tratamento só é permitido com uma base legal. Nos incisos lidos (I a VI) estão o **consentimento**, o **cumprimento de obrigação legal** e a **execução de contrato** (ou de procedimentos preliminares a pedido do titular), além de outras hipóteses, como o exercício regular de direitos. **O restante do artigo ficou truncado na leitura, incluindo o legítimo interesse (inciso IX), e precisa ser confirmado no link.** O guia da ANPD de 2024 trata do legítimo interesse e propõe um teste em três fases: finalidade, necessidade e balanceamento com salvaguardas.
- **Art. 8º, consentimento.** Pode ser dado por escrito ou por outro meio que comprove a vontade do titular. Se for escrito, vai em cláusula destacada. **O ônus de provar o consentimento é de quem coleta.** Vale só para finalidades determinadas, e autorização genérica é nula. Pode ser revogado a qualquer momento, por procedimento gratuito e fácil.
- **Art. 9º, transparência.** O titular tem direito a informação clara e ostensiva sobre a finalidade, a forma e a duração do tratamento, a identidade e o contato do controlador, o compartilhamento de dados, as responsabilidades e os seus direitos.
- **Art. 18, direitos do titular.** Entre outros: confirmação de que há tratamento, acesso, correção, anonimização, bloqueio ou eliminação de dados desnecessários e portabilidade.
- **Art. 52, sanções.** Advertência, multa de até 2% do faturamento no Brasil limitada a R$50 milhões por infração, multa diária e publicização da infração, entre outras. A página marca alguns incisos com nota de vigência, então convém conferir quais estão em vigor.

### O que a ANPD orienta sobre cookies

- Dados coletados por cookies podem ser dados pessoais, principalmente quando formam um perfil de comportamento.
- **Cookies de publicidade** (Pixel da Meta, Google Tag com remarketing) **dificilmente se apoiam em legítimo interesse**, sobretudo quando são cookies de terceiro ou rastreiam entre sites. A base adequada costuma ser o **consentimento**.
- Cookies **estritamente necessários** tendem a se apoiar em legítimo interesse, e o consentimento não serve para eles. A medição de audiência pode usar legítimo interesse se for agregada, sem perfil e sem cruzamento de dados.
- Boas práticas para o banner: botão **Rejeitar** com o mesmo destaque do Aceitar, segundo nível com escolha por categoria, cookies que dependem de consentimento **desligados por padrão**, link para exercer direitos e **registro do consentimento**.
- O que evitar no banner: ter só o botão "Concordo", esconder a recusa, deixar cookies já ativos, condicionar o acesso ao aceite, tratar "continuar navegando" como aceite e não oferecer forma de revogar.

### Aplicação ao Gescar (nossa interpretação, a validar com o advogado)

- **Formulário e clique no WhatsApp.** Antes do envio, mostrar um aviso claro de finalidade ("contato comercial sobre o Gescar"), o nome do controlador (Fillconnect) e o link da política de privacidade (art. 9º).
- **Base legal por finalidade.** Para responder a quem pediu contato, a base provável é procedimento preliminar a contrato a pedido do titular (art. 7º, V). Para usar o dado em publicidade (Conversions API, Data Manager, remarketing), a base é o **consentimento específico**, com caixa não pré-marcada (art. 8º). Ainda falta confirmar se o legítimo interesse cabe em alguma etapa, depois de ler o inciso IX e o guia.
- **Mínimo de dados para as plataformas.** Enviar à Meta e ao Google só o necessário para medir (e-mail e telefone com hash, ID do evento e etapa), e só dos leads com base legal definida.
- **Prova do consentimento.** Registrar no CRM a data, a hora, o canal, o texto aceito e a versão da política. Sem esse registro, o consentimento não se prova (art. 8º).
- **Canal do titular.** Ter um e-mail ou formulário para pedidos de acesso, correção e exclusão, com prazo de resposta definido (art. 18).
- **Dono de revenda.** Mesmo em venda B2B, o nome, o telefone e o e-mail dele são dados pessoais.
- **WhatsApp.** A própria política do WhatsApp exige opt-in e política de privacidade publicada (doc 07).
- **Dados vindos da Meta.** Só em agregado, sem enriquecer ficha de lead (doc 05, item 9). Isso também ajuda a cumprir o princípio de usar só o necessário.

## Regras práticas (viram checklist)

- [ ] Política de privacidade publicada em português, com controlador, contato, finalidades, bases legais, compartilhamento com Meta e Google, prazo de guarda e direitos do titular (art. 9º)
- [ ] Banner de cookies conforme o guia da ANPD: Rejeitar fácil, padrão desligado e registro do consentimento
- [ ] Formulário com aviso de finalidade, link da política e caixa de consentimento **não pré-marcada** para uso em publicidade (art. 8º)
- [ ] Botão ou anúncio de WhatsApp com aviso de finalidade e link da política
- [ ] Prova do consentimento guardada no CRM (data, hora, canal, texto, versão da política)
- [ ] Opt-in do WhatsApp registrado
- [ ] Revogação tão fácil quanto o aceite (art. 8º)
- [ ] Canal do titular funcionando, com prazo de resposta definido (art. 18)
- [ ] Eventos enviados às plataformas só com o mínimo de dados, com hash SHA-256 e só de leads com base legal definida
- [ ] **Pendente:** confirmar o art. 7º a partir do inciso VII (legítimo interesse), a vigência dos incisos do art. 52 e a Resolução 2/2022 (encarregado ou canal de comunicação para agente de pequeno porte)
- [ ] **Validação do advogado** da política, dos textos de consentimento e das bases legais antes da primeira publicação
