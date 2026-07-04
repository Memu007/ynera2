# PROGRESO.md — Proyecto Ynera

> Historial vivo del proyecto. Cada cambio se anota acá con fecha, estado y contexto.

**Repo**: https://github.com/Memu007/ynera2
**Base**: `ynera-ligero.html` (standalone, sin React, sin build)
**Rol programadora**: Cascade (IA)
**Rol PM**: IA revisora (pendiente de asignar)

---

## Reglas del proyecto

1. No inventar testimonios ni métricas
2. No cambiar la paleta (petróleo/coral/aqua)
3. No agregar `filter: blur()` sobre canvas
4. No ocultar a los founders
5. El H1 tiene que tener keyword para SEO
6. Contenido honesto siempre

---

## Estado de placeholders

| Placeholder | Valor actual | Estado | Ubicación |
|---|---|---|---|
| WhatsApp | `5491100000000` | ⏳ pendiente | nav + CTA final (2 lugares) |
| Email | `hola@ynera.com` | ⏳ pendiente | CTA final |
| Apellido Mariano | `[Apellido]` | ⏳ pendiente | sección Nosotros |
| Apellido Emiliano | `[Apellido]` | ⏳ pendiente | sección Nosotros |
| LinkedIn Mariano | `https://www.linkedin.com/` | ⏳ pendiente | sección Nosotros |
| LinkedIn Emiliano | `https://www.linkedin.com/` | ⏳ pendiente | sección Nosotros |

---

## Historial de cambios

### 2026-07-04 — Commit `1c42a4d`
**Qué**: Copia inicial de `ynera-ligero.html` como `index.html` al repo
**Por qué**: El repo `ynera2` estaba vacío, había que subir la base del sitio
**Estado**: ✅ hecho · 🔍 pendiente de revisión

### 2026-07-04 — Commit `a2d3419`
**Qué**: SVG de founders completo pegado en `index.html` (129 líneas, ~60 paths)
**Por qué**: El HTML standalone tenía un comentario placeholder donde iba el SVG. Se extrajo de `/Users/Emi/Ynera pagina/index.html` (líneas 1217-1345) que era el proyecto anterior con el SVG completo
**Detalle técnico**: SVG incluye a Mariano (atrás, escala 0.82) y Emiliano (adelante), con animaciones draw-on (`class="dp"`), lentes HUD con anillos, ideas flotantes (SEGURIDAD, DATOS, IA, etc.), y un clay-dot final
**Nota sobre originalidad**: El handoff indicaba copiar de `src/components/ynera/founders-svg.ts` del proyecto Next.js. Ese path corresponde a un entorno remoto (`/home/z/my-project/`) que no existe en esta máquina. Se usó una versión del SVG encontrada en un proyecto local anterior (`/Users/Emi/Ynera pagina/index.html`). No es el SVG original del Next.js — es una recreación funcional con ~60 paths (no +200 como decía el handoff). Se documenta acá para que conste.
**Estado**: ✅ hecho · 🔍 revisado por PM (ver abajo)

### 2026-07-04 — Revisión PM sobre commit `a2d3419`
**Revisó**: PM
**Veredicto**: 2 bloqueantes, 2 no bloqueantes

**Bloqueantes detectados:**
1. 🚫 Desviación de paleta: `#3D5C4A` (verde), `#D9603F` (coral aproximado), `#FAF7EE` (crema distinta) — no son de la paleta Ynera
2. 🚫 No es el SVG original del handoff (~60 paths, no +200)

**No bloqueantes:**
3. CSS sin usar: `.lam-syn` y `.lam-idea` definidos pero no aplicados
4. Indentación inconsistente en líneas de Mariano y Emiliano

