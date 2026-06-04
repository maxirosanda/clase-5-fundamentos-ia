# Guion de clase en vivo (prompt + copiar/pegar): VerdeCasa sin escribir código

Clase única, **live-coding grabado**: el docente no autora ni una línea de código. Maneja los archivos de Astro, la consola y Colab **a mano**, pero todo lo que sean líneas de código las **copia y pega de un chat de IA** al que le pasa un prompt. Los alumnos miran y replican con el video. La habilidad que se enseña es **componer prompts y verificar la salida**, no programar.

**Duración:** ~120 minutos.

---

## El método: prompt → copiar → pegar → correr

No usás un asistente agéntico ni dejás que la IA toque tus archivos. Usás un **chat de IA** (pestaña o panel), le pasás un prompt y **copiás y pegás** lo que devuelve. Vos manejás el resto.

- **Archivos de Astro:** los creás y editás vos, a mano. Las líneas de código las copiás del chat y las pegás en el archivo.
- **Consola:** la manejás vos (`npm create astro`, `npx astro add tailwind`, `npm run dev`, `git push`…).
- **Python:** en **Google Colab**. Pegás el código que te da la IA en las celdas y las corrés.
- **n8n:** armás los nodos a mano (es visual). Cuando un nodo necesita una expresión o código (nodo Function/Code), se lo pedís al chat y lo pegás.

### Qué cuenta como "no escribir código"
- **No autorás lógica:** ningún componente, script ni expresión sale de vos tipeando; todo viene de un prompt.
- **Sí hacés a mano:** crear/editar archivos, copiar/pegar, correr comandos en consola, configurar nodos de n8n y la UI de Vercel. Eso es operar, no programar.

> Para una clase grabada, este mecanismo es más transparente que un agente: los alumnos ven exactamente en qué archivo va cada bloque y qué comando corrés.

---

## Prep off-camera (no es material para alumnos, es estar listo)

- Chat de IA abierto (pestaña o panel) y el editor con la carpeta del proyecto.
- Máquina lista: Node LTS y sesiones de GitHub, Vercel y n8n iniciadas.
- **Notebook de Colab** abierto, con la primera celda lista para instalar spaCy y bajar el modelo (`en_core_web_sm`).
- API de enriquecimiento elegida y probada (clima o geolocalización por código postal).
- **Ensayo de las dos zonas de riesgo** (spaCy en Colab y n8n): saber qué prompt te da código que corre al primer intento.

---

## Guion minuto a minuto (120 min)

Flujo de cada segmento: **prompteás al chat → copiás → pegás (archivo o celda) → corrés en consola/Colab → verificás.** *Zona de riesgo* = donde el debug por prompt puede comerte el reloj.

