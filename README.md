# Práctica 1. Procesamiento de datos mediante Apache Spark

## Enunciado
El objetivo de este proyecto es diseñar y ejecutar un pipeline de procesamiento de datos masivos usando los registros de viajes de taxis y vehículos de transporte de la ciudad de Nueva York (TLC Trip Record Data). El proyecto busca aplicar los principios de Computación de Altas Prestaciones (HPC) al análisis de datos reales, abordando problemas de escalabilidad, paralelismo y optimización de rendimiento.

El estudiante deberá demostrar su capacidad para manipular volúmenes de datos de cientos de millones de filas, aplicando técnicas de procesamiento distribuido (por ejemplo, con Spark o Dask), y evaluando la eficiencia de diferentes estrategias de particionado, caching, y join. Además, se espera que explore el formato Parquet, ampliamente utilizado en análisis de datos a gran escala por su compresión y acceso columnar.

Los datos provienen del portal oficial de la Taxi and Limousine Commission (TLC) de la ciudad de Nueva York, que publica mensualmente registros detallados de viajes. Cada registro contiene información como la hora y lugar de recogida y destino, distancia, importe del viaje, método de pago y número de pasajeros.

Para el proyecto se recomienda trabajar con al menos 12 meses de datos consecutivos (por ejemplo, de 2023), lo que asegura un volumen lo bastante grande para justificar el uso de técnicas de HPC. El análisis incluirá series temporales (por hora, día o mes), distribución geográfica de los viajes por zonas de la ciudad, y agregaciones por tipo de tarifa o vehículo.

Puede encontrar más información del conjunto de datos en el siguiente enlace: https://www1.nyc.gov/site/tlc/about/tlc-trip-record-data.page

Realice los estudios que considere necesarios sobre los datos que contiene.  Es obligatorio proporcionar al menos tres estudios. Ejemplos de estudios:

    Velocidad media de los taxis en función de la hora.
    Viajes en taxi más comunes
    Registros financieros (propinas, personas, etc.)

Será necesario realizar al menos una ejecución basada en una consulta SQL (spark.sql(.....)), al menos una consulta mediante una concatenación de llamadas a métodos del DataFrame como: select, groupBy, y finalmente una haciendo uso de RDDs. Con el objetivo de estudiar el mejor método de trabajo, uno de los estudios realizados tiene que estar implementado de las tres formas.

Tendrá que preparar un informe, indicando los siguientes aspectos:

    Tiempo de ejecución.
    Cantidad de datos procesados en término de número de viajes.


Será obligatorio realizar un análisis de rendimiento en términos de aceleración para una de las consultas en dos variantes.

Se entregará tanto el código implementado como los comentarios y párrafos necesarios en un único Notebook de Python.

Ayudas:

- Lectura del fichero de entrada

```
df = spark.read.format("parquet").option("inferSchema", "true").option("timestampFormat","yyyy-MM-dd HH:mm:ss").option("header", "true").option("mode", "DROPMALFORMED").load("/content/tripdata_2017-1.csv")
```

## Casos a implementar:

* Número de viajes de taxis que terminan en disputas por barrio
* Velocidad media en función de la hora
* Coste medio por viaje por hora y zona
