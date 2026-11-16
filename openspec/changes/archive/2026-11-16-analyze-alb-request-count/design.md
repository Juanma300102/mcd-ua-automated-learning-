# Design

## Context

El notebook original tiene la carga, el diagnóstico, el EDA (secciones 3.0 a 3.d), las líneas base y las respuestas ajustadas a `RequestCountPerTarget`. Una inspección previa del nuevo CSV mostró: mismo esquema de 6 columnas; `target_group` vacía; `value` entero entre 0 y 2 664 010; misma grilla horaria completa de 3575 horas; primera hora con tráfico 2026-06-22 14:00 UTC; 1276 ceros en total. En el período estable de la otra serie (desde 2026-07-13), el cociente `RequestCount / RequestCountPerTarget` tiene una mediana de 20,8 y va de 14,9 a 29,3.

## Goals / Non-Goals

**Goals:**
- Reutilizar el código del original con cambios mínimos y recalcular todas las cifras.

**Non-Goals:**
- Modificar el notebook original o sus specs.
- Factorizar el código común en un módulo compartido. Son dos entregables independientes de un TP; un módulo agregaría acoplamiento sin beneficio para el lector.

## Decisions

- **Copiar el `.ipynb` y editar celdas por id**, en lugar de generarlo desde cero. Criterio: se conserva la estructura de la consigna y los criterios ya justificados. Así los dos notebooks se comparan sección por sección.
- **El código de diagnóstico tolera columnas vacías.** `nunique()` devuelve 0 para `target_group`; la celda de la Etapa 2 se adapta para mostrarlo y explicarlo, en lugar de suponer columnas constantes.
- **Las cifras se recalculan, no se copian.** Ninguna cifra del original se reutiliza en las respuestas: todas salen de las salidas ejecutadas de la copia. Por ejemplo, la fecha de inicio estable se recalcula con el mismo criterio y puede diferir de 2026-07-13.
- **El cociente se presenta como "solicitudes totales por solicitud por target", no como "cantidad de targets".** Criterio: el CSV no tiene dimensión de *target group* y el ALB podría enrutar a otros grupos. Además, el promedio horario de targets sanos no es un entero. El cociente varía entre 15 y 29: eso basta para mostrar que la métrica por target no es proporcional al tráfico.
- **Etiquetas de gráficos:** "Solicitudes / hora (total del ALB)", con la misma paleta y el mismo estilo que el original.

## Risks / Trade-offs

- [Código duplicado entre los dos notebooks] → Aceptado. Un arreglo futuro en uno debe replicarse en el otro; queda anotado en el README.
- [El ALB podría incluir tráfico de otros servicios] → La Etapa 1 y la sección de comparación lo explican como limitación. El cociente se usa como indicio, no como medición exacta.
