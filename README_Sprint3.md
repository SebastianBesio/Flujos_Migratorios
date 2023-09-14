# <h1 align="center">**`SPRINT 3`**</h1>

### **Objetivo del Sprint**

- Storytelling
- Producto Dashboard y Reportes
- Modelado Predicción Machine Learning

# **Producto entregable**

El producto final es un dashboard y reportes interactivos implementado en Power BI.

Debajo les detallaremos las características principales del producto y algunos ejemplos de análisis realizados para que vean cómo podrían utilizarlo para sus propios análisis.


## **DASHBOARD**

A la izquierda se encuentran 4 KPIs luego se puede ver varias gráficas para ver las tendencias de las distintas variables a lo largo de los años, pudindo filtrar por años y paises.


<p align='center'>
<img src ="images/Dashboard_S3.png" width="800">
<p>

### **KPIs**

- KPI 1: Reducción del Desempleo
- KPI 2: Mejora Escolaridad
- KPI 3: Esperanza de vida
- KPI 4: HDI

Detallados en [Sprint 2](README_Sprint2.md)

## **Comparaciones**

Donde se pueden ver comparaciones para ver relaciones entre varios indicadores. Como por ejemplo el desempleo y la migración neta.

<p align='center'>
<img src ="images/Comparaciones_S3.png" width="800">
<p>

## **Emigración**

En este reporte se pueden elegir el pais de origen de la emigración y los paises para estudiar los destinos de flujo migratorio. Se observa una gráfica que muestra el aumento de los emigrantes de ese pais hacia los destinos elegidos.

Además debajo a la izqueirda se puede ver la cantidad total de emigrantes que tiene el país de origen como para poder ver la diferencia en la imigración.

<p align='center'>
<img src ="images/Emigracion_S3.png" width="800">
<p>

**Análisis**

En el caso de Venezuela se puede observar la gran emigración a partir del año 2015, como consecuencia de la crisis económica ocurrida durante la primera presidencia de Maduro. La crisis económica y humanitaria en Venezuela fue tal que ha llevado a una de las crisis migratorias más grandes de América Latina. Como podemos observar millones de venezolanos han abandonado el país en busca de refugio y oportunidades en países vecinos.

``Cuba?``
``Otro?``

## **Inmigración**

La inmigración es un fenómeno global y ha sido un tema importante en las discusiones políticas y sociales en todo el mundo. Es un proceso mediante el cual las personas se mudan de un país o región a otro con el objetivo de establecerse y vivir en el lugar de destino de manera permanente o temporal. A modo de ejemplo podemos mencionar el caso de Estados Unidos y el de Argentina.

**EE.UU.**

La disminución en la emigración de México a los Estados Unidos a partir de 2010 puede atribuirse a una combinación de factores económicos, demográficos y políticos, las razones claves fueron:  
1. Cambios en la economía
2. Crisis económicas en los Estados Unidos
3. Mayor control fronterizo
4. Mayor inversión en educación


<p align='center'>
<img src ="images/Inmigracion_EEUU_S3.png" width="800">
<p>

**Argentina**

La reducción de la inmigración en Argentina en la década de 1990 se produjo porque: esa década estuvo marcada por una serie de reformas económicas, como la Convertibilidad y la privatización de empresas, que inicialmente generaron estabilidad, pero luego dieron paso a crisis económicas y sociales, que culminaron en la crisis financiera y el colapso del gobierno a principios de los años 2000. 
Luego la inmigración aumentó hasta la actualidad y la razón principal fue por la creación en el año 2003 de la Ley Migraciones 25.871, que regulariza la situación documentaria de cientos de miles de migrantes, especialmente a personas que provienen de países del MERCOSUR.


<p align='center'>
<img src ="images/Inmigracion_Arg_S3.png" width="800">
<p>

## **Sistema Predicción**

**Forecasting**

El Forecasting consiste en la estimación y el análisis del valor de una variable futura mediante algoritmos.

**Prophet**

Es una herramienta de codigo abierto diseñada por Meta en 2017 para predecir valores futuros basados en datos historicos (Forecasting).

[Introducción Prophet](https://facebook.github.io/prophet/)

[Documentación Prophet](https://facebook.github.io/prophet/docs/quick_start.html)

`COMO FUNCIONA?`

Prophet divide los datos en tres partes principales:

Tendencia: Es una línea recta que muestra la dirección general en la que van los datos con el tiempo, si están aumentando o disminuyendo.

Estacionalidad: Son los patrones repetitivos que ocurren cada cierto tiempo, como las ventas que aumentan durante las festividades.

Efectos vacacionales: Son eventos especiales que pueden afectar los datos, como un aumento en las ventas durante un período de descuento. (No se incluyo)

Luego, Prophet utiliza fórmulas matemáticas (Harvey Peters 1990) para predecir cómo se verán los datos en el futuro. Ayuda a las empresas a tomar decisiones basadas en estas predicciones.

**Predicción de Migración Neta**

El modelo de predicción se agregó a una Cloud Function, en donde toma la migración neta y pronostica su valor para los proximos 5 años futuros. No se hace para mas años ya que mientras mas lejana la predicción mas imprecisa es.

Esos datos se agregaron en el campo migracion_neta_pred dentro de la tabla de migracion de BigQuery para luego poder consultarlos directamente desde Power BI.

<p align='center'>
<img src ="images/Prediccion_S3.png" width="800">
<p>
