# OpenCode Agent Development Platform

Repositorio base para desarrollar y versionar capacidades de OpenCode orientadas a proyectos de software con arquitectura de microservicios.

## Que contiene este repositorio

- `agents/`: agentes especializados reutilizables para automatizar tareas complejas.
- `skills/`: skills cargables con procedimientos guiados y flujos de trabajo concretos.
- `templates/`: plantillas base para documentacion y artefactos generados.
- `opencode.jsonc`: configuracion local de OpenCode, permisos y conexion MCP.

## Componentes actuales

### Agente incluido

- `agents/AgentCreateProjectFromScratch.md`: agente fundacional simplificado para crear la estructura basica del proyecto y copiar todo `./templates/` en `./docs/templates/`.
  - Configurado para preferir el modelo gratuito `gemini-2.0-flash` cuando el entorno soporte fijar modelo.
- `agents/AgentProjectFromScratch.md`: alias compatible del agente fundacional para invocaciones historicas desde terminal.

### Skill incluida

- `skills/scaffold-project-structure/SKILL.md`: procedimiento minimo para crear la estructura basica del proyecto y copiar todo `./templates/` en `./docs/templates/`.
- `skills/analyst-doc-flow/SKILL.md`: procedimiento operativo detallado para analizar un documento de negocio confirmado por el usuario y derivar Epica, FRS, US, OpenAPI y RTM.
- `skills/functional-traceability-rules/SKILL.md`: reglas compartidas de trazabilidad funcional y no duplicacion usadas por analisis y validacion documental.
- `skills/validate-doc-flow/SKILL.md`: procedimiento detallado para validar y remediar trazabilidad funcional sin sobrecargar el agente validador.

### Comando incluido

- `.opencode/commands/analyze-doc.md`: comando recomendado para lanzar `AgentAnalystDocFlow` con ruta explicita de documento.

### Plantillas incluidas

- `templates/executive-report.template.html`: plantilla HTML para informes ejecutivos.
- `templates/functional-requirement.template.md`: plantilla Markdown para requisitos funcionales con trazabilidad y criterios de aceptacion.
- `templates/analyst-doc-flow-output.template.md`: plantilla Markdown para estructurar la salida final de `AgentAnalystDocFlow`.

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
- nuevos comandos operativos,
- nuevas plantillas,
- automatizaciones de soporte para equipos de analisis, arquitectura, QA y operacion.
