# FRS-UBUS-001 — Consulta de informacion operativa por parada urbana

---

## Metadatos

| Campo                        | Valor |
|-----------------------------|-------|
| **ID**                      | FRS-UBUS-001 |
| **Versión**                 | 1.0.0 |
| **Estado**                  | en-revisión |
| **Estabilidad**             | estable |
| **Fecha**                   | 2026-03-10 |
| **Autor**                   | Oficina de Analisis Funcional |
| **Revisado por**            | pendiente de refinamiento |
| **Aprobado por**            | pendiente de refinamiento |
| **Módulo Funcional**        | Experiencia Digital del Viajero |
| **Submódulo Funcional**     | Informacion Operativa y Ticketing Urbano |
| **Épica**                   | EPIC-UBUS-01 — Autoservicio digital para informacion operativa y ticketing basico en autobus urbano |
| **Prioridad**               | alta |
| **Porcentaje de completud** | 80% |
| **Fuente**                  | docs/requirements/functional/Documento inicial de analisis.txt |
| **Sesión refinamiento**     | REF-ANA-UBUS-001-01 |
| **Enlace RTM**              | traceability/RTM.yaml#LINK-001, traceability/RTM.yaml#LINK-002 |
| **Método verificación**     | test |

---

## Historial de versiones

| Versión | Fecha      | Autor      | Cambios |
|---------|------------|------------|---------|
| 1.0.0   | 2026-03-10 | Oficina de Analisis Funcional | Version inicial derivada del documento ANA-UBUS-001 |

---

## 1. Descripción

El sistema debe permitir al usuario consultar una parada concreta del servicio urbano y visualizar informacion operativa relevante para decidir su desplazamiento. La respuesta debe incluir proximas llegadas previstas, incidencias activas que afecten a la parada o linea relacionada y datos basicos de accesibilidad cuando existan y hayan sido validados por el cliente.

---

## 2. Alcance y límites

### 2.1 Alcance incluido

- Consulta de una parada concreta del servicio urbano.
- Visualizacion de proximas llegadas previstas en lenguaje comprensible.
- Visualizacion de incidencias relevantes del servicio.
- Visualizacion de informacion basica de accesibilidad cuando exista.
- Distincion entre ausencia de incidencias e indisponibilidad de informacion.

### 2.2 Fuera de alcance

- Planificacion avanzada de rutas.
- Gestion de flota y mantenimiento.
- Compra o validacion de billetes.
- Integraciones multimodales avanzadas.

### 2.3 Límites del requisito

- Solo deben mostrarse datos operativos confirmados o validados.
- La semantica detallada de accesibilidad puede requerir refinamientos posteriores.

---

## 3. Evento disparador

- **Tipo de disparador:** `usuario`
- **Disparador principal:** El usuario consulta una parada concreta desde la aplicacion movil.
- **Canal / origen:** Aplicacion movil del servicio urbano.
- **Frecuencia esperada:** Alta durante uso cotidiano y franjas de mayor demanda.

---

## 4. Actores y stakeholders

### 4.1 Actores del sistema

| Actor | Tipo | Rol en este requisito |
|-------|------|-----------------------|
| Viajero urbano | `primario` | Consulta informacion operativa antes del viaje |
| Usuario con necesidades de accesibilidad | `primario` | Evalua si la parada o servicio presentan limitaciones relevantes |
| Aplicacion movil | `secundario` | Presenta informacion operativa al usuario |
| Origen de informacion operativa | `sistema-externo` | Aporta proximas llegadas, incidencias y datos basicos de accesibilidad |

### 4.2 Stakeholders interesados

| Stakeholder | Interés / Impacto |
|-------------|-------------------|
| Operador o autoridad de transporte urbano | Mejorar autoservicio y confianza en el canal digital |
| Personal de soporte o atencion | Reducir consultas repetitivas por informacion operativa |

---

## 5. Entradas y salidas del sistema

### 5.1 Entradas

| # | Nombre | Tipo / Formato | Origen | Obligatorio | Validaciones |
|---|--------|----------------|--------|-------------|--------------|
| 1 | identificador de parada | identificador | Usuario / app | Sí | Debe corresponder a una parada valida del servicio urbano |
| 2 | linea relacionada | identificador | Usuario / app | No | Si se informa, debe relacionarse con la parada consultada |

