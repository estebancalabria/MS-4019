# 🧪 Laboratorio 1 — Creación del Primer Agente en SharePoint

## 🎯 Objetivo

Crear un agente básico en SharePoint capaz de responder preguntas utilizando documentos empresariales almacenados en una biblioteca documental.

---

# 📋 Requisitos Previos

Antes de comenzar, asegúrese de tener:

* Una cuenta Microsoft 365.
* Acceso a SharePoint Online.
* Licencia Microsoft 365 Copilot habilitada.
* Permisos para crear sitios SharePoint o acceso a un sitio existente.

---

# ⏱️ Duración Estimada

30 minutos

---

# 🧠 Escenario

El departamento de Recursos Humanos desea crear un agente capaz de responder preguntas frecuentes sobre:

* Vacaciones
* Trabajo remoto
* Beneficios
* Políticas internas

Toda esta información estará almacenada en SharePoint.

---

# 🛠️ Parte 1 — Crear el Sitio de SharePoint

## Paso 1 — Abrir SharePoint

1. Abra Microsoft 365.
2. Ingrese a SharePoint.

Debería visualizar una pantalla similar a la siguiente:

* Menú lateral izquierdo
* Sección “Descubrir”
* Sitios recientes
* Barra de búsqueda superior

---

## Paso 2 — Crear un Sitio Nuevo

> ⚠️ La ubicación de esta opción puede variar dependiendo del tenant, idioma o permisos del usuario.

En este laboratorio utilizaremos la navegación observada en el tenant de prueba.

1. En el menú lateral izquierdo, haga clic en:

```text id="j9r7o1"
Compilar
```

2. Seleccione:

```text id="v1f0bn"
Sitios
```

3. Haga clic en:

```text id="2r3s5r"
Sitio de grupo
```

---

## Paso 3 — Configurar el Sitio

Complete los siguientes campos:

| Campo            | Valor                             |
| ---------------- | --------------------------------- |
| Nombre del sitio | RRHH-Lab                          |
| Descripción      | Sitio para laboratorio de agentes |
| Privacidad       | Privado                           |

Luego:

1. Haga clic en **Siguiente**.
2. Haga clic en **Finalizar**.

Espere unos segundos mientras SharePoint crea el sitio.

---

# 🛠️ Parte 2 — Crear la Biblioteca Documental

## Paso 4 — Abrir el Sitio

Una vez creado el sitio:

1. Ingrese al sitio **RRHH-Lab**.

---

## Paso 5 — Crear Biblioteca

1. En la parte superior del sitio, haga clic en:

```text id="jjylw8"
Nuevo
```

2. Seleccione:

```text id="q7ivhs"
Biblioteca de documentos
```

3. Configure:

| Campo  | Valor              |
| ------ | ------------------ |
| Nombre | Documentacion-RRHH |

4. Haga clic en:

```text id="7l03fu"
Crear
```

---

# 🛠️ Parte 3 — Crear los Documentos

## Paso 6 — Crear Documento de Vacaciones

1. Ingrese a la biblioteca:

```text id="l5kkbe"
Documentacion-RRHH
```

2. Haga clic en:

```text id="mzt7cs"
Nuevo → Documento Word
```

3. Asigne el siguiente nombre:

```text id="8hj0a7"
Politica-Vacaciones.docx
```

4. Pegue el siguiente contenido:

```text id="9pdy2v"
Política de Vacaciones

Los empleados tienen derecho a 14 días de vacaciones anuales.

Las vacaciones deben solicitarse con al menos 15 días de anticipación.

Las solicitudes se realizan mediante Microsoft Teams o correo electrónico al supervisor.
```

5. Cierre el documento.

---

## Paso 7 — Crear Documento de Trabajo Remoto

1. Haga clic nuevamente en:

```text id="4i1flq"
Nuevo → Documento Word
```

2. Nombre del archivo:

```text id="40plku"
Politica-HomeOffice.docx
```

3. Pegue:

