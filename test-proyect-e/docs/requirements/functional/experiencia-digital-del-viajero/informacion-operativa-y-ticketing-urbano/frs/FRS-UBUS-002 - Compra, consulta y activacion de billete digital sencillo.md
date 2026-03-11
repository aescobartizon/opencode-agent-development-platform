# FRS-UBUS-002 — Compra, consulta y activacion de billete digital sencillo

---

## Metadatos

| Campo                        | Valor |
|-----------------------------|-------|
| **ID**                      | FRS-UBUS-002 |
| **Versión**                 | 1.0.0 |
| **Estado**                  | en-revisión |
| **Estabilidad**             | en-cambio |
| **Fecha**                   | 2026-03-10 |
| **Autor**                   | Oficina de Analisis Funcional |
| **Revisado por**            | pendiente de refinamiento |
| **Aprobado por**            | pendiente de refinamiento |
| **Módulo Funcional**        | Experiencia Digital del Viajero |
| **Submódulo Funcional**     | Informacion Operativa y Ticketing Urbano |
| **Épica**                   | EPIC-UBUS-01 — Autoservicio digital para informacion operativa y ticketing basico en autobus urbano |
| **Prioridad**               | crítica |
| **Porcentaje de completud** | 74% |
| **Fuente**                  | docs/requirements/functional/Documento inicial de analisis.txt |
| **Sesión refinamiento**     | REF-ANA-UBUS-001-01 |
| **Enlace RTM**              | traceability/RTM.yaml#LINK-003, traceability/RTM.yaml#LINK-004 |
| **Método verificación**     | test |

---

## Historial de versiones

| Versión | Fecha      | Autor      | Cambios |
|---------|------------|------------|---------|
| 1.0.0   | 2026-03-10 | Oficina de Analisis Funcional | Version inicial derivada del documento ANA-UBUS-001 |

---

## 1. Descripción

El sistema debe permitir al usuario comprar un billete sencillo digital desde la aplicacion movil, recibir una confirmacion clara del resultado, disponer del billete adquirido para su consulta posterior y entender su estado funcional. Cuando el modelo operativo del cliente lo requiera, el sistema debe permitir la activacion del billete antes del embarque y comunicar claramente cuando no pueda activarse.

---

## 2. Alcance y límites

### 2.1 Alcance incluido

- Compra de billete sencillo digital desde canal movil.
- Confirmacion clara del resultado de la compra.
- Disponibilidad del billete adquirido para consulta posterior.
- Visualizacion comprensible del estado funcional del billete.
- Activacion del billete antes del uso cuando proceda.
- Mensaje claro cuando un billete no pueda activarse.

### 2.2 Fuera de alcance

- Gestion completa de abonos complejos.
- Fidelizacion.
- Validacion fisica o embarcada detallada.
- Reglas tarifarias avanzadas no descritas en el documento fuente.

### 2.3 Límites del requisito

- La primera fase se centra en billete sencillo digital.
- La regla exacta entre compra y activacion permanece abierta.

---

## 3. Evento disparador

- **Tipo de disparador:** `usuario`
- **Disparador principal:** El usuario compra un billete sencillo digital o consulta y activa un billete adquirido desde la app movil.
- **Canal / origen:** Aplicacion movil del servicio urbano.
- **Frecuencia esperada:** Alta en escenarios de uso cotidiano del servicio.

---

## 4. Actores y stakeholders

### 4.1 Actores del sistema

| Actor | Tipo | Rol en este requisito |
|-------|------|-----------------------|
| Viajero urbano | `primario` | Compra, consulta y activa el billete digital |
| Viajero ocasional | `primario` | Requiere una experiencia clara y guiada de compra y uso |
| Aplicacion movil | `secundario` | Presenta el proceso de compra y estado del billete |
| Plataforma de ticketing y pago | `sistema-externo` | Registra compra y gestiona disponibilidad/activacion del billete |

### 4.2 Stakeholders interesados

| Stakeholder | Interés / Impacto |
|-------------|-------------------|
| Operador o autoridad de transporte urbano | Reducir friccion en acceso al servicio |
| Personal de soporte o atencion | Reducir dudas sobre estado y uso del billete |

---

## 5. Entradas y salidas del sistema

### 5.1 Entradas

| # | Nombre | Tipo / Formato | Origen | Obligatorio | Validaciones |
|---|--------|----------------|--------|-------------|--------------|
| 1 | solicitud de compra de billete sencillo | solicitud funcional | Usuario / app | Sí | Debe corresponder al producto de ticketing inicial definido por el cliente |
| 2 | identificador de billete | identificador | Usuario / app | Sí para consulta y activacion | Debe corresponder a un billete adquirido por el usuario |

