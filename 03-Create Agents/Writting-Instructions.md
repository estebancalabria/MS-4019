# Cómo Escribir Instrucciones Efectivas para Agentes en Microsoft Copilot Studio

> **Módulo de curso:** Microsoft 365 Copilot – Creación de Agentes  
> **Audiencia:** Makers, consultores y administradores de M365 Copilot  
> **Fuentes:** Microsoft Learn, Microsoft Copilot Studio Docs, CIAOPS Blog

---

## ¿Qué es un System Prompt?

Antes de hablar de buenas prácticas, es fundamental entender el concepto de **system prompt** (instrucción de sistema).

Un **system prompt** es un bloque de texto que le da contexto, identidad, límites y comportamiento al modelo de IA **antes** de que el usuario empiece a interactuar con él. Es, en términos simples, el "contrato inicial" entre el diseñador del agente y el modelo de lenguaje.

En Microsoft Copilot Studio, el system prompt se llama **Instructions** y se configura en la página **Overview** del agente. Este texto:

- Define el **rol** del agente (quién es, para qué sirve)
- Establece las **restricciones** (qué puede y qué no puede responder)
- Determina el **formato** de las respuestas
- Indica explícitamente **qué fuentes de conocimiento debe usar** para fundamentar sus respuestas

> 💡 **Concepto clave:** Las instrucciones son tratadas por el sistema de forma similar al código. Una instrucción mal redactada puede "romper" el comportamiento del agente, igual que un bug en un programa.

---

## ¿Por qué estudiar System Prompts de otros agentes?

Una excelente forma de aprender a escribir buenas instrucciones es **leer cómo lo hacen sistemas reales**. El repositorio público:

🔗 **[https://github.com/asgeirtj/system_prompts_leaks](https://github.com/asgeirtj/system_prompts_leaks)**

...recopila supuestos system prompts filtrados de sistemas comerciales conocidos (ChatGPT, Claude, Perplexity, Copilot, entre otros). Aunque su autenticidad no puede garantizarse al 100%, son extremadamente valiosos como material de estudio porque permiten observar:

- Cómo se estructura una instrucción profesional
- Qué patrones se repiten en sistemas de producción
- Cómo se definen los límites y restricciones
- Qué tono y formato se utiliza

> ⚠️ **Nota ética:** Usar estos ejemplos como referencia educativa es legítimo. No deben replicarse para suplantar sistemas o marcas.

---

## La Importancia del Markdown en las Instrucciones

Microsoft Copilot Studio recomienda explícitamente el uso de **Markdown** para estructurar las instrucciones del agente. Hay dos razones fundamentales:

### 1. Legibilidad para humanos
Las instrucciones largas son difíciles de mantener. El Markdown permite organizarlas con secciones claras, listas y jerarquías visuales que facilitan su revisión y actualización.

### 2. Comprensión del modelo
Los modelos de lenguaje están entrenados con grandes volúmenes de texto en Markdown. Usarlo mejora la capacidad del modelo de **procesar y seguir las instrucciones correctamente**.

### Elementos de Markdown recomendados

| Elemento | Sintaxis | Cuándo usarlo |
|---|---|---|
| Encabezados de sección | `# Título`, `## Subtítulo` | Separar bloques: rol, restricciones, formato, fuentes |
| Listas no ordenadas | `- ítem` | Enumerar reglas o comportamientos |
| Listas numeradas | `1. paso` | Secuencias de pasos en orden estricto |
| Negritas | `**texto**` | Marcar instrucciones críticas |
| Código inline | `` `nombre` `` | Referenciar nombres de fuentes de conocimiento o secciones |

**Ejemplo de estructura con Markdown:**

```markdown
## Rol
Eres un asistente especializado en beneficios de RRHH de Contoso.

## Restricciones
- Solo responde preguntas sobre beneficios de salud, dental y bienestar.
- No respondas preguntas fuera de este dominio.

## Fuentes de conocimiento
- Basa todas tus respuestas exclusivamente en el sitio de SharePoint "RRHH-Beneficios".
- Si la información no está en ese sitio, indícalo al usuario.

## Formato de respuesta
- Usa tablas para comparar planes de salud.
- Incluye siempre un link al portal de inscripción.
```

---

## Buenas Prácticas para Escribir Instrucciones

Las siguientes prácticas están basadas en la documentación oficial de Microsoft Copilot Studio y en experiencia de la comunidad de makers.

### ✅ 1. Define el Rol y el Objetivo con Claridad

El agente debe saber exactamente **quién es** y **para qué existe**. Un rol vago produce respuestas inconsistentes.

```
Eres un asistente de soporte de RRHH para empleados de Contoso.
Tu objetivo es responder consultas sobre beneficios, licencias y políticas internas.
```

---

### ✅ 2. Establece Restricciones Claras (Constraints)

Definir qué debe responder **y qué no** es tan importante como definir el objetivo. Sin restricciones, el agente puede responder cosas para las que no fue diseñado.

```
Solo responde preguntas relacionadas con beneficios educativos, de salud y bienestar
para empleados y sus dependientes.
Si el usuario pregunta algo fuera de este dominio, indícale que no puedes ayudar
con esa consulta y sugiérele contactar a soporte@contoso.com.
```

---

### ✅ 3. Referencia Explícitamente las Fuentes de Conocimiento

Este es uno de los puntos más importantes y frecuentemente omitidos. **Aunque las fuentes de conocimiento estén configuradas en el agente, el modelo puede no usarlas si no se le indica explícitamente en las instrucciones.**

Mencioná por nombre la fuente que debe consultar y en qué situaciones:

```
Para responder consultas sobre beneficios, busca siempre en el sitio de SharePoint
"RRHH-Beneficios-2025".
Para consultas sobre políticas de licencias, consultá el documento
"Política de Licencias - Contoso v3.pdf" disponible en la Knowledge Base.
```

> 💡 **Tip:** Cuantas más fuentes tenga el agente configuradas, más importante es especificar en las instrucciones cuál usar para cada tipo de consulta. Esto evita que el agente elija una fuente incorrecta o mezcle información de distintos orígenes.

---

### ✅ 4. Especifica el Formato de las Respuestas

El agente puede estructurar sus respuestas de distintas formas. Si no se le indica, elegirá por defecto. Sé explícito con el formato esperado.

```
Siempre respondé consultas sobre planes de salud en formato de tabla comparativa.
Incluí columnas para: Plan, Cobertura, Costo mensual, Red de prestadores.
Agregá al final un párrafo con la recomendación más adecuada según el caso.
```

---

### ✅ 5. Usa Verbos Precisos y Vocabulario Accionable

Microsoft recomienda un vocabulario específico según el objetivo de cada instrucción:

| Objetivo | Verbos recomendados |
|---|---|
| Condiciones | `when`, `if`, `ensure`, `compare` |
| Filtrar información | `from`, `include`, `exclude`, `identify` |
| Recuperar datos | `get`, `retrieve`, `use`, `analyze`, `extract` |
| Interacción con el usuario | `notify`, `ask`, `suggest`, `confirm` |

**Ejemplo:**
```
When the user asks about their health plan, retrieve the relevant information
from the SharePoint knowledge source "RRHH-Beneficios-2025".
If the plan is not found, ask the user to confirm the plan name.
```

---

### ✅ 6. Numera los Pasos cuando el Orden Importa

Para flujos donde las acciones tienen un orden necesario, enumeralas explícitamente:

```
1. Saludá al usuario y preguntá en qué podés ayudarlo.
2. Identificá si la consulta es sobre beneficios de salud, dental o bienestar.
3. Buscá la información en la fuente de conocimiento correspondiente.
4. Presentá la respuesta en el formato indicado.
5. Preguntá si el usuario necesita más información.
```

---

### ✅ 7. Usá el Framework: Rol / Restricciones / Fuentes / Formato

Una estructura probada en la comunidad de Copilot Studio para organizar las instrucciones:

```markdown
## Rol
[Quién es el agente y cuál es su propósito]

## Restricciones
[Qué consultas puede y no puede responder]

## Fuentes de conocimiento
[Qué documentos o sitios debe consultar y cuándo]

## Formato de respuesta
[Cómo debe estructurar y presentar las respuestas]

## Tono
[Solo si el tono debe diferir del profesional/cortés por defecto]
```

---

## Tips Críticos de Comportamiento

### 🚫 Tip 1 — Que el agente NO responda fuera de su objetivo

El agente debe rechazar educadamente preguntas fuera de su dominio. Esto se conoce como **guardrails** o scope enforcement.

```
Solo respondé mensajes relacionados con los recursos humanos de Contoso.
Si el usuario pregunta sobre otro tema, respondé:
"Lo siento, solo puedo ayudarte con consultas de RRHH de Contoso.
Para otras consultas, contactá a soporte@contoso.com."
```

---

### 📚 Tip 2 — Que fundamente sus respuestas SOLO en documentos citados

Si el agente tiene fuentes de conocimiento configuradas, instruilo explícitamente para que **siempre cite las fuentes** y no responda desde su conocimiento general.

```
CUANDO GENERES UNA RESPUESTA, CITÁ SIEMPRE LA FUENTE.
Conservá los tags de cita en el formato [^x_y^] exactamente como aparecen.
No alteres, agregues ni elimines ningún tag de cita.
Toda afirmación debe poder rastrearse a un documento o sitio de la Knowledge Base.
```

Esta instrucción, recomendada por Microsoft Learn, garantiza trazabilidad y confianza en las respuestas del agente.

---

### 🤐 Tip 3 — Que si no sabe, NO invente

La **alucinación** — cuando el modelo inventa información que no existe — es uno de los mayores riesgos de los agentes de IA. Instrúyelo explícitamente para que no lo haga:

```
Si no encontrás información relevante en las fuentes de conocimiento configuradas,
respondé honestamente que no tenés esa información disponible.
NO inventes datos, fechas, nombres, montos ni procedimientos.
Sugerí al usuario contactar a [nombre del equipo o canal] para consultas sin respuesta.
```

> 💡 Complementá esto desactivando la opción **"Allow the AI to use its own general knowledge"** en la configuración de Generative AI del agente, si no querés que el modelo responda fuera de las fuentes configuradas.

### 🎨 Tip 4 — Dar un template exacto de salida en Markdown

Aunque Copilot Studio soporta Markdown en las respuestas del agente, **el modelo no lo usará consistentemente si no se lo instruís**. La técnica más efectiva no es solo decirle "usá Markdown" — es **mostrarle exactamente cómo debe verse cada respuesta** con un template concreto.

Incluí en el system prompt un bloque como este, con el molde de salida que querés:

````markdown
## Formato de respuesta

Estructurá SIEMPRE tus respuestas siguiendo este template exacto:

---
### [Título breve que describe la consulta]

**Resumen:** [Una oración con la respuesta directa a la consulta.]

**Detalle:**
- [Punto 1]
- [Punto 2]
- [Punto 3]

| Campo | Valor |
|---|---|
| [Dato clave 1] | [Valor] |
| [Dato clave 2] | [Valor] |

**Fuente:** [^cita^]

> ¿Hay algo más en lo que pueda ayudarte?
---
````

> 💡 **Por qué importa:** Darle un template reduce la variabilidad del modelo — en lugar de inventar una estructura diferente en cada respuesta, sigue el molde. Esto hace que el agente sea más **predecible y consistente**, lo que mejora la experiencia del usuario y facilita el testing. Además, los modelos de lenguaje aprenden mejor de ejemplos concretos que de instrucciones abstractas como "respondé de forma clara y ordenada".

---

### 🧠 Tip 5 — Método socrático: pedirle que haga preguntas de a una cuando falta contexto

Uno de los problemas más comunes en agentes mal configurados es que el modelo **asume contexto que no tiene** y responde con información incorrecta o genérica. La solución es instruirlo explícitamente para que, cuando le falte información, haga preguntas — pero **de a una por vez**.

```
Si para responder correctamente necesitás información que el usuario no proporcionó,
no asumas ni inventes. En cambio, hacé UNA sola pregunta aclaratoria a la vez.
Esperá la respuesta antes de hacer la siguiente pregunta.
No bombardees al usuario con múltiples preguntas en el mismo mensaje.

Ejemplo:
- ✅ "¿Para cuántos empleados es el plan que estás consultando?"
- ❌ "¿Para cuántos empleados es? ¿Qué cobertura necesitás? ¿En qué provincia?"
```

> 💡 **Por qué funciona:** Este enfoque, inspirado en el método socrático, guía al usuario hacia la respuesta correcta mediante preguntas progresivas. Evita abrumarlo, mantiene la conversación fluida y permite al agente construir contexto de forma iterativa antes de comprometerse con una respuesta.

---

### 🌡️ Tip 6 — La temperatura: determinismo vs. creatividad

La **temperatura** es un parámetro del modelo de lenguaje que controla cuánta aleatoriedad hay en las respuestas. Entenderla es clave para diseñar agentes predecibles.

| Temperatura | Comportamiento | Cuándo usarla |
|---|---|---|
| **Baja (≈ 0)** | Respuestas muy consistentes, casi siempre la misma salida para la misma pregunta | Agentes de soporte técnico, consultas de datos, FAQs |
| **Media (≈ 0.5–0.7)** | Balance entre consistencia y variedad | Asistentes conversacionales generales |
| **Alta (≈ 1+)** | Respuestas creativas y variadas, más riesgo de desviación | Generación de contenido, brainstorming |

En Microsoft Copilot Studio, **la temperatura no se configura directamente en la interfaz** — es manejada internamente por el modelo. Sin embargo, **podés simular un comportamiento de baja temperatura desde el system prompt** siendo muy explícito y estructurado en tus instrucciones:

```
Respondé siempre siguiendo el template de formato indicado.
No improvises estructuras alternativas.
Si la respuesta no encaja en el template, adaptá el template mínimamente
y justificá el cambio al final del mensaje.
```

> ⚠️ **Para tener en cuenta:** Cuanto más abierta y ambigua es la instrucción, más "creativo" (y menos predecible) se vuelve el modelo. Un system prompt detallado y con templates actúa como un regulador de temperatura implícito.

---

### 🤖 Tip 7 — Usá el agente Prompt Coach para mejorar tus instrucciones

Microsoft 365 Copilot incluye un agente oficial llamado **Prompt Coach** que actúa como un asistente pedagógico especializado en ayudarte a escribir mejores prompts e instrucciones. En lugar de adivinar si tu system prompt está bien redactado, podés pedirle a Prompt Coach que lo analice y lo mejore.

**¿Qué hace Prompt Coach?**
- Analiza tus instrucciones y te da feedback sobre claridad, estructura y cobertura
- Te guía a través del framework **Goal → Context → Source → Expectations (GCSE)**
- Sugiere reformulaciones más precisas y accionables
- Verifica que el prompt cumpla con las guías de Responsible AI
- Propone ejemplos concretos para mejorar la consistencia del agente

**¿Cómo acceder?**

Prompt Coach está disponible como template oficial en Microsoft 365 Copilot:

1. Abrí **Microsoft 365 Copilot** (copilot.microsoft.com)
2. Buscá el agente **"Prompt Coach"** en la galería de agentes
3. Instalalo y comenzá una conversación pegando tu system prompt actual

> 🔗 Documentación oficial: [Create a Prompt Coach agent from a template – Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agent-template-prompt-coach)

**Flujo de trabajo recomendado:**

```
1. Escribí una primera versión de tus instrucciones (borrador inicial)
2. Pegáselas a Prompt Coach y pedile: "Analizá estas instrucciones para un agente
   de Copilot Studio. ¿Qué le falta? ¿Qué está ambiguo? Sugerí mejoras."
3. Aplicá el feedback y volvé a pegar la versión mejorada
4. Repetí hasta que Prompt Coach no encuentre mejoras significativas
5. Copiá la versión final en el campo Instructions de tu agente en Copilot Studio
```

> 💡 **Por qué funciona:** Usás IA para mejorar las instrucciones con las que vas a construir IA. Es un ciclo de mejora continua — y el mejor validador de un system prompt es otro modelo de lenguaje que entiende qué hace que una instrucción sea efectiva o no.

---

### 📝 Tip 8 — Few-shot: mostrá ejemplos de conversación dentro del system prompt

Una de las técnicas más potentes — y menos usadas por makers principiantes — es incluir **ejemplos de intercambio usuario/agente directamente en las instrucciones**. Esto se llama **few-shot prompting** y le muestra al modelo exactamente qué tono, formato y nivel de detalle se espera, mejor que cualquier descripción abstracta.

```markdown
## Ejemplos de conversación esperada

**Ejemplo 1 — Consulta dentro del scope:**

Usuario: ¿Cuáles son los planes de salud disponibles para empleados?
Agente:
### Planes de salud disponibles

**Resumen:** Contoso ofrece tres planes de salud para empleados en relación de dependencia.

| Plan | Cobertura | Costo mensual empleado |
|---|---|---|
| Plan Básico | 70% | $2.500 |
| Plan Estándar | 85% | $4.200 |
| Plan Premium | 100% | $6.800 |

**Fuente:** [^RRHH-Beneficios-2025^]

> ¿Querés que te explique las diferencias en la red de prestadores?

---

**Ejemplo 2 — Consulta fuera del scope:**

Usuario: ¿Cuánto es mi sueldo este mes?
Agente: Esa información la gestiona el área de Liquidación de Haberes.
Te recomiendo contactarlos en sueldos@contoso.com.
¿Puedo ayudarte con alguna consulta sobre tus beneficios?
```

> 💡 **Por qué funciona:** Los modelos de lenguaje aprenden mejor de ejemplos concretos que de reglas abstractas. Un ejemplo de conversación bien escrito vale más que tres párrafos de instrucciones. Incluir al menos un ejemplo "dentro del scope" y uno "fuera del scope" establece el comportamiento esperado en ambos casos.

---

### 🌐 Tip 9 — El idioma de las instrucciones importa

Los modelos de lenguaje que potencian Copilot Studio están entrenados mayoritariamente en **inglés**. Esto tiene un impacto real y medible en la calidad de las instrucciones:

| Instrucciones en... | Ventajas | Desventajas |
|---|---|---|
| **Inglés** | Mayor precisión, mejor seguimiento de instrucciones complejas, menos ambigüedad | Más difícil de mantener para equipos hispanohablantes |
| **Español** | Más accesible para el equipo maker, más fácil de revisar | Puede haber pérdida de matiz en instrucciones muy específicas |

**Recomendación práctica:**

- Si el agente responde a usuarios en **español**, configurá el idioma de respuesta en las instrucciones pero podés escribir las instrucciones en inglés:
```
Always respond in Spanish, using formal "usted" tone.
Respond only to questions related to Contoso HR benefits.
```
- Si el equipo maker no maneja inglés fluido, escribí en español — una instrucción clara en español es mejor que una instrucción confusa en inglés.
- **No mezcles idiomas** en el mismo bloque de instrucciones — genera inconsistencias en la interpretación del modelo.

> 💡 **Tip práctico:** Usá Prompt Coach (Tip 7) para traducir y mejorar tus instrucciones al inglés una vez que tenés clara la lógica en español.

---

### 🗂️ Tip 10 — Versioná tus instrucciones como si fueran código

Las instrucciones de un agente en producción **cambian con el tiempo** — se descubren nuevos casos borde, cambian las políticas del negocio, mejoran las técnicas de prompting. Sin un sistema de versionado, es imposible saber qué cambió, cuándo y por qué.

**Práctica recomendada:**

Guardá cada versión del system prompt en un archivo de texto o documento de SharePoint con este encabezado:

```
# System Prompt — Agente RRHH Contoso
# Versión: 1.3
# Fecha: 2025-05-20
# Autor: [nombre]
# Cambios: Se agregó restricción sobre consultas de sueldos.
#           Se actualizó la fuente de conocimiento a RRHH-Beneficios-2025.
# Versión anterior: 1.2 (2025-04-10)
```

**Por qué importa en entornos empresariales:**
- Permite hacer **rollback** si una nueva versión empeora el comportamiento
- Facilita la **auditoría** — en organizaciones reguladas, saber qué instrucciones tenía el agente en una fecha determinada puede ser un requisito
- Habilita la **colaboración** — varios makers pueden trabajar sobre el mismo agente sin pisarse
- Convierte las instrucciones en un **activo documentado** de la organización, no en conocimiento tácito de una persona

> 💡 Si tu organización ya usa GitHub o Azure DevOps, considerá guardar los system prompts en un repositorio junto con el resto de la configuración del agente.

---

## Lo que las Instrucciones NO pueden hacer

Es importante conocer las limitaciones para gestionar expectativas correctamente:

- **No pueden invocar fuentes de conocimiento que no están configuradas** — si instruís al agente a buscar en un documento que no fue agregado como Knowledge Source, la instrucción no tendrá efecto. Las fuentes deben estar habilitadas en la configuración del agente.
- **No reemplazan la configuración** — las instrucciones guían el comportamiento, pero los recursos (fuentes de conocimiento) deben existir y estar activos.
- **No modifican el comportamiento de Adaptive Cards** — eso se configura directamente en la tarjeta.

---

## Problemas Comunes al Escribir Instrucciones

### 🧠 Alucinaciones

La **alucinación** es cuando el modelo genera información que suena plausible pero es falsa o inexistente. Es el riesgo más conocido de los LLMs y uno de los más difíciles de eliminar por completo.

**¿Por qué ocurre?**
Los modelos de lenguaje no "saben" — predicen la siguiente palabra más probable. Cuando no tienen información suficiente en las fuentes configuradas, pueden completar la respuesta con datos de su entrenamiento o directamente inventarlos.

**Síntomas frecuentes:**
- Cita documentos que no existen
- Inventa nombres, fechas, montos o procedimientos
- Responde con seguridad sobre temas fuera de su base de conocimiento

**Cómo mitigarlo desde las instrucciones:**
```
Si no encontrás la información en las fuentes de conocimiento configuradas,
respondé: "No tengo esa información disponible en mi base de conocimiento.
Te recomiendo consultar a [equipo/canal]."
NO inventes ni supongas datos. La precisión es más importante que dar una respuesta.
```

---

### 🎲 Determinismo y variabilidad

El **determinismo** se refiere a qué tan consistente es el agente: si ante la misma pregunta siempre da la misma respuesta, o si varía cada vez.

Un agente con **alta variabilidad** puede:
- Dar respuestas distintas a la misma pregunta en distintas sesiones
- Cambiar el formato de salida sin motivo
- Interpretar de forma diferente instrucciones ambiguas

**¿Por qué importa en producción?**
Los usuarios y los equipos de soporte esperan comportamiento predecible. Un agente que responde diferente cada vez genera desconfianza.

**Cómo reducir la variabilidad desde las instrucciones:**
- Usá templates de respuesta concretos (ver Tip 4)
- Evitá instrucciones ambiguas o abiertas a interpretación
- Sé explícito con los límites: qué hacer, qué no hacer, qué decir cuando no sabe
- Cuanto más específica es la instrucción, menos margen tiene el modelo para improvisar

> 💡 **Regla práctica:** Si podés imaginarte dos respuestas razonablemente diferentes para la misma pregunta dado tu system prompt, la instrucción es demasiado ambigua. Refinala.

---


## Errores Frecuentes al Escribir Instrucciones (Anti-patterns)

Estos son los errores más comunes que se ven en agentes mal configurados. Reconocerlos es el primer paso para evitarlos.

| ❌ Anti-pattern | Ejemplo malo | ✅ Versión corregida |
|---|---|---|
| **Rol vago** | "Sos un asistente útil." | "Sos un asistente de RRHH para empleados de Contoso, especializado en beneficios y licencias." |
| **Sin restricciones** | *(no hay ninguna)* | "Solo respondés preguntas sobre RRHH. Para otros temas derivás a soporte@contoso.com." |
| **Instrucción contradictoria** | "Sé breve pero explicá todo en detalle." | "Respondé en máximo 3 bullets. Si el usuario quiere más detalle, ofrecé expandir." |
| **Formato no especificado** | "Respondé bien." | "Usá el template de respuesta definido en la sección Formato." |
| **Fuente no referenciada** | *(fuentes configuradas pero no mencionadas)* | "Consultá siempre el SharePoint 'RRHH-Beneficios-2025' antes de responder." |
| **Instrucción negativa sin alternativa** | "No respondas sobre sueldos." | "Si te preguntan sobre sueldos, indicá que esa información la maneja el área de Compensaciones y derivá a comp@contoso.com." |
| **Demasiadas instrucciones mezcladas** | Un párrafo de 500 palabras sin estructura | Secciones separadas con `##` para rol, restricciones, formato y fuentes |

> 💡 **Regla de oro:** Si tu instrucción es ambigua para un humano que la lee por primera vez, también lo será para el modelo.

---

## Prueba y Refinamiento Iterativo

Las instrucciones no son estáticas. Deben evolucionar con el uso.

1. **Probá con el Test Pane** de Copilot Studio antes de publicar
2. **Probá casos borde** — preguntas ambiguas, fuera de scope, mal formuladas
3. **Agregá instrucciones de a poco** — si algo se rompe con muchos cambios a la vez, es difícil identificar la causa
4. **Revisá logs y feedback de usuarios** para detectar respuestas incorrectas
5. **Iterá colaborativamente** — involucra a quienes conocen el dominio del negocio

> 💡 Si el agente no responde como se espera, intentá **quitar todas las instrucciones y agregarlas de a una**, probando entre cada adición. Esto ayuda a identificar instrucciones conflictivas.

---

## Recursos Oficiales

| Recurso | URL |
|---|---|
| Write agent instructions – Microsoft Copilot Studio | [learn.microsoft.com](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-instructions) |
| Configure high-quality instructions (generative orchestration) | [learn.microsoft.com](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/generative-mode-guidance) |
| Best practices for declarative agents (M365 Copilot) | [learn.microsoft.com](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-best-practices) |
| Design guidance and best practices | [learn.microsoft.com](https://learn.microsoft.com/en-us/copilot/microsoft-365/employee-self-service/design-best-practices) |
| Repositorio de system prompts filtrados (referencia educativa) | [github.com/asgeirtj/system_prompts_leaks](https://github.com/asgeirtj/system_prompts_leaks) |

---


---

## Apéndice — Template Completo de System Prompt

Este template integra todas las buenas prácticas del documento. Está listo para copiar, adaptar y usar como punto de partida en cualquier agente de Copilot Studio.

```markdown
# System Prompt — [Nombre del Agente]
# Versión: 1.0 | Fecha: [YYYY-MM-DD] | Autor: [nombre]

## Rol
Sos [nombre del agente], un asistente especializado en [dominio] para [audiencia].
Tu objetivo es [objetivo principal del agente].
Trabajás exclusivamente para [nombre de la organización].

## Restricciones
- Solo respondés preguntas relacionadas con [dominio específico].
- No respondés consultas sobre [temas excluidos explícitamente].
- Si el usuario pregunta algo fuera de tu dominio, respondé:
  "Lo siento, solo puedo ayudarte con [dominio]. Para otras consultas,
  contactá a [canal/email]."
- No inventés información. Si no encontrás la respuesta en tus fuentes,
  decilo honestamente.
- No uses conocimiento general propio — basate únicamente en las fuentes configuradas.

## Fuentes de conocimiento
- Para consultas sobre [tema A], buscá en [nombre exacto de la fuente A].
- Para consultas sobre [tema B], consultá el documento "[nombre del documento B]".
- Si la información no está disponible en ninguna fuente configurada, respondé:
  "No tengo esa información disponible. Te recomiendo contactar a [equipo/canal]."

## Comportamiento ante falta de contexto
Si para responder necesitás información que el usuario no proporcionó,
no asumas ni inventes. Hacé UNA sola pregunta aclaratoria a la vez.
Esperá la respuesta antes de continuar.

## Formato de respuesta
Estructurá SIEMPRE tus respuestas siguiendo este template:

---
### [Título breve que describe la consulta]

**Resumen:** [Una oración con la respuesta directa.]

**Detalle:**
- [Punto 1]
- [Punto 2]
- [Punto 3]

| Campo        | Valor   |
|---|---|
| [Dato clave 1] | [Valor] |
| [Dato clave 2] | [Valor] |

**Fuente:** [^cita^]

> ¿Hay algo más en lo que pueda ayudarte?
---

Usá Markdown en todas las respuestas:
- `##` para títulos de sección
- `**negrita**` para términos clave
- `-` para listas
- Tablas para comparaciones
- Nunca respondas con bloques de texto sin estructura cuando haya más de tres puntos.

## Citas
CUANDO GENERES UNA RESPUESTA, CITÁ SIEMPRE LA FUENTE.
Conservá los tags de cita en el formato [^x_y^] exactamente como aparecen.
No alteres, agregues ni elimines ningún tag de cita.

## Ejemplos de conversación esperada

**Ejemplo 1 — Consulta dentro del scope:**

Usuario: [pregunta típica dentro del dominio]
Agente:
### [Título]

**Resumen:** [respuesta directa]

**Detalle:**
- [punto]
- [punto]

**Fuente:** [^fuente^]

> ¿Hay algo más en lo que pueda ayudarte?

---

**Ejemplo 2 — Consulta fuera del scope:**

Usuario: [pregunta fuera del dominio]
Agente: Esa consulta está fuera de mi área. Te recomiendo contactar a [canal].
¿Puedo ayudarte con alguna consulta sobre [dominio]?
```

> ⚠️ **Recordá:** Este template es un punto de partida. Ajustá cada sección al dominio específico de tu agente, probalo con casos reales y refinalo iterativamente con el feedback de los usuarios y la ayuda de Prompt Coach.

*Documento preparado para el curso de Microsoft 365 Copilot – Módulo de creación de agentes.*  
*Última actualización: Mayo 2026*
