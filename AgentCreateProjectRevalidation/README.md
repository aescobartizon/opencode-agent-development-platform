# AgentCreateProjectRevalidation

Repositorio de gobernanza para el proyecto AgentCreateProjectRevalidation.

## Propósito

Establecer la base documental, operativa y de trazabilidad de un sistema con arquitectura de microservicios bajo un modelo multi-repo.

## Alcance inicial

Este repositorio centraliza requisitos, arquitectura global, backlog, trazabilidad, QA transversal, operación global y artefactos para trabajo coordinado entre equipos humanos y agentes.

## Arquitectura objetivo

- Arquitectura basada en microservicios.
- Modelo multi-repo: un repositorio de gobernanza y repositorios independientes por servicio.
- Sin código de implementación de negocio en este repositorio.

## Modelo de repositorios

- `AgentCreateProjectRevalidation/`: gobierno, requisitos, trazabilidad, contratos, QA global y operación cross-servicio.
- `AgentCreateProjectRevalidation-svc-*`: repositorios externos e independientes por microservicio, registrados en `services/registry.yaml`.

## Estructura del repositorio de gobernanza

- `docs/`: documentación fuente del proyecto.
- `traceability/`: matrices y vistas de trazabilidad extremo a extremo.
- `backlog/`: épicas y casos de uso.
- `services/`: registro de servicios y contratos, sin implementación.
- `spec/`: artefactos de especificación.
- `src/`: interfaces y elementos compartidos futuros.
- `tests/`: pruebas globales y de contrato.
- `ops/`: operación, observabilidad y runbooks globales.
- `artifacts/`: salidas generadas.

## Principio de trazabilidad

Cada requisito debe poder rastrearse hacia épicas, casos de uso, historias, pruebas y referencias externas a repositorios de servicio, PRs y commits.

## Flujo de trabajo base

1. Capturar contexto y requisitos.
2. Refinar y documentar decisiones globales.
3. Mantener trazabilidad en `traceability/`.
4. Registrar servicios y contratos en `services/`.
5. Coordinar QA, operación y evidencias globales.

## Próximos pasos

1. Documentar visión, alcance y stakeholders en `docs/project/`.
2. Crear primeras épicas y casos de uso en `backlog/`.
3. Registrar servicios cuando existan repos independientes.
4. Definir contratos OpenAPI en `spec/open-api/` y publicarlos en `services/contracts/`.
5. Completar estrategia QA y operación global.
