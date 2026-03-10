# EPIC-BUS-01 — Digitalización del ciclo de venta de plazas para rutas interurbanas de autobús

---

## Metadatos

| Campo                        | Valor                                                                 |
|-----------------------------|-----------------------------------------------------------------------|
| **ID**                      | EPIC-BUS-01                                                           |
| **Versión**                 | 1.0.0                                                                 |
| **Estado**                  | aprobado                                                              |
| **Estabilidad**             | estable                                                               |
| **Fecha**                   | 2026-03-10                                                            |
| **Autor**                   | Oficina de Análisis Funcional                                         |
| **Revisado por**            | Responsable de Operaciones de Transporte                              |
| **Aprobado por**            | Dirección de Negocio de Movilidad                                     |
| **Módulo Funcional**        | Comercialización y Venta                                              |
| **Submódulo Funcional**     | Venta Digital de Billetes                                             |
| **Prioridad**               | crítica                                                               |
| **Porcentaje de completud** | 100%                                                                  |
| **Fuente**                  | Plan de digitalización comercial del canal web y móvil para rutas interurbanas |
| **Sesión refinamiento**     | REF-BUS-2026-03-05-01                                                 |
| **Enlace RTM**              | traceability/RTM.yaml#EPIC-BUS-01                                     |
| **Objetivo de negocio**     | BGS-BUS-01 — Incrementar la venta digital y reducir la dependencia del canal presencial |

> **Estados válidos:** `borrador` | `en-revisión` | `aprobado` | `rechazado` | `obsoleto`
>
> **Estabilidad válida:** `estable` | `volátil` | `en-cambio`
>
> **Prioridades válidas:** `crítica` | `alta` | `media` | `baja`
>
> **Porcentaje de completud:** valor entre `0%` y `100%`

---

## Historial de versiones

| Versión | Fecha      | Autor                         | Cambios |
|---------|------------|-------------------------------|---------|
| 0.1.0   | 2026-03-04 | Oficina de Análisis Funcional | Borrador inicial de la épica |
| 0.9.0   | 2026-03-07 | Oficina de Análisis Funcional | Ajustes tras refinamiento con Comercial, Operaciones y Atención al Cliente |
| 1.0.0   | 2026-03-10 | Oficina de Análisis Funcional | Versión aprobada |

---

## 1. Propósito de la épica

> Explica qué problema de negocio aborda esta épica y por qué existe.

Esta épica tiene como propósito habilitar un proceso digital completo para la búsqueda, reserva, compra, emisión y consulta de billetes de autobús en rutas interurbanas, permitiendo a los clientes operar de forma autónoma desde los canales web y móvil.

La épica existe para transformar un proceso tradicionalmente dependiente de taquilla, atención telefónica o intermediación manual en un flujo digital trazable, escalable y orientado a la mejora de ventas, experiencia de usuario y eficiencia operativa.

---

## 2. Contexto de negocio

> Situación actual, necesidad detectada y motivación.

La compañía opera rutas interurbanas con una oferta de expediciones, tarifas y plazas que hasta ahora se comercializan de forma heterogénea entre canal presencial, atención al cliente y herramientas digitales limitadas. Esta situación provoca fricción en la compra, baja autonomía del cliente, dependencia de procesos manuales y dificultad para escalar la comercialización en momentos de alta demanda.

El negocio necesita consolidar un canal digital que permita a los clientes consultar servicios disponibles, comprar billetes y recuperar su reserva sin intervención humana, garantizando además consistencia con la operación de plazas, trazabilidad de las ventas y soporte postventa básico.

La motivación principal es incrementar el peso del canal digital en la venta total, mejorar la experiencia del viajero y reducir costes operativos derivados de tareas manuales repetitivas.

---

## 3. Objetivo de negocio

> Resultado esperado desde la perspectiva del negocio.

Disponer de una capacidad funcional digital que permita vender plazas interurbanas de autobús de forma autónoma, segura y trazable, incrementando el volumen de ventas digitales, reduciendo la dependencia del canal presencial y mejorando la gestión operativa y de atención al cliente asociada a las reservas emitidas.

---

## 4. Alcance

### 4.1 Incluido en esta épica

