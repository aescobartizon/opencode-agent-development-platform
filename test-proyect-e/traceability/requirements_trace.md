# Trazabilidad de requisitos

Proyecto: `test-proyect-e`
Versión: `1.0.0`
Estado inicial: base creada sin requisitos funcionales instanciados.

## Principio

La trazabilidad se mantiene en los artefactos fuente y en `traceability/RTM.yaml`, evitando matrices duplicadas innecesarias.

## Cadena objetivo

Business Requirement -> Épica -> FRS -> Historia de usuario -> OpenAPI o contrato -> Caso de prueba -> Evidencia

## Estado actual

| Nivel | Estado |
|---|---|
| Business requirements | pendiente |
| Épicas | sin instanciar |
| FRS | sin instanciar |
| Historias de usuario | sin instanciar |
| Contratos OpenAPI o AsyncAPI | sin instanciar |
| Casos de prueba globales | sin instanciar |
| Referencias a implementación externa | sin instanciar |

## Reglas

- `RTM.yaml` es la matriz estructurada principal.
- `end_to_end_traceability.csv` ofrece una vista tabular exportable.
- Las referencias a repositorios externos se registran cuando existan implementaciones reales.
