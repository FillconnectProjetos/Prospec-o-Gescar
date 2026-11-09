# 12 · Google Ads API (versão atual)

| Fonte oficial | Lido em |
|---|---|
| [Google Ads API](https://developers.google.com/google-ads/api) | 09/11/2026 |
| [Notas de versão](https://developers.google.com/google-ads/api/docs/release-notes) | 09/11/2026 |
| [Gerenciar conversões off-line](https://developers.google.com/google-ads/api/docs/conversions/upload-offline) | 09/11/2026 |
| [Blog oficial de desenvolvedores Google Ads](https://ads-developers.googleblog.com/) | 09/11/2026 (fonte do Google; usar para anúncios de mudança) |

## Resumo para o Gescar

- **Versão mais recente na data da leitura: v26.1, lançada em 28/10/2026.** Antes dela: v26 (14/10/2026) e v25.2 (23/09/2026). As datas de desativação ficam na tabela "Deprecation and sunset timetable", não lida nesta rodada.
- Foram três versões em cerca de cinco semanas, então qualquer integração do Gescar ADS deve prever atualização periódica.
- **Conversões off-line saíram da Google Ads API** (ver doc 09): para quem não tinha histórico, o caminho é a Data Manager API.
- A página de conversões off-line informa ainda que os **tokens de desenvolvedor** foram descontinuados em favor de projetos do Google Cloud, com encerramento em **09/09/2026**. **Confirmar na página de acesso da API antes de qualquer integração**, porque isso muda o processo de credenciamento.

Para o piloto atual, a API **não é necessária**: campanhas são montadas na interface, com aprovação do Edelson. A API só entra quando o Gescar ADS for automatizar leitura de relatórios e, no futuro, ações aprovadas pelo Copiloto.

## Regras práticas (viram checklist)

- [ ] Fase piloto: operação pela interface. Nenhuma escrita via API.
- [ ] Quando houver integração: usar a última versão estável e conferir o calendário de desativação a cada mês.
- [ ] Credenciamento: confirmar se ainda há token de desenvolvedor ou se o acesso é por projeto Google Cloud.
- [ ] Toda ação de escrita (criar, pausar, mudar orçamento) passa por aprovação humana registrada, regra do Copiloto.