### 5.2 Salidas

| # | Nombre | Tipo / Formato | Destino | Descripción |
|---|--------|----------------|---------|-------------|
| 1 | confirmacion de compra | mensaje / evidencia digital | Usuario / app | Resultado claro de la compra |
| 2 | billete disponible | evidencia digital | Usuario / app | Billete adquirido disponible para consulta posterior |
| 3 | estado funcional del billete | texto / etiqueta funcional | Usuario / app | Estado comprensible del billete |
| 4 | resultado de activacion | mensaje funcional | Usuario / app | Confirma activacion o imposibilidad de activacion |

---

## 6. Calidad y sensibilidad del dato

### 6.1 Clasificación de datos

| Dato / conjunto | Sensibilidad | Origen | Retención | Observaciones |
|-----------------|--------------|--------|-----------|---------------|
| Billete digital adquirido | `confidencial` | Plataforma de ticketing | pendiente de refinamiento | Debe respetar obligaciones regulatorias y organizativas aplicables |
| Estado funcional del billete | `confidencial` | Plataforma de ticketing | pendiente de refinamiento | Debe ser comprensible y no inducir a error |
| Evidencia de compra | `confidencial` | Plataforma de ticketing / pago | pendiente de refinamiento | Debe ser clara para el usuario |

### 6.2 Reglas de calidad de datos

| ID | Dimensión | Regla / umbral |
|----|-----------|----------------|
| DQ-001 | completitud | La confirmacion de compra debe indicar de forma clara si la compra se completo o no |
| DQ-002 | validez | El billete consultado o activado debe corresponder a un billete adquirido |
| DQ-003 | unicidad | El usuario no debe interpretar que dispone de varios billetes validos por una misma compra no confirmada |
| DQ-004 | consistencia | El estado funcional mostrado debe corresponder al estado real de uso del billete |

### 6.3 Consideraciones funcionales sobre datos

- La experiencia debe evitar que el usuario interprete incorrectamente que ya dispone de un billete valido cuando aun no cumple las condiciones de uso.
- Los detalles exactos de pago y validez temporal permanecen pendientes de refinamiento.

---

## 7. Precondiciones

- El canal movil esta disponible para el usuario.
- El cliente acepta iniciar con billete sencillo digital como producto de ticketing base.

---

## 8. Postcondiciones

- El usuario dispone de evidencia clara del resultado de la compra o del motivo del fallo.
- El sistema deja disponible el billete para consulta posterior cuando la compra es correcta.
- El usuario entiende si el billete esta listo para uso o requiere activacion.

---

## 9. Supuestos

- El billete sencillo digital es el producto mas adecuado para iniciar la experiencia digital.
- El modelo operativo del cliente puede requerir activacion previa al embarque.

---

## 10. Restricciones

| Tipo | Restricción | Impacto / Justificación |
|------|-------------|-------------------------|
| `normativa` | La gestion de datos del usuario y del billete debe respetar obligaciones regulatorias y organizativas aplicables | Condiciona el tratamiento funcional del billete |
| `organizativa` | La experiencia del billete digital debe ser simple y entendible desde el primer uso | Limita complejidad funcional inicial |
| `proceso` | La solucion debe ser coherente con la operacion real del servicio urbano | Evita estados funcionales irreales |
| `temporal` | La primera fase debe centrarse en capacidades de alto valor y baja ambiguedad | Prioriza compra y uso basico |

---

## 11. Frecuencia, volumetría y criticidad operativa

| Aspecto | Valor |
|---------|-------|
| **Frecuencia esperada** | Alta |
| **Volumen estimado** | pendiente de refinamiento |
| **Picos esperados** | En franjas de uso intensivo del transporte urbano |
| **Ventana operativa** | Durante el servicio urbano y periodos de mayor uso |
| **Criticidad de negocio** | `alta` |
| **Impacto por indisponibilidad** | Mayor friccion de acceso al servicio y aumento de dependencia de canales presenciales |

---

## 12. Flujo principal

1. El usuario inicia la compra de un billete sencillo digital desde la app.
2. El sistema procesa la solicitud y comunica de forma clara el resultado de la compra.
3. Si la compra es correcta, el billete queda disponible para consulta posterior.
4. El sistema muestra el estado funcional del billete de forma comprensible.
5. Cuando proceda, el usuario activa el billete antes de subir al autobus.
6. El sistema comunica el resultado de la activacion o la imposibilidad de activarlo.

---

## 13. Flujos alternativos

