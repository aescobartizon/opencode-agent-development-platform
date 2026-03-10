# FRS-BUS-001 — Reserva y emisión de billetes para rutas interurbanas de autobús

---

## Metadatos

| Campo                        | Valor                                                                 |
|-----------------------------|-----------------------------------------------------------------------|
| **ID**                      | FRS-BUS-001                                                           |
| **Versión**                 | 1.0.0                                                                 |
| **Estado**                  | aprobado                                                              |
| **Estabilidad**             | estable                                                               |
| **Fecha**                   | 2026-03-10                                                            |
| **Autor**                   | Oficina de Análisis Funcional                                         |
| **Revisado por**            | Responsable de Operaciones de Transporte                              |
| **Aprobado por**            | Dirección de Negocio de Movilidad                                     |
| **Módulo Funcional**        | Comercialización y Venta                                              |
| **Submódulo Funcional**     | Reserva y Emisión de Billetes                                         |
| **Épica**                   | EPIC-BUS-01 — Digitalización del ciclo de venta de plazas             |
| **Prioridad**               | crítica                                                               |
| **Porcentaje de completud** | 100%                                                                  |
| **Fuente**                  | Necesidad de negocio derivada del plan de digitalización del canal web y app |
| **Sesión refinamiento**     | REF-BUS-2026-03-05-01                                                 |
| **Enlace RTM**              | traceability/RTM.yaml#FRS-BUS-001                                     |
| **Método verificación**     | test                                                                  |

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

| Versión | Fecha      | Autor                         | Cambios |
|---------|------------|-------------------------------|---------|
| 0.1.0   | 2026-03-03 | Oficina de Análisis Funcional | Borrador inicial |
| 0.9.0   | 2026-03-07 | Oficina de Análisis Funcional | Ajustes tras refinamiento con Operaciones y Atención al Cliente |
| 1.0.0   | 2026-03-10 | Oficina de Análisis Funcional | Versión aprobada |

---

## 1. Descripción

> Descripción funcional completa del requisito. Qué debe hacer el sistema, no cómo lo hace.

El sistema debe permitir que un cliente reserve y compre un billete para una ruta interurbana de autobús seleccionando origen, destino, fecha, horario y número de pasajeros. El sistema debe mostrar las expediciones disponibles, las plazas libres, la tarifa aplicable y el importe final antes de confirmar la compra.

Una vez completado el proceso de reserva y pago, el sistema debe emitir un billete electrónico con identificador único, datos del viaje, datos del pasajero y código de validación, disponible para consulta y descarga. El sistema también debe registrar la operación para su posterior uso por parte de los equipos de inspección, atención al cliente y explotación.

---

## 2. Alcance y límites

> Delimita expresamente qué cubre este requisito y qué queda fuera para evitar ambigüedades y expansión de alcance.

### 2.1 Alcance incluido

- Búsqueda de expediciones por origen, destino y fecha.
- Visualización de horarios, plazas disponibles y tarifas.
- Selección de una expedición concreta.
- Introducción de datos básicos del pasajero.
- Aplicación de descuentos comerciales o bonificaciones configuradas.
- Confirmación de reserva y pago.
- Emisión de billete electrónico.
- Consulta posterior del billete emitido por localizador.

### 2.2 Fuera de alcance

- Gestión del mantenimiento de la flota de autobuses.
- Planificación de rutas por parte de Operaciones.
- Venta presencial en taquilla física.
- Programas de fidelización avanzados basados en puntos.
- Gestión de incidencias de pasarela de pago más allá del resultado funcional recibido.

### 2.3 Límites del requisito

- El requisito cubre únicamente rutas interurbanas nacionales operadas por la compañía.
- El requisito contempla emisión para un máximo de 6 pasajeros por operación.
- El requisito no contempla cambios complejos de billetes combinados con otros operadores.

---

## 3. Evento disparador

> Evento, acción o condición que inicia la ejecución de este requisito.

