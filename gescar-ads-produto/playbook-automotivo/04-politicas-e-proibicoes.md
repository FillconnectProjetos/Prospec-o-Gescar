# 04 · Políticas e proibições

Base: doc 05 (políticas da Meta) e doc 13 (LGPD) da biblioteca `trafego-pago/docs/`, mais o Código de Defesa do Consumidor. **Não é aconselhamento jurídico:** a lista abaixo é operacional e deve ser validada por advogado antes da Sprint 3, quando o agente começa a escrever anúncios.

## Bloqueios automáticos (o texto nem chega ao lojista)

| Proibido | Por quê | Alternativa que o agente oferece |
| --- | --- | --- |
| "Crédito aprovado garantido", "aprovação na hora", "sem consulta ao SPC/Serasa", "nome sujo aprovado" | Promessa enganosa e possível categoria de crédito na Meta | "Ajudamos você a simular o financiamento" |
| Perguntas ou afirmações sobre quem vê: "Está com nome sujo?", "Ganha pouco?", "Passou dos 50?" | Política de atributos pessoais da Meta (doc 05, item 2) | Falar do carro e do benefício |
| Preço diferente do estoque | Oferta anunciada obriga a loja (CDC) e gera reclamação | Puxar o preço do cadastro do veículo |
| Parcela sem condições completas ("só R$ 899 por mês") | Oferta de crédito ao consumidor exige informar preço à vista, taxa, número de parcelas e total **[CONFIRMAR com advogado]** | Anunciar o preço à vista ou "condições na loja" |
| "Sem entrada" quando não for verdade para todo cliente | Enganoso | "Entrada facilitada" só se a loja confirmar |
| Logo de montadora, de concorrente ou de banco | Propriedade intelectual (doc 05, item 5) | Só nome e modelo do veículo anunciado |
| Urgência falsa: "últimas horas", "só hoje" sem prazo real | Prática enganosa | Data real do feirão ou nada |
| Foto que não é do veículo anunciado | Enganoso | Foto real do Estúdio |
| Menção a Detran, Renave ou órgão público como parceiro | Insinuação de vínculo público e possível tema social na Meta | Não citar |

## Alertas (o agente avisa e o lojista decide)

| Situação | O que o agente diz |
| --- | --- |
| Anúncio fala de financiamento ou parcelas | "Esse anúncio pode ser classificado como crédito pela Meta, o que limita o público e atrasa a aprovação. Sugiro focar no carro." |
| Veículo com sinistro, leilão ou recuperado de financiamento | "Por lei e por confiança, isso precisa ficar claro no atendimento. Não recomendo esconder." **[CONFIRMAR obrigação de informar no anúncio]** |
| Comparação com concorrente | "Comparação direta com outra loja gera risco jurídico. Prefiro destacar o nosso diferencial." |

## Conta e dados

- Uma conta de anúncios por loja, ligada à empresa real dela (doc 05, item 10).
- Dados recebidos da Meta só em agregado, sem enriquecer ficha de cliente (doc 05, item 9).
- Formulário com aviso de finalidade, a loja como responsável pelos dados e link da política de privacidade da loja (doc 13).
- Lista de clientes para público personalizado: fora do piloto até haver consentimento registrado (doc 13).

## Anúncio reprovado

1. O agente lê o motivo da reprovação e explica ao lojista em uma frase.
2. Propõe a correção (editar gera anúncio novo e nova análise) ou o pedido de revisão, quando a reprovação parecer engano.
3. Registra em `registrar_nota` para não repetir o erro naquela loja.
