# US-UBUS-004 — Como viajero quiero consultar el estado de mi billete y activarlo cuando proceda para usarlo correctamente

---

## Metadatos

| Campo                        | Valor |
|-----------------------------|-------|
| **ID**                      | US-UBUS-004 |
| **Versión**                 | 1.0.0 |
| **Estado**                  | en-refinamiento |
| **Estabilidad**             | en-cambio |
| **Fecha**                   | 2026-03-10 |
| **Autor**                   | Oficina de Analisis Funcional |
| **Revisado por**            | pendiente de refinamiento |
| **Aprobado por**            | pendiente de refinamiento |
| **Módulo Funcional**        | Experiencia Digital del Viajero |
| **Submódulo Funcional**     | Informacion Operativa y Ticketing Urbano |
| **Épica asociada**          | EPIC-UBUS-01 — Autoservicio digital para informacion operativa y ticketing basico en autobus urbano |
| **FRS asociado principal**  | FRS-UBUS-002 — Compra, consulta y activacion de billete digital sencillo |
| **Prioridad**               | crítica |
| **Tipo de historia**        | funcional |
| **Porcentaje de completud** | 68% |
| **Fuente**                  | docs/requirements/functional/Documento inicial de analisis.txt |
| **Sesión refinamiento**     | REF-ANA-UBUS-001-01 |
| **Enlace RTM**              | traceability/RTM.yaml#LINK-004 |
| **Método verificación**     | test |

---

## Historial de versiones

| Versión | Fecha      | Autor      | Cambios |
|---------|------------|------------|---------|
| 1.0.0   | 2026-03-10 | Oficina de Analisis Funcional | Version inicial derivada del documento ANA-UBUS-001 |

---

## 1. Historia de usuario

**Como** viajero urbano  
**Quiero** consultar el estado funcional de mi billete y activarlo antes de subir cuando proceda  
**Para** saber si puedo usarlo correctamente al acceder al autobus

---

## 2. Objetivo funcional

Permitir al usuario ver el estado funcional del billete adquirido y ejecutar o entender la activacion segun el modelo operativo del cliente.

---

## 3. Contexto

El documento fuente identifica incertidumbre sobre el estado del billete y sobre el momento correcto para utilizarlo o activarlo.

---

## 4. Alcance

### 4.1 Incluido

- Consulta posterior del billete adquirido.
- Visualizacion del estado funcional del billete.

### 4.2 Fuera de alcance

- Reglas operativas definitivas de validacion a bordo.
- Automatismos de activacion no confirmados por el cliente.

### 4.3 Límites

- La obligatoriedad o automatizacion de activacion sigue pendiente de refinamiento.

---

## 5. Actor principal y actores relacionados

### 5.1 Actor principal

| Actor | Descripción |
|-------|-------------|
| Viajero urbano | Necesita entender si el billete esta listo para uso y cuando activarlo |

### 5.2 Actores relacionados

| Actor | Relación con la historia |
|-------|---------------------------|
| Personal de soporte o atencion | Puede ayudar al usuario a interpretar el estado funcional |
| Aplicacion movil | Presenta estado y activacion del billete |

---

## 6. Disparador

- El usuario consulta un billete adquirido o intenta activarlo antes de subir al autobus.

---

## 7. Precondiciones

- Existe un billete sencillo digital adquirido.
- El modelo operativo del cliente puede requerir activacion previa.

---

## 8. Postcondiciones

### 8.1 Éxito

- El usuario entiende el estado funcional del billete.
- El usuario puede activar el billete cuando proceda.

### 8.2 Fallo

- El usuario recibe una explicacion clara cuando el billete no puede activarse.

---

## 9. Reglas de negocio asociadas

| ID | Regla | Fuente / referencia |
|----|-------|---------------------|
| BR-001 | El billete adquirido debe quedar disponible para consulta posterior | RFN-010 |
| BR-002 | El estado funcional del billete debe mostrarse de manera comprensible | RFN-011 |
| BR-003 | Debe permitirse la activacion del billete antes del uso cuando el modelo lo requiera | RFN-012 |
| BR-004 | Debe informarse claramente cuando un billete no pueda activarse | RFN-013 |
| BR-005 | Debe evitarse que el usuario interprete incorrectamente que dispone de un billete valido cuando todavia no cumple condiciones de uso | RFN-014 |

