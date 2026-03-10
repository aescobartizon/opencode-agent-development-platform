# Índice del repositorio

## Raíz

| Ruta | Finalidad | Artefactos | Naturaleza | Alcance externo |
|---|---|---|---|---|
| `README.md` | Guía de entrada del proyecto | Contexto, alcance, flujo base | Fuente de verdad | No |
| `INDEX.md` | Mapa del repositorio | Inventario estructural | Fuente de verdad | No |
| `AGENTS.md` | Convenciones de agentes | Roles, responsabilidades, herramientas | Fuente de verdad | No |
| `PROJECT_REPORT.html` | Informe ejecutivo inicial | Resumen estructural y métricas | Salida derivada | No |
| `.opencode/` | Soporte local para automatización | Agentes, comandos, skills | Fuente de soporte | No |
| `docs/` | Documentación principal del proyecto | Requisitos, arquitectura, QA, reportes | Fuente de verdad | Referencia externa posible |
| `traceability/` | Trazabilidad integral | Matrices, CSV, vistas cruzadas | Fuente de verdad | Sí |
| `backlog/` | Backlog funcional | Épicas y casos de uso | Fuente de verdad | Sí |
| `services/` | Registro de microservicios | Registro central y contratos | Fuente de verdad | Sí, referencia repos externos |
| `spec/` | Especificaciones técnicas | OpenAPI y artefactos SDD | Fuente de verdad | Sí |
| `src/` | Recursos compartidos futuros | Interfaces, tipos, SDKs | Fuente de verdad | Sí |
| `tests/` | Calidad transversal | Contrato, integración, fixtures | Fuente de verdad | Sí |
| `ops/` | Operación global | Orquestación, CI/CD global, runbooks | Fuente de verdad | Sí |
| `agents/` | Recursos agénticos del proyecto | Definiciones y plantillas futuras | Fuente de soporte | No |
| `artifacts/` | Exportaciones generadas | Informes y salidas automáticas | Salida derivada | No |

## Carpetas principales

### `docs/project/`
Información general del proyecto, visión, alcance, contexto, stakeholders y glosario. Fuente de verdad.

### `docs/requirements/functional/`
Requisitos funcionales aprobados e instanciados. Fuente de verdad.

### `docs/requirements/technical/`
Requisitos técnicos, restricciones, atributos de calidad y condiciones no funcionales. Fuente de verdad.

### `docs/requirements/templates/`
Plantillas de requisitos reutilizables. Fuente de soporte.

### `docs/architecture/`
Arquitectura global, comunicación entre servicios, despliegue y diseño cross-servicio. Fuente de verdad. No aloja implementación ni contratos OpenAPI finales.

### `docs/adr/`
Decisiones de arquitectura de alcance global. Fuente de verdad.

### `docs/refinement/`
Sesiones, evidencias y preguntas abiertas de refinamiento. Fuente de verdad.

### `docs/executive-reports/`
Informes ejecutivos emitidos. Salida derivada controlada.

### `docs/qa/`
Estrategia de calidad, aceptación y criterios de prueba transversales. Fuente de verdad.

### `docs/templates/`
Plantillas generales del proyecto, incluyendo informe ejecutivo y requisito funcional. Fuente de soporte.

### `traceability/`
Matriz de trazabilidad, vistas humanas y referencias a repositorios externos, PRs y commits. Fuente de verdad.

### `backlog/epics/`
Épicas `E-NNN`. Fuente de verdad.

### `backlog/use-cases/`
Casos de uso `UC-NNN`. Fuente de verdad.

### `services/registry.yaml`
Registro central de repositorios de servicio. Fuente de verdad. Referencia contenido externo.

### `services/contracts/`
Contratos públicos por servicio. Fuente de verdad documental. No contiene implementación.

### `spec/open-api/`
Definiciones OpenAPI de trabajo y análisis. Fuente de verdad de especificación temprana.

### `src/`
Ubicación reservada para interfaces y componentes compartidos, no para microservicios completos. Fuente de verdad futura.

### `tests/`
Pruebas de contrato e integración multi-servicio. Fuente de verdad para QA global.

### `ops/`
Operación global, observabilidad, pipelines coordinados y runbooks. Fuente de verdad operacional.

### `agents/`
Activos específicos para agentes del proyecto. Fuente de soporte.

### `artifacts/`
Documentación exportada y resultados generados. Salida derivada.
