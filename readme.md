# Predicción de rentabilidades del S&P 500 con Regresión Lineal

Breve práctica de IA/ML para estimar el comportamiento del índice S&P 500 usando un modelo sencillo de regresión lineal a partir de datos históricos diarios.

## Objetivo
- Cargar y preparar los datos del S&P 500.
- Entrenar un modelo de regresión lineal para predecir el cierre (o la rentabilidad) a corto plazo.
- Evaluar el rendimiento con métricas básicas y visualizar resultados.

## Datos
- Archivo: `datos.csv`
- Contiene series diarias del S&P 500 con columnas típicas: `Date`, `Open`, `High`, `Low`, `Close`, `Volume`.
- Se pueden crear variables derivadas como rentabilidad diaria: 

$$r_t = \frac{\text{Close}_t - \text{Close}_{t-1}}{\text{Close}_{t-1}}$$

## Modelos implementados

### Modelo B: Regresión Lineal Simple
Entrenamiento con todo el conjunto histórico (división clásica train/test). Ajusta una única regresión lineal con todos los datos de entrenamiento y evalúa sobre el conjunto de prueba.

### Modelo C: Ventana Deslizante (Rolling Window)
Entrena el modelo repetidamente con ventanas temporales móviles de tamaño fijo. En cada iteración, usa los últimos $N$ días para entrenar y predice el siguiente día. Actualiza la ventana deslizándola en el tiempo. Captura mejor cambios recientes del mercado.

## Metodología (resumen)
1. Limpieza y conversión de `Date` a tipo fecha, orden por tiempo.
2. Generación de features simples (p. ej., rezagos de `Close` o de rentabilidad, medias móviles cortas/largas).
3. División entrenamiento/prueba respetando el orden temporal.
4. Entrenamiento de Regresión Lineal y evaluación ($\text{RMSE}$/$\text{MAE}$/$R^2$) sobre el conjunto de prueba.
5. Visualizaciones: serie real vs. predicha y dispersión predicción-real.

## Estructura
- `PL1.ipynb` y/o `cauderno.ipynb`: cuadernos con el flujo completo de análisis, entrenamiento y evaluación.
- `datos.csv`: datos de entrada.
- `enunciado.txt`: especificaciones de la práctica.

## Cómo ejecutar
1. Abrir el cuaderno `PL1.ipynb` en Jupyter/VS Code.
2. Ejecutar las celdas en orden (se instalarán/usarás librerías estándar como pandas, numpy, scikit-learn y matplotlib/plotly).
3. Revisa las métricas impresas y las gráficas para interpretar el desempeño.

## Resultados esperados
- Métricas de error razonables para un modelo lineal básico y gráficos que muestren la cercanía de las predicciones a los valores reales.
- Este es un punto de partida didáctico: se anima a probar más features, regularización (Ridge/Lasso) o modelos no lineales para mejorar.

## Notas
- El conjunto está orientado a aprendizaje; no se asume uso en producción ni consejos de inversión.