---

## 10. Datos de entrada y salida

### 10.1 Entradas

| # | Entrada | Origen | Obligatoria | Validaciones |
|---|---------|--------|-------------|--------------|
| 1 | identificador de billete | Usuario / app | Sí | Debe corresponder a un billete adquirido |
| 2 | solicitud de activacion | Usuario / app | No | Solo aplica cuando el usuario intenta activar |

### 10.2 Salidas

| # | Salida | Destino | Descripción |
|---|--------|---------|-------------|
| 1 | estado funcional del billete | Usuario / app | Estado comprensible del billete |
| 2 | resultado de activacion | Usuario / app | Confirmacion clara o rechazo informado |

---

## 11. Criterios de aceptación

### AC-001 — Mostrar estado funcional comprensible

- **Dado** que existe un billete digital adquirido
- **Cuando** el usuario consulta ese billete
- **Entonces** la solucion debe mostrar su estado funcional de manera comprensible

### AC-002 — Activar billete cuando proceda

- **Dado** que el modelo operativo requiere activacion previa y el billete cumple las condiciones necesarias
- **Cuando** el usuario solicita la activacion
- **Entonces** la solucion debe permitir activar el billete antes del uso

### AC-003 — Informar claramente cuando no pueda activarse

- **Dado** que el usuario intenta activar un billete que no puede activarse
- **Cuando** la solucion procesa la solicitud
- **Entonces** la solucion debe informar claramente que el billete no puede activarse

---

## 12. Escenarios Gherkin asociados

### Feature: Consultar y activar billete digital

```gherkin
Feature: Consultar y activar billete digital
  As a viajero urbano
  I want consultar el estado funcional de mi billete y activarlo antes de subir cuando proceda
  So that saber si puedo usarlo correctamente al acceder al autobus

  Scenario: Mostrar estado funcional comprensible
    Given existe un billete digital adquirido
    When el usuario consulta ese billete
    Then la solucion muestra su estado funcional de manera comprensible

  Scenario: Activar billete cuando proceda
    Given el modelo operativo requiere activacion previa y el billete cumple las condiciones necesarias
    When el usuario solicita la activacion
    Then la solucion permite activar el billete antes del uso

  Scenario: Informar claramente cuando no pueda activarse
    Given el usuario intenta activar un billete que no puede activarse
    When la solucion procesa la solicitud
    Then la solucion informa claramente que el billete no puede activarse
```

## 13. Trazabilidad de tests Gherkin

| Test ID | Feature | Escenario | Tipo | AC cubierto | Estado | Observaciones |
|---------|---------|-----------|------|-------------|--------|---------------|
| GT-001  | Consultar y activar billete digital | Mostrar estado funcional comprensible | funcional | AC-001 | pendiente | Cubre visibilidad del estado |
| GT-002  | Consultar y activar billete digital | Activar billete cuando proceda | funcional | AC-002 | pendiente | Depende de regla operativa final |
| GT-003  | Consultar y activar billete digital | Informar claramente cuando no pueda activarse | negativo | AC-003 | pendiente | Cubre rechazo controlado de activacion |

---

## 14. Trazabilidad de cobertura funcional y riesgo

| Cobertura ID | Tipo | Referencia origen | AC relacionado | Test Gherkin | Riesgo relacionado | Control validado | Estado cobertura | Evidencia |
|--------------|------|-------------------|----------------|--------------|--------------------|------------------|------------------|-----------|
| COV-001 | funcional | FRS-UBUS-002 | AC-003 | GT-001 | — | Visualizacion comprensible del estado del billete | pendiente | pendiente de refinamiento |
| COV-002 | riesgo | FRS-UBUS-002 | AC-004 | GT-002 | USRSK-001 | Activacion solo cuando proceda segun reglas funcionales | pendiente | pendiente de refinamiento |
| COV-003 | riesgo | FRS-UBUS-002 | AC-004 | GT-003 | USRSK-002 | Mensaje claro cuando la activacion no puede realizarse | pendiente | pendiente de refinamiento |

---

## 15. Requisitos no funcionales asociados

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| RNF-003 | usabilidad | La interfaz debe ser sencilla y apta para usuarios con distinto nivel de familiaridad digital | Validacion funcional por negocio |

---

