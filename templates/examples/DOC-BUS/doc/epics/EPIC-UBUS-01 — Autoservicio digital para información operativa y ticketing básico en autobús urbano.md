# EPIC-UBUS-01 — Autoservicio digital para información operativa y ticketing básico en autobús urbano

---

## Metadatos

| Campo                        | Valor |
|-----------------------------|-------|
| **ID**                      | EPIC-UBUS-01 |
| **Versión**                 | 1.0.0 |
| **Estado**                  | en-revisión |
| **Estabilidad**             | estable |
| **Fecha**                   | 2026-03-10 |
| **Autor**                   | Oficina de Análisis Funcional |
| **Revisado por**            | Responsable de Producto de Movilidad Urbana |
| **Aprobado por**            | Dirección de Servicios Digitales |
| **Módulo Funcional**        | Experiencia Digital del Viajero |
| **Submódulo Funcional**     | Información Operativa y Ticketing Urbano |
| **Prioridad**               | crítica |
| **Porcentaje de completud** | 78% |
| **Fuente**                  | analysis/urban-bus-initial-analysis.txt |
| **Sesión refinamiento**     | REF-UBUS-2026-03-10-01 |
| **Enlace RTM**              | traceability/RTM.yaml#EPIC-UBUS-01 |
| **Objetivo de negocio**     | BGS-UBUS-01 — Incrementar el autoservicio digital del viajero urbano |

> **Estados válidos:** `borrador` | `en-revisión` | `aprobado` | `rechazado` | `obsoleto`
>
> **Estabilidad válida:** `estable` | `volátil` | `en-cambio`
>
> **Prioridades válidas:** `crítica` | `alta` | `media` | `baja`
>
> **Porcentaje de completud:** valor entre `0%` y `100%`

---

## Historial de versiones

| Versión | Fecha | Autor | Cambios |
|---------|-------|-------|---------|
| 1.0.0 | 2026-03-10 | Oficina de Análisis Funcional | Versión inicial |

---

## 1. Propósito de la épica

Esta épica tiene como propósito habilitar una experiencia digital sencilla y útil para el viajero de autobús urbano, permitiéndole consultar información operativa relevante del servicio y utilizar un billete digital básico desde el canal móvil.

La épica existe para resolver dos necesidades centrales del usuario urbano: reducir la incertidumbre antes del viaje y facilitar el acceso al servicio sin depender exclusivamente de interacciones presenciales o medios físicos tradicionales.

---

## 2. Contexto de negocio

El cliente, como operador o autoridad de transporte urbano, quiere reforzar el autoservicio digital del ciudadano en el uso cotidiano del autobús municipal. Actualmente, la experiencia del usuario presenta limitaciones en dos momentos clave del viaje.

El primero es la fase previa al desplazamiento, en la que el usuario necesita saber cuándo llegará su autobús, si hay incidencias que afectan a la parada o la línea, y si existe alguna limitación relevante de accesibilidad. El segundo es la fase de acceso al servicio, en la que el viajero necesita comprar y utilizar un billete digital simple desde el móvil de forma clara y fiable.

La necesidad de negocio consiste en ofrecer una experiencia móvil integrada, comprensible y preparada para evolucionar posteriormente a funcionalidades de mayor alcance.

---

## 3. Objetivo de negocio

Mejorar el autoservicio digital del viajero urbano mediante una experiencia móvil que permita:

- consultar información operativa útil y comprensible del servicio de autobuses urbanos,
- reducir la incertidumbre previa al viaje,
- facilitar la compra y uso de un billete sencillo digital,
- agilizar el acceso al autobús,
- aumentar la confianza del ciudadano en el canal digital del servicio.

---

## 4. Alcance

### 4.1 Incluido en esta épica

- Consulta de próximas llegadas por parada urbana.
- Visualización de incidencias operativas relevantes para el viajero.
- Visualización de información básica de accesibilidad cuando esté disponible.
- Compra de billete sencillo digital desde la aplicación móvil.
- Consulta del estado funcional del billete adquirido.
- Activación del billete antes del embarque cuando el modelo operativo del cliente lo requiera.

### 4.2 Fuera de alcance

- Planificación avanzada de rutas y alternativas multimodales.
- Gestión de flota, mantenimiento y operación interna del servicio.
- Gestión completa de abonos complejos o productos de larga duración.
- Programas de fidelización.
- Integraciones complejas con otros medios de transporte en esta fase inicial.

### 4.3 Límites

