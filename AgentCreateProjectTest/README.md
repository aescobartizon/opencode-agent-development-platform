# AgentCreateProjectNoDupTrace

## Propósito

Repositorio de gobernanza para organizar documentación, trazabilidad, arquitectura global y operación cross-servicio del proyecto **AgentCreateProjectNoDupTrace**.

## Descripción

Proyecto de prueba para validar el agente sin trazabilidad duplicada.

## Alcance inicial

- Base documental del proyecto.
- Trazabilidad fuente única entre requisitos, historias, servicios y pruebas.
- Registro central de servicios y contratos, sin implementar microservicios.
- Preparación para trabajo posterior de analistas, arquitectura, QA y DevOps.

## Arquitectura objetivo

El proyecto se prepara para una arquitectura de **microservicios** bajo un modelo **multi-repo**.

- Este repositorio contiene gobernanza, documentación y trazabilidad.
- Cada microservicio vivirá en su repositorio independiente.
- Los contratos y referencias externas se registrarán aquí, pero el código no vive en este repositorio.

## Modelo de repositorios

- `AgentCreateProjectNoDupTrace/`: repositorio de gobernanza.
- `AgentCreateProjectNoDupTrace-svc-*`: repositorios independientes por servicio, registrados en `services/registry.yaml` cuando existan.

## Estructura del repositorio de gobernanza

- `docs/`: contexto, requisitos, arquitectura, refinamiento, QA e informes.
- `traceability/`: fuente de verdad de la trazabilidad del proyecto.
- `backlog/`: épicas e historias de usuario.
- `services/`: registro de servicios y contratos de integración.
- `spec/`: especificaciones OpenAPI y artefactos SDD.
- `src/`, `tests/`, `ops/`: activos transversales futuros sin implementación de negocio inicial.
- `agents/` y `.opencode/`: soporte para automatización agéntica.

## Principio de trazabilidad

La trazabilidad se mantiene **sin duplicación**:

- `traceability/RTM.yaml` es la matriz estructurada principal.
- `traceability/requirements_trace.md` y `traceability/end_to_end_traceability.csv` ofrecen vistas complementarias.
- Las relaciones jerárquicas finas se mantienen en los artefactos fuente y no en matrices derivadas redundantes.

## Flujo de trabajo base

1. Documentar contexto y alcance en `docs/project/`.
2. Crear requisitos funcionales y técnicos en `docs/requirements/`.
3. Descomponer backlog en `backlog/epics/` y `backlog/user-stories/`.
4. Mantener trazabilidad en `traceability/RTM.yaml`.
5. Registrar servicios reales en `services/registry.yaml`.
6. Publicar contratos en `services/contracts/` y `spec/open-api/`.

## Próximos pasos

- Definir visión, alcance y stakeholders iniciales.
- Crear primeras épicas e historias de usuario.
- Registrar servicios cuando exista diseño aprobado.
- Completar estrategia QA y operación global.
- Usar la plantilla de requisito funcional para nuevos FRS.
