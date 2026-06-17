# Fraud Detection — IEEE-CIS Dataset

Pipeline completo de detección de fraude en transacciones financieras, orientado
a un contexto bancario. Este es un proyecto de portafolio para roles de Data Scientist.

## Resultados

Modelo usado: **LightGBM** tuneado con RandomizedSearchCV (TimeSeriesSplit) —
AUC-ROC **0.9036** / PR-AUC **0.5026**, sobre un baseline de AUC-ROC 0.8959 / PR-AUC 0.4891.

Hallazgo clave (SHAP): el monto de la transacción (`TransactionAmt`)
es la variable más relevante, seguido de variables de conteo que fueron previamente anonimizdas por el dueño del dataset (`C*`) y
`R_emaildomain`. Dominios de correo poco comunes, un ejemplo de ello es protonmail.com, con un ~46% tasa de fraude, lo que indica una señal muy fuerte de riesgo.

## Dataset

[IEEE-CIS Fraud Detection — Kaggle](https://www.kaggle.com/c/ieee-fraud-detection)
590,540 transacciones · 403 features finales tras feature engineering · Desbalance ~96.5% / 3.5% fraude

> Los archivos CSV no están incluidos en el repositorio. Descárgalos desde Kaggle
> y ubícalos en la carpeta `data/`.

## Estructura

```
fraud-detection/
├── data/                          # Dataset local (no incluido en el repo)
├── 01_EDA.ipynb                   # Análisis exploratorio con narrativa de negocio
├── 02_features.ipynb              # Feature engineering: encoding, split temporal
├── 03_model_comparison.ipynb      # Baseline: Random Forest vs XGBoost vs LightGBM
├── 04_model_final.ipynb           # Tuning, SHAP, conclusiones del modelo ganador
└── README.md
```

## Pipeline

1. **EDA** — patrones de fraude por monto, dispositivo, tipo de tarjeta y producto.
2. **Feature engineering** — encoding ordinal/binario, target encoding de dominios de correo, split temporal (no aleatorio, para evitar leakage).
3. **Comparación de modelos** — tres baselines con hiperparámetros conservadores; LightGBM elegido por mejor AUC-ROC y ~6x más rápido que Random Forest.
4. **Modelo final** — tuning con RandomizedSearchCV + TimeSeriesSplit, interpretabilidad con SHAP.

## Decisiones técnicas relevantes

- Split temporal en lugar de aleatorio: simula cómo un banco recibe transacciones en producción.
- Se detectó y corrigió un data leak por `TransactionID` filtrado accidentalmente, además se confirmó que no aportaba relevancia real al reentrenar sin él.
- `scale_pos_weight` se calcula desde la distribución real de clases para manejar el desbalance.

## Stack

Python · pandas · scikit-learn · XGBoost · LightGBM · SHAP · matplotlib · seaborn