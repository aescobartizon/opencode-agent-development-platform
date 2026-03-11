# US-UBUS-002 — Como viajero quiero ver incidencias y accesibilidad basica para planificar mejor mi desplazamiento

---

## Metadatos

| Campo                        | Valor |
|-----------------------------|-------|
| **ID**                      | US-UBUS-002 |
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
| **FRS asociado principal**  | FRS-UBUS-001 — Consulta de informacion operativa por parada urbana |
| **Prioridad**               | alta |
| **Tipo de historia**        | funcional |
| **Porcentaje de completud** | 72% |
| **Fuente**                  | docs/requirements/functional/Documento inicial de analisis.txt |
| **Sesión refinamiento**     | REF-ANA-UBUS-001-01 |
| **Enlace RTM**              | traceability/RTM.yaml#LINK-002 |
| **Método verificación**     | test |

---

## Historial de versiones

| Versión | Fecha      | Autor      | Cambios |
|---------|------------|------------|---------|
| 1.0.0   | 2026-03-10 | Oficina de Analisis Funcional | Version inicial derivada del documento ANA-UBUS-001 |

---

## 1. Historia de usuario

**Como** viajero urbano o usuario con necesidades de accesibilidad  
**Quiero** ver incidencias relevantes y accesibilidad basica de la parada o servicio  
**Para** planificar mejor mi desplazamiento y evitar sorpresas antes del viaje

---

## 2. Objetivo funcional

Permitir al usuario identificar incidencias activas relevantes y conocer informacion basica de accesibilidad cuando exista y sea fiable.

---

## 3. Contexto

El documento fuente indica dificultades para entender si existen incidencias que afecten al servicio y la necesidad de mostrar informacion basica de accesibilidad cuando sea posible.

---

## 4. Alcance

### 4.1 Incluido

- Visualizacion de incidencias activas relevantes.
- Diferenciacion entre ausencia de incidencias e informacion no disponible.

### 4.2 Fuera de alcance

- Catalogo completo de incidencias.
- Semantica avanzada de accesibilidad.

### 4.3 Límites

- Solo se mostrara accesibilidad cuando exista y haya sido validada por el cliente.

---

## 5. Actor principal y actores relacionados

### 5.1 Actor principal

| Actor | Descripción |
|-------|-------------|
| Usuario con necesidades de accesibilidad | Persona que necesita conocer de antemano limitaciones relevantes para su desplazamiento |

### 5.2 Actores relacionados

| Actor | Relación con la historia |
|-------|---------------------------|
| Viajero urbano habitual | Necesita evaluar incidencias antes del viaje |
| Aplicacion movil | Presenta incidencias y accesibilidad visible |

---

## 6. Disparador

- El usuario consulta la informacion operativa de una parada o linea relacionada.

---

## 7. Precondiciones

- Existen criterios de publicacion para incidencias relevantes.
- La informacion de accesibilidad visible ha sido validada por el cliente cuando exista.

---

## 8. Postcondiciones

### 8.1 Éxito

- El usuario entiende si existen incidencias relevantes.
- El usuario visualiza informacion basica de accesibilidad cuando aplique.

### 8.2 Fallo

- La app comunica ausencia de dato o indisponibilidad sin hacer afirmaciones no confirmadas.

---

## 9. Reglas de negocio asociadas

| ID | Regla | Fuente / referencia |
|----|-------|---------------------|
| BR-001 | Debe informarse al usuario cuando existan incidencias activas que afecten a la parada o linea relacionada | RFN-004 |
| BR-002 | Debe diferenciarse una situacion sin incidencias de una situacion en la que la informacion no este disponible | RFN-005 |
| BR-003 | La accesibilidad basica solo debe mostrarse cuando exista y haya sido validada por el cliente | RFN-006 |
| BR-004 | Debe evitarse mostrar informacion ambigua o no confirmada como definitiva | RFN-007 |

---

## 10. Datos de entrada y salida

### 10.1 Entradas

| # | Entrada | Origen | Obligatoria | Validaciones |
|---|---------|--------|-------------|--------------|
| 1 | identificador de parada | Usuario / app | Sí | Debe corresponder a una parada valida |

### 10.2 Salidas

