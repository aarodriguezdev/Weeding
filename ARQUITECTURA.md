# Neela Wedding HTML5 Template v1.0.1 — Análisis Arquitectónico Exhaustivo

> **Autor del análisis:** Arquitecto Senior  
> **Fecha:** 2026-05-10  
> **Versión analizada:** 1.0.1 (lanzada junio 2022, release inicial octubre 2021)  
> **Autor de la plantilla:** Wisely Themes

---

## Tabla de Contenidos

1. [Visión General](#1-visión-general)
2. [Estructura de Directorios](#2-estructura-de-directorios)
3. [Stack Tecnológico Completo](#3-stack-tecnológico-completo)
4. [Arquitectura de Páginas](#4-arquitectura-de-páginas)
5. [Arquitectura CSS / Estilos](#5-arquitectura-css--estilos)
6. [Arquitectura JavaScript](#6-arquitectura-javascript)
7. [Backend y Formularios](#7-backend-y-formularios)
8. [Integraciones Externas](#8-integraciones-externas)
9. [Assets y Recursos Estáticos](#9-assets-y-recursos-estáticos)
10. [Sistema de Diseño y UI](#10-sistema-de-diseño-y-ui)
11. [Responsive & Breakpoints](#11-responsive--breakpoints)
12. [SEO y Metadatos](#12-seo-y-metadatos)
13. [Navegación y Enrutamiento](#13-navegación-y-enrutamiento)
14. [Animaciones y Efectos](#14-animaciones-y-efectos)
15. [Compatibilidad de Navegadores](#15-compatibilidad-de-navegadores)
16. [Build System](#16-build-system)
17. [Diagrama de Dependencias](#17-diagrama-de-dependencias)
18. [Fortalezas y Deudas Técnicas](#18-fortalezas-y-deudas-técnicas)

---

## 1. Visión General

**Neela** es una plantilla HTML5 premium para sitios web de bodas. Está construida sobre Bootstrap 5 con jQuery como motor de interactividad. Ofrece dos modalidades de uso principales:

- **One-Page**: toda la boda en un único scroll con anclas suaves
- **Multi-Page**: navegación entre páginas independientes

No utiliza ningún framework de JavaScript moderno (React, Vue, Angular) ni sistema de build automatizado. Es una plantilla estática de entrega directa, pensada para que un diseñador/desarrollador web la personalice y la suba a cualquier hosting que soporte PHP para el formulario de contacto.

**Paradigma:** Server-Side Static HTML + PHP Mailer + jQuery DOM manipulation.

---

## 2. Estructura de Directorios

```
Weeding/
│
├── changelog.txt                          # Registro de versiones
│
├── Documentation/                         # Documentación del template
│   ├── documentation.html                 # Guía de instalación y uso
│   ├── assets/
│   │   └── images/                        # 12 capturas de pantalla de docs
│   ├── css/
│   │   ├── bella-icon-set.css             # Iconos de la documentación
│   │   ├── documenter_style.css           # Estilos de la documentación
│   │   ├── shDocumenter.css               # Syntax highlighter
│   │   └── fonts/                         # Fuentes del doc
│   └── js/
│       ├── jquery.1.6.4.js                # jQuery legado para docs
│       ├── jquery.easing.js               # Easings para docs
│       ├── jquery.scrollTo-1.4.2-min.js   # Scroll para docs
│       └── script.js                      # Script de la documentación
│
├── Neela HTML 5 Template/                 # *** DIRECTORIO PRINCIPAL DEL TEMPLATE ***
│   ├── *.html (17 páginas)                # Todas las páginas del sitio
│   ├── contact.php                        # Manejador de formularios (backend)
│   ├── css/
│   │   ├── style.scss                     # Fuente SCSS (146 KB)
│   │   ├── style.css                      # CSS compilado (176 KB)
│   │   ├── style.css.map                  # Source map (37 KB)
│   │   ├── bootstrap.min.css              # Bootstrap 5 (155 KB)
│   │   ├── bootstrap.rtl.min.css          # Bootstrap RTL (155 KB)
│   │   ├── fontawesome-all.min.css        # Font Awesome 6 (59 KB)
│   │   ├── neela-icon-set.css             # Iconos custom (1.5 KB)
│   │   ├── owl.carousel.min.css           # Owl Carousel (3.4 KB)
│   │   └── rtl.css                        # Estilos RTL custom (19 KB)
│   ├── js/
│   │   ├── scripts.js                     # Script principal (1,212 líneas)
│   │   ├── variables.js                   # Config variables (94 líneas)
│   │   ├── jquery-3.6.0.min.js            # jQuery core (89.5 KB)
│   │   ├── jquery-ui.min.js               # jQuery UI (25.2 KB)
│   │   ├── jquery-migrate-3.3.2.min.js    # jQuery Migrate (11.2 KB)
│   │   ├── jquery.placeholder.min.js      # Placeholder fallback (1.2 KB)
│   │   ├── jquery.nicescroll.js           # Custom scrollbar (121 KB)
│   │   ├── jquery.zoomslider.js           # Zoom slider (8.7 KB)
│   │   ├── bootstrap.bundle.js            # Bootstrap JS (207 KB)
│   │   ├── bootstrap.bundle.min.js        # Bootstrap JS min (78.7 KB)
│   │   ├── owl.carousel.min.js            # Owl Carousel (44.3 KB)
│   │   ├── lightbox.min.js                # Lightbox (9.5 KB)
│   │   ├── waypoints.min.js               # Scroll waypoints (9.0 KB)
│   │   ├── waypoints-sticky.min.js        # Sticky elements (1.2 KB)
│   │   ├── modernizr-3.6.0.min.js         # Feature detection (17.4 KB)
│   │   ├── richmarker.js                  # Google Maps markers (11.9 KB)
│   │   └── ismobile.js                    # Mobile detection (2.1 KB)
│   ├── webfonts/
│   │   ├── fa-brands-400.*                # Font Awesome brands
│   │   ├── fa-regular-400.*               # Font Awesome regular
│   │   ├── fa-solid-900.*                 # Font Awesome solid
│   │   ├── neela-icon-set.*               # Iconos custom Neela
│   │   └── playfairdisplay-regular.*      # Fuente Playfair Display
│   └── images/
│       ├── flower-large.svg               # Ornamento floral grande
│       ├── flower-medium.svg              # Ornamento floral mediano
│       ├── flower-small.svg               # Ornamento floral pequeño
│       ├── flower-large-dark.svg          # Variante oscura
│       ├── flower-large-light.svg         # Variante clara
│       ├── neela-pattern.png              # Patrón de fondo
│       ├── loading.gif                    # Gif del preloader
│       ├── logo.png                       # Logo (52 KB)
│       ├── logo-white.png                 # Logo blanco (52 KB)
│       ├── favicon.ico / favicon.svg      # Favicons
│       ├── apple-touch-icon-180x180.png   # iOS 180px
│       ├── apple-touch-icon-192x192.png   # Android 192px
│       ├── apple-touch-icon-512x512.png   # PWA 512px
│       └── manifest.json                  # PWA Web Manifest
│
└── Neela PSD/                             # Archivos fuente Photoshop (15 .psd)
    └── *.psd
```

---

## 3. Stack Tecnológico Completo

### Lenguajes

| Lenguaje | Versión | Uso |
|---|---|---|
| HTML | 5 | Estructura de todas las páginas |
| CSS | 3 | Estilos visuales |
| SCSS/Sass | - | Preprocesador CSS (compilado manual) |
| JavaScript | ES5 | Toda la lógica del cliente |
| PHP | 7+ (implícito) | Envío de emails vía formulario |

### Frameworks y Librerías CSS

| Librería | Versión | Peso | Uso |
|---|---|---|---|
| Bootstrap | 5.x | 155 KB (min) | Grid, componentes UI, responsive |
| Bootstrap RTL | 5.x | 155 KB (min) | Soporte idiomas derecha-izquierda |
| Font Awesome | 6.x | 59 KB (min) | Iconos vectoriales |
| Owl Carousel | 2.x | 3.4 KB (min) | Estilos de sliders/carouseles |
| Neela Icon Set | Custom | 1.5 KB | Iconos específicos de boda |

### Frameworks y Librerías JavaScript

| Librería | Versión | Peso | Uso |
|---|---|---|---|
| jQuery | 3.6.0 | 89.5 KB | Manipulación DOM, AJAX, eventos |
| jQuery UI | - | 25.2 KB | Interacciones UI avanzadas |
| jQuery Migrate | 3.3.2 | 11.2 KB | Compatibilidad jQuery legado |
| jQuery Placeholder | - | 1.2 KB | Fallback HTML5 placeholder |
| jQuery NiceScroll | - | 121 KB | Scrollbar custom |
| jQuery ZoomSlider | - | 8.7 KB | Slider con zoom |
| Bootstrap Bundle | 5.x | 78.7 KB (min) | JS de componentes Bootstrap |
| Owl Carousel | 2.x | 44.3 KB | Sliders y carruseles |
| Lightbox | - | 9.5 KB | Galería de imágenes |
| Waypoints | - | 9.0 KB | Triggers por scroll |
| Waypoints Sticky | - | 1.2 KB | Elementos sticky |
| Modernizr | 3.6.0 | 17.4 KB | Detección de características |
| Rich Marker | - | 11.9 KB | Marcadores custom en Google Maps |
| isMobile | - | 2.1 KB | Detección de dispositivo móvil |
| Retina.js | - | 2.0 KB | Soporte pantallas Retina |

### Servicios Externos (APIs)

| Servicio | Uso | Clave/Configuración |
|---|---|---|
| Google Maps JavaScript API | Mapa de ubicaciones de la boda | API Key expuesta en variables.js |
| Google Fonts | Tipografía Poppins (peso 300) | CDN link |
| Google reCAPTCHA v2 | Protección anti-spam en formularios | Secret key en contact.php |
| Vimeo Player | Embed de video de la historia | URL hardcoded en HTML |
| via.placeholder.com | Imágenes placeholder de demo | URLs en HTML |

### Tipografías

| Fuente | Tipo | Distribución | Uso |
|---|---|---|---|
| Poppins (weight 300) | Google Font | CDN | Cuerpo de texto |
| Playfair Display | Custom WOFF/WOFF2 | Local (webfonts/) | Títulos y headings |
| Font Awesome 6 | Icon Font | Local (webfonts/) | Iconos generales |
| Neela Icon Set | Custom Icon Font | Local (webfonts/) | Iconos temáticos de boda |

### Herramientas de Diseño

| Herramienta | Versión | Archivos |
|---|---|---|
| Adobe Photoshop | CS5+ (implícito) | 15 archivos .psd en /Neela PSD/ |
| Sass/SCSS | - | style.scss → style.css (compilado externo) |

---

## 4. Arquitectura de Páginas

### 4.1 Mapa de Páginas (17 HTML)

```
┌──────────────────────────────────────────────────────┐
│                  VARIANTES DE HOME                   │
├─────────────────────┬──────────────┬─────────────────┤
│  index.html         │index-multi   │index-onepage    │
│  (One-Page Full)    │page.html     │-video.html      │
│  ~3048 líneas       │~1800 líneas  │~1043 líneas     │
│                     │              │                 │
│  index-invite.html  │              │                 │
│  (Minimal invite)   │              │                 │
│  ~500 líneas        │              │                 │
└─────────────────────┴──────────────┴─────────────────┘

┌──────────────────────┐  ┌─────────────────────────────┐
│   PÁGINAS INTERNAS   │  │       PÁGINAS DE BLOG        │
├──────────────────────┤  ├─────────────────────────────┤
│ about-us.html        │  │ blog-single-post.html        │
│ wedding-details.html │  │ blog-listing-sidebar-right   │
│ wedding-party.html   │  │ blog-listing-sidebar-left    │
│ rsvp.html            │  │ blog-listing-no-sidebar-1    │
│ gift-registry.html   │  │ blog-listing-no-sidebar-2    │
└──────────────────────┘  └─────────────────────────────┘

┌──────────────────────────────────┐
│          GALERÍAS                │
├──────────────────────────────────┤
│ gallery.html   (2 columnas)      │
│ gallery-2.html (3 columnas)      │
│ gallery-3.html (4 columnas)      │
└──────────────────────────────────┘
```

### 4.2 Anatomía de Componentes por Página

#### index.html (One-Page completo — referencia principal)

```
<head>
  └── Meta tags, CSS links (Bootstrap, FA, Owl, Neela, style.css)

<body class="one-page">
  ├── #preloader          → Animación SVG corazón + nombres pareja
  ├── <header>            → Logo + nav links + mobile toggle
  ├── #home               → Hero: slideshow de fondo, timer countdown, CTA
  ├── #about-us           → Perfiles novios + redes sociales
  ├── #our-story          → Timeline: texto, imágenes, carousel, video Vimeo
  ├── #the-invite         → Save-the-date card: fecha, hora, lugar
  ├── #location           → Google Maps + detalles ceremonia/recepción
  ├── #bridal-party       → Grid damas de honor + padrinos con hover
  ├── #testimonials       → Slider Owl Carousel con citas
  ├── #gift-registry      → Lista de regalos + fondo de luna de miel
  ├── #gallery            → Galería horizontal con Lightbox
  ├── #blog               → Cards de entradas de blog
  ├── #rsvp               → Formulario RSVP + reCAPTCHA
  └── <footer>            → Datos contacto + links + newsletter
      └── JS scripts (jQuery, Bootstrap, plugins, scripts.js)
```

---

## 5. Arquitectura CSS / Estilos

### 5.1 Sistema de Capas CSS

```
Orden de carga en <head>:
1. bootstrap.min.css       ← Reset + Grid + Componentes base
2. fontawesome-all.min.css ← Iconos FA6
3. neela-icon-set.css      ← Iconos temáticos custom
4. owl.carousel.min.css    ← Estilos de carousel
5. style.css               ← Todos los estilos custom (sobreescribe todo)
6. rtl.css (opcional)      ← Sobreescritura RTL si aplica
```

### 5.2 Variables SCSS Principales (style.scss)

```scss
$color:       #8eaeba;   // Color primario (teal/sage)
$text-color:  #73777b;   // Color de texto (gris oscuro)
// Backgrounds:
//   Secciones alternas: #f9f9f9 (off-white)
//   Overlay: darken($color)
```

### 5.3 Mixins SCSS Definidos

```scss
@mixin border-radius($radius)
@mixin box-shadow($shadow)
@mixin opacity($opacity)
@mixin transition($transition)
@mixin transform($transforms)
@mixin animation($animation)
```

### 5.4 Fuentes Tipográficas

| Elemento | Fuente | Peso | Entrega |
|---|---|---|---|
| Body / párrafos | Poppins | 300 (light) | Google Fonts CDN |
| H1, H2, H3... | Playfair Display | Regular | WOFF/WOFF2 local |

### 5.5 Paleta de Colores

```
#8eaeba  → Primario (teal/sage green — botones, acentos, líneas decorativas)
#73777b  → Texto principal
#f9f9f9  → Fondo secciones alternas
#ffffff  → Fondo secciones principales
Overlay  → darken(#8eaeba) — fondos oscuros sobre imágenes
```

---

## 6. Arquitectura JavaScript

### 6.1 Patrón de Organización

El código custom sigue un **patrón de objeto literal** — todo encapsulado en un objeto `Neela`:

```javascript
var Neela = {
  init: function() { ... },         // Punto de entrada: llama a build() y events()
  build: function() { ... },        // Inicializa todos los componentes
  events: function() { ... },       // Registra event listeners

  // Componentes:
  preloader(),
  navigation(),
  createMobileMenu(),
  heroHeight(),
  googleMap(),
  createLightboxGallery(),
  createBackgroundSlideshow(),
  createOwlSliders(),
  createGallery(),
  bgImageGrid(),
  countdown(),
  parallaxBg(),
  parallaxTimeline(),
  contactForm(),
  animateElems(),
  windowResize(),
  neelaStyle()
}

// Bootstrap
$(document).ready(function() { Neela.init(); });
```

### 6.2 Archivo variables.js — Configuración externalizada

```javascript
// RTL
var rtl = false;

// Navegación one-page
var onepage = true;

// Hero
var heroFullscreen = true;
var slideshowImages = ['img1.jpg', 'img2.jpg', ...]; // Array de fondos

// Countdown
var countdownLabels = { days: 'Days', hours: 'Hours', ... };

// Google Maps
var mapColor = '#8eaeba';
var mapZoom = 15;
var mapLat = 33.779613;
var mapLng = -118.066904;
var mapMarkers = [
  { title: 'Reception', type: 'reception', lat: ..., lng: ... },
  { title: 'Ceremony',  type: 'ceremony',  lat: ..., lng: ... },
  // + 4 marcadores más (accommodations, transport)
];

// Formulario
var formMessages = { success: '...', error: '...' };
```

### 6.3 Flujo de Carga de Scripts (orden en HTML)

```
1. jquery-3.6.0.min.js          ← Base obligatoria
2. jquery-ui.min.js
3. jquery-migrate-3.3.2.min.js
4. jquery.placeholder.min.js
5. jquery.nicescroll.js
6. jquery.zoomslider.js
7. bootstrap.bundle.min.js
8. owl.carousel.min.js
9. lightbox.min.js
10. waypoints.min.js
11. waypoints-sticky.min.js
12. modernizr-3.6.0.min.js
13. richmarker.js
14. ismobile.js
15. retina.min.js
16. variables.js                 ← Config antes del script principal
17. scripts.js                   ← Script principal (depende de todo lo anterior)
```

---

## 7. Backend y Formularios

### 7.1 contact.php

El único componente server-side. Maneja el envío de emails de los formularios RSVP y contacto.

**Flujo:**
```
POST request (formulario HTML)
  → contact.php
    → Sanitización XSS (función sanitize())
    → Verificación reCAPTCHA v2 (curl a Google API)
    → Construcción email HTML
    → mail() PHP nativo
    → JSON response: { "sent": true/false }
```

**Campos del formulario RSVP:**

| Campo | Tipo HTML | Validación |
|---|---|---|
| Nombre | text | Required (JS) |
| Email | email | Required + formato (JS) |
| Asistencia | radio (Sí/No) | Required (JS) |
| Nº invitados | select (0-7) | Opcional |
| Preferencia comida | checkbox múltiple | Opcional |
| Mensaje | textarea | Opcional |

**Variables configurables en contact.php:**
```php
$emailto  = 'your@email.com';   // Email destino
$fromName = 'Neela Wedding';     // Nombre remitente
$fromEmail= 'noreply@...';       // Email remitente
$subject  = 'RSVP / Contact';    // Asunto
$secretkey= 'RECAPTCHA_KEY';     // Clave reCAPTCHA
```

---

## 8. Integraciones Externas

### 8.1 Google Maps JavaScript API

- **Clave API:** `AIzaSyBHOXsTqoSDPQ5eC5TChvgOf3pAVGapYog` *(expuesta en variables.js — clave de demo)*
- **Librería auxiliar:** richmarker.js para marcadores HTML custom
- **Marcadores configurados:**
  - 1x Recepción (Old Ranch Country Club)
  - 1x Ceremonia (Birchwood Church)
  - 3x Alojamientos
  - 1x Transporte (Seal Beach VORTAC)
- **Color del mapa:** `#8eaeba` (aplica estilo custom)
- **Zoom inicial:** 15

### 8.2 Google Fonts

```html
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300&display=swap" rel="stylesheet">
```

### 8.3 Google reCAPTCHA v2

- Widget visual "No soy un robot" integrado en el formulario RSVP
- Verificación server-side en contact.php via curl

### 8.4 Vimeo

- Player embed en sección "Our Story / Timeline"
- URL de demo: `https://player.vimeo.com/video/136240001`

### 8.5 Redes Sociales

- **Compartir en blog:** Facebook, Twitter, Pinterest
- **Perfiles de pareja:** Instagram, Twitter, Facebook
- **Open Graph tags** en blog-single-post.html para previsualización social

---

## 9. Assets y Recursos Estáticos

### 9.1 Imágenes Clave

| Archivo | Tamaño | Uso |
|---|---|---|
| logo.png | 52 KB | Logo en header (fondo oscuro) |
| logo-white.png | 52 KB | Logo en hero (fondo claro) |
| flower-large.svg | - | Ornamento decorativo principal |
| flower-medium.svg / flower-small.svg | - | Ornamentos secundarios |
| neela-pattern.png | - | Textura de fondo de sección |
| loading.gif | - | Animación preloader |
| favicon.svg / .ico | 3.8/1.4 KB | Favicons web |
| apple-touch-icon-*.png | 85-189 KB | Iconos PWA / iOS / Android |

### 9.2 Dimensiones de Imágenes Recomendadas (por el template)

| Tipo | Dimensión | Formato |
|---|---|---|
| Hero / Slideshow | 1920 × 1080 px | JPG + @2x retina |
| Perfiles novia/novio | 600 × 600 px | JPG |
| Galería | 635 × 635 px | JPG |
| Blog post | 800 × 500 px | JPG |
| Logo | Variable | PNG (transparente) |

### 9.3 PWA / Progressive Web App

El template incluye un `manifest.json` básico con:
- Iconos para iOS (180px), Android (192px, 512px)
- Permite ser añadido a pantalla de inicio en móviles

---

## 10. Sistema de Diseño y UI

### 10.1 Componentes Reutilizables

| Componente | Tecnología | Páginas que lo usan |
|---|---|---|
| Preloader | CSS + SVG + jQuery | Todas |
| Header / Navbar | Bootstrap 5 Navbar + jQuery | Todas |
| Hero Slideshow | jQuery custom + CSS3 | index, index-multipage, index-onepage-video |
| Hero Video | HTML5 `<video>` + CSS3 | index-onepage-video |
| Countdown Timer | jQuery custom | index, index-invite |
| Timeline | jQuery + Owl Carousel | index, about-us |
| Google Map | Google Maps API + RichMarker | index, wedding-details |
| Owl Carousel Slider | Owl Carousel 2 | index, testimonials, gallery |
| Lightbox Gallery | Lightbox.js | gallery, gallery-2, gallery-3 |
| RSVP Form | Bootstrap Forms + jQuery AJAX | index, rsvp |
| Blog Cards | Bootstrap Grid + CSS | index, todos los blog pages |
| Footer | Bootstrap Grid + CSS | Todas |

### 10.2 Ornamentos Decorativos SVG

El template utiliza flores SVG como elemento de diseño recurrente:
- `flower-large.svg` / `flower-large-dark.svg` / `flower-large-light.svg`
- `flower-medium.svg`
- `flower-small.svg`

Implementadas como `<img>` o `background-image` en secciones clave.

### 10.3 Iconos Temáticos de Boda (neela-icon-set)

```
icon-big-church          → Iglesia
icon-champagne-glasses   → Copas de champagne
icon-diamond-ring        → Anillo de diamante
icon-honeymoon           → Luna de miel
icon-two-hearts          → Dos corazones
icon-wedding             → Boda genérico
icon-wedding-day         → Día de la boda
icon-photo-camera        → Cámara de fotos
```

---

## 11. Responsive & Breakpoints

El sistema responsive se basa íntegramente en Bootstrap 5:

| Breakpoint | Ancho | Clases Bootstrap |
|---|---|---|
| Extra small (mobile) | < 576px | (default) |
| Small | ≥ 576px | `sm` |
| Medium | ≥ 768px | `md` |
| Large | ≥ 992px | `lg` |
| Extra large | ≥ 1200px | `xl` |
| XXL | ≥ 1400px | `xxl` |

**Características responsive adicionales:**
- Soporte `@2x` Retina via `retina.min.js` + media queries custom en SCSS
- Menú hamburguesa para móviles (creado via `createMobileMenu()` en scripts.js)
- `heroHeight()` recalcula altura del hero en resize
- `windowResize()` re-evalúa componentes al cambiar tamaño de ventana

---

## 12. SEO y Metadatos

### 12.1 Meta Tags Estándar (todas las páginas)

```html
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1">
<meta name="keywords" content="one-page, single page, multi-page, wedding template, retina ready, responsive, modern html5 template, bootstrap, css3, wedding, venue">
<meta name="description" content="Neela - Responsive One/Multi-Page Wedding HTML5 Template">
<meta name="author" content="Wisely Themes">
```

### 12.2 Open Graph (solo blog-single-post.html)

```html
<meta property="og:locale" content="en_US">
<meta property="og:type" content="article">
<meta property="og:site_name" content="...">
<meta property="og:title" content="...">
<meta property="og:description" content="...">
<meta property="og:url" content="...">
<meta property="og:image" content="...">
```

---

## 13. Navegación y Enrutamiento

### 13.1 One-Page Navigation

La navegación one-page usa anclas (`#section-id`) y scroll suave implementado en `scripts.js → navigation()`:
- Hash activo resaltado en la barra de navegación durante scroll
- Waypoints detectan qué sección está en viewport

### 13.2 Multi-Page Navigation

Navegación estándar HTML con `<a href="pagina.html">`. El header y footer se replican manualmente en cada página (sin includes/partials — HTML estático puro).

### 13.3 Estructura del Menú

```
Home (dropdown)
  ├── One Page
  ├── Multi Page
  ├── Invite Page
  └── Video Background

About Us
Wedding Details (dropdown)
  ├── Wedding Details
  └── Wedding Party

Gallery (dropdown)
  ├── Gallery 2-Col
  ├── Gallery 3-Col
  └── Gallery 4-Col

Blog (dropdown)
  ├── Blog Sidebar Right
  ├── Blog Sidebar Left
  ├── Blog No Sidebar 1
  ├── Blog No Sidebar 2
  └── Blog Single Post

Gift Registry
RSVP
```

---

## 14. Animaciones y Efectos

### 14.1 Sistema de Animaciones de Scroll

Las animaciones al hacer scroll se controlan via atributos `data-*`:

```html
<!-- Ejemplo de elemento animado -->
<div data-animation-delay="0.2"
     data-animation-direction="from-left">
  ...
</div>
```

Direcciones disponibles:
- `from-left`
- `from-right`
- `from-top`
- `from-bottom`
- `fade`

Implementación: Waypoints (`waypoints.min.js`) detectan el elemento en viewport y aplican clases CSS con transiciones.

### 14.2 Parallax

- **`parallaxBg()`**: Parallax de fondos de sección via CSS `background-attachment: fixed` + jQuery
- **`parallaxTimeline()`**: Parallax del timeline reactivo a movimiento del ratón (mousemove)
- Habilitado via `data-parallax="true"` en elementos HTML

### 14.3 Efectos Hero

- Slideshow de imágenes de fondo con efecto de zoom (Ken Burns effect)
- Transición suave entre slides
- Modo alternativo: video de fondo en HTML5 `<video autoplay muted loop>`

### 14.4 Preloader

```
Pantalla completa blanca →
  SVG animado (corazón pulsando) →
    Nombres de los novios →
      fade-out + reveal de la página
```

---

## 15. Compatibilidad de Navegadores

| Navegador | Soporte | Notas |
|---|---|---|
| Chrome (moderno) | Completo | Target principal |
| Firefox (moderno) | Completo | |
| Safari (moderno) | Completo | |
| Edge (moderno) | Completo | |
| IE 6-8 | Parcial | HTML5 shim incluido en HTML |
| IE 9-11 | Mayormente funcional | Algunos CSS3 degradados |
| iOS Safari | Completo | Optimizado táctil |
| Chrome Mobile | Completo | Optimizado táctil |

---

## 16. Build System

**No existe build system automatizado.** Específicamente, se confirma la **ausencia** de:

- `package.json` (npm/Node.js)
- `bower.json` (Bower)
- `gulpfile.js` (Gulp)
- `Gruntfile.js` (Grunt)
- `webpack.config.js` (Webpack)
- `.babelrc` (transpilación ES6+)

La compilación SCSS → CSS se realizó externamente (probablemente con un editor como VS Code + Live Sass Compiler, o Koala) y el archivo compilado `style.css` se incluye directamente. El source map `style.css.map` permite debugging en DevTools.

**Para futuros desarrollos, se recomienda agregar:**
- Un `package.json` con scripts de Sass watch
- Un proceso básico de minificación y bundling

---

## 17. Diagrama de Dependencias

```
index.html
│
├── CSS Layer
│   ├── bootstrap.min.css
│   ├── fontawesome-all.min.css
│   ├── neela-icon-set.css (→ webfonts/neela-icon-set.*)
│   ├── owl.carousel.min.css
│   └── style.css (→ style.scss [fuente])
│       ├── webfonts/playfairdisplay-regular.*
│       └── images/* (ornamentos, patrones)
│
├── JS Layer (orden estricto)
│   ├── jquery-3.6.0.min.js         [BASE]
│   │   ├── jquery-ui.min.js
│   │   ├── jquery-migrate-3.3.2.min.js
│   │   ├── jquery.placeholder.min.js
│   │   ├── jquery.nicescroll.js
│   │   └── jquery.zoomslider.js
│   ├── bootstrap.bundle.min.js     [FRAMEWORK]
│   ├── owl.carousel.min.js         [PLUGIN]
│   ├── lightbox.min.js             [PLUGIN]
│   ├── waypoints.min.js            [PLUGIN]
│   ├── waypoints-sticky.min.js     [PLUGIN]
│   ├── modernizr-3.6.0.min.js      [UTILITY]
│   ├── richmarker.js               [PLUGIN]
│   ├── ismobile.js                 [UTILITY]
│   ├── retina.min.js               [UTILITY]
│   ├── variables.js                [CONFIG] ← DEBE ir antes de scripts.js
│   └── scripts.js                  [MAIN APP] ← Depende de TODO lo anterior
│
└── External APIs
    ├── Google Fonts (Poppins)
    ├── Google Maps JS API
    │   └── richmarker.js
    ├── Google reCAPTCHA v2
    └── Vimeo Player
```

---

## 18. Fortalezas y Deudas Técnicas

### Fortalezas

- **Cobertura completa de casos de uso** para boda: 17 páginas cubriendo todas las necesidades
- **Diseño responsive** bien implementado con Bootstrap 5
- **Soporte RTL** para idiomas árabe/hebreo
- **Soporte PWA básico** (manifest.json + iconos multi-resolución)
- **Configuración externalizada** en variables.js — facilita personalización sin tocar scripts
- **Múltiples variantes de layout** (one-page, multi-page, invite, video)
- **Assets fuente PSD** incluidos para personalización del diseño

### Deudas Técnicas

| Deuda | Riesgo | Nota |
|---|---|---|
| jQuery como dependencia central | Medio | Obsolescencia a largo plazo; reemplazable por Vanilla JS |
| API Key de Google Maps expuesta en código fuente | Alto | Debe restringirse por dominio en Google Cloud Console |
| Sin build system | Medio | Sin minificación CSS/JS, sin tree-shaking, sin hash de assets |
| SCSS compilado manualmente | Bajo | Proceso frágil, no reproducible fácilmente |
| No hay sistema de partials/includes | Medio | Header/footer duplicado en las 17 páginas — cambios manuales en todas |
| JavaScript en ES5 (var, no módulos) | Bajo | Código funcional pero no moderno |
| NiceScroll.js (121 KB) | Bajo | Librería muy pesada para lo que hace (scrollbar cosmético) |
| Imágenes sin lazy loading nativo | Bajo | Falta `loading="lazy"` en `<img>` — afecta rendimiento inicial |
| Sin HTTPS forzado | Bajo | Depende de la configuración del hosting |
| PHP mail() nativo | Bajo | Recomendable reemplazar con PHPMailer/SMTP para mayor fiabilidad |

---

*Documento generado el 2026-05-10 | Neela HTML5 Template v1.0.1 | Wisely Themes*
