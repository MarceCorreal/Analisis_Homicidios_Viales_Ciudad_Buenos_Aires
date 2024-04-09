# Análisis de Homicidios Viales en la Ciudad Autónoma de Buenos Aires (CABA), Argentina.
## Segundo Proyecto individual Henry

Los accidentes de transito son eventos que involucran diferentes tipos de vehículos en las calles de la ciudad.
Dichos accidentes pueden traer consecuencias desde leves a lesiones graves y fallecimientos,
En Buenos Aires tienen altos impactos por las altas tasas de fallecidos y su aumwnto. 
Las tasas de mortalidad son un indicador importante por regiones y por numero de habitantes
En Argentina, cada año mueren cerca de 4.000 personas en siniestros viales, Estas cifras equivalen a 11 personas por día

### Objetivo

El objetivo del proyecto es la elaboración de un proyecto de anális de datos con el fin de generar información que le permita a las autoridades locales tomar medidas para disminuir la cantidad de víctimas fatales de los siniestros viales.
Inicialmente, se hace un ETl, entendiendo y limpiando los datos para cada uno de los cuadernos que se entregan en la consigna: etl_hechos y etl_victimas. 

[etl_hechos](https://drive.google.com/file/d/1trm4cMmp5ZCqvqb89VRqBQ9fiz69FK_F/view?usp=drive_link)

[etl_victimas](https://drive.google.com/file/d/1H3ccZghMDrwF0a1QrhSImVplwmJ_Q9Sh/view?usp=drive_link)

En cada uno de estos notebooks, se indica paso a paso, las acciones que se desarrollaron para limpiar los datos.
El dataframe resultado del ETL de cada archivo es el siguiente:

[df_hechos](https://drive.google.com/file/d/1SX5r-hsMfx1RUze-dd0cuHTT1m7PFVMu/view?usp=drive_link)

[df_victimas](https://drive.google.com/file/d/16_g6U-Cy2Wxi3UaOjwg812QygMxXZjHl/view?usp=drive_link)


A travez de la columna colún ID_Hecho, se hizo merge de los dos archivos de datos y se limprió y organizó en archivo nuevamente en un data freme llamado df_accidentes.

[df_accidentes](https://drive.google.com/file/d/1jRNG1FQIQWvNS6mt0mUeJiclwsGFKp9n/view?usp=drive_link)

Posterior al análisis preliminar, se procede a analizar la información a profundidad, buscando sacar conclusiones de valor que respondan a la problemática descrita en el contexto del proyecto.
Para lo anterior, se desarrolla el eda en un cuaderno de jupyter, que trata 3 temas principalmente

* Característica de tiempo del hecho
* Características geográficas del hecho
* Características de la víctima

Los programs que se deberán impliementar para disminuir la cantidad de víctimas mortales estarán dirigidos a estos 3 sectores.






