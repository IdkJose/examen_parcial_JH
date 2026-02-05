# Evidencia: Deploy con GitHub Actions y Pages usando Token

1) Crear repositorio

- Inicializar repo local, conectar remoto y pushear `main`.

2) Crear Token (Personal Access Token)

- En GitHub: Settings -> Developer settings -> Personal access tokens -> Generate new token.
- Scopes: seleccionar `repo` (mínimo) para permitir push a `gh-pages`.

3) Desarrollar sitio web

- Archivos añadidos: `index.html`, `styles.css`.

4) Workflow

- Archivo: `.github/workflows/deploy.yml` (usa `secrets.PERSONAL_TOKEN`).

5) Configurar secret

- Ir a Settings -> Secrets and variables -> Actions -> New repository secret.
- Nombre sugerido: `PERSONAL_TOKEN`.

Comandos útiles (local):

```bash
git init
git add .
git commit -m "Initial site and workflow"
git branch -M main
git remote add origin https://github.com/<TU_USUARIO>/<TU_REPO>.git
git push -u origin main
```

Usando `gh` CLI para crear el secret (no pegue su token en público):

```bash
echo "<TU_PAT_AQUI>" | gh secret set PERSONAL_TOKEN -b -R <TU_USUARIO>/<TU_REPO>
```

6) Verificar en Actions y Pages

- Revisar la pestaña Actions para ver la corrida del workflow.
- Habilitar GitHub Pages para que publique desde `gh-pages` (branch) si es necesario.

Respuestas (en mis palabras):

- Diferencia entre usar `GITHUB_TOKEN` y un token manual:

  - `GITHUB_TOKEN` es emitido automáticamente por GitHub Actions y tiene permisos limitados y un ciclo de vida corto; es suficiente para muchas operaciones internas. Un token manual (PAT) puede tener permisos y scopes personalizados (por ejemplo, `repo`) y persiste hasta su expiración manual; además permite escenarios donde `GITHUB_TOKEN` no funciona (acciones disparadas por forks, o permisos más amplios).

- ¿Por qué guardar el token en `secrets` y no directamente en el YAML?

  - Porque los secrets están cifrados y no se muestran en los logs; poner un token en el YAML lo expondría en el repo público y sería un riesgo de seguridad.

Generar PDF de evidencia (local):

```bash
pandoc evidence.md -o evidencia.pdf
```
