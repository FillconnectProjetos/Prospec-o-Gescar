# Gescar ADS, estrutura dos clientes

Esta pasta é o "cérebro" do agente Gescar ADS: o que ele sabe e como deve agir ao operar a conta Meta Ads de **cada revenda cliente do Gescar**. É ela que a IA de desenvolvimento do Gescar consome.

## Duas estruturas, nunca misturadas

| | Estrutura própria do Gescar | Estrutura dos clientes (esta pasta) |
| --- | --- | --- |
| Pasta | `trafego-pago/` | `gescar-ads-produto/` |
| Objetivo | Captar revendas para assinar o Gescar (B2B) | Vender os carros de cada revenda (B2C) |
| Conversões | WhatsApp, formulário, demonstração, assinatura | Lead, lead qualificado, test drive, proposta, venda |
| Quem aprova | Edelson | O lojista |
| Conta de anúncios | Conta do Gescar | Uma conta por lojista |

Compartilham só o método (plan → budget → audit), as regras de aprovação e a biblioteca de documentação oficial (`trafego-pago/docs/`). Metas, públicos, criativos e dados da estrutura própria **não** valem aqui.

## Camadas de treinamento do agente

| Camada | Onde fica | Quem escreve |
| --- | --- | --- |
| 1. Método e regras | `instrucoes-agente/system-prompt-v1.md` | Fillconnect |
| 2. Playbook automotivo | `playbook-automotivo/` | Fillconnect, calibrado no piloto |
| 3. Perfil da loja | Banco do Gescar (`ads_perfil_loja`) | Lojista no onboarding |
| 4. Memória da conta | Banco do Gescar (`ads_memoria_conta`) | Agente, revisado pela Fillconnect |
| 5. Referências agregadas | Banco do Gescar (`ads_benchmarks`) | Gescar calcula |

As camadas 1 e 2 são arquivos versionados aqui. As camadas 3 a 5 são dados e entram em cada conversa.

## Casos de teste

`casos-de-teste/` tem os cenários que provam que o agente se comporta como esperado. Regra: uma versão nova das instruções ou do playbook só vai para os lojistas se acertar **pelo menos 90%** dos casos e **todos** os casos marcados como segurança.

## Convenções

- **[HIPÓTESE]**: ponto de partida a validar no piloto. Não tratar como verdade.
- **[CONFIRMAR]**: checar na fonte oficial antes de implementar ou publicar.
- Toda mudança nas camadas 1 e 2 entra em `instrucoes-agente/CHANGELOG.md` com versão, data e motivo.

## Documentos de referência

- Especificação de produto: https://claude.ai/artifact/CF2NZkDFpDEDgdd3Qwf1es
- Documento técnico de migração: https://claude.ai/artifact/8hKfVRfxmMWRYk64kPEzQR
- Método padrão de tráfego Fillconnect: https://claude.ai/artifact/9stF4NGrHUmSUTt5Be7Xi1
