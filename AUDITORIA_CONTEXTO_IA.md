# Neela Wedding Template — Contexto para Agente de IA

> **Tipo de documento:** Auditoría de contexto para agente IA  
> **Propósito:** Dotar a un agente de IA de todo el conocimiento necesario para asistir en el desarrollo, personalización o extensión de este proyecto  
> **Proyecto:** Neela HTML5 Wedding Template v1.0.1  
> **Fecha:** 2026-05-10

---

## RESUMEN EJECUTIVO

Eres el desarrollador asignado a un proyecto de sitio web de bodas. El sitio está construido sobre la plantilla comercial **Neela v1.0.1** de Wisely Themes. Es un sitio HTML5 estático con un único archivo PHP para formularios. No existe framework JavaScript moderno ni build system. Todo el código cliente está en ES5 con jQuery. Cualquier tarea que recibas debe respetar las convenciones y el stack existente salvo que se indique lo contrario explícitamente.

---

## SECCIÓN 1 — PROPÓSITO DEL PROYECTO

- **¿Qué es?** Un sitio web de boda personalizable para una pareja específica.
- **¿Para qué sirve?** Informar a los invitados sobre la fecha, lugar, historia de la pareja, lista de participantes (padrinos/damas), regalos, y recopilar confirmaciones de asistencia (RSVP).
- **¿Quién lo usa?** La pareja contratante (editan el contenido) y sus invitados (consumen el sitio).
- **¿Dónde se despliega?** Cualquier hosting con PHP 7+. No requiere base de datos ni servidor Node.js.

---

## SECCIÓN 2 — STACK TECNOLÓGICO (referencia rápida)

```
FRONTEND
  HTML5           → Estructura de todas las páginas
  CSS3 / SCSS     → Estilos (SCSS es la fuente, CSS es el compilado)
  JavaScript ES5  → Toda la lógica del cliente (no hay ES6+, no hay módulos)
  Bootstrap 5     → Grid y componentes UI responsive
  jQuery 3.6.0    → DOM, eventos, AJAX — es la dependencia central del JS

BACKEND
  PHP (nativo)    → Solo contact.php — envío de emails del formulario RSVP

APIS EXTERNAS
  Google Maps JS API  → Mapa de ubicaciones
  Google reCAPTCHA v2 → Anti-spam en formulario
  Google Fonts CDN    → Tipografía Poppins
  Vimeo embed         → Video de la historia de la pareja

HERRAMIENTAS DE DISEÑO
  Photoshop (.psd)    → Archivos fuente en /Neela PSD/
  Sass/SCSS           → El CSS se preprocesa con Sass (compilación manual)
```

---

## SECCIÓN 3 — ESTRUCTURA DE ARCHIVOS (lo que necesitas saber)

### Directorio principal de trabajo: `/Neela HTML 5 Template/`

| Ruta | Descripción |
|---|---|
| `*.html` | Las 17 páginas del sitio |
| `contact.php` | Único backend — maneja envío de formularios |
| `css/style.scss` | **FUENTE** de los estilos (editar esto, no el .css) |
| `css/style.css` | CSS compilado (regenerar tras editar el .scss) |
| `css/bootstrap.min.css` | Bootstrap 5 — NO editar |
| `css/fontawesome-all.min.css` | Font Awesome 6 — NO editar |
| `css/neela-icon-set.css` | Iconos custom de boda — editar solo si necesitas nuevos iconos |
| `js/variables.js` | **ARCHIVO DE CONFIGURACIÓN** — personalizar aquí (mapa, countdown, etc.) |
| `js/scripts.js` | Lógica principal — editar aquí la funcionalidad |
| `webfonts/` | Fuentes locales (FA6, Playfair Display, Neela icons) |
| `images/` | Logos, ornamentos SVG, favicon, manifest.json |

### Archivos que NO debes editar sin instrucción explícita

- `css/bootstrap.min.css`
- `css/bootstrap.rtl.min.css`
- `css/fontawesome-all.min.css`
- `css/owl.carousel.min.css`
- `js/jquery-*.js`
- `js/bootstrap.bundle.min.js`
- `js/owl.carousel.min.js`
- Todo lo que esté en `/Documentation/`

