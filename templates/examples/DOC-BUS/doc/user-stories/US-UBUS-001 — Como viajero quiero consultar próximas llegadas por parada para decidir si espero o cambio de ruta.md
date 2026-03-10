# US-UBUS-001 — Como viajero quiero consultar próximas llegadas por parada para decidir si espero o cambio de ruta

---

## Metadatos

| Campo                        | Valor |
|-----------------------------|-------|
| **ID**                      | US-UBUS-001 |
| **Versión**                 | 1.0.0 |
| **Estado**                  | lista |
| **Estabilidad**             | estable |
| **Fecha**                   | 2026-03-10 |
| **Autor**                   | Oficina de Análisis Funcional |
| **Revisado por**            | Responsable de Producto de Movilidad Urbana |
| **Aprobado por**            | Dirección de Servicios Digitales |
| **Módulo Funcional**        | Experiencia Digital del Viajero |
| **Submódulo Funcional**     | Información Operativa y Ticketing Urbano |
| **Épica asociada**          | EPIC-UBUS-01 — Autoservicio digital para información operativa y ticketing básico en autobús urbano |
| **FRS asociado principal**  | FRS-UBUS-001 — Consulta de próximas llegadas e incidencias por parada urbana |
| **Prioridad**               | alta |
| **Tipo de historia**        | funcional |
| **Porcentaje de completud** | 100% |
| **Fuente**                  | analysis/urban-bus-initial-analysis.txt |
| **Sesión refinamiento**     | REF-UBUS-2026-03-10-01 |
| **Enlace RTM**              | traceability/RTM.yaml#US-UBUS-001 |
| **Método verificación**     | test |

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

| Versión | Fecha | Autor | Cambios |
|---------|-------|-------|---------|
| 1.0.0 | 2026-03-10 | Oficina de Análisis Funcional | Versión inicial |

---

## 1. Historia de usuario

**Como** viajero urbano  
**Quiero** consultar las próximas llegadas de una parada  
**Para** decidir si espero, camino a otra parada o cambio de línea

---

## 2. Objetivo funcional

Permitir al usuario obtener, de forma rápida y comprensible, las próximas llegadas previstas en una parada concreta del servicio urbano de autobuses.

---

## 3. Contexto

El viajero urbano necesita tomar decisiones inmediatas antes de iniciar o continuar su desplazamiento. La información de próximas llegadas es uno de los datos más críticos para reducir incertidumbre y mejorar la experiencia de uso del servicio.

---

## 4. Alcance

### 4.1 Incluido

- Consulta de una parada concreta mediante identificador válido.
- Visualización de próximas llegadas con línea, destino y tiempo estimado.
- Gestión de error funcional cuando la parada no existe.
- Evitar duplicados visibles en la respuesta mostrada al usuario.

### 4.2 Fuera de alcance

- Visualización de incidencias detalladas.
- Información avanzada de accesibilidad.
- Recomendación de rutas alternativas.
- Mapas o navegación geográfica avanzada.

### 4.3 Límites

- La historia se centra en experiencia móvil.
- La respuesta se limita a la parada consultada.
- No modifica ningún estado de negocio; solo informa.

---

## 5. Actor principal y actores relacionados

### 5.1 Actor principal

| Actor | Descripción |
|-------|-------------|
| Viajero urbano | Usuario que consulta una parada desde la aplicación móvil |

### 5.2 Actores relacionados

| Actor | Relación con la historia |
|-------|---------------------------|
| Aplicación móvil | Solicita y presenta la respuesta |
| Backend de información operativa | Devuelve próximas llegadas por parada |

---

## 6. Disparador

- El usuario abre el detalle de una parada en la aplicación móvil.

---

## 7. Precondiciones

- La parada existe en el catálogo oficial de la red urbana.
- El backend de información operativa está disponible.
- Existe información de predicción de llegadas para la parada o el sistema puede responder de forma controlada.

---

## 8. Postcondiciones

### 8.1 Éxito

- El usuario visualiza próximas llegadas válidas para la parada consultada.
- La consulta queda registrada como evento funcional.

### 8.2 Fallo

- El sistema devuelve un error funcional controlado o una respuesta sin datos inconsistentes.

---

## 9. Reglas de negocio asociadas

