# US-UBUS-003 — Como viajero quiero comprar un billete sencillo digital para acceder al servicio sin depender de un canal presencial

---

## Metadatos

| Campo                        | Valor |
|-----------------------------|-------|
| **ID**                      | US-UBUS-003 |
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
| **Porcentaje de completud** | 70% |
| **Fuente**                  | docs/requirements/functional/Documento inicial de analisis.txt |
| **Sesión refinamiento**     | REF-ANA-UBUS-001-01 |
| **Enlace RTM**              | traceability/RTM.yaml#LINK-003 |
| **Método verificación**     | test |

---

## Historial de versiones

| Versión | Fecha      | Autor      | Cambios |
|---------|------------|------------|---------|
| 1.0.0   | 2026-03-10 | Oficina de Analisis Funcional | Version inicial derivada del documento ANA-UBUS-001 |

---

## 1. Historia de usuario

**Como** viajero urbano o viajero ocasional  
**Quiero** comprar un billete sencillo digital desde la aplicacion movil  
**Para** acceder al servicio con una experiencia simple y sin depender de interacciones presenciales

---

## 2. Objetivo funcional

Permitir la compra de un billete sencillo digital y ofrecer una confirmacion clara del resultado al usuario.

---

## 3. Contexto

El documento fuente identifica la necesidad de disponer de un mecanismo simple para comprar un billete digital desde el movil.

---

## 4. Alcance

### 4.1 Incluido

- Inicio y resolucion de compra de billete sencillo digital.
- Confirmacion clara del resultado de la compra.

### 4.2 Fuera de alcance

- Abonos complejos.
- Fidelizacion.

### 4.3 Límites

- La definicion detallada de medios de pago queda pendiente de refinamiento.

---

## 5. Actor principal y actores relacionados

### 5.1 Actor principal

| Actor | Descripción |
|-------|-------------|
| Viajero ocasional | Persona que usa el servicio de forma puntual y necesita una experiencia especialmente clara y guiada |

### 5.2 Actores relacionados

| Actor | Relación con la historia |
|-------|---------------------------|
| Viajero urbano habitual | Tambien compra billete sencillo cuando aplica |
| Aplicacion movil | Presenta el proceso de compra y la confirmacion |

---

## 6. Disparador

- El usuario decide comprar un billete sencillo digital desde la aplicacion movil.

---

## 7. Precondiciones

- El billete sencillo digital forma parte del alcance inicial del producto.
- El canal movil esta disponible.

---

## 8. Postcondiciones

### 8.1 Éxito

- La compra queda confirmada de forma clara al usuario.
- El billete adquirido queda disponible para uso posterior.

### 8.2 Fallo

- El usuario entiende que no dispone de un billete valido si la compra no se completa.

---

## 9. Reglas de negocio asociadas

| ID | Regla | Fuente / referencia |
|----|-------|---------------------|
| BR-001 | Debe permitirse la compra de un billete sencillo digital desde la aplicacion movil | RFN-008 |
| BR-002 | Debe mostrarse una confirmacion clara del resultado de la compra | RFN-009 |

---

## 10. Datos de entrada y salida

### 10.1 Entradas

| # | Entrada | Origen | Obligatoria | Validaciones |
|---|---------|--------|-------------|--------------|
| 1 | solicitud de compra de billete sencillo | Usuario / app | Sí | Debe corresponder al producto disponible en esta fase |

### 10.2 Salidas

| # | Salida | Destino | Descripción |
|---|--------|---------|-------------|
| 1 | confirmacion de compra | Usuario / app | Resultado claro de la compra |
| 2 | evidencia del billete adquirido | Usuario / app | Prueba funcional del billete comprado |

---

## 11. Criterios de aceptación

### AC-001 — Compra de billete sencillo digital

- **Dado** que el usuario inicia la compra de un billete sencillo digital
- **Cuando** la solucion procesa la solicitud
- **Entonces** la solucion debe permitir completar la compra desde la aplicacion movil

### AC-002 — Confirmacion clara del resultado

- **Dado** que la compra ha sido procesada
- **Cuando** se informa el resultado al usuario
- **Entonces** la solucion debe mostrar una confirmacion clara del resultado de la compra

### AC-003 — No inducir a error sobre la validez del billete

- **Dado** que la compra no se ha completado correctamente o el billete no cumple aun condiciones de uso
- **Cuando** el usuario revisa el resultado
- **Entonces** la solucion no debe inducir a interpretar que ya dispone de un billete valido

---

## 12. Escenarios Gherkin asociados

### Feature: Comprar billete sencillo digital

```gherkin
Feature: Comprar billete sencillo digital
  As a viajero urbano o viajero ocasional
  I want comprar un billete sencillo digital desde la aplicacion movil
  So that acceder al servicio con una experiencia simple y sin depender de interacciones presenciales

  Scenario: Compra de billete sencillo digital
    Given el usuario inicia la compra de un billete sencillo digital
    When la solucion procesa la solicitud
    Then la solucion permite completar la compra desde la aplicacion movil

  Scenario: Confirmacion clara del resultado
    Given la compra ha sido procesada
    When se informa el resultado al usuario
    Then la solucion muestra una confirmacion clara del resultado de la compra

  Scenario: No inducir a error sobre la validez del billete
    Given la compra no se ha completado correctamente o el billete no cumple aun condiciones de uso
    When el usuario revisa el resultado
    Then la solucion no induce a interpretar que ya dispone de un billete valido
```

