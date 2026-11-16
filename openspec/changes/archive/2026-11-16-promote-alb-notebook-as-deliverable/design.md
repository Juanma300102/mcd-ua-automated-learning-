# Design

## Context

Estado actual: `TP_Analisis_de_Dataset_v3.ipynb` analiza `RequestCountPerTarget` y `TP_Analisis_de_Dataset_v3_alb_request_count.ipynb` analiza `RequestCount`. El segundo menciona 9 veces al primero como "TP principal" o "notebook base" (celdas `bf9d70fd`, `7790a36f`, `e3f0a1b2`, `e3f0a1b3`, `c0dd8462`, `2f41c17d` y `d1a2b3c4`). Las specs `store-traffic-dataset-selection`, `store-traffic-eda` y `store-traffic-model-use` ejecutan `TP_Analisis_de_Dataset_v3.ipynb` esperando la serie por target, y `alb-traffic-analysis` usa el nombre largo.

## Goals / Non-Goals

**Goals:**
- Que el nombre de la plantilla corresponda al entregable y que cada notebook declare su rol.

**Non-Goals:**
- Cambiar cálculos, cifras o gráficos.
- Unificar los dos notebooks.
- Reescribir los artefactos archivados, que reflejan los nombres vigentes cuando se escribieron.

## Decisions

- **Intercambio con `git mv` en dos pasos**, pasando por un nombre temporal. Criterio: el historial de cada archivo sigue su contenido, así que `git log --follow` del entregable muestra la historia del análisis del ALB.
- **El aviso del primer intento va como celda nueva después del título**, con id fijo. Criterio: es lo primero que ve el lector y no altera las celdas existentes ni sus salidas.
- **"Primer intento exploratorio" en lugar de "TP principal".** El entregable cita el archivo por nombre, para que el docente pueda abrirlo, y presenta su hallazgo como la motivación del cambio de métrica.
- **Las specs se actualizan con MODIFIED donde solo cambia el nombre de archivo de un escenario.** "Copia independiente del notebook" se elimina con REMOVED y se reemplaza con ADDED, porque su escenario "Original intacto" deja de ser cierto y una modificación no puede quitar escenarios.
- **Verificación de "sin cambios de cifras"** comparando las salidas de texto antes y después en ambos notebooks, con el mismo procedimiento usado en los cambios anteriores.

## Risks / Trade-offs

- [Enlaces externos al nombre largo del ALB] → El repositorio es reciente; el README documenta los nombres nuevos.
- [La declaración de IA del entregable lista cambios con nombres históricos de archivo] → Se agrega una línea que explica el intercambio de nombres.
