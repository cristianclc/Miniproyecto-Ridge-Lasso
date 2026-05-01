# Predicción y Clasificación de Autos Usados

## Descripción del Proyecto

Este proyecto tiene como objetivo analizar y modelar el mercado de vehículos usados en Estados Unidos utilizando datos provenientes de Craigslist. A través de técnicas de aprendizaje automático supervisado, se desarrollan modelos capaces de:

- Predecir el precio de un vehículo usado.
- Clasificar si un vehículo tiene alta o baja demanda.

El enfoque incluye un flujo completo de ciencia de datos: desde la adquisición y procesamiento de datos hasta la construcción, optimización y evaluación de modelos.

## Colaboradores

- Cristian Linero
- David Márquez


## Dataset

- **Fuente:** Kaggle  
- **Autor:** Austin Reese  
- **Enlace:** https://www.kaggle.com/datasets/austinreese/craigslist-carstrucks-data

## Objetivos

### Objetivo General

Diseñar modelos supervisados de regresión y clasificación utilizando técnicas de regularización e integrados en pipelines optimizados con validación cruzada.

### Objetivos Específicos

1. Implementar un pipeline de preprocesamiento:
   - `ColumnTransformer`
   - `OneHotEncoder`
   - `StandardScaler`

2. Entrenar modelos de regresión:
   - Ridge
   - Lasso
   - Optimización con `GridSearchCV`

3. Construir modelo de clasificación:
   - Regresión Logística
   - Clasificación de demanda (HighDemand vs LowDemand)

4. Evaluar modelos de regresión:
   - MAE
   - RMSE
   - R²
    
5. Comparar modelos Ridge vs Lasso

6. Evaluar modelo de clasificación:
   - Accuracy
   - Precisión
   - Recall
   - F1-score
   - Curva ROC y AUC

## Metodología

El proyecto sigue un flujo estructurado:

1. Recolección de datos.
2. Limpieza y preprocesamiento.
3. Ingeniería de características.
4. Construcción de pipelines.
5. Entrenamiento de modelos.
6. Optimización de hiperparámetros (GridSearchCV).
7. Evaluación y comparación de modelos.
8. Interpretación de resultados.
