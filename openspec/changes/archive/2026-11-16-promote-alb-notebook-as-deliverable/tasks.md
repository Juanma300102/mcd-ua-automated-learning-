# Tasks

## 1. Intercambio de nombres

- [x] 1.1 Guardar las salidas de texto de ambos notebooks y hacer el intercambio con `git mv` mediante un nombre temporal. Verificar con `git status` que aparecen dos renombres y que la salida de carga de `TP_Analisis_de_Dataset_v3.ipynb` muestra `RequestCount`

## 2. Textos

- [x] 2.1 En el entregable, reemplazar las 9 referencias a "TP principal" o "notebook base" por "primer intento exploratorio" con el nombre `TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb`, y actualizar la nota de la Etapa 1 y la declaración de IA, que debe mencionar el intercambio. Verificar que "TP principal" no aparece en el entregable
- [x] 2.2 En el primer intento, insertar después del título la celda de aviso con el enlace al entregable y el hallazgo que motivó el cambio de métrica, y actualizar su declaración de IA. Verificar que la segunda celda contiene "primer intento exploratorio" y `TP_Analisis_de_Dataset_v3.ipynb`
- [x] 2.3 Reorganizar el README con el entregable primero y el primer intento después, con los comandos actualizados. Verificar que los dos comandos documentados existen como archivos

## 3. Ejecución

- [x] 3.1 Ejecutar ambos notebooks con `uv run jupyter nbconvert --to notebook --execute --inplace <notebook>`. Verificar el código de salida 0, sin errores, y que las salidas de texto son idénticas a las guardadas en 1.1
