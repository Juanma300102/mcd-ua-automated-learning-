# Spec Delta

## MODIFIED Requirements

### Requirement: Respuestas y entregable ejecutado
Las cinco celdas de respuesta del notebook entregable SHALL citar cifras de la serie `RequestCount`, y el notebook SHALL quedar ejecutado de punta a punta sin errores.

#### Scenario: Ejecución final
- **WHEN** se ejecuta `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3.ipynb`
- **THEN** termina con código 0, sin errores en las celdas y sin el texto "Reemplacen este texto por su respuesta"

## REMOVED Requirements

### Requirement: Copia independiente del notebook
**Reason**: El análisis del ALB deja de ser una copia secundaria y pasa a ser el entregable con el nombre de la plantilla. El notebook por target cambia de nombre y recibe un aviso, así que ya no queda "sin cambios".
**Migration**: Lo reemplazan los requisitos "Notebook entregable con el nombre de la plantilla" y "Rol explícito de cada notebook".

## ADDED Requirements

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
