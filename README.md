# Análisis de Homicidios Viales en la Ciudad Autónoma de Buenos Aires (CABA), Argentina.
## Segundo Proyecto individual Henry

Los accidentes de transito son eventos que involucran diferentes tipos de vehículos en las calles de la ciudad.
Dichos accidentes pueden traer consecuencias desde leves a lesiones graves y fallecimientos,
En Buenos Aires tienen altos impactos por las altas tasas de fallecidos y su aumwnto. 
Las tasas de mortalidad son un indicador importante por regiones y por numero de habitantes
En Argentina, cada año mueren cerca de 4.000 personas en siniestros viales, Estas cifras equivalen a 11 personas por día

### Objetivo

El objetivo del proyecto es la elaboración de un proyecto de anális de datos con el fin de generar información que le permita a las autoridades locales tomar medidas para disminuir la cantidad de víctimas fatales de los siniestros viales.

### Desarrollo
Bibliotecas utilizadas

*NumPy para soporte de arrays y matrices

*Pandas para manipulación y análisis de datos

*Datetime y time para trabajar con objetos de fecha y hora

*Matplotlib.pyplot para la creación de gráficos estáticos, animados e interactivos

*Seaborn, una biblioteca de visualización de datos basada en matplotlib, para hacer gráficos más atractivos

*Calendar, que proporciona funciones relacionadas con la visualización y manipulación de calendarios y fechas.

*Importa el módulo cm de matplotlib, que es parte de la biblioteca de visualización matplotlib.

*Importa la biblioteca folium para la creación de mapas interactivos y su plugin HeatMap para visualizaciones de densidad.

*Importar la biblioteca warnings para controlar las advertencias

*Importa plotly.express para hacer el mapa de calor para visualizar en python


#### ETL

Inicialmente, se hace un ETl, entendiendo y limpiando los datos para cada uno de los cuadernos que se entregan en la consigna: etl_hechos y etl_victimas. 

