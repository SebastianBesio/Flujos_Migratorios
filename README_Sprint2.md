# <h1 align="center">**`SPRINT 2`**</h1>

### **Objetivo del Sprint**

- Documentación general de los trabajos.
- Workflow detallando tecnologías
- Diccionario de datos
- ETL completo
- Pipeline ETL automatizado
- Pipelines para alimentar el DW Automatizado e Incremental
- Data Warehouse
- Diagrama ER detallado (tablas, PK, FK y tipo de dato)
- Análisis de datos de muestra
- MVP de Dashboard

## **Implementación de Stack Tecnológico**

Se utilizó el siguiente Stack Tecnológico para implementar el workflow deseado.

- Data Sources
    - [API](https://documents.worldbank.org/en/publication/documents-reports/api) del Banco Mundial
    - [Web Scraping](https://datosmacro.expansion.com/demografia/migracion/inmigracion/argentina?anio=1990#geo0) pagina con datos de inmigración para varios países y años.
    - Descarga automática de [CSV](https://hdr.undp.org/sites/default/files/2021-22_HDR/HDR21-22_Composite_indices_complete_time_series.csv) de la [UNDP](https://hdr.undp.org/data-center/documentation-and-downloads) sobre indicadores varios de distintos paises entre 1990 y 2021.

- Raw ETL
    - Google [Cloud Function](https://cloud.google.com/functions) en Python para realizar ETL de la fuente de datos hacia el Bucket.
    - [Pandas](https://pandas.pydata.org/) para manejo de datos.
    - [urllib](https://docs.python.org/3/library/urllib.html), [regex](https://docs.python.org/3/library/re.html) y [Beautiful Soup](https://pypi.org/project/beautifulsoup4/) para Web Scraping.
    - [google.cloud.storage](https://cloud.google.com/python/docs/reference/storage/latest) para almacenar en Buckets de GCP.

- Raw Data
    -  [GCP Cloud Storage](https://cloud.google.com/storage) para almacenar los datos crudos en un Bucket en la nube de GCP.

- ETL hacia BigQuery
    - Google [Cloud Function](https://cloud.google.com/functions) en Python para realizar ETL desde el Bucket hacia BigQuery.
    - [Pandas](https://pandas.pydata.org/) para manejo de datos.
    - [google.cloud.storage](https://cloud.google.com/python/docs/reference/storage/latest) para almacenar en Buckets de GCP.
    - [google.cloud.bigquery](https://cloud.google.com/bigquery/docs/reference/libraries) para comunicarse, crear tablas y almacenar en BigQuery de GCP.

- Dataset
    - [GCP BigQuery](https://cloud.google.com/bigquery) para transformar los datos crudos en tablas.
- Data Visualization and Dashboard
    - [Power BI](https://powerbi.microsoft.com/es-es/) para generación de Dashboards y visualizaciones tomando datos directamente de nuestro Dataset.
- Automatización
    - [GCP Pub/Sub](https://cloud.google.com/pubsub) para manejo de triggers para activar Cloud Functions.
    - [GCP Cloud Scheduler](https://cloud.google.com/scheduler) para crear tareas programadas que ejecute los triggers de las Cloud Functions de forma periódica.

<p align='center'>
<img src ="images/Stack_tecnologico_S2.png" width="800">
<p>


## **Diccionario de datos**

Como fuente de datos principa

| Fuente | Tipo Datos |
| - |- |
| Año | Año a los que corresponden los datos. |
| Migración neta | Diferencia entre la inmigración y la emigración. |
| Desempleo | Persona que busca empleo y pero no lo tiene. |
| PIB per cápita | Producto Interno Bruto por persona. |
| hdi | Indice de Desarrollo Humano. |
| Esperanza_vida | La esperanza de vida es la media de la cantidad de años que vive una determinada población. |
| Año_prom_esc | Número de años promedio de educación de una persona. |


## **Diagrama de Entidad-Relacion**

asdsa

<p align='center'>
<img src ="images/Diagrama_ER.png" width="800">
<p>







---
# BORRAR ABAJO?


## **ETL y EDA Preliminar**

Luego con los datos de las diversas fuentes, se hicieron varias limpiezas y estudio de la calidad del dato. Adicionalmente se juntaron en un único dataset con todas las variables relevantes para continuar el estudio y se exportaron a un archivo destino en [datos_procesados](datasets/datos_procesados).

### *Subtitulo*

Las variables a analizar en nuestro dataset son las siguientes:

| Fuente | Tipo Datos |
| - |- |
| Año | Año a los que corresponden los datos. |
| Migración neta | Diferencia entre la inmigración y la emigración. |
| Desempleo | Persona que busca empleo y pero no lo tiene. |
| PIB per cápita | Producto Interno Bruto por persona. |
| hdi | Indice de Desarrollo Humano. |
| Esperanza_vida | La esperanza de vida es la media de la cantidad de años que vive una determinada población. |
| Año_prom_esc | Número de años promedio de educación de una persona. |


Para evitar confusiones, recordemos que cuando la Migración Neta es
- **positiva**, significa que hay mas inmigración que emigración.
- **negativa**, significa que hay mas emigración que inmigración.


Del análisis se desprende por ejemplo que en varios paises hay una tendencia inversa entre el desempleo y el flujo migratorio.

<p align='center'>
<img src ="images/Migracion_vs_Desempleo.png" width="800">
<p>

Haciendo un poco mas amplio el análisis se puede observar la matriz de correlación (por ejemplo en este caso para Argentina) que el desempleo tiene una correlación inversa al flujo migratorio como se explicó anteriormente. Pero también se puede ver que otros indicadores como son el HDI, promedio años de escolarización y Esperanza de vida tienen una correlación positiva con respecto a la migración.

<p align='center'>
<img src ="images/Matriz_Correlacion_Ejemplo.png" width="500">
<p>


### *Conclusiones*

- En general el desempleo y la migración neta tienen una buena correlación. Esto sería razonable ya que cuando hay menos empleo es mas probable de que la gente salga a buscar nuevas oportunidades en otros países.

- Hay algunas excepciones como el caso de los Estados Unidos es un país que recibe tanta inmigración que por más que haya más desempleo su migración neta no se ve afectada.

- Tambien resulta interesante mencionar el caso de Venezuela, que a partir del año 2015, posiblemente consecuencia de la crisis economica a que apareció en la primera presidencia de Maduro, tuvo un gran crecimiento en la emigración de su país. Esto impactó en Varios países vecinos como el caso de Colombia que tuvieron un aumento enla inmigración a partir de ese periodo.

- Se podrian utilizar indicadores como el HDI, Desempleo y promedio años de escolarización como explicaciones de ciertos flujos migratorios.

- Es importante remarcar que, siendo que tenemos datos de Migración Neta y no de inmigración y emigración, a veces resulta dificil detectar si fue que no hubo cambios en la migración o si en realidad hubo pero fue un cambio balanceado entre ambos valores que no se logra interpretar al analizar la migración neta.

Para un análisis más detallado de todo este proceso se puede consultar el [EDA](EDA.ipynb).

## **KPIs utilizados**

### **KPI 1: Desempleo**

Debido a que una de las propuestas que tiene la ONG es la de realizar campaña de empleo en los países mas vulnerables se puede utilizar un KPI que mida el porcentaje de desempleo y tenga como objetivo bajar 2 % en un año.

### **KPI 2: Escolaridad**

Otra forma con la que se quiere mejorar la calidad de vida es mejorando los niveles de escolaridad de la población para que a futuro logren tener más oportunidades de empleo. Teniendo esto en cuenta se puede medir la variación de los años de escolaridad y poner como objetivo el aumento de 1 año por año.


### KPI 3: Pobreza
Buscamos reducir la pobreza y mejorar la calidad de vida en comunidades vulnerables. Este KPI mide la proporción de población que vive bajo el umbral de pobreza. Nuestra meta es disminuir esta proporción en un 5% en un año a través de estrategias efectivas. Aspiramos a crear un entorno más equitativo y con mayores oportunidades para todos.


### KPI 4: HDI
El HDI refleja la salud, educación y bienestar de la población. Se relaciona con nuestro propósito de mejorar la calidad de vida en comunidades vulnerables. Al enlazar la atención médica, formación, reducción de desempleo y pobreza, este KPI busca aumentar el HDI en un 3% en un año.


## **Solución Propuesta**

Debajo se detalla la solución propuesta separando los distintos entregables en cada etapa del proyecto.

### *Sprint 1*

- Documentación de Contexto, Objetivo y Alcance del proyecto.
- Definición del Stack Tecnológico completo.
- Análisis Exploratorio de los Datos preliminar y definición de 4 KPI's a utilizar.

### *Sprint 2*

- Data Warehouse automatizado con Carga Inicial.
- Dashboard preliminar (MVP)
- Sistema preliminar de predicción de flujos migratorios (MVP)

### *Sprint 3*

- Dashboard interactivo con KPI's que ayuden a analizar e interpretar las razones de los flujos migratorios.
- Una Web App para poder acceder al modelo predictivo para detectar de antemano cambios en flujos migratorios, detectando en qué países y que problemáticas así de esta forma se podrían tomar acciones preventivas.


## **Metodologías de trabajo y organización**
Utilizamos un acercamiento a metodologías ágiles, definiendo las tareas que precisamos realizar en la semana para llegar al entregable pedido. Luego en las Daily meeting aprovechamos para hacer una puesta a punto de lo realizado, hablar sobre que problemas nos habíamos enfrentado y con que tareas ibamos a continuar.


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
<img src ="images/Gantt.png" width="1000">
<p>
