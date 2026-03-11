# {{US-ID}} — {{US-TITLE}}

---

## Metadatos

| Campo                        | Valor                                      |
|-----------------------------|--------------------------------------------|
| **ID**                      | {{US-ID}}                                  |
| **Versión**                 | {{VERSION}}                                |
| **Estado**                  | {{STATUS}}                                 |
| **Estabilidad**             | {{STABILITY}}                              |
| **Fecha**                   | {{DATE}}                                   |
| **Autor**                   | {{AUTHOR}}                                 |
| **Revisado por**            | {{REVIEWER}}                               |
| **Aprobado por**            | {{APPROVER}}                               |
| **Módulo Funcional**        | {{FUNCTIONAL_MODULE}}                      |
| **Submódulo Funcional**     | {{FUNCTIONAL_SUBMODULE}}                   |
| **Épica asociada**          | {{EPIC-ID}} — {{EPIC-TITLE}}               |
| **FRS asociado principal**  | {{FRS-ID}} — {{FRS-TITLE}}                 |
| **Prioridad**               | {{PRIORITY}}                               |
| **Tipo de historia**        | {{US_TYPE}}                                |
| **Porcentaje de completud** | {{COMPLETION_PERCENTAGE}}                  |
| **Fuente**                  | {{SOURCE}}                                 |
| **Sesión refinamiento**     | {{REF-ID}}                                 |
| **Enlace RTM**              | {{LINK-NNN}}                               |
| **Método verificación**     | {{VERIFICATION_METHOD}}                    |

> **Estados válidos:** `borrador` | `en-refinamiento` | `lista` | `en-desarrollo` | `en-validación` | `cerrada` | `rechazada` | `obsoleta`
>
> **Estabilidad válida:** `estable` | `volátil` | `en-cambio`
>
> **Prioridades válidas:** `crítica` | `alta` | `media` | `baja`
>
> **Tipos de historia sugeridos:** `funcional` | `validación` | `error` | `integración` | `seguridad` | `observabilidad`
>
> **Métodos de verificación:** `test` | `inspección` | `demostración` | `análisis`
>
> **Porcentaje de completud:** valor entre `0%` y `100%`

---

## Historial de versiones

| Versión | Fecha      | Autor      | Cambios |
|---------|------------|------------|---------|
| 1.0.0   | {{DATE}}   | {{AUTHOR}} | Versión inicial |

---

## 1. Historia de usuario

> Redactada en formato clásico y entendible por negocio.

**Como** {{ROLE}}  
**Quiero** {{NEED}}  
**Para** {{BUSINESS_VALUE}}

---

## 2. Objetivo funcional

> Explica de forma breve qué comportamiento concreto aporta esta historia dentro del FRS.

{{US_OBJECTIVE}}

---

## 3. Contexto

> Situación o necesidad en la que se enmarca la historia.

{{US_CONTEXT}}

---

## 4. Alcance

### 4.1 Incluido

- {{IN_SCOPE_1}}
- {{IN_SCOPE_2}}

### 4.2 Fuera de alcance

- {{OUT_OF_SCOPE_1}}
- {{OUT_OF_SCOPE_2}}

### 4.3 Límites

- {{BOUNDARY_1}}

---

## 5. Actor principal y actores relacionados

### 5.1 Actor principal

| Actor | Descripción |
|-------|-------------|
| {{PRIMARY_ACTOR}} | {{PRIMARY_ACTOR_DESC}} |

### 5.2 Actores relacionados

| Actor | Relación con la historia |
|-------|---------------------------|
| {{RELATED_ACTOR_1}} | {{RELATED_ACTOR_DESC_1}} |
| {{RELATED_ACTOR_2}} | {{RELATED_ACTOR_DESC_2}} |

---

## 6. Disparador

> Evento que inicia la historia.

- {{TRIGGER_EVENT}}

---

## 7. Precondiciones

- {{PRECONDITION_1}}
- {{PRECONDITION_2}}

---

## 8. Postcondiciones

### 8.1 Éxito

- {{SUCCESS_POSTCONDITION_1}}
- {{SUCCESS_POSTCONDITION_2}}

### 8.2 Fallo

- {{FAIL_POSTCONDITION_1}}

---

## 9. Reglas de negocio asociadas

| ID | Regla | Fuente / referencia |
|----|-------|---------------------|
| BR-001 | {{RULE_1}} | {{RULE_SOURCE_1}} |
| BR-002 | {{RULE_2}} | {{RULE_SOURCE_2}} |

---

## 10. Datos de entrada y salida

### 10.1 Entradas

| # | Entrada | Origen | Obligatoria | Validaciones |
|---|---------|--------|-------------|--------------|
| 1 | {{INPUT_1}} | {{INPUT_SOURCE_1}} | Sí / No | {{INPUT_VALIDATION_1}} |

### 10.2 Salidas

| # | Salida | Destino | Descripción |
|---|--------|---------|-------------|
| 1 | {{OUTPUT_1}} | {{OUTPUT_DEST_1}} | {{OUTPUT_DESC_1}} |