- **Tipo de disparador:** `usuario`
- **Disparador principal:** El cliente solicita la búsqueda y compra de un billete de autobús.
- **Canal / origen:** Portal web de venta y aplicación móvil oficial.
- **Frecuencia esperada:** Continua durante la ventana operativa del canal digital, con mayor intensidad en vísperas de fines de semana, festivos y periodos vacacionales.

---

## 4. Actores y stakeholders

> Distinguir entre **actores del sistema** (interactúan directamente con el sistema) y **stakeholders** (tienen interés en el resultado pero no interactúan directamente).

### 4.1 Actores del sistema

| Actor | Tipo | Rol en este requisito |
|-------|------|-----------------------|
| Cliente | `primario` | Busca expediciones, selecciona viaje, introduce datos y realiza la compra |
| Pasarela de pago | `secundario` | Devuelve el resultado funcional del cobro |
| Sistema de explotación de plazas | `sistema-externo` | Proporciona disponibilidad de plazas por expedición |
| Inspector / revisor | `secundario` | Consulta o valida el billete emitido durante el viaje |
| Agente de atención al cliente | `secundario` | Consulta la reserva para soporte postventa |

> **Tipos:** `primario` (inicia el flujo) | `secundario` (participa en el flujo) | `sistema-externo`

### 4.2 Stakeholders interesados

| Stakeholder | Interés / Impacto |
|-------------|-------------------|
| Dirección Comercial | Incrementar ventas por canal digital y reducir fricción en la compra |
| Operaciones de Transporte | Disponer de reservas consistentes para control de ocupación |
| Atención al Cliente | Poder localizar fácilmente una reserva y dar soporte |
| Finanzas | Garantizar conciliación básica entre reservas emitidas y pagos aceptados |
| Cumplimiento / Legal | Asegurar tratamiento adecuado de datos del pasajero y emisión de comprobantes |

---

## 5. Entradas y salidas del sistema

> Descripción explícita de los datos que el sistema recibe y produce como resultado de este requisito.

### 5.1 Entradas

| # | Nombre | Tipo / Formato | Origen | Obligatorio | Validaciones |
|---|--------|----------------|--------|-------------|--------------|
| 1 | Origen | Código de estación | Cliente | Sí | Debe existir en catálogo de estaciones habilitadas |
| 2 | Destino | Código de estación | Cliente | Sí | Debe existir en catálogo y ser distinto del origen |
| 3 | Fecha de viaje | Fecha `YYYY-MM-DD` | Cliente | Sí | Debe ser fecha válida y no anterior al día actual |
| 4 | Expedición seleccionada | Identificador alfanumérico | Cliente / sistema | Sí | Debe corresponder a una expedición disponible para la búsqueda |
| 5 | Número de pasajeros | Entero | Cliente | Sí | Valor entre 1 y 6 |
| 6 | Datos del pasajero principal | Nombre, apellidos, documento, email, teléfono | Cliente | Sí | Formatos obligatorios y campos mínimos completos |
| 7 | Tipo de descuento | Código de tarifa bonificada | Cliente | No | Debe estar vigente y ser compatible con la expedición |
| 8 | Confirmación de compra | Booleano | Cliente | Sí | Debe ser afirmativa para continuar al pago |

### 5.2 Salidas

| # | Nombre | Tipo / Formato | Destino | Descripción |
|---|--------|----------------|---------|-------------|
| 1 | Lista de expediciones | Lista estructurada | Cliente | Horarios, duración, plazas y precio por expedición |
| 2 | Resumen de compra | Objeto estructurado | Cliente | Datos del trayecto, pasajeros, tarifa y total |
| 3 | Billete electrónico | PDF / representación digital | Cliente | Billete emitido con localizador y código de validación |
| 4 | Registro de reserva | Registro transaccional | Sistemas internos | Reserva persistida para consulta operativa y soporte |
| 5 | Estado de emisión | Código y mensaje funcional | Cliente / sistemas internos | Confirma éxito o causa funcional del fallo |

