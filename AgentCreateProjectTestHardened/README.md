# AgentCreateProjectTestHardened

## Propósito
Repositorio de gobernanza para el proyecto **AgentCreateProjectTestHardened**, creado para validar la versión endurecida del agente fundacional de OpenCode.

## Alcance inicial
Este repositorio centraliza requisitos, trazabilidad, backlog, contratos, arquitectura global, QA cross-servicio y operación global. No contiene implementación de microservicios.

## Arquitectura objetivo
- Arquitectura de **microservicios**.
- Modelo **multi-repo**.
- Un repositorio de gobernanza central + un repositorio independiente por servicio.

## Modelo de repositorios
- `AgentCreateProjectTestHardened/`: repositorio de gobernanza y fuente de verdad documental.
- `AgentCreateProjectTestHardened-svc-*`: repositorios independientes por microservicio, registrados en `services/registry.yaml`.

## Estructura del repositorio de gobernanza
- `docs/`: contexto, requisitos, arquitectura, refinamiento, QA e informes.
- `traceability/`: matrices y vistas de trazabilidad.
- `backlog/`: épicas y casos de uso.
- `services/`: registro de servicios y contratos de integración, sin código.
- `spec/`: especificaciones generadas durante análisis y diseño.
- `src/`: componentes compartidos futuros, sin implementación de servicios.
- `tests/`: pruebas globales de integración y contrato.
- `ops/`: operación, observabilidad y runbooks cross-servicio.
- `agents/` y `.opencode/`: soporte para trabajo asistido por agentes.
- `artifacts/`: salidas generadas automáticamente.

## Principio de trazabilidad
Todo artefacto relevante debe poder rastrearse desde requisito de negocio hasta caso de prueba y referencia externa de implementación en repos de servicio. La fuente de verdad estructurada es `traceability/RTM.yaml`.

## Flujo de trabajo base
1. Capturar contexto y requisitos.
2. Refinar preguntas y acuerdos.
3. Modelar arquitectura global y decisiones ADR.
4. Registrar servicios en `services/registry.yaml` cuando existan.
5. Mantener contratos en `services/contracts/`.
6. Actualizar matrices de trazabilidad y evidencias QA.

## Próximos pasos
1. Completar contexto de negocio en `docs/project/`.
2. Crear primeras épicas y casos de uso.
3. Definir requisitos funcionales y técnicos.
4. Registrar los primeros repositorios de servicio cuando sean creados.
5. Añadir contratos OpenAPI y estrategia de pruebas global.
