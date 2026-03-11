# {{EPIC-ID}} — {{EPIC-TITLE}}

---

## Metadatos

| Campo                        | Valor                                      |
|-----------------------------|--------------------------------------------|
| **ID**                      | {{EPIC-ID}}                                |
| **Versión**                 | {{VERSION}}                                |
| **Estado**                  | {{STATUS}}                                 |
| **Estabilidad**             | {{STABILITY}}                              |
| **Fecha**                   | {{DATE}}                                   |
| **Autor**                   | {{AUTHOR}}                                 |
| **Revisado por**            | {{REVIEWER}}                               |
| **Aprobado por**            | {{APPROVER}}                               |
| **Módulo Funcional**        | {{FUNCTIONAL_MODULE}}                      |
| **Submódulo Funcional**     | {{FUNCTIONAL_SUBMODULE}}                   |
| **Prioridad**               | {{PRIORITY}}                               |
| **Porcentaje de completud** | {{COMPLETION_PERCENTAGE}}                  |
| **Fuente**                  | {{SOURCE}}                                 |
| **Sesión refinamiento**     | {{REF-ID}}                                 |
| **Enlace RTM**              | {{LINK-NNN}}                               |
| **Objetivo de negocio**     | {{BUSINESS_GOAL_ID}} — {{BUSINESS_GOAL}}   |

> **Estados válidos:** `borrador` | `en-revisión` | `aprobado` | `rechazado` | `obsoleto`
>
> **Estabilidad válida:** `estable` | `volátil` | `en-cambio`
>
> **Prioridades válidas:** `crítica` | `alta` | `media` | `baja`
>
> **Porcentaje de completud:** valor entre `0%` y `100%`

---

## Historial de versiones

| Versión | Fecha      | Autor      | Cambios |
|---------|------------|------------|---------|
| 1.0.0   | {{DATE}}   | {{AUTHOR}} | Versión inicial |
| 1.1.0   | {{DATE}}   | {{AUTHOR}} | Simplificación de la plantilla: eliminación de casos de uso y alineación a trabajo basado en historias de usuario |

---

## 1. Propósito de la épica

> Explica qué problema de negocio aborda esta épica y por qué existe.

{{EPIC_PURPOSE}}

---

## 2. Contexto de negocio

> Situación actual, necesidad detectada y motivación.

{{BUSINESS_CONTEXT}}

---

## 3. Objetivo de negocio

> Resultado esperado desde la perspectiva del negocio.

{{BUSINESS_OBJECTIVE}}

---

## 4. Alcance

### 4.1 Incluido en esta épica

- {{IN_SCOPE_1}}
- {{IN_SCOPE_2}}
- {{IN_SCOPE_3}}

### 4.2 Fuera de alcance

- {{OUT_OF_SCOPE_1}}
- {{OUT_OF_SCOPE_2}}

### 4.3 Límites

- {{BOUNDARY_1}}
- {{BOUNDARY_2}}

---

## 5. Problema que resuelve

> Describe el dolor actual, la ineficiencia, riesgo o limitación que esta épica pretende resolver.

{{PROBLEM_STATEMENT}}

---

## 6. Valor esperado

> Beneficio esperado para negocio, operación, cliente o cumplimiento.

| Tipo de valor     | Descripción |
|-------------------|-------------|
| Negocio           | {{BUSINESS_VALUE}} |
| Operativo         | {{OPERATIONAL_VALUE}} |
| Cliente / usuario | {{USER_VALUE}} |
| Cumplimiento      | {{COMPLIANCE_VALUE}} |

---

## 7. Stakeholders

| Stakeholder | Interés / expectativa | Impacto |
|-------------|------------------------|---------|
| {{STAKEHOLDER_1}} | {{STAKEHOLDER_INTEREST_1}} | {{STAKEHOLDER_IMPACT_1}} |
| {{STAKEHOLDER_2}} | {{STAKEHOLDER_INTEREST_2}} | {{STAKEHOLDER_IMPACT_2}} |

---

## 8. Capacidades funcionales esperadas

> Grandes capacidades que la épica debe habilitar. No entrar aún al detalle técnico ni al detalle de implementación.

| ID | Capacidad | Descripción |
|----|-----------|-------------|
| CAP-001 | {{CAPABILITY_1}} | {{CAPABILITY_DESC_1}} |
| CAP-002 | {{CAPABILITY_2}} | {{CAPABILITY_DESC_2}} |
| CAP-003 | {{CAPABILITY_3}} | {{CAPABILITY_DESC_3}} |

