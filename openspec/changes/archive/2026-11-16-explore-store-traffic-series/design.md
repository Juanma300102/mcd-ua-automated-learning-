# Design

## Context

La spec `store-traffic-data-profiling` ya estableció que la serie es univariada y horaria, sin huecos, con ceros antes del 2026-06-22 16:00 UTC y 61 ceros en la semana de puesta en marcha. Un análisis previo con pandas de las medias semanales (semanas que empiezan el lunes) mostró: 16 188, 62 934 y 89 172 en las tres primeras semanas, y luego entre 97 000 y 119 000. La autocorrelación del período activo es 0,989 en el rezago 1, 0,943 en el 24 y 0,801 en el 168.

## Goals / Non-Goals

**Goals:**
- Que cada herramienta usada se derive del tipo de dato, como pide la consigna, y que cada corte de período tenga un criterio reproducible.

**Non-Goals:**
- Descomposición STL o pruebas de estacionariedad. Requerirían statsmodels y exceden el nivel exploratorio que pide el TP.
- Entrenar cualquier modelo.

## Decisions

- **Criterio del período estable: primer lunes con media semanal ≥ 90 % de la mediana de las medias semanales.** La mediana es robusta a las semanas de arranque. El 90 % separa con margen la última semana de rampa (89 172, frente a un umbral cercano a 91 000) de la primera semana estable (98 323). Alternativa descartada: elegir una fecha a ojo, que no es reproducible.
- **Perfiles y estadísticas sobre el período estable.** Si se incluyeran los ceros y la rampa, la media bajaría y la distribución tendría una cola izquierda artificial. El período activo completo se muestra al lado para que se vea esa diferencia.
- **Reemplazar las plantillas en lugar de borrarlas.** Se conserva la numeración 3.a a 3.d de la consigna y cada encabezado explica la sustitución. Así el docente puede seguir la estructura original.
- **Autocorrelación con `Series.autocorr` por rezago**, no con `statsmodels.plot_acf`. Alcanza con pandas, que ya es dependencia del proyecto.
- **Visualización:** una serie, un color (azul `#2a78d6` de la paleta de referencia), grilla tenue, sin doble eje. Las líneas de referencia van en tinta oscura y el mapa de calor usa una escala secuencial de un solo tono azul. Al ser un notebook estático no hay capa de *hover*; los valores clave se imprimen como texto, que funciona como vista tabular.

## Risks / Trade-offs

- [El umbral del 90 % es una elección] → Se imprime la tabla semanal completa, para que el lector vea que el corte no depende de un valor límite.
- [El tráfico se mide en UTC y los usuarios podrían estar en otra zona horaria] → En la respuesta se aclara que las horas están en UTC y que el patrón se desplaza si se convierte a hora local.
