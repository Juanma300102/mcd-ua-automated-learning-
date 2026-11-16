# Design

## Context

Definición verificada en la documentación de AWS (ver proposal.md). Los 1131 valores con `.5` del dataset confirman que hay una división: un conteo bruto de solicitudes siempre es entero.

## Goals / Non-Goals

**Goals:**
- Precisar la unidad de medida sin cambiar ningún cálculo ni ninguna cifra.

**Non-Goals:**
- Obtener o analizar `RequestCount`, que no está en el dataset.

## Decisions

- **Término "target" con aclaración la primera vez.** En la Etapa 1 se define "target (instancia, tarea o IP registrada en el *target group*)" y después se usa "target". Criterio: es el término de AWS y abarca más casos que "instancia".
- **Las referencias a capacidad también pasan a "targets".** Criterio: lo que agrega o quita el *autoscaling* son targets del grupo. Mantener "instancias" en un lugar y "targets" en otro confundiría al lector.

## Risks / Trade-offs

- [El texto queda más técnico] → La definición aparece una vez, en la Etapa 1.
