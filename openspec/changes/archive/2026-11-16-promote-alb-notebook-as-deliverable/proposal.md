# Proposal

## Why

El análisis de `RequestCount` del ALB (`TP_Analisis_de_Dataset_v3_alb_request_count.ipynb`) es más sólido que el primero, sobre `RequestCountPerTarget`. Mide la demanda real sin pasar por la cantidad de targets, que cambió hasta un 19 % en una misma semana, y demostró con datos que la métrica por target subestima los cambios de tráfico (−18,2 % frente a −33,7 % en la caída del 18 al 21/09).

Hoy el repositorio presenta al revés la jerarquía entre los dos notebooks: el de la métrica por target tiene el nombre de la plantilla del TP y el del ALB figura como "variante". El usuario decidió entregar el análisis del ALB y conservar el otro como **primer intento exploratorio**, que documenta cómo se llegó a la métrica correcta.

## What Changes

- **Intercambio de nombres** (con `git mv`, para conservar el historial):
  - `TP_Analisis_de_Dataset_v3_alb_request_count.ipynb` pasa a llamarse `TP_Analisis_de_Dataset_v3.ipynb` y es el **entregable**.
  - El actual `TP_Analisis_de_Dataset_v3.ipynb` pasa a llamarse `TP_Analisis_de_Dataset_v3_exploracion_por_target.ipynb` y es el **primer intento exploratorio**.
  - Los dos quedan en la raíz, para que las rutas relativas a `data/` sigan funcionando.
- **Entregable:** se reescribe el texto que lo presenta como "variante del TP principal" para que se sostenga solo. El análisis por target pasa a citarse como "primer intento exploratorio", con su nombre de archivo, como antecedente que motivó el cambio de métrica (Etapa 1, Etapa 2, sección 3.e, Etapa 3 y declaración de IA). No cambia ninguna cifra ni ningún cálculo.
- **Primer intento:** se agrega al inicio una celda de aviso que indica que no es el entregable, enlaza al notebook entregado y resume el hallazgo que llevó a cambiar de métrica. Se actualiza su declaración de IA. El resto del contenido no se modifica.
- **README:** se reorganiza con el entregable primero y el primer intento después, con los comandos de ejecución actualizados.
- **Specs:** se actualizan los nombres de archivo en los escenarios afectados y se agrega el requisito sobre el rol de cada notebook.
- Se vuelven a ejecutar ambos notebooks.

## Capabilities

### New Capabilities
<!-- ninguna -->

### Modified Capabilities
- `alb-traffic-analysis`: pasa a ser el notebook entregable con el nombre de la plantilla. Se elimina el requisito "Copia independiente del notebook" y se lo reemplaza por "Notebook entregable con el nombre de la plantilla"; se agrega el rol de cada notebook.
- `store-traffic-dataset-selection`: el escenario de ejecución apunta al nuevo nombre del primer intento.
- `store-traffic-eda`: ídem.
- `store-traffic-model-use`: el requisito de cierre se refiere al primer intento con su nuevo nombre.

## Impact

- Renombra los dos notebooks. Cualquier enlace externo al archivo del ALB deja de funcionar, aunque el repositorio solo tiene dos commits propios.
- Edita celdas markdown de ambos notebooks y el README; agrega una celda al primer intento.
- La spec `python-environment` ya ejecuta `TP_Analisis_de_Dataset_v3.ipynb` y no cambia: después del intercambio, ese nombre corresponde al entregable.
