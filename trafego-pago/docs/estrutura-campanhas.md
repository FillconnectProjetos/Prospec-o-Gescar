# Modelo Gescar de estrutura de campanhas

Cada regra aponta para o doc de origem entre colchetes. O que é decisão nossa, e não regra de plataforma, está marcado como **[decisão Gescar]**.

> Nada aqui é publicado nem muda gasto sem aprovação do Edelson, ação por ação. Cada aprovação vira registro em `decisoes/log.md`.

## 1. Nomenclatura padrão

Formato (igual para campanha, conjunto/grupo e anúncio, acrescentando o nível):

```
GESCAR | Plataforma | Objetivo | Público | Região
```

| Campo | Valores permitidos |
|---|---|
| Plataforma | `META`, `GOOGLE` |
| Objetivo | `CADASTROS-WPP`, `CADASTROS-FORM`, `PESQUISA`, `REMARKETING` |
| Público | `DONOS-REVENDA`, `VISITANTES-30D`, `LEADS-SEM-DEMO`, ou o tema do grupo no Google (`SISTEMA-REVENDA`, `MARKETING-REVENDA`) |
| Região | `MT`, `MT-CUIABA`, depois `GO`, `MS` etc. |

Sufixos por nível **[decisão Gescar]**:

- Campanha: `GESCAR | META | CADASTROS-WPP | DONOS-REVENDA | MT | C1` (C1 = ciclo 1).
- Conjunto/grupo: acrescentar `| CJ-<variação>` (ex.: `CJ-INTERESSES`, `CJ-ABERTO`).
- Anúncio: acrescentar `| AD-<ângulo>-<formato>-v<n>` (ex.: `AD-ESTUDIO-IMG-v1`, `AD-RADAR-VID-v2`).

Regras:

- Sem acento, maiúsculas, separador ` | ` com espaço. Facilita filtro e leitura por API no Gescar ADS.
- O nome nunca muda depois de publicado; mudança de estratégia = novo item com novo `v<n>` [01: criativo não é editável].

## 2. Orçamento do ciclo 1: até R$500

A fonte única de orçamento e critério é o [`trafego-pago/README.md`](../README.md), mantido pela frente de plano de campanhas (branch `trafego-pago/plano-ciclo-1`, ainda não integrada à `main` quando este doc foi escrito). Se esse arquivo não existir na sua cópia, vale a tabela abaixo. Este modelo só aplica o que está lá. Na data deste doc:

| Ciclo | Período | Google | Meta | Total |
|---|---|---|---|---|
| 0 | até 20/11/2026 | Renave R$45/dia | n/a | ~R$500 |
| 1 | 21/11 a 20/12/2026 | R$348 (R$11,60/dia) | R$150 (limite de gasto da campanha, ~R$5,50/dia) | até R$498 |
| 2 | só se o ciclo 1 der resultado | R$650 | R$350 | R$1.000 |

Critério de "deu resultado" no ciclo 1: **3+ demonstrações realizadas, custo por demonstração até R$120 e custo por contato qualificado até R$60**. Se o README mudar, ele prevalece sobre esta tabela.

Remarketing na Meta: R$0 no ciclo 1 (público pequeno demais), liga a partir do ciclo 2.

## 3. Google: Pesquisa

- 1 campanha `GESCAR | GOOGLE | PESQUISA | DONOS-REVENDA | MT | C1` [08: separar campanha só quando muda orçamento ou região].
- Localização: Mato Grosso, "presença" (pessoas no local) **[decisão Gescar; conferir nome exato da opção na interface]**.
- Rede: só Pesquisa, sem parceiros nem Display no ciclo 1 **[decisão Gescar]**.
- Grupos temáticos [08: grupos por tema, estrutura consolidada]:
  - `SISTEMA-REVENDA`: sistema para revenda de veículos, software para garagem, gestão de loja de carros.
  - `MARKETING-REVENDA`: anúncio de carros para revenda, marketing para revenda de veículos, arte para venda de carros.
- 3 anúncios responsivos por grupo, com a palavra do tema no título [08].
- Correspondência: frase e exata no ciclo 1 + lista de negativas (grátis, curso, emprego, vaga, download, pirata) [08, ressalva nossa].
- Lance: **[decisão Gescar]** "Maximizar cliques" com limite de CPC no ciclo 1, porque o volume de conversões será baixo demais para Lances inteligentes aprenderem. Migrar para "Maximizar conversões" quando a conta tiver conversões validadas.
- Conversão primária: demo agendada / lead qualificado, enviada via Data Manager [09]. Envio de formulário como secundária.
- Consentimento e tag: Google Tag + Modo de Consentimento básico [10, 13].
- Anúncio e página sem promessa de resultado, preço claro [11].

## 4. Meta: Cadastros com WhatsApp

- 1 campanha `GESCAR | META | CADASTROS-WPP | DONOS-REVENDA | MT | C1`, objetivo **Cadastros** [02]. O rascunho atual em `meta/ciclo-1.md` usa **Engajamento** com destino WhatsApp: os dois otimizam para conversas [04]; a escolha final é do Edelson (ver doc 02).
- Local de conversão: WhatsApp (mensagem). Otimização: conversas [04].
- 1 conjunto por público [01]. Com R$150 no ciclo, **um conjunto só**, para não dividir aprendizado **[decisão Gescar]**:
  - `CJ-INTERESSES`: Mato Grosso, 25 a 60 anos, interesses de revenda e comércio de veículos com Advantage+ (como no rascunho `trafego-pago/meta/ciclo-1.md`).
- 2 a 3 anúncios no conjunto, um por ângulo (Estúdio, Radar, Copiloto) [01].
- Orçamento no conjunto [01].
- Resposta no WhatsApp em menos de 24h, para usar as 72h gratuitas [06].
- Primeira mensagem identifica o Gescar e oferece atendimento humano [07].
- Medição: se o número estiver na Cloud API, enviar `QualifiedLead` e demo com `ctwa_clid` pela CAPI de mensagens [04]. Se não estiver, a campanha mede só "conversa iniciada" e o relatório do ciclo precisa dizer isso.
- Texto sem atributo pessoal ("sua loja está no prejuízo?") [05].

## 5. Meta: Remarketing (ciclo 2 em diante)

- Campanha `GESCAR | META | REMARKETING | VISITANTES-30D | MT | C2`, objetivo Cadastros [02].
- Públicos: visitantes do site em 30 dias e leads sem demo, **somente de quem consentiu cookies de publicidade** [10, 13].
- Liga só se o público for grande o bastante para entregar; tamanho mínimo não foi lido: conferir no Gerenciador.
- Criativo diferente da prospecção: prova (demo em vídeo, depoimento real autorizado).

## 6. Fontes de cada regra

[01](01-meta-estrutura-campanha.md) · [02](02-meta-objetivos-e-advantage-leads.md) · [04](04-meta-clique-para-whatsapp-e-capi-mensagens.md) · [05](05-meta-politicas-de-anuncios.md) · [06](06-whatsapp-cloud-api-e-precos.md) · [07](07-whatsapp-politicas-e-templates.md) · [08](08-google-estrutura-de-conta.md) · [09](09-google-conversoes-e-importacao-offline.md) · [10](10-google-modo-de-consentimento-e-tag.md) · [11](11-google-politicas-de-anuncios.md) · [13](13-lgpd-anuncios-formularios-whatsapp.md)
