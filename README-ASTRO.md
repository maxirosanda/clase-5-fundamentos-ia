# Guion de clase en vivo: Sitio web con Astro + Tailwind (de cero a Vercel)

Clase única de ~2 horas, **live-coding grabado**. Construís un sitio web completo de cero —Astro, Node, Tailwind, Git, GitHub y Vercel— y lo dejás publicado en vivo. No autorás código: los componentes los **copiás y pegás de un chat de IA** al que le pasás un prompt; los archivos y la consola los manejás a mano. Los alumnos miran y replican con el video.

> Esta vez el alcance entra cómodo en 2 horas, con aire para enseñar bien cada paso (a diferencia de meter de todo a presión).

---

## Método

Chat de IA para el código (prompt → copiar → pegar), archivos y consola a mano. Cada paso: **prompteás → copiás → creás/editás el archivo → corrés en consola → verificás en el navegador.**

## Prep off-camera

- Node LTS instalado; sesiones de GitHub y Vercel iniciadas.
- Chat de IA abierto y el editor listo.
- Decidí de antemano las secciones del sitio (para no improvisar el contenido en cámara).
- Ensayá una vez el deploy a Vercel: es lo único que, si falla, te frena en vivo.

---

## El sitio que vas a construir

Una landing para **VerdeCasa** (venta de plantas de interior), con: navbar, hero, grilla de productos, sección de cuidados/beneficios, FAQ, formulario de contacto y footer. Responsiva y publicada en Vercel.

---

## Guion minuto a minuto (120 min)

| # | Segmento | Min | Qué hacés | Conceptos |
|---|---|---|---|---|
| 0 | **Visión** | 5' | Mostrás una referencia o bosquejás el sitio y listás las secciones. Abrís chat de IA y editor. | Planificación, prototipo → demo |
| 1 | **Scaffold** | 12' | `npm create astro` (template minimal), `npx astro add tailwind`, `npm run dev`. Recorrés la estructura (pages, layouts, components) y explicás el modelo de Astro. | Scaffold, estructura de archivos |
| 2 | **Layout + navbar + footer** | 15' | Prompt (template) para un `Layout.astro` con head, navbar, `<slot>` y footer en Tailwind. Creás el archivo, pegás, lo usás en `index.astro`. | Prompt engineering (template), Tailwind, componentización |
| 3 | **Hero** | 12' | Componés en vivo un prompt template para el hero (título, subtítulo, CTA, imagen). Creás `Hero.astro`, pegás, importás, verificás en mobile y desktop. | Prompt engineering, Tailwind responsive |
| 4 | **Grilla de productos** | 18' | Prompt con **few-shot**: le das el ejemplo de una card y pedís la grilla responsiva con datos de ejemplo. Pegás y ajustás el grid. | Few-shot prompting, Tailwind grid, datos/props en Astro |
| 5 | **FAQ + formulario** | 18' | Prompts para un accordion de FAQ y un formulario de contacto. Pegás. Dedicás 2' a **revisar el código generado** (accesibilidad, validación). | Prompt engineering, Tailwind, revisión de código IA |
| 6 | **Pulido + responsive + lint** | 12' | Recorrés el sitio en mobile/desktop, ajustás con re-prompts puntuales, agregás y corrés Prettier. | Iteración/refinamiento, linters |
| 7 | **Git + GitHub** | 12' | `git init`, commit, creás el repo en GitHub y `git push`. Explicás los commits como checkpoints. | Control de versiones, GitHub |
| 8 | **Deploy en Vercel** | 12' | Conectás el repo a Vercel, build, obtenés la **URL en vivo**. Hacés un cambio chico + commit para mostrar el redeploy automático. | Deploy continuo, CI/CD básico |
| 9 | **Cierre + recap** | 4' | Recorrés el sitio desde la URL pública y recapitulás los conceptos vistos. | Prototipo → demo |

**Total:** 120 minutos, a ritmo cómodo.

---

## Lo que cubre esta clase

- Prompt engineering: templates (seg. 2-3) y few-shot (seg. 4).
- Asistentes de codificación / generación de UI con IA (seg. 2-5).
- Tailwind CSS: layout, responsive, grid (seg. 2-6).
- Scaffold y estructura de un proyecto Astro (seg. 1).
- Revisión de código generado por IA (seg. 5).
- Iteración/refinamiento y linters (seg. 6).
- Control de versiones con Git + GitHub (seg. 7).
- Deploy continuo en Vercel (seg. 8).
- Prototipo → demo funcional en vivo (seg. 0, 8, 9).

*Por decisión de alcance, no incluye: Python/NLP, chatbot, testing/regresión, monitoreo, ética ni n8n. El de n8n va como ejercicio aparte.*

---

## Contingencias

- **Si vas largo:** reducí la grilla a 3 productos (seg. 4) o mostrá el linter de palabra (seg. 6). En el peor caso, dejá la FAQ afuera.
- **Si vas corto:** sumá un toggle de modo oscuro o una segunda pasada de pulido con prompts. Da mucho juego para enseñar Tailwind.

## Tips para que el video sea replicable

- Leé cada prompt completo en voz alta antes de mandarlo: ahí está el aprendizaje.
- Mostrá el árbol de archivos y nombrá cada archivo al crearlo.
- Al pegar, dejá el chat y el editor lado a lado.
- Hacé commit en cada milestone (después del layout, del hero, etc.): son checkpoints para que el alumno se ubique.
- Cerrá con el sitio andando desde la URL de Vercel, no desde localhost.