---

## 6. Calidad y sensibilidad del dato

> Define expectativas mínimas sobre la calidad del dato y su tratamiento funcional.

### 6.1 Clasificación de datos

| Dato / conjunto | Sensibilidad | Origen | Retención | Observaciones |
|-----------------|--------------|--------|-----------|---------------|
| Datos identificativos del pasajero | `confidencial` | Cliente | 5 años | Necesarios para soporte, inspección y obligaciones administrativas |
| Datos de la reserva | `interno` | Sistema | 5 años | Deben conservarse para operación y trazabilidad |
| Datos de contacto | `confidencial` | Cliente | 3 años | Utilizados para envío de billete y comunicaciones relacionadas |
| Datos de pago tokenizados | `restringido` | Pasarela de pago | Según política financiera | El sistema funcional no almacena tarjeta completa |

### 6.2 Reglas de calidad de datos

| ID | Dimensión | Regla / umbral |
|----|-----------|----------------|
| DQ-001 | completitud | Toda reserva confirmada debe tener origen, destino, fecha, expedición, pasajeros y datos mínimos del pasajero principal |
| DQ-002 | validez | El documento identificativo y el email deben cumplir el formato permitido |
| DQ-003 | unicidad | Cada billete emitido debe tener un localizador único no reutilizable |
| DQ-004 | consistencia | El número de plazas reservadas no puede superar la disponibilidad confirmada de la expedición |

### 6.3 Consideraciones funcionales sobre datos

- El email del cliente debe ser suficiente para reenviar el billete y localizar la compra.
- Las bonificaciones solo deben aplicarse si los datos aportados permiten validarlas funcionalmente.
- La expedición ofrecida al cliente debe corresponder con disponibilidad vigente en el momento de la confirmación.

---

## 7. Precondiciones

> Condiciones que deben cumplirse **antes** de que este requisito pueda ejecutarse.

- Debe existir un catálogo vigente de estaciones y rutas comercializables.
- Deben existir expediciones publicadas para la fecha consultada.
- El canal digital debe estar operativo.
- El sistema de disponibilidad debe responder con plazas y tarifas activas.
- La pasarela de pago debe encontrarse disponible para operaciones de cobro.

---

## 8. Postcondiciones

> Estado del sistema **después** de que este requisito se haya ejecutado correctamente.

- La reserva queda registrada con estado `emitida`.
- Las plazas correspondientes quedan descontadas de la disponibilidad comercial.
- El cliente dispone de un billete electrónico válido asociado a un localizador único.
- El sistema registra la operación para consulta posterior por soporte e inspección.
- El cliente recibe confirmación de compra y acceso al billete.

---

## 9. Supuestos

> Condiciones que se asumen como verdaderas para que este requisito sea válido. Si un supuesto no se cumple, el requisito debe revisarse.

- Se asume que la información de plazas devuelta por el sistema de explotación es fiable y actualizada.
- Se asume que la pasarela de pago devuelve un resultado funcional inequívoco de aceptación o rechazo.
- Se asume que el cliente acepta las condiciones de transporte antes de confirmar la compra.
- Se asume que las tarifas y descuentos vigentes han sido cargados previamente por negocio.

---

## 10. Restricciones

> Limitaciones funcionales, regulatorias, organizativas o temporales que condicionan este requisito.

| Tipo | Restricción | Impacto / Justificación |
|------|-------------|-------------------------|
| `normativa` | El tratamiento de datos personales del pasajero debe ajustarse a la normativa aplicable de protección de datos | Condiciona qué datos se solicitan y cómo se muestran o conservan |
| `organizativa` | Solo pueden venderse rutas dadas de alta por la compañía en el catálogo comercial | Evita comercialización de expediciones no autorizadas |
| `proceso` | La emisión del billete solo puede completarse tras respuesta positiva del proceso de cobro | Asegura consistencia entre venta y pago |
| `temporal` | No se permite la compra online de una expedición cuya salida esté prevista en menos de 10 minutos | Reduce riesgo operativo y conflictos de embarque |
| `seguridad` | El sistema no debe exponer información completa de medios de pago al usuario interno | Minimiza exposición de datos sensibles |
| `compatibilidad` | El billete emitido debe poder consultarse desde web, app y herramientas de inspección | Asegura operatividad en distintos canales |

