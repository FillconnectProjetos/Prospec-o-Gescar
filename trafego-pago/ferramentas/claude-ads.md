# Skill Claude Ads: revisão antes de instalar

Fonte: github.com/AgriciDaniel/claude-ads, licença MIT, commit fc3908e786c318776df89a3a098333da377364be (17/10/2026).

## O que foi verificado
- Os SKILL.md são instruções em texto; não executam código sozinhos.
- Chamadas de rede encontradas nos scripts:
  - `fetch_page.py` e `capture_screenshot.py`: buscam só a URL que o usuário pede para auditar.
  - `generate_image.py`: chama Gemini, OpenAI, Stability ou Replicate só se uma chave de API for configurada. Não usamos.
  - `audit_ecosystem_live.py`: API do GitHub, ferramenta de manutenção do autor. Não usamos.
- Nenhuma telemetria, nenhum envio de dados de conta para servidor de terceiros.

## O que foi instalado
Só os SKILL.md de que o projeto precisa, em `.claude/skills/`: ads-dna, ads-landing, ads-audit, ads-plan, ads-math,
ads-google, ads-meta. Os scripts Python não foram copiados. Licença em `.claude/skills/LICENSE-claude-ads`.

## Limite de uso
Sem os scripts e as referências do pacote completo, as skills servem como roteiro de análise em texto.
O fetch guardado do `ads-landing` e a pontuação determinística do `ads-audit` não estão disponíveis.
A análise de página é feita lendo o código do site no repositório do Gescar, e a auditoria de conta usa os dados dos conectores (Windsor/Meta).
Se algum dia precisarmos da pontuação automática, instalar o pacote completo no commit revisado.