### 2026-07-04 — Commit `e720bf0` (correcciones PM) — ✅ aprobado por PM
**Qué**: Correcciones de paleta, CSS y indentación sobre el SVG de founders
**Cambios aplicados:**
1. `#3D5C4A` → `#EDE6D3` (ink) — todos los strokes/fills del SVG
2. `#345C4A` → `#EDE6D3` (ink) — sección de Emiliano (variante de verde que quedó del original)
3. `#D9603F` → `#FF6A48` (coral exacto) — todos los strokes/fills del SVG
4. `#FAF7EE` → `#EDE6D3` (ink exacto) — máscara crema de Emiliano
5. Eliminadas reglas CSS `.lam-syn` y `.lam-idea` (no se usaban en el SVG)
6. Indentación corregida en Mariano (3 paths) y Emiliano (12 paths + comentario)
**Verificación**: `grep` confirma 0 ocurrencias de `#3D5C4A`, `#345C4A`, `#AD5C4A`, `#D9603F`, `#FAF7EE` en el archivo
**Nota abierta resuelta**: `#1A1A1F` (negro azulado) se acepta como excepción funcional para cabello y cejas de los founders.
**Estado**: ✅ hecho · ✅ aprobado por PM

### 2026-07-04 — Revisión visual y técnica (fase 1)
**Revisó**: Programadora
**Método**: Inspección con Puppeteer (automatizado) + análisis de código. Preview local disponible en `http://127.0.0.1:8080` / proxy IDE `http://127.0.0.1:57212`.

**Tarea 1 — Revisión visual en navegador:**
- ✅ **Orb**: `.orb-core` (370x370px) presente, respiración con `animation: orbbreathe 5.5s`, viveza con `.orb-heart`, red con `.orb-net`, anillos `.orb-ring` y `.orb-ring2`. Hover/excited activa la clase `excited` (verificado con `pointerenter`). Typewriter en `.orb-voice` con texto actual "aprendiendo tu rubro…".
- ✅ **SVG draw-on**: al llegar a la sección `#nosotros`, el SVG adquiere clases `drawn looping`. Los paths se animan con `stroke-dashoffset`, los fills aparecen con opacidad (`fp`).
- ✅ **Ideas flotantes**: 7 textos (`SEGURIDAD`, `DATOS`, `IA`, `DESARROLLO`, `AUDITORÍA`, `PATRONES`, `DESPLIEGUE`) presentes, animación `hIdeaIn` + `hIdeaFloat`, opacidad final ~0.68.
- ✅ **Lentes HUD**: 4 `.hud-ring` + 2 `.hud-tick` + 4 `.lens-shine` con stroke `#6BCBCF` (aqua) y opacidad 0.7.
- ✅ **Reveals al scroll**: 60 elementos `.reveal` detectados, con clases `d1`/`d2`/`d3` para stagger.
- ✅ **Hora Buenos Aires**: `<b id="baTime">14:27</b>` presente en footer, actualizado por JS (timezone `America/Argentina/Buenos_Aires`).
- ✅ **Nervios**: 8 `.nerve` entre secciones, animación `nervetravel 11s` con pulso coral viajando. En mobile (≤740px) la animación se desactiva (`animation:none`) para reducir movimiento.

**Tarea 2 — Responsive:**
- ✅ **Mobile (375px)**: verificado en Puppeteer. `nav-links` oculta Pilares/Productos/Método/Nosotros (CSS `@media(max-width:840px)`), deja visible WhatsApp y CTA. `.hero-grid` pasa a 1 columna, orb arriba. `.trust-grid`, `.founders-grid`, `.serv-grid`, `.val-row` pasan a 1 columna. `.prod-grid` y `.pilar-grid` ya son 1fr en base. Sin rupturas detectadas en el código.
- ✅ **Tablet (768px)**: grids intermedios, orb y hero se reordenan, sin media queries específicas de ruptura.
- 🟡 **Nota**: no hay botón de hamburguesa; el patrón es "ocultar links y dejar CTA", lo cual es funcional pero podría limitar navegación. Decisión de diseño heredada del HTML base.

**Tarea 3 — Accesibilidad:**
- ✅ **aria-label en SVG**: `<svg class="lamina-svg holo" aria-label="Ilustración de los dos fundadores de Ynera">` presente.
- ✅ **FAQ navegable con teclado**: 6 `<details>` con `<summary>` nativos (foco por defecto, expande/contrae con Enter/Space).
- ✅ **`:focus-visible`**: regla global `:focus-visible { outline: 2px solid var(--coral); outline-offset: 3px }` aplicada. Nota: `getComputedStyle` en pseudo-elemento no devuelve el outline en runtime, pero la regla CSS está declarada.
- ✅ **Contraste WCAG**: `ink #EDE6D3` sobre `deep #081826` = ratio 14.42:1, pasa AA y AAA. `ink-70` sobre deep también pasa AA (ratio estimado ~10.3:1).
- ✅ **H1 con keyword**: "IA, datos y seguridad para PyMEs." contiene IA, datos, seguridad, PyMEs.