> **Tipos sugeridos:** `normativa` | `organizativa` | `proceso` | `temporal` | `compatibilidad` | `seguridad`

---

## 11. Frecuencia, volumetría y criticidad operativa

> Información funcional útil para priorización, dimensionamiento posterior y análisis de impacto.

| Aspecto | Valor |
|---------|-------|
| **Frecuencia esperada** | Alta, uso continuo diario |
| **Volumen estimado** | 18.000 búsquedas diarias y 3.500 compras diarias en temporada media |
| **Picos esperados** | Viernes, domingos, festivos nacionales y periodos vacacionales |
| **Ventana operativa** | 24x7 para consulta y compra |
| **Criticidad de negocio** | `alta` |
| **Impacto por indisponibilidad** | Pérdida directa de ventas, incremento de atención manual y deterioro de imagen del canal digital |

---

## 12. Flujo principal

> Secuencia de pasos del camino feliz (happy path).

1. El cliente accede al canal digital de venta.
2. El cliente informa origen, destino y fecha de viaje.
3. El sistema consulta las expediciones disponibles para los criterios indicados.
4. El sistema muestra al cliente la lista de expediciones con horario, duración, plazas y precio.
5. El cliente selecciona una expedición.
6. El sistema muestra el detalle de la compra y solicita los datos del pasajero.
7. El cliente completa los datos requeridos y confirma la intención de compra.
8. El sistema recalcula el importe final y presenta el resumen definitivo.
9. El cliente confirma la compra y realiza el pago.
10. El sistema recibe confirmación positiva del cobro.
11. El sistema registra la reserva y emite el billete electrónico.
12. El sistema muestra confirmación de compra y pone el billete a disposición del cliente.

---

## 13. Flujos alternativos

> Variaciones válidas del flujo principal.

### 13.1 Aplicación de descuento de ida y vuelta

- **Condición de activación:** El cliente selecciona una combinación de trayectos que permite descuento comercial.
- **Pasos:**
  1. El sistema detecta que la combinación cumple las condiciones promocionales.
  2. El sistema recalcula el importe con la tarifa promocional.
  3. El sistema muestra el descuento aplicado en el resumen de compra.
  4. El cliente continúa el proceso con el nuevo importe.

### 13.2 Compra para varios pasajeros

- **Condición de activación:** El cliente indica más de un pasajero.
- **Pasos:**
  1. El sistema solicita la información mínima de cada pasajero.
  2. El sistema verifica que la expedición dispone de suficientes plazas.
  3. El sistema recalcula el total según el número de pasajeros y tarifas aplicables.
  4. El cliente revisa el resumen agregado y continúa con el pago.

### 13.3 Consulta posterior por localizador

- **Condición de activación:** El cliente ya completó una compra y desea recuperar el billete.
- **Pasos:**
  1. El cliente accede a la opción de consulta de reserva.
  2. El cliente informa localizador y correo electrónico.
  3. El sistema valida la coincidencia.
  4. El sistema muestra la reserva y permite descargar el billete.

---

## 14. Flujos de excepción

> Situaciones de error o fallo que el sistema debe manejar.

### 14.1 Sin expediciones disponibles

- **Condición de activación:** No existen expediciones comercializables para origen, destino y fecha.
- **Respuesta del sistema:** El sistema informa de que no hay servicios disponibles y permite modificar la búsqueda.
- **Código de error (si aplica):** BUS-VAL-001

