# Tasks

## 1. Formato de números

- [x] 1.1 Definir `numero_es`, `EJE_ES` y `EJE_MILLONES` en la celda de estilo `b3a0e1d3` de ambos notebooks, y aplicarlos a los ejes, las barras de color, las leyendas y las anotaciones (millones solo en el notebook del ALB). Verificar en los gráficos renderizados que no quedan millones completos ni decimales con punto

## 2. Declaración de IA

- [x] 2.1 Insertar en ambos notebooks, antes de `b29e94a0`, la celda "Declaración de uso de IA". Verificar que menciona la herramienta, el modelo, OpenSpec 2.0.0 `spec-driven` y la carpeta de cambios archivados

## 3. Ejecución

- [x] 3.1 Ejecutar ambos notebooks con `uv run jupyter nbconvert --to notebook --execute --inplace <notebook>` y verificar el código de salida 0, la ausencia de errores y que las salidas de texto no cambiaron
