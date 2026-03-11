# US-UBUS-001 — Como viajero quiero consultar proximas llegadas por parada para reducir incertidumbre antes del viaje

---

## Metadatos

| Campo                        | Valor |
|-----------------------------|-------|
| **ID**                      | US-UBUS-001 |
| **Versión**                 | 1.0.0 |
| **Estado**                  | en-refinamiento |
| **Estabilidad**             | estable |
| **Fecha**                   | 2026-03-10 |
| **Autor**                   | Oficina de Analisis Funcional |
| **Revisado por**            | pendiente de refinamiento |
| **Aprobado por**            | pendiente de refinamiento |
| **Módulo Funcional**        | Experiencia Digital del Viajero |
| **Submódulo Funcional**     | Informacion Operativa y Ticketing Urbano |
| **Épica asociada**          | EPIC-UBUS-01 — Autoservicio digital para informacion operativa y ticketing basico en autobus urbano |
| **FRS asociado principal**  | FRS-UBUS-001 — Consulta de informacion operativa por parada urbana |
| **Prioridad**               | alta |
| **Tipo de historia**        | funcional |
| **Porcentaje de completud** | 82% |
| **Fuente**                  | docs/requirements/functional/Documento inicial de analisis.txt |
| **Sesión refinamiento**     | REF-ANA-UBUS-001-01 |
| **Enlace RTM**              | traceability/RTM.yaml#LINK-001 |
| **Método verificación**     | test |

---

## Historial de versiones

| Versión | Fecha      | Autor      | Cambios |
|---------|------------|------------|---------|
| 1.0.0   | 2026-03-10 | Oficina de Analisis Funcional | Version inicial derivada del documento ANA-UBUS-001 |

---

## 1. Historia de usuario

**Como** viajero urbano  
**Quiero** consultar proximas llegadas de una parada concreta  
**Para** reducir la incertidumbre antes del viaje y decidir si espero el autobus

---

## 2. Objetivo funcional

Permitir al usuario conocer de forma clara cuando llegara el proximo autobus en una parada concreta.

---

## 3. Contexto

El documento fuente identifica como necesidad frecuente del viajero conocer con claridad cuando llegara el proximo autobus a una parada concreta.

---

## 4. Alcance

### 4.1 Incluido

- Consulta de una parada concreta.
- Visualizacion de proximas llegadas previstas.

### 4.2 Fuera de alcance

- Incidencias detalladas.
- Accesibilidad basica de parada.

### 4.3 Límites

- La informacion debe ser comprensible para un usuario no tecnico.

---

## 5. Actor principal y actores relacionados

### 5.1 Actor principal

| Actor | Descripción |
|-------|-------------|
| Viajero urbano | Persona que usa el autobus con frecuencia y necesita rapidez, simplicidad y fiabilidad |

### 5.2 Actores relacionados

| Actor | Relación con la historia |
|-------|---------------------------|
| Viajero ocasional | Tambien necesita una experiencia clara y guiada |
| Aplicacion movil | Presenta la respuesta al usuario |

---

## 6. Disparador

- El usuario consulta una parada concreta desde la aplicacion movil.

---

## 7. Precondiciones

- Existe una parada valida del servicio urbano.
- Existe informacion operativa sobre proximas llegadas.

---

## 8. Postcondiciones

### 8.1 Éxito

- El usuario ve las proximas llegadas previstas para la parada consultada.
- La informacion se presenta de forma comprensible.

### 8.2 Fallo

- El usuario recibe una comunicacion clara de indisponibilidad o error funcional sin ambiguedad.

---

## 9. Reglas de negocio asociadas

| ID | Regla | Fuente / referencia |
|----|-------|---------------------|
| BR-001 | Debe permitirse consultar una parada concreta | RFN-001 |
| BR-002 | Deben mostrarse las proximas llegadas previstas para la parada consultada | RFN-002 |

---

## 10. Datos de entrada y salida

### 10.1 Entradas

