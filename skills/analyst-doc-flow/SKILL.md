---
name: analyst-doc-flow
description: "Procedimiento operativo para analizar un documento de negocio confirmado por el usuario y derivar Epica, FRS, User Stories, OpenAPI y trazabilidad sin duplicaciones."
license: MIT
compatibility: opencode
---

## Objetivo

Esta skill define el flujo operativo detallado de `AgentAnalystDocFlow` para mantener la especificacion del agente mas corta, estricta y mantenible.

El agente debe usar esta skill como fuente procedimental principal una vez el usuario haya confirmado explicitamente el documento fuente.

Debe complementar esta skill con las reglas comunes definidas en:

```text
skills/functional-traceability-rules/SKILL.md
```

## Regla cero: seleccionar un BRS pendiente con el usuario

Nunca analizar sin eleccion explicita del usuario.

Ruta base obligatoria para detectar candidatos:

```text
/docs/requirements/functional/
```

Reglas:

1. Si la instruccion inicial ya incluye una ruta exacta o un nombre inequívoco, usarlo como candidato confirmado por el usuario.
2. Si la instruccion inicial no incluye documento exacto, escanear `/docs/requirements/functional/` para detectar BRS pendientes.
3. Considerar como candidato BRS cualquier fichero bajo esa ruta que cumpla al menos uno de estos patrones, en este orden:
   - nombre `BRS-*.md`
   - fichero `*.md` dentro de carpeta `brs/` o `business-requirements/`
   - contenido con `BRS-`, `Business Requirement` o `Requisito de negocio`
4. Excluir candidatos ubicados en `epics/`, `frs/`, `us/`, `docs/templates/` o `docs/requirements/templates/` aunque contengan referencias a BRS.
5. Considerar pendiente un BRS que no figure en `docs/requirements/functional/.processed_documents.log`.
6. Presentar al usuario la lista de BRS pendientes y pedirle que elija uno explicitamente.
7. Si solo hay un pendiente, pedir igualmente confirmacion explicita.
8. Si no hay pendientes, pedir al usuario una ruta concreta o una instruccion expresa para usar un documento alternativo.
9. No usar ejemplos ni fallback sin confirmacion.
10. No leer ni procesar el contenido del BRS elegido hasta que el usuario lo confirme.

Orden recomendado de deteccion:

1. Buscar `BRS-*.md`.
2. Buscar `**/brs/*.md` y `**/business-requirements/*.md`.
3. Revisar contenido de otros `*.md` restantes bajo `/docs/requirements/functional/` solo si no hubo suficientes candidatos inequívocos en los pasos anteriores.

Plantilla de pregunta cuando existan pendientes:

```text
He detectado estos BRS pendientes en `/docs/requirements/functional/`. Indica cual quieres analizar usando la ruta exacta o el nombre del fichero.
```

Plantilla de pregunta cuando no existan pendientes:

```text
No he encontrado BRS pendientes en `/docs/requirements/functional/`. Indica el documento exacto a analizar (ruta o nombre inequívoco).
```

## Flujo documental oficial

```text
Epica -> FRS -> US -> OpenAPI -> AC -> GT -> Evidencia
                 \-> Riesgo -> Control -> GT/Evidencia
```

Reglas del flujo:

1. Una Epica puede derivar en una o varias FRS.
2. Una FRS puede derivar en una o varias US.
3. Si una US implica interaccion API, debe crearse o actualizarse un fichero de especificacion OpenAPI real en `spec/open-api/`.
4. Cada US debe contener `AC-*`, `GT-*` y `COV-*`.
5. La trazabilidad estructurada principal vive en `traceability/RTM.yaml`.
6. No crear matrices auxiliares redundantes si la misma relacion ya existe en Epica, FRS, US o `RTM.yaml`.

## Plantillas oficiales

Todos los documentos deben crearse desde `docs/templates/`.

| Documento | Plantilla |
|---|---|
| Epica | `docs/templates/epic.template.md` |
| FRS | `docs/templates/functional-requirement.template.md` |
| User Story | `docs/templates/user-story.template.md` |
| Salida final del agente | `docs/templates/analyst-doc-flow-output.template.md` |

Reglas:

- copiar la plantilla oficial
- sustituir placeholders por valores reales extraidos o inferidos razonablemente del documento fuente
- si falta informacion suficiente, usar `pendiente de refinamiento`
- nunca dejar placeholders `{{...}}` en documentos reales
- mantener la estructura y trazabilidad propia de cada plantilla

