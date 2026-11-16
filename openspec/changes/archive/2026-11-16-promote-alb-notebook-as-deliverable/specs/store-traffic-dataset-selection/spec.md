# Spec Delta

## MODIFIED Requirements

### Requirement: Carga del CSV local
El notebook SHALL cargar `data/store-service-request-count-per-target-hourly-since-2026-05-01.csv` como único dataset, con una sola opción de carga activa, e interpretar `period_start_utc` y `period_end_utc` como fechas en UTC.

#### Scenario: Ejecución local desde la raíz del repositorio
- **WHEN** el notebook se ejecuta con `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb`
- **THEN** la celda de carga muestra las primeras filas, `df` tiene 3575 filas y 6 columnas, y `period_start_utc` tiene tipo `datetime64[..., UTC]`

#### Scenario: Ya no se usa el dataset de ejemplo
- **WHEN** se busca `load_dataset("penguins")` en celdas de código no comentadas
- **THEN** no hay coincidencias
