# 04 · Meta: anúncios de clique para WhatsApp e Conversions API para Business Messaging

| Fonte oficial | Lido em |
|---|---|
| [Conversions API para Business Messaging (WhatsApp)](https://developers.facebook.com/documentation/ads-commerce/conversions-api/business-messaging) | 09/11/2026 |
| [Anúncios de clique para WhatsApp (Marketing API)](https://developers.facebook.com/documentation/ads-commerce/marketing-api/ad-creative/messaging-ads/click-to-whatsapp) | 09/11/2026 |

## Resumo para o Gescar

**Anúncio de clique para WhatsApp** abre a conversa com o Gescar direto no WhatsApp. Pode rodar com os objetivos Engajamento, **Cadastros**, Vendas ou Tráfego. Com **Cadastros**, a única otimização disponível é **CONVERSATIONS** (conversas iniciadas). O conjunto precisa do `page_id` no objeto promovido; o número de WhatsApp é opcional na API. Cobrança por impressão.

O problema: "conversa iniciada" não é "revenda qualificada". Para a Meta aprender quem vira demo e cliente, precisamos devolver o resultado da conversa pela **Conversions API para Business Messaging**:

- **Exige WhatsApp Business Platform**: Cloud API (recomendada) ou On-Premises (que já expirou em 23/10/2025, então na prática é **Cloud API**). O aplicativo WhatsApp Business (o do celular) não aparece como integração válida nessa página.
- Exige app de desenvolvedor com acesso avançado a `whatsapp_business_management` e `whatsapp_business_manage_events`, nível de acesso da Marketing API e login via Embedded Signup ou Facebook Login for Business.
- O dataset é criado a partir do ID da conta WhatsApp Business (WABA).
- Campos obrigatórios do evento: `action_source = business_messaging`, `messaging_channel = whatsapp`, `user_data.whatsapp_business_account_id` e **`user_data.ctwa_clid`**.
- O **ctwa_clid** vem no objeto `referral` do webhook de mensagens quando a conversa nasce de um anúncio. Tem que ser **guardado junto com a conversa** no CRM para ser enviado depois com a conversão.
- Eventos aceitos incluem `LeadSubmitted`, `QualifiedLead`, `Purchase`, entre outros.
- A Meta **não deduplica** esses eventos: a deduplicação é responsabilidade nossa.
- Só vale para o que acontece **dentro da conversa**. Conversão no site vai pela CAPI web (doc 03).

## Regras práticas (viram checklist)

- [ ] Antes de rodar clique para WhatsApp com otimização para resultado, decidir: número do Gescar está na **Cloud API**? Se não, a campanha só mede "conversa iniciada".
- [ ] Webhook grava `ctwa_clid` + telefone + data na ficha do lead no CRM, no primeiro contato.
- [ ] Quando o vendedor marca "qualificado", o CRM envia `QualifiedLead`; quando a demo é feita ou a assinatura fecha, envia o evento correspondente, sempre com o `ctwa_clid` original.
- [ ] Deduplicar no nosso lado antes de enviar (um evento por lead por etapa).
- [ ] Respeitar o limite de 7 dias do `event_time` (doc 03).
- [ ] Mensagem automática inicial informa que é o Gescar e oferece falar com pessoa (política do WhatsApp, doc 07).
