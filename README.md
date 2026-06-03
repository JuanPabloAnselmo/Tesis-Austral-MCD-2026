# Tesis-Austral-MCD-2026

Este repositorio contiene las notebooks utilizadas para comparar estrategias de entrenamiento temporal en modelos de detección de fraude bajo escenarios con dinámica temporal y etiquetas tardías.

## Datasets utilizados

### 1. IEEE-CIS Fraud Detection

El dataset de IEEE-CIS se encuentra incluido en el repositorio como:

```text
ieee-fraud-detection.zip
```

La notebook correspondiente espera los archivos originales del dataset, principalmente:

```text
train_transaction.csv
train_identity.csv
```

### 2. BAF Variant IV

Dataset correspondiente a Bank Account Fraud Variant IV.

Descargar desde Kaggle:

[BAF Variant IV en Kaggle](https://www.kaggle.com/datasets/sgpjesus/bank-account-fraud-dataset-neurips-2022/data?select=Variant+IV.csv)

Archivo esperado:

```text
Variant_IV.csv
```

### 3. BAF Variant V

Dataset correspondiente a Bank Account Fraud Variant V.

Descargar desde Kaggle:

[BAF Variant V en Kaggle](https://www.kaggle.com/datasets/sgpjesus/bank-account-fraud-dataset-neurips-2022/data?select=Variant+V.csv)


Archivo esperado:

```text
Variant_V.csv
```

## Orden de ejecución

Las notebooks deben ejecutarse en el siguiente orden:

```text
1. NB_01_IEEE_CIS.ipynb
2. NB_02_BAF_Variant_IV.ipynb
3. NB_03_BAF_Variant_V.ipynb
4. NB_04_global_analysis.ipynb
```

Las primeras tres notebooks ejecutan los experimentos por dataset.
La cuarta notebook une los resultados y realiza el análisis estadístico global.

## Notebooks

### NB_01_IEEE_CIS.ipynb

Ejecuta el protocolo experimental sobre el dataset IEEE-CIS.

Genera resultados para las estrategias:

```text
STATIC
ALL_HISTORY
SLIDING_WINDOW
DECAY
DUAL_MODEL
```

### NB_02_BAF_Variant_IV.ipynb

Ejecuta el protocolo experimental sobre BAF Variant IV.

### NB_03_BAF_Variant_V.ipynb

Ejecuta el protocolo experimental sobre BAF Variant V.

### NB_04_global_analysis.ipynb

Carga los resultados generados por las tres notebooks anteriores y calcula:

```text
delta = metric_strategy - metric_ALL_HISTORY
```

La métrica principal es:

```text
Average Precision / AUC-PR
```

Además aplica:

```text
Friedman
Wilcoxon signed-rank pareado
Benjamini-Hochberg
Índice de dominancia pareada
Intervalos de confianza bootstrap
```

## Salidas esperadas

Cada notebook experimental genera un archivo de resultados con métricas por período, delay y estrategia.

La notebook global genera tablas y figuras finales para el análisis de tesis.

## Objetivo del análisis

El objetivo es evaluar si las estrategias adaptativas de actualización temporal superan a la estrategia ALL_HISTORY en escenarios de fraude con dinámica temporal y etiquetas tardías.

La comparación se realiza mediante deltas relativos dentro del mismo dataset, delay y período de evaluación, evitando comparar métricas absolutas entre datasets.

