# Guion del ejercicio en vivo: Clasificación de texto con IA en Colab (datos de Kaggle)

Ejercicio separado, **live-demo grabado** (~70 min) en Google Colab. Cargás un dataset real de Kaggle, extraés entidades con spaCy, clasificás los textos con un transformer y medís qué tan bien lo hace con métricas. Los alumnos miran y replican con el video. Método: **prompteás al chat de IA → copiás → pegás en la celda → corrés → verificás.**

> Es el segmento más técnico del módulo (el que dijimos que se siente avanzado para fundamentos). En modo demo y copiando/pegando corre sin que te trabes; el riesgo no es técnico sino **abrumar** a un público principiante. Como ellos igual leen el material para el multiple choice, alcanza con mostrar que existe y que se puede correr, sin enseñarlo a fondo.

---

## Qué suma este ejercicio

Lleva la cobertura de los dos guiones anteriores de ~50% a **~70-75%**, sumando:

- Limpieza y extracción de entidades con spaCy (NER).
- Clasificación con un transformer preentrenado (zero-shot).
- Métricas NLP: precisión, recall, F1 y alerta por umbral.
- Diseño conversacional / intents (como puente: la misma técnica clasifica intents en un chatbot).
- Mención de sesgos sobre el clasificador.

*Siguen afuera, porque no entran natural en un Colab: codemods/refactor, tests/regresión, mockups con Galileo/Uizard, documentación de producto y monitoreo.*

---

## El dataset

**News Category Dataset** de Kaggle (`rmisra/news-category-dataset`), el mismo que tu material enlaza para spaCy: https://www.kaggle.com/datasets/rmisra/news-category-dataset

Es ideal porque cada registro trae el **texto** (`headline`, `short_description`) para el NER, y la **categoría real** (`category`) que sirve de etiqueta verdadera para medir las métricas. Está en inglés, así que usás el modelo `en_core_web_sm`.

---

## Prep off-camera (clave, hacelo antes de grabar)

- Colab abierto. **Activá GPU** (Runtime → Change runtime type → GPU): el transformer corre mucho más rápido.
- **Acceso a Kaggle resuelto de antemano:** subí tu `kaggle.json` y configuralo, o tené el archivo del dataset ya en tu Google Drive listo para montar. **No muestres el token de Kaggle en cámara.**
- **Reducí el dataset:** quedate con 4-5 categorías y una muestra chica (~100-150 filas) balanceada. Nunca corras el transformer sobre las ~200k filas completas.
- **Corré todo una vez antes de grabar:** que el modelo zero-shot baje y funcione (la primera descarga tarda).

---

## El flujo del notebook

`Cargar dataset (Kaggle)` → `Filtrar + muestrear` → `spaCy NER` → `Clasificar con transformer (zero-shot)` → `Métricas (P/R/F1 + alerta)`

---

## Guion minuto a minuto (~71 min)

Flujo de cada celda: prompteás al chat → pegás en Colab → corrés → mostrás la salida.

| # | Segmento | Min | Qué hacés | Conceptos |
|---|---|---|---|---|
| 0 | **Visión** | 4' | Explicás: vamos a clasificar texto real y medir qué tan bien lo hace un modelo. Abrís el notebook. | Visión del pipeline NLP |
| 1 | **Cargar datos de Kaggle** — *riesgo* | 10' | Corrés la celda de descarga (Kaggle API ya configurada) o montás el archivo desde Drive. Cargás el JSONL con pandas (`read_json(..., lines=True)`) y mostrás las columnas. | Ingestión de datos, datasets reales |
| 2 | **Filtrar + muestrear** | 6' | Prompteás y pegás código para quedarte con 4-5 categorías y ~100 filas. Explicás por qué muestreás (velocidad de inferencia en vivo). | Preparación de datos |
| 3 | **NER con spaCy** | 12' | Instalás spaCy + `en_core_web_sm`. Prompteás un script que normalice el texto y extraiga entidades (PERSON/ORG/GPE) de los titulares; lo pegás, corrés y mostrás las entidades. | Limpieza/normalización, spaCy, NER |
| 4 | **Clasificación con transformer** — *riesgo* | 15' | Prompteás el pipeline zero-shot de HuggingFace (`bart-large-mnli`) usando tus 4-5 categorías como `candidate_labels`. Lo corrés sobre la muestra y mostrás la etiqueta predicha al lado de la real. | Transformers, clasificación semántica |
| 5 | **Métricas** | 12' | Prompteás código que compara predicho vs. real y calcula precisión/recall/F1 (con `sklearn` o a mano), e imprime una **alerta si una métrica cae bajo un umbral** (ej. 0.7). | Métricas NLP, alertas, evaluación de modelos |
| 6 | **Puente a intents + sesgos** | 8' | Conectás: "esta misma técnica es la que clasifica los intents de un chatbot". Comentás 1-2 sesgos posibles (categorías sub-representadas, sesgos del modelo preentrenado). | Diseño conversacional/intents, ética/sesgos |
| 7 | **Cierre + recap** | 4' | Recapitulás los conceptos: spaCy, transformers, métricas, intents. | Visión del pipeline |

**Total:** ~71 minutos.

---

## Riesgos y contingencias

- **#1 – Acceso a Kaggle / token en cámara.** Resuelto antes de grabar; nunca muestres el `kaggle.json`. Si la API falla, tené el archivo en Drive como respaldo.
- **#2 – Tamaño del dataset.** Son ~200k filas. Filtrá y muestreá **siempre**; correr el transformer sobre todo el dataset cuelga la clase.
- **#3 – Tiempo de inferencia.** Con GPU y ~100 filas, corre en segundos. Sin GPU, reducí la muestra a 30-50.
- **Descarga del modelo.** La primera vez `bart-large-mnli` tarda en bajar; corrélo antes de grabar para que esté cacheado en la sesión.
- **Salida del modelo.** Si el formato no es el esperado, re-prompteá; mostralo como momento didáctico pero mantenelo corto.

---

## Tips para que el video sea replicable

- Mostrá el `head()` del dataframe para que vean los datos reales de Kaggle.
- Poné la predicción y la etiqueta real lado a lado: ahí se entiende qué mide cada métrica.
- Leé cada prompt en voz alta antes de mandarlo.
- Mencioná que activaste GPU y por qué (los alumnos lo van a necesitar al replicar).
- Cerrá mostrando la tabla de métricas con la alerta: es lo concreto que conecta con lo que leen en el material.
