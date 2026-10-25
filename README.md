# Credit Risk Intelligence

**Gestão de carteira, risco de crédito e inadimplência | Case de Analytics & MIS**

**[Explorar o dashboard interativo](https://matheusandrean.github.io/credit-risk-intelligence-web/)** · [Ver código-fonte](https://github.com/matheusandrean/credit-risk-intelligence-web)


Decisões de concessão, risco e cobrança não deveriam ser analisadas isoladamente. Uma carteira pode crescer em volume e, ao mesmo tempo, concentrar exposição em produtos mais arriscados, deteriorar sua qualidade ou exigir maior esforço de recuperação. O desafio está em conectar essas visões e dar contexto financeiro às métricas.

O **Credit Risk Intelligence** foi desenvolvido para simular esse ambiente de decisão. O projeto reúne a jornada de crédito — da proposta à liquidação ou baixa — em uma estrutura analítica orientada à gestão da carteira. A experiência pública permite explorar os indicadores por competência, produto e unidade federativa; o projeto técnico correspondente foi estruturado em Power BI Desktop.

> **Contexto:** trata-se de uma simulação de portfólio, com dados integralmente sintéticos. Os resultados não representam uma instituição financeira, uma carteira real ou o desempenho observado de qualquer empresa.

## O problema de negócio

Uma visão exclusivamente comercial pode celebrar o volume concedido sem evidenciar o risco assumido. Uma visão exclusivamente de cobrança, por outro lado, tende a enxergar o problema quando o atraso já se materializou. O objetivo deste case é aproximar essas leituras.

A pergunta que orienta o trabalho é:

**Como acompanhar crescimento, exposição e deterioração do crédito em uma visão coerente, capaz de apoiar a priorização de análises de risco e cobrança?**

Para respondê-la, o painel organiza três dimensões complementares: **originação** (entrada de risco), **carteira** (exposição e comportamento) e **recuperação** (pagamentos, cobranças e baixas). A análise por safra conecta essas dimensões ao tempo de maturação dos contratos.

## Escopo da simulação

| Dimensão | Recorte |
| --- | --- |
| Histórico | Novembro/2023 a outubro/2026 (36 competências) |
| Origem | Carteira e eventos gerados programaticamente; sem informações reais de clientes |
| Produtos | Crédito pessoal, consignado, financiamento de veículo e parcelado digital |
| Abrangência | 12 UFs sintéticas da base |
| Projeto analítico | Modelo dimensional e medidas no Power BI Desktop |
| Camada pública | Aplicação Web independente, alimentada por tabelas agregadas |

O conjunto original da simulação reúne aproximadamente **45 mil clientes, 70 mil contratos e 3,2 milhões de registros** distribuídos entre dimensões, propostas, parcelas, pagamentos, posições mensais e eventos de cobrança. Esses volumes se referem à base geradora do case — **não** à quantidade de linhas disponibilizadas no site público.

## Uma leitura possível da carteira

**Competência de referência: setembro/2026 · todos os produtos e UFs · valores simulados.**

| Indicador | Resultado | Interpretação |
| --- | ---: | --- |
| Exposição (EAD) | **R$ 416,7 mi** | Exposição financeira estimada no fechamento |
| Carteira D30+ / EAD | **19,99%** | Parcela da exposição com atraso a partir de 30 dias |
| Carteira D90+ / EAD | **1,42%** | Parcela da exposição com atraso a partir de 90 dias |
| Perda esperada (ECL) | **R$ 19,3 mi** | Estimativa sintética de perda da carteira |
| Aprovação de propostas | **80,37%** | 2.538 propostas aprovadas de 3.158 recebidas |

Nesse recorte, o **parcelado digital** responde por aproximadamente **7,5% da exposição**, mas por **21,7% da perda esperada simulada**. Isso não prova que o produto seja inadequado ou menos rentável: abre uma investigação sobre composição de risco, características de originação, distribuição dos atrasos e suficiência da precificação.

É esse o tipo de pergunta que o case procura tornar visível. O painel não substitui uma política de crédito; ele organiza evidências para que decisões e hipóteses possam ser discutidas com critérios claros.

## O que pode ser explorado no dashboard

| Visão | O que responde |
| --- | --- |
| **Visão executiva** | Como evoluem exposição, saldo, D30+, D90+ e ECL? Onde estão as principais concentrações? |
| **Carteira & risco** | Como o aging e os estágios de risco distribuem a exposição? Quais recortes demandam investigação? |
| **Originação** | Qual é o volume de propostas, a taxa de aprovação e o crédito concedido por produto? |
| **Análise de safras** | Como o atraso observado muda com o MOB e com a maturação de cada coorte? |
| **Cobrança & perdas** | Como evoluem recebimentos, ações, custos, valores atribuídos e write-offs? |
| **Metodologia** | Quais são as fórmulas, premissas e limitações que condicionam a leitura das métricas? |

Os filtros de **competência, produto e UF** atravessam as visões, permitindo comparar recortes da mesma carteira sem trocar a definição dos indicadores.

## Critérios de cálculo e cuidados de interpretação

O case separa deliberadamente **estoques** de **fluxos**. EAD, saldo e exposição vencida são fotografias de uma competência e não devem ser somados entre meses. Propostas, concessões, pagamentos e ações de cobrança representam movimentações do período.

- **D30+ e D90+:** exposição (EAD) de contratos com DPD ≥ 30 ou ≥ 90 dias, dividida pelo EAD total da competência.
- **Taxa de aprovação:** número de propostas aprovadas dividido pelo número de propostas analisadas no período.
- **ECL:** soma das perdas esperadas geradas no modelo sintético; não é um cálculo regulatório validado.
- **Vintage / MOB:** proporção de EAD em D30+ entre contratos observados na safra e no respectivo mês de vida; **não** é uma curva de default cumulativo.
- **Cobrança:** valores atribuídos a ações são proxies da simulação. Não medem causalidade nem recuperação incremental.

Um cuidado adicional: **outubro/2026 apresenta propostas, mas não registra novas aprovações ou concessões no recorte sintético**. Por isso, a competência é mantida para transparência da série, mas não deve ser interpretada isoladamente como uma decisão real de endurecimento da política de crédito. A leitura ilustrativa acima utiliza setembro/2026.

## Arquitetura do projeto

A solução tem duas camadas distintas:

**1. Modelo analítico — Power BI Desktop**  
Base geradora em Python; entidades de clientes, contratos, propostas, parcelas e eventos; modelo dimensional; medidas DAX; relatórios de originação, risco, safras e cobrança. O projeto Power BI é um artefato técnico separado, não hospedado neste repositório.

**2. Aplicação pública — Web estática**  
Exportação de agregados por competência, produto, UF e dimensões analíticas; interface em HTML, CSS e JavaScript; visualizações SVG, filtros globais e navegação entre as seis visões. O navegador recalcula os indicadores a partir dos agregados publicados em `assets/portfolio-data.json`.

A versão Web **não é um PBIX publicado ou incorporado pelo Power BI Service**. É uma implementação independente do relatório, preparada para acesso público sem licença de Power BI para os visitantes.

### Estrutura deste repositório

```text
index.html                 Interface e navegação
app.js                     Métricas, filtros e gráficos
styles.css                 Componentes e sistema visual
assets/portfolio-data.json Agregações públicas sintéticas
assets/favicon.svg        Identidade visual
README.md                 Contexto e documentação do case
```

Para executar localmente, na raiz do repositório:

```bash
python -m http.server 8000
```

Acesse `http://localhost:8000`. A aplicação é estática e pode ser hospedada no GitHub Pages, sem backend ou conta de usuário.

## Limites do exercício

O projeto demonstra estruturação de informações, raciocínio analítico e comunicação gerencial. **Não demonstra**, por si só, melhoria efetiva de inadimplência, aumento de recuperação ou superioridade de modelos preditivos.

Os saldos e pagamentos seguem regras da simulação e não equivalem necessariamente a um cronograma Price contabilmente exato. PD, LGD, EAD e ECL não foram calibrados para cumprir IFRS 9, CPC 48 ou regulamentação do Banco Central. Séries macroeconômicas usadas no material de origem são simuladas, não oficiais. A análise vintage pode sofrer viés de sobrevivência. Nenhum resultado deve ser usado para decisões reais de crédito.

---

**Matheus Marcondes**  
*Case independente de Analytics & MIS aplicado ao ciclo de crédito, risco e cobrança.*