---

## 9. Criterios de éxito de la épica

> Cómo sabremos que la épica ha cumplido su objetivo.

| ID | Criterio de éxito | Métrica / evidencia |
|----|-------------------|---------------------|
| ESC-001 | {{SUCCESS_CRITERIA_1}} | {{SUCCESS_METRIC_1}} |
| ESC-002 | {{SUCCESS_CRITERIA_2}} | {{SUCCESS_METRIC_2}} |

---

## 10. Indicadores / KPIs asociados

| KPI | Definición | Objetivo |
|-----|------------|----------|
| {{KPI_1}} | {{KPI_DEF_1}} | {{KPI_TARGET_1}} |
| {{KPI_2}} | {{KPI_DEF_2}} | {{KPI_TARGET_2}} |

---

## 11. Dependencias de alto nivel

| Tipo | Dependencia | Relación | Descripción |
|------|-------------|----------|-------------|
| `proceso` | {{DEP_PROCESS_1}} | `depende-de` | {{DEP_DESC_1}} |
| `sistema` | {{DEP_SYSTEM_1}} | `depende-de` | {{DEP_DESC_2}} |
| `organización` | {{DEP_ORG_1}} | `condiciona` | {{DEP_DESC_3}} |

---

## 12. Riesgos y supuestos

### 12.1 Riesgos

| Riesgo ID | Descripción | Probabilidad | Impacto | Mitigación |
|-----------|-------------|--------------|---------|------------|
| ERSK-001 | {{RISK_1}} | baja/media/alta | baja/media/alta | {{MITIGATION_1}} |
| ERSK-002 | {{RISK_2}} | baja/media/alta | baja/media/alta | {{MITIGATION_2}} |

### 12.2 Supuestos

- {{ASSUMPTION_1}}
- {{ASSUMPTION_2}}

---

## 13. Requisitos funcionales candidatos asociados

> Requisitos funcionales que previsiblemente formarán parte de esta épica.

| FRS ID | Título | Estado | Observaciones |
|--------|--------|--------|---------------|
| {{FRS-ID-1}} | {{FRS_TITLE_1}} | {{FRS_STATUS_1}} | {{FRS_NOTE_1}} |
| {{FRS-ID-2}} | {{FRS_TITLE_2}} | {{FRS_STATUS_2}} | {{FRS_NOTE_2}} |

---

## 14. Historias de usuario candidatas

> Historias de usuario que desarrollan funcionalmente la épica.

| US ID | Título | Estado | Prioridad | Observaciones |
|-------|--------|--------|-----------|---------------|
| {{US-ID-1}} | {{US_TITLE_1}} | {{US_STATUS_1}} | {{US_PRIORITY_1}} | {{US_NOTE_1}} |
| {{US-ID-2}} | {{US_TITLE_2}} | {{US_STATUS_2}} | {{US_PRIORITY_2}} | {{US_NOTE_2}} |
| {{US-ID-3}} | {{US_TITLE_3}} | {{US_STATUS_3}} | {{US_PRIORITY_3}} | {{US_NOTE_3}} |

---

## 15. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Objetivo de negocio | {{BUSINESS_GOAL_ID}} | {{BUSINESS_GOAL}} |
| Módulo funcional | {{FUNCTIONAL_MODULE}} | {{FUNCTIONAL_MODULE_DESC}} |
| Submódulo funcional | {{FUNCTIONAL_SUBMODULE}} | {{FUNCTIONAL_SUBMODULE_DESC}} |
| Requisitos funcionales | {{FRS-LIST}} | Requisitos vinculados a la épica |
| Historias de usuario | {{US-LIST}} | Historias derivadas |
| Riesgos relacionados | {{RISK-LIST}} | Riesgos asociados |
| Tests derivados agregados | {{TEST-LIST}} | Tests agregados o vinculados cuando existan |
| Enlace RTM | {{LINK-NNN}} | Entrada en `traceability/RTM.yaml` |

---

## 16. Notas y decisiones abiertas

| # | Nota / pregunta | Responsable | Estado | Fecha objetivo | Decisión tomada | Evidencia |
|---|------------------|-------------|--------|----------------|-----------------|----------|
| 1 | {{NOTE_1}} | {{OWNER_1}} | abierta | {{TARGET_DATE_1}} | {{DECISION_1}} | {{EVIDENCE_REF_1}} |

> **Estados sugeridos:** `abierta` | `en-análisis` | `resuelta` | `descartada`

---

*Plantilla: `epic.template.md` v1.1.0*