| ID | Regla | Fuente / referencia |
|----|-------|---------------------|
| BR-001 | Toda llegada visible debe pertenecer a la parada consultada | FRS-UBUS-001 |
| BR-002 | Toda llegada visible debe incluir línea, destino y tiempo estimado | FRS-UBUS-001 |
| BR-003 | No deben mostrarse duplicados de la misma llegada | FRS-UBUS-001 |

---

## 10. Datos de entrada y salida

### 10.1 Entradas

| # | Entrada | Origen | Obligatoria | Validaciones |
|---|---------|--------|-------------|--------------|
| 1 | stopId | Usuario / app | Sí | Debe existir en el catálogo oficial |
| 2 | lineId | Usuario / app | No | Si se informa, debe corresponder a la parada |

### 10.2 Salidas

| # | Salida | Destino | Descripción |
|---|--------|---------|-------------|
| 1 | arrivals | Usuario / app | Lista de próximas llegadas |
| 2 | queryStatus | Usuario / app | Estado funcional de la consulta |

---

## 11. Criterios de aceptación

### AC-001 — Consulta válida de próximas llegadas

- **Dado** que existe una parada urbana válida
- **Cuando** el usuario consulta la parada
- **Entonces** el sistema debe mostrar las próximas llegadas con línea, destino y tiempo estimado

### AC-002 — Error controlado para parada inexistente

- **Dado** que la parada consultada no existe
- **Cuando** el usuario intenta consultar esa parada
- **Entonces** el sistema debe devolver un error funcional controlado

### AC-003 — Respuesta sin duplicados visibles

- **Dado** que el backend devuelve varias llegadas para la parada
- **Cuando** la aplicación presenta la información al usuario
- **Entonces** no deben mostrarse duplicados visibles de la misma llegada

---

## 12. Escenarios Gherkin asociados

### Feature: Consultar próximas llegadas por parada

```gherkin
Feature: Consultar próximas llegadas por parada
  As a viajero urbano
  I want consultar las próximas llegadas de una parada
  So that decidir si espero, camino a otra parada o cambio de línea

  Scenario: Consulta válida de próximas llegadas
    Given existe una parada urbana válida
    When el usuario consulta la parada
    Then el sistema muestra las próximas llegadas con línea, destino y tiempo estimado

  Scenario: Parada inexistente
    Given la parada consultada no existe
    When el usuario intenta consultar esa parada
    Then el sistema devuelve un error funcional controlado

  Scenario: Respuesta sin duplicados visibles
    Given el backend devuelve varias llegadas para la parada
    When la aplicación presenta la información al usuario
    Then no se muestran duplicados visibles de la misma llegada
```
## 13. Trazabilidad de tests Gherkin

> Relación explícita entre historia, criterios de aceptación y escenarios Gherkin.

| Test ID | Feature | Escenario | Tipo | AC cubierto | Estado | Observaciones |
|---------|---------|-----------|------|-------------|--------|---------------|
| GT-001 | Consultar próximas llegadas por parada | Consulta válida de próximas llegadas | funcional | AC-001 | implementado | Cubre el flujo principal |
| GT-002 | Consultar próximas llegadas por parada | Parada inexistente | negativo | AC-002 | implementado | Cubre error controlado |
| GT-003 | Consultar próximas llegadas por parada | Respuesta sin duplicados visibles | borde / error | AC-003 | pendiente | Requiere dataset específico |

> **Estados sugeridos de test:** `pendiente` | `implementado` | `ejecutado-pass` | `ejecutado-fail` | `bloqueado`

---

## 14. Trazabilidad de cobertura funcional y riesgo

| Cobertura ID | Tipo | Referencia origen | AC relacionado | Test Gherkin | Riesgo relacionado | Control validado | Estado cobertura | Evidencia |
|--------------|------|-------------------|----------------|--------------|--------------------|------------------|------------------|-----------|
| COV-001 | funcional | FRS-UBUS-001 | AC-001 | GT-001 | — | Validación de estructura mínima de la respuesta | cubierta | qa/us-ubus-001/gt-001.md |
| COV-002 | riesgo | FRS-UBUS-001 | AC-002 | GT-002 | USRSK-001 | Error funcional controlado para parada inválida | cubierta | qa/us-ubus-001/gt-002.md |
| COV-003 | funcional | FRS-UBUS-001 | AC-003 | GT-003 | — | Eliminación de duplicados visibles | parcial | Dataset específico pendiente |

---

