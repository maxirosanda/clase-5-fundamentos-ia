# Guion del ejercicio en vivo: Automatización de emails con n8n

Ejercicio separado, **live-demo grabado** (~70-75 min). Construís en n8n un flujo que: recibe datos desde un formulario del propio n8n, los pasa por un nodo de IA que redacta el email, y lo envía. Los alumnos miran y replican con el video. n8n es visual (configurás nodos, no escribís código); donde haga falta una expresión o el prompt del nodo de IA, lo componés con tu chat de IA y lo pegás.

> Es bastante más corto que la clase del sitio web. Al final hay opciones para estirarlo si necesitás llenar más tiempo.

---

## Qué cubre este ejercicio

- Pipeline de datos: ingestión (formulario) → transformación (IA redacta) → acción (envío).
- Workflows y automatización (familia n8n / Make / Zapier).
- Uso de un modelo de IA para generar contenido.
- Prompt engineering (el prompt del nodo de IA).
- Validación y branching, reintentos, idempotencia y manejo de errores.
- Seguridad: manejo de credenciales.
- Notificaciones / integración con un servicio externo (email).

Junto con la clase del sitio web, este ejercicio completa el ~45% de contenido que elegiste.

---

## Prep off-camera (clave, hacelo antes de grabar)

- Cuenta de n8n iniciada (cloud o self-host).
- **Credencial de email ya configurada** (SMTP o Gmail OAuth): es lo más frágil; no lo armes en cámara y **no muestres secretos**. En vivo solo la seleccionás.
- **Credencial del nodo de IA ya cargada** (API key del proveedor) y probada: verificá que responde antes de grabar.
- Chat de IA abierto para componer el prompt del nodo de IA.
- Decididos: los campos del formulario y un caso de prueba (un email tuyo como destino real).

---

## El flujo que vas a construir

Escenario: **VerdeCasa** quiere automatizar el envío de emails personalizados a clientes. El formulario pide nombre del cliente, email de destino, tema de la consulta y tono deseado; la IA redacta el email y se envía.

`Formulario (Form Trigger)` → `Validación (IF)` → `Nodo de IA (redacta asunto + cuerpo)` → `Enviar email`

---

## Guion minuto a minuto (~75 min)

Flujo de cada paso: configurás el nodo a mano → mapeás los datos → ejecutás → verificás los datos que salen.

| # | Segmento | Min | Qué hacés | Conceptos |
|---|---|---|---|---|
| 0 | **Visión** | 5' | Mostrás el resultado final (un email ya recibido) y explicás el flujo. Creás un workflow nuevo. | Automatización, visión del pipeline |
| 1 | **Formulario (Form Trigger)** | 12' | Agregás el nodo **On form submission** (Form Trigger). Definís los campos: nombre, email destino, tema, tono. Mostrás la URL del formulario. | Ingestión de datos, trigger, formulario de n8n |
| 2 | **Validación (IF)** | 8' | Nodo **IF** para chequear campos requeridos y formato del email; rama de error para datos inválidos. | Validación, branching, workflows |
| 3 | **Nodo de IA** | 18' | Agregás un nodo de IA (p. ej. OpenAI "Message a Model" o "Basic LLM Chain"). En tu chat de IA componés el prompt que toma los campos del formulario con expresiones (`{{ $json.tema }}`, etc.) y pide **asunto + cuerpo**; lo pegás. Ejecutás con el dato de prueba y mostrás el contenido generado. | Transformación con IA, prompt engineering, mapeo de datos |
| 4 | **Enviar email** | 12' | Agregás el nodo **Send Email** (SMTP) o **Gmail**. Seleccionás la credencial ya creada. Mapeás: destinatario = campo del formulario, asunto y cuerpo = salida del nodo de IA. | Acción/exposición, notificaciones, integración de servicios, seguridad (credenciales) |
| 5 | **Prueba end-to-end** | 8' | Abrís el formulario, cargás un caso real y enviás. Mostrás el email que llega a la casilla. | Prototipo → demo, pipeline completo |
| 6 | **Robustez** | 8' | Activás **Retry On Fail** en el nodo de email; explicás idempotencia (no enviar dos veces el mismo) y manejo de errores (rama de error / Error Trigger). | Reintentos, idempotencia, manejo de errores |
| 7 | **Cierre + recap** | 4' | Recorrés el flujo nodo por nodo y recapitulás los conceptos. | Visión del pipeline |

**Total:** ~75 minutos (sin la validación del paso 2, ~67).

---

## Opciones para estirarlo (si querés más tiempo)

- **Persistencia:** sumá un nodo de Google Sheets que registre cada envío (fecha, destinatario, tema). Suma "exposición/almacenamiento de datos".
- **Confirmación al usuario:** respondé al que envió el formulario con un mensaje de "email enviado".
- **Notificación al equipo:** en paralelo, un nodo de Slack/Discord que avise al equipo de VerdeCasa.
- **Segundo paso de IA:** un nodo que traduzca el email a otro idioma, o que clasifique la consulta antes de redactar.
- **Más branching:** rutas distintas según el "tema" (reclamo, consulta, pedido) con prompts diferentes.

Con dos o tres de estas, el ejercicio se acerca a la hora y media.

---

## Riesgos y contingencias

- **#1 – Credenciales de email.** Es donde más se cae en vivo. Tenelas listas y probadas; tené un proveedor de respaldo (si usás SMTP, tené Gmail a mano, o al revés).
- **#2 – API key / cuota del nodo de IA.** Verificá que responde antes de grabar.
- **Salida malformada de la IA.** Si no separa asunto y cuerpo, mostrá cómo lo arreglás re-prompteando (pedí explícitamente un formato), pero mantenelo corto.
- **Seguridad en cámara:** nunca muestres claves ni tokens; trabajá siempre con credenciales ya guardadas.

---

## Tips para que el video sea replicable

- Mostrá los **datos de ejecución** (el JSON) en cada nodo: así los alumnos ven la información fluyendo paso a paso.
- Leé el prompt del nodo de IA en voz alta antes de ejecutarlo.
- Cargá y enviá el formulario **en cámara**, con un caso real.
- Cerrá mostrando el **email recibido** en la bandeja de entrada, no solo el "success" de n8n.
