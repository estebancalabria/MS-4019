# Programa

* Orientado al uso de Agentes.
  * Modulo 1: Introducion. Agentes. Governance.
  *  Modulo 2: Agentes Precompilados
  *  Modulo 3: Construir agentes
    * Buenas Practicas
    * Intrucciones
    * Origenes de Conocimiento
    * Agent Builder
  *  Modulo 4: Compoartir agentes
    *  Caso de exito

---

# Modulo 1

* Agente de Excel

  ```
  Quiero las columnas nombre, apellido, fecha de nacimiento, profesion, sueldo. Quiero que valide que fecha de naciemiento sea de tipo fecha en formato de fecha que usamos en Argentina. Que el sueldo sea una columna de dinero en formato que usamos en Argentina.
  ```

> [!NOTE] FOCO en Seguridad


# Modulo 2

## Agente Analista
  * https://matplotlib.org/
  * 

* Utilice una planilla que genere con copilot en Excel

* Casos de Uso 
###  Para generar Graficos

 ```
 Quiero que uses matplotlib para generarme un diagrama de pie donde se vean la el promedio de sueldo por profesion
 ```

### Para generar Dashboards

```
Quiero un dashboard interactivo
```

### Hacer predicciones

```
Me llamo Esteban Calabria. Naci el 20/09/1980. Trabajo en IT. Podes en base a los datos que conoces predecir mi sueldo? Queiiro un valor estimado.
```

## Agente Prompt Coach

* Lo Instale desde la galeria de agentes
* Use el siguiente Prompt
```
Redactame un prompt paa el agente investigador para que me genere un analisis de mercado sobre el impacto del precio del petroleo teniendo en cuenta la situacion geopolitica y unos key points estrategicos de que puedo hacer desde una empresa como Chevron para tomar decisiones.
```
* Me Genero el siguiente prompt para copiar y pegar
```
Actúa como un analista senior de mercados energéticos con especialización en petróleo, geopolítica internacional y estrategia corporativa para empresas Oil & Gas integradas.

OBJETIVO  
Elaborar un análisis de mercado exhaustivo sobre el impacto del precio del petróleo, considerando el contexto geopolítico actual, y derivar implicaciones estratégicas claras para la toma de decisiones desde una empresa como Chevron.

CONTEXTO  
Chevron es una compañía energética integrada con operaciones upstream, midstream y downstream, presencia global y exposición tanto a riesgos geopolíticos como a oportunidades derivadas de la volatilidad del crudo. El análisis debe ser relevante para la alta dirección (estrategia, finanzas, inversiones y gestión de riesgos).

ALCANCE DEL ANÁLISIS  
1. Análisis del precio del petróleo  
   - Evolución reciente del Brent y WTI.  
   - Principales drivers actuales del precio (oferta, demanda, inventarios, política monetaria, OPEP+).  
   - Escenarios de corto y medio plazo (base, alcista y bajista).

2. Situación geopolítica  
   - Conflictos y tensiones relevantes (por ejemplo: Oriente Medio, Rusia-Ucrania, relaciones EE. UU.–China).  
   - Impacto de sanciones, riesgos de interrupción de suministro y decisiones de países productores.  
   - Implicaciones para flujos comerciales, precios y volatilidad.

3. Impacto específico en Chevron  
   - Efectos sobre upstream (capex, rentabilidad de proyectos, producción).  
   - Implicaciones para downstream y trading.  
   - Riesgos financieros, operativos y reputacionales.

4. Key Strategic Points – ¿Qué puede hacer Chevron?  
   Proponer recomendaciones estratégicas claras y accionables, por ejemplo:
   - Decisiones de inversión y priorización de proyectos.  
   - Gestión del riesgo de precios (hedging, diversificación).  
   - Ajustes en cartera geográfica.  
   - Oportunidades en M&A o partnerships.  
   - Consideraciones sobre transición energética y posicionamiento a largo plazo.

FORMATO Y EXPECTATIVAS  
- Estructura clara con encabezados.  
- Uso de bullets para recomendaciones estratégicas.  
- Lenguaje ejecutivo, preciso y orientado a decisión.  
- Incluir conclusiones clave y un resumen ejecutivo final.  
- Basar el análisis en datos recientes y fuentes fiables (mercados energéticos y análisis geopolítico).

Enfócate en aportar insights estratégicos, no solo descripción de hechos.
```

## Agente Researcher/Investigador

* Hacer una busqueda masiva en internet (100+ sitiios dependiendo el tema)
* Estructura la respuesta utilizando "Chain of thoughts" (planica)
  * Divide el problema en una serie de pasos
* Todo lo que el agente analista menciona lo cita
  * "No utilices datos que sean de tu conociminto sino que todo tiene que estar citado"

## Mencion

* Idea Coach
* Writting Coach
* Carrer Coach

---

# MOdilo 3 : Creacion de Agentes
