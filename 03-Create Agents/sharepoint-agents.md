# Comparativa: Agentes en SharePoint vs Agentes en Copilot Chat

> **Audiencia:** Arquitectos de soluciones, administradores IT y consultores de adopción Microsoft 365  
> **Actualizado:** Mayo 2026

---

## 1. ¿Qué es SharePoint?

Microsoft SharePoint es una plataforma de colaboración y gestión de contenido empresarial que forma parte del ecosistema Microsoft 365. Permite a las organizaciones crear sitios de intranet, almacenar y compartir documentos, gestionar flujos de trabajo y publicar contenido interno de forma estructurada.

Sus pilares principales son:

- **Gestión documental:** Bibliotecas con control de versiones, metadatos y coautoría en tiempo real.
- **Sitios de equipo y comunicación:** Espacios colaborativos por proyecto, área o departamento.
- **Integración con el ecosistema M365:** Conexión nativa con Teams, OneDrive, Power Automate, Power Apps y Copilot.
- **Búsqueda empresarial:** Motor de búsqueda indexado sobre el contenido organizacional, respetando permisos por usuario.

Con la irrupción de la IA generativa, SharePoint se convirtió en una fuente de conocimiento clave para los agentes de Copilot, dado que concentra gran parte del saber institucional de las organizaciones.

---

## 2. El modelo de Agentes en Microsoft 365

Microsoft introdujo el concepto de **agentes** como extensiones de IA especializadas que amplían las capacidades de Copilot. A diferencia de un chat de propósito general, un agente está enfocado en un dominio, conjunto de documentos o flujo de trabajo específico.

Existen dos superficies principales donde estos agentes operan:

1. **SharePoint Agents** – nativos de la plataforma SharePoint.
2. **Agentes en Copilot Chat** – accesibles desde la interfaz centralizada de Microsoft 365 Copilot Chat.

---

## 3. SharePoint Agents

### ¿Qué son?

Los SharePoint Agents son agentes de IA que viven dentro de un sitio de SharePoint. Cada sitio moderno viene con un **agente listo para usar** (*ready-made agent*) que toma como fuentes de conocimiento el propio sitio y sus sitios hub asociados. Además, los editores del sitio pueden crear **agentes personalizados** acotados a páginas, bibliotecas o carpetas específicas.

### Características principales

- Se crean directamente desde la interfaz del sitio, sin código.
- El conocimiento proviene de páginas, bibliotecas de documentos y sitios hub del tenant.
- Se pueden publicar y compartir dentro del sitio o en Teams.
- Desde octubre de 2025, también es posible incrustar agentes creados en Copilot Studio directamente en SharePoint, habilitando acciones avanzadas, flujos de Power Automate y lógica compleja.

### Tipos de archivo soportados

Los agentes de SharePoint soportan los formatos de documento estándar de Office (Word, Excel, PowerPoint, PDF, etc.). Actualmente **no** procesan datos de Listas de SharePoint ni páginas de la biblioteca *Site Pages*.

### Casos de uso típicos

- Agente de onboarding en el sitio de RRHH.
- Asistente de políticas internas en el sitio de Cumplimiento.
- Agente de soporte técnico sobre la base de conocimiento del área de IT.
- Consulta de catálogos de productos en sitios de ventas.

### Seguridad en SharePoint Agents

La seguridad es **heredada del modelo de permisos de SharePoint**. Puntos clave:

- **Trimming de permisos:** El agente sólo devuelve información de los documentos y páginas a los que el usuario que consulta tiene acceso. Si un documento está fuera del alcance del usuario, el agente no lo referenciará, aunque esté incluido en las fuentes configuradas.
- **Sin elevación de privilegios:** El agente opera bajo la identidad del usuario autenticado. No existe mecanismo para que el agente acceda a contenido restringido en nombre del usuario.
- **Sensitivity Labels (Purview):** Los documentos etiquetados con permisos definidos por el usuario y cifrados no son accedidos por el agente a menos que el usuario tenga permisos `EXTRACT` explícitos sobre ellos.
- **Administración centralizada:** Los administradores de SharePoint pueden gestionar qué agentes están activos en el tenant desde el **Copilot Control System** en el Microsoft 365 Admin Center.
- **Historial de chat:** El historial de conversaciones con el agente es privado para cada usuario. Sólo el propio usuario puede verlo o eliminarlo.
- **Auditoría:** Los administradores con permisos de SharePoint Admin o superiores pueden supervisar el uso de agentes a nivel de tenant.

---

## 4. Agentes en Copilot Chat

### ¿Qué es Copilot Chat?

Microsoft 365 Copilot Chat es la interfaz centralizada de IA de Microsoft 365, disponible en la web, Teams y aplicaciones móviles. Funciona como punto de acceso unificado para la asistencia con IA generativa, con dos modalidades según la licencia del usuario:

| Modalidad | Disponibilidad |
|---|---|
| Copilot Chat (base) | Incluido con licencias Microsoft 365 |
| Microsoft 365 Copilot (completo) | Requiere licencia adicional M365 Copilot |

### Agentes en Copilot Chat

Los agentes en Copilot Chat son asistentes especializados que los usuarios pueden invocar directamente desde la interfaz de chat. Se crean en **Copilot Studio** y se despliegan en el canal de Copilot Chat.

### Características principales

- Acceso a fuentes de datos amplias: SharePoint, Graph Connectors, APIs externas, bases de datos.
- Soporte para acciones (triggers en Power Automate, llamadas a APIs REST).
- Lógica avanzada: temas, condiciones, variables y flujos.
- Los usuarios sin licencia M365 Copilot pueden acceder a agentes básicos (web-grounded); los agentes que acceden a SharePoint o Graph requieren licencia M365 Copilot o facturación por consumo (*pay-as-you-go*) habilitada en el tenant.
- Disponibles también en Teams mediante @menciones.

