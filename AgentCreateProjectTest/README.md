# AgentCreateProjectTest

Proyecto de prueba para validar la generacion end-to-end del repositorio de gobernanza de OpenCode.

## Proposito

Establecer una base de gobernanza para un proyecto con arquitectura de microservicios, modelo multi-repo y trazabilidad desde requisitos hasta pruebas e implementacion referenciada en repositorios externos.

## Alcance inicial

- Requisitos funcionales y tecnicos.
- Casos de uso y backlog inicial.
- Trazabilidad extremo a extremo.
- Registro de servicios y contratos de integracion.
- Arquitectura global, QA y operacion cross-servicio.
- Soporte para colaboracion entre humanos y agentes IA.

## Arquitectura objetivo

El proyecto esta preparado para una arquitectura de microservicios con repositorio central de gobernanza y repositorios independientes por servicio.

## Modelo de repositorios

- `AgentCreateProjectTest/`: repositorio de gobernanza creado en este ejercicio.
- `AgentCreateProjectTest-svc-*`: repositorios externos por microservicio, referenciados en `services/registry.yaml`.

Este repositorio no contiene implementacion de negocio de los servicios.

## Estructura resumida

- `docs/`: documentacion fuente del proyecto.
- `traceability/`: fuente de verdad de la trazabilidad.
- `backlog/`: epicas y casos de uso.
- `services/`: registro de servicios y contratos.
- `spec/`: artefactos SDD y OpenAPI en elaboracion.
- `src/`: espacio reservado para artefactos compartidos.
- `tests/`: pruebas globales de contrato e integracion.
- `ops/`: operacion global, observabilidad y runbooks.
- `agents/` y `.opencode/`: soporte para automatizacion agéntica.

## Principio de trazabilidad

Todo requisito debe poder vincularse, cuando exista contenido real, con epicas, casos de uso, historias, servicios, pruebas y referencias externas a repositorios de implementacion.

## Flujo de trabajo base

1. Capturar contexto y requisitos.
2. Refinar y documentar decisiones globales.
3. Mantener trazabilidad en `traceability/`.
4. Registrar servicios en `services/registry.yaml` cuando existan.
5. Publicar contratos en `services/contracts/`.
6. Coordinar QA y operacion cross-servicio.

## Proximos pasos

1. Crear el contexto funcional inicial en `docs/project/`.
2. Registrar primeras epicas y casos de uso.
3. Definir arquitectura global y ADRs.
4. Dar de alta servicios reales en `services/registry.yaml`.
5. Generar contratos y pruebas de integracion global.
