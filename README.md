# Deploy con GitHub Actions y Token (ejemplo)

Pasos resumidos para la prueba de despliegue usando un token personal (no `GITHUB_TOKEN`).

- Crear un Personal Access Token (PAT) con scope `repo`.
- Guardar el PAT como secret en el repositorio con nombre `PERSONAL_TOKEN`.
- Añadir y pushear los archivos a la rama `main`.
- La Action despliega el contenido de la raíz al branch `gh-pages`.

Ver `evidence.md` para la evidencia y respuestas a las preguntas.
