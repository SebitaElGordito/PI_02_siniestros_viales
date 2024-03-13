![Pandas](https://img.shields.io/badge/-Pandas-333333?style=flat&logo=pandas)
![Numpy](https://img.shields.io/badge/-Numpy-333333?style=flat&logo=numpy)
![Matplotlib](https://img.shields.io/badge/-Matplotlib-333333?style=flat&logo=matplotlib)
![Seaborn](https://img.shields.io/badge/-Seaborn-333333?style=flat&logo=seaborn)


<br>

# :construction: PI 02 siniestros viales :construction:

<br>

<p align="center">
<img src="https://github.com/SebitaElGordito/PI_02_siniestros_viales/blob/main/Images/imagen_dashboard.jpeg?raw=true" alt="banner siniestros viales" width="900" height="450">

<br>

## Índice

* [Contexto](#hammer-contexto)

* [Datos](#memo-datos)

* [ETL](#etl)

* [Feature engineering](#feature-engineering)

* [EDA](#bar_chart-eda)

* [Modelo de Recomendación](#robot-modelo-de-recomendación)

* [Desarrollo de API](#desarrollo-de-api)

* [Deployment](#deployment)

* [Video](#video)

<br>

## :hammer: Contexto

La ciudad de Buenos Aires nos propone como analista de datos, abordar la problemática de los siniestros viales que concluyen con fatalidaddes.

La ciudad de Buenos Aires, al igual que muchas capitales a nivel mundial, se encuentra confrontando una importante problemática relacionada con los siniestros viales. Dichos incidentes constituyen una preocupación prioritaria para las autoridades locales, quienes han implementado diversas estrategias con el objetivo de mitigar su incidencia. Entre estas iniciativas, se destaca la recopilación sistemática de datos generados por los siniestros, proporcionando así una oportunidad invaluable para llevar a cabo un análisis exhaustivo y obtener conclusiones significativas.

Argentina ostenta uno de los índices más altos de mortalidad producida por siniestros de tránsito y se calcula que 20 personas mueren por día, casi 7.000 fallecidos por año, y más de 120.000 heridos anuales de distinto grado, de acuerdo a un relevamiento de Luchemos por la Vida.

<br>

## :memo: Datos

Se pone a disposición un dataset sobre homicidios en siniestros viales acaecidos en la Ciudad de Buenos Aires durante el periodo 2016-2021.

Se espera como productos finales un reporte de las tareas realizadas, metodologías adoptadas y principales conclusiones y la presentación de un dashboard interactivo que facilite la interpretación de la información y si análisis.

Actualmente, según el censo poblacional realizado en el año 2022, la población de CABA es de 3,070,612 de habitantes en una superficie de 200 km2, lo que implica una densidad de aproximadamente 15,603 hab/km2 [(Fuente)](https://www.argentina.gob.ar/caba#:~:text=Poblaci%C3%B3n%3A%203.120.612%20habitantes%20(Censo%202022)). Sumado a esto, el Julio de 2023 se registraron 12,437,735 de vehículos transitando por los peajes de las autopistas de acceso a CABA [(Fuente)](https://www.estadisticaciudad.gob.ar/eyc/?p=41995). Por lo que la prevención de siniestros viales y la implementación de políticas efectivas son esenciales para abordar este problema de manera adecuada.

Para este proyecto se trabajó con la **Bases de Víctimas Fatales en Siniestros Viales** que se encuentra en formato de Excel y contiene dos pestañas de datos:

* **HECHOS**: que contiene una fila de hecho con id único y las variables temporales, espaciales y participantes asociadas al mismo.
* **VICTIMAS**: contiene una fila por cada víctima de los hechos y las variables edad, sexo y modo de desplazamiento asociadas a cada víctima. Se vincula a los HECHOS mediante el id del hecho.

<br>

## Tecnologías utilizadas

Para la elaboración de este proyecto se utilizó Python y Pandas para los procesos de extracción, transformación y carga de los datos, como así también para el análisis exploratorio de los datos. En el siguiente apartado se describen los resultados del análisis.

Finalmente, para la construcción de un dashboard interactivo se utiliza Power BI.

<p align="center">
<img src="https://github.com/SebitaElGordito/PI_02_siniestros_viales/blob/main/Images/Dashboard.jpeg?raw=true" alt="banner siniestros viales" width="800" height="400">

<br>

## ETL

Extracción de Datos

En primer lugar, se realizó un proceso de extracción, transformación y carga de los datos (ETL), tanto de "HECHOS" como "VÍCTIMAS", donde se estandarizaron nombres de las variables, se analizaron nulos y duplicados de los registros, se eliminaron columnas redundantes o con muchos valores faltantes, entre otras tareas. Una vez finalizado este proceso para los dos conjuntos de datos de "Homicidios" se procedió a unir los dos conjuntos en uno solo denominado `df_homicidios`.

* Carga de Datos
Los datos transformados y limpios se utilizaron para realizar el EDA pertinente, y el posterior análisis mediante un dashboard de power BI.

<br>

## :bar_chart: EDA

Se utilizaron herramientas como Python, Pandas y Matplotlib para explorar los datos, generando estadísticas descriptivas, gráficos de tendencias y correlaciones.

Localización y Tiempo de los Siniestros: Se observó una mayor incidencia de siniestros en ciertas comunas y horarios, destacándose las primeras horas de la mañana y las avenidas principales.

* Perfil de las Víctimas: La mayoría de las víctimas eran hombres jóvenes, sugiriendo la necesidad de campañas de concienciación dirigidas a este grupo.

* Tipo de Vehículo Involucrado: Los automóviles y motocicletas estuvieron involucrados en la mayoría de los siniestros, lo que indica la necesidad de regulaciones específicas para estos vehículos.

* Relación entre Condiciones del Siniestro y Fatalidades: Se detectó un aumento en la tasa de fatalidades en siniestros nocturnos y en condiciones de baja visibilidad.

<br>

## KPI

Se plantearon tres objetivos en relación a la disminución de la cantidad de víctimas fatales de los siniestros viales, desde los cuales se proponen tres indicadores de rendimiento clave o KPI.

* *Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos seis meses, en CABA, en comparación con la tasa de homicidios en siniestros viales del semestre anterior*

    Las tasas de mortalidad relacionadas con siniestros viales suelen ser un indicador crítico de la seguridad vial en una región. Se define como **Tasa de homicidios en siniestros viales** al número de víctimas fatales en accidentes de tránsito por cada 100,000 habitantes en un área geográfica durante un período de tiempo específico, en este caso se toman 6 meses.

    En este caso, para el año 2021, la *Tasa de homicidios en siniestros viales* fue de 1.77 lo que significa que, durante los primeros 6 meses del año 2021, hubo aproximadamente 1.77 homicidios en accidentes de tránsito por cada 100,000 habitantes. Ahora, el objetivo planteado es reducir esta tasa para el siguiente semestre de 2021 en un 10%, esto es **1.60**. Cuando se calcula el KPI para este período se obtiene que la *Tasa de homicidios en siniestros viales* fue de **1.35**, lo que significa que para el segundo semestre de 2021 se cumple con el objetivo propuesto.

* *Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año, en CABA, respecto al año anterior*

    Como se vio en el análisis exploratorio, el 42% de las víctimas mortales se transportaban en moto al momento del hecho, por lo que se consideró importante proponer el monitoreo de la cantidad de accidentes mortales en este tipo de conductor. Para ello se define a la **Cantidad de accidentes mortales de motociclistas** como el número absoluto de accidentes fatales en los que estuvieron involucradas víctimas que viajaban en moto en un determinado periodo temporal.

    Para este caso, se toma como año actual al año 2021 y como año anterior al año 2020. En primer lugar, se calculó la *Cantidad de accidentes mortales de motociclistas* para el año 2020, el cual resultó de -44.00, de esta manera el objetivo a cumplir es de **-40.92** (es decir, la reducción del 7% de la cantidad de accidentes para 2020). El calcular la *Cantidad de accidentes mortales de motociclistas* para el año 2021 resultó de **64.29** lo que significa que aumentó un 64% la cantidad de muertes de conductores de motociclistas respecto del 2021.

* *Reducir en un 10% la tasa de homicidios de peaton respecto del año anterior.

    Como se vio en el análisis exploratorio, el 35% de las víctimas mortales eran peatones, por lo que se consideró importante proponer el monitoreo de la cantidad de accidentes mortales en peatones. Para ello se define a la **Cantidad de accidentes mortales de peatones** como el número absoluto de accidentes fatales en los que estuvieron involucradas víctimas que se trasladaban a pie al momento del accidente.

    Para este caso, se toma como año actual al año 2021 y como año anterior al año 2020. En primer lugar, se calculó la *Cantidad de accidentes mortales de peatones* para el año 2020, el cual resultó de (es decir, la reducción del 10% de la cantidad de accidentes para 2020). El calcular la *Cantidad de accidentes mortales de peatones* para el año 2021 resultó de **64.29** lo que significa que aumentó un 64% la cantidad de muertes de conductores de motociclistas respecto del 2021.


<br>

## Conclusiones
La aplicación de técnicas de ciencia de datos ha permitido identificar áreas clave para mejorar la seguridad vial en Buenos Aires. La integración del proceso ETL y EDA ha demostrado ser fundamental para una comprensión profunda de los siniestros viales. Las conclusiones obtenidas son de gran valor para informar políticas públicas y estrategias orientadas a reducir la incidencia y gravedad de los siniestros viales en la ciudad.

<br>

* **`Sebastian Vazquez`**..................   [![linkedin](https://img.shields.io/badge/linkedin-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sebastian-vazquez-67353722b/)