La respuesta final del agente debe seguir `docs/templates/analyst-doc-flow-output.template.md`. Si no existe en el proyecto, usar `templates/analyst-doc-flow-output.template.md` como fallback.

## Rutas oficiales

- epicas: `docs/requirements/functional/{modulo}/{submodulo}/epics/`
- FRS: `docs/requirements/functional/{modulo}/{submodulo}/frs/`
- user stories: `docs/requirements/functional/{modulo}/{submodulo}/us/`
- OpenAPI derivada: `spec/open-api/`
- trazabilidad estructurada: `traceability/RTM.yaml`

No usar `use-cases/`, `epics_to_use_cases.md` ni `use_cases_to_openapi.md`.

## Proteccion contra reprocesado

Antes de procesar, comprobar:

```text
docs/requirements/functional/.processed_documents.log
```

Formato esperado:

```text
timestamp | documento | modulo | submodulo | epics | frs | us | openapi
```

Si el documento ya fue procesado:

1. informar al usuario
2. mostrar el registro encontrado
3. abortar por defecto salvo instruccion explicita de reproceso

## Procedimiento detallado

### Paso 1 - Leer exclusivamente el documento confirmado

Antes de este paso, si el usuario no indico documento exacto, debes haber escaneado `/docs/requirements/functional/`, filtrado BRS pendientes y obtenido una eleccion explicita del usuario.

Extraer unicamente:

- problema de negocio
- objetivo
- alcance funcional
- actores y stakeholders
- restricciones funcionales
- eventos o procesos principales
- datos de entrada y salida si aparecen
- interacciones API si el documento las menciona o las hace inevitables

No deducir sin base documental:

- microservicios concretos
- arquitectura interna
- topologia tecnica
- soluciones de infraestructura

### Paso 2 - Escanear artefactos existentes

Revisar:

- `docs/requirements/functional/`
- `spec/open-api/`
- `traceability/RTM.yaml`

Detectar:

- epicas existentes reutilizables
- FRS existentes reutilizables
- US existentes reutilizables
- especificaciones OpenAPI existentes relacionadas

Estados reutilizables:

- `borrador`
- `en-revision`
- `en-refinamiento`

No modificar automaticamente artefactos aprobados o cerrados sin instruccion explicita.

Ademas, durante la seleccion inicial del documento, debes usar este mismo inventario para evitar ofrecer como pendientes documentos ya procesados.

### Paso 3 - Determinar modulo y submodulo funcional

Proponer modulo y submodulo funcional con base en el documento y en artefactos existentes.

Usar la mejor coincidencia semantica disponible.

Solo preguntar al usuario si la clasificacion es realmente ambigua y cambia materialmente la organizacion del repositorio.

### Paso 4 - Crear o actualizar Epica

Usar `docs/templates/epic.template.md`.

Antes de guardar, asegurar que existe:

```text
docs/requirements/functional/{modulo}/{submodulo}/epics/
```

Completar como minimo:

- objetivo de negocio
- contexto
- alcance
- stakeholders
- capacidades funcionales
- riesgos agregados
- FRS candidatas
- US candidatas si ya son identificables
- `LINK-NNN`

La epica debe trazar a FRS y US agregadas. No debe bajar a detalle de Gherkin individual.

### Paso 5 - Crear o actualizar FRS derivadas

Cada bloque funcional coherente del documento debe convertirse en una FRS.

Usar `docs/templates/functional-requirement.template.md`.

Antes de guardar, asegurar que existe:

```text
docs/requirements/functional/{modulo}/{submodulo}/frs/
```

Completar como minimo:

- descripcion
- alcance y limites
- actores
- entradas y salidas
- restricciones
- flujo principal y alternativos relevantes
- criterios de aceptacion iniciales
- riesgos y controles
- historias de usuario derivadas
- tests de alto nivel iniciales
- `LINK-NNN`

Si no hay informacion suficiente en una seccion, usar `pendiente de refinamiento`.

### Paso 6 - Crear o actualizar User Stories derivadas

Cada FRS debe derivar una o varias US cuando el documento permita descomponer comportamiento verificable.

Usar `docs/templates/user-story.template.md`.

Antes de guardar, asegurar que existe:

```text
docs/requirements/functional/{modulo}/{submodulo}/us/
```

Cada US debe contener como minimo:

