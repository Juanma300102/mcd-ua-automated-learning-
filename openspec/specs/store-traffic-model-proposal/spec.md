# store-traffic-model-proposal Specification

## Purpose
Define cómo el notebook del TP propone y justifica, con evidencia calculada, el tipo de modelo adecuado para la serie de tráfico del servicio de tienda.

## Requirements

### Requirement: Línea base ingenua como evidencia
El notebook SHALL calcular el MAE y el MAPE de tres predictores ingenuos (valor de hace 1 h, de hace 24 h y de hace 168 h) sobre las dos últimas semanas completas del período estable.

#### Scenario: Tabla de líneas base
- **WHEN** se ejecuta la celda de líneas base
- **THEN** se imprime una tabla con una fila por predictor, con su MAE y su MAPE, y se indica el período evaluado

### Requirement: Propuesta de modelo justificada
La celda "✏️ Su respuesta — Etapa 4" SHALL proponer pronóstico (*forecasting*) con `value` como target, listar las *features* de calendario y de rezagos, y justificar la elección con cifras del EDA y de las líneas base.

#### Scenario: Respuesta completa
- **WHEN** se lee la celda de respuesta de la Etapa 4
- **THEN** nombra el tipo de modelo, el target y las *features*, explica por qué no corresponde clasificación ni *clustering*, y no contiene "Reemplacen este texto por su respuesta"
