# Proposal

## Why

En el notebook del ALB, los ejes de los gráficos muestran cifras de millones completas (por ejemplo, `2500000`), difíciles de leer, sobre todo en el histograma de la sección 3.b. En los dos notebooks, los números de los gráficos usan el formato inglés (`106,164`, `0.86`), mientras que el texto está en español. Además, el usuario pidió declarar el uso del agente de IA: modelo y marco de trabajo SDD.

## What Changes

- Se agregan, en la celda de estilo de la sección 3.0 de cada notebook, dos formateadores de ejes en convención española: punto para miles y coma para decimales.
  - `EJE_MILLONES`: muestra millones abreviados (`2,3 M`).
  - `EJE_ES`: muestra miles y decimales (`100.000`, `0,8`).
- Notebook del ALB: los ejes, la barra de color y las leyendas con valores de millones pasan a `EJE_MILLONES`; los ejes de autocorrelación y del cociente, a `EJE_ES`.
- Notebook principal: todos los ejes numéricos de valores, la barra de color y las leyendas pasan a `EJE_ES`. Sus cifras no llegan al millón, así que no se abrevian.
- Las anotaciones de autocorrelación en el gráfico usan coma decimal.
- Se agrega en ambos notebooks una celda "Declaración de uso de IA", antes de "Cierre y entrega": herramienta, modelo, marco SDD (OpenSpec, esquema `spec-driven`), cambios realizados y responsabilidades.
- Se vuelven a ejecutar ambos notebooks.

Fuera de alcance: los `print` y las tablas de pandas mantienen su formato; el pedido se refiere a los gráficos.

## Capabilities

### New Capabilities
- `notebook-presentation`: formato de los números en los gráficos y declaración del uso de IA en los notebooks del TP.

### Modified Capabilities
<!-- ninguna -->

## Impact

- `TP_Analisis_de_Dataset_v3.ipynb` y `TP_Analisis_de_Dataset_v3_alb_request_count.ipynb`: celdas de gráficos (`b3a0e1d3`, `cde4df87`, `4fa3b9e2`, `7c1e2311` y, en el del ALB, `e3f0a1b3`), una celda markdown nueva y las salidas. Las cifras impresas no cambian.