---

## SECCIÓN 4 — PÁGINAS Y SU FUNCIÓN

| Archivo HTML | Función |
|---|---|
| `index.html` | Home one-page completo — PÁGINA PRINCIPAL |
| `index-multipage.html` | Home multi-página — alternativa modular |
| `index-invite.html` | Página minimalista solo invitación |
| `index-onepage-video.html` | One-page con hero de video de fondo |
| `about-us.html` | Historia y perfiles de la pareja |
| `wedding-details.html` | Ceremonia, photoshoot, recepción |
| `wedding-party.html` | Damas de honor y padrinos |
| `gallery.html` | Galería 2 columnas |
| `gallery-2.html` | Galería 3 columnas |
| `gallery-3.html` | Galería 4 columnas |
| `rsvp.html` | Formulario RSVP dedicado |
| `gift-registry.html` | Lista de regalos y fondo de luna de miel |
| `blog-single-post.html` | Entrada de blog individual |
| `blog-listing-sidebar-right.html` | Blog con sidebar derecho |
| `blog-listing-sidebar-left.html` | Blog con sidebar izquierdo |
| `blog-listing-no-sidebar-1.html` | Blog sin sidebar (variante 1) |
| `blog-listing-no-sidebar-2.html` | Blog sin sidebar (variante 2) |

---

## SECCIÓN 5 — GUÍA DE PERSONALIZACIÓN

### 5.1 Cambiar nombres de la pareja

Busca y reemplaza el texto de ejemplo en todos los archivos `.html`. Los nombres aparecen en:
- El `<title>` de cada página
- La sección `#home` (hero)
- La sección `#about-us`
- El preloader (SVG con nombres)
- El footer

### 5.2 Cambiar fecha de la boda (countdown)

Editar en `js/variables.js`:
```javascript
// Buscar la variable de fecha del countdown
// Formato: new Date('Month DD, YYYY HH:MM:SS')
```

### 5.3 Cambiar el mapa y ubicaciones

Editar en `js/variables.js`:
```javascript
var mapLat = 33.779613;       // Latitud del centro del mapa
var mapLng = -118.066904;     // Longitud del centro del mapa
var mapZoom = 15;             // Zoom inicial

var mapMarkers = [
  {
    title: 'Ceremony',
    type: 'ceremony',        // tipos: ceremony, reception, accommodation, transport
    lat: ...,
    lng: ...,
    address: '...',
    time: '...'
  },
  // Agregar/quitar marcadores aquí
];
```

**Importante:** La API Key de Google Maps (`AIzaSyBHOXsTqoSDPQ5eC5TChvgOf3pAVGapYog`) es de demo y debe reemplazarse por una propia, restringida al dominio del cliente.

### 5.4 Cambiar imágenes del slideshow hero

Editar en `js/variables.js`:
```javascript
var slideshowImages = [
  'images/tu-foto-1.jpg',
  'images/tu-foto-2.jpg',
  'images/tu-foto-3.jpg'
];
```

Dimensión recomendada: 1920×1080px. Para Retina, añadir versión `@2x`.

### 5.5 Cambiar colores

Editar `css/style.scss`:
```scss
$color: #8eaeba;        // Color primario — cambiar por el color de la boda
$text-color: #73777b;   // Color de texto
```
Luego recompilar SCSS → CSS.

### 5.6 Configurar el formulario RSVP / Contacto

Editar `contact.php`:
```php
$emailto  = 'email-del-cliente@dominio.com';
$fromName = 'Boda Nombre1 & Nombre2';
$fromEmail= 'noreply@dominio.com';
$subject  = 'RSVP - Boda';
$secretkey= 'TU_CLAVE_RECAPTCHA_SECRETA';
```

---

## SECCIÓN 6 — CONVENCIONES DE CÓDIGO

### HTML