### 5.2 Salidas

| # | Nombre | Tipo / Formato | Destino | Descripción |
|---|--------|----------------|---------|-------------|
| 1 | proximas llegadas | lista | Usuario / app | Llegadas previstas para la parada consultada |
| 2 | incidencias activas | lista | Usuario / app | Incidencias relevantes para la parada o linea relacionada |
| 3 | informacion basica de accesibilidad | estructura o ausencia de dato | Usuario / app | Datos basicos visibles solo si son fiables |
| 4 | estado funcional de consulta | texto | Usuario / app | Diferencia consulta valida, sin incidencias o indisponibilidad |

---

## 6. Calidad y sensibilidad del dato

### 6.1 Clasificación de datos

| Dato / conjunto | Sensibilidad | Origen | Retención | Observaciones |
|-----------------|--------------|--------|-----------|---------------|
| Datos de parada y llegadas | `interno` | Origen operativo del cliente | pendiente de refinamiento | Su calidad condiciona la confianza del usuario |
| Incidencias publicables | `interno` | Operacion del servicio | pendiente de refinamiento | Deben seguir criterios homogeneos |
| Datos basicos de accesibilidad | `interno` | Cliente / catalogo funcional | pendiente de refinamiento | Solo visibles cuando exista validacion minima |

### 6.2 Reglas de calidad de datos

| ID | Dimensión | Regla / umbral |
|----|-----------|----------------|
| DQ-001 | completitud | Toda llegada visible debe ser comprensible para un usuario no tecnico |
| DQ-002 | validez | La parada consultada debe existir en la red urbana del cliente |
| DQ-003 | unicidad | No deben mostrarse registros duplicados como si fueran llegadas distintas |
| DQ-004 | consistencia | La ausencia de incidencias no debe mostrarse como indisponibilidad |

### 6.3 Consideraciones funcionales sobre datos

- No debe mostrarse informacion ambigua o no confirmada como definitiva.
- La accesibilidad solo debe publicarse cuando el cliente pueda sostener su calidad minima.

---

## 7. Precondiciones

- Existe una parada valida del servicio urbano.
- Existe algun origen de informacion operativa sobre proximas llegadas e incidencias.

---

## 8. Postcondiciones

- El usuario dispone de informacion operativa comprensible para decidir su viaje.
- La consulta deja evidencia funcional suficiente para seguimiento posterior.

---

## 9. Supuestos

- El cliente dispone de identificadores estables de parada y linea.
- La aplicacion movil es el canal prioritario en la primera fase.

---

## 10. Restricciones

| Tipo | Restricción | Impacto / Justificación |
|------|-------------|-------------------------|
| `organizativa` | Solo debe mostrarse accesibilidad cuando exista calidad minima sostenida por el cliente | Evita publicar informacion poco fiable |
| `proceso` | Debe distinguirse ausencia de incidencias frente a indisponibilidad de informacion | Reduce interpretaciones incorrectas |
| `temporal` | La primera fase debe centrarse en capacidades de alto valor y baja ambiguedad | Limita alcance inicial |
| `seguridad` | No debe exponerse informacion operativa no relevante para el viajero | Mantiene foco en dato visible y comprensible |

---

## 11. Frecuencia, volumetría y criticidad operativa

| Aspecto | Valor |
|---------|-------|
| **Frecuencia esperada** | Alta |
| **Volumen estimado** | pendiente de refinamiento |
| **Picos esperados** | En periodos de mayor uso del servicio urbano |
| **Ventana operativa** | Durante el servicio urbano y periodos de mayor uso |
| **Criticidad de negocio** | `alta` |
| **Impacto por indisponibilidad** | Aumenta incertidumbre del usuario y consultas a soporte |

---

## 12. Flujo principal

1. El usuario consulta una parada concreta desde la app movil.
2. El sistema recupera la informacion operativa disponible para esa parada.
3. El sistema organiza la respuesta en proximas llegadas, incidencias y accesibilidad basica cuando aplique.
4. La app muestra la informacion con mensajes claros y comprensibles.

---

## 13. Flujos alternativos

### 13.1 Consulta sin incidencias activas

- **Condición de activación:** No existen incidencias activas que afecten a la parada o linea relacionada.
- **Pasos:**
  1. El sistema devuelve una respuesta valida sin incidencias activas.
  2. La app informa expresamente que no existen incidencias activas.

