# Sitio de bodas — Andrés y Glenda

## Contexto del proyecto
Plantilla HTML5 estática (Neela) personalizada para la boda de **Andrés y Glenda**.
- **Fecha:** Sábado 14 de noviembre de 2026
- **Hora:** 02:00 PM (Ceremonia 02:00 PM – 03:00 PM)
- **Venue:** HIKARU — Purabá, Santa Bárbara, Heredia, Costa Rica
- **Orden del nombre:** "Andrés y Glenda" (él primero)
- **Correo de contacto:** andrevrh21@gmail.com

## Cómo levantar el servidor
Desde la terminal, dentro de la carpeta del template:
```bash
cd "Neela HTML 5 Template"
npx serve -p 3000
```
Abre en el navegador: `http://localhost:3000/index-multipage.html`

## Estructura de archivos
```
Weeding/
├── CLAUDE.md                      ← este archivo
├── Neela HTML 5 Template/         ← raíz del sitio
│   ├── index.html                 ← one-page principal
│   ├── index-multipage.html       ← multi-page principal
│   ├── index-onepage-video.html   ← variante con video
│   ├── index-invite.html          ← página de invitación
│   ├── about-us.html
│   ├── wedding-details.html
│   ├── wedding-party.html
│   ├── gift-registry.html
│   ├── rsvp.html
│   ├── gallery.html / gallery-2.html / gallery-3.html
│   ├── blog-*.html (5 archivos)
│   ├── css/
│   │   ├── style.css              ← CSS compilado (editar manualmente)
│   │   └── style.scss             ← fuente SCSS (editar en paralelo)
│   ├── js/
│   │   └── variables.js           ← config del mapa de Google y otros
│   └── images/
│       ├── STZ07954.jpg           ← fotos reales de la pareja (hero)
│       ├── STZ07956.jpg
│       ├── STZ07970.jpg
│       ├── STZ08128.jpg
│       └── STZ08435.jpg
```

## Regla crítica de CSS
**No hay pipeline de build.** Cada vez que se edita CSS, hay que hacerlo en **ambos archivos**:
- `css/style.css` — el que usa el navegador
- `css/style.scss` — mantener en sync manualmente

## Personalización de diseño
| Elemento | Valor |
|---|---|
| Color primario | `#8eaeba` (azul grisáceo) |
| Color secundario | `#59723f` (verde oliva) |
| Fuente nombre pareja | Dear Script (`webfonts/dear-script.otf`) |
| Fuente venue HIKARU | Amiri (Google Fonts) |
| Clase venue | `.venue-name { font-family: 'Amiri', serif; }` |
| Tamaño "Reserva la Fecha" | `.invite .invite_title .text { font-size: 5.5rem; }` |

## Historia de la pareja (texto real — no modificar)
El texto de la historia real de la pareja está en las secciones `#about-us` de:
- `about-us.html` (líneas ~159–178)
- `index-multipage.html`, `index-onepage-video.html`, `wedding-details.html`

El encabezado es: **"Él le propuso matrimonio y ella dijo: ¡Sí!"**

El texto real está en español (4 párrafos sobre su historia de amor, reencuentro, familia e hijas, gratitud a Dios).

## Idioma
Todo el sitio está traducido al español. Reglas:
- Texto en inglés → traducir a español
- Lorem Ipsum (latín) → dejar como está (es relleno placeholder)
- La pasada de traducción ya está completa

## Pendiente / decisiones sin tomar
- **js/variables.js línea 94:** El marcador del mapa interactivo (Google Maps) todavía dice `"Birchwood Church <br> Seal Beach, CA 90740"` con coordenadas de California. No se ha actualizado porque requiere conseguir las coordenadas reales de HIKARU en Purabá, Costa Rica.

## Tecnología
- Bootstrap 5, jQuery, Owl Carousel, zoomSlider
- Node.js disponible localmente (para scripts de utilidad)
- Sin npm registry disponible offline (usar paquetes ya cacheados)
- Servidor local: `npx serve -p 3000`

## Decisiones de estilo tomadas anteriormente
- "Save the Date" → "Reserva la Fecha" con decoraciones de flores
- Flor decorativa en SVG: `images/flower-large.svg`, `flower-medium.svg`, `flower-small.svg`
- Hero: slideshow con las fotos STZ*.jpg reales (reemplazaron placeholders)
- Venue en páginas: `<span class="venue-name">HIKARU</span>` (solo el nombre en Amiri, no la dirección)
- Google Fonts link con Amiri añadido a: index.html, index-multipage.html, index-onepage-video.html, wedding-details.html
