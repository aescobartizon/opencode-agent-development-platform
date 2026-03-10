# FRS-UBUS-001 — Consulta de próximas llegadas e incidencias por parada urbana

---

## Metadatos

| Campo                        | Valor |
|-----------------------------|-------|
| **ID**                      | FRS-UBUS-001 |
| **Versión**                 | 1.0.0 |
| **Estado**                  | en-revisión |
| **Estabilidad**             | estable |
| **Fecha**                   | 2026-03-10 |
| **Autor**                   | Oficina de Análisis Funcional |
| **Revisado por**            | Responsable de Producto de Movilidad Urbana |
| **Aprobado por**            | Dirección de Servicios Digitales |
| **Módulo Funcional**        | Experiencia Digital del Viajero |
| **Submódulo Funcional**     | Información Operativa y Ticketing Urbano |
| **Épica**                   | EPIC-UBUS-01 — Autoservicio digital para información operativa y ticketing básico en autobús urbano |
| **Prioridad**               | alta |
| **Porcentaje de completud** | 86% |
| **Fuente**                  | analysis/urban-bus-initial-analysis.txt |
| **Sesión refinamiento**     | REF-UBUS-2026-03-10-01 |
| **Enlace RTM**              | traceability/RTM.yaml#FRS-UBUS-001 |
| **Método verificación**     | test |

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

| Versión | Fecha | Autor | Cambios |
|---------|-------|-------|---------|
| 1.0.0 | 2026-03-10 | Oficina de Análisis Funcional | Versión inicial |
| 2.1.0 | 2026-03-10 | Oficina de Análisis Funcional | Añadidos bloques de alcance, disparador, restricciones, volumetría, datos, riesgos, observabilidad y abiertas |
| 2.2.0 | 2026-03-10 | Oficina de Análisis Funcional | Añadidos módulo funcional, submódulo funcional y porcentaje de completud |
| 2.3.0 | 2026-03-10 | Oficina de Análisis Funcional | Refuerzo de trazabilidad a US, tests y continuidad hacia Gherkin |

---

## 1. Descripción

El sistema debe permitir al viajero consultar una parada concreta del servicio urbano de autobuses y visualizar la información operativa relevante para tomar una decisión de viaje en ese momento.

La consulta debe mostrar, como mínimo, las próximas llegadas previstas a la parada y, cuando existan, las incidencias activas o condiciones básicas de accesibilidad que puedan afectar al uso del servicio por parte del viajero.

---

## 2. Alcance y límites

### 2.1 Alcance incluido

- Consulta de una parada urbana concreta.
- Visualización de próximas llegadas previstas.
- Visualización de incidencias activas relevantes para la parada o líneas asociadas.
- Visualización de información básica de accesibilidad cuando esté disponible y validada.
- Comunicación clara de ausencia de datos o indisponibilidad del servicio.

### 2.2 Fuera de alcance

- Planificación avanzada de rutas.
- Recomendación automática de alternativas de viaje.
- Gestión de flota o regulación operativa interna.
- Compra o validación de billetes.
- Mapas avanzados o navegación geográfica compleja.

### 2.3 Límites del requisito

- La primera versión se centra en la consulta por parada desde aplicación móvil.
- La taxonomía detallada de accesibilidad puede requerir refinamiento posterior.
- Solo deben mostrarse incidencias publicables y validadas por la operación del servicio.

---

## 3. Evento disparador

- **Tipo de disparador:** `usuario`
- **Disparador principal:** El viajero selecciona o consulta una parada urbana desde la aplicación móvil.
- **Canal / origen:** Aplicación móvil del servicio de transporte urbano.
- **Frecuencia esperada:** Muy alta en uso cotidiano, especialmente en franjas punta.

---

## 4. Actores y stakeholders

### 4.1 Actores del sistema

| Actor | Tipo | Rol en este requisito |
|-------|------|-----------------------|
| Viajero urbano | `primario` | Consulta la información operativa de una parada |
| Aplicación móvil | `secundario` | Presenta la información funcional al usuario |
| Backend de información operativa | `sistema-externo` | Proporciona próximas llegadas, incidencias y metadatos de accesibilidad |

