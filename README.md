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
  - Configurado para preferir el modelo gratuito `gpt-5-nano` cuando el entorno soporte fijar modelo.

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

## Convenciones de rutas

- `agents/`: definiciones de agentes versionadas en este repositorio de plataforma.
- `skills/`: skills versionadas y cargables por OpenCode.
- `templates/`: plantillas fuente versionadas para ser copiadas a proyectos generados.

Cuando un agente o skill necesite una plantilla, debe resolverla en este orden:

1. `templates/` relativo al repositorio actual
2. `~/.config/opencode/templates/` como fallback global del usuario

Esto evita depender solo de rutas externas no versionadas.

## Modelo de generacion

Este repositorio de plataforma usa assets en raiz (`agents/`, `skills/`, `templates/`).

Los proyectos generados por el agente pueden incluir una zona `.opencode/` propia para alojar agentes, skills y comandos del proyecto destino. Esa estructura no sustituye los assets fuente de esta plataforma; los complementa.

## Garantias del agente actual

El agente `agents/AgentCreateProjectFromScratch.md` esta endurecido para:

- resolver plantillas primero desde `templates/` y despues desde `~/.config/opencode/templates/`,
- copiar todo el contenido disponible de `templates/` al scaffold folder del proyecto `docs/templates/`,
- conservar placeholders solo en archivos plantilla y no en documentos instanciados,
- generar contenido semilla minimo en areas clave del repositorio,
- persistir carpetas vacias importantes con `.gitkeep` o `README.md`,
- generar `PROJECT_REPORT.html` y su copia en `docs/executive-reports/INF-EJE-001.html`,
- usar `python3` como fallback cuando `python` no exista en el entorno.

## Uso esperado

Este repositorio esta pensado como base de desarrollo y mantenimiento para evolucionar:

- nuevos agentes,
- nuevas skills,
- nuevas plantillas,
- automatizaciones de soporte para equipos de analisis, arquitectura, QA y operacion.
