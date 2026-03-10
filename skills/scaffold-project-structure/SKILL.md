---
name: scaffold-project-structure
description: "Procedimiento para crear la base estructural de un repositorio de gobernanza para proyectos de microservicios en modelo multi-repo. Usa plantillas relativas del repo y fallback global."
license: MIT
compatibility: opencode
---

## Que hace esta skill

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
│   └── use-cases/
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

Plantillas obligatorias:

- `templates/executive-report.template.html`
- `templates/functional-requirement.template.md`

Destinos obligatorios en el proyecto generado:

- `docs/templates/executive-report.template.html`
- `docs/templates/functional-requirement.template.md`
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
- `backlog/use-cases`
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
- `traceability/requirements_trace.md`
- `traceability/end_to_end_traceability.csv`
- `traceability/epics_to_use_cases.md`
- `traceability/RTM.yaml`
- `traceability/use_cases_to_openapi.md`
- `services/registry.yaml`
- `docs/refinement/sessions/INDEX.md`
- `PROJECT_REPORT.html`

Crear tambien placeholders vacios donde aplique:

- `services/contracts/.gitkeep`
- `spec/open-api/.gitkeep`
- `src/.gitkeep`
- `tests/.gitkeep`
- `ops/.gitkeep`

### Paso 4 - Copiar plantillas

Intentar primero copiar desde rutas relativas del repo actual.

Unix:

```bash
cp templates/executive-report.template.html docs/templates/executive-report.template.html
cp templates/functional-requirement.template.md docs/templates/functional-requirement.template.md
cp templates/functional-requirement.template.md docs/requirements/templates/functional-requirement.template.md
```

Windows:

```cmd
copy "templates\executive-report.template.html" "docs\templates\executive-report.template.html"
copy "templates\functional-requirement.template.md" "docs\templates\functional-requirement.template.md"
copy "templates\functional-requirement.template.md" "docs\requirements\templates\functional-requirement.template.md"
```

Si la ruta relativa no existe o falla la copia, usar fallback global:

Unix:

```bash
cp ~/.config/opencode/templates/executive-report.template.html docs/templates/executive-report.template.html
cp ~/.config/opencode/templates/functional-requirement.template.md docs/templates/functional-requirement.template.md
cp ~/.config/opencode/templates/functional-requirement.template.md docs/requirements/templates/functional-requirement.template.md
```

Si ambos metodos fallan, leer el contenido con `read` y escribirlo con `write`.

### Paso 5 - Inicializar trazabilidad

Crear estructuras vacias y validas:

- `traceability/requirements_trace.md`
- `traceability/end_to_end_traceability.csv`
- `traceability/epics_to_use_cases.md`
- `traceability/RTM.yaml` con `enlaces: []`
- `traceability/use_cases_to_openapi.md`

### Paso 6 - Inicializar registro de servicios

Crear `services/registry.yaml` con estructura completa y `services: []`.

No inventar servicios.

### Paso 7 - Generar informe ejecutivo

Usar `docs/templates/executive-report.template.html` para generar `PROJECT_REPORT.html`.

- Sustituir placeholders por valores reales.
- Copiar tambien el resultado a `docs/executive-reports/INF-EJE-001.html`.

### Paso 8 - Validar coherencia final

Confirmar que:

- existen todos los ficheros obligatorios,
- las plantillas fueron copiadas,
- no hay placeholders sin sustituir en documentos instanciados,
- `services/registry.yaml` y `traceability/RTM.yaml` tienen estructura valida,
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
- no depende exclusivamente de rutas hardcodeadas fuera del repo.
