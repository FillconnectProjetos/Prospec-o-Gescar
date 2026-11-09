# Checklist pré-publicação

Preencher para **cada** campanha ou anúncio antes de pedir aprovação ao Edelson. Item sem ✅ bloqueia o pedido. O checklist preenchido vai junto com o registro em `decisoes/log.md`.

Campanha: `______________________`  Data: `__/__/____`  Responsável: `________`

## 1. Política de anúncios

- [ ] Nenhuma promessa de resultado sem prova ("venda o dobro", "+40%") [05, 11]
- [ ] Só funcionalidades que existem hoje e aparecem na demo [11]
- [ ] Nenhuma pergunta ou afirmação sobre atributo pessoal de quem vê (financeiro, idade etc.) [05]
- [ ] Nenhuma insinuação de parceria com órgão público (Detran, Senatran, Renave) [11]
- [ ] Menção a lei ou regulação revisada quanto a "temas sociais" na Meta [05]
- [ ] Preço, se citado, igual ao da página e com modelo de cobrança claro [11]
- [ ] Sem botão falso, imitação de notificação ou clickbait [11]

## 2. Medição

- [ ] Google Tag em todas as páginas; ação de conversão primária configurada [09, 10]
- [ ] Pixel da Meta ativo; eventos do navegador e da CAPI com mesmo `event_id` e `event_name` [03]
- [ ] Fila da CAPI enviando em menos de 7 dias [03]
- [ ] Clique para WhatsApp: `ctwa_clid` sendo gravado no CRM, ou registro de que só mediremos "conversa iniciada" [04]
- [ ] Formulário grava `gclid`/`gbraid`/`wbraid` e e-mail/telefone [09]
- [ ] Envio de conversões do CRM ao Google pelo Data Manager, dentro de 63 dias [09]
- [ ] Teste feito: um lead de teste aparece no Gerenciador de Eventos e no Google Ads

## 3. LGPD e consentimento

- [ ] Política de privacidade publicada, citando Meta e Google como destinatários [13]
- [ ] Banner de cookies com "Rejeitar" de mesmo destaque, padrão desligado [13]
- [ ] Modo de Consentimento ligado, padrão negado [10]
- [ ] Formulário com finalidade, link da política e caixa de consentimento não pré-marcada [13]
- [ ] Opt-in do WhatsApp registrado; instrução de saída nas mensagens de marketing [07, 13]
- [ ] E-mail e telefone com hash SHA-256 antes do envio [03, 09]

## 4. Página de destino

- [ ] No ar, abre em celular e desktop, sem "em construção" [11]
- [ ] Promessa do anúncio aparece na página [11]
- [ ] URL de exibição corresponde ao domínio real [11]
- [ ] Botão de WhatsApp e formulário funcionando
- [ ] Contato da empresa visível

## 5. Nomenclatura e estrutura

- [ ] Nome no padrão `GESCAR | Plataforma | Objetivo | Público | Região | C<n>` [estrutura-campanhas]
- [ ] Uma campanha = um objetivo; um conjunto por público [01]
- [ ] Google: grupos temáticos, 3 anúncios por grupo, negativas cadastradas [08]
- [ ] Região correta (MT no ciclo 1)
- [ ] Orçamento diário dentro da divisão do ciclo aprovada

## 6. Aprovação

- [ ] Orçamento do ciclo e o que esta ação consome dele
- [ ] Registro em `decisoes/log.md` com data, motivo e resultado esperado
- [ ] **Aprovação explícita do Edelson para esta ação** (publicar / ativar / pausar / orçamento)

Referências: [01](01-meta-estrutura-campanha.md) · [03](03-meta-conversions-api-e-deduplicacao.md) · [04](04-meta-clique-para-whatsapp-e-capi-mensagens.md) · [05](05-meta-politicas-de-anuncios.md) · [07](07-whatsapp-politicas-e-templates.md) · [08](08-google-estrutura-de-conta.md) · [09](09-google-conversoes-e-importacao-offline.md) · [10](10-google-modo-de-consentimento-e-tag.md) · [11](11-google-politicas-de-anuncios.md) · [13](13-lgpd-anuncios-formularios-whatsapp.md) · [estrutura-campanhas](estrutura-campanhas.md)
