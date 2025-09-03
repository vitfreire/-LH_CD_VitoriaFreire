

# PProductions — EDA e Modelagem IMDb (Vitória Freire)

Projeto de análise exploratória de dados (EDA) e modelagem preditiva da **nota IMDb** a partir do dataset do desafio da Indicium.
O desenvolvimento e a execução são focados no **Google Colab**, com geração automática de relatórios e artefatos.

---

## Acesso rápido ao notebook

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/vitfreire/-LH_CD_VitoriaFreire/blob/principal/LH_CD_VitoriaFreire2/LH_CD_VitoriaFreire2.ipynb)

> Alternativa via GitHub: abra este repositório → entre na pasta `lh_cd_vitoriafreire2/` → clique no arquivo **`LH_CD_VitoriaFreire2.ipynb`**. No topo da página do GitHub aparecerá o botão **“Open in Colab”**; clique para abrir no Colab e executar.

---

## O que há neste repositório

* `lh_cd_vitoriafreire2/LH_CD_VitoriaFreire2.ipynb` — notebook principal com **EDA** e **Modelagem**.
* `Relatorio_EDA_VitoriaFreire.pdf` — relatório executivo da EDA (exportado e incluído no repositório).
* `Relatorio_Modelagem_VitoriaFreire.pdf` — relatório técnico da modelagem (exportado e incluído no repositório).
* `modelo_imdb_final.pkl` — modelo final treinado (formato `.pkl`) incluído no repositório.
* `README.md` — este arquivo.

> Observação: quando executado no Colab, o notebook também salva os artefatos no seu Google Drive (estrutura detalhada abaixo).

---

## Como executar no Google Colab

**Pré-requisito**: ter o arquivo CSV do desafio no seu Google Drive com o nome `desafio_indicium_imdb.csv`.
Se usar outro nome ou pasta, ajuste a variável `CSV_PATH` no início da Célula 1 (EDA).

### Passo a passo

1. Abra o notebook pelo botão **Open in Colab** acima (ou via GitHub → pasta `lh_cd_vitoriafreire2` → arquivo `.ipynb` → **Open in Colab**).
2. No Colab, **execute a Célula 1 (EDA)** do início ao fim:

   * Montagem do Google Drive
   * Leitura e tratamento dos dados
   * Qualidade de dados, correlações, testes e visualizações
   * Respostas às perguntas do desafio
   * Geração do relatório **`Relatorio_EDA_VitoriaFreire.pdf`**
   * Salvamento do dataset tratado **`dataset_processed.csv`**
3. Em seguida, **execute a Célula 2 (Modelagem)**:

   * Usa o dataset tratado salvo na EDA
   * Pré-processamento (numéricas, categóricas e texto via TF-IDF + SVD)
   * Comparação de 5 modelos + baseline
   * GridSearch no melhor modelo
   * Métricas OOF, resíduos, learning curves e SHAP (se aplicável)
   * Previsão do caso **The Shawshank Redemption**
   * Geração do relatório **`Relatorio_Modelagem_VitoriaFreire.pdf`**
   * Salvamento do modelo final **`.pkl`**

> O notebook instala automaticamente as dependências no próprio ambiente do Colab (scikit-learn, xgboost, shap, fpdf2, kaleido, etc.).

---

## Saídas geradas ao rodar no Colab (Google Drive)

Os arquivos são gravados em `MyDrive/eda_imdb_outputs/`:

```
eda_imdb_outputs/
├─ artifacts/
│  ├─ Relatorio_EDA_VitoriaFreire.pdf
│  ├─ Relatorio_Modelagem_VitoriaFreire.pdf
│  ├─ dataset_processed.csv
│  └─ modeling_summary_plus.json
├─ figs/
│  └─ *.png / *.html (gráficos e figuras interativas)
└─ models/
   └─ model_imdb_final.pkl
```

> No repositório GitHub, já estão incluídos: `Relatorio_EDA_VitoriaFreire.pdf`, `Relatorio_Modelagem_VitoriaFreire.pdf` e `modelo_imdb_final.pkl`.

---

## O que o notebook faz (visão geral)

**Célula 1 — EDA**

* Parsing e limpeza;
* Qualidade de dados, faltantes e duplicatas;
* Correlações (Pearson/Spearman) e testes (Shapiro–Wilk, ANOVA, Kruskal–Wallis, Cramér’s V, Spearman parcial);
* Painel multivariado (nota, década, sentimento de sinopses, duração × nota);
* Respostas às perguntas do desafio (recomendação “universal”, fatores de faturamento, TF-IDF e SVM para inferir gênero);
* Relatório executivo em PDF.

**Célula 2 — Modelagem**

* Feature engineering (numéricas, categóricas, texto TF-IDF + SVD);
* `ColumnTransformer` + `Pipeline`;
* 5 modelos (ElasticNet, RandomForest, HistGradientBoosting, SVR, XGBoost) + baseline;
* CV estratificada por faixas de nota, GridSearch, métricas OOF, resíduos, learning curves;
* SHAP para modelos de árvore/boosting (quando aplicável);
* Previsão do caso **Shawshank**;
* Relatório técnico em PDF e salvamento do **`.pkl`**.

---

## Onde estão as respostas solicitadas no desafio

1. **EDA criativa + hipóteses**
   Notebook → seções “Análise de Qualidade de Dados”, “Análises Estatísticas”, “Hipóteses e Testes”, “Visualizações”.
   PDF: `Relatorio_EDA_VitoriaFreire.pdf`.

2. **Filme recomendado para uma pessoa desconhecida**
   Notebook → “Respostas às Perguntas do Desafio → 1) Recomendação ‘universal’”.

3. **Fatores relacionados à alta expectativa de faturamento**
   Notebook → “2) Fatores de alta expectativa de faturamento” (correlações de Spearman, quartis de receita, faturamento por gênero).

4. **Insights a partir de Overview e inferência de gênero**
   Notebook → “3) Overview → inferência de gênero (texto)” (TF-IDF, SVM, cross-validação, holdout, matriz de confusão).

5. **Como prever a nota IMDb (tipo de problema, variáveis e métricas)**
   Notebook → **Célula 2 — Modelagem** (regressão).
   Explica features e transformações; compara modelos; faz GridSearch; métricas (MAE principal, com RMSE e R²); prós e contras; learning curves.

6. **Previsão para o caso Shawshank**
   Notebook → “inferência de exemplo (Shawshank)” e no PDF de modelagem.

7. **Modelo salvo em `.pkl`**
   Arquivo final: `model_imdb_final.pkl` (também presente no repositório).

---


## Problemas comuns e soluções

* **“CSV não encontrado”**
  Garanta que o arquivo está em `MyDrive/desafio_indicium_imdb.csv`.
  Se estiver em outra pasta, ajuste `CSV_PATH` no início da Célula 1.

* **Falha ao exportar PNG de gráficos Plotly (`kaleido`)**
  O notebook possui *fallback* para HTML. Mesmo assim, `kaleido` é instalado sob demanda no Colab.

* **SHAP não aparece**
  Só é executado para modelos de árvore/boosting. Se o melhor for linear (ex.: ElasticNet), o bloco é ignorado com segurança.

---

## Reprodutibilidade

* Seeds fixas e dados processados salvos (`dataset_processed.csv`).
* Dependências instaladas sob demanda no próprio Colab.
* Os relatórios e figuras são gerados automaticamente a cada execução.

---

## Autoria

**Vitória Freire**
LinkedIn: [https://www.linkedin.com/in/vitoriafreiredev](https://www.linkedin.com/in/vitoriafreiredev)

---

