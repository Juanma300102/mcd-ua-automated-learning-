# store-traffic-data-profiling Specification

## Purpose
Define cómo el notebook del TP identifica los tipos de variables, la variable objetivo y la calidad de los datos del dataset de tráfico horario del servicio de tienda.

## Requirements

### Requirement: Diagnóstico estructural de la serie
El notebook SHALL mostrar los valores únicos por columna, la cantidad de filas duplicadas, la duración de cada período y la completitud del índice horario entre el primer y el último `period_start_utc`.

#### Scenario: Columnas constantes
- **WHEN** se ejecuta la celda de diagnóstico
- **THEN** la salida muestra 1 valor único para `load_balancer`, `target_group` y `metric_name`

#### Scenario: Grilla horaria completa
- **WHEN** se compara el índice con un rango horario completo
- **THEN** la salida informa 0 horas faltantes, 0 timestamps duplicados y una duración única de 1 hora por período

### Requirement: Períodos con valor cero
El notebook SHALL contar las horas con valor 0 y separarlas en antes de la primera hora con tráfico y después de ella.

#### Scenario: Ceros antes y después del inicio
- **WHEN** se ejecuta la celda de diagnóstico
- **THEN** la salida informa la primera hora con valor positivo (2026-06-22 16:00 UTC), 1264 horas en cero antes de esa hora y 61 horas en cero después, todas entre el 22 y el 26 de junio

### Requirement: Clasificación y respuesta de la Etapa 2
La celda "✏️ Su respuesta — Etapa 2" SHALL clasificar cada columna con la tabla de tipos del notebook, identificar el target y resumir la calidad de los datos con cifras del propio notebook.

#### Scenario: Respuesta completa
- **WHEN** se lee la celda de respuesta de la Etapa 2
- **THEN** clasifica las 6 columnas, nombra `value` como variable a predecir en el tiempo y no contiene "Reemplacen este texto por su respuesta"

### Requirement: Definición de la métrica con fuente oficial
El notebook SHALL definir `RequestCountPerTarget` según la documentación de AWS (solicitudes recibidas por el *target group* divididas por la cantidad de targets sanos) y citar la URL de la fuente, y SHALL describir `value` como solicitudes por target, no por instancia.

#### Scenario: Definición visible
- **WHEN** se leen las respuestas de las Etapas 1 y 2
- **THEN** aparecen la fórmula de AWS y la URL `https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-cloudwatch-metrics.html`

#### Scenario: Unidad consistente
- **WHEN** se busca "por instancia" en las celdas del notebook
- **THEN** no hay coincidencias