### 14.2 Plazas agotadas durante la confirmación

- **Condición de activación:** La expedición tenía plazas al mostrar resultados pero ya no dispone de ellas al confirmar la compra.
- **Respuesta del sistema:** El sistema informa de la indisponibilidad sobrevenida, cancela la continuación del proceso y ofrece volver al listado actualizado.
- **Código de error (si aplica):** BUS-AVL-002

### 14.3 Pago rechazado

- **Condición de activación:** La pasarela de pago devuelve rechazo funcional de la operación.
- **Respuesta del sistema:** El sistema informa de que no ha sido posible completar el pago y permite reintentar o elegir otro medio permitido.
- **Código de error (si aplica):** BUS-PAY-003

### 14.4 Datos obligatorios incompletos o inválidos

- **Condición de activación:** El cliente intenta continuar sin completar los datos mínimos o con formatos no válidos.
- **Respuesta del sistema:** El sistema identifica los campos erróneos, muestra mensajes claros y bloquea el avance hasta su corrección.
- **Código de error (si aplica):** BUS-VAL-004

### 14.5 Error en la emisión tras cobro aceptado

- **Condición de activación:** El cobro ha sido aceptado pero el billete no puede emitirse en el proceso estándar.
- **Respuesta del sistema:** El sistema registra incidencia, informa al cliente de que la operación está en revisión y genera un caso para atención prioritaria.
- **Código de error (si aplica):** BUS-ISS-005

---

## 15. Reglas de negocio

> Restricciones, políticas o lógica de dominio que aplican a este requisito.

| ID | Regla | Fuente / Referencia |
|----|-------|---------------------|
| BR-001 | El origen y el destino deben ser estaciones distintas | Política comercial de venta |
| BR-002 | No se pueden vender más plazas de las disponibles para una expedición | Norma operativa de ocupación |
| BR-003 | Una expedición no puede comercializarse online a menos de 10 minutos de su salida | Política operativa del canal digital |
| BR-004 | Toda compra confirmada debe generar un localizador único | Norma funcional de trazabilidad |
| BR-005 | Las bonificaciones solo pueden aplicarse si el cliente aporta la información requerida | Política tarifaria |
| BR-006 | Un billete emitido debe estar asociado al menos a un pasajero identificado | Procedimiento de inspección y soporte |
| BR-007 | El billete solo se considera válido cuando el estado de la reserva es `emitida` | Modelo de estados de venta |

---

## 16. Requisitos no funcionales asociados

> Requisitos de calidad, rendimiento o seguridad directamente vinculados a este requisito funcional.

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| NFR-BUS-001 | rendimiento | La búsqueda de expediciones debe responder con rapidez adecuada para el usuario | 95% de las búsquedas completadas en menos de 3 segundos |
| NFR-BUS-002 | disponibilidad | El canal digital de compra debe estar disponible la mayor parte del tiempo | Disponibilidad mensual igual o superior al 99,5% |
| NFR-BUS-003 | seguridad | Los datos personales del pasajero deben estar protegidos en consulta y almacenamiento | No mostrar datos sensibles completos a perfiles no autorizados |
| NFR-BUS-004 | usabilidad | El proceso de compra debe ser comprensible y guiado | El usuario debe poder completar la compra sin asistencia en el flujo estándar |
| NFR-BUS-005 | mantenibilidad | Los mensajes funcionales de error deben ser catalogables y gestionables | Todos los errores funcionales deben devolver código y texto controlado |

> **Tipos válidos:** `rendimiento` | `seguridad` | `disponibilidad` | `usabilidad` | `escalabilidad` | `mantenibilidad`

---

## 17. Criterios de aceptación

> Condiciones concretas y verificables que deben cumplirse para considerar este requisito implementado y aceptado. Seguir el patrón **Dado / Cuando / Entonces**.
>
> **Cobertura mínima recomendada:** incluir al menos un criterio del flujo principal, uno de validación relevante, uno de error relevante y uno de autorización/seguridad si aplica.

