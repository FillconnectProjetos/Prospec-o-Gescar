# 09 · Google Ads: conversões, conversões otimizadas para leads e importação offline

| Fonte oficial | Lido em |
|---|---|
| [Sobre conversões otimizadas (answer/9888656)](https://support.google.com/google-ads/answer/9888656) | 09/11/2026 |
| [Conversões otimizadas para leads (answer/14101585)](https://support.google.com/google-ads/answer/14101585) | 09/11/2026 |
| [Sobre importação de conversões off-line (answer/2998031)](https://support.google.com/google-ads/answer/2998031) | 09/11/2026 |
| [Diretrizes de importação off-line (answer/15081888)](https://support.google.com/google-ads/answer/15081888) | 09/11/2026 |
| [Google Ads API: gerenciar conversões off-line](https://developers.google.com/google-ads/api/docs/conversions/upload-offline) | 09/11/2026 |
| [Data Manager API: migrar da Google Ads API](https://developers.google.com/data-manager/api/devguides/events/google-ads/offline/upgrade) | 09/11/2026 (página atualizada em 03/11/2026) |

## Resumo para o Gescar

**Conversões otimizadas** somam dados próprios com hash SHA-256 (e-mail, telefone, nome) às conversões, e o Google casa com contas Google logadas que interagiram com o anúncio. Há dois tipos: **para web** (conversão no site) e **para leads** (venda que acontece fora do site, mas começou num formulário do site). A segunda é exatamente o caso do Gescar: o lead preenche o formulário, a venda fecha depois no comercial.

**Importação offline** clássica usa o **GCLID**: o site guarda o ID do clique junto com o lead e, quando a venda sai, devolve ao Google. O próprio Google recomenda **começar por conversões otimizadas para leads** em vez da importação clássica.

**Prazos (confirmados na fonte oficial):**

- Importação por GCLID: conversões enviadas **mais de 90 dias** depois do último clique não entram.
- Conversões otimizadas para leads: enviadas **mais de 63 dias** depois do último clique não entram.
- Conversões importadas levam cerca de **3 horas** para aparecer.
- Reenviar o mesmo evento é seguro: o Google descarta duplicatas pelo identificador, nome, data e hora.

**Data Manager API (confirmado):** a fonte secundária estava certa. A documentação oficial informa:

- A partir de **15/06/2026**, o upload de conversões off-line e de conversões otimizadas para leads foi **migrado para a Data Manager API e bloqueado na Google Ads API**.
- Na API, chamadas de `UploadClickConversions` **falham** para tokens de desenvolvedor que não enviaram conversões off-line entre **17/12/2025 e 15/06/2026**. O Gescar não tinha esse histórico, logo **não pode usar a Google Ads API para isso**: o caminho é a **Data Manager API** (ou o Data Manager dentro da interface do Google Ads).
- Na interface, conversões otimizadas para leads aceitam **só arquivos do Data Manager**; formatos antigos precisam ser atualizados.
- A Data Manager API **não exige token de desenvolvedor**, usa cota por projeto do Google Cloud e um único método (`IngestEvents`) para envio e ajuste. Não permite retratar uma conversão, só reajustar o valor.

Boas práticas da documentação: enviar todos os identificadores de clique disponíveis (`gclid`, `gbraid`, `wbraid`) junto com os dados do usuário; normalizar e aplicar SHA-256 em e-mail e telefone; usar ID único da transação; informar o consentimento (`ad_user_data`) em cada conversão.

## Regras práticas (viram checklist)

- [ ] Formulário do site grava `gclid` (e `gbraid`/`wbraid`) e e-mail/telefone do lead no CRM.
- [ ] Ação de conversão primária no Google: **lead qualificado / demo agendada**, não só envio de formulário.
- [ ] Envio dos eventos do CRM pelo **Data Manager** (arquivo ou API). Não planejar integração nova com `UploadClickConversions`.
- [ ] Envio pelo menos semanal; nada pode passar de **63 dias** (conversões otimizadas para leads) ou **90 dias** (GCLID).
- [ ] Cada conversão leva o status de consentimento do lead (doc 10 e 13).
- [ ] Validar a importação pela coluna "Todas as conv. (por hora da conv.)" após ~3h.
