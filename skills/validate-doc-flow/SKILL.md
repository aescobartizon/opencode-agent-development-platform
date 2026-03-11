---
name: validate-doc-flow
description: "Procedimiento detallado para validar y remediar trazabilidad funcional entre Epica, FRS, US, OpenAPI y RTM."
license: MIT
compatibility: opencode
---

## Objetivo

Esta skill define el flujo operativo detallado de `AgentValidateDocFlow` para mantener la especificacion del agente corta, estricta y mantenible.

Debe usarse junto con:

```text
skills/functional-traceability-rules/SKILL.md
```

## Fuente normativa principal

Tomar como base:

- `documentation-platform-sdd.md`
- `docs/templates/epic.template.md`
- `docs/templates/functional-requirement.template.md`
- `docs/templates/user-story.template.md`
- `skills/functional-traceability-rules/SKILL.md`

Si alguna plantilla oficial no existe, reportarlo como hallazgo de severidad alta.

## Flujo obligatorio

### Paso 1 - Descubrir artefactos reales

Inventariar:

- epicas
- FRS
- US
- OpenAPI
- RTM

Construir una vista de relaciones reales encontradas en el repositorio.

### Paso 2 - Validar integridad estructural

Validar como minimo:

- Epica con `EPIC-ID` y `LINK-NNN`
- FRS con `FRS-ID`, `EPIC-ID` y `LINK-NNN`
- US con `US-ID`, `EPIC-ID`, `FRS-ID` y `LINK-NNN`
- US con al menos un `AC-*`
- US con OpenAPI derivada cuando tenga impacto API

### Paso 3 - Validar coherencia jerarquica

Comprobar reciprocidad entre documentos:

- si una US referencia una FRS, la FRS debe listar esa US
- si una FRS referencia una epica, la epica debe listar esa FRS
- si una epica lista una US, esa US debe pertenecer a esa epica
- si una US declara OpenAPI derivada, la ruta debe existir bajo `spec/open-api/` o quedar justificada como pendiente

### Paso 4 - Validar cobertura funcional

Comprobar:

- todo `AC-*` en FRS aparece al menos en un `TC-*` cuando la plantilla lo soporte
- todo `AC-*` en US aparece al menos en un `GT-*`
- todo `GT-*` referencia exactamente un `AC-*`
- toda OpenAPI derivada queda asociada a `AC-*` y `GT-*` cuando aplica comportamiento observable

### Paso 5 - Validar cobertura de riesgos

Comprobar:

- todo riesgo alto en FRS aparece en `Tests de alto nivel` cuando la plantilla lo soporte
- todo riesgo alto en US aparece en `COV-*` tipo `riesgo`
- toda fila `COV-*` de tipo `riesgo` referencia un riesgo existente
- ningun riesgo marcado como cubierto carece de control validado

### Paso 6 - Validar evidencia

Comprobar:

- toda cobertura `cubierta` tiene evidencia
- toda cobertura `parcial` tiene nota o evidencia parcial
- ningun `GT-*` ejecutado carece de estado de prueba cuando aplique

### Paso 7 - Validar no duplicacion y estructuras legacy

Marcar hallazgo si aparecen artefactos como:

- `traceability/epics_to_use_cases.md`
- `traceability/use_cases_to_openapi.md`
- matrices manuales duplicadas de `Epica -> FRS`, `FRS -> US` o `US -> OpenAPI`
- `use-cases/`
- referencias activas a `Caso de uso` como artefacto principal del flujo actual

### Paso 8 - Emitir resultado consolidado

Clasificar cada regla validada como:

- `pass`
- `fail`
- `warning`
- `not-applicable`

Emitir un veredicto global:

- `conforme`
- `conforme con observaciones`
- `no conforme`

### Paso 9 - Remediar trazabilidad cuando sea posible

En modo `remediacion`, intentar actualizar automaticamente la trazabilidad si existe evidencia suficiente en los artefactos fuente.

Se puede corregir automaticamente:

- referencias reciprocas faltantes entre Epica, FRS y US cuando el contexto sea inequívoco
- referencias OpenAPI en US y `RTM.yaml` cuando el fichero exista y la relacion sea clara
- listas incompletas de FRS o US derivadas respaldadas por artefactos existentes
- inconsistencias menores de naming trazable
- enlaces `LINK-NNN` faltantes cuando ya exista entrada inequívoca en `RTM.yaml`
- `RTM.yaml` para incorporar relaciones estructuradas ya presentes en Epica, FRS, US y OpenAPI

No se puede corregir automaticamente:

- relaciones que requieran decidir alcance funcional
- OpenAPI no mencionada ni respaldada por la US o el documento fuente
- criterios de aceptacion inexistentes
- riesgos nuevos no documentados
- cambios que alteren semantica de negocio sin evidencia documental

Si una remediacion requiere criterio del usuario:

1. hacer primero todo lo corregible
2. formular una unica pregunta concreta
3. explicar exactamente que trazabilidad depende de esa respuesta

## Reglas `VAL-*` obligatorias

| Regla ID | Nivel | Validacion |
|---|---|---|
| VAL-001 | Epica | existe `EPIC-ID` |
| VAL-002 | Epica | existe `LINK-NNN` |
| VAL-003 | Epica | existe al menos una FRS derivada o pendiente justificada |
| VAL-004 | FRS | existe `FRS-ID` |
| VAL-005 | FRS | existe `EPIC-ID` |
| VAL-006 | FRS | existe `LINK-NNN` |
| VAL-007 | FRS | existe al menos una US derivada o pendiente justificada |
| VAL-008 | FRS | todo `AC-*` aparece en `TC-*` cuando aplica |
| VAL-009 | FRS | todo riesgo alto aparece en `TC-*` cuando aplica |
| VAL-010 | US | existe `US-ID` |
| VAL-011 | US | existe `EPIC-ID` |
| VAL-012 | US | existe `FRS-ID` |
| VAL-013 | US | existe `LINK-NNN` |
| VAL-014 | US | si hay impacto API, existe referencia OpenAPI en `spec/open-api/` |
| VAL-015 | US | existe al menos un `AC-*` |
| VAL-016 | US | todo `AC-*` aparece en `GT-*` |
| VAL-017 | US | todo `GT-*` referencia exactamente un `AC-*` |
| VAL-018 | US | toda OpenAPI derivada queda trazada a `AC-*` y `GT-*` cuando aplica |
| VAL-019 | US | todo riesgo alto aparece en `COV-*` tipo `riesgo` |
| VAL-020 | US | toda fila `COV-*` con estado `cubierta` tiene evidencia |
| VAL-021 | Cross | FRS y US son reciprocas en su relacion |
| VAL-022 | Cross | Epica y FRS son reciprocas en su relacion |

## Severidad de hallazgos

Clasificar hallazgos asi:

- `alta`: rompe flujo, trazabilidad o validez del artefacto
- `media`: inconsistencia importante, pero con workaround o acotada
- `baja`: desviacion menor de convencion o presentacion

Ejemplos de severidad alta:

- OpenAPI referenciada en US pero inexistente en `spec/open-api/`
- FRS sin epica de origen
- US sin FRS principal
- `AC-*` sin cobertura `GT-*`
- cobertura `cubierta` sin evidencia

## Salida final

Al finalizar debes mostrar:

## Alcance validado

lista de rutas y artefactos revisados

## Resultado global

`conforme`, `conforme con observaciones` o `no conforme`

## Modo ejecutado

`validacion` o `remediacion`

## Resumen por nivel

- Epicas
- FRS
- US
- OpenAPI
- RTM

## Reglas VAL evaluadas

tabla resumida con `VAL-*` y estado `pass/fail/warning/not-applicable`

## Hallazgos

Por cada hallazgo incluir:

- severidad
- artefacto
- identificador
- regla afectada
- descripcion
- accion correctiva sugerida

## Correcciones aplicadas automaticamente

lista de cambios de trazabilidad aplicados por el agente

## Pendientes que requieren decision del usuario

lista corta de decisiones funcionales no inferibles, solo si existen

## Inconsistencias de trazabilidad

lista explicita de relaciones no reciprocas, faltantes o duplicadas

## Recomendacion final

acciones prioritarias para dejar el flujo conforme