---

## 11. Criterios de aceptación

> Deben ser verificables y cubrir al menos flujo principal, validación relevante y error relevante cuando aplique.

### AC-001 — {{AC_TITLE_1}}

- **Dado** que {{GIVEN_1}}
- **Cuando** {{WHEN_1}}
- **Entonces** {{THEN_1}}

### AC-002 — {{AC_TITLE_2}}

- **Dado** que {{GIVEN_2}}
- **Cuando** {{WHEN_2}}
- **Entonces** {{THEN_2}}

### AC-003 — {{AC_TITLE_3}}

- **Dado** que {{GIVEN_3}}
- **Cuando** {{WHEN_3}}
- **Entonces** {{THEN_3}}

---

## 12. Escenarios Gherkin asociados

> Escenarios ejecutables o previstos para validar la historia.  
> Cada escenario debe trazar al menos un criterio de aceptación.

### Feature: {{FEATURE_NAME}}

```gherkin
Feature: {{FEATURE_NAME}}
  As a {{ROLE}}
  I want {{NEED}}
  So that {{BUSINESS_VALUE}}

  Scenario: {{SCENARIO_1_TITLE}}
    Given {{GIVEN_1}}
    When {{WHEN_1}}
    Then {{THEN_1}}

  Scenario: {{SCENARIO_2_TITLE}}
    Given {{GIVEN_2}}
    When {{WHEN_2}}
    Then {{THEN_2}}

  Scenario: {{SCENARIO_3_TITLE}}
    Given {{GIVEN_3}}
    When {{WHEN_3}}
    Then {{THEN_3}}
```

## 13. Trazabilidad de tests Gherkin

> Relación explícita entre historia, criterios de aceptación y escenarios Gherkin.

| Test ID | Feature | Escenario | Tipo | AC cubierto | Estado | Observaciones |
|---------|---------|-----------|------|-------------|--------|---------------|
| GT-001  | {{FEATURE_NAME}} | {{SCENARIO_1_TITLE}} | funcional | AC-001 | {{TEST_STATUS_1}} | {{TEST_NOTE_1}} |
| GT-002  | {{FEATURE_NAME}} | {{SCENARIO_2_TITLE}} | negativo | AC-002 | {{TEST_STATUS_2}} | {{TEST_NOTE_2}} |
| GT-003  | {{FEATURE_NAME}} | {{SCENARIO_3_TITLE}} | borde / error | AC-003 | {{TEST_STATUS_3}} | {{TEST_NOTE_3}} |

> **Estados sugeridos de test:** `pendiente` | `implementado` | `ejecutado-pass` | `ejecutado-fail` | `bloqueado`

> **Regla obligatoria:** todo `AC-*` definido en la historia debe estar cubierto por al menos un `GT-*`, y todo `GT-*` debe trazar exactamente a un `AC-*`.

---

## 14. Trazabilidad de cobertura funcional y riesgo

> Esta sección conecta explícitamente criterios de aceptación, riesgos y escenarios Gherkin.
> Debe permitir demostrar qué comportamiento funcional y qué mitigaciones quedan realmente cubiertos.

| Cobertura ID | Tipo | Referencia origen | AC relacionado | Test Gherkin | Riesgo relacionado | Control validado | Estado cobertura | Evidencia |
|--------------|------|-------------------|----------------|--------------|--------------------|------------------|------------------|-----------|
| COV-001 | funcional | {{FRS-ID}} | AC-001 | GT-001 | — | {{CONTROL_VALIDATED_1}} | {{COVERAGE_STATUS_1}} | {{COVERAGE_EVIDENCE_1}} |
| COV-002 | riesgo | {{FRS-ID}} | AC-002 | GT-002 | USRSK-001 | {{CONTROL_VALIDATED_2}} | {{COVERAGE_STATUS_2}} | {{COVERAGE_EVIDENCE_2}} |
| COV-003 | riesgo | {{FRS-ID}} | AC-003 | GT-003 | USRSK-002 | {{CONTROL_VALIDATED_3}} | {{COVERAGE_STATUS_3}} | {{COVERAGE_EVIDENCE_3}} |

> **Tipos válidos:** `funcional` | `riesgo` | `cumplimiento` | `seguridad`
>
> **Estados sugeridos:** `cubierta` | `parcial` | `pendiente` | `no-aplica`
>
> **Reglas obligatorias:**
> - todo `AC-*` debe aparecer al menos una vez en esta tabla,
> - todo riesgo de impacto `alto` debe estar cubierto por al menos una fila de tipo `riesgo`,
> - toda fila con `Test Gherkin` debe referenciar un `GT-*` definido en la sección 13.

---

## 15. Requisitos no funcionales asociados

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| {{NFR-ID-1}} | {{NFR_TYPE_1}} | {{NFR_DESC_1}} | {{NFR_METRIC_1}} |

---

