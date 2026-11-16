# Spec Delta

## Purpose

Define cómo los notebooks del TP presentan los números en los gráficos (convención española, millones abreviados) y cómo declaran el uso de un agente de IA.

## ADDED Requirements

### Requirement: Números de gráficos en convención española
Los ejes, las barras de color, las leyendas y las anotaciones de los gráficos de ambos notebooks SHALL usar punto como separador de miles y coma como separador decimal.

#### Scenario: Eje de miles
- **WHEN** se renderiza el histograma 3.b del notebook principal
- **THEN** las marcas del eje muestran valores como `100.000` y la leyenda muestra la media como `106.164`

#### Scenario: Decimales
- **WHEN** se renderiza el gráfico de autocorrelación
- **THEN** las marcas y anotaciones usan coma decimal (por ejemplo, `0,86`)

### Requirement: Millones abreviados
Los gráficos cuyos valores alcanzan el millón SHALL mostrarlos abreviados en millones, con un decimal y el sufijo ` M`.

#### Scenario: Histograma del ALB
- **WHEN** se renderiza el histograma 3.b del notebook del ALB
- **THEN** el eje muestra valores como `2,2 M` y ninguna marca muestra el número completo

### Requirement: Declaración de uso de IA
Cada notebook SHALL incluir, antes de "Cierre y entrega", una celda que declare la herramienta y el modelo de IA usados, el marco de desarrollo guiado por especificaciones (OpenSpec, con su versión y su esquema), los cambios registrados y la división de responsabilidades.

#### Scenario: Declaración visible
- **WHEN** se lee la celda de declaración
- **THEN** menciona Claude Code, el modelo Claude Opus 5.5 (`claude-opus-5-5`), OpenSpec 2.0.0 con el esquema `spec-driven` y la carpeta `openspec/changes/archive/`