### Casos de uso típicos

- Agente de helpdesk que crea tickets vía API y consulta la base de conocimiento.
- Asistente de ventas que accede a Dynamics 365 y SharePoint simultáneamente.
- Agente de RR.HH. que integra datos de múltiples sistemas de gestión.
- Copilot de reuniones con acceso a calendario, correo y documentos.

### Seguridad en Agentes de Copilot Chat

- **Microsoft Graph como capa de acceso:** Copilot Chat accede a los datos organizacionales a través de Microsoft Graph, respetando todos los permisos y políticas de acceso condicional del tenant.
- **Sin acceso a datos internos por defecto:** En la modalidad base (sin licencia M365 Copilot), Copilot Chat **no** puede leer emails, archivos de SharePoint, chats de Teams ni calendarios. Sólo procesa lo que el usuario carga manualmente o tiene abierto.
- **Con licencia M365 Copilot:** Se habilita el acceso a datos del tenant siempre dentro del scope de permisos del usuario. El modelo no tiene visibilidad universal; sólo accede a lo que el usuario autenticado podría ver.
- **Controles administrativos:**  Los administradores de tenant pueden habilitar o bloquear agentes específicos desde el Admin Center. El bloqueo de un agente afecta su disponibilidad en Copilot Chat.
- **Facturación por consumo y grupos de seguridad:** Si el tenant usa el modelo *pay-as-you-go* de Copilot Studio, el acceso a agentes avanzados puede restringirse mediante grupos de seguridad asignados a la política de facturación.
- **Sensitivity Labels y Purview:** Al igual que con SharePoint Agents, los documentos cifrados con permisos definidos por el usuario no son accesibles para el agente a menos que el usuario tenga permisos explícitos.
- **Compliance:** Copilot Chat honra los controles de seguridad, cumplimiento, privacidad y residencia de datos del tenant configurados en Microsoft Purview.

---

## 5. Cuadro comparativo

| Dimensión | SharePoint Agents | Agentes en Copilot Chat |
|---|---|---|
| **Superficie** | Sitio de SharePoint (web, Teams) | Copilot Chat (web, Teams, móvil) |
| **Creación** | Desde el sitio, sin código (+ Copilot Studio avanzado) | Copilot Studio (low-code / pro-code) |
| **Fuentes de conocimiento** | Sitio actual, sitios hub, bibliotecas seleccionadas | SharePoint, Graph Connectors, APIs, archivos subidos |
| **Acceso a datos del tenant** | Sí (scope del sitio + permisos del usuario) | Sólo con licencia M365 Copilot o metered billing |
| **Soporte para acciones** | Limitado (Copilot Studio integrado desde oct. 2025) | Completo (flujos, APIs, conectores) |
| **Lógica avanzada** | Básica en agentes nativos / avanzada vía Copilot Studio | Completa (temas, variables, condiciones) |
| **Licencia mínima** | M365 Copilot o pay-as-you-go habilitado | M365 base (agentes web) / M365 Copilot (datos tenant) |
| **Seguridad de acceso** | Trimming de permisos SharePoint por usuario | Microsoft Graph + permisos de usuario |
| **Administración** | SharePoint Admin Center + Copilot Control System | Microsoft 365 Admin Center + Copilot Control System |
| **Auditoría** | Supervisión por SharePoint Admin | Logs de actividad de Copilot en Purview |
| **Complejidad de creación** | Baja | Media-alta |
| **Ideal para** | Conocimiento contextual de un sitio/área específica | Flujos de trabajo complejos y multi-sistema |

---

## 6. Consideraciones de licenciamiento

- **Licencia Microsoft 365 Copilot:** Habilita ambas superficies en su capacidad completa. El uso de agentes en SharePoint, Teams y Copilot Chat con grounding en datos del tenant no consume créditos adicionales de Copilot Studio.
- **Sin licencia M365 Copilot + Pay-as-you-go:** Los agentes que acceden a SharePoint o Graph Connectors se facturan por consumo en **Copilot Credits** (moneda unificada desde septiembre de 2025).
- **SharePoint Advanced Management (SAM):** Incluido con la licencia M365 Copilot desde principios de 2025. Facilita la auditoría y gobernanza de permisos, crítica para una adopción segura de agentes.

---

## 7. Recomendaciones de adopción

**Usar SharePoint Agents cuando:**
- El caso de uso es contextual a un sitio o área específica.
- Los usuarios necesitan consultar documentación sin salir de su flujo de trabajo en SharePoint.
- Se requiere una implementación rápida con bajo esfuerzo técnico.

**Usar Agentes en Copilot Chat cuando:**
- El agente necesita integrar múltiples fuentes de datos o sistemas externos.
- Se requiere automatización y ejecución de acciones (crear registros, enviar emails, disparar flujos).
- El alcance del agente es transversal a la organización, no acotado a un sitio.

**En ambos casos:**
- Auditar y revisar los permisos de SharePoint **antes** de activar los agentes. Copilot puede exponer rápidamente información que estaba técnicamente accesible pero no era fácilmente descubrible.
- Configurar Sensitivity Labels en Microsoft Purview para proteger documentos sensibles.
- Establecer políticas de administración de agentes en el Copilot Control System desde el primer día.

---

*Fuentes: Microsoft Learn, Microsoft Support, Microsoft Purview Documentation — Mayo 2026*