## 16. Dependencias

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Épica | {{EPIC-ID}} | `pertenece-a` | Épica funcional contenedora |
| FRS | {{FRS-ID}} | `deriva-de` | Requisito funcional principal |
| Historias | {{US-RELATED-LIST}} | `relacionada-con` | Historias complementarias o dependientes |
| Servicio ext. | {{DEP_SYS_1}} | `consume` | Dependencia externa si aplica |

---

## 17. Especificacion OpenAPI derivada

> Cuando la historia implique interaccion API, el agente analista debe generar o actualizar la especificacion correspondiente en `spec/open-api/{modulo}/{submodulo}/`.
> Esta seccion deja trazabilidad explicita entre la historia y las definiciones API derivadas.

| Artefacto API | Ruta / ID | Tipo | Operacion / evento | Estado | Observaciones |
|---------------|-----------|------|--------------------|--------|---------------|
| OpenAPI spec | {{OPENAPI_FILE_1}} | `openapi` | {{OPENAPI_OPERATION_1}} | {{OPENAPI_STATUS_1}} | {{OPENAPI_NOTE_1}} |
| OpenAPI spec | {{OPENAPI_FILE_2}} | `openapi` | {{OPENAPI_OPERATION_2}} | {{OPENAPI_STATUS_2}} | {{OPENAPI_NOTE_2}} |

> **Reglas obligatorias:**
> - si la US expone, consulta o modifica comportamiento API, debe existir al menos una entrada en esta tabla,
> - toda ruta referenciada debe vivir en `spec/open-api/{modulo}/{submodulo}/`,
> - toda especificacion OpenAPI derivada debe poder trazarse con al menos un `AC-*` y un `GT-*`.

---

## 18. Observabilidad funcional

### 16.1 Eventos funcionales

| Evento | Cuándo ocurre | Datos mínimos |
|--------|----------------|---------------|
| {{OBS_EVENT_1}} | {{OBS_WHEN_1}} | {{OBS_DATA_1}} |
| {{OBS_EVENT_2}} | {{OBS_WHEN_2}} | {{OBS_DATA_2}} |

### 16.2 Alertas

| Alerta | Condición | Acción esperada |
|--------|-----------|-----------------|
| {{ALERT_1}} | {{ALERT_CONDITION_1}} | {{ALERT_ACTION_1}} |

### 16.3 KPIs

| KPI | Definición | Objetivo |
|-----|------------|----------|
| {{KPI_1}} | {{KPI_DEF_1}} | {{KPI_TARGET_1}} |

---

## 19. Riesgos y controles

| Riesgo ID | Descripción | Probabilidad | Impacto | Control / mitigación |
|-----------|-------------|--------------|---------|----------------------|
| USRSK-001 | {{RISK_1}} | baja/media/alta | baja/media/alta | {{CONTROL_1}} |

> **Regla obligatoria:** todo riesgo con impacto `alto` debe quedar trazado en la sección `14. Trazabilidad de cobertura funcional y riesgo`.

---

## 20. Trazabilidad

> Esta sección es obligatoria y debe estar completa antes de dar la historia por lista o cerrada.

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Objetivo de negocio | {{BUSINESS_GOAL_ID}} | {{BUSINESS_GOAL}} |
| Módulo funcional | {{FUNCTIONAL_MODULE}} | {{FUNCTIONAL_MODULE_DESC}} |
| Submódulo funcional | {{FUNCTIONAL_SUBMODULE}} | {{FUNCTIONAL_SUBMODULE_DESC}} |
| Épica asociada | {{EPIC-ID}} | {{EPIC-TITLE}} |
| FRS principal | {{FRS-ID}} | {{FRS-TITLE}} |
| FRS relacionados | {{FRS-RELATED-LIST}} | Requisitos relacionados si aplica |
| Historias relacionadas | {{US-RELATED-LIST}} | Otras historias relacionadas |
| Especificaciones OpenAPI derivadas | {{OPENAPI-LIST}} | Ficheros o definiciones OpenAPI en `spec/open-api/{modulo}/{submodulo}/` |
| Criterios de aceptación | AC-001, AC-002, AC-003 | Criterios definidos en §11 |
| Tests Gherkin | GT-001, GT-002, GT-003 | Escenarios definidos en §13 |
| Cobertura funcional y riesgo | COV-001, COV-002, COV-003 | Cobertura definida en §14 |
| Riesgos relacionados | {{RISK-LIST}} | Riesgos asociados |
| ADR relacionado | {{ADR-ID}} | {{ADR-TITLE}} |
| Enlace RTM | {{LINK-NNN}} | Entrada en `traceability/RTM.yaml` |

---

## 21. Notas y decisiones abiertas

| # | Nota / pregunta | Responsable | Estado | Fecha objetivo | Decisión tomada | Evidencia |
|---|------------------|-------------|--------|----------------|-----------------|----------|
| 1 | {{NOTE_1}} | {{OWNER_1}} | abierta | {{TARGET_DATE_1}} | {{DECISION_1}} | {{EVIDENCE_REF_1}} |

> **Estados sugeridos:** `abierta` | `en-análisis` | `resuelta` | `descartada`

---

*Plantilla: `user-story.template.md` v1.2.0*