### 13.2 Consulta con accesibilidad no disponible

- **Condición de activación:** No existe informacion de accesibilidad validada o mantenida por el cliente.
- **Pasos:**
  1. El sistema omite la informacion no fiable o la presenta como no disponible.
  2. La app mantiene una comunicacion neutra y no concluyente.

---

## 14. Flujos de excepción

### 14.1 Informacion operativa no disponible

- **Condición de activación:** El sistema no puede obtener informacion operativa util en ese momento.
- **Respuesta del sistema:** El usuario recibe un mensaje claro de indisponibilidad sin datos ambiguos.
- **Código de error (si aplica):** pendiente de refinamiento

---

## 15. Reglas de negocio

| ID | Regla | Fuente / Referencia |
|----|-------|---------------------|
| BR-001 | La solucion debe permitir consultar una parada concreta del servicio urbano | RFN-001 |
| BR-002 | La solucion debe mostrar las proximas llegadas previstas para la parada consultada | RFN-002 |
| BR-003 | Debe diferenciarse ausencia de incidencias frente a informacion no disponible | RFN-005 |
| BR-004 | La accesibilidad solo debe mostrarse cuando exista y haya sido validada por el cliente | RFN-006 |

---

## 16. Requisitos no funcionales asociados

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| RNF-001 | rendimiento | La experiencia debe ser suficientemente rapida para uso cotidiano | pendiente de refinamiento |
| RNF-002 | disponibilidad | La funcionalidad debe estar disponible durante el servicio urbano y periodos de mayor uso | pendiente de refinamiento |
| RNF-004 | usabilidad | La informacion debe inspirar confianza y coherencia | Validacion funcional por negocio |

---

## 17. Criterios de aceptación

### AC-001 — Mostrar proximas llegadas comprensibles

- **Dado** que existe una parada valida del servicio urbano
- **Cuando** el usuario consulta esa parada
- **Entonces** la solucion debe mostrar las proximas llegadas previstas de forma comprensible

### AC-002 — Mostrar incidencias relevantes activas

- **Dado** que existen incidencias activas que afectan a la parada o a una linea relacionada
- **Cuando** el usuario consulta la parada
- **Entonces** la solucion debe informar esas incidencias de forma comprensible

### AC-003 — Diferenciar ausencia de incidencias e indisponibilidad

- **Dado** que no existen incidencias activas o la informacion no esta disponible
- **Cuando** el usuario consulta la parada
- **Entonces** la solucion debe distinguir claramente ambos escenarios

### AC-004 — Mostrar accesibilidad basica validada

- **Dado** que existe informacion basica de accesibilidad validada por el cliente
- **Cuando** el usuario consulta la parada
- **Entonces** la solucion debe mostrar esa informacion de forma clara

---

## 18. Tests de alto nivel

| ID | Tipo | Título | AC vinculado | US derivada objetivo | Riesgo cubierto | Precondición del test | Datos de entrada | Resultado esperado | Resultado ejecución | Prioridad |
|----|------|--------|--------------|----------------------|-----------------|------------------------|------------------|-------------------|---------------------|-----------|
| TC-UBUS-001 | funcional | Consulta de proximas llegadas por parada valida | AC-001 | US-UBUS-001 | — | Existe parada valida | parada valida | Se muestran proximas llegadas comprensibles | pendiente | alta |
| TC-UBUS-002 | funcional | Visualizacion de incidencias activas relevantes | AC-002 | US-UBUS-002 | RSK-001 | Existen incidencias activas publicables | parada con incidencia | Se muestran incidencias relevantes | pendiente | alta |
| TC-UBUS-003 | borde | Diferenciacion entre ausencia de incidencias e indisponibilidad | AC-003 | US-UBUS-002 | RSK-001 | Existen escenarios comparables | parada sin incidencias / parada sin datos | Se distingue cada escenario | pendiente | alta |
| TC-UBUS-004 | funcional | Visualizacion de accesibilidad basica validada | AC-004 | US-UBUS-002 | RSK-002 | Existe dato de accesibilidad validado | parada con accesibilidad | Se muestra accesibilidad clara y neutra | pendiente | media |

### Notas de testing

