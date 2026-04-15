# AI Context - Transportes Frutillar

## 2026-04-15 17:06 - Creación inicial del sitio web

### Objetivo
Crear sitio web en Astro para Transportes Frutillar (transporte de personas + tours en Frutillar, Chile), preparado para deploy en Vercel.

### Decisiones clave
- **Framework:** Astro 5.x con adapter `@astrojs/vercel` y output `static`
- **Diseño:** UI moderna con CSS puro (sin Tailwind), fuente Inter de Google Fonts
- **Página Home:** Foco principal en transporte de personas con formulario de reserva
- **Página Tours:** 5 tours predefinidos por Frutillar con formulario de reserva
- **Formulario WhatsApp:** Ambas páginas envían datos (origen, destino, fecha, hora, pasajeros, nombre) pre-rellenados a WhatsApp vía `wa.me`
- **Google Maps Autocomplete:** Integrado como mejora progresiva (funciona sin API key, con API key agrega autocompletado de direcciones restringido a Chile)
- **Número WhatsApp:** `56988979094` (+56 9 2244 4508)
- **Fecha mínima:** Los inputs de fecha no permiten seleccionar fechas pasadas

### Archivos tocados
- `package.json` — dependencias: astro, @astrojs/vercel
- `astro.config.mjs` — configuración static + vercel adapter
- `tsconfig.json` — hereda de astro/tsconfigs/strict
- `src/env.d.ts` — tipos de Astro
- `src/layouts/Layout.astro` — layout principal con navbar + footer
- `src/components/BookingForm.astro` — formulario reutilizable (transporte/tour) con WhatsApp + Google Maps autocomplete
- `src/pages/index.astro` — Home (transporte de personas)
- `src/pages/tours.astro` — Tours por Frutillar
- `public/favicon.svg` — favicon SVG
- `.env.example` — variable `PUBLIC_GOOGLE_MAPS_API_KEY`
- `.gitignore` — archivos ignorados

### Comandos ejecutados
- `nvm install 22 && nvm use 22` (Astro 5+ requiere Node >= 22)
- `npm install`
- `npx astro build` (exitoso, 2 páginas generadas)

## 2026-04-15 17:17 - Integración de logo y fotos reales

### Objetivo
Integrar el logo de la empresa y 4 fotos reales (2 de pasajeros, 2 de tours) en el sitio.

### Decisiones clave
- Archivos renombrados sin espacios para evitar problemas en URLs: `logo.jpg`, `pasajeros-1.webp`, `pasajeros-2.webp`, `tours-1.webp`, `tours-2.webp`
- Logo redondo (circular con `border-radius: 50%`) en navbar (48px) y footer (80px)
- Fotos de pasajeros: galería de 2 columnas en la sección "¿Por qué elegirnos?" del Home
- Fotos de tours: galería en el hero de la página Tours con efecto de rotación sutil

### Archivos tocados
- `public/logo.jpg` (renombrado desde "transportes frutillar.jpg")
- `public/fotos/pasajeros-1.webp`, `pasajeros-2.webp`, `tours-1.webp`, `tours-2.webp` (renombrados)
- `src/layouts/Layout.astro` — logo en navbar y footer
- `src/pages/index.astro` — fotos de pasajeros en sección why-us
- `src/pages/tours.astro` — fotos de tours en hero

### Riesgos / Pendientes
- **CAMBIAR** el número de WhatsApp `56912345678` en `index.astro` y `tours.astro` por el número real
- **OPCIONAL:** Agregar `PUBLIC_GOOGLE_MAPS_API_KEY` en `.env` para activar autocompletado de direcciones
- **OPCIONAL:** Agregar imágenes reales de Frutillar (el placeholder actual es un div con gradiente)
- **OPCIONAL:** Agregar `nvm use 22` al `.nvmrc` si se comparte el repo
- Vulnerabilidades npm (3 high) provienen de dependencias transitivas de Astro