### 13.1 Billete adquirido pero pendiente de activacion

- **Condición de activación:** El modelo del cliente requiere activacion previa y la compra fue correcta.
- **Pasos:**
  1. El billete queda disponible para consulta posterior.
  2. La app muestra que el billete aun no esta listo para uso hasta su activacion.

### 13.2 Activacion no permitida

- **Condición de activación:** El billete no puede activarse por reglas funcionales aun no satisfechas.
- **Pasos:**
  1. El sistema rechaza la activacion.
  2. La app informa claramente que el billete no puede activarse.

---

## 14. Flujos de excepción

### 14.1 Compra no completada

- **Condición de activación:** La compra de billete sencillo no se completa correctamente.
- **Respuesta del sistema:** El usuario recibe una confirmacion clara de fallo y no interpreta que dispone de un billete valido.
- **Código de error (si aplica):** pendiente de refinamiento

---

## 15. Reglas de negocio

| ID | Regla | Fuente / Referencia |
|----|-------|---------------------|
| BR-001 | La solucion debe permitir la compra de un billete sencillo digital desde la aplicacion movil | RFN-008 |
| BR-002 | La solucion debe mostrar una confirmacion clara del resultado de la compra | RFN-009 |
| BR-003 | La solucion debe poner el billete adquirido a disposicion del usuario para su consulta posterior | RFN-010 |
| BR-004 | La solucion debe mostrar el estado funcional del billete de manera comprensible | RFN-011 |
| BR-005 | Debe permitir la activacion del billete cuando el modelo del cliente lo requiera e informar claramente cuando no pueda activarse | RFN-012, RFN-013, RFN-014 |

---

## 16. Requisitos no funcionales asociados

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| RNF-001 | rendimiento | La experiencia de compra y consulta debe ser suficientemente rapida para uso cotidiano | pendiente de refinamiento |
| RNF-003 | usabilidad | La interfaz debe ser sencilla para usuarios con distinto nivel de familiaridad digital | Validacion funcional por negocio |
| RNF-006 | seguridad | La gestion del dato de usuario y del billete debe respetar obligaciones aplicables | pendiente de refinamiento |

---

## 17. Criterios de aceptación

### AC-001 — Confirmacion clara de compra

- **Dado** que el usuario solicita la compra de un billete sencillo digital
- **Cuando** la compra se procesa
- **Entonces** la solucion debe mostrar una confirmacion clara del resultado de la compra

### AC-002 — Billete disponible para consulta posterior

- **Dado** que la compra del billete se completa correctamente
- **Cuando** el usuario consulta sus billetes
- **Entonces** el billete adquirido debe estar disponible con una evidencia clara

### AC-003 — Estado funcional comprensible

- **Dado** que existe un billete digital adquirido
- **Cuando** el usuario consulta ese billete
- **Entonces** la solucion debe mostrar el estado funcional del billete de manera comprensible

### AC-004 — Activacion controlada del billete

- **Dado** que el modelo operativo requiere activacion previa o el usuario intenta activar el billete
- **Cuando** el usuario solicita la activacion
- **Entonces** la solucion debe activar el billete cuando proceda o informar claramente si no puede activarse

---

## 18. Tests de alto nivel

| ID | Tipo | Título | AC vinculado | US derivada objetivo | Riesgo cubierto | Precondición del test | Datos de entrada | Resultado esperado | Resultado ejecución | Prioridad |
|----|------|--------|--------------|----------------------|-----------------|------------------------|------------------|-------------------|---------------------|-----------|
| TC-UBUS-TKT-001 | funcional | Compra correcta de billete sencillo digital | AC-001 | US-UBUS-003 | — | Usuario inicia compra valida | solicitud de compra | Se muestra confirmacion clara de compra | pendiente | crítica |
| TC-UBUS-TKT-002 | funcional | Consulta posterior de billete adquirido | AC-002 | US-UBUS-004 | RSK-001 | Existe compra correcta previa | identificador de billete | El billete queda disponible para consulta | pendiente | alta |
| TC-UBUS-TKT-003 | funcional | Visualizacion comprensible del estado del billete | AC-003 | US-UBUS-004 | RSK-001 | Existe billete adquirido | identificador de billete | El estado se muestra de forma comprensible | pendiente | alta |
| TC-UBUS-TKT-004 | negativo | Activacion no permitida informada claramente | AC-004 | US-UBUS-004 | RSK-002 | Existe escenario donde la activacion no procede | identificador de billete | El sistema informa claramente que no puede activarse | pendiente | crítica |

### Notas de testing

