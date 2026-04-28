# Fraud Detection — IEEE-CIS Dataset

Pipeline completo de detección de fraude en transacciones financieras, orientado 
a contexto bancario. Desarrollado como proyecto de portafolio para roles de 
Data Scientist en el sector financiero colombiano.

## Objetivo

Identificar patrones de fraude en 590,540 transacciones reales de comercio 
electrónico, cubriendo el ciclo completo: exploración con narrativa de negocio, 
feature engineering, y modelo de clasificación optimizado para datos desbalanceados.

## Dataset

[IEEE-CIS Fraud Detection — Kaggle](https://www.kaggle.com/c/ieee-fraud-detection)  
590,540 transacciones · 434 features tras merge · Desbalance 96.5% / 3.5% fraude

> Los archivos CSV no están incluidos en el repositorio. Descárgalos directamente 
> desde Kaggle y ubícalos en la carpeta `data/`.

## Estructura

fraud-detection/
├── data/                        # Dataset local (no incluido en el repo)
├── notebooks/
│   ├── 01_EDA.ipynb             # Análisis exploratorio con narrativa de negocio ✅
│   ├── 02_feature_eng.ipynb     # Feature engineering (en progreso)
│   └── 03_model.ipynb           # Modelo y evaluación (pendiente)
└── README.md

## Hallazgos del EDA

- Solo el **3.5%** de las transacciones son fraudulentas — desbalance severo que 
  requiere estrategia de balanceo y evaluación con AUC-ROC
- Las transacciones fraudulentas tienen un monto promedio mayor ($149 vs $134)
- Los dispositivos **móviles** presentan una tasa de fraude ~1.5x mayor que desktop
- La categoría **C** de ProductCD concentra la tasa de fraude más alta
- La tarjeta **Discover** lidera en tasa de fraude entre los tipos de tarjeta

## Stack

Python · pandas · scikit-learn · XGBoost · matplotlib · seaborn
