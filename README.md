# <h1 align="center">**`Estudio de Flujos Migratorios en América.`**</h1>

<p align='center'>
<img src ="https://www.immigration-residency.com/wp-content/uploads/2021/09/global-immigration-map.jpg" width="600">
<p>


# **`Sprint 1`**

## **Contexto**

En los últimos años han habido grandes flujos migratorios entre los distintos países de América. Éstos se han dado por diversas razones, como pueden ser la estabilidad, la educación y las oportunidades de empleo de un país.

### *Cliente*
La `Organización del Desarrollo y Bienestar` es una ONG que busca contribuir en la en la mejora de los ingresos de familias más vulnerables para que logren tener una mejor calidad de vida en el continente Americano.

## **Objetivo**

Analizar el flujo migratorio de las personas con el fin de proveer información a la ONG, para que conozca las razónes principales de la migración y así poder realizar acciones que ataquen algunas de las problemáticas que las generan, mejorando así la calidad de vida de las personas.

## **Alcance**

Dado que la ONG actua principalmente en América se van a trabajar con datos de paises ese continente. Además se piensa estudiar desde el año `1990` porque es a partir de esas fechas que hay mayor cantidad de datos como para hacer un análisis mas detallado. 

La calidad de vida se podría cuantificar con algunos indicadores como: ``Esperanza de vida al nacer??``, el año promedio escolar, desempleo e índice de desarrollo humano.

### *Fuera de alcance*

Como hay mucha emigración desde América Latina hacia Europa se podría agregar en el estudio los países europeos como destino para poder compararlos con los paises de América que podria brindar mas informacion sobre las causas de dicha migración.

## **Fuentes de datos**

