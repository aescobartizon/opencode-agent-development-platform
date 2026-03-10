# Índice del repositorio — AgentCreateProjectTestHardened

| Ruta | Finalidad | Artefactos | Naturaleza | Repos externos |
|---|---|---|---|---|
| `docs/` | Documentación principal del proyecto | visión, requisitos, arquitectura, QA, refinamiento, informes | fuente de verdad | referencia externa cuando aplique |
| `docs/project/` | Contexto general del proyecto | alcance, visión, glosario, stakeholders | fuente de verdad | no |
| `docs/requirements/` | Requisitos aprobados y plantillas | requisitos funcionales, técnicos y templates | fuente de verdad | no |
| `docs/architecture/` | Arquitectura global del sistema | catálogos, decisiones cross-servicio, comunicación | fuente de verdad | puede referenciar servicios |
| `docs/adr/` | Decisiones de arquitectura de alcance global | ADRs | fuente de verdad | puede referenciar servicios |
| `docs/refinement/` | Evidencias de refinamiento | sesiones, evidencias, preguntas pendientes | fuente de verdad | no |
| `docs/executive-reports/` | Informes ejecutivos del proyecto | HTML y resúmenes ejecutivos | salida derivada controlada | no |
| `docs/qa/` | Estrategia de calidad global | estrategia, criterios cross-servicio, evidencias | fuente de verdad | puede referenciar tests externos |
| `docs/templates/` | Plantillas operativas del repo | plantillas HTML y Markdown | fuente base reutilizable | no |
| `traceability/` | Trazabilidad integral del proyecto | RTM, CSV E2E, matrices y cruces | fuente de verdad | sí |
| `backlog/` | Backlog funcional del sistema | épicas y casos de uso | fuente de verdad | no |
| `services/` | Registro central de microservicios | registry y contratos | fuente de verdad | sí |
| `services/contracts/` | Interfaces públicas de integración | OpenAPI, AsyncAPI y contratos futuros | fuente de verdad | sí |
| `spec/` | Especificaciones generadas | artefactos SDD y definiciones analíticas | fuente de verdad operativa | sí |
| `spec/open-api/` | Definiciones OpenAPI previas a publicación | YAML de análisis | fuente de verdad operativa | sí |
| `src/` | Código compartido futuro | tipos, SDKs, interfaces comunes | contenido futuro | sí |
| `tests/` | Pruebas globales | contrato, integración, fixtures globales | fuente de verdad técnica | sí |
| `ops/` | Operación global del sistema | observabilidad, runbooks, orquestación | fuente de verdad técnica | sí |
| `agents/` | Recursos de agentes del proyecto | prompts, perfiles, guías | fuente de verdad operativa | no |
| `.opencode/` | Integración con OpenCode | agentes, comandos, skills | soporte operativo | no |
| `artifacts/` | Salidas generadas | exportaciones y artefactos automáticos | salida derivada | no |

## Notas
- Los microservicios no viven en este repositorio.
- Los repositorios independientes de servicio se registran en `services/registry.yaml`.
- Los documentos instanciados fuera de carpetas de plantillas no deben contener placeholders sin sustituir.
