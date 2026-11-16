# Design

## Context

`df` ya llega con las fechas en UTC (ver la spec `store-traffic-dataset-selection`). En una inspección previa con pandas se observó: 0 NaN; 0 filas duplicadas; `period_end_utc - period_start_utc` igual a 1 hora en todas las filas; 1131 valores con decimal `.5`. Los decimales son coherentes con que la métrica es un promedio por *target*: `Sum` de solicitudes dividido por la cantidad de instancias.

## Goals / Non-Goals

**Goals:**
- Que la clasificación de cada columna esté respaldada por una salida visible del notebook.

**Non-Goals:**
- Visualizaciones y estadísticas de distribución, que corresponden a la Etapa 3.

## Decisions

- **Una sola celda nueva de diagnóstico, en lugar de modificar las celdas de plantilla.** Criterio: las celdas `fdf2e613`, `170cdd77` y `e1dcd988` de la consigna siguen siendo válidas para cualquier dataset. Lo específico de una serie temporal se agrega en una celda aparte, con comentarios que explican cada chequeo.
- **`value` se clasifica como numérica continua** aunque se origine en un conteo. Criterio: es un promedio por instancia (aparecen valores `x.5`), así que no es un entero discreto.
- **El target es `value` en el futuro, es decir, un problema de pronóstico.** Criterio: no hay una columna de etiqueta. Las únicas variables informativas son el tiempo y el propio valor. Las columnas constantes no aportan información.

## Risks / Trade-offs

- [Un lector podría tomar los ceros como faltantes] → La celda separa los ceros anteriores al primer tráfico, que corresponden a un servicio todavía sin uso, de los 61 ceros de la semana de puesta en marcha. La respuesta explica la diferencia.