| # | Salida | Destino | Descripción |
|---|--------|---------|-------------|
| 1 | incidencias relevantes | Usuario / app | Incidencias que afectan al viaje |
| 2 | accesibilidad basica | Usuario / app | Informacion basica visible cuando sea fiable |

---

## 11. Criterios de aceptación

### AC-001 — Mostrar incidencias activas relevantes

- **Dado** que existen incidencias activas que afectan a la parada o linea relacionada
- **Cuando** el usuario consulta la informacion operativa
- **Entonces** la solucion debe mostrar esas incidencias de forma comprensible

### AC-002 — Diferenciar ausencia de incidencias e indisponibilidad

- **Dado** que no existen incidencias activas o la informacion no esta disponible
- **Cuando** el usuario consulta la informacion operativa
- **Entonces** la solucion debe distinguir claramente ambos escenarios

### AC-003 — Mostrar accesibilidad basica validada

- **Dado** que existe informacion basica de accesibilidad validada por el cliente
- **Cuando** el usuario consulta la parada
- **Entonces** la solucion debe mostrar esa informacion de forma clara y no ambigua

---

## 12. Escenarios Gherkin asociados

### Feature: Consultar incidencias y accesibilidad por parada

```gherkin
Feature: Consultar incidencias y accesibilidad por parada
  As a viajero urbano o usuario con necesidades de accesibilidad
  I want ver incidencias relevantes y accesibilidad basica de la parada o servicio
  So that planificar mejor mi desplazamiento y evitar sorpresas antes del viaje

  Scenario: Mostrar incidencias activas relevantes
    Given existen incidencias activas que afectan a la parada o linea relacionada
    When el usuario consulta la informacion operativa
    Then la solucion muestra esas incidencias de forma comprensible

  Scenario: Diferenciar ausencia de incidencias e indisponibilidad
    Given no existen incidencias activas o la informacion no esta disponible
    When el usuario consulta la informacion operativa
    Then la solucion distingue claramente ambos escenarios

  Scenario: Mostrar accesibilidad basica validada
    Given existe informacion basica de accesibilidad validada por el cliente
    When el usuario consulta la parada
    Then la solucion muestra esa informacion de forma clara y no ambigua
```

## 13. Trazabilidad de tests Gherkin

| Test ID | Feature | Escenario | Tipo | AC cubierto | Estado | Observaciones |
|---------|---------|-----------|------|-------------|--------|---------------|
| GT-001  | Consultar incidencias y accesibilidad por parada | Mostrar incidencias activas relevantes | funcional | AC-001 | pendiente | Cubre flujo de incidencias |
| GT-002  | Consultar incidencias y accesibilidad por parada | Diferenciar ausencia de incidencias e indisponibilidad | negativo | AC-002 | pendiente | Cubre diferenciacion de estados |
| GT-003  | Consultar incidencias y accesibilidad por parada | Mostrar accesibilidad basica validada | funcional | AC-003 | pendiente | Depende de definicion minima de accesibilidad |

---

## 14. Trazabilidad de cobertura funcional y riesgo

| Cobertura ID | Tipo | Referencia origen | AC relacionado | Test Gherkin | Riesgo relacionado | Control validado | Estado cobertura | Evidencia |
|--------------|------|-------------------|----------------|--------------|--------------------|------------------|------------------|-----------|
| COV-001 | funcional | FRS-UBUS-001 | AC-002 | GT-001 | — | Publicacion de incidencias relevantes | pendiente | pendiente de refinamiento |
| COV-002 | riesgo | FRS-UBUS-001 | AC-003 | GT-002 | USRSK-001 | Distincion entre ausencia de incidencias e indisponibilidad | pendiente | pendiente de refinamiento |
| COV-003 | riesgo | FRS-UBUS-001 | AC-004 | GT-003 | USRSK-002 | Publicacion solo de accesibilidad validada | pendiente | pendiente de refinamiento |

---

## 15. Requisitos no funcionales asociados

| ID | Tipo | Descripción | Criterio medible |
|----|------|-------------|------------------|
| RNF-004 | usabilidad | La informacion mostrada debe inspirar confianza y coherencia | Validacion funcional por negocio |

