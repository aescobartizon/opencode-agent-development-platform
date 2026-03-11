# Changelog

## Unreleased

- Refactorizado `AgentAnalystDocFlow` para exigir la solicitud explicita del documento fuente antes de cualquier analisis.
- Ajustado `AgentAnalystDocFlow` para escanear BRS pendientes en `/docs/requirements/functional/` y pedir al usuario que elija cual analizar.
- Reforzado `AgentAnalystDocFlow` para exigir generacion de ficheros OpenAPI reales y delegar siempre la validacion final en `AgentValidateDocFlow`.
- Extraida la salida final de `AgentAnalystDocFlow` a `templates/analyst-doc-flow-output.template.md`.
- Extraida la logica procedimental detallada a `skills/analyst-doc-flow/SKILL.md` para mejorar mantenibilidad.
- Simplificado `AgentValidateDocFlow` y extraido su procedimiento detallado a `skills/validate-doc-flow/SKILL.md`.
- Actualizado `AgentValidatePlatform` para validar el nuevo handshake explicito de confirmacion de documento en `AgentAnalystDocFlow`.
- Añadido `.opencode/commands/analyze-doc.md` como comando recomendado para analisis documental con ruta explicita.
- Extraidas reglas comunes a `skills/functional-traceability-rules/SKILL.md` y referenciadas desde analisis y validacion documental.
- Añadidos ejemplos de invocacion y reproceso en `skills/analyst-doc-flow/SKILL.md`.
- Agentes y skills actualizados para preferir el modelo `gemini-2.0-flash`.
- AgentCreateProjectFromScratch actualizado a v1.3.1 con preferencia explicita por `gemini-2.0-flash`.
- Reforzada la instruccion de copiar todo `templates/` al scaffold folder `docs/templates/` del proyecto generado.
- Alineado `AgentCreateProjectFromScratch` con los assets reales del repositorio (`agents/`, `skills/`, `templates/`).
- Corregida la resolución de plantillas para usar primero `templates/` del repo y `~/.config/opencode/templates/` solo como fallback.
- Unificada la skill `scaffold-project-structure` con el modelo actual de repositorio de gobernanza multi-repo.
- Endurecida la validación del agente para excluir directorios de plantillas del chequeo de placeholders.
- Añadido contenido semilla mínimo en áreas clave como `docs/project/`, `docs/requirements/technical/` y `docs/refinement/`.
- Añadida persistencia Git para carpetas críticas vacías mediante `.gitkeep` o `README.md`.
- Reforzada la validación de `services/registry.yaml` y `traceability/RTM.yaml` para exigir `services: []` y `enlaces: []`.
- Añadida generación obligatoria de `PROJECT_REPORT.html` y copia en `docs/executive-reports/INF-EJE-001.html`.
- Mejorada la portabilidad del agente usando `python3` cuando `python` no está disponible.
- Revalidado el flujo end-to-end con proyectos de prueba generados correctamente y sin placeholders fuera de plantillas.
