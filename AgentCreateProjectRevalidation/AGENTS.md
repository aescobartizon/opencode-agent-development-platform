# AGENTS

## Agentes contemplados

| Agente | Rol | Responsabilidad principal | Herramientas típicas |
|---|---|---|---|
| AgentProjectFromScratch | Fundacional | Crear y validar el repositorio de gobernanza | estructura, documentación, validación |
| AgentRequirementsAnalyst | Análisis | Elaborar requisitos, casos de uso y refinamiento | plantillas, trazabilidad, OpenAPI |
| AgentArchitect | Arquitectura | Diseñar arquitectura global y contratos cross-servicio | ADR, catálogos, especificaciones |
| AgentDeveloper | Desarrollo | Implementar cambios en repos de servicio externos | código, tests, PRs |
| AgentQA | Calidad | Diseñar validación funcional y pruebas transversales | estrategia QA, RTM, evidencias |
| AgentDevOps | Operación | Preparar operación global, CI/CD y observabilidad | ops, runbooks, pipelines |

## Reglas de trabajo

1. Este repositorio no contiene implementación de microservicios.
2. Los servicios viven en repositorios independientes y solo se registran aquí.
3. La trazabilidad debe mantenerse desde requisito hasta prueba y referencia externa.
4. Ningún documento final debe conservar marcadores sin resolver.
5. Los agentes deben preferir estructuras estables y escalables.

## Convención mínima

- Requisitos: `FRS-NNN`
- Casos de uso: `UC-NNN`
- Épicas: `E-NNN`
- Servicios: `SVC-NNN`
- Casos de prueba: `TC-NNN`
- ADRs: `ADR-NNNN`
- Refinamiento: `REF-NNN`
- Informes ejecutivos: `INF-EJE-NNN`
- Enlaces RTM: `LINK-NNN`
