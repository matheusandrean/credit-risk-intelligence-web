# Credit Risk Intelligence — Case interativo público

Este repositório é um case de portfólio com **dados 100% sintéticos**, versão Web do painel desenvolvido no Power BI Desktop.

## Recursos

- Visão executiva da carteira e indicadores D30+, D90+ e ECL;
- Composição de atraso, estágios de risco, originação, aprovação, safras e cobrança;
- Filtros integrados de competência, produto e UF;
- Interface responsiva inspirada em paleta roxa (sem uso de logo ou associação à marca Nubank);
- HTML/CSS/JS puro: sem login, API privada, licença Power BI ou infraestrutura paga.

## Como publicar gratuitamente no GitHub Pages

1. Crie um repositório **público** novo no GitHub (`credit-risk-intelligence-web`).
2. Faça upload do **conteúdo desta pasta `site` na raiz** do repositório. Inclua `index.html`, `app.js`, `styles.css`, `assets/` e `.nojekyll`.
3. Vá em **Settings → Pages**, escolha **Deploy from a branch**, branch **main**, pasta **/(root)**, e salve.
4. Aguarde o fluxo de implantação do GitHub Pages e verifique a URL informada na seção Pages. NÃO assuma um endereço antes da implantação concluir.

Para teste local, na pasta contendo `index.html`, rode:

```sh
python -m http.server 8000
```

E abra `http://localhost:8000`.

## Fonte dos dados

Gerado a partir do pacote `Credit_Risk_Intelligence_v2_Nu_Style_COMPLETO.zip` pelo script `tools/build_public_data.py` (fornecido separadamente no pacote de autoria). O site publica apenas séries **agregadas** por mês/produto/UF/estágio/faixa de atraso/safra, não dados por cliente, contrato ou proposta.

Importante: agregação não torna informações reais automaticamente anônimas; neste projeto, todos os dados de origem já são sintéticos.

## Limitações

É uma simulação educacional. O cálculo de saldo pode divergir de um método amortizativo Price exato; PD, LGD, EAD e ECL são hipóteses sintéticas e não constituem modelos validados pelas normas contábeis ou prudenciais. As curvas vintage podem conter viés de sobrevivência. Indicadores de cobrança atribuída não implicam causalidade ou resultado incremental.

Este site **não é um PBIX publicado** e não se apresenta como tal. É uma visualização Web separada, construída a partir das mesmas bases.
