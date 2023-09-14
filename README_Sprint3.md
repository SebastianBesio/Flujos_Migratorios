# <h1 align="center">**`SPRINT 3`**</h1>

### **Objetivo del Sprint**

- Storytelling
- Producto Dashboard y Reportes
- Modelado Predicción Machine Learning

# **Producto entregable**

El producto final es un dashboard y reportes interactivos implementado en Power BI.

Debajo les detallaremos las caracteristicas principales del producto y algunos ejemplos de análisis realizados para que vean cómo podrían utilizarlo para sus propios análisis.


## **DASHBOARD**

``Breve descripcion gral?``


<p align='center'>
<img src ="images/Dashboard_S3.png" width="800">
<p>

``KPIs de nuevo?``

## **Comparaciones**

<p align='center'>
<img src ="images/Comparaciones_S3.png" width="800">
<p>

Donde se pueden ver comparaciones para ver relaciones entre varios indicadores. Como por ejemplo el desempleo y la migración neta.

``Desempleo vs mig neta?``

## **Emigración**

En este reporte se pueden elegir el pais de origen de la emigración y los paises destino para estudiar los destinos de flujo migratorio. Se observa una grafica que muestra el aumento de los emigrantes de ese pais hacia los destinos elegidos.

Ademas debajo a la izqueirda se puede ver la cantidad total de emigrantes que tiene el país de origen como para poder ver la diferencia en la imigración.

<p align='center'>
<img src ="images/Emigracion_S3.png" width="800">
<p>

**Análisis ejemplo**

``Venezuela 2015?``
``Cuba?``
``Otro?``

## **Inmigración**

``ALGO?``

**EE.UU.**

``ALGO?``

<p align='center'>
<img src ="images/Inmigracion_EEUU_S3.png" width="800">
<p>

**Argentina**

``ALGO?``

<p align='center'>
<img src ="images/Inmigracion_Arg_S3.png" width="800">
<p>

``Comentar que le falta mejora para hacerlo interactivo????``


## **Sistema Predicción**

**Forecasting**

El Forecasting consiste en la estimación y el análisis del valor de una variable futura mediante algoritmos.

**Prophet**

Es una herramienta de codigo abierto diseñada por Meta para predecir valores futuros basados en datos historicos (Forecasting).
<p align='center'>
<img src ="images/Prediccion_S3.png" width="800">
<p>


Algo asi en español?

[Introducción Prophet](https://facebook.github.io/prophet/)

[Documentación Prophet](https://facebook.github.io/prophet/docs/quick_start.html)

`COMO FUNCIONA?`

**Predicción de Migración Neta**

El modelo de predicción se agregó a una Cloud Function, en donde toma la migración neta y pronostica su valor para los proximos 5 años futuros. No se hace para mas años ya que mientras mas lejana la predicción mas imprecisa es.

Esos datos se agregaron en el campo migracion_neta_pred dentro de la tabla de migracion de BigQuery para luego poder consultarlos directamente desde Power BI.

<p align='center'>
<img src ="images/Prediccion_S3.png" width="800">
<p>
