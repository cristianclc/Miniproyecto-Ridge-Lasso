# Información del Proyecto

## Contexto

Craigslist alberga la colección más grande de vehículos usados en venta a nivel mundial, lo que representa una fuente de datos invaluable. Sin embargo, la naturaleza descentralizada y masiva de estos anuncios históricamente ha dificultado su recopilación y análisis unificado.

Para abordar este desafío, se construyó un *web scraper* como proyecto académico, el cual posteriormente se expandió para crear este conjunto de datos. El resultado es una recopilación que incluye **cada entrada de vehículo usado publicado dentro de Estados Unidos en Craigslist**, ofreciendo una vista sin precedentes del mercado de autos usados.

### Contenido y estructura

Los datos se extraen periódicamente (con una frecuencia esperada de actualización trimestral) y contienen casi toda la información relevante que Craigslist proporciona sobre las ventas de automóviles. El conjunto de datos principal es un archivo `vehicles.csv` de **1.45 GB** que incluye **26 columnas** con información como precio, condición, fabricante, coordenadas de geolocalización (latitud/longitud) y otras 18 categorías.


## Fuente de los datos

- **Autor:** Austin Reese
- **Plataforma:** Kaggle
- **Enlace de acceso:** [Used Cars Dataset en Kaggle](https://www.kaggle.com/datasets/austinreese/craigslist-carstrucks-data)

### Listado Completo de Variables

| Variable | Descripción | Tipo Relevante |
|:---|:---|:---|
| `id` | Identificador único del anuncio | Numérico (Clave) |
| `url` | URL directa del anuncio | Texto |
| `region` | Región de Craigslist donde se publicó | Categórica |
| `region_url` | URL de la región | Texto |
| `price` | **Precio de venta del vehículo (Target de regresión)** | Numérico |
| `year` | Año de fabricación del vehículo | Numérico |
| `manufacturer` | Marca del vehículo (ej. Ford, Toyota) | Categórica |
| `model` | Modelo específico del vehículo | Categórica (Alta cardinalidad) |
| `condition` | Condición reportada (ej. excelente, bueno) | Categórica |
| `cylinders` | Número de cilindros del motor | Categórica |
| `fuel` | Tipo de combustible (ej. gasolina, diesel) | Categórica |
| `odometer` | Millas recorridas (kilometraje) | Numérico |
| `title_status` | Estado del título de propiedad | Categórica |
| `transmission` | Tipo de transmisión (automático, manual) | Categórica |
| `VIN` | Número de Identificación del Vehículo | Texto (Alta cardinalidad) |
| `drive` | Tipo de tracción (4WD, FWD, RWD) | Categórica |
| `size` | Tamaño del vehículo (compacto, mediano, grande) | Categórica |
| `type` | Tipo genérico (camioneta, sedán, SUV) | Categórica |
| `paint_color` | Color exterior del vehículo | Categórica |
| `image_url` | URL de la imagen del anuncio | Texto |
| `description` | Descripción textual del anuncio | Texto |
| `county` | **Columna inútil (posible error)** | Sin valor |
| `state` | Estado de EE. UU. donde se cotiza | Categórica |
| `lat` | Latitud de la ubicación del anuncio | Numérico |
| `long` | Longitud de la ubicación del anuncio | Numérico |
| `posting_date` | Fecha de publicación del anuncio | Fecha/Hora |


## Objetivo general

Diseñar modelos supervisados de regresión y clasificación binaria utilizando técnicas de regresión lineal regularizada (Ridge, Lasso) y regresión logística, integradas en un flujo completo con `Pipeline` y búsqueda de hiperparámetros mediante `GridSearchCV`, con el propósito de:

1. **Estimar el precio de un auto usado** a partir de sus características (tarea de regresión).
2. **Clasificar si un vehículo está en alta demanda o baja demanda** (tarea de clasificación binaria).

### Objetivos específicos

| # | Objetivo Específico | Técnica asociada |
|:--|:---|:---|
| 1 | Implementar un pipeline de preprocesamiento que incluya codificación one-hot para variables categóricas y escalado estándar para variables numéricas. | `ColumnTransformer`, `OneHotEncoder`, `StandardScaler` |
| 2 | Entrenar y optimizar modelos de regresión Ridge y Lasso mediante `GridSearchCV` con validación cruzada (5 folds) para predecir el precio. | `Ridge`, `Lasso`, `GridSearchCV` |
| 3 | Entrenar y optimizar un modelo de Regresión Logística para clasificar la demanda alta/baja, donde `HighDemand` se define por encima de la mediana del precio. | `LogisticRegression`, `GridSearchCV` |
| 4 | Evaluar el desempeño de los modelos de regresión con métricas MAE, RMSE y R², y gráficos de valores predichos vs. reales. | `mean_absolute_error`, `mean_squared_error`, `r2_score` |
| 5 | Evaluar el desempeño del modelo de clasificación con matriz de confusión, accuracy, precisión, recall, F1-score, curva ROC y AUC. | `confusion_matrix`, `roc_curve`, `auc` |
| 6 | Comparar los modelos Ridge y Lasso para determinar cuál ofrece mejor capacidad de generalización con regularización. | Análisis comparativo de coeficientes y métricas |
| 7 | Identificar las variables más influyentes en la predicción del precio y en la clasificación de la demanda. | Interpretación de coeficientes |


## Consideraciones finales

El presente proyecto integrador aplica los conceptos fundamentales del aprendizaje automático supervisado a un problema del mundo real con alto valor práctico: la compra y venta de autos usados. A través de un enfoque estructurado que abarca desde la exploración inicial de los datos hasta la implementación de pipelines y la optimización de hiperparámetros, se busca no solo obtener modelos predictivos funcionales, sino también comprender las fortalezas y limitaciones de cada técnica empleada.

La elección de modelos lineales regularizados (Ridge, Lasso y Regresión Logística) responde al equilibrio entre interpretabilidad y rendimiento, aspectos clave en entornos comerciales donde entender *por qué* un modelo hace una predicción es tan relevante como la precisión de la misma. La integración de `Pipeline` y `GridSearchCV` garantiza un flujo de trabajo reproducible, profesional y alineado con las mejores prácticas de la industria.