- formato `Como / Quiero / Para`
- objetivo funcional
- actor principal
- criterios de aceptacion iniciales `AC-*`
- escenarios Gherkin iniciales `GT-*`
- trazabilidad de tests Gherkin
- trazabilidad de cobertura funcional y riesgo `COV-*`
- riesgos y controles
- `LINK-NNN`

### Paso 7 - Generar o actualizar OpenAPI cuando aplique

Si una US describe comportamiento API observable, crear o actualizar especificacion en `spec/open-api/`.

Reglas:

- debe existir un fichero real en `spec/open-api/`; no basta con mencionar OpenAPI en la US o en `RTM.yaml`
- la especificacion debe trazarse desde la US
- debe poder relacionarse con uno o mas `AC-*`
- debe poder verificarse con uno o mas `GT-*` cuando aplique
- no inventar endpoints o payloads no respaldados por el documento fuente
- usar `pendiente de refinamiento` cuando falte precision

### Paso 8 - Actualizar trazabilidad estructurada

Actualizar `traceability/RTM.yaml` para reflejar relaciones nuevas o modificadas, incluyendo los `openapi_files` realmente generados o actualizados.

Cada enlace puede incluir:

- `requisito`
- `historia`
- `openapi_files`
- `test_case`
- `servicio`
- `repo_url`
- `pr_url`
- `commit_sha`
- `estado`

No crear matrices auxiliares duplicadas.

### Paso 9 - Registrar procesamiento

Actualizar `docs/requirements/functional/.processed_documents.log` con el formato oficial.

### Paso 10 - Invocar validacion final

Invocar `AgentValidateDocFlow` sobre el repositorio actual en modo remediacion.

Esta invocacion es obligatoria y debe ocurrir despues de generar los ficheros OpenAPI y despues de actualizar `RTM.yaml` y `.processed_documents.log`.

Aceptar las correcciones automaticas que el validador pueda aplicar cuando exista evidencia suficiente.

Si el validador detecta decisiones funcionales no inferibles:

1. aplicar primero todas las correcciones automaticas posibles
2. trasladar al usuario una unica pregunta concreta
3. explicar que trazabilidad depende de esa respuesta

## Trazabilidad minima obligatoria

```text
Modulo
 -> Submodulo
   -> Epica
     -> FRS
       -> US
         -> OpenAPI (si aplica)
         -> AC
         -> GT
         -> COV
```

Reglas:

1. Toda FRS debe referenciar una unica epica.
2. Toda US debe referenciar una FRS principal.
3. Toda US debe referenciar una epica asociada.
4. Todo `AC-*` de una US debe quedar cubierto por al menos un `GT-*`.
5. Todo riesgo alto en una US debe aparecer en `COV-*`.
6. Toda OpenAPI derivada debe figurar en la US y, cuando aplique, en `RTM.yaml`.
7. Toda relacion jerarquica debe ser reciproca entre documentos cuando la plantilla correspondiente la soporte.

## Criterio de exito

El resultado es correcto solo si:

- el documento fue confirmado explicitamente antes del analisis
- el agente escaneo `/docs/requirements/functional/` cuando no se recibio una ruta exacta
- el usuario eligio explicitamente un BRS pendiente o un documento concreto antes del analisis
- el documento no fue reprocesado sin autorizacion
- existe al menos una epica valida o actualizada
- existen FRS derivadas coherentes con la epica
- existen US derivadas coherentes con cada FRS
- las US contienen `AC-*`, `GT-*` y `COV-*`
- la OpenAPI fue creada o actualizada como fichero real bajo `spec/open-api/` cuando la historia la requiere
- `traceability/RTM.yaml` refleja las relaciones nuevas
- no se crearon matrices duplicadas de trazabilidad
- todas las plantillas fueron usadas correctamente
- `AgentValidateDocFlow` fue invocado al final como validacion delegada obligatoria

## Ejemplos de invocacion

### Caso normal con ruta exacta

```text
Analiza `docs/input/documento-inicial-negocio.md`.
```

### Caso sin ruta exacta y con eleccion de BRS pendiente

```text
Analiza el siguiente BRS pendiente de `/docs/requirements/functional/`.
```

### Caso usando el comando dedicado

```text
/analyze-doc docs/input/documento-inicial-negocio.md
```

### Caso canonico DOC-BUS

```text
Analiza `templates/examples/DOC-BUS/analysis/Documento inicial de analisis.txt`.
```

### Caso de reproceso explicito

```text
Reprocesa `docs/input/documento-inicial-negocio.md` aunque ya exista en `.processed_documents.log`.
```
