---
name: scaffold-project-structure
description: "Procedimiento para crear la base estructural de un repositorio de gobernanza para proyectos de microservicios en modelo multi-repo. Usa plantillas relativas del repo y fallback global."
license: MIT
compatibility: opencode
---

## Que hace esta skill

Esta skill debe ejecutarse preferentemente con el modelo gratuito `gemini-3-flash` cuando la plataforma permita fijar modelo para el agente o subagente que la consume.

Esta skill describe como crear, desde cero, un **repositorio de gobernanza** para un proyecto con arquitectura de microservicios bajo modelo **multi-repo**.

El resultado esperado es un repositorio central de gobierno que contiene:

- documentacion del proyecto,
- requisitos funcionales y tecnicos,
- trazabilidad,
- backlog funcional,
- registro de servicios y contratos,
- soporte para QA, ops y agentes,
- plantillas reutilizables.

No crea microservicios, frontends ni infraestructura de despliegue por servicio.

## Convenciones de rutas

### En la plataforma actual

Los assets versionados viven en estas rutas del repositorio de la plataforma:

- `agents/`
- `skills/`
- `templates/`

### En el proyecto generado

El proyecto generado debe incluir, como minimo, esta estructura:

```text
/
├── README.md
├── INDEX.md
├── AGENTS.md
├── PROJECT_REPORT.html
├── .opencode/
│   ├── agents/
│   ├── commands/
│   └── skills/
├── docs/
│   ├── project/
│   ├── requirements/
│   │   ├── functional/
│   │   ├── technical/
│   │   └── templates/
│   ├── architecture/
│   ├── adr/
│   ├── refinement/
│   │   ├── sessions/
│   │   ├── evidence/
│   │   └── pending-questions.md
│   ├── executive-reports/
│   ├── qa/
│   └── templates/
├── traceability/
├── backlog/
│   ├── epics/
│   └── user-stories/
├── services/
│   ├── registry.yaml
│   └── contracts/
├── spec/
│   └── open-api/
├── src/
├── tests/
├── ops/
├── agents/
└── artifacts/
```

## Variables requeridas

| Variable | Origen |
|---|---|
| `PROJECT_NAME` | nombre del proyecto |
| `BASE_DIR` | directorio destino base |
| `PROJECT_DESCRIPTION` | descripcion breve del proyecto |
| `DATE` | fecha actual en formato `YYYY-MM-DD` |

## Resolucion de plantillas

Resolver siempre las plantillas con este orden:

1. `templates/` del repositorio actual
2. `~/.config/opencode/templates/` como fallback global

Contenido obligatorio a copiar desde `templates/`:

- `functional-requirement.template.md`
- `user-story.template.md`
- `epic.template.md`
- `executive-report.template.html`
- `examples/DOC-BUS/analysis/Documento inicial de analisis.txt`
- `examples/DOC-BUS/doc/epics/EPIC-UBUS-01 — Autoservicio digital para información operativa y ticketing básico en autobús urbano.md`
- `examples/DOC-BUS/doc/requirements/FRS-UBUS-001 — Consulta de próximas llegadas e incidencias por parada urbana.md`
- `examples/DOC-BUS/doc/user-stories/US-UBUS-001 — Como viajero quiero consultar próximas llegadas por parada para decidir si espero o cambio de ruta.md`
- `examples/DOC-BUS/spec/open-api/urban-bus-arrivals.openapi.yaml`
- y cualquier otro fichero o carpeta adicional bajo `templates/` que esté disponible en el origen.

Destinos obligatorios en el proyecto generado:

- `docs/templates/` con el contenido completo de `templates/` preservando estructura relativa; este directorio es el scaffold folder oficial de plantillas del proyecto generado
- `docs/requirements/templates/functional-requirement.template.md`

## Procedimiento

### Paso 1 - Verificar el directorio destino

Comprobar si `{BASE_DIR}/{PROJECT_NAME}` ya existe.

- Si no existe, continuar.
- Si existe y esta vacio, continuar.
- Si existe con contenido, no sobrescribir; comparar contra la estructura objetivo y crear solo los faltantes.

### Paso 2 - Crear la estructura base

Crear las carpetas raiz y subcarpetas minimas del repositorio de gobernanza:

- `.opencode/agents`
- `.opencode/commands`
- `.opencode/skills`
- `docs/project`
- `docs/requirements/functional`
- `docs/requirements/technical`
- `docs/requirements/templates`
- `docs/architecture`
- `docs/adr`
- `docs/refinement/sessions`
- `docs/refinement/evidence`
- `docs/executive-reports`
- `docs/qa`
- `docs/templates`
- `traceability`
- `backlog/epics`
- `backlog/user-stories`
- `services/contracts`
- `spec/open-api`
- `src`
- `tests`
- `ops`
- `agents`
- `artifacts`

### Paso 3 - Crear ficheros base obligatorios

Crear como minimo:

