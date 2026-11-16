# Proposal

## Why

La Etapa 2 del notebook ya ejecuta `df.dtypes`, `df.info()` y `df.isna()` sobre el nuevo dataset, pero eso no alcanza para clasificar bien las variables de una serie temporal. No muestra que tres columnas son constantes, que `period_end_utc` es redundante, que la grilla horaria está completa ni que hay un período largo con valor 0 antes de la puesta en producción. La celda de respuesta sigue con el texto de plantilla.

## What Changes

- Se agrega, después de la celda de faltantes (`e1dcd988`), una celda de código de diagnóstico con: valores únicos por columna, filas duplicadas, verificación de que `period_end_utc - period_start_utc` es siempre 1 hora, completitud del índice horario y conteo de horas con valor 0 por período.
- Se completa la celda "✏️ Su respuesta — Etapa 2" (`7790a36f`). Cada columna se clasifica según la tabla de tipos del notebook, se identifica el target y se resume la calidad de los datos con cifras.
- El notebook se ejecuta en el mismo archivo y guarda las salidas.

## Capabilities

### New Capabilities
- `store-traffic-data-profiling`: identificación de tipos de variables, target y calidad de datos del dataset de tráfico horario dentro del notebook del TP.

### Modified Capabilities
<!-- ninguna -->

## Impact

- `TP_Analisis_de_Dataset_v3.ipynb`: una celda de código nueva y la celda `7790a36f`.
- Las celdas de plantilla `cde4df87` y `4fa3b9e2` siguen fallando hasta `explore-store-traffic-series`.
