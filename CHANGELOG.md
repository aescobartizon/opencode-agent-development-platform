# Changelog

## Unreleased

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
