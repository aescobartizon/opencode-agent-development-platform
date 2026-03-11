# Agentes disponibles para el proyecto

Este repositorio queda preparado para colaboración entre equipos humanos y agentes especializados. La siguiente tabla describe los agentes de referencia de la plataforma que encajan con esta base de gobernanza.

| Agente | Rol | Responsabilidad principal | Herramientas principales |
|---|---|---|---|
| AgentProjectFromScratch | Fundacional | Crear y mantener la estructura base del repositorio de gobernanza | bash, lectura de archivos, edición estructurada |
| AgentAnalystDocFlow | Analista documental | Transformar insumos de negocio en épicas, FRS, historias y OpenAPI cuando aplique, solicitando primero el documento fuente exacto | bash, lectura de archivos, edición estructurada |
| AgentValidateDocFlow | Validador documental | Verificar coherencia, completitud y trazabilidad del flujo funcional | bash, lectura de archivos, edición estructurada |
| AgentValidatePlatform | Validador integral de plataforma | Validar consistencia entre agentes, skills, plantillas y proyectos generados | bash, lectura de archivos, edición estructurada |

## Uso previsto

- Usar `AgentProjectFromScratch` para evolución estructural del repositorio.
- Usar `AgentAnalystDocFlow` para crear artefactos funcionales reales a partir de documentación de negocio; el agente comienza solicitando el documento fuente exacto si no viene ya identificado.
- Usar `AgentValidateDocFlow` para revisar cumplimiento de flujo y trazabilidad.
- Usar `AgentValidatePlatform` para validaciones integrales de la plataforma documental.

## Zonas de soporte

- `.opencode/agents/` para extensiones locales de agentes.
- `.opencode/commands/` para automatizaciones internas del proyecto.
- `.opencode/commands/analyze-doc.md` como comando recomendado para lanzar el analisis documental con ruta explicita.
- `.opencode/skills/` para skills específicas del contexto del proyecto.
- `agents/` para documentación, prompts y recursos complementarios del trabajo agéntico.