| # | Segmento | Min | Qué hacés (prompt → copiar/pegar → correr) | Conceptos |
|---|---|---|---|---|
| 0 | **Visión** | 4' | Describís el proyecto; abrís el chat de IA, el editor y Colab. | Visión end-to-end, prototipo → demo |
| 1 | **Scaffold** | 9' | Corrés a mano `npm create astro` y `npx astro add tailwind`. Para ajustes de config, prompteás, copiás y pegás. Verificás con `npm run dev` y definís la estructura de carpetas. | Scaffold del proyecto |
| 2 | **UI con IA** | 24' | **Momento central.** Componés en vivo un prompt **template** y uno **few-shot** por componente (hero, FAQ, formulario). Pegás el código que devuelve la IA en cada archivo `.astro` que creás vos, los importás, verificás en el navegador y re-prompteás ajustes. | Prompt engineering (templates/few-shot), asistentes de codificación, Tailwind, mockups (mención), revisión |
| 3 | **Calidad exprés** | 11' | Prompteás y pegás: config de ESLint + Prettier (corrés el formateo), un test para el validador del formulario (lo corrés) y un script que ordene y deduplique clases de Tailwind. Mencionás regresión. | Linters, refactor/codemods, tests, regresión |
| 4 | **Datos y NLP en Colab** — *riesgo* | 18' | En Colab: corrés la celda de instalación de spaCy. Prompteás un script que normalice texto y extraiga entidades de un JSON de FAQs; lo pegás y corrés (12'). Prompteás otro de precisión/recall/F1 con alerta por umbral; lo pegás y corrés (6'). Si rompe, pegás el error y pedís el fix. | Pipelines, limpieza con spaCy, NER, métricas NLP, alertas |
| 5 | **Flujo en n8n** — *riesgo* | 24' | Armás los nodos a mano (visual): webhook → validación → branching → API de enriquecimiento → respuesta → notificación. Donde un nodo pida una expresión o código, se lo pedís al chat y lo pegás. Señalás reintentos, idempotencia y seguridad. | Workflows (reintentos, idempotencia, seguridad), n8n/Make/Zapier, enriquecimiento con APIs, notificaciones, intents/entidades/contexto, lógica de chatbot |
| 6 | **Conectar el chat** | 8' | Prompteás el código de un widget de chat que haga POST al webhook; lo pegás en la página y lo cableás; probás en vivo y responde con un dato enriquecido. | Integración end-to-end, exposición, prototipo → demo |
| 7 | **Deploy** | 10' | `git push` a mano y conectás Vercel por su UI; obtenés la URL pública y apuntás el webhook a producción. | Deploy continuo (GitHub + Vercel) |
| 8 | **Monitoreo + ética + cierre** | 12' | Prompteás un script que lea logs de estado del webhook y decida OK/ALERTA/ROLLBACK; lo pegás/corrés y lo mostrás (6'). Cerrás con ética/privacidad: minimización, consentimiento, 2 sesgos + mitigación, y el checklist (6'). | Monitoreo/rollback, ética/privacidad/sesgos, documentación, checklist |

**Total:** 120 minutos.

---

## El cambio de objetivo (decilo en clase)

Al construir todo por prompts + copiar/pegar, lo que entrenás no es escribir código, sino:

- **Componer prompts efectivos** (templates, few-shot, contexto, restricciones).
- **Saber dónde va cada bloque** y correrlo en el lugar correcto (archivo, consola, celda, nodo).
- **Verificar y corregir** la salida pegando el error y re-prompteando.
- **Decidir cuándo el resultado es suficientemente bueno.**

La cobertura de conceptos del curso se mantiene; la profundidad se corre de "cómo se programa X" a "cómo logro que la IA lo programe, dónde lo pego y cómo sé que está bien".

---

## Cobertura de conceptos

Método: 100% prompt-driven con copiar/pegar, todo demostrado en vivo; los alumnos replican con el video.

| Concepto / Unidad | Segmento |
|---|---|
| Prototipo a demo / end-to-end | 0, 6, 7 |
| Scaffold del proyecto | 1 |
| Prompt engineering (templates/few-shot) | 2 |
| Asistentes de codificación | 2 |
| Tailwind CSS | 2 |
| Mockups con IA (mención) | 2 |
| Refactor / codemods | 3 |
| Tests y regresión | 3 |
| Linters / refinamiento | 3 |
| Pipelines de datos | 4, 5 |
| Limpieza con spaCy / NER | 4 |
| Métricas NLP (alertas) | 4 |
| Workflows (reintentos, idempotencia, seguridad) | 5 |
| n8n / Make / Zapier | 5 |
| Enriquecimiento con APIs | 5 |
| Notificaciones | 5 |
| Intents, entidades y contexto | 5 |
| Lógica de chatbot (Dialogflow/Bot Framework) | 5 |
| Deploy continuo (GitHub + Vercel) | 7 |
| Monitoreo / rollback | 8 |
| Ética, privacidad y sesgos | 8 |
| Documentación / tareas de producto | 8 |

**Cobertura:** 22 de las ~24 unidades. Queda afuera **transformers** (era bonus). Supera el 70% objetivo.

---

## Contingencias (si te estás pasando)

El debug por prompt en vivo es impredecible. Si vas corto, recortá en este orden:

1. **Métricas NLP (seg. 4):** mostrá el script ya generado en vez de pedirlo en vivo. ~5'.
2. **Monitoreo (seg. 8):** contalo de palabra. ~4'.
3. **Codemod (seg. 3):** mostrá antes/después sin generarlo en vivo. ~4'.
4. **Tercer componente (seg. 2):** generá 2 en lugar de 3. ~5'.

No recortes la espina: scaffold (1), UI por prompts (2), flujo de n8n (5) y deploy (7).

---

## Tips para que el video sea replicable

- Leé cada prompt completo en voz alta **antes** de mandarlo: ahí está el aprendizaje.
- Al pegar, mostrá el chat y el archivo/celda lado a lado, y nombrá el archivo en voz alta.
- Cuando algo falle, no lo escondas: mostrá cómo pegás el error y lo arreglás re-prompteando. Eso es oro didáctico.
- Tené n8n y la página visibles juntas al conectar el chat, para ver el ida y vuelta.
- Cerrá con la demo andando de punta a punta: del scaffold al chat respondiendo con dato enriquecido en la URL en vivo.
