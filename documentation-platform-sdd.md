# Documentation Platform SDD

## 1. Proposito

Este documento define el flujo oficial de documentacion funcional de la plataforma, el modelo de trazabilidad entre artefactos y las reglas de validacion necesarias para que un agente de validacion pueda comprobar completitud, coherencia y cobertura.

El alcance cubre los artefactos documentales base de analisis y descomposicion funcional:

- `epic.template.md`
- `functional-requirement.template.md`
- `user-story.template.md`
- trazabilidad estructurada en `traceability/RTM.yaml`

No define trazabilidad de codigo fuente ni pipelines CI/CD, aunque deja preparada la continuidad hacia esos artefactos.

---

## 2. Flujo oficial de documentacion

El flujo normativo de trabajo es el siguiente:

1. Se crea o modifica una **Epica**.
2. De una **Epica** se derivan una o varias **FRS**.
3. De una **FRS** se derivan una o varias **US**.
4. Cuando la **US** implique interaccion API, el agente analista genera o actualiza una o varias especificaciones en `spec/open-api/`.
5. Cada **US** define uno o mas **criterios de aceptacion** (`AC-*`).
6. Cada **US** define uno o mas **escenarios Gherkin** (`GT-*`) que validan los criterios de aceptacion.
7. Los **riesgos** identificados en FRS y US deben quedar cubiertos por pruebas cuando su impacto lo requiera.
8. La trazabilidad estructurada se refleja en `traceability/RTM.yaml` mediante `LINK-NNN`.
9. Cuando sea necesario trazar una épica de forma agregada en `RTM.yaml`, el enlace puede incluir el campo opcional `epica` además de los campos de requisito e historia.

Cadena objetivo de trazabilidad:

```text
Epica -> FRS -> US -> OpenAPI -> AC -> GT -> Evidencia
                 \-> Riesgo -> Control -> GT/Evidencia
```

---

## 3. Artefactos y responsabilidad

### 3.1 Epica

La epica representa una necesidad o iniciativa de negocio de alto nivel.

Debe responder a:

- por que existe,
- que valor aporta,
- que FRS se derivan,
- que US se esperan,
- que riesgos agregados existen.

La epica no baja a detalle de validacion Gherkin individual; solo mantiene trazabilidad agregada.

### 3.2 Functional Requirement Specification (FRS)

La FRS traduce una epica en comportamiento funcional verificable.

Debe responder a:

- que debe hacer el sistema,
- que alcance tiene,
- que entradas, salidas, restricciones y reglas aplican,
- que criterios de aceptacion definen el requisito,
- que US se derivan,
- que riesgos y controles deben quedar cubiertos,
- que tests de alto nivel validan ese requisito.

La FRS es el puente entre necesidad funcional y descomposicion a historias.

### 3.3 User Story (US)

La US aterriza una FRS en comportamiento implementable y verificable.

Debe responder a:

- que necesita el usuario,
- que especificacion API se genera o modifica cuando aplica,
- como se verifica funcionalmente,
- que criterios de aceptacion deben cumplirse,
- que escenarios Gherkin los validan,
- que riesgos quedan cubiertos,
- que evidencia demuestra la cobertura.

La US es el artefacto principal de trazabilidad fina entre analisis y validacion ejecutable.

---

## 4. Estructura de trazabilidad por artefacto

### 4.1 Trazabilidad minima en Epica

La epica debe trazar como minimo a:

- objetivo de negocio,
- modulo y submodulo funcional,
- lista de FRS derivadas,
- lista de US derivadas,
- riesgos relacionados,
- tests derivados agregados,
- enlace RTM.

### 4.2 Trazabilidad minima en FRS

La FRS debe trazar como minimo a:

- requisito de negocio de origen,
- epica contenedora,
- historias de usuario derivadas,
- riesgos relacionados,
- controles relacionados,
- tests de alto nivel (`TC-*`),
- cobertura funcional derivada hacia US,
- enlace RTM.

### 4.3 Trazabilidad minima en User Story

La US debe trazar como minimo a:

- epica asociada,
- FRS principal,
- FRS relacionados si aplica,
- historias relacionadas si aplica,
- especificaciones OpenAPI derivadas si aplica,
- criterios de aceptacion (`AC-*`),
- tests Gherkin (`GT-*`),
- cobertura funcional y de riesgo (`COV-*`),
- riesgos relacionados,
- ADR relacionado si aplica,
- enlace RTM.

---

## 5. Matriz maestra de trazabilidad