[etl_hechos](https://drive.google.com/file/d/1trm4cMmp5ZCqvqb89VRqBQ9fiz69FK_F/view?usp=drive_link)

[etl_victimas](https://drive.google.com/file/d/1H3ccZghMDrwF0a1QrhSImVplwmJ_Q9Sh/view?usp=drive_link)

En cada uno de estos notebooks, se indica paso a paso, las acciones que se desarrollaron para limpiar los datos.
El dataframe resultado del ETL de cada archivo es el siguiente:

[df_hechos](https://drive.google.com/file/d/1SX5r-hsMfx1RUze-dd0cuHTT1m7PFVMu/view?usp=drive_link)

[df_victimas](https://drive.google.com/file/d/16_g6U-Cy2Wxi3UaOjwg812QygMxXZjHl/view?usp=drive_link)


A travez de la columna colún ID_Hecho, se hizo merge de los dos archivos de datos y se limprió y organizó en archivo nuevamente en un data freme llamado df_accidentes.

[df_accidentes](https://drive.google.com/file/d/1jRNG1FQIQWvNS6mt0mUeJiclwsGFKp9n/view?usp=drive_link)


### Análisis

Posterior al análisis preliminar, se procede a analizar la información a profundidad, buscando sacar conclusiones de valor que respondan a la problemática descrita en el contexto del proyecto.
Para lo anterior, se desarrolla el eda en un cuaderno de jupyter, que trata 3 temas principalmente

* Característica temporales del hecho
* Características geográficas del hecho
* Características de la víctima

Los programs sociales y capacitaciones que se deberán impliementar en Buenos Aire  para disminuir la cantidad de víctimas mortales, estarán dirigidos a estos 3 sectores.

Para el análisis profundde de los datos se desarrolló el EDA

[eda_accidentes](https://drive.google.com/file/d/1ndVjABgyYDN_vIOFxbyIdtplH45lV_Oc/view?usp=sharing)

El EDA se desarrolló en un archivo parquet previniendo un tema de espacio, sinembargo, fué necesario convertir Parquet a un formato compatible con MySQL (json), dado que MySQL no admite directamente el formato Parquet.
Se guardo el df_accidentes_analizado en json, para que el df_accidentes crudo quedara como evidencia del proceso, adicionalmente, el sistema no permite guardar el df con el formato de coordenadas en paruqet.

[df_accidentes_analizado](https://drive.google.com/file/d/1VggAvEJezQB6ckIR1B9DPupYTfJLfEbH/view?usp=drive_link)

#### EDA

Aún cuando las gráficas y el desarrollo del EDA se puede visualizar el el notebook de jupiter a continuación voy a compartir las principales 
conclusiones y gáficas del análisis:

Inicialmente, se utilizó función para validar los datos, buscando donde borrar los nan porque de lo contrario, si borraba los nan en todo el df se borraban todos loa datos pued todas las filas tenian un registro no identificado,

Posteríor, se analizó el área del hecho como toal obteniendo las siguientes conclusiones:

#### Análisis Temporal

* Distribución Anual de Hechos: Aún cuando al hacer el etl, borré columna de año, día, mes y hora, dejándo una sóla columna en el eda fué necesario separarlo en columnas independientes de nuevo para poder hacer el análisis que buscaba.
Al graficar la distribución de hechos, se puede ver como el año con la mayor cantida de hechos fué el 2018, seguido por el 2016. desde ese momento se puede ver una tendencia suave a la disminución hasta el 2019 donde abruptamente baja y se mantiene la tendencia lo quepuede explicarse con el inicio de la pandemia y su posterior estabilización en el 2021:



![image](https://github.com/MarceCorreal/PI2_DA/assets/121261433/9665fc30-6724-4e08-8d44-0045190c83dc)


* Distribución Mensual de Hechos: En este aso, se referencia 

En este caso es clara el impacto de la cantidad de accidentes en Diciembre, lo cual puede explicarse por las fechas devcembrinas, seguido por agosto que también cuadran con las vacaciones de mitad de año. Esta conclusión lleva a sugerir que los programas de prevención que se realicen podrían efectuarse en los meses de Noviembre y Julio 


![image](https://github.com/MarceCorreal/PI2_DA/assets/121261433/6d4d7f8d-ce72-48a5-8b38-bc6b3ba1e60a)


Posterior a este análisis me parceión interesante revisar la diferencia de tendencia mensual a travez de los años, para lo cual hice 6 subplots año tras año, indicando lo que revisavamos el grafico anterior donde la tendencia aumenta a los meses de diciembre, pero los años de pandemia 2019, 20 y 21 contaron con tendencias negativas.

![image](https://github.com/MarceCorreal/PI2_DA/assets/121261433/d04aaa01-2056-4c5c-9daf-bef04e06959d)


* Distribcución Semanal:  de HechosContinúo con el análisis temporal del hecho, de mayor a menor, anual, mensual y semanal.
En este caso, mediante la gráfica se puede verificar que durante la semana no hay mayores variaciones en la frecuencia de los hechos de tránsito. En efecto los días donde se evidencia la mayor cantidad de hechos es el fin de semana y los lunes los cuales se puede explicar facilmente. De tal modo que los programas que se realicen pueden ir relacionados a los días de fiesta y el consumo probable de bebidas alcoholicas.

![image](https://github.com/MarceCorreal/PI2_DA/assets/121261433/44768c19-257e-4577-964f-59362e7c98ee)


#### Análisis Geográfico

* Distribución geográfica de los hechos: Para entender esta distribución, en un primer momento tuve problemas con el formato de las coordenadas, pues inicialmente tenía las coordenadas en string pero viniendo de objetos, por lo tanto fué necesario separar de nuevo las coordenadas en longitud y latitud, convertir formatos a float, volverlos a unir y dejarlos como objeto. Aunque era el mismo formato, si no hacía esa vuelta el sistema no lo podía graficar.
De cualquier forma inicialmente se graficó primero el mapa de buenos aires con los puntos de las coordenadas de los hechos,con folium.map, pero esta gráfica era muy dificil de leer, porque quedan todas las flechitas juntas el el mapa:

![image](https://github.com/MarceCorreal/PI2_DA/assets/121261433/b1835eca-c89c-4406-ae94-c8da7924bd8f)


Dado que desde esta gráfica no se puede concluir nada, se realizó en mapa de calor que da mayor información:

![image](https://github.com/MarceCorreal/PI2_DA/assets/121261433/3da0cb8e-cd9c-433d-8ca3-3ca84e53b90f)

Sinembargo esta gráfica tampoco da mayor información, así que filtreré la comuna con mayor frecuencia de hechos:

![image](https://github.com/MarceCorreal/PI2_DA/assets/121261433/c9a216d7-4eb8-4235-98ab-1f920eacdbab)

La anterior gráfica indica que la comuna de mayor frecuencia de hechos es la comuna número 1, seguida de la 4 y la 9 por loque las campañas de prevención debe iniciar de esa forma.

#### Análisis de las víctimas

* Distribución de Edades de Víctimas de los Hechos
La gráfica a continuación indica de forma clara que la edades donde se presentan más cantidad de víctimas en accidentes de tráfico es entre los 20 y 30 año, lo que se supone por la juventude inexperiencia al volante, y aunque tiene una tendencia a la baja incrementa de nuevo al rededor de los 70 años, lo cual se expica por la vejész.  Esto es un indicador del tipo de programas y la población a la cual estarán enfocados los programas.

![image](https://github.com/MarceCorreal/PI2_DA/assets/121261433/264d0d9e-1ccb-4e32-a9e2-9818cd3b22ad)

* Distribución anual de la cantidad de Víctimas por género anual:
La gráfica a continuación permite inferir que todos los años es mayor por un margen considerable la cantidad de víctimas del género masculino.  Esto se puede inferir por el gusto que este género tiene por la velocidad, y por el mayor porcentaje de consumo de alcohol.
Se ve nuevamente una disminución de víctimas importante en el año 2020 que coincide con el año de la pandemia. Sinembargo es importante dirigir las campañas de prevención a ambos géneros ya que no simpre el rol de la victima es el conductor del vehiculo.

![image](https://github.com/MarceCorreal/PI2_DA/assets/121261433/9ef78ccb-8d74-49e2-bad9-04057936c17a)

* Dispersión del rol de la víctima por edades
Para terminar el análisis sobre las víctimas, es importante conocer el rol de la víctima dentro de la escena del hecho.  En ese sentido, la gráfica revela que en un alto porcentaje se desconoce el rol de la víctima lo que se puede entender por falta de claridad en el hecho o dificultades con los datos.
Sinembargo, en contra de lo que se pensaba en el que la víctima era mayoritariamente el conductor, los datos revelan que las víctimas en su mayoría son los peatones sin entender todavía quien es el acusado, para lo cual habrá luego otro análisis.
Adicionalmente, se puede ver que el rango de la edad de los peatones que mueren en accidentes de tránsito tienen entre 45 y 60 años, lo cual puede entenderse por disminución de facultades como marcha y visión.

![image](https://github.com/MarceCorreal/PI2_DA/assets/121261433/fdc11c61-90d7-49b9-a1c0-b52b92a033da)

## KPIs.

La consigna del proyecto incluye el análisis del comportamiento del cumplimiento de 3 objetivos para reducir la cantidad de víctimas asociados a a 3 indicadores claves de rendimiento KPI asi:

### Reducción Tasa de Homicidios

Reducir en un 10% la tasa de homicidios en siniestros viales de los últimos seis meses en CABA, en comparación con el semestre anterior: Este KPI se basa en la Tasa de homicidios en siniestros viales, que mide el número de víctimas fatales en accidentes de tránsito por cada 100,000 habitantes durante un período específico. Se calcula dividiendo el número de homicidios en siniestros viales por la población total y multiplicando por 100,000. Para el año 2021. El objetivo era reducir la tasa en un 10% para el segundo semestre de 2021, lo que equivale a 1.61. Sin embargo, el KPI resultante fue de 1.66, indicando que se no se cumplió con el objetivo propuesto.

### Reducción cantidad de accidenes mortales de motociclistas

Reducir en un 7% la cantidad de accidentes mortales de motociclistas en el último año en CABA, respecto al año anterior: Este indicador se basa en la Cantidad de accidentes mortales de motociclistas, que mide el cambio porcentual en el número de accidentes mortales en los que estuvieron involucrados motociclistas entre dos años consecutivos. El objetivo era no soprepasar -44.2 para 2021, lo que representa una reducción del 7%. Sin embargo, el valor obtenido para 2021 fue de 53,3, indicando un aumento del 53% en comparación con 2020, lo que no cumple con el objetivo establecido.

### Reducción en un 10% los homicidios en las avenidas en el último año en CABA

Reducir en un 10% los homicidios en las avenidas en el último año en CABA, respecto al año anterior: Este KPI se basa en los homicidios en las avenidas, que mide el número de víctimas fatales en accidentes de tránsito durante un año. Para el año 2020, fue de 69 victimas, y el objetivo era reducirla a 62 para 2021, lo que representa una disminución del 10%. Sin embargo, el número de víctimas para 2021 fue de 66 victimas, indicando una disminución de homicidios en las avenidas en comparación con el año anterior, pero aún asi insuficiente e incumpliendo así el objetivo establecido.


### DASHBOAR

Basados y enlazados con los datos anteriormente expuestos se deja en el repositorio de Google Drive el Dashboard interactivo:

[Dashboard](https://drive.google.com/file/d/1iKbu-PMKwwilCOI9Kxq49B7BiPZZCYay/view?usp=sharing)












