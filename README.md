# OpenCode Agent Development Platform

Repositorio base para desarrollar y versionar capacidades de OpenCode orientadas a proyectos de software con arquitectura de microservicios.

## Que contiene este repositorio

- `agents/`: agentes especializados reutilizables para automatizar tareas complejas.
- `skills/`: skills cargables con procedimientos guiados y flujos de trabajo concretos.
- `templates/`: plantillas base para documentacion y artefactos generados.
- `opencode.jsonc`: configuracion local de OpenCode, permisos y conexion MCP.

## Componentes actuales

### Agente incluido

- `agents/AgentCreateProjectFromScratch.md`: agente fundacional para crear desde cero un repositorio de gobernanza para proyectos multi-repo basados en microservicios.

### Skill incluida

- `skills/scaffold-project-structure/SKILL.md`: procedimiento paso a paso para crear la estructura inicial de un proyecto en momento cero.

### Plantillas incluidas

- `templates/executive-report.template.html`: plantilla HTML para informes ejecutivos.
- `templates/functional-requirement.template.md`: plantilla Markdown para requisitos funcionales con trazabilidad y criterios de aceptacion.

## Objetivo

Este repositorio sirve como plataforma de trabajo para:

- definir agentes especializados,
- encapsular conocimiento operativo en skills,
- estandarizar artefactos de proyecto mediante plantillas,
- acelerar la creacion de repositorios de gobernanza y documentacion estructurada.

## Configuracion

El archivo `opencode.jsonc` habilita permisos abiertos y define un endpoint MCP remoto en `http://127.0.0.1:8081/mcp`.

## Uso esperado

Este repositorio esta pensado como base de desarrollo y mantenimiento para evolucionar:

- nuevos agentes,
- nuevas skills,
- nuevas plantillas,
- automatizaciones de soporte para equipos de analisis, arquitectura, QA y operacion.
