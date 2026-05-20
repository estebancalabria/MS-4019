# AI-Ready Documents para Agentes Copilot

> Guía práctica para preparar documentos Word y PDF antes de cargarlos como Knowledge Sources en Microsoft Copilot Studio.

---

## ¿Por qué importa el formato del documento?

Cuando un agente Copilot consume un documento como fuente de conocimiento, no lo "lee" como lo haría un humano. Internamente ejecuta un pipeline con cuatro etapas:

```
Documento → Chunking → Embedding → Retrieval → Generación
```

1. **Chunking**: el texto se divide en fragmentos de ~300–500 tokens
2. **Embedding**: cada chunk se convierte en un vector numérico
3. **Retrieval**: ante una pregunta, se buscan los chunks más similares semánticamente
4. **Generación**: el LLM produce una respuesta basándose únicamente en esos chunks recuperados

El problema es que **un chunk recuperado debe poder responder una pregunta de forma autónoma**, sin contexto externo. Si el documento está mal estructurado, los chunks serán fragmentos sin sentido y el agente responderá mal — aunque la información esté en el documento.

---

## Consideraciones estructurales

### Headings reales, no texto en negrita

Word permite aplicar estilos de Heading 1, Heading 2, Heading 3. Estos estilos son leídos por el parser y usados para determinar límites de chunk y jerarquía semántica.

| ✅ Correcto | ❌ Incorrecto |
|---|---|
| Párrafo con estilo `Heading 1` aplicado | Texto en negrita 18pt que "parece" un título |
| Jerarquía H1 > H2 > H3 coherente | Títulos sin jerarquía, todos del mismo nivel |

### Párrafos cohesivos por idea

Cada párrafo debería desarrollar **una sola idea**. Párrafos muy largos que mezclan múltiples conceptos generan chunks que confunden al retrieval.

### Evitar referencias cruzadas internas

Frases como *"como se explicó en la sección anterior"*, *"ver Anexo B"*, o *"el gráfico de arriba muestra..."* son problemáticas: el chunk que se recupera no trae ese contexto consigo.

### Terminología consistente

Si el documento usa "cliente", "usuario final" y "beneficiario" para referirse a la misma entidad, el retrieval puede fallar cuando la pregunta usa un término y el chunk relevante usa otro. Elegir un término canónico y usarlo de forma consistente.

---

## Contenido que daña la calidad del retrieval

### Imágenes sin descripción textual

Organigramas, flujos de proceso, tablas en imagen, capturas de pantalla — el parser extrae texto, no imágenes. Si la información clave está en una imagen sin alt text ni descripción de texto adyacente, **el agente no la verá**.

Solución: agregar párrafos descriptivos debajo de cada imagen que expliquen su contenido.

### Text boxes flotantes

Los cuadros de texto flotantes en Word (Insert > Text Box) son ignorados por la mayoría de los parsers de Copilot. Todo el contenido dentro de un text box debe migrarse al flujo principal del documento.

### Headers y footers repetitivos

El nombre de la empresa, número de página, y fecha que aparecen en cada página se convierten en ruido que se repite en múltiples chunks, diluyendo la calidad semántica.

### Tablas de diseño visual

Las tablas usadas solo para layout (poner texto en columnas, crear recuadros visuales) se parsean de forma no lineal. Usar tablas únicamente cuando los datos tienen estructura real de filas y columnas.

### Columnas múltiples

Un documento con layout de dos columnas (como una newsletter) será leído de izquierda a derecha por el parser, mezclando contenido de columnas distintas. Evitar multi-column layouts en documentos que serán fuente de conocimiento.

---

## Transformaciones recomendadas antes de cargar

### 1. Convertir a texto plano estructurado

La conversión a Markdown es una de las transformaciones más efectivas: elimina el ruido de formato, preserva la jerarquía semántica y produce texto limpio para el chunker.

#### MarkItDown — Microsoft Open Source

