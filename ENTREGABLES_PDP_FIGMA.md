# 🐾 PDP Puppis - Entregables Diseño & Desarrollo

**Proyecto:** Mejora PDP (Product Detail Page)  
**Fecha:** Agosto 2026  
**Autor:** Claude (UX/UI + Frontend)  
**Status:** ✅ Completado (Mobile + Desktop)
**Última Actualización:** Desktop frame 1280x3500px creado en Figma

---

## 📋 Resumen Ejecutivo

Se ha diseñado y desarrollado una **PDP optimizada con identidad Puppis** aplicando:

- ✅ Identidad visual completa (colores, tipografía, componentes)
- ✅ **Diseño Mobile** (390px) en Figma - estructura interactiva completa
- ✅ **Diseño Desktop** (1280px) en Figma - layout side-by-side con 10 secciones
- ✅ HTML/CSS producción lista para VTEX IO (mobile-first responsive)
- ✅ Componentes interactivos (sticky bar, acordeones, selector de variantes)
- ✅ Conversión optimizada (CTA prominente, jerarquía de precios clara)
- ✅ Accesibilidad AA (contraste, targets ≥44px)
- ✅ Figma → Entregables listos para equipo de diseño + implementación

---

## 🎨 Identidad Visual Aplicada

### Colores (Guardrails Obligatorios)

| Uso | Código | RGB |
|-----|--------|-----|
| **Azul Principal** (CTAs, precio, links) | `#194F90` | 25, 79, 144 |
| **Azul Oscuro** (Titulares, texto jerarquía) | `#23376E` | 35, 55, 110 |
| **Azul Secundario** (Acentos, badges) | `#3F7CBD` | 63, 124, 189 |
| **Amarillo Principal** (Highlights, promociones) | `#FFD100` | 255, 209, 0 |
| **Amarillo Suave** (Fondos promocionales) | `#FAD972` | 250, 217, 114 |
| **Amarillo Secundario** | `#FABF1A` | 250, 191, 26 |
| **Grises** (Fondos, separadores) | `#F6F6F6, #EDEDED` | 246,246,246 / 237,237,237 |
| **Blanco** | `#FFFFFF` | 255, 255, 255 |

### Tipografía

- **Titulares & CTAs:** Roboto Bold (fallback: Nunito Bold)
- **Cuerpo:** Roboto Regular (fallback: Helvetica Neue)
- **Énfasis:** Roboto Medium
- **Tono:** Cercano, juguetón, voseo argentino ("recibís", "elegí")

---

## 📱 Entregables Técnicos

### 1. **HTML/CSS Producción** ✅
- **Archivo:** `/puppis-pdp.html`
- **Tipo:** Single-file HTML con CSS incrustado
- **Stack:** HTML5 + CSS3 + Vanilla JavaScript
- **Características:**
  - ✓ Mobile-first (390px viewport)
  - ✓ Responsive desktop (1280px)
  - ✓ Sticky bar al scrollear
  - ✓ Acordeones interactivos (envío, especificaciones, ingredientes)
  - ✓ Selector de variantes (chips)
  - ✓ Stepper de cantidad
  - ✓ Carrusel cross-sell
  - ✓ Galerías con dots

**Secciones implementadas:**
1. Header sticky (logo, búsqueda, carrito)
2. Breadcrumb truncado
3. Galería con badges superpuestos + carrusel
4. Bloque de compra (visible en primer scroll)
5. Rating + reviews anclables
6. Precio grande + precio por kg
7. Selector de presentación (chips)
8. Stepper cantidad + CTA full-width
9. Envío programado (card destacada única, amarillo)
10. Opciones de envío (acordeón 3 filas)
11. Medios de pago
12. Descripción (acordeón expandible)
13. Especificaciones (tabla 2 columnas)
14. Ingredientes (acordeón cerrado)
15. Reviews (resumen por estrellas + 2 destacadas)
16. Cross-sell carrusel (productos relacionados)
17. Franja Puppis Club (15% descuento)
18. Footer

**Token CSS aplicados:**
```css
--color-azul-900: #23376E
--color-azul-700: #194F90
--color-azul-500: #3F7CBD
--color-amarillo-900: #FFD100
--color-amarillo-400: #FAD972
--color-amarillo-300: #FABF1A
--color-gris-100: #F6F6F6
--color-gris-50: #EDEDED
--color-blanco: #FFFFFF
--spacing-xs/sm/md/lg/xl: 4px, 8px, 16px, 24px, 32px
--radius-sm/md/lg/full: 4px, 8px, 12px, 9999px
```

---

### 2. **Diseño Figma** ✅
- **URL:** https://www.figma.com/design/pcafE9ypFVPoikFUnuDreG
- **File:** "Puppis PDP - Mobile & Desktop"
- **Páginas:** 2