- **Entorno requerido:** pendiente de refinamiento
- **Datos de prueba:** Solicitudes de compra correctas e incorrectas, billetes adquiridos y no activables
- **Dependencias externas:** Plataforma de ticketing y medio de confirmacion de compra
- **Responsable de ejecución:** pendiente de refinamiento

---

## 19. Riesgos y controles asociados

| Riesgo ID | Descripción del riesgo | Probabilidad | Impacto | Control / mitigación | Evidencia esperada |
|-----------|------------------------|--------------|---------|----------------------|--------------------|
| RSK-001 | El usuario no entiende correctamente el estado de su billete digital | media | alta | Mensajes funcionales claros sobre compra, disponibilidad y estado del billete | Evidencia funcional en AC-002 y AC-003 |
| RSK-002 | Existen dudas sobre el momento correcto de activacion del billete | media | alta | Informar claramente cuando la activacion procede y cuando no puede ejecutarse | Evidencia funcional en AC-004 y cobertura de riesgo en US-UBUS-004 |

---

## 20. Observabilidad funcional

### 20.1 Eventos funcionales a registrar

| Evento | Cuándo ocurre | Datos mínimos a registrar |
|--------|----------------|---------------------------|
| DIGITAL_TICKET_PURCHASE_PROCESSED | Al resolverse una compra de billete | resultado, timestamp |
| DIGITAL_TICKET_STATUS_VIEWED | Al consultar un billete adquirido | identificador de billete, estado funcional |
| DIGITAL_TICKET_ACTIVATION_REQUESTED | Al solicitar activacion | identificador de billete, resultado |

### 20.2 Alertas funcionales

| Alerta | Condición de activación | Destinatario / acción esperada |
|--------|--------------------------|--------------------------------|
| ALERT-TICKET-STATE-CONFUSION | Incidencia repetida por dudas de estado o uso del billete | Revision funcional de mensajes y reglas |

### 20.3 Métricas / KPIs de negocio

| Indicador | Fórmula / definición | Objetivo / umbral |
|-----------|----------------------|-------------------|
| KPI-TKT-01 | Compras correctas / intentos de compra | pendiente de refinamiento |

---

## 21. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Requisito de negocio | BGS-UBUS-01 | Mejorar el autoservicio digital del viajero urbano |
| Épica | EPIC-UBUS-01 | Autoservicio digital para informacion operativa y ticketing basico en autobus urbano |
| Historias de usuario derivadas | US-UBUS-003, US-UBUS-004 | Historias derivadas del requisito |
| Servicio | pendiente de refinamiento | No se identifica servicio concreto en el documento fuente |
| ADR relacionado | pendiente de refinamiento | No identificado en esta fase |
| Riesgo relacionado | RSK-001, RSK-002 | Riesgos funcionales asociados |
| Control relacionado | Controles descritos en §19 | Controles funcionales asociados al requisito |
| Sesión refinamiento | REF-ANA-UBUS-001-01 | Refinamiento inicial derivado del documento fuente |
| Tests de alto nivel | TC-UBUS-TKT-001, TC-UBUS-TKT-002, TC-UBUS-TKT-003, TC-UBUS-TKT-004 | Ver §18 |
| Cobertura funcional derivada | US-UBUS-003, US-UBUS-004 + TC-UBUS-TKT-* | Debe continuar en US con AC y Gherkin |
| Enlace RTM | LINK-003, LINK-004 | Entradas en `traceability/RTM.yaml` |

---

## 22. Dependencias

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Requisito FRS | FRS-UBUS-001 | `relacionada-con` | Comparte contexto funcional general del autoservicio del viajero |
| Servicio ext. | Plataforma de ticketing y pago | `consume` | Debe soportar compra, disponibilidad y activacion del billete |

---

## 23. Notas y decisiones abiertas

| # | Nota / Pregunta abierta | Responsable | Estado | Fecha objetivo | Decisión tomada | Impacto | Evidencia / referencia |
|---|--------------------------|-------------|--------|----------------|-----------------|---------|------------------------|
| 1 | Confirmar si la activacion del billete debe ser obligatoria o automatica en algun escenario | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Alto | Documento inicial de analisis.txt §12 |
| 2 | Definir cuanto tiempo puede transcurrir entre compra y activacion sin afectar a la validez | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Alto | Documento inicial de analisis.txt §12 |
| 3 | Confirmar que informacion minima debe ver el usuario para considerar que el billete esta listo para uso | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Alto | Documento inicial de analisis.txt §12 |

---

*Plantilla: `functional-requirement.template.md` v2.3.0 — AgentProjectFromScratch v1.2.2*