## 16. Dependencias

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Épica | EPIC-UBUS-01 | `pertenece-a` | Epica funcional contenedora |
| FRS | FRS-UBUS-002 | `deriva-de` | Requisito funcional principal |
| Historias | US-UBUS-003 | `relacionada-con` | Historia previa de compra del billete |
| Servicio ext. | pendiente de refinamiento | `consume` | Plataforma de ticketing no concretada en el documento fuente |

---

## 17. Especificacion OpenAPI derivada

| Artefacto API | Ruta / ID | Tipo | Operacion / evento | Estado | Observaciones |
|---------------|-----------|------|--------------------|--------|---------------|
| OpenAPI spec | spec/open-api/urban-bus-digital-ticket.openapi.yaml | `openapi` | GET /digital-tickets/{ticketId} | borrador | Operacion derivada para consulta del billete |
| OpenAPI spec | spec/open-api/urban-bus-digital-ticket.openapi.yaml | `openapi` | POST /digital-tickets/{ticketId}/activation | borrador | Regla exacta de activacion pendiente de refinamiento |

---

## 18. Observabilidad funcional

### 18.1 Eventos funcionales

| Evento | Cuándo ocurre | Datos mínimos |
|--------|----------------|---------------|
| DIGITAL_TICKET_STATUS_VIEWED | Al consultar estado del billete | identificador de billete, estado |
| DIGITAL_TICKET_ACTIVATION_RESULT | Al resolver activacion | identificador de billete, resultado |

### 18.2 Alertas

| Alerta | Condición | Acción esperada |
|--------|-----------|-----------------|
| ALERT-TICKET-ACTIVATION-CONFUSION | Incremento de intentos fallidos o consultas sobre activacion | Refinar regla funcional y mensajes |

### 18.3 KPIs

| KPI | Definición | Objetivo |
|-----|------------|----------|
| KPI-US-UBUS-004 | Activaciones correctas / intentos de activacion aplicables | pendiente de refinamiento |

---

## 19. Riesgos y controles

| Riesgo ID | Descripción | Probabilidad | Impacto | Control / mitigación |
|-----------|-------------|--------------|---------|----------------------|
| USRSK-001 | El usuario no entiende correctamente el estado de su billete digital | media | alta | Mostrar estado funcional comprensible |
| USRSK-002 | Existen dudas sobre el momento correcto de activacion del billete | media | alta | Informar claramente cuando puede y cuando no puede activarse |

---

## 20. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Objetivo de negocio | BGS-UBUS-01 | Mejorar el autoservicio digital del viajero urbano |
| Módulo funcional | Experiencia Digital del Viajero | Dominio funcional principal |
| Submódulo funcional | Informacion Operativa y Ticketing Urbano | Ambito funcional del autoservicio inicial |
| Épica asociada | EPIC-UBUS-01 | Epica de autoservicio digital urbano |
| FRS principal | FRS-UBUS-002 | Compra, consulta y activacion de billete digital sencillo |
| FRS relacionados | — | No aplica |
| Historias relacionadas | US-UBUS-003 | Historia complementaria |
| Especificaciones OpenAPI derivadas | spec/open-api/urban-bus-digital-ticket.openapi.yaml | OpenAPI derivada para ticketing digital |
| Criterios de aceptación | AC-001, AC-002, AC-003 | Criterios definidos en §11 |
| Tests Gherkin | GT-001, GT-002, GT-003 | Escenarios definidos en §13 |
| Cobertura funcional y riesgo | COV-001, COV-002, COV-003 | Cobertura definida en §14 |
| Riesgos relacionados | USRSK-001, USRSK-002 | Riesgos asociados |
| ADR relacionado | pendiente de refinamiento | No identificado en esta fase |
| Enlace RTM | LINK-004 | Entrada en `traceability/RTM.yaml` |

---

## 21. Notas y decisiones abiertas

| # | Nota / pregunta | Responsable | Estado | Fecha objetivo | Decisión tomada | Evidencia |
|---|------------------|-------------|--------|----------------|-----------------|----------|
| 1 | Confirmar si la activacion del billete debe ser obligatoria o automatica en algun escenario | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Documento inicial de analisis.txt §12 |
| 2 | Definir cuanto tiempo puede transcurrir entre compra y activacion sin afectar a la validez del titulo | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Documento inicial de analisis.txt §12 |

---

*Plantilla: `user-story.template.md` v1.2.0*
