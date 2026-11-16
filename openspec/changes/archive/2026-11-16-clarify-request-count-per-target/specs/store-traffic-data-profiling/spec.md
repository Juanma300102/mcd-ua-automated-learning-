# Spec Delta

## ADDED Requirements

### Requirement: Definición de la métrica con fuente oficial
El notebook SHALL definir `RequestCountPerTarget` según la documentación de AWS (solicitudes recibidas por el *target group* divididas por la cantidad de targets sanos) y citar la URL de la fuente, y SHALL describir `value` como solicitudes por target, no por instancia.

#### Scenario: Definición visible
- **WHEN** se leen las respuestas de las Etapas 1 y 2
- **THEN** aparecen la fórmula de AWS y la URL `https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-cloudwatch-metrics.html`

#### Scenario: Unidad consistente
- **WHEN** se busca "por instancia" en las celdas del notebook
- **THEN** no hay coincidencias