| # | Entrada | Origen | Obligatoria | Validaciones |
|---|---------|--------|-------------|--------------|
| 1 | identificador de parada | Usuario / app | Sí | Debe corresponder a una parada valida |

### 10.2 Salidas

| # | Salida | Destino | Descripción |
|---|--------|---------|-------------|
| 1 | proximas llegadas | Usuario / app | Llegadas previstas de la parada consultada |

---

## 11. Criterios de aceptación

### AC-001 — Consulta valida de proximas llegadas

- **Dado** que existe una parada valida del servicio urbano
- **Cuando** el usuario consulta esa parada
- **Entonces** la solucion debe mostrar las proximas llegadas previstas

### AC-002 — Informacion comprensible para usuario no tecnico

- **Dado** que existen proximas llegadas para una parada consultada
- **Cuando** la solucion presenta la informacion al usuario
- **Entonces** la informacion debe ser comprensible para un usuario no tecnico

### AC-003 — Error o indisponibilidad comunicados sin ambiguedad

- **Dado** que la informacion de llegadas no puede obtenerse de forma valida
- **Cuando** el usuario consulta la parada
- **Entonces** la solucion debe informar el problema sin tecnicismos innecesarios ni datos ambiguos

---

## 12. Escenarios Gherkin asociados

### Feature: Consultar proximas llegadas por parada

```gherkin
Feature: Consultar proximas llegadas por parada
  As a viajero urbano
  I want consultar proximas llegadas de una parada concreta
  So that reducir la incertidumbre antes del viaje y decidir si espero el autobus

  Scenario: Consulta valida de proximas llegadas
    Given existe una parada valida del servicio urbano
    When el usuario consulta esa parada
    Then la solucion muestra las proximas llegadas previstas

  Scenario: Informacion comprensible
    Given existen proximas llegadas para una parada consultada
    When la solucion presenta la informacion al usuario
    Then la informacion es comprensible para un usuario no tecnico

  Scenario: Indisponibilidad comunicada sin ambiguedad
    Given la informacion de llegadas no puede obtenerse de forma valida
    When el usuario consulta la parada
    Then la solucion informa el problema sin tecnicismos innecesarios ni datos ambiguos
```

## 13. Trazabilidad de tests Gherkin

| Test ID | Feature | Escenario | Tipo | AC cubierto | Estado | Observaciones |
|---------|---------|-----------|------|-------------|--------|---------------|
| GT-001  | Consultar proximas llegadas por parada | Consulta valida de proximas llegadas | funcional | AC-001 | pendiente | Cobertura de flujo principal |
| GT-002  | Consultar proximas llegadas por parada | Informacion comprensible | funcional | AC-002 | pendiente | Valida claridad funcional |
| GT-003  | Consultar proximas llegadas por parada | Indisponibilidad comunicada sin ambiguedad | negativo | AC-003 | pendiente | Cubre comunicacion de error |

---

## 14. Trazabilidad de cobertura funcional y riesgo

| Cobertura ID | Tipo | Referencia origen | AC relacionado | Test Gherkin | Riesgo relacionado | Control validado | Estado cobertura | Evidencia |
|--------------|------|-------------------|----------------|--------------|--------------------|------------------|------------------|-----------|
| COV-001 | funcional | FRS-UBUS-001 | AC-001 | GT-001 | — | Consulta de parada y visualizacion de llegadas | pendiente | pendiente de refinamiento |
| COV-002 | funcional | FRS-UBUS-001 | AC-001 | GT-002 | — | Presentacion comprensible para usuario no tecnico | pendiente | pendiente de refinamiento |
| COV-003 | riesgo | FRS-UBUS-001 | AC-003 | GT-003 | USRSK-001 | Comunicacion clara de error o indisponibilidad | pendiente | pendiente de refinamiento |

---

## 15. Requisitos no funcionales asociados

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| RNF-001 | rendimiento | Experiencia suficientemente rapida para uso cotidiano | pendiente de refinamiento |

---

