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
**Qué**: SVG de founders completo pegado en `index.html` (129 líneas, +200 paths)
**Por qué**: El HTML standalone tenía un comentario placeholder donde iba el SVG. Se extrajo de `/Users/Emi/Ynera pagina/index.html` (líneas 1217-1345) que era el proyecto anterior con el SVG completo
**Detalle técnico**: SVG incluye a Mariano (atrás, escala 0.82) y Emiliano (adelante), con animaciones draw-on (`class="dp"`), lentes HUD con anillos, ideas flotantes (SEGURIDAD, DATOS, IA, etc.), y un clay-dot final
**Estado**: ✅ hecho · 🔍 pendiente de revisión

---

## Tareas pendientes

- ⏳ Reemplazar placeholders con datos reales (WhatsApp, email, apellidos, LinkedIn) — bloqueado hasta que el usuario pase los datos
- ⏳ Revisión visual completa del sitio en navegador
- ⏳ Verificar que las animaciones del SVG de founders funcionen (draw-on + loops)
- ⏳ Verificar responsive (mobile, tablet)
- ⏳ Verificar accesibilidad (skip-link, aria-labels, focus-visible)

---

## Notas técnicas

- El sitio es un solo archivo HTML standalone (sin build, sin dependencias)
- Las fuentes se cargan vía Google Fonts (IBM Plex Serif/Sans/Mono)
- El orb es CSS puro (gradientes radiales + dots DOM) — no canvas
- Las animaciones se pausan fuera de viewport y durante scroll
- Hay soporte para `prefers-reduced-motion`
