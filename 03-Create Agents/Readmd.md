# Transformación de los procesos empresariales cotidianos con agentes

## Compilación y administración de un agente – Resumen Completo

Este módulo de Microsoft Learn explora cómo crear, configurar, probar, editar y administrar agentes personalizados utilizando Microsoft 365 Copilot Chat y SharePoint. El objetivo principal es permitir que usuarios técnicos y no técnicos puedan construir asistentes inteligentes capaces de automatizar tareas, consultar información corporativa y mejorar la productividad dentro de la organización.

---

# Introducción a los agentes en Microsoft 365 Copilot

Los agentes personalizados son asistentes de inteligencia artificial diseñados para resolver tareas específicas, automatizar procesos o brindar soporte contextual dentro de una organización.

Estos agentes pueden:

* Responder preguntas.
* Consultar documentación corporativa.
* Guiar procesos internos.
* Generar contenido.
* Crear documentos, gráficos o imágenes.
* Integrarse con SharePoint, Teams y otras fuentes de datos.

Microsoft ofrece dos enfoques principales para crear agentes:

1. **Copilot Chat + Agent Builder**
2. **Agentes de SharePoint**

---

# Creación de un agente en Copilot Chat

## Agent Builder

La creación de agentes en Copilot Chat se realiza mediante el **Generador de agentes (Agent Builder)**.

El proceso puede comenzar desde:

* Una descripción en lenguaje natural.
* Una plantilla predefinida.
* Configuración manual avanzada.

El Agent Builder posee dos pestañas principales:

| Pestaña    | Función                                                 |
| ---------- | ------------------------------------------------------- |
| Describir  | Conversación en lenguaje natural para definir el agente |
| Configurar | Configuración detallada del comportamiento del agente   |

Ambas pestañas se sincronizan automáticamente.

---

# Pestaña Describir

La pestaña **Describir** permite conversar con el sistema utilizando lenguaje natural.

Por ejemplo:

* Qué hace el agente.
* Quién es su audiencia.
* Qué tono debe usar.
* Qué tareas debe resolver.

El sistema transforma automáticamente esta conversación en instrucciones estructuradas.

## Ventajas

* No requiere conocimientos técnicos.
* Facilita la creación rápida.
* Traduce lenguaje natural a instrucciones complejas.
* Ayuda a definir comportamiento, propósito y alcance.

---

# Pestaña Configurar

La pestaña **Configurar** permite controlar todos los detalles del agente.

Incluye:

* Plantillas
* Nombre
* Descripción
* Icono
* Instrucciones
* Orígenes de conocimiento
* Capacidades
* Prompts sugeridos

---

# Plantillas

Las plantillas permiten crear agentes rápidamente usando configuraciones predefinidas.

Incluyen:

* Nombre
* Descripción
* Instrucciones
* Prompts sugeridos
* Configuración inicial

## Beneficios

### Facilidad de creación

Aceleran el proceso inicial.

### Consistencia

Mantienen estructuras homogéneas.

### Buenas prácticas

Incorporan configuraciones recomendadas.

### Personalización

Pueden modificarse completamente.

### Eficiencia

Reducen tiempo de implementación.

## Importante

Cambiar de plantilla luego de personalizar el agente puede sobrescribir configuraciones existentes.

---

# Icono del agente

Cada agente puede tener un icono personalizado.

## Requisitos

* Formato `.png`
* Máximo 1 MB

---

# Nombre, descripción e instrucciones

El sistema genera instrucciones automáticamente basándose en:

* La descripción inicial.
* Las respuestas dadas durante la conversación.
* Las plantillas seleccionadas.

Las instrucciones pueden:

* Editarse manualmente.
* Refinarse desde la pestaña Describir.
* Reescribirse completamente.

---

# Cómo funcionan las instrucciones

El sistema:

1. Analiza el lenguaje natural.
2. Detecta intención y contexto.
3. Genera instrucciones estructuradas.
4. Define comportamiento del agente.

Las instrucciones controlan:

* Tono.
* Estilo.
* Restricciones.
* Tipo de respuestas.
* Flujo conversacional.

## Recomendación

Siempre revisar las instrucciones generadas antes de publicar el agente.

---

# Orígenes de conocimiento