| Origen | Destino | Cardinalidad | Medio de trazado | Campo / seccion esperada | Obligatorio | Regla de validacion |
|--------|---------|--------------|------------------|--------------------------|-------------|---------------------|
| Epica | FRS | 1..n | referencia directa | `epic.template.md` -> `Requisitos funcionales` | si | toda epica debe listar al menos una FRS o marcar refinamiento pendiente |
| Epica | US | 1..n | referencia directa | `epic.template.md` -> `Historias de usuario` | si | toda epica debe listar una o mas US candidatas o justificar ausencia |
| Epica | Riesgos | 0..n | referencia directa | `epic.template.md` -> `Riesgos relacionados` | si | si existen riesgos deben estar identificados en `RISK-LIST` |
| Epica | RTM | 1 | identificador | `LINK-NNN` | si | toda epica debe tener enlace RTM |
| FRS | Epica | 1 | referencia directa | `functional-requirement.template.md` -> `Epica` | si | toda FRS debe pertenecer a una unica epica |
| FRS | US | 1..n | lista derivada | `Historias de usuario derivadas` | si | toda FRS debe listar una o mas US o marcar pendiente |
| FRS | AC | 1..n | seccion interna | `§17 Criterios de aceptacion` | si | toda FRS debe contener al menos un AC |
| FRS | TC | 1..n | tabla interna | `§18 Tests de alto nivel` | si | todo AC de FRS debe estar cubierto por al menos un TC |
| FRS | Riesgos | 0..n | tabla interna | `§19 Riesgos y controles asociados` | si | todo riesgo alto debe aparecer en tests de alto nivel |
| FRS | Controles | 0..n | tabla interna | `§19 Riesgos y controles asociados` | si | todo riesgo debe tener control o justificarse |
| FRS | RTM | 1 | identificador | `LINK-NNN` | si | toda FRS debe tener enlace RTM |
| US | Epica | 1 | referencia directa | `user-story.template.md` -> `Epica asociada` | si | toda US debe pertenecer a una unica epica |
| US | FRS principal | 1 | referencia directa | `FRS asociado principal` | si | toda US debe derivar de una FRS principal |
| US | FRS relacionados | 0..n | lista | `FRS relacionados` | no | si existen, deben ser IDs validos |
| US | Historias relacionadas | 0..n | lista | `Historias relacionadas` | no | si existen, deben usar lista `US-RELATED-LIST` |
| US | OpenAPI | 0..n | tabla interna | `§17 Especificacion OpenAPI derivada` | si | toda US con impacto API debe referenciar al menos un fichero en `spec/open-api/` |
| US | AC | 1..n | seccion interna | `§11 Criterios de aceptacion` | si | toda US debe tener al menos un AC |
| US | GT | 1..n | tabla interna | `§13 Trazabilidad de tests Gherkin` | si | todo GT debe mapear exactamente a un AC |
| US | Riesgos | 0..n | tabla interna | `§18 Riesgos y controles` | si | todo riesgo alto debe quedar cubierto en `§14` |
| US | Cobertura funcional | 1..n | tabla interna | `§14 Trazabilidad de cobertura funcional y riesgo` | si | todo AC debe aparecer al menos una vez |
| US | Cobertura de riesgo | 0..n | tabla interna | `§14 Trazabilidad de cobertura funcional y riesgo` | si | todo riesgo alto debe tener al menos una fila tipo `riesgo` |
| US | Evidencia | 0..n | referencia directa | columna `Evidencia` en `§14` | si | toda cobertura `cubierta` debe tener evidencia asociada |
| US | RTM | 1 | identificador | `LINK-NNN` | si | toda US debe tener enlace RTM |

Nota normativa para `RTM.yaml`:

- el campo `epica` es opcional y se usa cuando se necesita representar una trazabilidad agregada de nivel épica,
- los campos `requisito` e `historia` siguen siendo los campos estructurados principales para FRS y US,
- un mismo `LINK-NNN` no debe mezclar varias relaciones ambiguas en una sola entrada.

---

## 6. Modelo detallado de trazabilidad funcional

### 6.1 De Epica a FRS

Una epica descompone una necesidad de negocio en FRS concretas.

Reglas:

- una FRS no puede existir sin una epica contenedora,
- la lista `FRS-LIST` en la epica debe contener todas las FRS derivadas aprobadas o en refinamiento,
- la FRS debe reflejar de vuelta la epica de origen.

### 6.2 De FRS a User Story

La FRS aterriza en una o varias historias.

Reglas:

- toda US debe aparecer en la lista de `Historias de usuario derivadas` de su FRS origen,
- toda US debe referenciar su `FRS asociado principal`,
- si una FRS esta aprobada y no tiene US derivadas, debe marcarse como excepcion justificada.

### 6.3 De User Story a criterios de aceptacion

Los criterios de aceptacion son la unidad minima de validacion funcional.

Reglas:

- toda US debe definir al menos un `AC-*`,
- los `AC-*` deben ser verificables y redactados en formato `Dado / Cuando / Entonces`,
- no puede existir un Gherkin sin un AC asociado.

### 6.4 De User Story a OpenAPI

