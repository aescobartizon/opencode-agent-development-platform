# EPIC-UBUS-01 — Autoservicio digital para informacion operativa y ticketing basico en autobus urbano

---

## Metadatos

| Campo                        | Valor |
|-----------------------------|-------|
| **ID**                      | EPIC-UBUS-01 |
| **Versión**                 | 1.0.0 |
| **Estado**                  | en-revisión |
| **Estabilidad**             | estable |
| **Fecha**                   | 2026-03-10 |
| **Autor**                   | Oficina de Analisis Funcional |
| **Revisado por**            | pendiente de refinamiento |
| **Aprobado por**            | pendiente de refinamiento |
| **Módulo Funcional**        | Experiencia Digital del Viajero |
| **Submódulo Funcional**     | Informacion Operativa y Ticketing Urbano |
| **Prioridad**               | crítica |
| **Porcentaje de completud** | 78% |
| **Fuente**                  | docs/requirements/functional/Documento inicial de analisis.txt |
| **Sesión refinamiento**     | REF-ANA-UBUS-001-01 |
| **Enlace RTM**              | traceability/RTM.yaml#LINK-001, traceability/RTM.yaml#LINK-002, traceability/RTM.yaml#LINK-003, traceability/RTM.yaml#LINK-004 |
| **Objetivo de negocio**     | BGS-UBUS-01 — Mejorar el autoservicio digital del viajero urbano |

---

## Historial de versiones

| Versión | Fecha      | Autor      | Cambios |
|---------|------------|------------|---------|
| 1.0.0   | 2026-03-10 | Oficina de Analisis Funcional | Version inicial derivada del documento ANA-UBUS-001 |

---

## 1. Propósito de la épica

Esta epica estructura la primera fase funcional de autoservicio digital para el viajero urbano. Su proposito es permitir que el ciudadano resuelva desde el movil dos necesidades de alto valor: conocer informacion operativa relevante antes del viaje y utilizar un billete digital sencillo para acceder al autobus.

---

## 2. Contexto de negocio

El documento fuente describe una experiencia digital actual no integrada para el usuario del autobus municipal. El viajero tiene dificultades para conocer proximas llegadas, entender incidencias y disponer de un mecanismo simple para comprar y usar un billete digital.

El cliente busca mejorar la experiencia del ciudadano, aumentar el uso del canal digital y reducir la dependencia de interacciones presenciales o consultas repetitivas a soporte.

---

## 3. Objetivo de negocio

Mejorar el autoservicio digital del viajero urbano mediante una experiencia movil sencilla que permita consultar informacion operativa relevante, reducir la incertidumbre antes del viaje, facilitar la compra de un billete digital sencillo y agilizar el acceso al autobus.

---

## 4. Alcance

### 4.1 Incluido en esta épica

- Consulta de proximas llegadas por parada.
- Consulta de incidencias relevantes del servicio.
- Visualizacion de informacion basica de accesibilidad cuando exista y sea fiable.
- Compra de billete sencillo digital desde la aplicacion movil.
- Consulta posterior del billete y visualizacion de su estado funcional.
- Activacion del billete antes del embarque cuando el modelo operativo lo requiera.

### 4.2 Fuera de alcance

- Planificacion avanzada de rutas y optimizacion de horarios.
- Gestion de flota y mantenimiento de vehiculos.
- Gestion completa de abonos complejos.
- Integraciones multimodales avanzadas y fidelizacion.

### 4.3 Límites

- La primera fase se centra en canal movil.
- Solo debe mostrarse accesibilidad cuando exista calidad minima sostenida por el cliente.
- La regla exacta de activacion del billete sigue pendiente de refinamiento.

---

## 5. Problema que resuelve

La experiencia digital actual no resuelve de forma integrada las necesidades mas frecuentes del viajero. Esto genera incertidumbre sobre la llegada del autobus, dudas ante incidencias del servicio y confusion sobre compra, estado y uso del billete digital.

---

## 6. Valor esperado

| Tipo de valor     | Descripción |
|-------------------|-------------|
| Negocio           | Incremento del uso del canal digital y mejor percepcion del servicio urbano |
| Operativo         | Menos consultas repetitivas a soporte sobre llegadas, incidencias y billetes |
| Cliente / usuario | Menor friccion y mas confianza antes y durante el acceso al autobus |
| Cumplimiento      | Base funcional trazable para evolucion posterior del producto |

---

## 7. Stakeholders

| Stakeholder | Interés / expectativa | Impacto |
|-------------|------------------------|---------|
| Operador o autoridad de transporte urbano | Mejorar autoservicio y adopcion del canal digital | Alto |
| Viajero urbano habitual | Rapidez, simplicidad y fiabilidad en uso cotidiano | Alto |
| Viajero ocasional | Experiencia clara y guiada | Alto |
| Usuario con necesidades de accesibilidad | Conocer limitaciones relevantes antes del desplazamiento | Alto |
| Personal de soporte o atencion | Reducir ambiguedad funcional y consultas manuales | Medio |

---

## 8. Capacidades funcionales esperadas

| ID | Capacidad | Descripción |
|----|-----------|-------------|
| CAP-001 | Informacion operativa por parada | Consultar llegadas, incidencias y accesibilidad basica asociadas a una parada o linea relacionada |
| CAP-002 | Compra digital de billete sencillo | Comprar un billete sencillo digital y recibir confirmacion clara del resultado |
| CAP-003 | Uso funcional del billete | Consultar el billete adquirido, entender su estado y activarlo cuando proceda |

