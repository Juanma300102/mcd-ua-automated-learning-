# Tasks

## 1. Segmentación

- [x] 1.1 Insertar después de `5134693a` la sección 3.0 (markdown y código): estilo de gráficos, períodos, criterio del período estable con su tabla semanal y el gráfico de la serie completa con sombreado y media móvil de 7 días. Verificar que imprime el inicio estable 2026-07-13

## 2. Plantillas adaptadas

- [x] 2.1 Reescribir `5a89a83f` (3.a) con `describe()` del período activo y del estable, asimetría y atípicos IQR. Verificar la salida de dos columnas
- [x] 2.2 Reescribir `1ba7626e` y `cde4df87` (3.b) con el histograma del período estable y las líneas de media y mediana. Verificar que la celda ejecuta sin `KeyError`
- [x] 2.3 Reescribir `dc5d2712` y `4fa3b9e2` (3.c) con los perfiles por hora y por día de la semana y la justificación de por qué no se usa la tabla de frecuencias. Verificar que imprime la hora de mínimo y la de máximo
- [x] 2.4 Reescribir `cdd2827e` y `7c1e2311` (3.d) con la autocorrelación de 1 a 168 horas y el mapa de calor día × hora, y la justificación de por qué no se usa la matriz de correlación. Verificar que imprime las autocorrelaciones en los rezagos 1, 24 y 168

## 3. Respuesta y ejecución

- [x] 3.1 Ejecutar `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3.ipynb` sin `--allow-errors` y verificar el código de salida 0
- [x] 3.2 Completar `c0dd8462` con entre 3 y 5 hallazgos que citen cifras de las salidas ya ejecutadas. Verificar que no queda el texto de plantilla
