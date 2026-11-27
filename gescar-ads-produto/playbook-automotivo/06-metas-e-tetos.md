# 06 · Metas e tetos de cada loja

As metas saem da conta de cada loja, não de médias da internet. O agente calcula os tetos no onboarding, mostra a conta ao lojista e grava em `ads_perfil_loja`.

## Fórmula

```
custo máximo por venda = margem média por carro × parcela da margem para anúncio
teto de custo por lead (CPL) = custo máximo por venda × taxa de lead para venda
teto de custo por test drive = custo máximo por venda × taxa de test drive para venda
```

| Entrada | De onde vem | Sem dado, usar |
| --- | --- | --- |
| Margem média por carro | Lojista no onboarding ou relatório do Gescar | Obrigatório perguntar |
| Parcela da margem para anúncio | Lojista decide | 10% a 15% **[HIPÓTESE]** |
| Taxa de lead para venda | CRM do Gescar, últimos 90 dias | 2% **[HIPÓTESE]** até a loja ter 30 leads registrados |
| Taxa de test drive para venda | CRM do Gescar, últimos 90 dias | 20% **[HIPÓTESE]** |

## Exemplo

Loja com margem média de R$ 5.000 por carro, que aceita investir 12% da margem em anúncio, e converte 3% dos leads em venda:

- Custo máximo por venda: 5.000 × 12% = **R$ 600**
- Teto de CPL: 600 × 3% = **R$ 18**
- Teto por test drive (20% dos test drives viram venda): 600 × 20% = **R$ 120**

## Teto mensal

O lojista define o teto mensal. O agente confere se ele faz sentido:

```
teto mensal coerente ≈ vendas que a loja quer gerar por anúncio no mês × custo máximo por venda
```

Se o lojista quer 5 vendas vindas de anúncio com custo máximo de R$ 600 cada, o teto coerente é por volta de R$ 3.000. Se ele define R$ 600, o agente explica que a expectativa é cerca de 1 venda, sem tentar convencer a gastar mais.

## Verba diária inicial

- Mínimo de R$ 20 por dia por campanha **[HIPÓTESE]**: abaixo disso a Meta demora demais para aprender.
- Ponto de partida: entre 2 e 3 vezes o teto de CPL por dia, limitado ao teto mensal dividido pelos dias restantes.
- No exemplo acima: entre R$ 36 e R$ 54 por dia.

## Recalcular

- A cada 30 dias, com a taxa real de lead para venda da loja.
- Quando o lojista mudar margem ou parcela para anúncio.
- O agente mostra a mudança ao lojista e grava o novo teto só depois do aceite dele.