### 4.2 Stakeholders interesados

| Stakeholder | Interés / Impacto |
|-------------|-------------------|
| Dirección de Servicios Digitales | Mejorar la experiencia digital del viajero |
| Operaciones Urbanas | Garantizar que la información visible sea coherente con la operación real |
| Atención al Cliente | Reducir consultas repetitivas sobre llegadas e incidencias |
| Ciudadanía / usuario final | Obtener información útil y comprensible antes del viaje |

---

## 5. Entradas y salidas del sistema

### 5.1 Entradas

| # | Nombre | Tipo / Formato | Origen | Obligatorio | Validaciones |
|---|--------|----------------|--------|-------------|--------------|
| 1 | stopId | string | Usuario / app | Sí | Debe existir en el catálogo de paradas |
| 2 | lineId | string | Usuario / app | No | Si se informa, debe estar asociada a la parada |
| 3 | includeAlerts | boolean | App | No | Valor por defecto `true` |
| 4 | includeAccessibility | boolean | App | No | Valor por defecto `true` |

### 5.2 Salidas

| # | Nombre | Tipo / Formato | Destino | Descripción |
|---|--------|----------------|---------|-------------|
| 1 | arrivals | array | Usuario / app | Próximas llegadas previstas |
| 2 | alerts | array | Usuario / app | Incidencias activas relevantes |
| 3 | accessibility | object / null | Usuario / app | Información básica de accesibilidad |
| 4 | queryStatus | string | Usuario / app | Estado funcional de la consulta |

---

## 6. Calidad y sensibilidad del dato

### 6.1 Clasificación de datos

| Dato / conjunto | Sensibilidad | Origen | Retención | Observaciones |
|-----------------|--------------|--------|-----------|---------------|
| Predicciones de llegada | `interno` | Sistema operativo | 30 días | Dato operativo sujeto a actualización frecuente |
| Incidencias activas | `interno` | Operaciones Urbanas | 30 días | Deben estar clasificadas y validadas |
| Datos de accesibilidad visibles | `interno` | Catálogo de operación | 90 días | Solo deben mostrarse cuando estén verificados |
| Identificador de parada | `público` | Catálogo de red | Permanente | Dato visible al viajero |

### 6.2 Reglas de calidad de datos

| ID | Dimensión | Regla / umbral |
|----|-----------|----------------|
| DQ-001 | completitud | Toda llegada visible debe incluir línea, destino y tiempo estimado |
| DQ-002 | validez | La parada consultada debe existir en el catálogo oficial |
| DQ-003 | unicidad | No deben mostrarse duplicados de la misma llegada |
| DQ-004 | consistencia | Las incidencias y datos de accesibilidad deben corresponder a la parada o línea consultada |

### 6.3 Consideraciones funcionales sobre datos

- La información debe ser entendible para un usuario no técnico.
- La ausencia de incidencias no debe confundirse con indisponibilidad de información.
- La accesibilidad solo debe mostrarse si el dato es fiable y mantenido por el cliente.

---

## 7. Precondiciones

- La parada debe existir en el catálogo de la red urbana.
- El backend de información operativa debe estar disponible.
- Debe existir una fuente válida para próximas llegadas.
- Las incidencias visibles deben estar previamente catalogadas como publicables.

---

## 8. Postcondiciones

- El usuario visualiza una respuesta operativa válida para la parada consultada.
- La consulta queda registrada como evento funcional.
- El sistema deja evidencia suficiente para medir uso, errores y degradación.

---

## 9. Supuestos

- Existe una fuente operativa que proporciona próximas llegadas por parada.
- Operaciones Urbanas mantiene un catálogo mínimo de incidencias visibles al usuario.
- La información básica de accesibilidad puede publicarse de forma controlada.
- La aplicación móvil es el canal prioritario para esta funcionalidad en la primera fase.

---

## 10. Restricciones