## 15. Requisitos no funcionales asociados

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| NFR-UBUS-ARR-01 | rendimiento | La consulta debe responder con rapidez adecuada para uso cotidiano | p95 < 2 segundos |
| NFR-UBUS-ARR-03 | usabilidad | La respuesta debe ser comprensible para ciudadanía no técnica | Validación UX y de negocio |

---

## 16. Dependencias

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Épica | EPIC-UBUS-01 | `pertenece-a` | Épica funcional contenedora |
| FRS | FRS-UBUS-001 | `deriva-de` | Requisito funcional principal |
| Historia | US-UBUS-002 | `relacionada-con` | Historia complementaria sobre incidencias y accesibilidad |
| Servicio ext. | SVC-UBUS-REALTIME | `consume` | Proporciona próximas llegadas por parada |

---

## 17. Especificación OpenAPI derivada

| Artefacto API | Ruta / ID | Tipo | Operación / evento | Estado | Observaciones |
|---------------|-----------|------|--------------------|--------|---------------|
| OpenAPI spec | spec/open-api/urban-bus-arrivals.openapi.yaml | `openapi` | GET /stops/{stopId}/arrivals | definido | Operación principal de consulta |
| OpenAPI spec | spec/open-api/urban-bus-arrivals.openapi.yaml#/components/schemas/Arrival | `openapi` | Schema Arrival | definido | Esquema base de llegada |

---

## 18. Observabilidad funcional

### 18.1 Eventos funcionales

| Evento | Cuándo ocurre | Datos mínimos |
|--------|----------------|---------------|
| ARRIVAL_LOOKUP_REQUESTED | Al iniciar la consulta | stopId, timestamp |
| ARRIVAL_LOOKUP_RETURNED | Al devolver una respuesta válida | stopId, totalArrivals |

### 18.2 Alertas

| Alerta | Condición | Acción esperada |
|--------|-----------|-----------------|
| ALERT-ARRIVAL-API-DEGRADED | Elevado ratio de respuestas degradadas | Revisar backend operativo |

### 18.3 KPIs

| KPI | Definición | Objetivo |
|-----|------------|----------|
| KPI-US-UBUS-001 | Consultas válidas / consultas totales | > 95% |

---

## 19. Riesgos y controles

| Riesgo ID | Descripción | Probabilidad | Impacto | Control / mitigación |
|-----------|-------------|--------------|---------|----------------------|
| USRSK-001 | Consulta de una parada inválida o inexistente | media | media | Validación de catálogo y error funcional controlado |

---

## 20. Trazabilidad

> Esta sección es obligatoria y debe estar completa antes de dar la historia por lista o cerrada.

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Objetivo de negocio | BGS-UBUS-01 | Incrementar el autoservicio digital del viajero urbano |
| Módulo funcional | Experiencia Digital del Viajero | Dominio funcional principal |
| Submódulo funcional | Información Operativa y Ticketing Urbano | Contexto funcional de operación visible al viajero |
| Épica asociada | EPIC-UBUS-01 | Épica de autoservicio digital urbano |
| FRS principal | FRS-UBUS-001 | Consulta de próximas llegadas e incidencias por parada urbana |
| FRS relacionados | — | No aplica |
| Historia relacionada | US-UBUS-002 | Historia complementaria |
| Especificaciones OpenAPI derivadas | spec/open-api/urban-bus-arrivals.openapi.yaml | OpenAPI de consulta operativa |
| Criterios de aceptación | AC-001, AC-002, AC-003 | Criterios definidos en §11 |
| Tests Gherkin | GT-001, GT-002, GT-003 | Escenarios definidos en §13 |
| Cobertura funcional y riesgo | COV-001, COV-002, COV-003 | Cobertura definida en §14 |
| Riesgos relacionados | USRSK-001 | Riesgo asociado |
| ADR relacionado | ADR-UBUS-001 | Exposición de información operativa urbana al viajero |
| Enlace RTM | traceability/RTM.yaml#US-UBUS-001 | Entrada en `traceability/RTM.yaml` |

---

## 21. Notas y decisiones abiertas

| # | Nota / pregunta | Responsable | Estado | Fecha objetivo | Decisión tomada | Evidencia |
|---|------------------|-------------|--------|----------------|-----------------|----------|
| 1 | Confirmar si se mostrará hora absoluta además de minutos estimados | Producto Digital | resuelta | 2026-03-10 | Se mostrarán ambos formatos cuando existan | REF-UBUS-2026-03-10-01 |

---

*Plantilla: `user-story.template.md` v1.2.0*
