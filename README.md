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

Los archivos de desarrollo local (`docker-compose.yml`, `Gemfile` y
`Gemfile.lock`) no se versionan en este repositorio; solo se publican las
fuentes del sitio.

Con Docker, crea un `docker-compose.yml` en la raíz con:

```yaml
services:
  jekyll:
    image: jekyll/jekyll:latest
    command: jekyll serve --host 0.0.0.0 --watch --force_polling
    ports:
      - 4000:4000
    user: "1000:1000"
    environment:
      - JEKYLL_NO_BUNDLER_REQUIRE=true
    volumes:
      - .:/srv/jekyll:z
```

y ejecuta `docker compose up`. El sitio queda en <http://localhost:4000/>.
El valor de `user` debe coincidir con tu UID/GID (`id -u` e `id -g`).

Con Ruby instalado, crea un `Gemfile` con
`gem 'github-pages', group: :jekyll_plugins`, ejecuta `bundle install` y
después `bundle exec jekyll serve --watch`.

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