| Tipo | Restricción | Impacto / Justificación |
|------|-------------|-------------------------|
| `organizativa` | Solo pueden mostrarse incidencias aprobadas para publicación al viajero | Evita mensajes inconsistentes o no validados |
| `proceso` | La consulta no debe modificar ningún estado de negocio | Es una operación de solo lectura |
| `temporal` | La respuesta debe corresponder al instante de consulta o a una ventana operativa válida | Reduce riesgo de información obsoleta |
| `compatibilidad` | El mismo comportamiento funcional debe ser consistente en iOS y Android | Garantiza una experiencia homogénea |
| `seguridad` | No deben exponerse datos internos no relevantes para el viajero | Protege información operativa no destinada a usuario final |

---

## 11. Frecuencia, volumetría y criticidad operativa

| Aspecto | Valor |
|---------|-------|
| **Frecuencia esperada** | Muy alta |
| **Volumen estimado** | 250.000 consultas diarias en escenario de operación madura |
| **Picos esperados** | 07:00–09:30 y 17:00–20:30 |
| **Ventana operativa** | 24x7 |
| **Criticidad de negocio** | `alta` |
| **Impacto por indisponibilidad** | Pérdida de confianza en el canal digital, incremento de incertidumbre y aumento de consultas manuales |

---

## 12. Flujo principal

1. El viajero accede al detalle de una parada urbana en la aplicación móvil.
2. La aplicación solicita al backend la información operativa de esa parada.
3. El backend recupera próximas llegadas, incidencias activas y datos básicos de accesibilidad si existen.
4. El sistema valida que la información sea coherente con la parada consultada.
5. La aplicación muestra al usuario las próximas llegadas y, cuando aplique, incidencias y accesibilidad relevante.

---

## 13. Flujos alternativos

### 13.1 Consulta filtrada por línea

- **Condición de activación:** El usuario selecciona una línea concreta dentro de la parada.
- **Pasos:**
  1. El sistema filtra la respuesta por la línea indicada.
  2. La aplicación muestra únicamente llegadas e incidencias relevantes para esa línea.

### 13.2 Consulta sin incidencias activas

- **Condición de activación:** No existen incidencias activas para la parada o línea.
- **Pasos:**
  1. El sistema devuelve una respuesta válida con lista vacía de alertas.
  2. La aplicación informa que no hay incidencias activas.

---

## 14. Flujos de excepción

### 14.1 Parada inexistente

- **Condición de activación:** El `stopId` no existe en el catálogo oficial.
- **Respuesta del sistema:** El sistema informa que la parada consultada no es válida.
- **Código de error (si aplica):** UBUS-ARR-404

### 14.2 Servicio operativo no disponible

- **Condición de activación:** No puede obtenerse información operativa en ese momento.
- **Respuesta del sistema:** El sistema informa de indisponibilidad temporal sin mostrar información inconsistente.
- **Código de error (si aplica):** UBUS-ARR-503

### 14.3 Información de accesibilidad no catalogada

- **Condición de activación:** Existen metadatos incompletos o no aprobados para publicación.
- **Respuesta del sistema:** El sistema omite esa información o muestra mensaje neutro de no disponibilidad.
- **Código de error (si aplica):** UBUS-ARR-204-A

---

## 15. Reglas de negocio

| ID | Regla | Fuente / Referencia |
|----|-------|---------------------|
| BR-001 | Toda llegada visible debe pertenecer a la parada consultada | Política operativa de información al viajero |
| BR-002 | Toda incidencia visible debe estar activa y ser publicable | Operaciones Urbanas |
| BR-003 | La ausencia de incidencias no debe presentarse como error | Criterio funcional de experiencia de usuario |
| BR-004 | La información de accesibilidad solo debe mostrarse cuando esté validada | Criterio de publicación del cliente |

---

