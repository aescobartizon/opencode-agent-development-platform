# AGENTS — AgentCreateProjectNoDupTrace

## Objetivo

Este repositorio está preparado para colaboración entre humanos y agentes especializados sin reorganizar la base documental.

## Agentes incluidos

| Agente | Rol | Responsabilidad principal | Herramientas habituales |
|---|---|---|---|
| AgentProjectFromScratch | Fundacional | Inicializar estructura, documentación base y trazabilidad | bash, read, apply_patch |
| AgentRequirementsAnalyst | Análisis | Elaborar requisitos funcionales y técnicos | read, apply_patch, webfetch |
| AgentArchitect | Arquitectura | Definir arquitectura global, contratos y decisiones | read, apply_patch, bash |
| AgentDeveloper | Desarrollo | Implementar en repos de servicio externos | bash, read, apply_patch |
| AgentQA | Calidad | Diseñar cobertura de pruebas y validaciones cross-servicio | read, apply_patch, bash |
| AgentDevOps | Operación | Preparar automatización, despliegue y observabilidad | bash, read, apply_patch |

## Reglas de colaboración

1. `traceability/RTM.yaml` es la matriz estructurada principal.
2. No crear matrices duplicadas para relaciones ya presentes en artefactos fuente o RTM.
3. Los repos de servicio se registran en `services/registry.yaml`.
4. Este repositorio no aloja implementación de microservicios.
5. Las plantillas se copian en `docs/templates/` y `docs/requirements/templates/`.

## Convenciones mínimas

- Épicas: `E-NNN`
- Requisitos funcionales: `FRS-NNN`
- Historias de usuario: `US-NNN`
- Servicios: `SVC-NNN`
- Casos de prueba: `TC-NNN`
- ADR: `ADR-NNNN`
- Refinamiento: `REF-NNN`
- Informes ejecutivos: `INF-EJE-NNN`

## Nota operativa

Los agentes futuros deben extender esta base respetando la separación entre documentación, trazabilidad, contratos, operación y artefactos generados.