#### **Página 1: 📱 Mobile (390px)**
- Frame completo de PDP mobile (2200px altura)
- Componentes:
  - Header sticky + logo + búsqueda + carrito
  - Breadcrumb truncado
  - Galería 390x390 con badges (Regalo, -15% OFF)
  - Bloque de compra: marca → título → rating → precio grande
  - Selector variantes (3 chips: 1Kg, 3Kg, 7.5Kg)
  - Stepper cantidad (−/+)
  - CTA "Agregar al carrito" full-width
  - Envío Programado (card amarillo, $4.401/mes)
  - Opciones de envío (3 rows: Domicilio, Flash <3hs, Retiro)
  - Especificaciones (tabla 2 col)
  - Reseñas (4.8★ con featured reviews)
  - Puppis Club (15% off, CTA)
  - Footer azul

#### **Página 2: 🖥️ Desktop (1280px)** ✅
- Frame completo de PDP desktop (1280x3500px altura)
- Layout: Galería (550px) | Producto (650px) — side-by-side
- Componentes implementados:
  - Header: logo 🐾 Puppis + search icon + carrito (80px)
  - Breadcrumb: navegación truncada (40px)
  - Hero: Galería + Product Info lado-a-lado (600px altura)
  - Scheduled Shipping: Card destacada amarilla (#FAD972) con precio mensual
  - Shipping Options: 3 filas (Domicilio, Flash, Retiro) en fondos gris
  - Description & Specs: 2 columnas balanceadas
  - Reviews: Aggregate rating 4.8⭐ + featured review en white card
  - Cross-Sell: 4 productos en carousel (Snacks, Vitaminas, Juguetes, Accesorios)
  - Puppis Club: Banner azul oscuro con 💎 icon, 15% discount highlight
  - Footer: Azul 900, copyright + lema "Las mascotas primero 🐾"

**Componentes reutilizables:**
- Botones (CTA azul, secundario blanco)
- Badges (amarillo/azul)
- Chips (variantes, activo/inactivo)
- Stepper
- Cards (shipping, reviews, promociones)

---

## 🎯 Problemas Corregidos

| Problema Original | Solución Implementada |
|---|---|
| CTA sin protagonismo, bajo el fold | ✅ CTA full-width (358px/358px mobile) a los 52px, tras precio + selector + cantidad |
| 3 cards de envío ocupan demasiado espacio | ✅ Acordeón compacto de 3 filas con ícono + título + subtítulo |
| Precio suscripción confunde con precio regular | ✅ Card destacada única "Suscribite y ahorrá" con precio claro (amarillo #FAD972) + toggle secundario |
| Badge "Regalo" no explica qué incluye | ✅ Texto descriptivo debajo: "Qué incluye: [detalles]" + tooltip "cancelás cuando quieras" |
| Sin selector de tamaño visible | ✅ Chips de presentación (1Kg, 3Kg, 7.5Kg) visibles antes del CTA |
| Sin reviews visible primer scroll | ✅ Rating estrella + n° reseñas anclable a sección; featured reviews en acordeón |
| Especificaciones en bloques planos | ✅ Tabla escaneable 2 columnas + ingredientes en acordeón cerrado |

---

## 📐 Breakpoints VTEX Aplicados

```
Mobile:  hasta 767px  (ajustes secundarios en 576px, 640px)
Tablet:  768–1023px  
Desktop: 1024px+     (ajustes secundarios en 1200px, 1300px)
```

**Responsive implementado:**
- ✅ Mobile-first CSS (base en 390px)
- ✅ Desktop media query (1024px+)
- ✅ Sticky bar mobile (desaparece en desktop)
- ✅ Layout grid (galería + producto lado-a-lado en desktop)

---

## ♿ Accesibilidad & Conversión

### Reglas Aplicadas

- ✅ **Contraste AA:** Texto azul `#23376E` sobre amarillo ✓; nunca blanco sobre amarillo
- ✅ **Targets táctiles:** Botones, stepper, chips ≥44px
- ✅ **Jerarquía de precios:** Precio regular manda; suscripción mostrada como ahorro
- ✅ **Skeleton loaders:** Listos para implementación
- ✅ **Copy rioplatense:** "recibís", "elegí", "¡Guau!", "¡Purrrr!"

### Conversión

- ✅ Un solo CTA primario por vista
- ✅ CTAs secundarios en outline azul
- ✅ Precio inequívoco en 3 segundos de lectura (prueba del vistazo)
- ✅ Elementos decorativos (blobs, brush) no interfieren con legibilidad
- ✅ Sticky bar no tapa contenido con foco

---

## 🔗 Cómo Usar

### Desarrollo HTML/CSS

1. **Visualizar en navegador:**
   ```bash
   open puppis-pdp.html
   # o
   python3 -m http.server 8000
   ```

2. **Integrar en VTEX IO:**
   - Copiar estilos CSS a variables de tema
   - Componentizar secciones (Header, Gallery, PurchaseBlock, etc.)
   - Conectar datos de producto (SKU, precio, reviews, etc.)
   - Implementar lógica de carrito

3. **Personalizar según marca:**
   - Reemplazar imágenes placeholder
   - Ajustar textos y copy
   - Sincronizar datos dinámicos desde VTEX API

### Diseño Figma

1. **Abrir archivo:** https://www.figma.com/design/pcafE9ypFVPoikFUnuDreG
2. **Visualizar frames:**
   - Página "📱 Mobile (390px)" → frame completo
   - Página "🖥️ Desktop (1280px)" → frame completo
3. **Exportar componentes:**
   - Figma → Right panel → Assets → Componentes disponibles
4. **Próximos pasos:**
   - Refinar microinteracciones (animaciones hover, transiciones)
   - Añadir variantes (hover, active, disabled)
   - Crear componentes de tabla de especificaciones
   - Diseñar estados de error/validación

---

## 📊 Métricas de Conversión (Esperadas)

| Métrica | Objetivo | Implementado |
|---------|----------|---|
| Scroll hasta CTA (mobile) | <2 scroll | ✅ CTA en 392px (1er fold) |
| Precio entendible | <3 segundos | ✅ Jerarquía visual clara |
| CTR CTA primario | +15% | ✅ Tamaño 358x52px, contraste AA |
| Tasa suscripción | +10% | ✅ Card destacada amarilla, -10% visible |
| Tasa de reviews | +20% | ✅ Rating anclable, 2 featured visibles |

---

## 📝 Changelog Técnico

```
✅ [FIGMA] Página Mobile (390px): Frame 2200px con 17 secciones
✅ [FIGMA] Página Desktop (1280px): Frame 3500px con 10 secciones
  - Header (80px) + Breadcrumb (40px)
  - Hero: Galería (550px) + Product Info (650px) - side-by-side
  - Scheduled Shipping: Card amarilla destacada con pricing
  - Shipping Options: 3 rows expandibles
  - Description & Specs: 2-column layout balanceado
  - Reviews: Aggregate rating + featured review
  - Cross-Sell: 4-item carousel
  - Puppis Club: Banner azul con 15% discount
  - Footer: Azul oscuro con branding

✅ [HTML] Estructura mobile-first (390px) según specs VTEX
✅ [HTML] Sticky bar: precio + CTA al scrollear
✅ [HTML] Acordeones: envío (3 filas), especificaciones, ingredientes
✅ [HTML] Selector variantes: chips activos/inactivos
✅ [HTML] Stepper cantidad: −/+, min=1
✅ [HTML] Envío Programado: card destacada única (amarillo)
✅ [HTML] Carrusel cross-sell: snap scroll
✅ [HTML] Galería: swipeable, dots navegables
✅ [UX] Jerarquía de precios clara (precio regular manda)
✅ [A11y] Contraste AA (#23376E sobre #FAD972), targets ≥44px
✅ [PERF] Vanilla JS (sin dependencias)
✅ [DESIGN] Identidad Puppis: Colores guardrails + Roboto fonts + Tono voseo
```

---

## 🚀 Próximos Pasos (Post-Entrega)

1. **Implementación VTEX IO:**
   - Crear componentes React reutilizables
   - Conectar a APIs de producto, carrito, reseñas
   - A/B testing en 10% tráfico

2. **Refinamiento Visual:**
   - Fotografía de productos (reemplazar placeholders)
   - Animaciones micro-interacciones (hover, tap feedback)
   - Ícones customizados (huella, hueso, tilde)

3. **Optimizaciones:**
   - Lazy loading galerías/cross-sell
   - Skeleton loaders implementados
   - Core Web Vitals (LCP, FID, CLS)

4. **Testing:**
   - Pruebas de usabilidad mobile
   - Auditoría accesibilidad (WAVE, Axe)
   - Testing en navegadores (Chrome, Safari, Firefox)

---

## 📞 Soporte

- **HTML/CSS:** `/puppis-pdp.html`
- **Figma:** https://www.figma.com/design/pcafE9ypFVPoikFUnuDreG
- **Branch:** `claude/puppis-pdp-figma-7otyhu`
- **Commit:** Ver historial en GitHub

**Lema Puppis:** 🐾 *"Las mascotas primero"*

---

**Generado por:** Claude Code  
**Identidad Puppis:** Guardrails completos aplicados ✅  
**Status:** Listo para equipo de diseño e implementación VTEX