## 16. Requisitos no funcionales asociados

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| NFR-UBUS-ARR-01 | rendimiento | La consulta debe responder con rapidez adecuada para uso cotidiano | p95 < 2 segundos |
| NFR-UBUS-ARR-02 | disponibilidad | El servicio debe estar disponible de forma continua | 99,5% mensual |
| NFR-UBUS-ARR-03 | usabilidad | Los mensajes deben ser comprensibles para ciudadanía no técnica | Validación por negocio y UX |
| NFR-UBUS-ARR-04 | mantenibilidad | Los errores funcionales deben ser catalogables | 100% de errores con código funcional |

---

## 17. Criterios de aceptación

### AC-001 — Mostrar próximas llegadas válidas

- **Dado** que existe una parada urbana válida
- **Cuando** el usuario consulta la parada
- **Entonces** el sistema debe mostrar las próximas llegadas con línea, destino y tiempo estimado

### AC-002 — Mostrar incidencias relevantes

- **Dado** que existen incidencias activas publicables para la parada o línea
- **Cuando** el usuario consulta la parada
- **Entonces** el sistema debe mostrar esas incidencias de forma comprensible

### AC-003 — Diferenciar entre ausencia de incidencias e indisponibilidad

- **Dado** que no existen incidencias activas o no hay información disponible
- **Cuando** el usuario consulta la parada
- **Entonces** el sistema debe distinguir claramente ambos escenarios

### AC-004 — Mostrar accesibilidad básica cuando exista

- **Dado** que la parada dispone de información básica de accesibilidad validada
- **Cuando** el usuario consulta la parada
- **Entonces** el sistema debe mostrar esa información de forma clara y neutra

---

## 18. Tests de alto nivel

| ID | Tipo | Título | AC vinculado | US derivada objetivo | Riesgo cubierto | Precondición del test | Datos de entrada | Resultado esperado | Resultado ejecución | Prioridad |
|----|------|--------|--------------|----------------------|-----------------|------------------------|------------------|-------------------|---------------------|-----------|
| TC-UBUS-ARR-001 | funcional | Consulta válida de próximas llegadas | AC-001 | US-UBUS-001 | — | Parada existente y backend operativo | stopId válido | Se muestran próximas llegadas correctas | pendiente | alta |
| TC-UBUS-ARR-002 | funcional | Consulta de incidencias activas | AC-002 | US-UBUS-002 | RSK-002 | Existen alertas activas publicables | stopId con alertas | Se muestran incidencias relevantes | pendiente | alta |
| TC-UBUS-ARR-003 | borde | Parada válida sin incidencias | AC-003 | US-UBUS-002 | — | Parada operativa sin alertas | stopId válido | Se informa ausencia de incidencias sin error | pendiente | media |
| TC-UBUS-ARR-004 | negativo | Parada inexistente | AC-001 | US-UBUS-001 | RSK-001 | stopId no catalogado | stopId inválido | Se devuelve error funcional controlado | pendiente | alta |

### Notas de testing

- **Entorno requerido:** Sandbox de información operativa urbana
- **Datos de prueba:** Paradas válidas, inválidas, con incidencias y con datos de accesibilidad
- **Dependencias externas:** Backend de información operativa
- **Responsable de ejecución:** QA funcional movilidad urbana

---

## 19. Riesgos y controles asociados

| Riesgo ID | Descripción del riesgo | Probabilidad | Impacto | Control / mitigación | Evidencia esperada |
|-----------|------------------------|--------------|---------|----------------------|--------------------|
| RSK-001 | Consulta de parada inexistente o mal identificada | media | media | Validación estricta de catálogo de paradas | Respuesta controlada UBUS-ARR-404 |
| RSK-002 | Incidencias o accesibilidad no suficientemente normalizadas | alta | alta | Refinamiento del catálogo funcional con Operaciones Urbanas | Catálogo aprobado y visible |
| RSK-003 | Información operativa desactualizada o ambigua | media | alta | Reglas de refresco y comunicación diferenciada de degradación | Eventos y alertas funcionales monitorizadas |

> **Regla obligatoria:** todo riesgo con impacto `alto` debe quedar trazado en la sección `18. Tests de alto nivel` y posteriormente en la US derivada correspondiente mediante criterios de aceptación y tests Gherkin.

