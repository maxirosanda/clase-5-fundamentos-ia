# Guion de clase en vivo: Landing page con Astro + Tailwind (de cero a Vercel)

Clase única de ~2 horas, **live-coding grabado**. Construís una landing page de cero —Astro, Node, Tailwind, Git, GitHub y Vercel— y la dejás publicada en vivo. Todo el código lo generás desde un **chat de IA externo en el navegador** (prompt → copiar → pegar); los archivos y la consola los manejás a mano. Los alumnos miran y replican con el video.

---

## Método de trabajo

Chat de IA externo en el navegador para el código. Archivos y consola a mano.

Cada paso sigue este flujo:

**Prompteás en el chat de IA → Copiás el código → Creás/editás el archivo a mano → Corrés el comando en la consola → Verificás en el navegador**

---

## Prep off-camera

- Node LTS instalado; sesiones de GitHub y Vercel iniciadas.
- Chat de IA abierto en el navegador y el editor listo (lado a lado en pantalla).
- Decidí de antemano las secciones del sitio (para no improvisar el contenido en cámara).
- Ensayá una vez el deploy a Vercel: es lo único que, si falla, te frena en vivo.

---

## El sitio que vas a construir

Una landing para **VerdeCasa** (venta de plantas de interior), con: navbar, hero, grilla de productos, sección de cuidados/beneficios, FAQ, formulario de contacto y footer. Responsiva y publicada en Vercel.

---

## Guion minuto a minuto (120 min)

| # | Segmento | Min | Qué hacés | Conceptos |
|---|---|---|---|---|
| 0 | **Visión** | 5' | Mostrás una referencia o bosquejás el sitio y listás las secciones. Abrís el chat de IA en el navegador y el editor. Explicás el método: todo el código vendrá de prompts al chat. | Planificación, prototipo → demo |
| 1 | **Scaffold** | 12' | Desde la consola: `npm create astro` (template minimal), `npx astro add tailwind`, `npm run dev`. Recorrés el árbol de archivos y explicás el modelo de Astro. | Scaffold, estructura de archivos, comandos manuales |
| 2 | **Layout + navbar + footer** | 15' | Prompt template al chat de IA para un `Layout.astro` con head, navbar, `<slot>` y footer en Tailwind. Creás el archivo a mano, pegás el código, lo usás en `index.astro`. | Prompt engineering (template), Tailwind, componentización |
| 3 | **Hero** | 12' | Componés en vivo un prompt template para el hero (título, subtítulo, CTA, imagen). Creás `Hero.astro` a mano, pegás, importás y verificás en mobile y desktop. | Prompt template, Tailwind responsive |
| 4 | **Grilla de productos** | 18' | Prompt few-shot al chat: le das el ejemplo de una card y pedís la grilla responsiva con datos de ejemplo. Pegás el código y ajustás el grid a mano. | Few-shot prompting, Tailwind grid, props en Astro |
| 5 | **FAQ + formulario** | 18' | Prompts al chat para un accordion de FAQ y un formulario de contacto. Pegás los componentes. Dedicás 2' a revisar el código generado (accesibilidad, validación). | Prompt engineering, revisión de código IA |
| 6 | **Pulido + responsive + lint** | 12' | Recorrés el sitio en mobile y desktop. Ajustás con re-prompts puntuales al chat. Agregás Prettier y lo corrés desde la consola. | Iteración con IA, linters, responsive |
| 7 | **Git + GitHub** | 12' | Desde la consola: `git init`, commit inicial, creás el repo en GitHub y `git push`. Explicás los commits como checkpoints del alumno. | Control de versiones, GitHub, comandos manuales |
| 8 | **Deploy en Vercel** | 12' | Conectás el repo a Vercel, build, obtenés la URL en vivo. Hacés un cambio chico + commit para mostrar el redeploy automático. | Deploy continuo, CI/CD básico |
| 9 | **Cierre + recap** | 4' | Recorrés el sitio desde la URL pública de Vercel (no desde localhost) y recapitulás los conceptos vistos. | Prototipo → demo |

**Total:** 120 minutos, a ritmo cómodo.

---

## Lo que cubre esta clase

- Prompt engineering: templates (seg. 2-3) y few-shot (seg. 4).
- Generación de UI con IA desde un chat externo en el navegador (seg. 2-5).
- Tailwind CSS: layout, responsive, grid (seg. 2-6).
- Scaffold y estructura de un proyecto Astro (seg. 1).
- Revisión de código generado por IA (seg. 5).
- Iteración y refinamiento con re-prompts, linters (seg. 6).
- Control de versiones con Git + GitHub (seg. 7).
- Deploy continuo en Vercel (seg. 8).
- Prototipo → demo funcional en vivo (seg. 0, 8, 9).

*Por decisión de alcance, no incluye: Python/NLP, chatbot, testing/regresión, monitoreo, ética ni n8n. El de n8n va como ejercicio aparte.*

---

## Contingencias

- **Si vas largo:** reducí la grilla a 3 productos (seg. 4) o mostrá el linter de palabra (seg. 6). En el peor caso, dejá la FAQ afuera.
- **Si vas corto:** sumá un toggle de modo oscuro o una segunda pasada de pulido con prompts. Da mucho juego para enseñar Tailwind.

---

## Tips para que el video sea replicable

- Leé cada prompt completo en voz alta antes de mandarlo al chat: ahí está el aprendizaje.
- Mostrá el árbol de archivos y nombrá cada archivo al crearlo a mano.
- Al pegar código, dejá el chat del navegador y el editor lado a lado en pantalla.
- Hacé commit después de cada milestone (layout, hero, productos, etc.): son checkpoints para que el alumno se ubique.
- Cerrá con el sitio andando desde la URL de Vercel, no desde localhost.