Los agentes pueden conectarse a múltiples fuentes de datos.

## Fuentes compatibles

### Web pública

Puede habilitarse o deshabilitarse.

### URLs públicas

Hasta 4 sitios web.

### Archivos cargados

Archivos embebidos desde el dispositivo.

### Chats de Teams

Hasta 5 URLs de Teams.

### SharePoint

* Sitios
* Carpetas
* Bibliotecas
* Archivos

### Conectores de Microsoft 365

Si el administrador lo permite.

---

# Consideraciones importantes

## Acceso web

Puede ser bloqueado por políticas organizacionales.

## SharePoint restringido

Si Restricted SharePoint Search está habilitado, no podrá usarse como origen.

## Tamaño de archivos

Depende de licencias y configuración.

Ejemplo:

* Hasta 200 MB con Microsoft 365 Copilot.

## Preparación de archivos

Los archivos nuevos pueden tardar varios minutos en indexarse.

---

# Capacidades del agente

Existen funcionalidades opcionales.

## Crear documentos, gráficos y código

Usa el **Code Interpreter**.

Permite:

* Ejecutar Python.
* Analizar datos.
* Crear gráficos.
* Generar documentos Word.
* Crear Excel.
* Generar PowerPoint.
* Resolver cálculos.

El usuario NO escribe Python directamente.

---

## Crear imágenes

Usa un generador basado en la tecnología de Microsoft Designer.

Permite:

* Crear imágenes.
* Generar arte.
* Producir ayudas visuales.
* Modificar imágenes mediante prompts.

---

# Prompts sugeridos

Los prompts sugeridos ayudan a iniciar conversaciones.

Pueden:

* Generarse automáticamente.
* Editarse.
* Eliminarse.
* Crearse manualmente.

## Diferencia importante

| Plataforma   | Límite     |
| ------------ | ---------- |
| Copilot Chat | Ilimitados |
| SharePoint   | Máximo 3   |

---

# Prueba del agente

Antes de publicar un agente se recomienda probarlo exhaustivamente.

## Objetivos

* Detectar errores.
* Refinar instrucciones.
* Validar experiencia de usuario.
* Optimizar rendimiento.
* Verificar precisión.
* Comprobar cumplimiento normativo.

---

# Qué debe probarse

## Instrucciones

### Tono y estilo

* Profesional
* Casual
* Corporativo
* Soporte técnico
* Educativo

### Claridad

Verificar precisión de respuestas.

### Consistencia

Preguntar lo mismo de distintas formas.

### Adaptabilidad

Modificar instrucciones y validar cambios.

### Casos límite

Probar prompts complejos o ambiguos.

---

# Pruebas de conocimiento

## Verificar integración

Confirmar acceso correcto a datos.

## Actualización

Validar nueva información.

## Referencias cruzadas

Probar información entre múltiples fuentes.

---

# Pruebas de capacidades

## Code Interpreter

### Consultas simples

Ejemplo:

* Crear gráfico de barras.

### Consultas complejas

Ejemplo:

* Analizar datasets completos.

### Casos extremos

Ejemplo:

* Scatter plot con línea de tendencia.

---

## Generación de imágenes

### Prompt simple

“Generar una puesta de sol”.

### Prompt complejo

“Crear gráfico + código + imagen”.

---

# Creación final del agente

Cuando el agente está listo:

1. Se selecciona **Crear**.
2. El agente pasa de borrador a activo.
3. Se implementa.
4. Se sincroniza configuración.
5. Se habilita monitoreo.
6. Se vuelve compartible.

---

# Compartir agentes

Luego de crear un agente puede:

* Compartirse.
* Abrirse directamente.
* Agregarse a favoritos.
* Anclarse al panel lateral.

Inicialmente los agentes son privados.

---

# Ejercicio: creación de un agente en Copilot Chat

El laboratorio propone crear un agente completamente personalizado.

## Flujo general

1. Ingresar a Microsoft 365.
2. Seleccionar “Nuevo agente”.
3. Describir el agente.
4. Refinar preguntas.
5. Revisar instrucciones.
6. Configurar conocimiento.
7. Habilitar capacidades.
8. Probar el agente.
9. Crear el agente.
10. Compartir o usar.

## Concepto importante

