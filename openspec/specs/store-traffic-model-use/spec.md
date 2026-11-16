# store-traffic-model-use Specification

## Purpose
Define el uso previsto del modelo de pronóstico de tráfico y las condiciones de cierre del notebook entregable del TP.

## Requirements

### Requirement: Uso previsto con riesgos
La celda "✏️ Su respuesta — Etapa 5" SHALL indicar el uso del modelo, sus usuarios y la decisión concreta que apoya, y SHALL incluir al menos dos riesgos o limitaciones.

#### Scenario: Respuesta completa
- **WHEN** se lee la celda de respuesta de la Etapa 5
- **THEN** responde las cuatro preguntas de la plantilla, menciona que `RequestCountPerTarget` depende de la cantidad de targets sanos del *target group*, propone `RequestCount` como medida del tráfico total y no contiene "Reemplacen este texto por su respuesta"

### Requirement: Entregable cerrado y ejecutado
El notebook del primer intento exploratorio (`TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb`) SHALL tener todas las celdas de código ejecutadas en orden y sin errores, ninguna celda con el texto de plantilla y la lista de cierre marcada.

#### Scenario: Verificación final
- **WHEN** se ejecuta `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb`
- **THEN** termina con código 0, todas las celdas de código tienen `execution_count` consecutivo y salidas, y no hay ninguna aparición de "Reemplacen este texto por su respuesta" ni de `- [ ]`