---

## 20. Observabilidad funcional

### 20.1 Eventos funcionales a registrar

| Evento | Cuándo ocurre | Datos mínimos a registrar |
|--------|----------------|---------------------------|
| ARRIVAL_LOOKUP_REQUESTED | Al iniciar una consulta de parada | stopId, lineId, timestamp |
| ARRIVAL_LOOKUP_RETURNED | Al devolver una respuesta válida | stopId, totalArrivals, totalAlerts |
| ARRIVAL_LOOKUP_FAILED | Al producirse un error funcional | stopId, errorCode, timestamp |

### 20.2 Alertas funcionales

| Alerta | Condición de activación | Destinatario / acción esperada |
|--------|--------------------------|--------------------------------|
| ALERT-ARRIVALS-DEGRADED | Elevado ratio de consultas sin datos válidos | Soporte operativo revisa backend |
| ALERT-ACCESSIBILITY-TAXONOMY-MISSING | Se detectan categorías no mapeadas | Operaciones Urbanas revisa catálogo funcional |

### 20.3 Métricas / KPIs de negocio

| Indicador | Fórmula / definición | Objetivo / umbral |
|-----------|----------------------|-------------------|
| KPI-ARR-01 | Consultas operativas exitosas / consultas totales | > 95% |
| KPI-ARR-02 | Consultas con incidencias correctamente clasificadas / consultas con alertas | > 95% |

---

## 21. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Requisito de negocio | BGS-UBUS-01 | Incrementar el autoservicio digital del viajero urbano |
| Épica | EPIC-UBUS-01 | Autoservicio digital para información operativa y ticketing básico en autobús urbano |
| Historias de usuario derivadas | US-UBUS-001, US-UBUS-002 | Historias derivadas del requisito |
| Servicio | SVC-UBUS-REALTIME | Servicio de información operativa por parada |
| ADR relacionado | ADR-UBUS-001 | Exposición de información operativa urbana al viajero |
| Riesgo relacionado | RSK-001, RSK-002, RSK-003 | Riesgos funcionales asociados |
| Control relacionado | CTRL-UBUS-ARR-01 | Validación de catálogo y clasificación funcional |
| Sesión refinamiento | REF-UBUS-2026-03-10-01 | Refinamiento inicial |
| Tests de alto nivel | TC-UBUS-ARR-001, TC-UBUS-ARR-002, TC-UBUS-ARR-003, TC-UBUS-ARR-004 | Ver §18 |
| Cobertura funcional derivada | US-UBUS-001, US-UBUS-002 + TC-UBUS-ARR-* | Debe continuar en US con AC y Gherkin |
| Enlace RTM | traceability/RTM.yaml#FRS-UBUS-001 | Entrada en `traceability/RTM.yaml` |

---

## 22. Dependencias

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Requisito FRS | FRS-UBUS-002 | `relacionada-con` | Comparte contexto funcional general de autoservicio del viajero |
| Servicio ext. | SVC-UBUS-REALTIME | `consume` | Proporciona llegadas, incidencias y accesibilidad |
| Servicio ext. | CAT-UBUS-STOPS | `consume` | Catálogo oficial de paradas urbanas |

---

## 23. Notas y decisiones abiertas

| # | Nota / Pregunta abierta | Responsable | Estado | Fecha objetivo | Decisión tomada | Impacto | Evidencia / referencia |
|---|--------------------------|-------------|--------|----------------|-----------------|---------|------------------------|
| 1 | Confirmar catálogo inicial de categorías de accesibilidad visibles al viajero | Operaciones Urbanas | abierta | 2026-03-18 | — | Alto | REF-UBUS-2026-03-10-01 |
| 2 | Definir severidad mínima de incidencias que deben mostrarse en primera versión | Producto Digital | abierta | 2026-03-18 | — | Medio | REF-UBUS-2026-03-10-01 |

---

*Plantilla: `functional-requirement.template.md` v2.3.0 — AgentProjectFromScratch v1.2.2*
