---
name: functional-traceability-rules
description: "Reglas compartidas de flujo funcional y trazabilidad para agentes de analisis y validacion documental."
license: MIT
compatibility: opencode
---

## Objetivo

Esta skill centraliza las reglas comunes de trazabilidad funcional usadas por `AgentAnalystDocFlow` y `AgentValidateDocFlow`.

Debe usarse como referencia comun para evitar duplicacion normativa entre agentes.

## Flujo oficial

```text
Epica -> FRS -> US -> OpenAPI -> AC -> GT -> Evidencia
                 \-> Riesgo -> Control -> GT/Evidencia
```

## Fuente estructurada principal

La matriz estructurada principal es:

```text
traceability/RTM.yaml
```

No crear matrices auxiliares duplicadas cuando la relacion ya exista en Epica, FRS, US o `RTM.yaml`.

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

## Reglas compartidas

1. Toda Epica debe poder derivar en una o varias FRS.
2. Toda FRS debe referenciar una unica Epica.
3. Toda FRS debe poder derivar en una o varias US.
4. Toda US debe referenciar una FRS principal.
5. Toda US debe referenciar una Epica asociada.
6. Si una US tiene impacto API, debe existir OpenAPI derivada o una justificacion explicita de pendiente de refinamiento.
7. Todo `AC-*` de una US debe quedar cubierto por al menos un `GT-*`.
8. Todo `GT-*` debe referenciar exactamente un `AC-*`.
9. Todo riesgo alto en una US debe aparecer en `COV-*`.
10. Toda OpenAPI derivada debe figurar en la US y, cuando aplique, en `RTM.yaml`.
11. Toda relacion jerarquica debe ser reciproca entre documentos cuando la plantilla correspondiente la soporte.
12. No usar estructuras legacy como `use-cases/`, `epics_to_use_cases.md` o `use_cases_to_openapi.md`.

## Reglas de remediacion automatica

Se puede corregir automaticamente solo cuando exista evidencia documental suficiente y la relacion sea inequívoca.

Se puede corregir:

- reciprocidad faltante entre Epica, FRS y US
- referencias OpenAPI existentes en US y `RTM.yaml`
- listas incompletas de artefactos derivados
- inconsistencias menores de naming trazable

No se puede corregir automaticamente:

- decisiones de alcance funcional
- requisitos no respaldados por documento fuente
- OpenAPI no respaldada por evidencia funcional
- riesgos nuevos no documentados

## Estructuras no permitidas

- `use-cases/`
- `traceability/epics_to_use_cases.md`
- `traceability/use_cases_to_openapi.md`
- matrices manuales duplicadas de `Epica -> FRS`, `FRS -> US` o `US -> OpenAPI`

## Criterio de conformidad

El flujo queda conforme solo si:

- las relaciones principales existen y son reciprocas cuando aplica
- no hay duplicacion de trazabilidad
- `RTM.yaml` refleja las relaciones estructuradas relevantes
- las historias con impacto API trazan su OpenAPI
- la cobertura `AC -> GT -> COV` es consistente