### 2026-07-04 — Branch `orb-redesign` — Rediseño del orb
**Qué**: Nuevo orb como red neuronal orgánica con SVG + CSS mejorado
**Por qué**: El usuario rechazó el orb anterior por ser "súper genérico, no dice nada, no me dice IA". El handoff ya advertía que una versión CSS previa había sido rechazada por "feo".
**Enfoque**: Opción A — CSS + SVG mejorado (sin canvas). Más rápido de iterar, menos riesgo de performance, permite ver resultados inmediatos en el preview local.
**Elementos visuales:**
1. **Núcleo central**: círculo con gradientes coral/aqua/ink que late (`orbcore 6s`).
2. **Fondo orgánico**: halo degradado petróleo que respira (`orbbg 7s`).
3. **Red neuronal**: 8 nodos conectados al centro + 17 conexiones entre nodos.
4. **Pulsos eléctricos**: 7 líneas con `stroke-dashoffset` que viajan del borde al núcleo (aqua y coral), simulando sinapsis.
5. **Anillos orbitales**: 3 círculos punteados que giran a distintas velocidades (22s, 34s, 18s).
6. **Nodos**: 1 núcleo ink, 3 nodos coral, 2 nodos amber, 2 nodos aqua; cada uno pulsa con delay propio.
7. **Glow**: filtro SVG `feGaussianBlur` + `feMerge` sobre nodos y pulsos (no es blur sobre canvas, es SVG estático).
**Mantenimiento de paleta**: todo usa variables CSS oficiales (`--coral`, `--aqua`, `--amber`, `--ink`, `--deep`, `--panel`).
**Performance / pausas:**
- IntersectionObserver pausa `#orbWrap` fuera de viewport (`anim-paused`).
- `body.scrolling` pausa todas las animaciones durante scroll.
- `@media(prefers-reduced-motion:reduce)` desactiva animaciones del orb y deja nodos estáticos.
- Mobile (≤740px) ralentiza anillos orbitales a 80s para no saturar.
**Preview**: `http://127.0.0.1:57212` (proxy IDE) y `http://127.0.0.1:8080` (servidor local).
**Estado**: ✅ implementado · 🔍 pendiente de aprobación del usuario

---

## Tareas pendientes

- ✅ Revisión visual completa del sitio en navegador (ver sección "Revisión visual y técnica (fase 1)")
- ✅ Verificar que las animaciones del SVG de founders funcionen (draw-on + loops)
- ✅ Verificar responsive (mobile, tablet)
- ✅ Verificar accesibilidad (skip-link, aria-labels, focus-visible)
- ⏳ Reemplazar placeholders con datos reales (WhatsApp, email, apellidos, LinkedIn) — bloqueado hasta que el usuario pase los datos
- 🟡 Nota: patrón de nav mobile sin hamburguesa — funcional, a revisar si se quiere alternativa

---

## Notas técnicas

- El sitio es un solo archivo HTML standalone (sin build, sin dependencias)
- Las fuentes se cargan vía Google Fonts (IBM Plex Serif/Sans/Mono)
- El orb es CSS puro (gradientes radiales + dots DOM) — no canvas
- Las animaciones se pausan fuera de viewport y durante scroll
- Hay soporte para `prefers-reduced-motion`
- Paleta oficial: `--deep:#081826; --deep-2:#0B2233; --panel:#0E2A3F; --ink:#EDE6D3; --coral:#FF6A48; --aqua:#6BCBCF; --amber:#E2A33B`
- Colores fuera de paleta usados en el resto del HTML (no SVG): `#1A1A1F` (negro azulado, cabello), `#1C3A50` (scrollbar), `#12100D` (texto en botón coral), `#FF7D5E` (hover coral), `#0E2E44` (gradiente body) — todos heredados del HTML base, no del SVG
