# {{FRS-ID}} — {{TITLE}}

---

## Metadatos

| Campo                        | Valor                                      |
|-----------------------------|--------------------------------------------|
| **ID**                      | {{FRS-ID}}                                 |
| **Versión**                 | {{VERSION}}                                |
| **Estado**                  | {{STATUS}}                                 |
| **Estabilidad**             | {{STABILITY}}                              |
| **Fecha**                   | {{DATE}}                                   |
| **Autor**                   | {{AUTHOR}}                                 |
| **Revisado por**            | {{REVIEWER}}                               |
| **Aprobado por**            | {{APPROVER}}                               |
| **Módulo Funcional**        | {{FUNCTIONAL_MODULE}}                      |
| **Submódulo Funcional**     | {{FUNCTIONAL_SUBMODULE}}                   |
| **Épica**                   | {{EPIC-ID}} — {{EPIC-TITLE}}               |
| **Prioridad**               | {{PRIORITY}}                               |
| **Porcentaje de completud** | {{COMPLETION_PERCENTAGE}}                  |
| **Fuente**                  | {{SOURCE}}                                 |
| **Sesión refinamiento**     | {{REF-ID}}                                 |
| **Enlace RTM**              | {{LINK-NNN}}                               |
| **Método verificación**     | {{VERIFICATION_METHOD}}                    |

> **Estados válidos:** `borrador` | `en-revisión` | `aprobado` | `rechazado` | `obsoleto`
>
> **Estabilidad válida:** `estable` | `volátil` | `en-cambio`
>
> **Prioridades válidas:** `crítica` | `alta` | `media` | `baja`
>
> **Métodos de verificación:** `test` | `inspección` | `demostración` | `análisis`
>
> **Porcentaje de completud:** valor entre `0%` y `100%`

---

## Historial de versiones

| Versión | Fecha      | Autor      | Cambios |
|---------|------------|------------|---------|
| 1.0.0   | {{DATE}}   | {{AUTHOR}} | Versión inicial |
| 2.1.0   | {{DATE}}   | {{AUTHOR}} | Añadidos bloques de alcance, disparador, restricciones, volumetría, datos, riesgos, observabilidad y resolución formal de abiertas |
| 2.2.0   | {{DATE}}   | {{AUTHOR}} | Añadidos en metadatos módulo funcional, submódulo funcional y porcentaje de completud |

---

## 1. Descripción

> Descripción funcional completa del requisito. Qué debe hacer el sistema, no cómo lo hace.

{{DESCRIPTION}}

---

## 2. Alcance y límites

> Delimita expresamente qué cubre este requisito y qué queda fuera para evitar ambigüedades y expansión de alcance.

### 2.1 Alcance incluido

- {{IN_SCOPE_1}}
- {{IN_SCOPE_2}}

### 2.2 Fuera de alcance

- {{OUT_OF_SCOPE_1}}
- {{OUT_OF_SCOPE_2}}

### 2.3 Límites del requisito

- {{BOUNDARY_1}}

---

## 3. Evento disparador

> Evento, acción o condición que inicia la ejecución de este requisito.

- **Tipo de disparador:** `usuario` | `sistema` | `programado` | `evento-externo`
- **Disparador principal:** {{TRIGGER_EVENT}}
- **Canal / origen:** {{TRIGGER_SOURCE}}
- **Frecuencia esperada:** {{TRIGGER_FREQUENCY}}

---

## 4. Actores y stakeholders

> Distinguir entre **actores del sistema** (interactúan directamente con el sistema) y **stakeholders** (tienen interés en el resultado pero no interactúan directamente).

### 4.1 Actores del sistema

| Actor | Tipo | Rol en este requisito |
|-------|------|-----------------------|
| {{ACTOR_1}} | `primario` \| `secundario` | {{ACTOR_ROLE_1}} |

> **Tipos:** `primario` (inicia el flujo) | `secundario` (participa en el flujo) | `sistema-externo`

### 4.2 Stakeholders interesados

