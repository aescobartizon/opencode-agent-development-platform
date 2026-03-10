# Trazabilidad de requisitos — AgentCreateProjectNoDupTrace

## Principio de gobierno

La trazabilidad del proyecto se mantiene con una fuente estructurada principal en `traceability/RTM.yaml` y vistas complementarias controladas. No se crean matrices derivadas redundantes para relaciones ya cubiertas por artefactos fuente y RTM.

## Cobertura inicial

| Nivel | Fuente principal | Estado |
|---|---|---|
| Requisito de negocio | Pendiente de creación | pendiente |
| Requisito funcional | `docs/requirements/functional/` | preparado |
| Historia de usuario | `backlog/user-stories/` | preparado |
| Servicio | `services/registry.yaml` | inicializado |
| Prueba | `tests/` y `traceability/RTM.yaml` | preparado |

## Regla operativa

- Registrar enlaces formales en `RTM.yaml`.
- Mantener referencias a repos externos cuando existan.
- Evitar artefactos de trazabilidad duplicados.
