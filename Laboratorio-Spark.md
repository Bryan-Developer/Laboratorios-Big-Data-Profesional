# Laboratorio de Spark
## Ejercicio 01 - Dataframe
### Con las tablas persona, empresa y transaccion en la Capa Universal debes de crear el siguiente Reporte
Campo | Tipo | Descripcion
------------ | ------------- | -------------
ID_PERSONA | INT | ID de la persona que realizó la transacción
NOMBRE_PERSONA | STRING | Nombre de la persona que realizó la transacción
EDAD_PERSONA | INT | Edad de la persona que realizó la transacción
SALARIO_PERSONA | DOUBLE | Salario de la persona que realizó la transacción
TRABAJO_PERSONA | STRING | Nombre de la empresa donde trabaja la persona
MONTO_TRANSACCION | DOUBLE | Monto de la transacción realizada
FECHA_TRANSACCION | STRING | Fecha de la transacción realizada
EMPRESA_TRANSACCION | STRING | Nombre de la empresa donde se realizó la transacción
1. Leer el archivo csv de persona.data en HDFS
```bash
[u47774417@vmcloudera01 ~]$ pyspark2 --master local[1]
>>> dfPersonaData=spark.read.format("csv").option("header","true").option("delimiter","|").load("hdfs:///user/u47774417/ejercicio2/database/u47774417_landing_tmp/persona/persona.data")
>>> dfPersonaData.show(5)
+---+---------+--------------+--------------------+-------------+----+-------+----------+
| ID|   NOMBRE|      TELEFONO|              CORREO|FECHA_INGRESO|EDAD|SALARIO|ID_EMPRESA|
+---+---------+--------------+--------------------+-------------+----+-------+----------+
|  1|     Carl|1-745-633-9145|arcu.Sed.et@ante....|   2004-04-23|  32|  20095|         5|
|  2|Priscilla|      155-2498|Donec.egestas.Ali...|   2019-02-17|  34|   9298|         2|
|  3|  Jocelyn|1-204-956-8594|amet.diam@loborti...|   2002-08-01|  27|  10853|         3|
|  4|    Aidan|1-719-862-9385|euismod.et.commod...|   2018-11-06|  29|   3387|        10|
|  5|  Leandra|      839-8044|at@pretiumetrutru...|   2002-10-10|  41|  22102|         1|
+---+---------+--------------+--------------------+-------------+----+-------+----------+
only showing top 5 rows
```
2. Leer el archivo csv de empresa.data en HDFS
```bash
>>> dfEmpresaData=spark.read.format("csv").option("header","true").option("delimiter","|").load("hdfs:///user/u47774417/ejercicio2/database/u47774417_landing_tmp/empresa/empresa.data")
>>> dfEmpresaData.show(5)
+---+---------+
| ID|   NOMBRE|
+---+---------+
|  1|  Walmart|
|  2|Microsoft|
|  3|    Apple|
|  4|   Toyota|
|  5|   Amazon|
+---+---------+
only showing top 5 rows
```
3. Leer el archivo csv de transacciones.data en HDFS
```bash
>>> dfTransaccionData = spark.read.format("csv").option("header","true").option("delimiter","|").load("hdfs:///user/u47774417/ejercicio2/database/u47774417_landing_tmp/transaccion/transacciones.data")
>>> dfTransaccionData.show(5)
+----------+----------+-----+----------+
|ID_PERSONA|ID_EMPRESA|MONTO|     FECHA|
+----------+----------+-----+----------+
|        18|         3| 1383|2018-01-21|
|        30|         6| 2331|2018-01-21|
|        47|         2| 2280|2018-01-21|
|        28|         1|  730|2018-01-21|
|        91|         4| 3081|2018-01-21|
+----------+----------+-----+----------+
only showing top 5 rows
```
4. Unir los dataframes persona y transacciones.
```bash
>>> dfTemp = dfTransaccionData.join(dfPersonaData, dfTransaccionData.ID_PERSONA == dfPersonaData.ID).join(dfEmpresaData, dfEmpresaData.ID == dfTransaccionData.ID_EMPRESA).select(dfTransaccionData['ID_PERSONA'], dfPersonaData['NOMBRE'].alias('NOMBRE_PERSONA'), dfPersonaData['EDAD'].alias('EDAD_PERSONA'), dfPersonaData['SALARIO'].alias('SALARIO_PERSONA'), dfPersonaData['ID_EMPRESA'].alias('EMPRESA_PERSONA'), dfTransaccionData['MONTO'].alias('MONTO_TRANSACCION'), dfTransaccionData['FECHA'].alias('FECHA_TRANSACCION'),dfEmpresaData['NOMBRE'].alias('EMPRESA_TRANSACCION'))
>>> dfTemp.show(5)
+----------+--------------+------------+---------------+---------------+-----------------+-----------------+-------------------+
|ID_PERSONA|NOMBRE_PERSONA|EDAD_PERSONA|SALARIO_PERSONA|EMPRESA_PERSONA|MONTO_TRANSACCION|FECHA_TRANSACCION|EMPRESA_TRANSACCION|
+----------+--------------+------------+---------------+---------------+-----------------+-----------------+-------------------+
|        18|          Owen|          34|           4759|              7|             1383|       2018-01-21|              Apple|
|        30|       Clayton|          52|           9505|              8|             2331|       2018-01-21|             Google|
|        47|        Vernon|          35|           7109|             10|             2280|       2018-01-21|          Microsoft|
|        28|       Stephen|          53|           9469|              8|              730|       2018-01-21|            Walmart|
|        91|         Erica|          32|           8934|              6|             3081|       2018-01-21|             Toyota|
+----------+--------------+------------+---------------+---------------+-----------------+-----------------+-------------------+
only showing top 5 rows
>>> dfReporte1 = dfTemp.join(dfEmpresaData, dfEmpresaData.ID == dfTemp.EMPRESA_PERSONA).select(dfTemp['ID_PERSONA'],dfTemp['NOMBRE_PERSONA'],dfTemp['EDAD_PERSONA'],d
fTemp['SALARIO_PERSONA'],dfEmpresaData['NOMBRE'].alias('TRABAJO_PERSONA'),dfTemp['MONTO_TRANSACCION'],dfTemp['FECHA_TRANSACCION'],dfTemp['EMPRESA_TRANSACCION'])
>>> dfReporte1.show(5)
+----------+--------------+------------+---------------+---------------+-----------------+-----------------+-------------------+
|ID_PERSONA|NOMBRE_PERSONA|EDAD_PERSONA|SALARIO_PERSONA|TRABAJO_PERSONA|MONTO_TRANSACCION|FECHA_TRANSACCION|EMPRESA_TRANSACCION|
+----------+--------------+------------+---------------+---------------+-----------------+-----------------+-------------------+
|        18|          Owen|          34|           4759|        Samsung|             1383|       2018-01-21|              Apple|
|        30|       Clayton|          52|           9505|             HP|             2331|       2018-01-21|             Google|
|        47|        Vernon|          35|           7109|           Sony|             2280|       2018-01-21|          Microsoft|
|        28|       Stephen|          53|           9469|             HP|              730|       2018-01-21|            Walmart|
|        91|         Erica|          32|           8934|         Google|             3081|       2018-01-21|             Toyota|
+----------+--------------+------------+---------------+---------------+-----------------+-----------------+-------------------+
only showing top 5 rows
```
5. Insertar en una tabla Hive
```bash
>>> dfReporte1.createOrReplaceTempView("dfReporte1_temp")
>>> sqlContext.sql("create table U47774417_UNIVERSAL.dfReporte1 as select * from dfReporte1_temp")
```
6. Verificar en Hive
```bash
hive> SELECT * FROM U47774417_UNIVERSAL.dfReporte1 LIMIT 10;
OK
18      Owen    34      4759    Samsung 1383    2018-01-21      Apple
30      Clayton 52      9505    HP      2331    2018-01-21      Google
47      Vernon  35      7109    Sony    2280    2018-01-21      Microsoft
28      Stephen 53      9469    HP      730     2018-01-21      Walmart
91      Erica   32      8934    Google  3081    2018-01-21      Toyota
74      Kaitlin 56      6515    Sony    2409    2018-01-21      HP
41      Wynne   31      19522   Toyota  3754    2018-01-22      Microsoft
42      Wanda   42      5419    IBM     4079    2018-01-22      IBM
24      Amaya   24      1801    HP      4475    2018-01-22      Google
67      Buffy   38      15116   Microsoft       561     2018-01-22      IBM
Time taken: 0.055 seconds, Fetched: 10 row(s)
```
## Ejercicio 02 - Elaboracion de Dataframe sin spark sql