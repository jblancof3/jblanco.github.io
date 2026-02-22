# research-page

Guía mínima para desarrollar y publicar esta página con Quarto + GitHub Actions.

## Flujo diario (simple)

1. Crear rama de trabajo:
   - `git checkout -b feat/mi-cambio`
2. Editar contenido (`.qmd`, `styles.css`, `_quarto.yml`).
3. Previsualizar cambios:
   - `quarto preview`
4. Validar build local:
   - `quarto render`
5. Guardar cambios:
   - `git add -A`
   - `git commit -m "mensaje corto"`
   - `git push origin feat/mi-cambio`
6. Abrir Pull Request hacia `main`.

## Publicación

- Al hacer merge a `main`, GitHub Actions publica automáticamente a GitHub Pages.
- Workflow: `.github/workflows/publish.yml`
- Revisar en GitHub:
  - Actions: job "Quarto Publish" en verde.
  - Settings > Pages: estado Published y URL activa.

## Qué subir al repo

Sí versionar:
- Fuentes: `*.qmd`, `styles.css`, `_quarto.yml`
- Workflow: `.github/workflows/publish.yml`
- Caché de ejecución: `_freeze/`

No versionar:
- Build final: `_site/`
- Entorno local: `.venv/`

## Checklist rápida antes de merge

- `quarto render` termina sin errores.
- `_freeze/` actualizado si cambió código ejecutable.
- No hay cambios accidentales en `_site/`.
- PR aprobado y mergeado a `main`.
