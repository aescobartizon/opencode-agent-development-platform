# Agentes del proyecto — AgentCreateProjectTestHardened

| Agente | Rol | Responsabilidad principal | Herramientas habituales |
|---|---|---|---|
| AgentProjectFromScratch | Fundacional | Crear y gobernar la base documental y operativa del repositorio de gobernanza | OpenCode, plantillas, trazabilidad |
| AgentRequirementsAnalyst | Análisis | Refinar requisitos, casos de uso y definiciones funcionales | Markdown, RTM, OpenAPI |
| AgentArchitect | Arquitectura | Diseñar arquitectura global y descomposición de servicios | ADR, diagramas, contratos |
| AgentDev | Desarrollo | Implementar servicios en repos externos | Git, lenguaje del servicio, tests |
| AgentQA | Calidad | Definir estrategia y pruebas cross-servicio | tests, evidencias, cobertura |
| AgentDevOps | Operación | Preparar CI/CD, observabilidad y operación global | ops, pipelines, runbooks |

## Reglas operativas
- Este repositorio contiene gobernanza, no implementación de negocio.
- Los servicios se registran, no se crean aquí.
- La trazabilidad estructurada vive en `traceability/RTM.yaml`.
- Los documentos reales deben quedar sin placeholders pendientes.
