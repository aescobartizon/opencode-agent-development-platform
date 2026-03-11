# Índice del repositorio

## Propósito

Este índice describe cada carpeta principal de `test-proyect-e`, su finalidad, los artefactos que aloja y su papel dentro del modelo multi-repo.

| Ruta | Finalidad | Artefactos esperados | Naturaleza | Relación con repos externos |
|---|---|---|---|---|
| `.opencode/` | Soporte operativo local para agentes, comandos y skills del proyecto | Configuración y assets de automatización local | Soporte operativo | Puede complementar agentes externos de plataforma |
| `docs/project/` | Contexto general del proyecto | visión, alcance, stakeholders, glosario, README del proyecto | Fuente de verdad | Referencia contexto global, no implementación |
| `docs/requirements/functional/` | Requisitos funcionales aprobados | FRS reales y artefactos funcionales derivados | Fuente de verdad | Enlaza con backlog, RTM y repos de servicio |
| `docs/requirements/technical/` | Requisitos técnicos y restricciones | NFR, restricciones, lineamientos técnicos | Fuente de verdad | Referencia decisiones que impactan servicios externos |
| `docs/requirements/templates/` | Copia operativa de plantillas de requisitos | plantilla de requisito funcional | Plantilla reutilizable | Sin código externo |
| `docs/architecture/` | Arquitectura global del sistema | catálogos, diagramas, decisiones cross-servicio | Fuente de verdad | Referencia servicios externos, no los aloja |
| `docs/adr/` | Decisiones de arquitectura de alcance global | ADR numerados | Fuente de verdad | Puede referenciar varios repos de servicio |
| `docs/refinement/` | Refinamiento y preguntas abiertas | sesiones, evidencias, pendientes | Fuente de verdad | Puede enlazar decisiones tomadas con equipos externos |
| `docs/executive-reports/` | Informes ejecutivos formales | informes HTML e hitos | Salida derivada y comunicación | Resume el estado global del ecosistema |
| `docs/qa/` | Estrategia de calidad global | estrategia de pruebas, criterios cross-servicio, evidencias | Fuente de verdad | Coordina pruebas entre servicios externos |
| `docs/templates/` | Plantillas copiadas desde la plataforma | plantillas y ejemplos reutilizables | Plantilla reutilizable | Fuente de apoyo interna al proyecto |
| `traceability/` | Trazabilidad estructurada del proyecto | RTM, trazabilidad general, CSV extremo a extremo | Fuente de verdad | Contiene referencias a repos externos de servicios |
| `backlog/epics/` | Backlog de alto nivel | épicas E-NNN | Fuente de verdad | Relaciona trabajo global con servicios futuros |
| `backlog/user-stories/` | Backlog operativo fino | historias US-NNN | Fuente de verdad | Relaciona trabajo con repositorios de servicio |
| `services/` | Registro central de microservicios y contratos | registry.yaml y contratos OpenAPI o AsyncAPI | Fuente de verdad | Referencia repos externos; no contiene implementación |
| `spec/` | Artefactos de especificación SDD | OpenAPI y otros artefactos analíticos | Fuente de verdad operativa | Puede apuntar a servicios externos |
| `src/` | Código compartido transversal | interfaces, tipos base, SDK internos | Fuente de verdad técnica | Nunca aloja microservicios completos |
| `tests/` | Pruebas de alcance global | contract tests, e2e, fixtures compartidos | Fuente de verdad de validación | Ejecuta validación sobre múltiples servicios |
| `ops/` | Operación global del sistema | orquestación, observabilidad, runbooks, CI global | Fuente de verdad operativa | Coordina múltiples repos externos |
| `agents/` | Artefactos y prompts de agentes del proyecto | documentación y activos agénticos | Soporte operativo | Puede complementar agentes de plataforma |
| `artifacts/` | Salidas generadas automáticamente | exportables, reportes, evidencias empaquetadas | Salida derivada | Puede consolidar salidas de varios servicios |

## Reglas clave

- La implementación de microservicios no vive en este repositorio.
- La trazabilidad estructurada principal vive en `traceability/RTM.yaml`.
- El registro de servicios vive en `services/registry.yaml` y empieza vacío.
- Las plantillas copiadas en `docs/templates/` conservan su contenido original para reutilización futura.