- La primera versión se centra en canal móvil.
- El producto de ticketing inicial será el billete sencillo digital.
- La definición detallada de ciertas categorías de accesibilidad e incidencias puede requerir refinamiento posterior.
- La validación operativa a bordo queda fuera de detalle funcional en esta fase, más allá del estado y evidencia digital del billete.

---

## 5. Problema que resuelve

Actualmente el viajero urbano no dispone de una experiencia digital suficientemente clara, centralizada y confiable para resolver dos preguntas esenciales del uso cotidiano del autobús:

1. si el servicio va a llegar en un tiempo útil y en qué condiciones operativas,
2. y si dispone de un billete digital válido y comprensible para acceder al servicio.

Esta situación genera incertidumbre, fricción en el uso del canal móvil, consultas repetitivas a personal de soporte y una percepción de experiencia fragmentada.

---

## 6. Valor esperado

| Tipo de valor | Descripción |
|---------------|-------------|
| Negocio | Incremento del uso del canal digital y mejora de la percepción del servicio urbano |
| Operativo | Reducción de consultas repetitivas sobre llegadas, incidencias y estado del billete |
| Cliente / usuario | Menor incertidumbre y experiencia más simple antes y durante el acceso al autobús |
| Cumplimiento | Base documental trazable y preparada para evolución controlada del producto |

---

## 7. Stakeholders

| Stakeholder | Interés / expectativa | Impacto |
|-------------|------------------------|---------|
| Dirección de Servicios Digitales | Consolidar una experiencia móvil de alto valor para el ciudadano | Alto |
| Operaciones Urbanas | Publicar información operativa útil, coherente y sostenible | Alto |
| Atención al Cliente | Reducir consultas manuales y ambigüedad funcional | Medio |
| Equipo de Recaudación / Ticketing | Garantizar compra y uso comprensible del billete digital | Alto |
| Ciudadanía / usuario final | Disponer de información fiable y acceso sencillo al servicio | Alto |

---

## 8. Capacidades funcionales esperadas

| ID | Capacidad | Descripción |
|----|-----------|-------------|
| CAP-001 | Consulta operativa por parada | Permitir al viajero consultar próximas llegadas en una parada concreta |
| CAP-002 | Gestión visible de incidencias | Mostrar incidencias relevantes del servicio que afecten al viaje |
| CAP-003 | Información básica de accesibilidad | Mostrar indicadores básicos de accesibilidad cuando existan y estén validados |
| CAP-004 | Compra de billete sencillo digital | Permitir adquirir un billete simple desde la app |
| CAP-005 | Estado y activación del billete | Permitir visualizar el estado del billete y activarlo antes del uso |

---

## 9. Criterios de éxito de la épica

| ID | Criterio de éxito | Métrica / evidencia |
|----|-------------------|---------------------|
| ESC-001 | El usuario puede resolver desde la app cuándo llegará el autobús y si existen incidencias relevantes | Evidencia funcional validada en historias y tests Gherkin |
| ESC-002 | El usuario puede completar la compra de un billete sencillo digital de forma autónoma | Evidencia funcional de compra y estado del billete |
| ESC-003 | El usuario entiende el estado funcional del billete y cuándo puede usarlo | Validación funcional y refinamiento de mensajes |
| ESC-004 | El canal digital reduce fricción y consultas repetitivas en escenarios básicos | Seguimiento de uso y feedback funcional del negocio |

---

## 10. Indicadores / KPIs asociados

| KPI | Definición | Objetivo |
|-----|------------|----------|
| KPI-UBUS-01 | Consultas operativas exitosas / consultas totales | > 95% |
| KPI-UBUS-02 | Compras correctas de billete / intentos de compra | > 97% |
| KPI-UBUS-03 | Activaciones correctas / billetes activables | > 98% |
| KPI-UBUS-04 | Incidencias correctamente clasificadas / incidencias publicadas | > 95% |

---

## 11. Dependencias de alto nivel

| Tipo | Dependencia | Relación | Descripción |
|------|-------------|----------|-------------|
| `sistema` | Backend de información operativa urbana | `depende-de` | Aporta próximas llegadas e incidencias activas |
| `sistema` | Plataforma de pagos | `depende-de` | Permite confirmar la compra del billete |
| `sistema` | Backend de ticketing | `depende-de` | Emite y activa el billete digital |
| `organización` | Operaciones Urbanas | `condiciona` | Define catálogo de incidencias y accesibilidad visible |
| `organización` | Producto / Negocio | `condiciona` | Debe cerrar reglas de activación del billete |

