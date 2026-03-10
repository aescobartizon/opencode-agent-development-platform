# INDEX — AgentCreateProjectTest

| Ruta | Finalidad | Artefactos | Naturaleza | Referencias externas |
|---|---|---|---|---|
| `docs/` | Documentacion de proyecto y gobierno | alcance, requisitos, arquitectura, QA, informes | fuente de verdad | puede referenciar repos de servicio |
| `docs/project/` | Contexto general del proyecto | vision, alcance, glosario, stakeholders | fuente de verdad | no |
| `docs/requirements/functional/` | Requisitos funcionales aprobados | FRS instanciados | fuente de verdad | puede referenciar servicios |
| `docs/requirements/technical/` | Requisitos tecnicos y restricciones | NFR, decisiones tecnicas iniciales | fuente de verdad | puede referenciar tecnologia externa |
| `docs/requirements/templates/` | Plantillas de requisitos | plantilla FRS | salida reutilizable | no |
| `docs/architecture/` | Arquitectura global | catalogos, diagramas, estrategia de despliegue | fuente de verdad | si |
| `docs/adr/` | Decisiones de arquitectura global | ADRs | fuente de verdad | si |
| `docs/refinement/` | Evidencias de refinamiento | sesiones, evidencias, preguntas pendientes | fuente de verdad | si |
| `docs/executive-reports/` | Informes ejecutivos emitidos | HTML y resúmenes | salida derivada | no |
| `docs/qa/` | Estrategia global de calidad | estrategia de pruebas, criterios cross-servicio | fuente de verdad | si |
| `docs/templates/` | Plantillas generales del repositorio | HTML y Markdown reutilizable | salida reutilizable | no |
| `traceability/` | Matriz de trazabilidad central | RTM, CSV, tablas de relacion | fuente de verdad | si, hacia repos externos |
| `backlog/` | Backlog operativo | epicas y casos de uso | fuente de verdad | no |
| `backlog/epics/` | Epicas del proyecto | archivos `E-NNN` | fuente de verdad | puede enlazar servicios |
| `backlog/use-cases/` | Casos de uso funcionales | archivos `UC-NNN` | fuente de verdad | puede enlazar OpenAPI |
| `services/` | Registro de microservicios y contratos | `registry.yaml`, contratos | fuente de verdad | si, repos de servicio |
| `services/contracts/` | Contratos publicos por servicio | OpenAPI, AsyncAPI | fuente de verdad | si |
| `spec/` | Artefactos SDD en elaboracion | specs por servicio o caso de uso | fuente de verdad operativa | si |
| `spec/open-api/` | Definiciones OpenAPI en trabajo | YAML preliminares | fuente de verdad temporal | si |
| `src/` | Artefactos compartidos transversales | interfaces y tipos comunes | contenido futuro | si |
| `tests/` | Pruebas globales | contratos, integracion, fixtures | fuente de verdad de QA global | si |
| `ops/` | Operacion global del ecosistema | runbooks, CI/CD global, observabilidad | fuente de verdad operativa | si |
| `agents/` | Recursos para agentes | prompts y definiciones futuras | contenido futuro | no |
| `.opencode/` | Integracion local con OpenCode | agentes, comandos, skills | soporte operativo | no |
| `artifacts/` | Exportaciones generadas | entregables y salidas automaticas | salida derivada | no |

## Nota

Los repositorios de servicio no viven aqui. Este repositorio los registra y enlaza, pero la implementacion permanece en repos independientes.