```text id="0j2u98"
Política de Trabajo Remoto

Los empleados pueden trabajar de forma remota hasta 3 días por semana.

Es obligatorio mantener disponibilidad en Teams entre las 9 AM y las 18 PM.

El equipamiento es provisto por la empresa.
```

4. Cierre el documento.

---

## Paso 8 — Crear Documento de Beneficios

1. Cree un nuevo documento Word.

2. Nombre:

```text id="obc6wb"
Beneficios.docx
```

3. Pegue:

```text id="yn7npa"
Beneficios Corporativos

La empresa ofrece:

- Cobertura médica premium
- Plataforma de capacitaciones
- Bono anual por desempeño
- Día libre de cumpleaños
```

4. Cierre el documento.

---

# 🛠️ Parte 4 — Crear el Agente

## Paso 9 — Iniciar la Creación del Agente

Dentro de la biblioteca:

```text id="wqcbff"
Documentacion-RRHH
```

1. Haga clic en:

```text id="dfk4o0"
Nuevo
```

2. Seleccione:

```text id="0p8s91"
Agente
```

> ⚠️ Si la opción “Agente” no aparece:
>
> * Verifique que Microsoft 365 Copilot esté habilitado.
> * Verifique permisos de edición sobre el sitio.
> * Algunas organizaciones restringen la creación de agentes.

---

## Paso 10 — Configurar el Agente

Complete:

| Campo       | Valor                                  |
| ----------- | -------------------------------------- |
| Nombre      | Agente-RRHH                            |
| Descripción | Agente para consultas internas de RRHH |

---

## Paso 11 — Seleccionar Fuentes de Información

Seleccione los siguientes documentos:

* Politica-Vacaciones.docx
* Politica-HomeOffice.docx
* Beneficios.docx

Luego haga clic en:

```text id="q3jz5d"
Crear
```

Espere mientras SharePoint genera el agente.

---

# 🛠️ Parte 5 — Probar el Agente

## Paso 12 — Abrir el Agente

1. Abra:

```text id="t1qvtt"
Agente-RRHH
```

Se abrirá la interfaz de chat.

---

## Paso 13 — Realizar Consultas

Copie y pegue las siguientes preguntas.

---

### Consulta 1

```text id="f50m2t"
¿Cuántos días de vacaciones tienen los empleados?
```

---

### Consulta 2

```text id="m43v4s"
¿Cuántos días de trabajo remoto están permitidos?
```

---

### Consulta 3

```text id="w26vsk"
¿Qué beneficios ofrece la empresa?
```

---

### Consulta 4

```text id="l4g3mj"
¿Cómo se solicitan las vacaciones?
```

---

# 🛠️ Parte 6 — Compartir el Agente

## Paso 14 — Compartir el Agente

1. Dentro del agente, haga clic en:

```text id="u2x5wk"
Compartir
```

2. Agregue otro usuario Microsoft 365.
3. Haga clic en:

```text id="pt0gdb"
Enviar
```

---

# 🛠️ Parte 7 — Validar Acceso

## Paso 15 — Verificar Funcionamiento

Solicite al usuario compartido que:

1. Abra el agente.
2. Realice consultas.
3. Verifique el acceso a la información.

---

# ✅ Resultado Esperado

Al finalizar este laboratorio, el alumno habrá:

* Creado un sitio SharePoint.
* Creado una biblioteca documental.
* Generado documentación empresarial.
* Creado un agente sin escribir código.
* Realizado consultas en lenguaje natural.
* Compartido el agente con otros usuarios.

---

# 🎯 Conceptos Aprendidos

* SharePoint Agents
* Microsoft 365 Copilot
* Grounding documental
* IA contextual
* Recuperación de información
* Permisos y acceso
* Productividad empresarial

---

# 🧹 Limpieza (Opcional)

Para eliminar el laboratorio:

1. Elimine el agente.
2. Elimine la biblioteca documental.
3. Elimine el sitio SharePoint.