El Agent Builder transforma automáticamente una descripción simple en instrucciones complejas.

---

# Creación de agentes en SharePoint

SharePoint posee su propia herramienta de agentes.

## Requisitos

Debe tener:

* Permisos de edición o superiores.

---

# Dónde crear agentes de SharePoint

Puede iniciarse desde:

1. Página principal del sitio.
2. Biblioteca documental.
3. Menú contextual de archivos.
4. Panel lateral de Copilot.

---

# Configuración de agentes de SharePoint

El editor tiene tres pestañas:

| Pestaña             | Función                    |
| ------------------- | -------------------------- |
| Información general | Nombre, descripción, icono |
| Orígenes            | Datos utilizados           |
| Comportamiento      | Instrucciones y prompts    |

---

# Orígenes en SharePoint

Puede utilizar:

* Sitio completo.
* Bibliotecas.
* Carpetas.
* Archivos específicos.

---

# Diferencias entre Copilot Chat y SharePoint

| Característica      | Copilot Chat | SharePoint |
| ------------------- | ------------ | ---------- |
| Plantillas          | Sí           | No         |
| Conversación guiada | Sí           | No         |
| Mensaje bienvenida  | No           | Sí         |
| Prompts ilimitados  | Sí           | No         |
| Code Interpreter    | Sí           | No         |
| Generación imágenes | Sí           | No         |

---

# Ejercicio: creación de agente SharePoint

El laboratorio guía al usuario para:

1. Elegir un sitio SharePoint.
2. Crear un agente.
3. Configurar orígenes.
4. Definir comportamiento.
5. Probar prompts.
6. Activar el agente.

Puede realizarse:

* En un entorno real.
* En un laboratorio simulado de Fabrikam.

---

# Edición de agentes

## Edición en Copilot Chat

Puede editarse desde:

* Lista lateral de agentes.
* Store de agentes.

Pasos:

1. Seleccionar “Editar”.
2. Modificar configuración.
3. Probar.
4. Actualizar.

---

# Edición en SharePoint

Los agentes SharePoint se almacenan como archivos `.agent`.

## Ubicaciones

### Desde página principal

`Contenido del sitio > Activos del sitio > Copilots`

### Desde bibliotecas

Dentro de la carpeta donde fueron creados.

---

# Administración de agentes

La administración correcta es clave para:

* Escalabilidad.
* Seguridad.
* Cumplimiento.
* Optimización.
* Confiabilidad.

---

# Buenas prácticas

## Planificar automatización

Definir objetivos claros.

## Mantener simplicidad

Evitar flujos excesivamente complejos.

## Documentar

Registrar propósito y configuración.

## Revisar periódicamente

Actualizar agentes regularmente.

---

# Agente predeterminado en SharePoint

Cada sitio puede tener un agente predeterminado.

El administrador puede:

* Cambiarlo.
* Restaurar el agente original.

---

# Desinstalar agentes en Copilot Chat

Copilot Chat permite:

* Desinstalar agentes.
* Mantener configuración intacta.

La eliminación definitiva solo puede hacerse desde Copilot Studio.

## Beneficios de desinstalar

* Liberar espacio.
* Solucionar problemas.
* Ocultar temporalmente.
* Conservar personalizaciones.

---

# Eliminación de agentes en SharePoint

No existe “desinstalación”.

Los agentes se eliminan como archivos normales de SharePoint.

Pasos:

1. Buscar archivo del agente.
2. Seleccionar menú contextual.
3. Elegir eliminar.

---

# Conclusiones

Microsoft 365 Copilot y SharePoint permiten crear agentes inteligentes sin necesidad de programación avanzada.

Los conceptos más importantes del módulo son:

* Uso de lenguaje natural para crear agentes.
* Configuración avanzada mediante instrucciones.
* Integración con SharePoint y Microsoft 365.
* Uso de conocimiento corporativo.
* Capacidades de IA generativa.
* Importancia de pruebas iterativas.
* Administración y mantenimiento continuo.

La combinación entre Copilot Chat y SharePoint permite construir asistentes altamente especializados para:

* Soporte interno.
* Recursos humanos.
* Gestión documental.
* Onboarding.
* Proyectos.
* Automatización empresarial.
* Productividad organizacional.