## 13. Trazabilidad de tests Gherkin

| Test ID | Feature | Escenario | Tipo | AC cubierto | Estado | Observaciones |
|---------|---------|-----------|------|-------------|--------|---------------|
| GT-001  | Comprar billete sencillo digital | Compra de billete sencillo digital | funcional | AC-001 | pendiente | Flujo principal de compra |
| GT-002  | Comprar billete sencillo digital | Confirmacion clara del resultado | funcional | AC-002 | pendiente | Cubre comunicacion del resultado |
| GT-003  | Comprar billete sencillo digital | No inducir a error sobre la validez del billete | negativo | AC-003 | pendiente | Cubre prevencion de interpretacion incorrecta |

---

## 14. Trazabilidad de cobertura funcional y riesgo

| Cobertura ID | Tipo | Referencia origen | AC relacionado | Test Gherkin | Riesgo relacionado | Control validado | Estado cobertura | Evidencia |
|--------------|------|-------------------|----------------|--------------|--------------------|------------------|------------------|-----------|
| COV-001 | funcional | FRS-UBUS-002 | AC-001 | GT-001 | — | Compra de billete sencillo desde movil | pendiente | pendiente de refinamiento |
| COV-002 | funcional | FRS-UBUS-002 | AC-002 | GT-002 | — | Confirmacion clara del resultado de compra | pendiente | pendiente de refinamiento |
| COV-003 | riesgo | FRS-UBUS-002 | AC-001 | GT-003 | USRSK-001 | Mensajeria que evita interpretar validez incorrecta | pendiente | pendiente de refinamiento |

---

## 15. Requisitos no funcionales asociados

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| RNF-003 | usabilidad | La experiencia debe ser sencilla para usuarios con distinto nivel de familiaridad digital | Validacion funcional por negocio |

---

## 16. Dependencias

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Épica | EPIC-UBUS-01 | `pertenece-a` | Epica funcional contenedora |
| FRS | FRS-UBUS-002 | `deriva-de` | Requisito funcional principal |
| Historias | US-UBUS-004 | `relacionada-con` | Continua con estado y activacion del billete |
| Servicio ext. | pendiente de refinamiento | `consume` | Plataforma de ticketing y pago no concretada en el documento fuente |

---

## 17. Especificacion OpenAPI derivada

| Artefacto API | Ruta / ID | Tipo | Operacion / evento | Estado | Observaciones |
|---------------|-----------|------|--------------------|--------|---------------|
| OpenAPI spec | spec/open-api/urban-bus-digital-ticket.openapi.yaml | `openapi` | POST /digital-tickets/simple/purchase | borrador | Operacion derivada de compra de billete sencillo |
| OpenAPI spec | spec/open-api/urban-bus-digital-ticket.openapi.yaml#/components/schemas/PurchaseResult | `openapi` | Schema PurchaseResult | borrador | Detalle de pago pendiente de refinamiento |

---

## 18. Observabilidad funcional

### 18.1 Eventos funcionales

| Evento | Cuándo ocurre | Datos mínimos |
|--------|----------------|---------------|
| DIGITAL_TICKET_PURCHASE_REQUESTED | Al iniciar compra | timestamp |
| DIGITAL_TICKET_PURCHASE_RESULT | Al resolver compra | resultado, timestamp |

### 18.2 Alertas

| Alerta | Condición | Acción esperada |
|--------|-----------|-----------------|
| ALERT-TICKET-PURCHASE-FAILED | Incremento de compras no completadas | Revision funcional del flujo y mensajes |

### 18.3 KPIs

| KPI | Definición | Objetivo |
|-----|------------|----------|
| KPI-US-UBUS-003 | Compras completadas / intentos de compra | pendiente de refinamiento |

---

## 19. Riesgos y controles

| Riesgo ID | Descripción | Probabilidad | Impacto | Control / mitigación |
|-----------|-------------|--------------|---------|----------------------|
| USRSK-001 | El usuario interprete que dispone de un billete valido cuando la compra no se completo o aun faltan condiciones de uso | media | alta | Confirmacion clara del resultado y mensajes que no induzcan a error |

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
| Historias relacionadas | US-UBUS-004 | Historia complementaria |
| Especificaciones OpenAPI derivadas | spec/open-api/urban-bus-digital-ticket.openapi.yaml | OpenAPI derivada para ticketing digital |
| Criterios de aceptación | AC-001, AC-002, AC-003 | Criterios definidos en §11 |
| Tests Gherkin | GT-001, GT-002, GT-003 | Escenarios definidos en §13 |
| Cobertura funcional y riesgo | COV-001, COV-002, COV-003 | Cobertura definida en §14 |
| Riesgos relacionados | USRSK-001 | Riesgo asociado |
| ADR relacionado | pendiente de refinamiento | No identificado en esta fase |
| Enlace RTM | LINK-003 | Entrada en `traceability/RTM.yaml` |

---

## 21. Notas y decisiones abiertas

| # | Nota / pregunta | Responsable | Estado | Fecha objetivo | Decisión tomada | Evidencia |
|---|------------------|-------------|--------|----------------|-----------------|----------|
| 1 | Definir el detalle minimo de evidencia visible del billete adquirido tras la compra | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Documento inicial de analisis.txt §12 |

---

*Plantilla: `user-story.template.md` v1.2.0*