Cuando una US afecte interfaces API, debe generar o actualizar especificaciones en `spec/open-api/`.

Reglas:

- toda US con comportamiento API debe declarar al menos una especificacion OpenAPI derivada,
- toda especificacion declarada debe vivir en `spec/open-api/`,
- toda especificacion OpenAPI derivada debe poder trazarse con uno o mas `AC-*`,
- toda especificacion OpenAPI derivada debe poder verificarse con uno o mas `GT-*` cuando la historia tenga comportamiento API observable.

### 6.5 De criterios de aceptacion a Gherkin

Los escenarios Gherkin son la validacion ejecutable o prevista de la US.

Reglas:

- todo `AC-*` debe estar cubierto por al menos un `GT-*`,
- todo `GT-*` debe trazar exactamente a un `AC-*`,
- la tabla `§13 Trazabilidad de tests Gherkin` es la fuente de verdad para esta relacion.

### 6.6 De riesgos a cobertura verificable

Los riesgos deben ser demostrablemente cubiertos cuando su impacto lo requiera.

Reglas:

- en FRS, todo riesgo funcional relevante debe quedar trazado en `Tests de alto nivel`,
- en US, todo riesgo de impacto `alto` debe quedar trazado en `§14 Trazabilidad de cobertura funcional y riesgo`,
- toda fila de cobertura de tipo `riesgo` debe identificar:
  - el `AC` que ayuda a mitigarlo,
  - el `GT` que lo valida,
  - el control validado,
  - la evidencia esperada o disponible.

### 6.7 De cobertura a evidencia

La cobertura declarada debe poder demostrarse.

Reglas:

- toda fila `COV-*` con estado `cubierta` debe tener evidencia,
- la evidencia puede ser enlace a ejecucion, reporte, registro o evidencia documental,
- si el estado es `pendiente`, la evidencia puede quedar vacia temporalmente.

---

## 7. Reglas normativas para un agente de validacion

Un agente de validacion debe comprobar, como minimo, las siguientes reglas.

### 7.1 Reglas de integridad estructural

1. Toda epica tiene `EPIC-ID`, `LINK-NNN` y al menos una referencia a FRS o indicacion de pendiente.
2. Toda FRS tiene `FRS-ID`, `EPIC-ID`, `LINK-NNN` y al menos una US derivada o indicacion de pendiente.
3. Toda US tiene `US-ID`, `EPIC-ID`, `FRS-ID`, `LINK-NNN` y al menos un AC.
4. Toda US con impacto API tiene al menos una referencia OpenAPI en `spec/open-api/`.

### 7.2 Reglas de coherencia jerarquica

5. Si una US referencia una FRS, la FRS debe listar esa US en `Historias de usuario derivadas`.
6. Si una FRS referencia una epica, la epica debe listar esa FRS en `FRS-LIST`.
7. Si una epica lista una US derivada, esa US debe pertenecer a la misma epica.
8. Si una US declara OpenAPI derivada, la ruta debe estar bajo `spec/open-api/`.

### 7.3 Reglas de cobertura funcional

9. Todo `AC-*` en FRS debe estar cubierto por al menos un `TC-*`.
10. Todo `AC-*` en US debe estar cubierto por al menos un `GT-*`.
11. Todo `GT-*` debe mapear exactamente a un `AC-*` existente.
12. Toda fila `COV-*` debe referenciar un `AC-*` y, salvo `no-aplica`, un `GT-*` valido.
13. Toda OpenAPI derivada declarada en una US debe quedar asociada a uno o mas `AC-*` y ser verificable por uno o mas `GT-*` cuando la historia tenga comportamiento API observable.

### 7.4 Reglas de cobertura de riesgos

14. Todo riesgo de impacto `alto` en FRS debe aparecer en `§18 Tests de alto nivel`.
15. Todo riesgo de impacto `alto` en US debe aparecer en `§14 Trazabilidad de cobertura funcional y riesgo`.
16. Toda fila de cobertura de tipo `riesgo` debe referenciar un riesgo existente en la US.
17. Ningun riesgo marcado como cubierto puede carecer de `Control validado`.

### 7.5 Reglas de evidencia

18. Toda cobertura con estado `cubierta` debe incluir `Evidencia`.
19. Toda cobertura con estado `parcial` debe incluir nota o evidencia parcial.
20. Ningun `GT-*` marcado como ejecutado puede quedar sin estado de prueba.

### 7.6 Reglas de consistencia semantica

21. No debe existir referencia a `Caso de uso` en FRS dentro del modelo actual, porque el flujo oficial es `Epica -> FRS -> US`.
22. La relacion entre epica y tests debe tratarse como agregada, no como trazabilidad fina obligatoria.
23. Las historias relacionadas en US deben aceptarse como lista, no como valor singular.
24. La OpenAPI derivada desde US debe tratarse como artefacto de diseño funcional derivado del analisis, no como implementacion tecnica final.

