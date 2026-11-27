# 07 · Leitura e decisão (audit)

Tabela usada pelo agente no audit semanal e sempre que o lojista perguntar "como está?". **T** é o teto de CPL da loja (arquivo 06). Os números da tabela vivem em `ads_regras` e podem ser ajustados por loja.

## Antes de decidir

- Menos de 3 dias de veiculação ou gasto menor que 2 × T: **esperar**. O agente diz "ainda é cedo para concluir" e não propõe mudança de verba.
- Medição fraca (arquivo 05): decidir com cautela e dizer isso ao lojista.

## Tabela de decisão por anúncio ou campanha

| Situação | Decisão | Quem executa |
| --- | --- | --- |
| Gasto ≥ 2 × T, zero leads, 3 dias ou mais no ar | Pausar o anúncio | Automático, com aviso ao lojista |
| Veículo vendido no estoque do Gescar | Pausar o anúncio do veículo | Automático, com aviso |
| CPL até 0,7 × T e pelo menos 1 test drive na semana | Propor aumento de 20% a 30% | Lojista aprova |
| CPL entre 0,7 × T e T | Manter | Nada a fazer |
| CPL entre T e 1,5 × T | Propor novo criativo (mesmo modelo de campanha) | Lojista aprova a ativação do novo anúncio |
| CPL acima de 1,5 × T por 5 dias ou mais | Propor pausar e trocar de modelo ou de veículo | Lojista aprova |
| CPL bom, 10 leads ou mais e zero test drive em 14 dias | Problema de qualidade ou de atendimento: propor formulário de maior intenção e perguntar como os leads estão sendo atendidos | Lojista decide |
| Frequência acima de 3 em 7 dias **[HIPÓTESE]** | Público cansado: propor novo criativo ou raio maior | Lojista aprova |
| Anúncio reprovado | Explicar e propor correção (arquivo 04) | Lojista aprova |

## Conta inteira

| Situação | Decisão |
| --- | --- |
| 90% do teto mensal usado | Avisar o lojista e não propor nada que aumente gasto |
| 100% do teto mensal | Bloqueio pelo motor de regras; só o lojista muda o teto nas configurações |
| Todas as campanhas acima de T por 2 semanas | Parar de propor aumentos e marcar conversa com o lojista sobre preço, estoque e atendimento. O problema pode não ser o anúncio |

## Formato do audit semanal

1. Resumo de uma linha (arquivo 05).
2. O que funcionou e o que não funcionou, em até 3 frases.
3. Até 3 propostas, cada uma como cartão de aprovação, da mais importante para a menos.
4. Uma nota em `registrar_nota` com o aprendizado da semana.
