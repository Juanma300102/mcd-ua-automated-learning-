# TP — Análisis de un Dataset

Trabajo práctico de Fundamentos de Aprendizaje Automático (2026). El notebook
`TP_Analisis_de_Dataset_v3.ipynb` analiza la serie horaria
`RequestCountPerTarget` del servicio de tienda, ubicada en
`data/store-service-request-count-per-target-hourly-since-2026-05-01.csv`.

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

## Ejecución del notebook

Ejecutar todas las celdas sin interfaz y guardar las salidas en el mismo archivo:

```bash
uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3.ipynb
```

Abrirlo de forma interactiva con JupyterLab, sin agregarlo como dependencia:

```bash
uv run --with jupyterlab jupyter lab
```

### Variante con el tráfico total del ALB

`TP_Analisis_de_Dataset_v3_alb_request_count.ipynb` aplica el mismo flujo a la
métrica `RequestCount` del balanceador
(`data/alb-request-count-hourly-since-2026-05-01.csv`) y la compara con la serie
por target. Se ejecuta igual:

```bash
uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3_alb_request_count.ipynb
```

El código de ambos notebooks está duplicado a propósito, porque son entregables
independientes: una corrección en uno debe replicarse en el otro.

## Datos

Los CSV están versionados en `data/`. Cada notebook los lee con una ruta relativa,
por lo que debe ejecutarse desde la raíz del repositorio. En Google Colab hay que
subir el archivo con el panel de archivos o con la celda de carga del notebook.