### AC-001 — Compra correcta de un billete individual

- **Dado** que existe una expedición con plazas disponibles entre Madrid y Segovia para la fecha seleccionada
- **Cuando** un cliente completa los datos obligatorios, confirma la compra y el pago es aceptado
- **Entonces** el sistema debe registrar la reserva, descontar una plaza y emitir un billete electrónico con localizador único

### AC-002 — Validación de campos obligatorios

- **Dado** que el cliente ha seleccionado una expedición
- **Cuando** intenta continuar sin informar el nombre del pasajero principal o con un email inválido
- **Entonces** el sistema debe bloquear el avance y mostrar el detalle de los campos a corregir

### AC-003 — Gestión de indisponibilidad sobrevenida

- **Dado** que una expedición mostrada previamente al cliente se queda sin plazas antes de la confirmación
- **Cuando** el cliente intenta finalizar la compra
- **Entonces** el sistema debe informar de que ya no hay plazas disponibles y evitar la emisión del billete

### AC-004 — Consulta posterior del billete

- **Dado** que existe una reserva emitida
- **Cuando** el cliente introduce un localizador válido y el email asociado
- **Entonces** el sistema debe mostrar la reserva y permitir la descarga del billete electrónico

### AC-005 — Protección de datos en consulta operativa

- **Dado** que un usuario interno no autorizado accede a la consulta de una reserva
- **Cuando** visualiza los datos del pasajero
- **Entonces** el sistema debe limitar la visualización de los campos sensibles según su perfil funcional

---

## 18. Tests de alto nivel

> Casos de prueba de alto nivel derivados de los criterios de aceptación. No son tests unitarios; cubren el comportamiento observable del sistema desde fuera.

| ID | Tipo | Título | AC vinculado | Precondición del test | Datos de entrada | Resultado esperado | Resultado ejecución | Prioridad |
|----|------|--------|--------------|------------------------|------------------|-------------------|---------------------|-----------|
| TC-001 | funcional | Compra individual correcta | AC-001 | Existe expedición con 10 plazas disponibles | Origen Madrid, destino Segovia, fecha válida, 1 pasajero, pago aceptado | Reserva emitida, 1 plaza descontada, billete generado | pendiente | alta |
| TC-002 | negativo | Bloqueo por email inválido | AC-002 | Expedición seleccionada | Datos de pasajero con email mal formado | El sistema no deja continuar y muestra error de validación | pendiente | alta |
| TC-003 | borde | Compra de máximo permitido de pasajeros | AC-001 | Expedición con al menos 6 plazas disponibles | 6 pasajeros con datos completos | Compra completada correctamente y emisión múltiple asociada | pendiente | media |
| TC-004 | negativo | Indisponibilidad de plazas en confirmación | AC-003 | Expedición mostrada inicialmente con plazas | Intento de compra tras agotarse plazas | El sistema informa de no disponibilidad y no emite billete | pendiente | alta |
| TC-005 | funcional | Consulta de billete por localizador | AC-004 | Reserva existente emitida | Localizador correcto y email asociado | El sistema muestra y permite descargar el billete | pendiente | media |
| TC-006 | seguridad | Limitación de visualización para usuario interno | AC-005 | Usuario interno con perfil restringido | Consulta de reserva emitida | Los datos sensibles se muestran enmascarados o limitados | pendiente | alta |

> **Tipos de test:** `funcional` | `negativo` | `borde` | `rendimiento` | `seguridad` | `regresión`
>
> **Resultado ejecución:** `pendiente` | `pass` | `fail` | `bloqueado` | `no-aplica`

### Notas de testing

- **Entorno requerido:** Entorno de preproducción con catálogo de rutas y simulador de pago
- **Datos de prueba:** Estaciones válidas, expediciones con distinta ocupación, perfiles internos diferenciados y localizadores de prueba
- **Dependencias externas:** Sistema de disponibilidad, pasarela de pago simulada y servicio de generación de billetes
- **Responsable de ejecución:** Equipo QA funcional de Canal Digital

