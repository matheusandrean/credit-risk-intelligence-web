# Credit Risk Intelligence | Portfolio Web

**Case interativo de inteligência de crédito, risco, inadimplência e cobrança.**

> **Projeto educacional com dados 100% sintéticos.** Não utiliza informações bancárias reais, não é afiliado a instituições financeiras e não é um relatório Power BI Service.

## O que o visitante encontrará

- **Visão executiva:** EAD, saldo principal, ECL, D30+ e D90+.
- **Carteira e risco:** exposição, faixas de atraso e estágios simulados.
- **Originação:** propostas, aprovação e concessões.
- **Safras (vintage):** evolução por coorte e meses de vida (MOB).
- **Cobrança e perdas:** pagamentos, ações de cobrança e baixas.
- **Metodologia:** transparência das premissas, fórmulas e limitações.

A aplicação foi construída em HTML, CSS e JavaScript puro, com tema visual roxo e filtros por competência, produto e UF. É independente do Power BI Service; o projeto técnico correspondente é mantido separadamente em Power BI Desktop.

## Publicação no GitHub Pages

O site foi preparado em um pacote `Credit_Risk_Intelligence_WEB_SITE_PUBLICAR.zip`. Para concluir a implantação:

1. **Descompacte** o ZIP em seu computador.
2. Na raiz deste repositório, clique em **Add file → Upload files**.
3. Arraste **os arquivos e a pasta `assets` descompactados**, não o ZIP. `index.html`, `app.js`, `styles.css` e `assets/portfolio-data.json` precisam ficar na raiz ou nos caminhos especificados.
4. Faça **Commit changes** na branch `main`.
5. Em **Settings → Pages**, selecione **Deploy from a branch → main → /(root) → Save**.
6. Aguarde a publicação e verifique o link informado pelo GitHub em **Settings → Pages**.

> Importante: não transfira dados corporativos, credenciais ou dados pessoais reais para este repositório público.

## Limitações

As métricas e cenários são simulações ilustrativas. Indicadores de risco e perdas esperadas não são modelos prudenciais ou contábeis calibrados; as curvas vintage têm limitações metodológicas. O case demonstra técnicas de analytics, não recomenda decisões de crédito.

## Tecnologia

Power BI Desktop (projeto analítico), Python (simulação/transformação) e HTML/CSS/JavaScript (interface pública).
