---
description: Analiza un documento de negocio con AgentAnalystDocFlow
---

Usa `AgentAnalystDocFlow` para analizar el documento indicado por el usuario.

## Uso

```text
/analyze-doc <ruta-del-documento>
```

## Reglas

1. La ruta del documento es obligatoria.
2. Si no se proporciona ruta, responder solo pidiendo el documento exacto.
3. Invocar `AgentAnalystDocFlow` usando esa ruta como documento fuente confirmado.
4. No sustituir la ruta por autodeteccion ni por ejemplos de `templates/`.
5. Si el usuario quiere reprocesar un documento ya registrado, debe indicarlo explicitamente.

## Ejemplos

```text
/analyze-doc docs/input/documento-negocio.md
/analyze-doc docs/business/vision-inicial.txt
```
