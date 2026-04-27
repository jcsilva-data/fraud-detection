fradu-detection
# Fraud Detection — IEEE-CIS Dataset

Detección de fraude en transacciones financieras usando el dataset IEEE-CIS (590k transacciones, ~3.5% fraude).

## Objetivo
Construir un pipeline completo de detección de fraude: EDA con narrativa de negocio, feature engineering, y modelo XGBoost optimizado para contexto bancario.

## Dataset
- [IEEE-CIS Fraud Detection — Kaggle](https://www.kaggle.com/c/ieee-fraud-detection)
- 590,540 transacciones | 434 features tras merge | Desbalance 96.5% / 3.5%

## Estructura
notebooks/
01_eda.ipynb          # Análisis exploratorio
02_feature_eng.ipynb  # Feature engineering
03_model.ipynb        # Modelo y evaluación

## Stack
Python · pandas · scikit-learn · XGBoost · matplotlib · seaborn