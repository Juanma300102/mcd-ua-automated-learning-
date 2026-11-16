# store-traffic-eda Specification

## Purpose
Define el análisis exploratorio que el notebook del TP aplica a la serie horaria de tráfico del servicio de tienda, con herramientas adecuadas a una serie temporal univariada.

## Requirements

### Requirement: Segmentación de períodos con criterio explícito
El notebook SHALL separar la serie en período sin tráfico, puesta en marcha y período estable. El inicio del período estable SHALL ser el primer lunes cuya media semanal alcance el 90 % de la mediana de las medias semanales del período activo.

#### Scenario: Inicio del período estable
- **WHEN** se ejecuta la celda de segmentación
- **THEN** imprime la tabla de medias semanales, el umbral y la fecha de inicio del período estable (2026-07-13)

#### Scenario: Serie en el tiempo
- **WHEN** se ejecuta la celda de segmentación
- **THEN** muestra un gráfico de la serie completa con los períodos sombreados y la media móvil de 7 días, con una sola escala vertical

### Requirement: Distribución y estadísticos
El notebook SHALL mostrar los estadísticos descriptivos de `value` para el período activo y el estable, la asimetría, la cantidad de atípicos según la regla IQR y un histograma del período estable con media y mediana.

#### Scenario: Comparación activo frente a estable
- **WHEN** se ejecuta la celda 3.a
- **THEN** la salida muestra `describe()` en dos columnas (activo y estable), la asimetría de cada período y la cantidad de atípicos del estable

### Requirement: Estacionalidad diaria y semanal
El notebook SHALL mostrar la media de `value` por hora del día y por día de la semana en el período estable, y un mapa de calor día × hora.

#### Scenario: Perfil diario
- **WHEN** se ejecuta la celda 3.c
- **THEN** se muestran el perfil por hora (con la banda entre los percentiles 25 y 75) y el perfil por día de la semana, y se imprimen la hora de mínimo y la de máximo

### Requirement: Dependencia temporal
El notebook SHALL medir la autocorrelación de la serie estable en rezagos de 1 a 168 horas y destacar los rezagos de 1, 24 y 168.

#### Scenario: Autocorrelación
- **WHEN** se ejecuta la celda 3.d
- **THEN** se grafican las autocorrelaciones y se imprimen los valores en los rezagos 1, 24 y 168

### Requirement: Plantillas no aplicables justificadas
Cada celda de plantilla que no aplica a una serie univariada SHALL reemplazarse, y su encabezado SHALL explicar por qué la herramienta original no corresponde.

#### Scenario: Ejecución sin errores
- **WHEN** se ejecuta `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb` sin `--allow-errors`
- **THEN** el comando termina con código 0

### Requirement: Hallazgos de la Etapa 3
La celda "✏️ Su respuesta — Etapa 3" SHALL listar entre 3 y 5 hallazgos, cada uno con al menos una cifra que el notebook muestra.

#### Scenario: Respuesta completa
- **WHEN** se lee la celda de respuesta
- **THEN** no contiene "Reemplacen este texto por su respuesta" y cada hallazgo cita una cifra
