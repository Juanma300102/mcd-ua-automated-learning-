# Tasks

## 1. Carga del dataset

- [x] 1.1 Reescribir la celda de código `cd405394`: Opción B adaptada (ruta local con `pathlib`, `files.upload()` si falta el archivo en Colab, `FileNotFoundError` con la ruta esperada si falta fuera de Colab), parseo de `period_start_utc` y `period_end_utc` a UTC, y las opciones A y C comentadas. Verificar con `uv run python` en una copia que `df.shape == (3575, 6)` y que `str(df["period_start_utc"].dtype)` contiene `UTC`
- [x] 1.2 Verificar que no queda `load_dataset("penguins")` en código activo: `grep` sobre las celdas de código del notebook, sin coincidencias fuera de comentarios

## 2. Respuesta de la Etapa 1

- [x] 2.1 Completar la celda markdown `bf9d70fd` con el dataset elegido (nombre, fuente: métrica de CloudWatch `RequestCountPerTarget` del ALB de producción, exportada a CSV) y una justificación de 2 a 4 líneas que cite la granularidad horaria, el rango de fechas y la cantidad de filas. Verificar que el texto "Reemplacen este texto por su respuesta" ya no aparece en esa celda

## 3. Ejecución

- [x] 3.1 Ejecutar `uv run jupyter nbconvert --to notebook --execute --inplace --allow-errors TP_Analisis_de_Dataset_v3.ipynb` y verificar que las celdas de las Etapas 1 y 2 tienen salidas sin error, y que solo `cde4df87` y `4fa3b9e2` registran errores (pendientes de `explore-store-traffic-series`)
