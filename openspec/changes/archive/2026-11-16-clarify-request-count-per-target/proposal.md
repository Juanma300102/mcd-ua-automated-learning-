# Proposal

## Why

El notebook describe `RequestCountPerTarget` como "solicitudes por instancia". El usuario observó que la métrica corresponde al *target group*. Se verificó contra la documentación de AWS: la métrica se calcula sobre un *target group* (dimensión `TargetGroup`), pero su valor es *"the total number of requests received by the target group, divided by the number of healthy targets in the target group"*.

Por lo tanto, la interpretación de "promedio por unidad" es correcta, pero la unidad es el **target sano del target group**: una instancia EC2, una tarea ECS o una IP. "Instancia" es impreciso. Además, el notebook no muestra la fuente de la definición.

Fuente: https://docs.aws.amazon.com/elasticloadbalancing/latest/application/load-balancer-cloudwatch-metrics.html

## What Changes

- La Etapa 1 cita la definición oficial de AWS y su fuente.
- La tabla de tipos de la Etapa 2 explica `value` con la fórmula de AWS: solicitudes del *target group* ÷ targets sanos. Esto también explica los valores `.5`.
- Las etiquetas de los ejes y los textos de las Etapas 3 a 5 pasan de "por instancia" a "por target".
- El riesgo de retroalimentación de la Etapa 5 se reformula en términos de targets sanos y cita `RequestCount` con dimensión `LoadBalancer, TargetGroup` como alternativa para el tráfico total.
- Se vuelve a ejecutar el notebook.

## Capabilities

### New Capabilities
<!-- ninguna -->

### Modified Capabilities
- `store-traffic-data-profiling`: se agrega el requisito de definir la métrica con su fuente oficial.
- `store-traffic-model-use`: el riesgo de la métrica se expresa en términos de targets sanos del *target group*.

## Impact

- `TP_Analisis_de_Dataset_v3.ipynb`: celdas `bf9d70fd`, `7790a36f`, `b3a0e1d3`, `cde4df87`, `4fa3b9e2`, `7c1e2311`, `c0dd8462`, `e4b1c2d3`, `8bf80e6c` y `2f41c17d`, más las salidas. No cambia ninguna cifra.
