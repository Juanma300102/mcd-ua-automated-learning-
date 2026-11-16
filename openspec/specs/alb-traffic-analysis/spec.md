# alb-traffic-analysis Specification

## Purpose

Define el notebook derivado que aplica el flujo del TP al tráfico total horario del ALB (RequestCount) y lo compara con la serie por target del servicio de tienda.

## Requirements

### Requirement: Carga del dataset RequestCount
La copia SHALL cargar `data/alb-request-count-hourly-since-2026-05-01.csv`, con la misma alternativa de subida para Colab y las fechas interpretadas en UTC.

#### Scenario: Carga local
- **WHEN** se ejecuta la celda de carga desde la raíz del repositorio
- **THEN** `df` tiene 3575 filas y 6 columnas, y `metric_name` vale `RequestCount`

### Requirement: Tipos y calidad propios de la nueva métrica
La Etapa 2 de la copia SHALL informar que `target_group` está completamente vacía, que `value` es entero y la cantidad de horas en 0 antes y después de la primera hora con tráfico, y SHALL explicar qué significa cada hallazgo.

#### Scenario: Columna vacía y valores enteros
- **WHEN** se ejecuta el diagnóstico de la Etapa 2
- **THEN** la salida muestra 3575 faltantes en `target_group`, 0 valores no enteros, la primera hora positiva 2026-06-22 14:00 UTC y 14 horas en 0 después de ella

### Requirement: EDA y propuesta recalculados
Las Etapas 3 y 4 de la copia SHALL recalcular la segmentación, los estadísticos, los perfiles, la autocorrelación y las líneas base sobre `RequestCount`, con los mismos criterios del notebook original.

#### Scenario: Criterio de período estable reutilizado
- **WHEN** se ejecuta la sección 3.0 de la copia
- **THEN** imprime la tabla semanal, el umbral del 90 % de la mediana y la fecha de inicio estable calculada para esta serie

### Requirement: Comparación con la serie por target
La copia SHALL calcular, en el período estable, el cociente horario `RequestCount / RequestCountPerTarget`, mostrar su distribución y su evolución en el tiempo, y advertir que aproxima la cantidad de targets solo si el ALB atiende un único *target group*.

#### Scenario: Cociente visible
- **WHEN** se ejecuta la sección de comparación
- **THEN** se imprimen la mediana, el mínimo y el máximo del cociente y se muestra un gráfico de su evolución

### Requirement: Respuestas y entregable ejecutado
Las cinco celdas de respuesta del notebook entregable SHALL citar cifras de la serie `RequestCount`, y el notebook SHALL quedar ejecutado de punta a punta sin errores.

#### Scenario: Ejecución final
- **WHEN** se ejecuta `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3.ipynb`
- **THEN** termina con código 0, sin errores en las celdas y sin el texto "Reemplacen este texto por su respuesta"

### Requirement: Notebook entregable con el nombre de la plantilla
El análisis del tráfico total del ALB SHALL vivir en `TP_Analisis_de_Dataset_v3.ipynb` como notebook entregable, y el análisis por target SHALL conservarse en `TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb` con sus cifras sin cambios.

#### Scenario: Nombres después del intercambio
- **WHEN** se listan los notebooks de la raíz del repositorio
- **THEN** existen `TP_Analisis_de_Dataset_v3.ipynb`, con `metric_name` igual a `RequestCount` en su salida de carga, y `TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb`, con `RequestCountPerTarget`

#### Scenario: Cifras del primer intento intactas
- **WHEN** se comparan las salidas de texto de `TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb` antes y después del cambio
- **THEN** son idénticas

### Requirement: Rol explícito de cada notebook
El notebook entregable SHALL presentarse como el análisis entregado y citar el análisis por target como "primer intento exploratorio" con su nombre de archivo, sin llamarlo "TP principal". El primer intento SHALL abrir con un aviso que indique que no es el entregable y enlace al notebook entregado.

#### Scenario: Sin referencias al "TP principal"
- **WHEN** se busca "TP principal" en las celdas de `TP_Analisis_de_Dataset_v3.ipynb`
- **THEN** no hay coincidencias, y aparece al menos una referencia a `TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb`

#### Scenario: Aviso en el primer intento
- **WHEN** se lee la segunda celda de `TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb`
- **THEN** indica que es un primer intento exploratorio, que no es el entregable, y menciona `TP_Analisis_de_Dataset_v3.ipynb`
