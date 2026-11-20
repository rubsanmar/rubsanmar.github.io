# rubensm.es

Blog personal de Ruben Sanchez Martin sobre sistemas, redes y ciberseguridad.
Sitio estático generado con Jekyll y publicado con GitHub Pages en
<https://rubensm.es>.

## Escribir una entrada

Crea un archivo en `_posts/` con el nombre `AAAA-MM-DD-titulo.md` y este
front matter mínimo:

```yaml
---
title: "Título de la entrada"
date: 2026-11-20 10:00:00 +0100
categories: [sistemas]
tags: [docker, redes]
---
```

El layout `post` se aplica automáticamente. Las categorías y etiquetas alimentan
`/categories/` y `/tags/`.

## Previsualización local

Con Ruby instalado:

```bash
bundle install
bundle exec jekyll serve --watch
```

Con Docker, sin instalar Ruby:

```bash
docker compose up
```

En ambos casos el sitio se sirve en <http://localhost:4000/>.

## Publicación

Cada push a `master` hace que GitHub Pages recompile el sitio. El dominio
`rubensm.es` se conserva gracias al archivo `CNAME`.

## Estructura

- `_config.yml`: identidad, autor y opciones de compilación.
- `_posts/`: entradas del blog.
- `_layouts/`, `_includes/`, `_sass/`: plantillas y estilos del tema.
- `images/`: portada y favicons.
- `docs/`: documentación de trabajo (no se publica ni se versiona).
- `AGENTS.md`: instrucciones para el agente (no se publica ni se versiona).

## Créditos

Basado en el tema [Jekyll-Uno](https://github.com/joshgerdes/jekyll-uno) de
Josh Gerdes, distribuido bajo licencia MIT. El aviso original se conserva en
`LICENSE`.
