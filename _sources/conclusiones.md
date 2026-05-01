# Conclusiones del Proyecto


## Cumplimiento de objetivos

El proyecto logró satisfactoriamente los dos objetivos principales:

| Objetivo | Estado | Resumen |
|----------|--------|---------|
| Predicción del precio (regresión) | Cumplido | Modelos Ridge y Lasso con R² ≈ 0.68 y MAE ≈ $4,300 |
| Clasificación de demanda (clasificación binaria) | Cumplido | Regresión Logística con Accuracy ≈ 85% y AUC = 0.93 |


### Comparación de modelos de regresión: Ridge vs. Lasso

| Aspecto | Ridge | Lasso |
|---------|-------|-------|
| R² | 0.6829 | 0.6828 |
| MAE | $4,301 | $4,294 |
| RMSE | $6,357 | $6,358 |
| **Veredicto** | Equivalente | Equivalente |

**Conclusión sobre regularización:**  
No existe una ventaja práctica de Lasso sobre Ridge en este dataset. Lasso no logró reducir coeficientes a cero de manera significativa, lo que sugiere que todas las variables seleccionadas aportan información relevante para la predicción del precio. Ambos modelos presentan el mismo patrón de heterocedasticidad: **mayor error en vehículos de alto precio** (>$60,000).


### Evaluación del modelo de clasificación

La Regresión Logística demostró un **desempeño sobresaliente** en la clasificación binaria de demanda alta vs. baja:

- **AUC = 0.93**: Capacidad de discriminación excelente.
- **Accuracy = 85.4%**: Acierto global muy alto.
- **F1-Score = 0.85**: Balance óptimo entre precisión y recall.

**Conclusión:** El modelo es confiable para aplicaciones operativas como priorización de inventario, fijación de precios dinámica y planificación de recursos. La definición de `HighDemand` basada en la mediana del precio generó clases naturalmente balanceadas, lo que facilitó el aprendizaje.

---

## Análisis de la regularización

La implementación de `GridSearchCV` con validación cruzada (5 folds) permitió encontrar los valores óptimos de hiperparámetros:

- **Ridge / Lasso** (alpha óptimo): Valor que equilibra el sesgo y la varianza, evitando sobreajuste sin perder poder predictivo.
- **Regresión Logística** (C óptimo): Inverso de la fuerza de regularización que maximizó el AUC y el F1-Score.

**¿Mejoró la regularización la capacidad de generalización?**  
Sí. La validación cruzada aseguró que los hiperparámetros seleccionados no estuvieran sobrescritos a los datos de entrenamiento. Esto se refleja en métricas de prueba consistentes (sin caídas drásticas respecto a validación), lo que indica **buena capacidad de generalización** en ambos modelos.


## Limitaciones del proyecto

1. **Alta cardinalidad no resuelta:** La variable `model` no pudo ser completamente explotada debido a su naturaleza (9,530 categorías).

2. **Heterocedasticidad en regresión:** Los modelos de regresión tienen mayor error en el segmento de autos de lujo (>$60,000). Esto podría mitigarse con:
   - Transformación logarítmica de `price`.
   - Modelos separados por segmento de precio.
   - Incorporación de características adicionales (opciones, equipamiento, historial de mantenimiento).

3. **Exclusión de `posting_date`:** No se utilizó información temporal (estacionalidad de precios), lo que podría añadir valor predictivo en futuras iteraciones.

## Conclusión final

El proyecto demuestra que es posible construir modelos predictivos útiles para plataformas de compra-venta de autos usados utilizando técnicas de regularización lineal y regresión logística. Si bien la tarea de **clasificación de demanda resultó sobresaliente (AUC 0.93)** , la **predicción de precios (R² 0.68)** deja margen de mejora, especialmente en el segmento de vehículos de alto valor. La implementación rigurosa de `Pipeline` y `GridSearchCV` asegura la reproducibilidad y validez de los resultados, cumpliendo con los estándares profesionales de aprendizaje automático supervisado.