- Consulta digital de rutas, fechas y expediciones disponibles.
- Selección de expediciones y cálculo de tarifas aplicables.
- Captura de datos básicos de pasajeros para la reserva.
- Confirmación de compra y emisión de billetes electrónicos.
- Consulta posterior de reservas emitidas por parte del cliente.
- Registro funcional de las ventas para operación, soporte y control.
- Gestión funcional de validaciones y errores del proceso de compra.

### 4.2 Fuera de alcance

- Planificación operativa de rutas y cuadrantes de flota.
- Gestión de mantenimiento de autobuses.
- Venta presencial en taquilla.
- Gestión avanzada de fidelización y programas de puntos.
- Revenue management dinámico avanzado.
- Integración con operadores externos multimodales en esta primera fase.

### 4.3 Límites

- La épica cubre únicamente rutas interurbanas nacionales operadas por la compañía.
- La primera versión se centra en venta digital directa en web y app móvil.
- La épica no entra en detalle técnico de integración, solo en la capacidad funcional esperada.
- La gestión de cambios y cancelaciones puede tratarse como evolución o como FRS independientes posteriores.

---

## 5. Problema que resuelve

> Describe el dolor actual, la ineficiencia, riesgo o limitación que esta épica pretende resolver.

Actualmente el proceso de venta de billetes presenta limitaciones de autoservicio, inconsistencias entre canales, dependencia de soporte manual y una trazabilidad funcional mejorable entre disponibilidad, venta y emisión. Esto reduce la conversión comercial, incrementa la carga operativa sobre personal de atención y dificulta la experiencia del cliente, especialmente en periodos de alta demanda.

La épica resuelve este problema proporcionando un marco funcional unificado para la venta digital de plazas, desde la consulta hasta la emisión del billete, con un modelo claro de relaciones entre cliente, reserva, expedición y soporte postventa.

---

## 6. Valor esperado

> Beneficio esperado para negocio, operación, cliente o cumplimiento.

| Tipo de valor     | Descripción |
|-------------------|-------------|
| Negocio           | Incremento del volumen de ventas por canales digitales y mejor aprovechamiento de la capacidad comercializable |
| Operativo         | Reducción de tareas manuales en atención al cliente y mejor control de reservas emitidas |
| Cliente / usuario | Proceso de compra más rápido, autónomo y disponible 24x7 |
| Cumplimiento      | Mayor trazabilidad de operaciones y tratamiento controlado de datos de pasajeros y reservas |

---

## 7. Stakeholders

| Stakeholder | Interés / expectativa | Impacto |
|-------------|------------------------|---------|
| Dirección Comercial | Aumentar las ventas digitales y mejorar la conversión del canal | Alto |
| Operaciones de Transporte | Disponer de ocupación comercial consistente con la disponibilidad real | Alto |
| Atención al Cliente | Poder localizar reservas y asistir al cliente con menor fricción | Alto |
| Dirección de Transformación Digital | Consolidar la digitalización del proceso comercial | Alto |
| Finanzas | Mejorar la conciliación funcional entre ventas y cobros aceptados | Medio |
| Cumplimiento / Legal | Garantizar tratamiento adecuado de datos y evidencias de operación | Medio |

---

## 8. Capacidades funcionales esperadas

> Grandes capacidades que la épica debe habilitar. No entrar aún al detalle técnico ni al detalle de implementación.

| ID | Capacidad | Descripción |
|----|-----------|-------------|
| CAP-001 | Consulta de expediciones | Permitir al cliente buscar servicios por origen, destino y fecha con visualización de horarios, plazas y precio |
| CAP-002 | Reserva y compra digital | Permitir seleccionar una expedición, informar datos requeridos y completar la compra |
| CAP-003 | Emisión de billete electrónico | Generar un billete digital con identificador único y datos del viaje tras la compra confirmada |
| CAP-004 | Consulta posterior de reserva | Permitir recuperar una reserva o billete emitido mediante datos de localización |
| CAP-005 | Registro funcional y trazabilidad | Dejar evidencias funcionales de búsqueda, compra, emisión y errores relevantes del proceso |
| CAP-006 | Gestión de validaciones y excepciones | Controlar datos inválidos, indisponibilidades de plazas y errores funcionales de compra |

---

## 9. Criterios de éxito de la épica

> Cómo sabremos que la épica ha cumplido su objetivo.

