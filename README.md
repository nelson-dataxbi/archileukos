# Archileukos

Este repositorio contiene el sitio web de Archileukos publicado con GitHub Pages y Jekyll.

La web se genera a partir de archivos Markdown (`.md`), datos en YAML (`.yml`) e imágenes dentro de `assets/img`.

## Dónde editar cada página

- Página principal: `index.md`
- Acerca de mi: `acerca-de-mi/index.md`
- Listado de proyectos: `proyectos/index.md`
- Datos de la galería de proyectos: `_data/projects.yml`
- Proyecto Pliegues de convivencia: `proyectos/proyecto-pliegues-convivencia/index.md`
- Proyecto Conectar para revivir: `proyectos/conectar-para-revivir/index.md`
- Proyecto A Supernormal greenway: `proyectos/a-supernormal-greenway/index.md`
- Proyecto Recuperar el horizonte: `proyectos/recuperar-el-horizonte/index.md`
- Proyecto TFG ETSAV: `proyectos/tfg-analisis-espacial-de-la-universidad-etsav/index.md`

El menú, el pie de página, los iconos y la estructura general están en `_layouts/default.html`. Normalmente no hace falta tocar ese archivo para actualizar contenido.

## Cómo editar texto

Cada página empieza con un bloque como este:

```yaml
---
title: "Acerca de mi"
body_class: "content-page"
---
```

No borres ese bloque. Edita el contenido que aparece debajo.

El contenido puede mezclarse con HTML. Por ejemplo:

```html
<p>Texto de la página.</p>
<figure class="wp-block-image size-full">
  <img src="{{ '/assets/img/logo-largo-4.png' | relative_url }}" alt="">
</figure>
```

## Cómo cambiar imágenes

Las imágenes están dentro de `assets/img`.

Estructura principal:

- Imágenes generales: `assets/img/`
- Miniaturas de la página de proyectos: `assets/img/proyectos/`
- Imágenes de cada proyecto:
  - `assets/img/proyecto-pliegues-convivencia/`
  - `assets/img/conectar-para-revivir/`
  - `assets/img/a-supernormal-greenway/`
  - `assets/img/recuperar-el-horizonte/`
  - `assets/img/tfg-analisis-espacial-de-la-universidad-etsav/`

Para usar una imagen en una página, usa esta forma:

```html
<img src="{{ '/assets/img/nombre-de-la-imagen.png' | relative_url }}" alt="">
```

Para una imagen dentro de un proyecto:

```html
<img src="{{ '/assets/img/conectar-para-revivir/image-9.png' | relative_url }}" alt="">
```

La parte `| relative_url` es importante: hace que las rutas funcionen correctamente en GitHub Pages.

## Cómo actualizar la galería de proyectos

La galería de `proyectos/index.md` se genera desde `_data/projects.yml`.

Cada proyecto tiene una entrada como esta:

```yaml
- title: Pliegues de convivencia
  slug: proyecto-pliegues-convivencia
  thumbnail: /assets/img/proyectos/TAP-10-1-1-300x300.png
  image_class: wp-image-29
  row: "1"
```

Campos importantes:

- `title`: nombre visible del proyecto.
- `slug`: nombre de la carpeta dentro de `proyectos/`.
- `thumbnail`: imagen que aparece en la galería.
- `row`: fila donde aparece. Usa `"1"` o `"2"`.

Para cambiar una miniatura:

1. Sube la nueva imagen a `assets/img/proyectos/`.
2. Cambia el valor de `thumbnail` en `_data/projects.yml`.

Para reordenar proyectos, cambia el orden de las entradas o cambia `row`.

## Cómo añadir un nuevo proyecto

1. Crea una carpeta nueva dentro de `proyectos/`, por ejemplo:

```txt
proyectos/nuevo-proyecto/
```

2. Dentro crea un archivo `index.md`.

3. Usa esta plantilla:

```markdown
---
title: "Nuevo proyecto"
body_class: "content-page project-page"
---
<p class="has-text-align-center" style="font-size:3.5rem">Nuevo proyecto</p>
<p class="has-text-align-center has-large-font-size">Subtitulo del proyecto</p>
<p>Texto del proyecto.</p>
```

4. Guarda las imágenes del proyecto en:

```txt
assets/img/nuevo-proyecto/
```

5. Añade el proyecto a `_data/projects.yml`:

```yaml
- title: Nuevo proyecto
  slug: nuevo-proyecto
  thumbnail: /assets/img/proyectos/miniatura-nuevo-proyecto.png
  image_class: wp-image-000
  row: "2"
```

## Cómo publicar cambios

Después de editar archivos:

```powershell
git status
git add -A
git commit -m "Actualizar contenido del sitio"
git push
```

GitHub Pages publicará la web automáticamente. Puede tardar entre 1 y 3 minutos.

URL actual:

```txt
https://nelson-dataxbi.github.io/archileukos/
```

## Notas importantes

- No edites archivos dentro de `_site/` si aparece esa carpeta: es una carpeta generada.
- No borres `_config.yml`, `_layouts/default.html` ni `_data/projects.yml`.
- Si se configura un dominio propio como `archileukos.com`, habrá que actualizar `url` y `baseurl` en `_config.yml`.
- El estilo visual principal está en `assets/css/site.css`.