---

## 16. Dependencias

| Tipo | ID / Sistema | Relación | Descripción |
|------|--------------|----------|-------------|
| Épica | EPIC-UBUS-01 | `pertenece-a` | Epica funcional contenedora |
| FRS | FRS-UBUS-001 | `deriva-de` | Requisito funcional principal |
| Historias | US-UBUS-001 | `relacionada-con` | Comparte consulta operativa por parada |
| Servicio ext. | pendiente de refinamiento | `consume` | Origen de informacion operativa no concretado en el documento fuente |

---

## 17. Especificacion OpenAPI derivada

| Artefacto API | Ruta / ID | Tipo | Operacion / evento | Estado | Observaciones |
|---------------|-----------|------|--------------------|--------|---------------|
| OpenAPI spec | spec/open-api/urban-bus-operational-info.openapi.yaml | `openapi` | GET /stops/{stopId}/operational-info | borrador | Misma operacion observable usada para incidencias y accesibilidad |
| OpenAPI spec | spec/open-api/urban-bus-operational-info.openapi.yaml#/components/schemas/OperationalAlert | `openapi` | Schema OperationalAlert | borrador | Taxonomia exacta de incidencias pendiente de refinamiento |

---

## 18. Observabilidad funcional

### 18.1 Eventos funcionales

| Evento | Cuándo ocurre | Datos mínimos |
|--------|----------------|---------------|
| STOP_ALERTS_SHOWN | Al mostrar incidencias al usuario | identificador de parada, total de incidencias |
| STOP_ACCESSIBILITY_SHOWN | Al mostrar accesibilidad basica | identificador de parada, presencia de accesibilidad |

### 18.2 Alertas

| Alerta | Condición | Acción esperada |
|--------|-----------|-----------------|
| ALERT-OPINFO-AMBIGUOUS | Se detecta publicacion de dato no confirmado o ambiguo | Revisar catalogo funcional y mensajes |

### 18.3 KPIs

| KPI | Definición | Objetivo |
|-----|------------|----------|
| KPI-US-UBUS-002 | Consultas con incidencias o accesibilidad comunicadas correctamente / consultas aplicables | pendiente de refinamiento |

---

## 19. Riesgos y controles

| Riesgo ID | Descripción | Probabilidad | Impacto | Control / mitigación |
|-----------|-------------|--------------|---------|----------------------|
| USRSK-001 | La informacion de incidencias se publique de forma incompleta, dispersa o dificil de interpretar | media | alta | Diferenciar estados y publicar solo informacion relevante |
| USRSK-002 | La informacion de accesibilidad se muestre sin fiabilidad suficiente | media | alta | Mostrar accesibilidad solo cuando exista validacion del cliente |

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
| Historias relacionadas | US-UBUS-001 | Historia complementaria |
| Especificaciones OpenAPI derivadas | spec/open-api/urban-bus-operational-info.openapi.yaml | OpenAPI derivada para consulta operativa |
| Criterios de aceptación | AC-001, AC-002, AC-003 | Criterios definidos en §11 |
| Tests Gherkin | GT-001, GT-002, GT-003 | Escenarios definidos en §13 |
| Cobertura funcional y riesgo | COV-001, COV-002, COV-003 | Cobertura definida en §14 |
| Riesgos relacionados | USRSK-001, USRSK-002 | Riesgos asociados |
| ADR relacionado | pendiente de refinamiento | No identificado en esta fase |
| Enlace RTM | LINK-002 | Entrada en `traceability/RTM.yaml` |

---

## 21. Notas y decisiones abiertas

| # | Nota / pregunta | Responsable | Estado | Fecha objetivo | Decisión tomada | Evidencia |
|---|------------------|-------------|--------|----------------|-----------------|----------|
| 1 | Definir las categorias de incidencias que deben mostrarse al viajero desde la primera version | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Documento inicial de analisis.txt §12 |
| 2 | Confirmar que informacion de accesibilidad puede publicarse con suficiente fiabilidad | pendiente de refinamiento | abierta | pendiente de refinamiento | pendiente de refinamiento | Documento inicial de analisis.txt §12 |

---

*Plantilla: `user-story.template.md` v1.2.0*