---

## 12. Riesgos y supuestos

### 12.1 Riesgos

| Riesgo ID | Descripción | Probabilidad | Impacto | Mitigación |
|-----------|-------------|--------------|---------|------------|
| ERSK-001 | La información de llegadas no tiene la calidad suficiente para generar confianza | media | alta | Establecer reglas de refresco, observabilidad y comunicación clara |
| ERSK-002 | Las incidencias visibles al usuario no están suficientemente normalizadas | alta | alta | Refinar catálogo funcional con Operaciones Urbanas |
| ERSK-003 | El usuario no entiende el estado real de su billete digital | media | alta | Diseñar estados y mensajes claros de compra, emisión y activación |
| ERSK-004 | No se cierra a tiempo la regla de activación del billete | media | alta | Mantener refinamiento específico antes de aprobación final |

### 12.2 Supuestos

- Existe una red urbana con identificadores estables de parada y línea.
- El canal móvil será el canal prioritario en la primera fase.
- Existe una fuente operativa de información sobre llegadas e incidencias.
- El billete sencillo digital es el producto adecuado para iniciar la evolución del ticketing móvil.
- Parte de la semántica de accesibilidad requerirá refinamiento posterior.

---

## 13. Requisitos funcionales candidatos asociados

| FRS ID | Título | Estado | Observaciones |
|--------|--------|--------|---------------|
| FRS-UBUS-001 | Consulta de próximas llegadas e incidencias por parada urbana | en-revisión | Primer bloque funcional de información operativa |
| FRS-UBUS-002 | Compra y activación de billete digital urbano | en-revisión | Segundo bloque funcional de ticketing básico |

---

## 14. Historias de usuario candidatas

| US ID | Título | Estado | Prioridad | Observaciones |
|-------|--------|--------|-----------|---------------|
| US-UBUS-001 | Como viajero quiero consultar próximas llegadas por parada para decidir si espero o cambio de ruta | lista | alta | Historia funcional madura |
| US-UBUS-002 | Como viajero quiero ver incidencias y accesibilidad de parada y línea para planificar mejor mi viaje | en-refinamiento | media | Quedan decisiones abiertas sobre taxonomía de accesibilidad |
| US-UBUS-003 | Como viajero quiero comprar un billete sencillo digital para no depender de pago físico al subir | lista | crítica | Historia principal de compra |
| US-UBUS-004 | Como viajero quiero activar mi billete antes de embarcar para validarlo correctamente en el autobús | en-refinamiento | crítica | Quedan reglas temporales de activación por cerrar |

---

## 15. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Objetivo de negocio | BGS-UBUS-01 | Incrementar el autoservicio digital del viajero urbano |
| Módulo funcional | Experiencia Digital del Viajero | Dominio funcional principal |
| Submódulo funcional | Información Operativa y Ticketing Urbano | Ámbito funcional de información operativa y ticketing básico |
| Requisitos funcionales | FRS-UBUS-001, FRS-UBUS-002 | Requisitos vinculados a la épica |
| Historias de usuario | US-UBUS-001, US-UBUS-002, US-UBUS-003, US-UBUS-004 | Historias derivadas |
| Riesgos relacionados | ERSK-001, ERSK-002, ERSK-003, ERSK-004 | Riesgos asociados |
| Tests relacionados | GT y TC derivados de FRS y US | Validación agregada de la épica |
| Enlace RTM | traceability/RTM.yaml#EPIC-UBUS-01 | Entrada en `traceability/RTM.yaml` |

---

## 16. Notas y decisiones abiertas

| # | Nota / pregunta | Responsable | Estado | Fecha objetivo | Decisión tomada | Evidencia |
|---|------------------|-------------|--------|----------------|-----------------|----------|
| 1 | Definir catálogo inicial de incidencias visibles al viajero | Operaciones Urbanas | abierta | 2026-03-18 | — | REF-UBUS-2026-03-10-01 |
| 2 | Confirmar semántica mínima de accesibilidad publicable | Operaciones Urbanas | abierta | 2026-03-18 | — | REF-UBUS-2026-03-10-01 |
| 3 | Cerrar ventana funcional entre compra y activación del billete | Producto Ticketing | abierta | 2026-03-20 | — | REF-UBUS-2026-03-10-01 |

---

*Plantilla: `epic.template.md` v1.1.0*
