# Tasks

## 1. Copia y carga

- [x] 1.1 Copiar `TP_Analisis_de_Dataset_v3.ipynb` a `TP_Analisis_de_Dataset_v3_alb_request_count.ipynb` y registrar el hash del original. Verificar que la copia existe y que el hash del original no cambia al final del cambio
- [x] 1.2 En la copia, apuntar la celda de carga al nuevo CSV y reescribir la respuesta de la Etapa 1 (`RequestCount` del ALB completo y la limitación de otros *target groups*). Verificar `df.shape == (3575, 6)` y `metric_name == "RequestCount"`

## 2. Diagnóstico y EDA

- [x] 2.1 Adaptar el diagnóstico de la Etapa 2 para la columna vacía y los valores enteros. Verificar que imprime 3575 faltantes en `target_group`, 0 no enteros, primera hora positiva 2026-06-22 14:00 UTC y 14 ceros posteriores
- [x] 2.2 Ajustar las etiquetas y los textos de las secciones 3.0 a 3.d a "solicitudes / hora (total del ALB)". Verificar que la sección 3.0 imprime el inicio estable recalculado

## 3. Comparación

- [x] 3.1 Agregar al final de la Etapa 3 una sección 3.e con el cociente `RequestCount / RequestCountPerTarget` en el período estable: estadísticos, gráfico de evolución y advertencia sobre otros *target groups*. Verificar que imprime la mediana, el mínimo y el máximo

## 4. Respuestas, ejecución y documentación

- [x] 4.1 Ejecutar la copia con `uv run jupyter nbconvert --to notebook --execute --inplace TP_Analisis_de_Dataset_v3_alb_request_count.ipynb`, verificar el código de salida 0 y reescribir las respuestas de las Etapas 2 a 5 con las cifras de sus salidas. Volver a ejecutar y verificar que no quedan errores ni texto de plantilla
- [x] 4.2 Agregar al README el segundo notebook y su comando de ejecución, y anotar que el código está duplicado entre ambos. Verificar ejecutando el comando documentado tal como está escrito
