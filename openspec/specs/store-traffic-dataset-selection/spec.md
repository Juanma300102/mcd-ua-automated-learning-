# store-traffic-dataset-selection Specification

## Purpose
Define cómo el notebook del TP elige, carga y justifica el dataset de tráfico horario RequestCountPerTarget del servicio de tienda, de forma reproducible en local y en Colab.

## Requirements

### Requirement: Carga del CSV local
El notebook SHALL cargar `data/store-service-request-count-per-target-hourly-since-2026-05-01.csv` como único dataset, con una sola opción de carga activa, e interpretar `period_start_utc` y `period_end_utc` como fechas en UTC.

#### Scenario: Ejecución local desde la raíz del repositorio
- **WHEN** el notebook se ejecuta con `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb`
- **THEN** la celda de carga muestra las primeras filas, `df` tiene 3575 filas y 6 columnas, y `period_start_utc` tiene tipo `datetime64[..., UTC]`

#### Scenario: Ya no se usa el dataset de ejemplo
- **WHEN** se busca `load_dataset("penguins")` en celdas de código no comentadas
- **THEN** no hay coincidencias

### Requirement: Alternativa para Google Colab
Si el CSV no existe en la ruta relativa, el notebook SHALL ofrecer la subida del archivo con `google.colab.files` en lugar de fallar con un error genérico de archivo inexistente.

#### Scenario: Archivo ausente en Colab
- **WHEN** la celda de carga corre en Colab sin el CSV en `data/`
- **THEN** se abre el diálogo de subida y `df` se construye a partir del archivo subido

#### Scenario: Archivo ausente fuera de Colab
- **WHEN** la celda corre fuera de Colab y el CSV no existe
- **THEN** se lanza un `FileNotFoundError` que indica la ruta esperada

### Requirement: Justificación de la elección
La celda "✏️ Su respuesta — Etapa 1" SHALL indicar el nombre y la fuente del dataset y justificar la elección en 2 a 4 líneas, citando datos que el propio notebook muestra.

#### Scenario: Respuesta completa
- **WHEN** se lee la celda de respuesta de la Etapa 1
- **THEN** no contiene el texto "Reemplacen este texto por su respuesta" y menciona la métrica, la granularidad horaria y el rango de fechas del dataset
