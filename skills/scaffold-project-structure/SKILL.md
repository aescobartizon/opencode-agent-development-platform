---
name: scaffold-project-structure
description: "Procedimiento minimo para crear la estructura basica del proyecto y copiar `templates/` a `docs/templates/`."
license: MIT
compatibility: opencode
---

## Objetivo

Esta skill solo cubre dos responsabilidades:

1. crear la estructura basica del proyecto
2. copiar todo `templates/` a `docs/templates/`

## Variables requeridas

| Variable | Origen |
|---|---|
| `PROJECT_NAME` | nombre del proyecto |
| `PROJECT_DESCRIPTION` | descripcion breve |
| `BASE_DIR` | directorio destino base |

## Reglas obligatorias

1. No crear nada si falta `PROJECT_NAME`.
2. No crear nada si falta `PROJECT_DESCRIPTION`.
3. No generar el scaffold en la raiz actual.
4. Crear obligatoriamente `{BASE_DIR}/{PROJECT_NAME}`.
5. Todo debe generarse dentro de `{BASE_DIR}/{PROJECT_NAME}`.

## Estructura basica obligatoria

Crear dentro de `{BASE_DIR}/{PROJECT_NAME}`:

```text
README.md
INDEX.md
AGENTS.md
.opencode/agents/
.opencode/commands/
.opencode/skills/
docs/project/
docs/requirements/functional/
docs/requirements/technical/
docs/requirements/templates/
docs/architecture/
docs/adr/
docs/refinement/sessions/
docs/refinement/evidence/
docs/executive-reports/
docs/qa/
docs/templates/
traceability/
backlog/epics/
backlog/user-stories/
services/contracts/
spec/open-api/
src/
tests/
ops/
agents/
artifacts/
```

## Copia de plantillas

Resolver el origen en este orden:

1. `templates/`
2. `~/.config/opencode/templates/`

Copiar todo el contenido disponible a:

```text
{BASE_DIR}/{PROJECT_NAME}/docs/templates/
```

Tambien copiar:

```text
functional-requirement.template.md -> {BASE_DIR}/{PROJECT_NAME}/docs/requirements/templates/functional-requirement.template.md
```

Si la copia por comandos falla, leer y escribir preservando toda la estructura relativa.

## Criterio de exito

La skill queda bien aplicada solo si:

- existe `{BASE_DIR}/{PROJECT_NAME}`
- la estructura basica existe dentro de esa carpeta
- `docs/templates/` contiene todo el arbol de `templates/` o su fallback
- `docs/requirements/templates/functional-requirement.template.md` existe
- no se creo nada fuera de la carpeta del proyecto