---

## 19. Riesgos y controles asociados

> Riesgos funcionales, operativos o de cumplimiento vinculados al requisito, junto con sus controles previstos.

| Riesgo ID | Descripción del riesgo | Probabilidad | Impacto | Control / mitigación | Evidencia esperada |
|-----------|------------------------|--------------|---------|----------------------|--------------------|
| RSK-001 | Sobreventa de plazas por desfase entre consulta y confirmación | media | alta | Revalidar disponibilidad en el momento de confirmar la compra | Registro de verificación final de plazas antes de emitir |
| RSK-002 | Emisión fallida tras cobro aceptado | baja | alta | Registrar operación pendiente de revisión y activar circuito de soporte prioritario | Incidencia registrada y trazabilidad de la operación |
| RSK-003 | Aplicación incorrecta de descuentos | media | media | Validar reglas tarifarias vigentes antes de confirmar importe final | Trazas funcionales de tarifa aplicada y regla invocada |
| RSK-004 | Exposición indebida de datos personales en consultas internas | baja | alta | Aplicar restricciones por perfil funcional y enmascaramiento de datos | Evidencia de perfiles y comportamiento validado en pruebas |
| RSK-005 | Pérdida de ventas por indisponibilidad del canal | media | alta | Monitorización funcional y plan de contingencia de atención al cliente | Alertas operativas y reporte de incidencias |

---

## 20. Observabilidad funcional

> Define qué evidencias funcionales debe producir el sistema para poder verificar comportamiento, operación y resultado de negocio.

### 20.1 Eventos funcionales a registrar

| Evento | Cuándo ocurre | Datos mínimos a registrar |
|--------|----------------|---------------------------|
| BUS_SEARCH_EXECUTED | Cuando el cliente ejecuta una búsqueda de expediciones | Fecha/hora, origen, destino, fecha de viaje, canal |
| BUS_TRIP_SELECTED | Cuando el cliente selecciona una expedición | Identificador de expedición, precio mostrado, canal |
| BUS_PURCHASE_CONFIRMED | Cuando el cliente confirma el resumen y pasa al pago | Resumen de compra, número de pasajeros, total |
| BUS_PAYMENT_ACCEPTED | Cuando el cobro es aceptado | Identificador de transacción, importe, referencia de reserva |
| BUS_TICKET_ISSUED | Cuando el billete queda emitido | Localizador, expedición, pasajeros, fecha/hora de emisión |
| BUS_PURCHASE_REJECTED | Cuando la compra no puede completarse | Código funcional, motivo, punto del flujo |

### 20.2 Alertas funcionales

| Alerta | Condición de activación | Destinatario / acción esperada |
|--------|--------------------------|--------------------------------|
| ALERT_NO_SEATS_SPIKE | Incremento anómalo de rechazos por falta de plazas | Operaciones revisa ocupación y consistencia de disponibilidad |
| ALERT_ISSUE_AFTER_PAYMENT | Se detecta cobro aceptado sin emisión completada | Atención al Cliente y Soporte funcional revisan y resuelven caso |
| ALERT_PAYMENT_REJECTION_RATE | Tasa de rechazos de pago por encima del umbral definido | Equipo de Canal Digital y proveedor de pagos analizan incidencia |

### 20.3 Métricas / KPIs de negocio

| Indicador | Fórmula / definición | Objetivo / umbral |
|-----------|----------------------|-------------------|
| Conversión de búsqueda a compra | Compras confirmadas / búsquedas ejecutadas | Superior al 15% |
| Tasa de emisión correcta | Billetes emitidos / pagos aceptados | Igual o superior al 99,8% |
| Tasa de abandono en pago | Compras iniciadas no completadas en fase de pago / compras iniciadas | Inferior al 8% |
| Incidencias postpago | Casos con cobro aceptado y emisión fallida / pagos aceptados | Inferior al 0,2% |

