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

### 2026-07-04 — Commit pendiente (correcciones PM)
**Qué**: Correcciones de paleta, CSS y indentación sobre el SVG de founders
**Cambios aplicados:**
1. `#3D5C4A` → `#EDE6D3` (ink) — todos los strokes/fills del SVG
2. `#345C4A` → `#EDE6D3` (ink) — sección de Emiliano (variante de verde que quedó del original)
3. `#D9603F` → `#FF6A48` (coral exacto) — todos los strokes/fills del SVG
4. `#FAF7EE` → `#EDE6D3` (ink exacto) — máscara crema de Emiliano
5. Eliminadas reglas CSS `.lam-syn` y `.lam-idea` (no se usaban en el SVG)
6. Indentación corregida en Mariano (3 paths) y Emiliano (12 paths + comentario)
**Verificación**: `grep` confirma 0 ocurrencias de `#3D5C4A`, `#345C4A`, `#AD5C4A`, `#D9603F`, `#FAF7EE` en el archivo
**Nota abierta**: `#1A1A1F` (negro azulado) se usa para cabello y cejas de ambos founders. No está en la paleta oficial pero es funcional para detalles oscuros de la ilustración. Pendiente de decisión de la PM.
**Estado**: ✅ hecho · 🔍 pendiente de revisión PM

---

## Tareas pendientes

- ⏳ Reemplazar placeholders con datos reales (WhatsApp, email, apellidos, LinkedIn) — bloqueado hasta que el usuario pase los datos
- ⏳ Revisión visual completa del sitio en navegador
- ⏳ Verificar que las animaciones del SVG de founders funcionen (draw-on + loops)
- ⏳ Verificar responsive (mobile, tablet)
- ⏳ Verificar accesibilidad (skip-link, aria-labels, focus-visible)
- 🔍 Decisión PM: ¿`#1A1A1F` en cabello/cejas del SVG es aceptable o hay que cambiarlo?

---

## Notas técnicas

- El sitio es un solo archivo HTML standalone (sin build, sin dependencias)
- Las fuentes se cargan vía Google Fonts (IBM Plex Serif/Sans/Mono)
- El orb es CSS puro (gradientes radiales + dots DOM) — no canvas
- Las animaciones se pausan fuera de viewport y durante scroll
- Hay soporte para `prefers-reduced-motion`
- Paleta oficial: `--deep:#081826; --deep-2:#0B2233; --panel:#0E2A3F; --ink:#EDE6D3; --coral:#FF6A48; --aqua:#6BCBCF; --amber:#E2A33B`
- Colores fuera de paleta usados en el resto del HTML (no SVG): `#1A1A1F` (negro azulado, cabello), `#1C3A50` (scrollbar), `#12100D` (texto en botón coral), `#FF7D5E` (hover coral), `#0E2E44` (gradiente body) — todos heredados del HTML base, no del SVG