Como fuente de datos principal se extrajeron datos del [Banco Mundial](https://datos.bancomundial.org/indicador), pero se complementó de otra fuente como [UNDP](https://hdr.undp.org/data-center/documentation-and-downloads) (Programa de Desarrollo de las Naciones Unidas).

| Fuente | Tipo Datos | Ultima Actualización |
| - |- | - |
| Banco Mundial | [Migración neta](https://datos.bancomundial.org/indicator/SM.POP.NETM?end=2017&start=1962) | 2022 |
| Banco Mundial | [Desempleo](https://datos.bancomundial.org/indicador/SL.UEM.TOTL.ZS?view=chart) | 2022 |
| Banco Mundial | [PBi per capita](https://datos.bancomundial.org/indicador/NY.GDP.PCAP.CD?view=chart) | 2022 |
| UNDP | [hdi](https://hdr.undp.org/data-center/documentation-and-downloads) | 2021 |
| UNDP | [Esperanza_vida](https://hdr.undp.org/data-center/documentation-and-downloads) | 2021 |
| UNDP | [Año_prom_esc](https://hdr.undp.org/data-center/documentation-and-downloads) | 2021 |
| UNDP | [PBI_per_cap_aj](https://hdr.undp.org/data-center/documentation-and-downloads) | 2021 |
| Our World in data | [pobreza](https://ourworldindata.org/poverty) | 2021 |

Dichos datos originales estan en la carpeta [datasets/datos_crudos](datasets/datos_crudos).

## **ETL y EDA Preliminar**

Luego con los datos de las diversas fuentes, se hicieron varias limpiezas y estudio de la calidad del dato. Adicionalmente se juntaron en un unico dataset con todas las variables relevantes para continuar el estudio y se exportaron a un archivo destino en [datasets/datos_procesados](datasets/datos_procesados).


*"Finalmente, como en Data es muy importante trabajar con datos de calidad, deberán incluir en su informe un análisis sobre los datos con los que van a trabajar (metadatos), detallandolos lo más posible: fuentes y confiabilidad de las mismas, qué representa cada columna de cada dataset, tipos de datos, método de adquisición, fecha de adquisición y ultima actualización, etc."*

### *Análisis*

`Migracion Neta, Positivo es Inmigración, Negativa Emigración.`

``Algun nombres y tipos de columnas a estudiar?``

``Poner algo?``

``Alguna grafica?``

### *Conclusiones*

``Poner algo``

Para un análisis mas detallado del todo este proceso se puede consultar el [EDA](EDA.ipynb).

## **KPIs utilizados**

### **KPI 1: Desempleo**

Debido a que una de las propuestas que tiene la ONG es la de realizar campaña de empleo en los paises mas vulnerables se puede utilizar un KPI que mida el porcentaje de desempleo y tenga como objetivo bajar 2 % en un año.

### **KPI 2: Escolaridad**

Otra forma con la que se quiere mejorar la calidad de vida es mejorando los niveles de escolaridad de la población para que a futuro logren tener mas oportunidades de empleo. Teniendo esto en cuenta se puede medir la variación de los años de escolaridad y poner como objetivo el aumento de 1 año por año.


### **KPI 3: **
...


### KPI 4: Pobreza
Buscamos reducir la pobreza y mejorar la calidad de vida en comunidades vulnerables. Este KPI mide la proporción de población que vive bajo el umbral de pobreza. Nuestra meta es disminuir esta proporción en un 5% en un año a través de estrategias efectivas. Aspiramos a crear un entorno más equitativo y con mayores oportunidades para todos.




## **Solución Propuesta**

Debajo se detalla la solución propuesta separando los distintos entregables en cada etapa del proyecto.

### *Sprint 1*

- Documentación de Contexto, Objetivo y Alcance del proyecto.
- Definición del Stack Tecnológico completo.
- Análisis Exploratorio de los Datos preliminar y definición de 4 KPI's a utilizar.

### *Sprint 2*

- Data Warehouse automatizado con Carga Inicial.
- Dashboard preliminar (MVP)
- Sistema preliminar de prediccion de razones de flujos migratorios (MVP)

### *Sprint 3*

- Dashboard interactivo con KPI's que ayuden a analizar e interpretar las razones de los flujos migratorios.
- Una Web App para poder acceder al modelo predictivo para detectar de antemano cambios en flujos migratorios, detectando en que países y que problemáticas asi de esta forma se podrían tomar acciones preventivas.

## **Implementación de Stack Tecnológico**

Para poder implementar la solución propuesta se propone utilizar el Stack Tecnológico detallado debajo.

- Data Sources
    - Archivos `.csv` de distintas organizaciónes como fuentes de datos relevantes.
- EDA en Python y Jupyter Notebook.
    - [Numpy](https://numpy.org/) y [Pandas](https://pandas.pydata.org/) para manejo de datos.
    - [Matplotlib](https://matplotlib.org/) y [Seaborn](https://seaborn.pydata.org/) para visualizaciones.
- Raw Data
    -  [GCP Cloud Storage](https://cloud.google.com/storage) para almacenar los datos crudos en la nuve de GCP.
- Data Warehouse
    - [GCP BigQuery](https://cloud.google.com/bigquery) para transformar los datos crudos en un Data Warehouse.
- Data Visualization and Dashboard
    - [Power BI](https://powerbi.microsoft.com/es-es/) para generación de Dashboards y visualizaciones tomando datos directamente de nuestro Data Warehouse.
- Virtual Machine
    - [GCP Compute Engine](https://cloud.google.com/compute) para poder alojar nuestro modelo de Machine Learning y dejar una API para producir las predicciones del modelo.
        - Machine Learing Model
            - [scikit-learn](https://scikit-learn.org/stable/)
        - API
            - [Fast API](https://fastapi.tiangolo.com/)
- Web App
    - [Streamlit](https://streamlit.io/) para crear nuestra aplicación Web y que el cliente pueda interactuar de una forma amigable con nuestro sistema de predicción.

<p align='center'>
<img src ="Stack_tecnologico.png" width="800">
<p>


## **Metodologías de trabajo y organización**
Utilizamos un acercamiento a metodologías ágiles, definiendo las tareas que precisabamos realizar en la semana para llegar al entregable pedido. Luego en las Daily meeting aprovechabamos para hacer una puesta a punto de lo realizado, hablar sobre que problemas nos habiamos enfrentado y con que tareas ibamos a continuar.


### **Distribución de tareas y roles**
| Nombre            | Rol           |
|-------------------|---------------|
| Marcelo Suarez    | Data Analyst  |
| Nehuen Gonzalez   | Data Analyst  |
| Thiago Gonzales   | Data Engineer |
| Sebastián Besio   | Data Engineer |


### **Diagrama de Gantt**

Estimación de tareas para llegar en tiempo y forma a la finalización del proyecto el 15/09/23 contemplando los dos hitos intermedios.

<p align='center'>
<img src ="Gantt.png" width="1000">
<p>
