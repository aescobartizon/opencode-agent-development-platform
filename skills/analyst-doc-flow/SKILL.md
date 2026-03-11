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
3. Si una US implica interaccion API, debe crearse o actualizarse un fichero de especificacion OpenAPI real en `spec/open-api/{modulo}/{submodulo}/`.
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
- para FRS es obligatorio usar `docs/templates/functional-requirement.template.md`
- para User Story es obligatorio usar `docs/templates/user-story.template.md`
- no se permite crear FRS ni US desde cero sin partir de esas plantillas
- no se permite inventar datos no presentes en el BRS o documento fuente para rellenar secciones de FRS o US
- cualquier seccion sin evidencia suficiente debe quedar como `pendiente de refinamiento`

La respuesta final del agente debe seguir `docs/templates/analyst-doc-flow-output.template.md`. Si no existe en el proyecto, usar `templates/analyst-doc-flow-output.template.md` como fallback.

## Rutas oficiales

- epicas: `docs/requirements/functional/{modulo}/{submodulo}/epics/`
- FRS: `docs/requirements/functional/{modulo}/{submodulo}/frs/`
- user stories: `docs/requirements/functional/{modulo}/{submodulo}/us/`
- OpenAPI derivada: `spec/open-api/{modulo}/{submodulo}/`
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

### Paso 3 - Solicitar modulo funcional y submodulo funcional

Debes preguntar explicitamente al usuario el modulo funcional y el submodulo funcional antes de crear directorios o guardar artefactos.

Puedes proponer una opcion recomendada basada en el documento y en artefactos existentes, pero no debes crear la estructura sin confirmacion explicita.

La pregunta debe pedir ambos valores en el mismo turno y dejar claro que se usaran para crear:

```text
docs/requirements/functional/{modulo}/{submodulo}/
```

### Paso 4 - Crear estructura funcional

Una vez confirmados modulo y submodulo, asegurar que existen:

```text
docs/requirements/functional/{modulo}/{submodulo}/epics/
docs/requirements/functional/{modulo}/{submodulo}/frs/
docs/requirements/functional/{modulo}/{submodulo}/us/
spec/open-api/{modulo}/{submodulo}/
```

### Paso 5 - Crear o actualizar Epica

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

### Paso 6 - Crear o actualizar FRS derivadas

Cada bloque funcional coherente del documento debe convertirse en una FRS.

Usar `docs/templates/functional-requirement.template.md`.

Esto es obligatorio. No se permite crear una FRS desde cero sin partir de esa plantilla.

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

No inventar informacion que no este explicitamente respaldada por el BRS o documento fuente confirmado.

### Paso 7 - Crear o actualizar User Stories derivadas

Cada FRS debe derivar una o varias US cuando el documento permita descomponer comportamiento verificable.

Usar `docs/templates/user-story.template.md`.

Esto es obligatorio. No se permite crear una US desde cero sin partir de esa plantilla.

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

Si falta informacion para cualquier apartado de la US, usar `pendiente de refinamiento` y no inventar contenido no respaldado por el BRS.

### Paso 8 - Generar o actualizar OpenAPI cuando aplique

Si una US describe comportamiento API observable, crear o actualizar especificacion en `spec/open-api/{modulo}/{submodulo}/`.

Reglas:

- debe existir un fichero real en `spec/open-api/{modulo}/{submodulo}/`; no basta con mencionar OpenAPI en la US o en `RTM.yaml`
- la ruta del fichero debe reflejar el mismo `modulo` y `submodulo` confirmado para los artefactos funcionales
- la especificacion debe trazarse desde la US
- debe poder relacionarse con uno o mas `AC-*`
- debe poder verificarse con uno o mas `GT-*` cuando aplique
- no inventar endpoints o payloads no respaldados por el documento fuente
- usar `pendiente de refinamiento` cuando falte precision

### Paso 9 - Chequeo interno obligatorio de FRS, US y OpenAPI

Antes de actualizar `RTM.yaml` y antes de invocar `AgentValidateDocFlow`, debes comprobar como minimo:

- toda FRS nueva o modificada referencia la epica correcta
- toda FRS nueva o modificada fue instanciada desde `docs/templates/functional-requirement.template.md`
- toda seccion de FRS sin evidencia suficiente quedo como `pendiente de refinamiento`
- toda US nueva o modificada referencia su FRS y su epica
- toda US nueva o modificada fue instanciada desde `docs/templates/user-story.template.md`
- toda seccion de US sin evidencia suficiente quedo como `pendiente de refinamiento`
- toda US contiene `AC-*`, `GT-*` y `COV-*`
- toda OpenAPI generada existe como fichero real bajo `spec/open-api/{modulo}/{submodulo}/`
- toda OpenAPI generada esta referenciada desde la US correspondiente
- no hay OpenAPI generada sin historia fuente que la respalde
- no hay OpenAPI generada fuera del `modulo` y `submodulo` confirmados para esa ejecucion

Si detectas inconsistencias basicas y puedes corregirlas con evidencia documental directa, debes corregirlas antes de continuar.

### Paso 10 - Actualizar trazabilidad estructurada

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

### Paso 11 - Registrar procesamiento

Actualizar `docs/requirements/functional/.processed_documents.log` con el formato oficial.

### Paso 12 - Invocar validacion final

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
- el usuario confirmo explicitamente modulo funcional y submodulo funcional antes de crear directorios
- el documento no fue reprocesado sin autorizacion
- existe al menos una epica valida o actualizada
- las FRS fueron instanciadas desde `docs/templates/functional-requirement.template.md`
- las US fueron instanciadas desde `docs/templates/user-story.template.md`
- existen FRS derivadas coherentes con la epica
- existen US derivadas coherentes con cada FRS
- cualquier apartado sin evidencia suficiente en FRS o US quedo marcado como `pendiente de refinamiento`
- no se invento informacion no respaldada por el BRS o documento fuente
- las US contienen `AC-*`, `GT-*` y `COV-*`
- la OpenAPI fue creada o actualizada como fichero real bajo `spec/open-api/{modulo}/{submodulo}/` cuando la historia la requiere
- se ejecuto un chequeo interno satisfactorio de FRS, US y OpenAPI antes de delegar la validacion final
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
