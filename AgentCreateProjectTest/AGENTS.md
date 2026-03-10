# AGENTS — AgentCreateProjectTest

## Agentes definidos para este repositorio

| Agente | Rol | Responsabilidad principal | Herramientas |
|---|---|---|---|
| AgentProjectFromScratch | Fundacional | Crear y mantener la base del repositorio de gobernanza | estructura, plantillas, trazabilidad, reportes |
| AgentRequirementsAnalyst | Analisis | Elaborar requisitos funcionales y tecnicos trazables | requisitos, refinement, RTM |
| AgentArchitect | Arquitectura | Definir arquitectura global, catalogo de servicios y ADRs | docs/architecture, docs/adr, services/contracts |
| AgentDeveloper | Desarrollo | Implementar cambios en repositorios de servicio externos y registrar referencias | repos externos, RTM, registry |
| AgentQA | Calidad | Definir pruebas de contrato e integracion global | docs/qa, tests, RTM |
| AgentDevOps | Operacion | Preparar operacion cross-servicio y CI/CD global | ops, observabilidad, runbooks |

## Principios de trabajo

- Mantener trazabilidad bidireccional.
- No alojar implementacion de microservicios en este repositorio.
- Registrar referencias externas a repos de servicio cuando existan.
- No dejar placeholders sin sustituir en documentos reales.
- Tratar `traceability/` y `services/registry.yaml` como fuentes de verdad.

## Convenciones

- IDs segun el esquema del proyecto: `FRS-NNN`, `UC-NNN`, `E-NNN`, `SVC-NNN`, `TC-NNN`, `ADR-NNNN`, `REF-NNN`, `LINK-NNN`.
- Los contratos publicados van en `services/contracts/`.
- Las definiciones OpenAPI en elaboracion van en `spec/open-api/`.
- Los informes ejecutivos emitidos van en `docs/executive-reports/`.