| Stakeholder | Interés / Impacto |
|-------------|-------------------|
| {{STAKEHOLDER_1}} | {{STAKEHOLDER_INTEREST_1}} |

---

## 5. Entradas y salidas del sistema

> Descripción explícita de los datos que el sistema recibe y produce como resultado de este requisito.

### 5.1 Entradas

| # | Nombre | Tipo / Formato | Origen | Obligatorio | Validaciones |
|---|--------|----------------|--------|-------------|--------------|
| 1 | {{INPUT_NAME_1}} | {{INPUT_TYPE_1}} | {{INPUT_SOURCE_1}} | Sí / No | {{INPUT_VALIDATION_1}} |

### 5.2 Salidas

| # | Nombre | Tipo / Formato | Destino | Descripción |
|---|--------|----------------|---------|-------------|
| 1 | {{OUTPUT_NAME_1}} | {{OUTPUT_TYPE_1}} | {{OUTPUT_DEST_1}} | {{OUTPUT_DESC_1}} |

---

## 6. Calidad y sensibilidad del dato

> Define expectativas mínimas sobre la calidad del dato y su tratamiento funcional.

### 6.1 Clasificación de datos

| Dato / conjunto | Sensibilidad | Origen | Retención | Observaciones |
|-----------------|--------------|--------|-----------|---------------|
| {{DATASET_1}} | `público` \| `interno` \| `confidencial` \| `restringido` | {{DATA_ORIGIN_1}} | {{DATA_RETENTION_1}} | {{DATA_NOTE_1}} |

### 6.2 Reglas de calidad de datos

| ID | Dimensión | Regla / umbral |
|----|-----------|----------------|
| DQ-001 | completitud | {{DQ_RULE_1}} |
| DQ-002 | validez | {{DQ_RULE_2}} |
| DQ-003 | unicidad | {{DQ_RULE_3}} |
| DQ-004 | consistencia | {{DQ_RULE_4}} |

### 6.3 Consideraciones funcionales sobre datos

- {{DATA_CONSIDERATION_1}}
- {{DATA_CONSIDERATION_2}}

---

## 7. Precondiciones

> Condiciones que deben cumplirse **antes** de que este requisito pueda ejecutarse.

- {{PRECONDITION_1}}

---

## 8. Postcondiciones

> Estado del sistema **después** de que este requisito se haya ejecutado correctamente.

- {{POSTCONDITION_1}}

---

## 9. Supuestos

> Condiciones que se asumen como verdaderas para que este requisito sea válido. Si un supuesto no se cumple, el requisito debe revisarse.

- {{ASSUMPTION_1}}

---

## 10. Restricciones

> Limitaciones funcionales, regulatorias, organizativas o temporales que condicionan este requisito.

| Tipo | Restricción | Impacto / Justificación |
|------|-------------|-------------------------|
| `normativa` | {{CONSTRAINT_1}} | {{CONSTRAINT_IMPACT_1}} |
| `organizativa` | {{CONSTRAINT_2}} | {{CONSTRAINT_IMPACT_2}} |
| `proceso` | {{CONSTRAINT_3}} | {{CONSTRAINT_IMPACT_3}} |
| `temporal` | {{CONSTRAINT_4}} | {{CONSTRAINT_IMPACT_4}} |

> **Tipos sugeridos:** `normativa` | `organizativa` | `proceso` | `temporal` | `compatibilidad` | `seguridad`

---

## 11. Frecuencia, volumetría y criticidad operativa

> Información funcional útil para priorización, dimensionamiento posterior y análisis de impacto.

| Aspecto | Valor |
|---------|-------|
| **Frecuencia esperada** | {{EXPECTED_FREQUENCY}} |
| **Volumen estimado** | {{EXPECTED_VOLUME}} |
| **Picos esperados** | {{EXPECTED_PEAKS}} |
| **Ventana operativa** | {{OPERATING_WINDOW}} |
| **Criticidad de negocio** | `alta` \| `media` \| `baja` |
| **Impacto por indisponibilidad** | {{BUSINESS_IMPACT}} |

---

## 12. Flujo principal

> Secuencia de pasos del camino feliz (happy path).