---

## 21. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Requisito de negocio | BRS-BUS-001 | Incrementar venta digital de plazas interurbanas |
| Épica | EPIC-BUS-01 | Digitalización del ciclo de venta de plazas |
| Caso de uso | UC-BUS-01 | Comprar billete de autobús interurbano |
| Historia de usuario | US-BUS-014 | Como cliente quiero comprar un billete para un trayecto concreto |
| Servicio | SVC-BUS-SALES | Servicio de reservas y emisión de billetes |
| ADR relacionado | ADR-022 | Uso de localizador único para reservas comerciales |
| Riesgo relacionado | RSK-001 | Sobreventa de plazas |
| Control relacionado | CTRL-BUS-01 | Revalidación de disponibilidad antes de emitir |
| Sesión refinamiento | REF-BUS-2026-03-05-01 | Refinamiento funcional con Comercial, Operaciones y Soporte |
| Tests de alto nivel | TC-001, TC-002, TC-003, TC-004, TC-005, TC-006 | Ver §18 |
| Enlace RTM | traceability/RTM.yaml#FRS-BUS-001 | Entrada de trazabilidad consolidada |

---

## 22. Dependencias

> Otros requisitos, servicios o sistemas de los que depende este requisito, incluyendo relaciones lógicas entre requisitos.

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Requisito FRS | FRS-BUS-002 | `depende-de` | Gestión de catálogo de rutas, estaciones y expediciones comercializables |
| Requisito FRS | FRS-BUS-003 | `depende-de` | Gestión de tarifas y descuentos |
| Requisito FRS | FRS-BUS-004 | `depende-de` | Consulta operativa de reservas y billetes |
| Servicio ext. | Sistema de disponibilidad de plazas | `consume` | Proporciona ocupación y capacidad disponible por expedición |
| Servicio ext. | Pasarela de pago | `consume` | Devuelve resultado funcional del cobro |
| Servicio ext. | Servicio de notificaciones | `publica` | Envía correo de confirmación con acceso al billete |

> **Relaciones entre requisitos:** `depende-de` | `extiende` | `especializa` | `reemplaza` | `conflicto`

---

## 23. Notas y decisiones abiertas

> Registro formal de cuestiones pendientes y su resolución esperada. Toda decisión cerrada debería enlazarse a evidencia o sesión de refinamiento cuando aplique.

| # | Nota / Pregunta abierta | Responsable | Estado | Fecha objetivo | Decisión tomada | Impacto | Evidencia / referencia |
|---|--------------------------|-------------|--------|----------------|-----------------|---------|------------------------|
| 1 | Definir si el límite de compra por operación debe mantenerse en 6 pasajeros o ampliarse a 10 | Dirección Comercial | resuelta | 2026-03-08 | Se mantiene el límite de 6 en la primera versión | Medio en ventas de grupos | Acta REF-BUS-2026-03-05-01 |
| 2 | Validar si algunas rutas premium requerirán asignación de asiento en el mismo flujo | Operaciones | en-análisis | 2026-03-20 | Pendiente para siguiente release | Alto para evolución del proceso | Backlog evolutivo BUS-R2 |
| 3 | Confirmar texto legal final de condiciones de transporte en la pantalla de confirmación | Legal | resuelta | 2026-03-09 | Aprobado texto estándar corporativo | Bajo | Documento LEG-BUS-2026-11 |
| 4 | Evaluar inclusión de bono recurrente para viajeros frecuentes | Dirección Comercial | descartada | 2026-03-15 | Se pospone a fase posterior | Bajo | Comité de priorización marzo 2026 |

> **Estados sugeridos:** `abierta` | `en-análisis` | `resuelta` | `descartada`

---

*Plantilla: `functional-requirement.template.md` v2.2.0 — Ejemplo completo de guía*
