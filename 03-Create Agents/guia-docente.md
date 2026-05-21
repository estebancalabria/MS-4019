# MS4019 – Creación y gestión de agentes en Microsoft 365 (Guía)

## 1. Introducción

* Microsoft 365 permite crear agentes para automatizar tareas y responder consultas.
* Los agentes pueden construirse en:

  * Copilot Chat (vía Copilot Studio)
  * SharePoint (herramienta integrada)

---

## 2. Componentes de un agente

Todo agente se compone de:

* **Nombre**

  * Identifica el agente.
  * Máx. ~30 caracteres.

* **Icono**

  * Imagen representativa del agente.
  * Ayuda a identificarlo visualmente.

* **Descripción**

  * Explica qué hace el agente.
  * Sirve como contexto para el modelo.

* **Instrucciones**

  * Reglas de comportamiento del agente.
  * Define tono, límites y tareas.
  * Es el núcleo del “comportamiento”.

* **Fuentes de conocimiento**

  * SharePoint, archivos, OneDrive, Graph Connectors.
  * Define qué información puede usar.

* **Capacidades (Copilot Chat)**

  * Code Interpreter (Python)
  * Generación de imágenes

* **Starter prompts**

  * Ejemplos de preguntas para el usuario.

---

## 3. Creación de agentes en Copilot Studio

### 3.1 Modo “Describe”

* Creación en lenguaje natural.
* El sistema genera automáticamente:

  * Nombre
  * Instrucciones
  * Estructura del agente
* Más simple, estilo conversación.

### 3.2 Modo “Configure”

* Configuración manual completa.
* Permite editar:

  * Instrucciones
  * Fuentes
  * Capacidades
* Más control y precisión.

### 3.3 Relación entre modos

* Ambos modos están sincronizados.
* Cambios en uno impactan en el otro.
* Permite empezar simple y refinar después.

---

## 4. Ejemplo de creación de agente

Ejemplo conceptual:

* Agente que usa NASA y SETI como fuentes
* Responde solo sobre:

  * Espacio
  * Astronomía
* Restricciones:

  * No debe responder sobre PII
  * No usar otras fuentes
* Respuestas en:

  * Inglés
  * Español
  * Klingon

Resultado:

* El sistema genera instrucciones automáticamente basadas en el texto del usuario.

---

## 5. Configuración de comportamiento

En instrucciones se define:

* Qué temas puede responder
* Qué fuentes puede usar
* Qué está prohibido (ej: PII)
* Tono de respuesta (formal, técnico, etc.)
* Formato de salida

Ejemplo:

* “Responder solo con datos de fuentes definidas”
* “No especular”
* “Mantener tono profesional”

---

## 6. Knowledge / grounding

* El agente se apoya en datos definidos.
* Puede incluir:

  * Sitios SharePoint
  * Documentos Word
  * Excel
  * OneDrive
* Regla clave:

  * Solo responde con lo que está permitido en las fuentes

---

## 7. Capacidades (solo Copilot Chat)

* Code Interpreter:

  * Ejecuta Python
  * Analiza datos

* Image Generator:

  * Genera imágenes desde texto

---

## 8. Starter prompts

* Ejemplos de uso del agente.
* Sirven como guía para el usuario.
* Se muestran al abrir el agente.
* Útiles para reutilización de consultas frecuentes.

---

## 9. Testing del agente

Antes de publicarlo:

* Probar preguntas reales
* Verificar tono
* Verificar precisión
* Validar consistencia
* Ajustar instrucciones si es necesario

---

## 10. SharePoint Agents

### 10.1 Estructura

* Overview
* Sources
* Behavior

### 10.2 Características

* Más simple que Copilot Studio
* No tiene modo “Describe”
* No tiene generación de imágenes ni código
* Limitado a 3 starter prompts

### 10.3 Fuentes

* SharePoint sites
* Document libraries
* OneDrive

---

## 11. Diferencias clave

| Copilot Studio       | SharePoint      |
| -------------------- | --------------- |
| Describe + Configure | Manual          |
| Hasta 6 prompts      | Hasta 3 prompts |
| Code + imágenes      | No              |
| Más flexible         | Más simple      |

---

## 12. Gestión de agentes

* Se pueden editar en cualquier momento
* Cambios no se reflejan hasta re-compartir
* Se pueden eliminar (borrado permanente)
* Se pueden desinstalar (solo local)

---

## 13. Ideas clave finales

* Los agentes se basan en instrucciones + datos
* El comportamiento depende de las fuentes (grounding)
* Testing es obligatorio antes de producción
* SharePoint y Copilot Studio tienen distintos niveles de control

int**
* o resumirlo a “chuleta de examen” en 1 página