- Doctype: `<!DOCTYPE html>`
- Charset: `UTF-8`
- Viewport: `width=device-width, initial-scale=1, maximum-scale=1`
- Estructura de sección típica:
  ```html
  <section id="nombre-seccion" class="section-padding">
    <div class="container">
      <div class="row">
        <div class="col-md-12">
          <!-- Contenido -->
        </div>
      </div>
    </div>
  </section>
  ```
- Clases Bootstrap 5 para grid (`col-md-6`, `col-lg-4`, etc.)
- IDs semánticos en secciones para scroll one-page (`#about-us`, `#gallery`, etc.)

### CSS / SCSS

- Variables SCSS: `$color`, `$text-color`
- Prefijo de clases: no hay prefijo consistente (es CSS legacy)
- Los mixins están definidos al inicio de style.scss
- Orden de propiedades: no hay orden estricto documentado
- Media queries al final de cada bloque de sección

### JavaScript

- Todo ES5 (no `const`, no `let`, no arrow functions, no módulos)
- Patrón: objeto literal `Neela.nombreMetodo()`
- Selectores jQuery: `$('#id')`, `$('.clase')`
- Configuración siempre en `variables.js`, nunca hardcodeada en `scripts.js`
- Los plugins jQuery se inicializan dentro de `Neela.build()`
- Event listeners se registran en `Neela.events()`
- Animaciones de scroll via Waypoints + clases CSS

### PHP

- Sanitización obligatoria con función `sanitize()` antes de usar cualquier dato del formulario
- Respuesta siempre en JSON: `{"sent": true}` o `{"sent": false, "error": "..."}`
- No usar `echo` directamente para HTML en la respuesta

---

## SECCIÓN 7 — COMPONENTES JS Y CÓMO USARLOS

### Owl Carousel (sliders)

Inicializado en `scripts.js → createOwlSliders()`. Para añadir un nuevo slider:
1. Agregar el HTML con clase `owl-carousel` y un atributo `data-*` identificativo
2. Inicializarlo en `createOwlSliders()` con las opciones deseadas

### Lightbox (galería)

Inicializado en `scripts.js → createLightboxGallery()`. Para una galería con lightbox:
```html
<a href="images/foto-grande.jpg" data-lightbox="gallery-name" data-title="Descripción">
  <img src="images/foto-thumb.jpg" alt="...">
</a>
```

### Waypoints (animaciones al scroll)

Para que un elemento se anime al entrar en viewport:
```html
<div data-animation-delay="0.3" data-animation-direction="from-left">
  <!-- contenido -->
</div>
```
El método `animateElems()` en scripts.js lo detecta automáticamente.

### Countdown Timer

Renderizado automáticamente en el elemento con ID del countdown. Se configura la fecha objetivo en `variables.js`. Las etiquetas (Days, Hours, Minutes, Seconds) también son configurables en `variables.js`.

---

## SECCIÓN 8 — LIMITACIONES CONOCIDAS

| Limitación | Impacto | Recomendación |
|---|---|---|
| Sin CMS — contenido hardcoded en HTML | Alto para clientes no técnicos | Integrar con Netlify CMS o similar si necesario |
| API Key Google Maps expuesta en JS | Alto (seguridad) | Restringir por dominio en Google Cloud Console |
| No hay build system | Medio | Añadir npm + sass watch si hay desarrollo continuo |
| Header/footer duplicado en 17 páginas | Medio | Usar PHP includes o un generador estático |
| contact.php usa mail() nativo de PHP | Bajo | En hostings restrictivos puede fallar — usar SMTP/PHPMailer |
| Sin lazy loading en imágenes | Bajo rendimiento | Añadir `loading="lazy"` a todas las `<img>` |
| Sin Content Security Policy | Seguridad | Configurar headers en .htaccess |
| NiceScroll.js muy pesado (121 KB) | Rendimiento | Eliminar si no es imprescindible |

---

## SECCIÓN 9 — FLUJO DE TRABAJO RECOMENDADO PARA CAMBIOS

