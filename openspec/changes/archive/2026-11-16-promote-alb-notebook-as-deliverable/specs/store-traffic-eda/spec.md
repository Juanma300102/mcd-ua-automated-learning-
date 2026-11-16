# Spec Delta

## MODIFIED Requirements

### Requirement: Plantillas no aplicables justificadas
Cada celda de plantilla que no aplica a una serie univariada SHALL reemplazarse, y su encabezado SHALL explicar por qué la herramienta original no corresponde.

#### Scenario: Ejecución sin errores
- **WHEN** se ejecuta `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb` sin `--allow-errors`
- **THEN** el comando termina con código 0