---

## 9. Criterios de éxito de la épica

| ID | Criterio de éxito | Métrica / evidencia |
|----|-------------------|---------------------|
| ESC-001 | El viajero puede resolver desde la app la consulta operativa basica del servicio | Evidencia funcional en FRS-UBUS-001 y US derivadas |
| ESC-002 | El viajero puede comprar un billete sencillo digital y entender su estado | Evidencia funcional en FRS-UBUS-002 y US derivadas |

---

## 10. Indicadores / KPIs asociados

| KPI | Definición | Objetivo |
|-----|------------|----------|
| KPI-UBUS-01 | Consultas operativas completadas / consultas operativas iniciadas | pendiente de refinamiento |
| KPI-UBUS-02 | Compras de billete completadas / intentos de compra | pendiente de refinamiento |

---

## 11. Dependencias de alto nivel

| Tipo | Dependencia | Relación | Descripción |
|------|-------------|----------|-------------|
| `proceso` | Publicacion de informacion operativa al viajero | `depende-de` | Las incidencias y datos de accesibilidad deben tener criterios de publicacion homogéneos |
| `sistema` | Origen de informacion operativa | `depende-de` | Debe existir una fuente para proximas llegadas e incidencias |
| `organización` | Modelo operativo de activacion de billete | `condiciona` | Determina si la activacion es obligatoria, opcional o no aplica |

---

## 12. Riesgos y supuestos

### 12.1 Riesgos

| Riesgo ID | Descripción | Probabilidad | Impacto | Mitigación |
|-----------|-------------|--------------|---------|------------|
| ERSK-001 | La informacion operativa no tiene calidad suficiente para generar confianza | media | alta | Diferenciar ausencia de incidencias, indisponibilidad e informacion validada |
| ERSK-002 | El usuario no entiende el estado real del billete ni el momento correcto de activacion | media | alta | Mantener mensajes claros y cerrar reglas funcionales abiertas antes de aprobacion |

### 12.2 Supuestos

- Existe una red urbana con identificadores estables de parada y linea.
- Existe algun origen de informacion operativa sobre proximas llegadas e incidencias.
- El canal movil es prioritario para la primera fase del producto.
- El billete sencillo digital es el producto de ticketing inicial.

---

## 13. Requisitos funcionales candidatos asociados

| FRS ID | Título | Estado | Observaciones |
|--------|--------|--------|---------------|
| FRS-UBUS-001 | Consulta de informacion operativa por parada urbana | en-revisión | Cubre llegadas, incidencias y accesibilidad basica |
| FRS-UBUS-002 | Compra, consulta y activacion de billete digital sencillo | en-revisión | Cubre compra, evidencia de compra, estado y activacion |

---

## 14. Historias de usuario candidatas

| US ID | Título | Estado | Prioridad | Observaciones |
|-------|--------|--------|-----------|---------------|
| US-UBUS-001 | Como viajero quiero consultar proximas llegadas por parada para reducir incertidumbre antes del viaje | en-refinamiento | alta | Historia principal de llegadas |
| US-UBUS-002 | Como viajero quiero ver incidencias y accesibilidad basica para planificar mejor mi desplazamiento | en-refinamiento | alta | Requiere cierre de categorias visibles |
| US-UBUS-003 | Como viajero quiero comprar un billete sencillo digital para acceder al servicio sin depender de un canal presencial | en-refinamiento | crítica | Requiere detalle posterior de pago |
| US-UBUS-004 | Como viajero quiero consultar el estado de mi billete y activarlo cuando proceda para usarlo correctamente | en-refinamiento | crítica | Requiere cerrar reglas temporales de activacion |

---

## 15. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Objetivo de negocio | BGS-UBUS-01 | Mejorar el autoservicio digital del viajero urbano |
| Módulo funcional | Experiencia Digital del Viajero | Dominio funcional principal |
| Submódulo funcional | Informacion Operativa y Ticketing Urbano | Ambito funcional inicial del producto |
| Requisitos funcionales | FRS-UBUS-001, FRS-UBUS-002 | Requisitos vinculados a la epica |
| Historias de usuario | US-UBUS-001, US-UBUS-002, US-UBUS-003, US-UBUS-004 | Historias derivadas |
| Riesgos relacionados | ERSK-001, ERSK-002 | Riesgos asociados |
| Tests derivados agregados | GT-001 a GT-003 en cada US derivada | Cobertura agregada de comportamiento observable |
| Enlace RTM | LINK-001, LINK-002, LINK-003, LINK-004 | Entradas en `traceability/RTM.yaml` |

---

## 16. Notas y decisiones abiertas

| # | Nota / pregunta | Responsable | Estado | Fecha objetivo | Decisión tomada | Evidencia |
|---|------------------|-------------|--------|----------------|-----------------|----------|
| 1 | Definir que categorias de incidencias se muestran al viajero desde la primera version | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Documento inicial de analisis.txt §12 |
| 2 | Confirmar que informacion minima de accesibilidad puede publicarse con fiabilidad | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Documento inicial de analisis.txt §12 |
| 3 | Cerrar si la activacion del billete es obligatoria, opcional o automatica y su ventana temporal | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Documento inicial de analisis.txt §12 |

---

*Plantilla: `epic.template.md` v1.1.0*
