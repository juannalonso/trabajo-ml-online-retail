# Predicción de probabilidad de recompra — Online Retail II

Trabajo del módulo de Machine Learning del Máster.

## Objetivo

Construir un modelo de clasificación que prediga la probabilidad de que un 
cliente vuelva a comprar en una tienda retail online, con el fin de orientar 
acciones comerciales de **fidelización** (clientes con alta probabilidad) y 
**retención** (clientes con baja probabilidad).

## Dataset

[Online Retail II (UCI)](https://archive.ics.uci.edu/dataset/502/online+retail+ii): 
transacciones de un retailer online de regalos con sede en Reino Unido, entre 
diciembre 2009 y diciembre 2011. ~1M de transacciones, ~5.800 clientes únicos.

## Enfoque

- **EDA** completo (calidad de datos, distribuciones, estacionalidad, perfil 
  de clientes).
- **Limpieza** con criterios documentados (eliminación de nulos, cancelaciones, 
  ajustes contables, outliers).
- **Construcción del dataset cliente** con cutoff temporal (1-jun-2011):
  - Features RFM y derivadas a partir del histórico anterior al cutoff.
  - Target binario: ¿el cliente volvió a comprar en los 6 meses posteriores?
- **Modelado**: comparación de Regresión Logística, Random Forest y LightGBM.
- **Optimización** con GridSearchCV (5-fold CV).
- **Explicabilidad**: feature importance, coeficientes de la LR y análisis SHAP.

## Resultados

| Modelo | AUC en test |
|---|---|
| LightGBM tuneado | **0.789** |
| Regresión Logística | 0.781 |
| Random Forest tuneado | 0.778 |

Variable más predictiva: **recency_days** (días desde la última compra). 

## Contenido del repositorio

- `modelo_recompra_online_retail.ipynb` — Notebook completo (EDA + modelo).
- `README.md` — Este archivo.

## Autor

Juan Alonso
