
# PProductions — EDA e Modelagem IMDb (Vitória Freire)

Projeto de análise exploratória de dados (EDA) e modelagem preditiva usando o dataset do desafio (IMDb).
O notebook foi pensado para rodar **no Google Colab** e entrega:

* Uma EDA completa (qualidade de dados, correlações, hipóteses, visualizações);
* Respostas às perguntas do desafio (recomendação “universal”, fatores ligados a faturamento, insights de *Overview* e inferência de gênero);
* Pipeline de **modelagem de nota IMDb** (regressão): comparação de modelos, *GridSearch* no melhor, métricas OOF, resíduos, *learning curves*, SHAP, e **salvamento do modelo `.pkl`**;
* Relatórios (PDFs) e artefatos salvos automaticamente.

---

## ⚙️ Como executar (Google Colab — recomendado)
Este projeto foi construído e testado 100% no Google Colab. Para executá-lo:

Acesse o Colab pelo link: https://colab.research.google.com/

5. **Onde ficam os resultados**
   São gravados no seu Drive, em `MyDrive/eda_imdb_outputs`:

   ```
   eda_imdb_outputs/
   ├─ figs/         # figuras .png, .html (gráficos)
   ├─ artifacts/    # PDFs e CSVs gerados na EDA/modelagem
   │   ├─ Relatorio_EDA_VitoriaFreire.pdf
   │   ├─ Relatorio_Modelagem_VitoriaFreire.pdf
   │   ├─ dataset_processed.csv
   │   └─ modeling_summary_plus.json
   └─ models/
       └─ model_imdb_final.pkl   # modelo treinado
   ```

---

## 🧭 O que existe no projeto

* **Notebook principal**: `LH_CD_VitoriaFreire.ipynb`

  * **CÉLULA 1 — EDA**

    * Parsing/limpeza, qualidade de dados, correlações (Pearson/Spearman), testes (Shapiro, ANOVA/Kruskal, Cramér’s V, Spearman parcial), hipóteses, gráficos (Plotly/Matplotlib/Seaborn), respostas do desafio e **PDF executivo de EDA**.
  * **CÉLULA 2 — Modelagem**

    * *Feature engineering* (numéricas, categóricas, texto com TF-IDF+SVD), *ColumnTransformer* + *Pipeline*, **5 modelos** (ElasticNet, RandomForest, HistGBR, SVR, XGBoost), **CV estratificada por faixas de nota**, *GridSearch* no vencedor, resíduos OOF, *learning curves*, SHAP (se árvore/boosting), **previsão do caso “Shawshank”**, **.pkl** e **PDF técnico**.

* **Artefatos** (gerados ao rodar):

  * `artifacts/Relatorio_EDA_VitoriaFreire.pdf`
  * `artifacts/Relatorio_Modelagem_VitoriaFreire.pdf`
  * `models/model_imdb_final.pkl`
  * `artifacts/dataset_processed.csv` (dataset tratado para modelagem)



## Entregas (onde encontrar)

1. **EDA criativa + hipóteses**

   * Notebook, seção **“Análise de Qualidade de Dados”**, **“Análises Estatísticas”**, **“Hipóteses e Testes”** e **“Visualizações”**.
   * PDF: `artifacts/Relatorio_EDA_VitoriaFreire.pdf`.

2. **Qual filme recomendar para alguém genérico**

   * Notebook → seção **“Respostas às Perguntas do Desafio → 1) Recomendação ‘universal’”** (tabela + explicação).

3. **Principais fatores ligados a faturamento**

   * Notebook → seção **“2) Fatores de alta expectativa de faturamento”** (Spearman, quartis de receita, faturamento por gênero + leitura).

4. **Insights a partir de Overview + inferência de gênero**

   * Notebook → seção **“3) Overview → inferência de gênero (texto)”**

     * TF-IDF, *pipeline* de SVM, *cross-val*, *holdout*, matriz de confusão e métricas.

5. **Como prever a nota IMDb (regressão)**

   * Notebook → **CÉLULA 2 — MODELAGEM**

     * Problema: **regressão**
     * *Features* (numéricas, categóricas, texto), justificativas e transformações (StandardScaler, OHE, TF-IDF+SVD).
     * Comparação de **5 modelos** + baseline, **GridSearch** no melhor, **métrica principal: MAE** (com RMSE e R²), prós/Contras do modelo vencedor e *learning curves*.

6. **Previsão para Shawshank**

   * Notebook → **“inferência de exemplo (Shawshank)”**
   * Também aparece no **PDF de modelagem**.

7. **Modelo salvo em `.pkl`**

   * Gerado ao final da CÉLULA 2: `models/model_imdb_final.pkl`.

---



## Dúvidas comuns

* **“CSV não encontrado”**
  Confira o nome exato do arquivo (`desafio_indicium_imdb.csv`) e a pasta no Drive.
  Se usar outro nome/pasta, ajuste `CSV_PATH`.

* **Erro com `kaleido` ao salvar PNG do Plotly**
  O notebook tem *fallback* para HTML. Mesmo assim, no Colab costuma instalar normalmente.

* **Erro no SHAP**
  SHAP roda apenas para **modelos de árvore/boosting**. Se o melhor for linear (ex.: ElasticNet), o notebook pula essa parte com segurança.

Bibliotecas Utilizadas

pandas, numpy

matplotlib, seaborn, plotly

scipy, textblob

wordcloud, fpdf

sklearn, statsmodels

🧾 Relatório PDF

O notebook gera automaticamente um relatório executivo em PDF com os principais gráficos e insights. O arquivo é salvo no seu Google Drive ou na pasta outputs.

👩‍💻 Autora

Vitória Freire



---
