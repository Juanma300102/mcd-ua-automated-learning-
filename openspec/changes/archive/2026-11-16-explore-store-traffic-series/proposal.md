# Proposal

## Why

Las plantillas de la Etapa 3 suponen un dataset tabular: histograma de `bill_length_mm`, frecuencias de `species` y una matriz de correlación entre variables numéricas. Con la serie horaria, dos de esas celdas fallan con `KeyError`. La tercera produce una matriz de 1×1 que no dice nada, porque hay una sola variable numérica. La consigna pide aplicar las herramientas **adecuadas al tipo de datos**: para una serie temporal univariada eso significa segmentar períodos, ver la serie en el tiempo, estudiar la estacionalidad diaria y semanal, y medir la autocorrelación.

## What Changes

- Se agrega una sección "3.0 — Segmentación de la serie" (markdown y código) con los períodos sin tráfico, de puesta en marcha y estable. El inicio del período estable se determina con un criterio calculado, no a ojo. Se grafica la serie completa con los períodos sombreados y su media móvil de 7 días.
- 3.a: estadísticos descriptivos de `value` para el período activo y el estable, asimetría y valores atípicos por regla IQR.
- 3.b: histograma de `value` en el período estable, con media y mediana.
- 3.c: la tabla de frecuencias categórica se reemplaza por perfiles según variables de calendario derivadas: media por hora del día y por día de la semana. Se explica por qué la plantilla original no aplica.
- 3.d: la matriz de correlación se reemplaza por la autocorrelación en distintos rezagos y un mapa de calor día de la semana × hora. Se explica por qué.
- Se completa la respuesta de la Etapa 3 (`c0dd8462`) con entre 3 y 5 hallazgos, cada uno con cifras.
- El notebook queda ejecutado de punta a punta **sin errores**.

## Capabilities

### New Capabilities
- `store-traffic-eda`: análisis exploratorio de la serie horaria de tráfico del servicio de tienda dentro del notebook del TP.

### Modified Capabilities
<!-- ninguna -->

## Impact

- `TP_Analisis_de_Dataset_v3.ipynb`: celdas `5a89a83f`, `1ba7626e`, `cde4df87`, `dc5d2712`, `4fa3b9e2`, `cdd2827e`, `7c1e2311` y `c0dd8462`, más dos celdas nuevas de la sección 3.0.
- Se resuelven los dos errores que quedaron pendientes de las etapas 1 y 2.