---

## 8. Matriz de validacion automatizable

| Regla ID | Nivel | Validacion | Resultado esperado |
|----------|------|------------|--------------------|
| VAL-001 | Epica | existe `EPIC-ID` | pass/fail |
| VAL-002 | Epica | existe `LINK-NNN` | pass/fail |
| VAL-003 | Epica | existe al menos una FRS derivada o pendiente justificada | pass/fail |
| VAL-004 | FRS | existe `FRS-ID` | pass/fail |
| VAL-005 | FRS | existe `EPIC-ID` | pass/fail |
| VAL-006 | FRS | existe `LINK-NNN` | pass/fail |
| VAL-007 | FRS | existe al menos una US derivada o pendiente justificada | pass/fail |
| VAL-008 | FRS | todo `AC-*` aparece en `TC-*` | pass/fail |
| VAL-009 | FRS | todo riesgo alto aparece en `TC-*` | pass/fail |
| VAL-010 | US | existe `US-ID` | pass/fail |
| VAL-011 | US | existe `EPIC-ID` | pass/fail |
| VAL-012 | US | existe `FRS-ID` | pass/fail |
| VAL-013 | US | existe `LINK-NNN` | pass/fail |
| VAL-014 | US | si la historia tiene impacto API, existe referencia OpenAPI en `spec/open-api/` | pass/fail |
| VAL-015 | US | existe al menos un `AC-*` | pass/fail |
| VAL-016 | US | todo `AC-*` aparece en `GT-*` | pass/fail |
| VAL-017 | US | todo `GT-*` referencia exactamente un `AC-*` | pass/fail |
| VAL-018 | US | toda OpenAPI derivada queda trazada a `AC-*` y `GT-*` cuando aplica | pass/fail |
| VAL-019 | US | todo riesgo alto aparece en `COV-*` tipo `riesgo` | pass/fail |
| VAL-020 | US | toda fila `COV-*` con estado `cubierta` tiene evidencia | pass/fail |
| VAL-021 | Cross | FRS y US son reciprocas en su relacion | pass/fail |
| VAL-022 | Cross | Epica y FRS son reciprocas en su relacion | pass/fail |

---

## 9. Fuente de verdad por nivel

| Relacion | Fuente de verdad primaria |
|----------|---------------------------|
| Epica -> FRS | `epic.template.md` |
| FRS -> Epica | `functional-requirement.template.md` |
| FRS -> US | `functional-requirement.template.md` |
| US -> FRS | `user-story.template.md` |
| US -> OpenAPI | `user-story.template.md` `§17` |
| US -> AC | `user-story.template.md` |
| AC -> GT | `user-story.template.md` `§13` |
| OpenAPI -> AC/GT | `user-story.template.md` `§17`, `§13`, `§14` |
| Riesgo US -> Cobertura | `user-story.template.md` `§14` |
| Riesgo FRS -> TC | `functional-requirement.template.md` `§18` |
| Trazabilidad estructurada global | `traceability/RTM.yaml` |

Cuando exista conflicto entre documentos narrativos y trazabilidad estructurada, el agente de validacion debe reportar inconsistencia y no asumir correccion automatica.

---

## 10. Criterio de exito del proceso documental

El proceso queda correctamente aplicado solo si:

- toda epica deriva en una o varias FRS trazables,
- toda FRS deriva en una o varias US trazables,
- toda US con impacto API genera o actualiza una especificacion en `spec/open-api/`,
- toda US define AC verificables,
- todo AC esta cubierto por Gherkin,
- toda OpenAPI derivada queda trazada a la US, a sus AC y a sus GT cuando aplica,
- todo riesgo de impacto alto tiene cobertura verificable,
- toda cobertura declarada como completa tiene evidencia,
- la trazabilidad cruzada entre documentos es reciproca y consistente,
- `traceability/RTM.yaml` puede representar los enlaces estructurados del flujo.

---

## 11. Recomendacion de uso por agentes

Un agente de validacion debe recorrer el proceso en este orden:

1. Validar integridad de IDs y metadatos.
2. Validar relaciones `Epica -> FRS -> US`.
3. Validar derivacion `US -> OpenAPI` cuando exista impacto API.
4. Validar cobertura `AC -> TC` en FRS.
5. Validar cobertura `AC -> GT` en US.
6. Validar cobertura `Riesgo -> Test/Cobertura`.
7. Validar evidencia de coberturas marcadas como completas.
8. Validar coherencia con `traceability/RTM.yaml`.

Si cualquiera de estas etapas falla, el agente debe reportar:

- artefacto afectado,
- identificador exacto,
- relacion faltante o inconsistente,
- gravedad (`alta`, `media`, `baja`),
- accion correctiva recomendada.