1. {{STEP_1}}
2. {{STEP_2}}
3. {{STEP_3}}

---

## 13. Flujos alternativos

> Variaciones válidas del flujo principal.

### 13.1 {{ALT_FLOW_TITLE}}

- **Condición de activación:** {{ALT_CONDITION}}
- **Pasos:**
  1. {{ALT_STEP_1}}

---

## 14. Flujos de excepción

> Situaciones de error o fallo que el sistema debe manejar.

### 14.1 {{EXC_FLOW_TITLE}}

- **Condición de activación:** {{EXC_CONDITION}}
- **Respuesta del sistema:** {{EXC_RESPONSE}}
- **Código de error (si aplica):** {{EXC_CODE}}

---

## 15. Reglas de negocio

> Restricciones, políticas o lógica de dominio que aplican a este requisito.

| ID | Regla | Fuente / Referencia |
|----|-------|---------------------|
| BR-001 | {{RULE_1}} | {{RULE_SOURCE_1}} |

---

## 16. Requisitos no funcionales asociados

> Requisitos de calidad, rendimiento o seguridad directamente vinculados a este requisito funcional.

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| {{NFR-ID}} | {{NFR_TYPE}} | {{NFR_DESCRIPTION}} | {{NFR_METRIC}} |

> **Tipos válidos:** `rendimiento` | `seguridad` | `disponibilidad` | `usabilidad` | `escalabilidad` | `mantenibilidad`

---

## 17. Criterios de aceptación

> Condiciones concretas y verificables que deben cumplirse para considerar este requisito implementado y aceptado. Seguir el patrón **Dado / Cuando / Entonces**.
>
> **Cobertura mínima recomendada:** incluir al menos un criterio del flujo principal, uno de validación relevante, uno de error relevante y uno de autorización/seguridad si aplica.

### AC-001 — {{AC_TITLE_1}}

- **Dado** que {{GIVEN_1}}
- **Cuando** {{WHEN_1}}
- **Entonces** {{THEN_1}}

### AC-002 — {{AC_TITLE_2}}

- **Dado** que {{GIVEN_2}}
- **Cuando** {{WHEN_2}}
- **Entonces** {{THEN_2}}

---

## 18. Tests de alto nivel

> Casos de prueba de alto nivel derivados de los criterios de aceptación. No son tests unitarios; cubren el comportamiento observable del sistema desde fuera.

| ID | Tipo | Título | AC vinculado | Precondición del test | Datos de entrada | Resultado esperado | Resultado ejecución | Prioridad |
|----|------|--------|--------------|------------------------|------------------|-------------------|---------------------|-----------|
| TC-001 | funcional | {{TC_TITLE_1}} | AC-001 | {{TC_PRE_1}} | {{TC_INPUT_1}} | {{TC_EXPECTED_1}} | pendiente | alta |
| TC-002 | funcional | {{TC_TITLE_2}} | AC-002 | {{TC_PRE_2}} | {{TC_INPUT_2}} | {{TC_EXPECTED_2}} | pendiente | media |
| TC-003 | borde | {{TC_TITLE_3}} | AC-001 | {{TC_PRE_3}} | {{TC_INPUT_3}} | {{TC_EXPECTED_3}} | pendiente | media |
| TC-004 | negativo | {{TC_TITLE_4}} | AC-002 | {{TC_PRE_4}} | {{TC_INPUT_4}} | {{TC_EXPECTED_4}} | pendiente | alta |

> **Tipos de test:** `funcional` | `negativo` | `borde` | `rendimiento` | `seguridad` | `regresión`
>
> **Resultado ejecución:** `pendiente` | `pass` | `fail` | `bloqueado` | `no-aplica`

### Notas de testing

- **Entorno requerido:** {{TEST_ENV}}
- **Datos de prueba:** {{TEST_DATA}}
- **Dependencias externas:** {{TEST_DEPS}}
- **Responsable de ejecución:** {{TEST_OWNER}}

---

## 19. Riesgos y controles asociados

> Riesgos funcionales, operativos o de cumplimiento vinculados al requisito, junto con sus controles previstos.

