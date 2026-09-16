# joseulloa.com

Página personal de José Ulloa Suárez. Sitio estático de una sola página (HTML + CSS, sin JavaScript ni build), servido por Cloudflare Pages en https://www.joseulloa.com.

## Estructura

- `index.html`, `styles.css`: la página.
- `assets/`: retrato en AVIF/WebP/JPEG (400 y 800 px).
- `favicon.svg`, `apple-touch-icon.png`, `site.webmanifest`, `og-image.png`.
- `_headers`: cabeceras de seguridad y caché para Cloudflare Pages, más `noindex` en `*.pages.dev`.
- `robots.txt`, `sitemap.xml`.

## Despliegue

Cada push a `main` despliega automáticamente vía la integración Git de Cloudflare Pages (proyecto `joseulloa-com`, framework "None", sin comando de build, directorio de salida `/`).

DNS en Cloudflare:
- `www` es un CNAME a `joseulloa-com.pages.dev` (proxied), creado desde el panel de Pages.
- `@` (apex) mantiene un registro A placeholder proxied (`192.0.2.1`). No borrarlo: es lo que permite que la regla de redirección 301 `joseulloa.com` → `www.joseulloa.com` funcione.

## Regla de privacidad

Nunca publicar teléfono, RUT ni dirección. Solo correo (ofuscado con entidades HTML) y LinkedIn. El JSON-LD no incluye correo.

Antes de cada push:

```
grep -inE "\+56|RUT|[0-9]{1,2}\.[0-9]{3}\.[0-9]{3}-[0-9kK]|alderete" index.html
```

debe devolver vacío.
