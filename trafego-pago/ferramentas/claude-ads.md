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
