# Design

## Context

Hallazgos del EDA (spec `store-traffic-eda`): autocorrelación de 0,947 a 1 h, 0,858 a 24 h y 0,743 a 168 h; estacionalidad diaria con una amplitud del 26 %; estacionalidad semanal débil (4,1 %); tendencia que cambia de nivel.

## Goals / Non-Goals

**Goals:**
- Respaldar la propuesta con una cifra calculada y no solo con una tabla de reglas.

**Non-Goals:**
- Entrenar y comparar modelos (la consigna dice "No tienen que entrenar el modelo").

## Decisions

- **Las líneas base ingenuas son la evidencia.** Criterio: no se ajusta ningún parámetro, así que no es entrenar. Aun así dan una vara concreta (el MAPE a superar) y muestran cuánto aporta cada rezago.
- **Evaluación en las dos últimas semanas completas**, del lunes 07/09 al domingo 20/09. Criterio: es el período más reciente con semanas completas, que es el que interesaría pronosticar en la práctica.
- **Modelo sugerido: regresión sobre *features* de calendario y rezagos** (por ejemplo, *gradient boosting*), con SARIMA o Prophet como alternativas. Criterio: incorpora la estacionalidad diaria y la tendencia, y es fácil de explicar.

## Risks / Trade-offs

- [El MAPE de la línea base de 1 h parece bajo, pero sirve solo para pronosticar 1 hora adelante] → La respuesta aclara que el horizonte útil para planificar capacidad es de horas a días, donde aplican los rezagos de 24 h y 168 h.
