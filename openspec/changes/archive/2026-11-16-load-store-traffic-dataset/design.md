# Design

## Context

La celda `cd405394` ofrece tres opciones de carga y hoy está activa la A (seaborn). El CSV ya está versionado en `data/` (se quitó `data/*` del `.gitignore`) y el entorno se reproduce con `uv sync`. Una inspección previa del archivo mostró lo siguiente: 3575 filas; columnas `load_balancer`, `target_group`, `metric_name`, `period_start_utc`, `period_end_utc` y `value`; un solo valor distinto en cada una de las tres primeras; rango horario desde `2026-05-01T00:00Z` hasta `2026-09-26T22:00Z`. Motivación: ver proposal.md.

## Goals / Non-Goals

**Goals:**
- Que la carga funcione igual en local y en Colab, y que quede explicada.

**Non-Goals:**
- Analizar tipos, faltantes o calidad, que corresponden a `identify-store-traffic-data-types`.
- Adaptar las plantillas de EDA, que corresponden a `explore-store-traffic-series`.

## Decisions

- **Adaptar la Opción B en lugar de agregar una cuarta opción.** Criterio: la consigna pide dejar descomentada una sola opción. La Opción B ("CSV propio") es la que corresponde a este caso, así que se reescribe para que primero busque la ruta local y, si no la encuentra y está en Colab, llame a `files.upload()`. Las opciones A y C quedan comentadas, como referencia.
- **`parse_dates` con `utc=True`.** Se usa `pd.read_csv(..., parse_dates=[...])` y después `pd.to_datetime(..., utc=True)`. Criterio: los timestamps traen sufijo `Z`. Convertirlos en la carga hace que la Etapa 2 ya vea el tipo temporal correcto y evita que el análisis horario de la Etapa 3 tenga desfases de zona.
- **Ruta con `pathlib.Path` relativa a la raíz.** Criterio: en el README se documentó que el notebook se ejecuta desde la raíz del repositorio. Es la forma más simple y no depende de rutas absolutas de la máquina.
- **Ejecución intermedia con `--allow-errors`.** Al cambiar `df`, las celdas de plantilla `cde4df87` (`bill_length_mm`) y `4fa3b9e2` (`species`) fallan con `KeyError`. Criterio: el notebook entregado tiene que tener sus salidas (contexto del proyecto), pero esas celdas pertenecen a la Etapa 3. Este cambio ejecuta el notebook en el mismo archivo con `--allow-errors`, para que las Etapas 1 y 2 queden con salidas reales. La ejecución limpia de punta a punta se exige en `define-store-traffic-model-use`. Alternativa descartada: editar ya las celdas de la Etapa 3, que mezcla etapas y rompe la separación por cambio que pidió el usuario.

## Risks / Trade-offs

- [El notebook queda temporalmente con dos celdas en error] → Se documenta en el cierre del cambio y lo resuelve `explore-store-traffic-series`.
- [En Colab no existe `data/`] → Se cubre con la subida mediante `files.upload()`. Como alternativa, se puede subir la carpeta con el panel de archivos.