## 16. Dependencias

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Épica | EPIC-UBUS-01 | `pertenece-a` | Epica funcional contenedora |
| FRS | FRS-UBUS-001 | `deriva-de` | Requisito funcional principal |
| Historias | US-UBUS-002 | `relacionada-con` | Historia complementaria sobre incidencias y accesibilidad |
| Servicio ext. | pendiente de refinamiento | `consume` | Origen de informacion operativa no concretado en el documento fuente |

---

## 17. Especificacion OpenAPI derivada

| Artefacto API | Ruta / ID | Tipo | Operacion / evento | Estado | Observaciones |
|---------------|-----------|------|--------------------|--------|---------------|
| OpenAPI spec | spec/open-api/urban-bus-operational-info.openapi.yaml | `openapi` | GET /stops/{stopId}/operational-info | borrador | Operacion derivada para consulta de informacion operativa por parada |
| OpenAPI spec | spec/open-api/urban-bus-operational-info.openapi.yaml#/components/schemas/OperationalInfoResponse | `openapi` | Schema OperationalInfoResponse | borrador | Cubre respuesta visible para esta historia |

---

## 18. Observabilidad funcional

### 18.1 Eventos funcionales

| Evento | Cuándo ocurre | Datos mínimos |
|--------|----------------|---------------|
| STOP_OPERATIONAL_INFO_REQUESTED | Al iniciar la consulta | identificador de parada, timestamp |
| STOP_OPERATIONAL_INFO_RETURNED | Al devolver informacion valida | identificador de parada, total de llegadas |

### 18.2 Alertas

| Alerta | Condición | Acción esperada |
|--------|-----------|-----------------|
| ALERT-ARRIVALS-UNAVAILABLE | Aumento de consultas sin dato de llegada valido | Revisar origen de informacion operativa |

### 18.3 KPIs

| KPI | Definición | Objetivo |
|-----|------------|----------|
| KPI-US-UBUS-001 | Consultas de llegadas resueltas / consultas de llegadas iniciadas | pendiente de refinamiento |

---

## 19. Riesgos y controles

| Riesgo ID | Descripción | Probabilidad | Impacto | Control / mitigación |
|-----------|-------------|--------------|---------|----------------------|
| USRSK-001 | La informacion de llegadas no sea clara o no este disponible cuando el usuario la necesita | media | alta | Mensajes comprensibles y comunicacion no ambigua de indisponibilidad |

---

## 20. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Objetivo de negocio | BGS-UBUS-01 | Mejorar el autoservicio digital del viajero urbano |
| Módulo funcional | Experiencia Digital del Viajero | Dominio funcional principal |
| Submódulo funcional | Informacion Operativa y Ticketing Urbano | Ambito funcional del autoservicio inicial |
| Épica asociada | EPIC-UBUS-01 | Epica de autoservicio digital urbano |
| FRS principal | FRS-UBUS-001 | Consulta de informacion operativa por parada urbana |
| FRS relacionados | — | No aplica |
| Historias relacionadas | US-UBUS-002 | Complementa la informacion operativa |
| Especificaciones OpenAPI derivadas | spec/open-api/urban-bus-operational-info.openapi.yaml | OpenAPI derivada para consulta operativa |
| Criterios de aceptación | AC-001, AC-002, AC-003 | Criterios definidos en §11 |
| Tests Gherkin | GT-001, GT-002, GT-003 | Escenarios definidos en §13 |
| Cobertura funcional y riesgo | COV-001, COV-002, COV-003 | Cobertura definida en §14 |
| Riesgos relacionados | USRSK-001 | Riesgo asociado |
| ADR relacionado | pendiente de refinamiento | No identificado en esta fase |
| Enlace RTM | LINK-001 | Entrada en `traceability/RTM.yaml` |

---

## 21. Notas y decisiones abiertas

| # | Nota / pregunta | Responsable | Estado | Fecha objetivo | Decisión tomada | Evidencia |
|---|------------------|-------------|--------|----------------|-----------------|----------|
| 1 | Confirmar el nivel minimo de detalle visible para llegadas desde la primera version | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Documento inicial de analisis.txt §7.1 |

---

*Plantilla: `user-story.template.md` v1.2.0*
