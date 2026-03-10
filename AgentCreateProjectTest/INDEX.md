# INDEX — AgentCreateProjectNoDupTrace

## Raíz del repositorio

| Ruta | Finalidad | Artefactos | Naturaleza | Referencias externas |
|---|---|---|---|---|
| `README.md` | Presentación general del repositorio | Guía inicial | Fuente de verdad | No |
| `INDEX.md` | Índice estructural del repositorio | Catálogo de carpetas y usos | Fuente de verdad | No |
| `AGENTS.md` | Definición de agentes y responsabilidades | Catálogo operativo | Fuente de verdad | No |
| `PROJECT_REPORT.html` | Informe ejecutivo generado | Salida HTML | Salida derivada | No |
| `.opencode/` | Soporte de automatización | Configuración de agentes, comandos y skills | Fuente de verdad operativa | No |
| `docs/` | Documentación de proyecto | Markdown y HTML | Mixto | Puede referenciar repos externos |
| `traceability/` | Trazabilidad central | Markdown, CSV y YAML | Fuente de verdad | Sí |
| `backlog/` | Backlog funcional | Épicas e historias | Fuente de verdad | Puede enlazar repos externos |
| `services/` | Registro de servicios y contratos | YAML y contratos | Fuente de verdad | Sí |
| `spec/` | Especificaciones técnicas | OpenAPI y artefactos SDD | Fuente de verdad técnica | Sí |
| `src/` | Activos compartidos futuros | Interfaces y tipos base | Fuente de verdad futura | Sí |
| `tests/` | Pruebas globales futuras | Contrato e integración | Fuente de verdad futura | Sí |
| `ops/` | Operación global futura | Runbooks, observabilidad, CI/CD | Fuente de verdad futura | Sí |
| `agents/` | Recursos agénticos del proyecto | Prompts y artefactos | Fuente de verdad operativa | No |
| `artifacts/` | Salidas exportadas | Artefactos generados | Salida derivada | No |

## Carpetas principales

### `.opencode/`

- **Finalidad:** soporte interno para automatización y trabajo de agentes.
- **Artefactos:** configuraciones, comandos y skills del proyecto.
- **Naturaleza:** fuente de verdad operativa.
- **Repos externos:** no contiene código externo, aunque puede orquestarlo.

### `docs/project/`

- **Finalidad:** describir visión, alcance, glosario y stakeholders.
- **Artefactos:** documentos base de entendimiento del proyecto.
- **Naturaleza:** fuente de verdad de contexto.
- **Repos externos:** no.

### `docs/requirements/functional/`

- **Finalidad:** almacenar requisitos funcionales aprobados.
- **Artefactos:** documentos FRS reales.
- **Naturaleza:** fuente de verdad.
- **Repos externos:** no, salvo referencias de trazabilidad.

### `docs/requirements/technical/`

- **Finalidad:** restricciones, criterios técnicos y no funcionales iniciales.
- **Artefactos:** documentos técnicos de soporte.
- **Naturaleza:** fuente de verdad.
- **Repos externos:** no.

### `docs/requirements/templates/`

- **Finalidad:** plantillas reutilizables para requisitos.
- **Artefactos:** plantillas Markdown.
- **Naturaleza:** fuente de verdad de formato.
- **Repos externos:** no.

### `docs/architecture/`

- **Finalidad:** arquitectura global y decisiones cross-servicio.
- **Artefactos:** diagramas, catálogos, modelos de comunicación.
- **Naturaleza:** fuente de verdad.
- **Repos externos:** sí, mediante referencias a servicios.

### `docs/adr/`

- **Finalidad:** decisiones arquitectónicas globales.
- **Artefactos:** ADRs.
- **Naturaleza:** fuente de verdad.
- **Repos externos:** puede referenciar servicios afectados.

### `docs/refinement/`

- **Finalidad:** registrar preguntas abiertas, sesiones y evidencias.
- **Artefactos:** índices, notas y evidencias.
- **Naturaleza:** fuente de verdad de refinamiento.
- **Repos externos:** no.

### `docs/executive-reports/`

- **Finalidad:** almacenar informes ejecutivos generados.
- **Artefactos:** HTML o documentos de reporte.
- **Naturaleza:** salida derivada controlada.
- **Repos externos:** no.

### `docs/qa/`

- **Finalidad:** estrategia de calidad y pruebas cross-servicio.
- **Artefactos:** estrategia, criterios y evidencias futuras.
- **Naturaleza:** fuente de verdad.
- **Repos externos:** sí, por cobertura de servicios.

### `docs/templates/`

- **Finalidad:** centralizar plantillas y ejemplos.
- **Artefactos:** HTML, Markdown y ejemplos de referencia.
- **Naturaleza:** fuente de verdad de formato.
- **Repos externos:** no.

### `traceability/`

- **Finalidad:** mantener trazabilidad del proyecto sin duplicar matrices derivadas.
- **Artefactos:** `requirements_trace.md`, `end_to_end_traceability.csv`, `RTM.yaml`.
- **Naturaleza:** fuente de verdad.
- **Repos externos:** sí, mediante `repo_url`, `pr_url` y `commit_sha`.

### `backlog/epics/`

- **Finalidad:** registrar épicas del proyecto.
- **Artefactos:** documentos E-NNN.
- **Naturaleza:** fuente de verdad.
- **Repos externos:** puede enlazar servicios.

### `backlog/user-stories/`

- **Finalidad:** registrar historias de usuario derivadas.
- **Artefactos:** documentos US-NNN.
- **Naturaleza:** fuente de verdad.
- **Repos externos:** puede enlazar repos de servicio y pruebas.

### `services/`

- **Finalidad:** registrar repos de microservicios y contratos públicos.
- **Artefactos:** `registry.yaml`, contratos OpenAPI/AsyncAPI.
- **Naturaleza:** fuente de verdad.
- **Repos externos:** sí, es un registro de ellos.

### `spec/open-api/`

- **Finalidad:** preparar definiciones OpenAPI en análisis.
- **Artefactos:** YAML futuros.
- **Naturaleza:** fuente de verdad técnica futura.
- **Repos externos:** sí, por servicio destino.

### `src/`

- **Finalidad:** activos compartidos transversales futuros.
- **Artefactos:** interfaces, SDKs y tipos base.
- **Naturaleza:** fuente de verdad futura.
- **Repos externos:** sí, serán consumidos por servicios.

### `tests/`

- **Finalidad:** pruebas de contrato e integración globales.
- **Artefactos:** suites y fixtures futuros.
- **Naturaleza:** fuente de verdad futura.
- **Repos externos:** sí, validan varios servicios.

### `ops/`

- **Finalidad:** operación global del ecosistema.
- **Artefactos:** runbooks, observabilidad y automatización futura.
- **Naturaleza:** fuente de verdad operativa futura.
- **Repos externos:** sí, coordina varios repos.

### `agents/`

- **Finalidad:** materiales locales para agentes del proyecto.
- **Artefactos:** prompts, guías y recursos de colaboración.
- **Naturaleza:** fuente de verdad operativa.
- **Repos externos:** no.

### `artifacts/`

- **Finalidad:** almacenar salidas generadas automáticamente.
- **Artefactos:** exportaciones y entregables automáticos.
- **Naturaleza:** salida derivada.
- **Repos externos:** no.
