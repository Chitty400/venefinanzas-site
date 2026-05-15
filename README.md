# VeneFinanzas — Web

Landing page y páginas legales. Lista para Vercel.

## Estructura

```
venefinanzas/
├── index.html          ← Landing principal
├── privacidad.html     ← Política de privacidad
├── terminos.html       ← Términos y condiciones
├── eliminar.html       ← Guía de eliminación de datos
├── vercel.json         ← Config de rutas, headers de seguridad y caché
├── assets/
│   └── screenshots/    ← PON AQUÍ tus capturas (ver abajo)
└── README.md
```

## Deploy en Vercel

### Opción A — GitHub (recomendada)
1. Sube esta carpeta a un repositorio en GitHub.
2. En [vercel.com](https://vercel.com), haz clic en **Add New → Project**.
3. Importa el repositorio y haz clic en **Deploy**. Listo.

### Opción B — Vercel CLI
```bash
npm i -g vercel
cd venefinanzas/
vercel          # primer deploy (te pide login si no estás autenticado)
vercel --prod   # para producción
```

### Opción C — Drag & Drop
Arrastra la carpeta directamente a [vercel.com/new](https://vercel.com/new).

---

## Agregar capturas de pantalla

1. Exporta tus screenshots en formato **WebP** (mejor compresión) o PNG.
   - Tamaño recomendado: **440×880 px** (2× para pantallas retina).
   - Nómbralas descriptivamente: `dashboard.webp`, `agenda.webp`, etc.

2. Colócalas en **`/assets/screenshots/`**.

3. Abre `index.html` y **descomenta** los bloques `<figure class="screen-card">`.
   Ajusta `data-src` y `alt` según corresponda:

```html
<figure class="screen-card">
  <img
    data-src="/assets/screenshots/dashboard.webp"
    alt="Panel principal de VeneFinanzas"
    width="220"
    height="440"
  />
  <div class="skeleton" aria-hidden="true"></div>
  <p class="screen-label">Dashboard</p>
</figure>
```

4. Elimina el bloque `<div class="screens-placeholder">`.

El lazy load es automático — las imágenes se cargan solo cuando el usuario
llega a la sección, con un efecto skeleton mientras cargan.

---

## Rutas

| URL           | Archivo           |
|---------------|-------------------|
| `/`           | `index.html`      |
| `/privacidad` | `privacidad.html` |
| `/terminos`   | `terminos.html`   |
| `/eliminar`   | `eliminar.html`   |

---

## Headers de seguridad (ya incluidos en vercel.json)

- `X-Content-Type-Options: nosniff`
- `X-Frame-Options: DENY`
- `Referrer-Policy: strict-origin-when-cross-origin`
- Cache inmutable para `/assets/`
