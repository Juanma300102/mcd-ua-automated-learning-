# Proposal

## Why

La Etapa 4 pide proponer y justificar un tipo de modelo, y la celda de respuesta (`8bf80e6c`) sigue con el texto de plantilla. El EDA ya mostró que el problema es una serie temporal con estacionalidad diaria y autocorrelación alta. Falta formalizar la propuesta y respaldarla con evidencia, sin entrenar un modelo complejo.

## What Changes

- Se agrega, antes de la respuesta, una celda de código con una **línea base ingenua estacional**: predecir cada hora con el valor de 1 hora antes, de 24 horas antes y de 168 horas antes. Se mide su error (MAE y MAPE) en las dos últimas semanas. No es entrenar un modelo: es la referencia mínima que cualquier modelo propuesto tiene que superar, y respalda con cifras qué *features* aportan información.
- Se completa la respuesta de la Etapa 4: tipo de modelo (pronóstico o *forecasting*), target, *features* y justificación.

## Capabilities

### New Capabilities
- `store-traffic-model-proposal`: propuesta y justificación del tipo de modelo para la serie de tráfico del servicio de tienda dentro del notebook del TP.

### Modified Capabilities
<!-- ninguna -->

## Impact

- `TP_Analisis_de_Dataset_v3.ipynb`: una celda de código nueva antes de `8bf80e6c`, y la celda `8bf80e6c`.