| ID | Criterio de éxito | Métrica / evidencia |
|----|-------------------|---------------------|
| ESC-001 | Los clientes pueden completar la compra digital de billetes sin intervención manual en el flujo estándar | Evidencia de compra completa en entorno productivo y reducción de ventas asistidas |
| ESC-002 | Toda compra válida genera un billete electrónico consultable posteriormente | Validación funcional de emisión y recuperación de billetes |
| ESC-003 | El proceso digital mantiene consistencia básica entre disponibilidad, reserva y emisión | Trazabilidad funcional sin sobreventa en los casos estándar |
| ESC-004 | El canal digital soporta la mayor parte de las operaciones previstas del negocio | Seguimiento del peso porcentual del canal digital sobre el total de ventas |

---

## 10. Indicadores / KPIs asociados

| KPI | Definición | Objetivo |
|-----|------------|----------|
| Porcentaje de venta digital | Billetes vendidos por canal digital / total de billetes vendidos | Superar el 45% en el primer ciclo de implantación |
| Conversión de búsqueda a compra | Compras confirmadas / búsquedas ejecutadas | Superior al 15% |
| Tasa de emisión correcta | Billetes emitidos / pagos aceptados | Igual o superior al 99,8% |
| Reducción de atención manual | Consultas o gestiones manuales asociadas a compra básica / periodo anterior | Reducción del 30% |
| Tasa de incidencias postpago | Casos con pago aceptado y billete no emitido / pagos aceptados | Inferior al 0,2% |

---

## 11. Dependencias de alto nivel

| Tipo | Dependencia | Relación | Descripción |
|------|-------------|----------|-------------|
| `proceso` | Publicación de catálogo comercial | `depende-de` | La venta digital requiere expediciones, estaciones y tarifas previamente publicadas |
| `sistema` | Sistema de disponibilidad de plazas | `depende-de` | La capacidad digital depende de consultar plazas disponibles por expedición |
| `sistema` | Pasarela de pago | `depende-de` | La compra digital necesita confirmación funcional del cobro |
| `organización` | Operaciones de Transporte | `condiciona` | Debe existir alineación entre oferta operativa y oferta comercial publicada |
| `organización` | Atención al Cliente | `condiciona` | Deben definirse procedimientos de soporte para incidencias funcionales |
| `proceso` | Política tarifaria vigente | `depende-de` | Las reglas de precio y descuento deben estar definidas y comunicadas |

---

## 12. Riesgos y supuestos

### 12.1 Riesgos

| Riesgo ID | Descripción | Probabilidad | Impacto | Mitigación |
|-----------|-------------|--------------|---------|------------|
| ERSK-001 | Desfase entre disponibilidad mostrada y plazas realmente vendibles | media | alta | Revalidar disponibilidad en el momento de la confirmación |
| ERSK-002 | Fallos funcionales de emisión tras cobro aceptado | baja | alta | Definir circuito de revisión prioritaria y trazabilidad de incidencias |
| ERSK-003 | Baja adopción del canal digital por mala experiencia de compra | media | alta | Diseñar flujo simple, mensajes claros y soporte de recuperación de reserva |
| ERSK-004 | Aplicación incorrecta de tarifas o bonificaciones | media | media | Validar reglas tarifarias antes de la confirmación final |
| ERSK-005 | Exposición indebida de datos personales en procesos de consulta | baja | alta | Definir perfiles funcionales, visibilidad restringida y enmascaramiento de datos |

### 12.2 Supuestos

- Se asume que el negocio dispone de un catálogo vigente de rutas, estaciones, expediciones y tarifas.
- Se asume que las plazas disponibles pueden consultarse de forma fiable en el momento de la compra.
- Se asume que la organización prioriza el canal digital como canal estratégico de venta.
- Se asume que atención al cliente contará con acceso funcional a las reservas emitidas.
- Se asume que las condiciones legales y comerciales del servicio están definidas antes de la implantación.

---

## 13. Requisitos funcionales candidatos asociados

> Requisitos funcionales que previsiblemente formarán parte de esta épica.

| FRS ID | Título | Estado | Observaciones |
|--------|--------|--------|---------------|
| FRS-BUS-001 | Reserva y emisión de billetes para rutas interurbanas de autobús | aprobado | Requisito funcional principal del flujo de venta |
| FRS-BUS-002 | Consulta de expediciones disponibles por origen, destino y fecha | en-revisión | Puede separarse del FRS principal si se desea mayor granularidad |
| FRS-BUS-003 | Consulta posterior de reservas y billetes emitidos | borrador | Cobertura postventa básica |
| FRS-BUS-004 | Gestión funcional de validaciones y errores del proceso de compra | borrador | Requisito transversal de soporte al flujo |
| FRS-BUS-005 | Aplicación de tarifas y descuentos comerciales | borrador | Podría consolidarse con otros FRS o mantenerse separado |

