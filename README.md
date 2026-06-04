# Página de perfil (Hugo + Lynx + GitHub Pages)

Sitio estático tipo “link in bio” generado con [Hugo](https://gohugo.io/) y el tema [Lynx](https://github.com/jpanther/lynx).

## Nota técnica

El tema Lynx aún referencia `.Site.Author` en algunas plantillas; Hugo 0.124+ lo eliminó. Este proyecto incluye parches en `layouts/partials/head.html` y `footer.html` que usan `.Site.Params.Author`.

## Personalizar

1. **`config.toml`** — `baseURL`, nombre, headline, enlaces en `[params.author].links`.
2. **`content/_index.md`** — Texto de presentación y metadatos.
3. **`assets/css/custom.css`** — Colores y estilos de los botones.
4. **`static/author.jpg`** — Foto de perfil (descomenta `image = "author.jpg"` en `config.toml`).

## Vista local

```powershell
hugo server -D
```

Abre la URL que muestra la terminal (normalmente http://localhost:1313/).

## Publicar en GitHub Pages

1. Crea en GitHub un repositorio llamado **`TU_USUARIO.github.io`** (solo uno por cuenta).
2. Actualiza `baseURL` en `config.toml` a `https://TU_USUARIO.github.io/`.
3. En la raíz del repo, sube este proyecto:

   ```powershell
   git remote add origin https://github.com/TU_USUARIO/TU_USUARIO.github.io.git
   git branch -M main
   git add .
   git commit -m "Sitio de perfil con Hugo y Lynx"
   git push -u origin main
   ```

4. En el repositorio: **Settings → Actions → General → Workflow permissions** → **Read and write permissions**.
5. Cuando termine el workflow: **Settings → Pages** → Source: rama **`gh-pages`**, carpeta **`/ (root)`**.

Tu sitio quedará en `https://TU_USUARIO.github.io/`.
