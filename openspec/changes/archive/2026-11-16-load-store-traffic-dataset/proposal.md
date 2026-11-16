# Proposal

## Why

La Etapa 1 del notebook `TP_Analisis_de_Dataset_v3.ipynb` todavía carga el dataset de ejemplo `penguins` de seaborn y la celda de respuesta sigue con el texto de plantilla. Para resolver el TP con datos propios hay que cargar el CSV versionado en `data/` y justificar la elección. Esta etapa es la base de las cuatro siguientes, porque todas operan sobre el `df` que se define acá.

## What Changes

- La celda de carga (`cd405394`) deja de usar `sns.load_dataset("penguins")` y lee `data/store-service-request-count-per-target-hourly-since-2026-05-01.csv`. Las columnas `period_start_utc` y `period_end_utc` se interpretan como fechas en UTC.
- La carga es reproducible en los dos entornos previstos: localmente, con la ruta relativa desde la raíz del repositorio, y en Google Colab, donde se ofrece subir el archivo si no está en la ruta. Queda activa una única opción de carga, como pide la consigna.
- La celda de respuesta de la Etapa 1 (`bf9d70fd`) se completa con el nombre y la fuente del dataset y con una justificación de entre 2 y 4 líneas, respaldada por datos observables: cantidad de filas, rango de fechas y métrica.
- El notebook se ejecuta y guarda sus salidas en el mismo archivo.

## Capabilities

### New Capabilities
- `store-traffic-dataset-selection`: elección, carga y justificación del dataset de tráfico horario del servicio de tienda dentro del notebook del TP.

### Modified Capabilities
<!-- ninguna -->

## Impact

- Se edita `TP_Analisis_de_Dataset_v3.ipynb`: celdas `cd405394` y `bf9d70fd`, más las salidas guardadas.
- Se lee el CSV de `data/` sin modificarlo.
- Las celdas de plantilla de la Etapa 3 (`cde4df87`, que usa `bill_length_mm`, y `4fa3b9e2`, que usa `species`) van a fallar con el nuevo `df` hasta que se resuelva el cambio `explore-store-traffic-series`. Ver design.md.
- Depende del entorno uv ya archivado (`python-environment`).