---

## 14. Historias de usuario candidatas

> Historias de usuario que desarrollan funcionalmente la épica.

| US ID | Título | Estado | Prioridad | Observaciones |
|-------|--------|--------|-----------|---------------|
| US-BUS-001 | Como cliente quiero buscar expediciones por origen, destino y fecha para elegir un viaje disponible | en-definición | alta | Relacionada con consulta inicial |
| US-BUS-002 | Como cliente quiero ver horarios, plazas y precios para comparar opciones antes de comprar | en-definición | alta | Ligada a visualización comercial |
| US-BUS-003 | Como cliente quiero comprar un billete indicando mis datos para viajar sin ir a taquilla | en-definición | crítica | Historia principal del flujo |
| US-BUS-004 | Como cliente quiero recibir un billete electrónico con localizador para poder usarlo en el viaje | en-definición | crítica | Asociada a emisión y entrega |
| US-BUS-005 | Como cliente quiero recuperar mi billete con un localizador para volver a consultarlo o descargarlo | borrador | media | Cobertura postventa |
| US-BUS-006 | Como agente de atención al cliente quiero localizar una reserva para dar soporte al viajero | borrador | media | Historia orientada a soporte |
| US-BUS-007 | Como sistema quiero bloquear compras sin plazas disponibles para evitar sobreventas | borrador | alta | Historia de control funcional |
| US-BUS-008 | Como cliente quiero ver mensajes claros cuando haya errores en mis datos o en el pago | borrador | alta | Historia de experiencia de error |

---

## 15. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Objetivo de negocio | BGS-BUS-01 | Incrementar la venta digital y reducir la dependencia del canal presencial |
| Módulo funcional | Comercialización y Venta | Dominio funcional de comercialización de servicios de transporte |
| Submódulo funcional | Venta Digital de Billetes | Capacidad digital específica de compra y gestión básica de reservas |
| Requisitos funcionales | FRS-BUS-001, FRS-BUS-002, FRS-BUS-003, FRS-BUS-004, FRS-BUS-005 | Requisitos vinculados a la épica |
| Historias de usuario | US-BUS-001 a US-BUS-008 | Historias derivadas de la épica |
| Riesgos relacionados | ERSK-001, ERSK-002, ERSK-003, ERSK-004, ERSK-005 | Riesgos asociados |
| Tests relacionados | TEST-BUS-EPIC-001, TEST-BUS-EPIC-002 | Validaciones de alto nivel sobre la capacidad global |
| Enlace RTM | traceability/RTM.yaml#EPIC-BUS-01 | Entrada en la matriz de trazabilidad |

---

## 16. Notas y decisiones abiertas

| # | Nota / pregunta | Responsable | Estado | Fecha objetivo | Decisión tomada | Evidencia |
|---|------------------|-------------|--------|----------------|-----------------|----------|
| 1 | Confirmar si la primera release incluirá compra de ida y vuelta en una sola operación | Dirección Comercial | resuelta | 2026-03-08 | Sí, se permite si la combinación está soportada por catálogo | Acta REF-BUS-2026-03-05-01 |
| 2 | Definir si la selección de asiento forma parte del alcance inicial | Operaciones | en-análisis | 2026-03-20 | Pendiente para siguiente iteración de análisis | Backlog evolutivo BUS-R2 |
| 3 | Determinar si la recuperación de billete requerirá solo localizador o localizador más email | Atención al Cliente | resuelta | 2026-03-09 | Se exige localizador y email asociado para mayor seguridad funcional | Acta de definición funcional v1 |
| 4 | Evaluar si las cancelaciones y cambios se documentarán en esta misma épica o en una épica separada | Oficina de Análisis Funcional | en-análisis | 2026-03-22 | Pendiente de decisión de alcance | Comité de backlog marzo 2026 |

> **Estados sugeridos:** `abierta` | `en-análisis` | `resuelta` | `descartada`

---

*Plantilla: `epic.template.md` v1.1.0 — Ejemplo completo de guía*
