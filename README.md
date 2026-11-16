# TP — Análisis de un Dataset

Trabajo práctico de Fundamentos de Aprendizaje Automático (2026).

## Notebooks

| Notebook | Rol | Métrica analizada |
|---|---|---|
| `TP_Analisis_de_Dataset_v3.ipynb` | **Entregable** | `RequestCount`: tráfico total horario del balanceador (`data/alb-request-count-hourly-since-2026-05-01.csv`) |
| `TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb` | Primer intento exploratorio | `RequestCountPerTarget`: promedio por target sano del servicio de tienda (`data/store-service-request-count-per-target-hourly-since-2026-05-01.csv`) |

El primer intento se conserva porque documenta cómo se llegó a la métrica
entregada: mostró que `RequestCountPerTarget` depende de la cantidad de targets,
y por eso el análisis final trabaja con el tráfico total. La sección 3.e del
entregable compara las dos series.

## Entorno

El entorno de Python se gestiona con [uv](https://docs.astral.sh/uv/). La
versión de Python está fijada en `.python-version` (3.12) y las versiones
exactas de las dependencias quedan registradas en `uv.lock`.

Crear o actualizar el entorno a partir del lockfile:

```bash
uv sync
```

Verificar que el lockfile está al día con `pyproject.toml`:

```bash
uv lock --check
```

## Ejecución

Ejecutar el entregable sin interfaz y guardar las salidas en el mismo archivo:

```bash
uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3.ipynb
```

El primer intento exploratorio se ejecuta igual:

```bash
uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb
```

Abrirlos de forma interactiva con JupyterLab, sin agregarlo como dependencia:

```bash
uv run --with jupyterlab jupyter lab
```

El código de ambos notebooks está duplicado a propósito, porque cada uno es
independiente: una corrección en uno debe replicarse en el otro.

## Datos

Los CSV están versionados en `data/`. Cada notebook los lee con una ruta relativa,
por lo que debe ejecutarse desde la raíz del repositorio. En Google Colab hay que
subir el archivo con el panel de archivos o con la celda de carga del notebook.
La sección 3.e del entregable también lee el CSV por target.

## Desarrollo

El trabajo se hizo con desarrollo guiado por especificaciones (OpenSpec). Las
especificaciones vigentes están en `openspec/specs/` y el historial de cambios,
con sus decisiones y criterios, en `openspec/changes/archive/`.
