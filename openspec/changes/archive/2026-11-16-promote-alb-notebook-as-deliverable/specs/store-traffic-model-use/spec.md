# Spec Delta

## MODIFIED Requirements

### Requirement: Entregable cerrado y ejecutado
El notebook del primer intento exploratorio (`TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb`) SHALL tener todas las celdas de código ejecutadas en orden y sin errores, ninguna celda con el texto de plantilla y la lista de cierre marcada.

#### Scenario: Verificación final
- **WHEN** se ejecuta `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb`
- **THEN** termina con código 0, todas las celdas de código tienen `execution_count` consecutivo y salidas, y no hay ninguna aparición de "Reemplacen este texto por su respuesta" ni de `- [ ]`