### Para cambios de contenido (texto, imágenes, nombres)
1. Editar directamente los archivos `.html` en `/Neela HTML 5 Template/`
2. Reemplazar imágenes en `/images/` respetando las dimensiones recomendadas
3. Actualizar `variables.js` para configuraciones dinámicas (fechas, mapa, slideshow)

### Para cambios de estilos
1. Editar `css/style.scss`
2. Compilar → genera `css/style.css`
3. El source map `style.css.map` se regenera automáticamente

### Para cambios de funcionalidad JavaScript
1. Editar `js/scripts.js` (o `js/variables.js` si es solo configuración)
2. Seguir el patrón del objeto `Neela`
3. Inicializaciones nuevas → en `Neela.build()`
4. Event listeners nuevos → en `Neela.events()`

### Para cambios en el formulario
1. Editar `contact.php` para configuración del email
2. Editar HTML del formulario en la página correspondiente
3. Mantener la sanitización XSS con `sanitize()`

---

## SECCIÓN 10 — GLOSARIO DE IDs Y CLASES CLAVE

### IDs de secciones (para navegación one-page)

| ID | Sección |
|---|---|
| `#home` | Hero principal |
| `#about-us` | Perfiles de la pareja |
| `#our-story` | Timeline / historia |
| `#the-invite` | Invitación / save-the-date |
| `#location` | Mapa y detalles de lugar |
| `#bridal-party` | Damas de honor y padrinos |
| `#testimonials` | Testimonios |
| `#gift-registry` | Lista de regalos |
| `#gallery` | Galería de fotos |
| `#blog` | Entradas del blog |
| `#rsvp` | Formulario de asistencia |

### Clases CSS relevantes

| Clase | Uso |
|---|---|
| `.section-padding` | Padding vertical estándar de sección |
| `.owl-carousel` | Contenedor para Owl Carousel |
| `.one-page` | En `<body>` para activar lógica one-page |
| `.form-floating` | Inputs con etiqueta flotante (Bootstrap 5) |
| `.required` | Campo obligatorio del formulario |
| `.fromName` / `.fromEmail` | Selectores jQuery del formulario |

---

## SECCIÓN 11 — CHECKLIST DE ENTREGA A CLIENTE

Antes de entregar el sitio personalizado, verificar:

- [ ] Nombres de la pareja actualizados en todas las páginas
- [ ] Fecha de boda configurada en `variables.js` (countdown)
- [ ] Fotos de la pareja reemplazadas (600×600px)
- [ ] Fotos del slideshow hero reemplazadas (1920×1080px)
- [ ] Ubicaciones del mapa actualizadas en `variables.js`
- [ ] API Key de Google Maps propia configurada y restringida por dominio
- [ ] Email receptor configurado en `contact.php`
- [ ] Clave reCAPTCHA configurada en `contact.php`
- [ ] Color primario actualizado en `style.scss` y recompilado
- [ ] Logo reemplazado (`logo.png` y `logo-white.png`)
- [ ] Favicon actualizado
- [ ] `manifest.json` actualizado con nombre del sitio
- [ ] Meta description y keywords actualizadas
- [ ] Open Graph tags actualizados en páginas de blog
- [ ] Enlace de video Vimeo actualizado (o sección eliminada)
- [ ] Prueba de envío de formulario RSVP en hosting real
- [ ] Prueba en móvil (iOS Safari + Chrome Android)

---

## SECCIÓN 12 — DEPENDENCIAS CRÍTICAS (NO ROMPER)

Estas son las dependencias donde un error de orden o versión rompe todo el sitio:

1. **jQuery DEBE cargarse antes que cualquier otro script**
2. **variables.js DEBE cargarse antes que scripts.js** — sin esto, el script principal falla silenciosamente
3. **Bootstrap CSS DEBE estar en el `<head>`** antes de style.css
4. **Bootstrap Bundle JS DEBE cargarse antes de cualquier componente Bootstrap** (modals, dropdowns, etc.)
5. **richmarker.js DEBE cargarse después de que la API de Google Maps esté disponible**

---

*Documento de auditoría generado el 2026-05-10 | Para uso como contexto de agente IA | Neela HTML5 Template v1.0.1*
