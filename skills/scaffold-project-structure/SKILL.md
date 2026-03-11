---
name: scaffold-project-structure
description: "Procedimiento minimo para crear la estructura basica del proyecto y copiar todo `./templates/` a `./docs/templates/`."
license: MIT
compatibility: opencode
---

## Objetivo

Esta skill solo cubre dos responsabilidades:

1. crear la estructura basica del proyecto
2. copiar todo `./templates/` a `./docs/templates/`

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


## Criterio de exito

La skill queda bien aplicada solo si:

- existe `{BASE_DIR}/{PROJECT_NAME}`
- la estructura basica existe dentro de esa carpeta
- `docs/templates/` contiene todo el contenido de `/home/vant/.opencode/templates/`
- no se creo nada fuera de la carpeta del proyecto