[**MarkItDown**](https://github.com/microsoft/markitdown) es una herramienta oficial de Microsoft que convierte documentos Word, PDF, PowerPoint, Excel, imágenes y más a Markdown.

```bash
# Instalación
pip install markitdown

# Uso básico
markitdown documento.docx > documento.md

# Desde Python
from markitdown import MarkItDown
md = MarkItDown()
result = md.convert("documento.docx")
print(result.text_content)
```

MarkItDown preserva:
- Jerarquía de headings (H1, H2, H3)
- Tablas en formato Markdown
- Listas ordenadas y no ordenadas
- Texto en negrita e itálica

Y elimina:
- Headers/footers
- Text boxes flotantes
- Metadatos de formato no semántico

Una vez convertido a `.md`, se puede cargar directamente como Knowledge Source o revisar y corregir antes de subir.

### 2. Usar Copilot en Word para limpiar el documento

Esta es quizás la forma más accesible para usuarios no técnicos: **pedirle al propio Copilot en Word que mejore el documento para consumo de IA**.

En el panel de Copilot dentro de Word, se pueden usar prompts como:

> *"Revisá este documento y reescribilo con párrafos más cortos y cohesivos, usando un heading por cada tema principal. Eliminá referencias cruzadas como 'como se dijo antes' o 'ver sección X' y reemplazalas con la información concreta."*

> *"Este documento va a ser usado como fuente de conocimiento para un agente de IA. Asegurate de que cada párrafo pueda entenderse de forma independiente, sin contexto previo. Estandarizá la terminología."*

> *"Identificá en este documento todo el contenido que está dentro de cuadros de texto o en imágenes sin descripción, y convertilo a párrafos de texto en el flujo principal del documento."*

Copilot en Word puede hacer el trabajo pesado de restructuración; el usuario solo necesita revisar y validar el resultado.

### 3. Estrategia para PDFs

Los PDFs presentan desafíos adicionales porque pueden ser:

- **PDFs de texto**: generados desde Word o similar — procesables directamente
- **PDFs escaneados**: imágenes de páginas — requieren OCR antes de ser útiles
- **PDFs de diseño**: con columnas, callouts, sidebars — requieren limpieza manual

Para PDFs escaneados, MarkItDown integra soporte de OCR con LLMs:

```python
from markitdown import MarkItDown
from openai import OpenAI

client = OpenAI()
md = MarkItDown(llm_client=client, llm_model="gpt-4o")
result = md.convert("documento_escaneado.pdf")
```

Para PDFs complejos de diseño, la recomendación es convertir primero a Word con Adobe Acrobat o Word mismo (Abrir PDF en Word), limpiar en Word con Copilot, y luego subir.

---

## Consideraciones para PDFs técnicos y manuales

Los manuales técnicos y documentos de procedimientos suelen tener estructuras problemáticas:

- Advertencias y notas en cajas visuales (NOTE, WARNING, CAUTION) — convertirlas a párrafos con prefijo textual
- Pasos numerados con imágenes intercaladas — agregar descripción de texto a cada imagen
- Glosarios al final — considerar separarlos en un documento propio para que tengan mejor peso semántico
- Apéndices con información técnica densa — evaluar si son Knowledge Sources útiles o ruido

---

## Estructura ideal de un documento AI-ready

```
[H1] Título principal del tema
Párrafo introductorio que describe de qué trata el documento
y qué preguntas responde.

[H2] Subtema A
Párrafo que desarrolla el subtema A de forma autónoma.
Toda la información necesaria para entender este punto
está en este párrafo, sin referencias externas.

[H2] Subtema B
Párrafo que desarrolla el subtema B de forma autónoma.
Usa los mismos términos que el resto del documento.

[H3] Detalle de Subtema B
Información más específica. Incluye el contexto necesario
para entenderse sin leer lo anterior.
```

---

## Checklist rápido antes de cargar un documento

### Estructura
- [ ] Los títulos usan estilos de Heading reales (H1, H2, H3), no texto en negrita manual
- [ ] El documento tiene una jerarquía de headings coherente y sin saltos
- [ ] Cada párrafo desarrolla una sola idea y puede entenderse de forma independiente
- [ ] No hay frases como "como se dijo antes", "ver sección X", "el gráfico de arriba"

### Contenido
- [ ] La información clave no está únicamente dentro de imágenes (organigramas, flujos, tablas en imagen)
- [ ] Las imágenes tienen descripción textual adyacente que explica su contenido
- [ ] Los cuadros de texto flotantes fueron migrados al flujo principal del documento
- [ ] La terminología es consistente en todo el documento (mismo término para el mismo concepto)

### Formato y ruido
- [ ] Los headers y footers no contienen información relevante (o están simplificados)
- [ ] No hay columnas múltiples (multi-column layout)
- [ ] Las tablas contienen datos reales, no son tablas de layout visual
- [ ] No hay texto con encoding raro, caracteres especiales problemáticos, o fuentes exóticas

### Para PDFs específicamente
- [ ] El PDF es de texto nativo (no escaneado) — o fue procesado con OCR previamente
- [ ] El PDF no es de diseño complejo con columnas, sidebars y callouts no lineales
- [ ] Las páginas con solo imágenes tienen contexto textual en páginas adyacentes

### Herramientas sugeridas
- [ ] Considerar convertir con [MarkItDown](https://github.com/microsoft/markitdown) y revisar el `.md` resultante
- [ ] Si el documento necesita restructuración, usar Copilot en Word con prompts de limpieza semántica
- [ ] Para PDFs escaneados, usar MarkItDown con integración LLM para OCR inteligente
