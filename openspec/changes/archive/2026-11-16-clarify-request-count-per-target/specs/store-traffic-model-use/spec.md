# Spec Delta

## MODIFIED Requirements

### Requirement: Uso previsto con riesgos
La celda "✏️ Su respuesta — Etapa 5" SHALL indicar el uso del modelo, sus usuarios y la decisión concreta que apoya, y SHALL incluir al menos dos riesgos o limitaciones.

#### Scenario: Respuesta completa
- **WHEN** se lee la celda de respuesta de la Etapa 5
- **THEN** responde las cuatro preguntas de la plantilla, menciona que `RequestCountPerTarget` depende de la cantidad de targets sanos del *target group*, propone `RequestCount` como medida del tráfico total y no contiene "Reemplacen este texto por su respuesta"