- `README.md`
- `INDEX.md`
- `AGENTS.md`
- `docs/project/README.md`
- `docs/project/vision.md`
- `docs/project/scope.md`
- `docs/project/stakeholders.md`
- `docs/project/glossary.md`
- `docs/requirements/technical/README.md`
- `traceability/requirements_trace.md`
- `traceability/end_to_end_traceability.csv`
- `traceability/RTM.yaml`
- `services/registry.yaml`
- `docs/refinement/pending-questions.md`
- `docs/refinement/sessions/INDEX.md`
- `PROJECT_REPORT.html`
- `docs/executive-reports/INF-EJE-001.html`

Crear tambien placeholders vacios donde aplique:

- `services/contracts/.gitkeep`
- `spec/open-api/.gitkeep`
- `src/.gitkeep`
- `tests/.gitkeep`
- `ops/.gitkeep`
- `docs/refinement/evidence/.gitkeep`
- `backlog/epics/.gitkeep`
- `backlog/user-stories/.gitkeep`
- `docs/requirements/functional/.gitkeep`

### Paso 4 - Copiar plantillas

Intentar primero copiar todo `templates/` desde rutas relativas del repo actual al scaffold folder `docs/templates/`, preservando su estructura completa y todos los archivos disponibles.

Unix:

```bash
cp -R templates/. docs/templates/
cp templates/functional-requirement.template.md docs/requirements/templates/functional-requirement.template.md
```

Windows:

```cmd
xcopy "templates" "docs\templates" /E /I /Y
copy "templates\functional-requirement.template.md" "docs\requirements\templates\functional-requirement.template.md"
```

Si la ruta relativa no existe o falla la copia, usar fallback global:

Unix:

```bash
cp -R ~/.config/opencode/templates/. docs/templates/
cp ~/.config/opencode/templates/functional-requirement.template.md docs/requirements/templates/functional-requirement.template.md
```

Si ambos metodos fallan, leer el contenido con `read` y escribirlo con `write`, preservando toda la estructura relativa de `templates/` dentro de `docs/templates/` y sin omitir ningun archivo del origen.

### Paso 5 - Inicializar trazabilidad

Crear estructuras vacias y validas sin duplicar relaciones ya trazadas en `epic`, `FRS`, `user-story` o `RTM.yaml`:

- `traceability/requirements_trace.md`
- `traceability/end_to_end_traceability.csv`
- `traceability/RTM.yaml` con `enlaces: []`

### Paso 6 - Inicializar registro de servicios

Crear `services/registry.yaml` con estructura completa y `services: []`.

No inventar servicios.

### Paso 7 - Persistir carpetas vacias para Git

Si una carpeta importante no tiene contenido real todavia, asegurar su persistencia con `.gitkeep` o un `README.md` minimo.

Como minimo:

- `services/contracts/.gitkeep`
- `spec/open-api/.gitkeep`
- `src/.gitkeep`
- `tests/.gitkeep`
- `ops/.gitkeep`
- `docs/refinement/evidence/.gitkeep`
- `backlog/epics/.gitkeep`
- `backlog/user-stories/.gitkeep`
- `docs/requirements/functional/.gitkeep`

### Paso 8 - Generar informe ejecutivo

Usar `docs/templates/executive-report.template.html` para generar `PROJECT_REPORT.html`.

- Sustituir placeholders por valores reales.
- Copiar tambien el resultado a `docs/executive-reports/INF-EJE-001.html`.
- Si se necesita Python para generar o validar, usar `python3` si `python` no existe.

### Paso 9 - Validar coherencia final

Confirmar que:

- existen todos los ficheros obligatorios,
- las plantillas fueron copiadas,
- todo el contenido disponible en `templates/` fue copiado a `docs/templates/`,
- `docs/templates/` contiene el arbol completo del origen de plantillas disponible,
- la carpeta `docs/templates/examples/` existe cuando el origen `templates/examples/` esta disponible,
- no hay placeholders sin sustituir en documentos instanciados fuera de `docs/templates/` y `docs/requirements/templates/`,
- `services/registry.yaml` contiene `services: []`,
- `traceability/RTM.yaml` contiene `enlaces: []`,
- existen `PROJECT_REPORT.html` y `docs/executive-reports/INF-EJE-001.html`,
- no existen matrices de trazabilidad derivadas que dupliquen relaciones ya mantenidas en plantillas fuente y `RTM.yaml`,
- las carpetas criticas vacias siguen siendo rastreables por Git,
- el repositorio queda listo para evolucionar con agentes y equipos humanos.

## Lo que esta skill no hace

- No crea repositorios de microservicios
- No implementa logica de negocio
- No define cloud provider
- No genera pipelines concretos de despliegue por servicio
- No hace `git commit` ni `git push` automaticamente

## Criterio de exito

La skill queda bien aplicada si el repositorio generado:

- es entendible para un miembro nuevo del equipo,
- usa modelo multi-repo con repositorio central de gobernanza,
- deja trazabilidad lista desde el inicio,
- reutiliza plantillas versionadas desde `templates/` o su fallback global,
- persiste en Git las carpetas criticas aunque esten vacias,
- no depende exclusivamente de rutas hardcodeadas fuera del repo.