- **Entorno requerido:** pendiente de refinamiento
- **Datos de prueba:** Paradas con y sin incidencias, y con y sin accesibilidad validada
- **Dependencias externas:** Origen de informacion operativa del cliente
- **Responsable de ejecución:** pendiente de refinamiento

---

## 19. Riesgos y controles asociados

| Riesgo ID | Descripción del riesgo | Probabilidad | Impacto | Control / mitigación | Evidencia esperada |
|-----------|------------------------|--------------|---------|----------------------|--------------------|
| RSK-001 | La informacion operativa o de incidencias puede ser incompleta, dispersa o dificil de interpretar | media | alta | Mensajes claros, distincion de estados y publicacion solo de informacion relevante | Evidencia funcional en AC-002, AC-003 y tests asociados |
| RSK-002 | La informacion de accesibilidad puede no ser suficientemente fiable | media | alta | Mostrar accesibilidad solo cuando exista y haya sido validada por el cliente | Evidencia funcional en AC-004 y cobertura de riesgo en US-UBUS-002 |

---

## 20. Observabilidad funcional

### 20.1 Eventos funcionales a registrar

| Evento | Cuándo ocurre | Datos mínimos a registrar |
|--------|----------------|---------------------------|
| STOP_OPERATIONAL_INFO_REQUESTED | Al iniciar consulta de parada | identificador de parada, timestamp |
| STOP_OPERATIONAL_INFO_RETURNED | Al devolver respuesta valida | identificador de parada, presencia de incidencias, presencia de accesibilidad |

### 20.2 Alertas funcionales

| Alerta | Condición de activación | Destinatario / acción esperada |
|--------|--------------------------|--------------------------------|
| ALERT-OPINFO-DEGRADED | Incremento de consultas sin informacion operativa util | Revision funcional y operativa de origen de datos |

### 20.3 Métricas / KPIs de negocio

| Indicador | Fórmula / definición | Objetivo / umbral |
|-----------|----------------------|-------------------|
| KPI-OPINFO-01 | Consultas operativas satisfactorias / consultas operativas iniciadas | pendiente de refinamiento |

---

## 21. Trazabilidad

| Artefacto | ID / Referencia | Descripción |
|-----------|------------------|-------------|
| Requisito de negocio | BGS-UBUS-01 | Mejorar el autoservicio digital del viajero urbano |
| Épica | EPIC-UBUS-01 | Autoservicio digital para informacion operativa y ticketing basico en autobus urbano |
| Historias de usuario derivadas | US-UBUS-001, US-UBUS-002 | Historias derivadas del requisito |
| Servicio | pendiente de refinamiento | No se identifica servicio concreto en el documento fuente |
| ADR relacionado | pendiente de refinamiento | No identificado en esta fase |
| Riesgo relacionado | RSK-001, RSK-002 | Riesgos funcionales asociados |
| Control relacionado | Controles descritos en §19 | Controles funcionales asociados al requisito |
| Sesión refinamiento | REF-ANA-UBUS-001-01 | Refinamiento inicial derivado del documento fuente |
| Tests de alto nivel | TC-UBUS-001, TC-UBUS-002, TC-UBUS-003, TC-UBUS-004 | Ver §18 |
| Cobertura funcional derivada | US-UBUS-001, US-UBUS-002 + TC-UBUS-* | Debe continuar en US con AC y Gherkin |
| Enlace RTM | LINK-001, LINK-002 | Entradas en `traceability/RTM.yaml` |

---

## 22. Dependencias

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Requisito FRS | FRS-UBUS-002 | `relacionada-con` | Comparte contexto funcional general del autoservicio digital del viajero |
| Servicio ext. | Origen de informacion operativa | `consume` | Proporciona llegadas, incidencias y accesibilidad basica cuando exista |

---

## 23. Notas y decisiones abiertas

| # | Nota / Pregunta abierta | Responsable | Estado | Fecha objetivo | Decisión tomada | Impacto | Evidencia / referencia |
|---|--------------------------|-------------|--------|----------------|-----------------|---------|------------------------|
| 1 | Confirmar categorias de incidencias visibles al viajero en primera version | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Alto | Documento inicial de analisis.txt §12 |
| 2 | Confirmar que informacion minima de accesibilidad puede publicarse con fiabilidad | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Alto | Documento inicial de analisis.txt §12 |

---

*Plantilla: `functional-requirement.template.md` v2.3.0 — AgentProjectFromScratch v1.2.2*