| Riesgo ID | Descripción del riesgo | Probabilidad | Impacto | Control / mitigación | Evidencia esperada |
|-----------|------------------------|--------------|---------|----------------------|--------------------|
| RSK-001 | {{RISK_1}} | baja/media/alta | baja/media/alta | {{CONTROL_1}} | {{EVIDENCE_1}} |
| RSK-002 | {{RISK_2}} | baja/media/alta | baja/media/alta | {{CONTROL_2}} | {{EVIDENCE_2}} |

---

## 20. Observabilidad funcional

> Define qué evidencias funcionales debe producir el sistema para poder verificar comportamiento, operación y resultado de negocio.

### 20.1 Eventos funcionales a registrar

| Evento | Cuándo ocurre | Datos mínimos a registrar |
|--------|----------------|---------------------------|
| {{OBS_EVENT_1}} | {{OBS_WHEN_1}} | {{OBS_DATA_1}} |
| {{OBS_EVENT_2}} | {{OBS_WHEN_2}} | {{OBS_DATA_2}} |

### 20.2 Alertas funcionales

| Alerta | Condición de activación | Destinatario / acción esperada |
|--------|--------------------------|--------------------------------|
| {{ALERT_1}} | {{ALERT_CONDITION_1}} | {{ALERT_ACTION_1}} |

### 20.3 Métricas / KPIs de negocio

| Indicador | Fórmula / definición | Objetivo / umbral |
|-----------|----------------------|-------------------|
| {{KPI_1}} | {{KPI_DEF_1}} | {{KPI_TARGET_1}} |

---

## 21. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Requisito de negocio | {{BRS-ID}} | {{BRS_TITLE}} |
| Épica | {{EPIC-ID}} | {{EPIC_TITLE}} |
| Caso de uso | {{UC-ID}} | {{UC_TITLE}} |
| Historia de usuario | {{US-ID}} | {{US_TITLE}} |
| Servicio | {{SVC-ID}} | {{SVC_NAME}} |
| ADR relacionado | {{ADR-ID}} | {{ADR_TITLE}} |
| Riesgo relacionado | {{RISK-ID}} | {{RISK_TITLE}} |
| Control relacionado | {{CTRL-ID}} | {{CTRL_TITLE}} |
| Sesión refinamiento | {{REF-ID}} | {{REF_TITLE}} |
| Tests de alto nivel | TC-001, TC-002, TC-003, TC-004 | Ver §18 |
| Enlace RTM | {{LINK-NNN}} | Entrada en `traceability/RTM.yaml` |

---

## 22. Dependencias

> Otros requisitos, servicios o sistemas de los que depende este requisito, incluyendo relaciones lógicas entre requisitos.

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Requisito FRS | {{DEP_FRS_ID}} | `depende-de` \| `extiende` \| `reemplaza` \| `conflicto` | {{DEP_DESCRIPTION}} |
| Servicio ext. | {{DEP_SVC}} | `consume` \| `publica` | {{DEP_SVC_DESCRIPTION}} |

> **Relaciones entre requisitos:** `depende-de` | `extiende` | `especializa` | `reemplaza` | `conflicto`

---

## 23. Notas y decisiones abiertas

> Registro formal de cuestiones pendientes y su resolución esperada. Toda decisión cerrada debería enlazarse a evidencia o sesión de refinamiento cuando aplique.

| # | Nota / Pregunta abierta | Responsable | Estado | Fecha objetivo | Decisión tomada | Impacto | Evidencia / referencia |
|---|--------------------------|-------------|--------|----------------|-----------------|---------|------------------------|
| 1 | {{NOTE_1}} | {{OWNER_1}} | abierta | {{TARGET_DATE_1}} | {{DECISION_1}} | {{IMPACT_1}} | {{EVIDENCE_REF_1}} |

> **Estados sugeridos:** `abierta` | `en-análisis` | `resuelta` | `descartada`

---

*Plantilla: `functional-requirement.template.md` v2.2.0 — AgentProjectFromScratch v1.2.2*
