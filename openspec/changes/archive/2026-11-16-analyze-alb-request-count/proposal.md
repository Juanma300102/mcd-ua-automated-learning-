# Proposal

## Why

El notebook entregado analiza `RequestCountPerTarget`, un promedio por target sano del *target group*. En la Etapa 5 ya se señaló que esa métrica cambia cuando el *autoscaling* agrega o quita targets, y se recomendó pronosticar el **tráfico total** (`RequestCount`). Ahora está disponible ese dato: `data/alb-request-count-hourly-since-2026-05-01.csv`. Rehacer el TP sobre esta métrica permite verificar si las conclusiones se sostienen sobre una variable que no depende de la cantidad de targets.

## What Changes

- Se crea una **copia** del notebook: `TP_Analisis_de_Dataset_v3_alb_request_count.ipynb`. El original queda sin cambios.
- En la copia se carga el nuevo CSV y se rehacen las cinco etapas con sus propias cifras. Se conservan la estructura, los criterios (por ejemplo, el inicio del período estable con la regla del 90 % de la mediana semanal) y las herramientas del notebook original, adaptando solo lo que cambia con estos datos.
- Diferencias que la copia tiene que tratar explícitamente, observadas en una inspección previa del CSV:
  - `metric_name` es `RequestCount` y `load_balancer` es el mismo ALB de producción.
  - `target_group` está **100 % vacía** (3575 NaN): la métrica es del balanceador completo, no de un *target group*.
  - `value` es **entero** (`int64`, 0 valores no enteros), con un orden de 2 a 2,7 millones de solicitudes por hora.
  - La primera hora con tráfico es **2026-06-22 14:00 UTC**, dos horas antes que en la serie por target. Después de esa hora hay **14** horas en 0, frente a 61 en la otra serie.
- Se agrega una sección de **comparación con la serie por target**: el cociente `RequestCount / RequestCountPerTarget` en el período estable. Su mediana es de alrededor de 21 y varía entre 15 y 29. Se presenta como evidencia del efecto de la cantidad de targets, con la advertencia de que el total del ALB podría incluir otros *target groups*.
- Se reescriben las respuestas de las cinco etapas con las cifras de la nueva serie, y la copia se entrega ejecutada.

## Capabilities

### New Capabilities
- `alb-traffic-analysis`: notebook derivado que analiza el tráfico total del ALB (`RequestCount`) con el flujo del TP y lo compara con la serie por target.

### Modified Capabilities
<!-- ninguna: el notebook original y sus specs no cambian -->

## Impact

- Archivo nuevo: `TP_Analisis_de_Dataset_v3_alb_request_count.ipynb`.
- Lee los dos CSV de `data/` sin modificarlos.
- El README se actualiza para mencionar el segundo notebook y su comando de ejecución.
