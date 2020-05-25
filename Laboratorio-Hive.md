# Laboratorio implementar DataLake
### 1. Crear la estructura de carpetas dentro de HDFS
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_landing_tmp/persona```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_landing_tmp/empresa```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_landing_tmp/transaccion```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_landing/persona```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_landing/empresa```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_landing/transaccion```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_universal/persona```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_universal/empresa```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_universal/transaccion```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_universal/transaccion_enriquecida```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/database/u47774417_smart```
1. Ejecuta el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio2/schema/database/u47774417_landing```
1. Ejecuta el siguiente comando para listar la estrucutra de carpetas previamente realizada ```hdfs dfs -ls -R /user/u47774417/ejercicio2```
```bash
[u47774417@vmcloudera01 ~]$ hdfs dfs -ls -R /user/u47774417/ejercicio2
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:57 /user/u47774417/ejercicio2/database
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:55 /user/u47774417/ejercicio2/database/u47774417_landing
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:55 /user/u47774417/ejercicio2/database/u47774417_landing/empresa
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:55 /user/u47774417/ejercicio2/database/u47774417_landing/persona
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:55 /user/u47774417/ejercicio2/database/u47774417_landing/transaccion
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:54 /user/u47774417/ejercicio2/database/u47774417_landing_tmp
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:54 /user/u47774417/ejercicio2/database/u47774417_landing_tmp/empresa
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:54 /user/u47774417/ejercicio2/database/u47774417_landing_tmp/persona
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:54 /user/u47774417/ejercicio2/database/u47774417_landing_tmp/transaccion
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:57 /user/u47774417/ejercicio2/database/u47774417_smart
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:57 /user/u47774417/ejercicio2/database/u47774417_universal
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:57 /user/u47774417/ejercicio2/database/u47774417_universal/empresa
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:57 /user/u47774417/ejercicio2/database/u47774417_universal/persona
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:57 /user/u47774417/ejercicio2/database/u47774417_universal/transaccion
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:57 /user/u47774417/ejercicio2/database/u47774417_universal/transaccion_enriquecida
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:59 /user/u47774417/ejercicio2/schema
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:59 /user/u47774417/ejercicio2/schema/database
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 17:59 /user/u47774417/ejercicio2/schema/database/u47774417_landing
```
### 2. Enlazar las carpetas de database a Hive dentro de la consola Hive
1. Ejecutamos hive para acceder a la consola de hive.
```bash
[u47774417@vmcloudera01 ~]$ hive
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0
Java HotSpot(TM) 64-Bit Server VM warning: Using incremental CMS is deprecated and will likely be removed in a future release
Java HotSpot(TM) 64-Bit Server VM warning: ignoring option MaxPermSize=512M; support was removed in 8.0

Logging initialized using configuration in jar:file:/opt/cloudera/parcels/CDH-5.16.2-1.cdh5.16.2.p0.8/jars/hive-common-1.1.0-cdh5.16.2.jar!/hive-log4j.properties
WARNING: Hive CLI is deprecated and migration to Beeline is recommended.
hive> 
```
2. Ejecuta la siguiente sentencia dentro de la consola de hive para enlazar la base de datos ```U47774417_LANDING_TMP```a su similar en hdfs ```CREATE DATABASE IF NOT EXISTS U47774417_LANDING_TMP LOCATION '/user/u47774417/ejercicio2/database/u47774417_landing_tmp';```
```bash
hive> CREATE DATABASE IF NOT EXISTS U47774417_LANDING_TMP LOCATION '/user/u47774417/ejercicio2/database/u47774417_landing_tmp';
OK
Time taken: 2.03 seconds
```
3. Ejecuta la siguiente sentencia dentro de la consola de hive para enlazar la base de datos ```U47774417_LANDING```a su similar en hdfs ```CREATE DATABASE IF NOT EXISTS U47774417_LANDING LOCATION '/user/u47774417/ejercicio2/database/u47774417_landing';```
```bash
hive> CREATE DATABASE IF NOT EXISTS U47774417_LANDING LOCATION '/user/u47774417/ejercicio2/database/u47774417_landing';
OK
Time taken: 0.027 seconds
```
4. Ejecuta la siguiente sentencia dentro de la consola de hive para enlazar la base de datos ```U47774417_UNIVERSAL```a su similar en hdfs ```CREATE DATABASE IF NOT EXISTS U47774417_UNIVERSAL LOCATION '/user/u47774417/ejercicio2/database/u47774417_universal';```
```bash
hive> CREATE DATABASE IF NOT EXISTS U47774417_UNIVERSAL LOCATION '/user/u47774417/ejercicio2/database/u47774417_universal';
OK
Time taken: 0.081 seconds
```
5. Ejecuta la siguiente sentencia dentro de la consola de hive para enlazar la base de datos ```U47774417_SMART```a su similar en hdfs ```CREATE DATABASE IF NOT EXISTS U47774417_SMART LOCATION '/user/u47774417/ejercicio2/database/u47774417_smart';```
```bash
hive> CREATE DATABASE IF NOT EXISTS U47774417_SMART LOCATION '/user/u47774417/ejercicio2/database/u47774417_smart';
OK
Time taken: 0.014 seconds
```
6. Para verficar la creacion de las bases de datos ejecutamos el siguiente comando ```SHOW DATABASE LIKE 'pattern'```.
```bash
hive> show databases like 'u47774417*';
OK
u47774417_landing
u47774417_landing_tmp
u47774417_smart
u47774417_universal
Time taken: 0.008 seconds, Fetched: 4 row(s)
```
7. Crear la tabla ```U47774417_LANDING_TMP.PERSONA``` con la siguiente estructura y enlazandalo a la carpeta en hdfs que tiene su misma estructura.
```bash
hive> CREATE TABLE U47774417_LANDING_TMP.PERSONA(
    > ID STRING,
    > NOMBRE STRING,
    > TELEFONO STRING,
    > CORREO STRING,
    > FECHA_INGRESO STRING,
    > EDAD STRING,
    > SALARIO STRING,
    > ID_EMPRESA STRING
    > )
    > ROW FORMAT DELIMITED
    > FIELDS TERMINATED BY '|'
    > LINES TERMINATED BY '\n'
    > STORED AS TEXTFILE
    > LOCATION '/user/u47774417/database/u47774417_landing_tmp/persona';
OK
Time taken: 0.155 seconds
```
8. Realiza la ingesta de datos del archvio ```persona.data``` a la carpeta ```/user/u47774417/database/u47774417_landing_tmp/persona``` para que se inserte registros en la tabla previamente insertada.
```bash
[u47774417@vmcloudera01 ~]$ hdfs dfs -put /dataset/persona.data /user/u47774417/database/u47774417_landing_tmp/persona
```
9. Para visualizar los datos ejecuta un ```select``` a la tabla ```U47774417_LANDING_TMP.PERSONA``` y limita el resultado a 10.
```bash
hive> SELECT * FROM U47774417_LANDING_TMP.PERSONA LIMIT 10;
OK
ID      NOMBRE  TELEFONO        CORREO  FECHA_INGRESO   EDAD    SALARIO ID_EMPRESA
1       Carl    1-745-633-9145  arcu.Sed.et@ante.co.uk  2004-04-23      32      20095   5
2       Priscilla       155-2498        Donec.egestas.Aliquam@volutpatnunc.edu  2019-02-17      34      9298    2
3       Jocelyn 1-204-956-8594  amet.diam@lobortis.co.uk        2002-08-01      27      10853   3
4       Aidan   1-719-862-9385  euismod.et.commodo@nibhlaciniaorci.edu  2018-11-06      29      3387    10
5       Leandra 839-8044        at@pretiumetrutrum.com  2002-10-10      41      22102   1
6       Bert    797-4453        a.felis.ullamcorper@arcu.org    2017-04-25      70      7800    7
7       Mark    1-680-102-6792  Quisque.ac@placerat.ca  2006-04-21      52      8112    5
8       Jonah   214-2975        eu.ultrices.sit@vitae.ca        2017-10-07      23      17040   5
9       Hanae   935-2277        eu@Nunc.ca      2003-05-25      69      6834    3
Time taken: 0.241 seconds, Fetched: 10 row(s)
```
10. Crear la tabla ```U47774417_LANDING_TMP.PERSONA``` con la siguiente estructura y enlazandalo a la carpeta en hdfs que tiene su misma estructura.
```bash
hive> CREATE TABLE U47774417_LANDING_TMP.EMPRESA(
    > ID STRING,
    > NOMBRE STRING
    > )
    > ROW FORMAT DELIMITED
    > FIELDS TERMINATED BY '|'
    > LINES TERMINATED BY '\n'
    > STORED AS TEXTFILE
    > LOCATION '/user/u47774417/database/u47774417_landing_tmp/empresa';
OK
Time taken: 0.067 seconds
```
11. Realiza la ingesta de datos del archvio ```empresa.data``` a la carpeta ```/user/u47774417/database/u47774417_landing_tmp/empresa``` para que se inserte registros en la tabla previamente insertada.
```bash
[u47774417@vmcloudera01 ~]$ hdfs dfs -put /dataset/empresa.data /user/u47774417/database/u47774417_landing_tmp/empresa
```
12. Para visualizar los datos ejecuta un ```select``` a la tabla ```U47774417_LANDING_TMP.EMPRESA``` y limita el resultado a 10.
```bash
hive> SELECT * FROM U47774417_LANDING_TMP.EMPRESA LIMIT 10;
OK
ID      NOMBRE
1       Walmart
2       Microsoft
3       Apple
4       Toyota
5       Amazon
6       Google
7       Samsung
8       HP
9       IBM
Time taken: 0.128 seconds, Fetched: 10 row(s)
```
13. Crear la tabla ```U47774417_LANDING_TMP.TRANSACCION``` con la siguiente estructura y enlazandalo a la carpeta en hdfs que tiene su misma estructura.
```bash
hive> CREATE TABLE U47774417_LANDING_TMP.TRANSACCION(
    > ID_PERSONA STRING,
    > ID_EMPRESA STRING,
    > MONTO STRING,
    > FECHA STRING
    > )
    > ROW FORMAT DELIMITED
    > FIELDS TERMINATED BY '|'
    > LINES TERMINATED BY '\n'
    > STORED AS TEXTFILE
    > LOCATION '/user/u47774417/database/u47774417_landing_tmp/transaccion';
OK
Time taken: 0.053 seconds
```
14. Realiza la ingesta de datos del archvio ```empresa.data``` a la carpeta ```/user/u47774417/database/u47774417_landing_tmp/empresa``` para que se inserte registros en la tabla previamente insertada.
```bash
[u47774417@vmcloudera01 ~]$ hdfs dfs -put /dataset/transacciones.data /user/u47774417/database/u47774417_landing_tmp/transaccion
```
15. Para visualizar los datos ejecuta un ```select``` a la tabla ```U47774417_LANDING_TMP.TRANSACCION``` y limita el resultado a 10.
```bash
hive> SELECT * FROM U47774417_LANDING_TMP.TRANSACCION LIMIT 10;
OK
ID_PERSONA      ID_EMPRESA      MONTO   FECHA
18      3       1383    2018-01-21
30      6       2331    2018-01-21
47      2       2280    2018-01-21
28      1       730     2018-01-21
91      4       3081    2018-01-21
74      8       2409    2018-01-21
41      2       3754    2018-01-22
42      9       4079    2018-01-22
24      6       4475    2018-01-22
Time taken: 0.056 seconds, Fetched: 10 row(s)
```
16. crea con nano en la consola el siguiente archivo ```persona.txt``` con el siguiente schema dentro
```bash
[u47774417@vmcloudera01 ~]$ nano persona.txt
[u47774417@vmcloudera01 ~]$ cat persona.txt 
{
  "name": "PERSONA",
  "type": "record",
  "fields": [
    {"name": "ID", "type": ["string", "null"]},
    {"name": "NOMBRE", "type": ["string", "null"]},
    {"name": "TELEFONO", "type": ["string", "null"]},
    {"name": "CORREO", "type": ["string", "null"]},
    {"name": "FECHA_INGRESO", "type": ["string", "null"]},
    {"name": "EDAD", "type": ["string", "null"]},
    {"name": "SALARIO", "type": ["string", "null"]},
    {"name": "ID_EMPRESA", "type": ["string", "null"]}
  ]
}
```
17. Guarda el archivo ```persona.txt``` en la siguiente ruta hdfs ```/user/u47774417/ejercicio2/schema/database/u47774417_landing```
```bash
hdfs dfs -put persona.txt /user/u47774417/ejercicio2/schema/database/u47774417_landing
```
18. Luego en la consola de hive crea una tabla almacenada en avro que tome el esquema que previamente hemos guardado en hdfs.
```bash
CREATE TABLE u47774417_LANDING.PERSONA
STORED AS AVRO
LOCATION '/user/u47774417/ejercicio2/database/u47774417_landing/persona'
TBLPROPERTIES (
'avro.schema.url'='hdfs:///user/u47774417/ejercicio2/schema/database/u47774417_landing/persona.txt',
'avro.output.codec'='snappy'
);
```
19. Ejecutamos previamente dos comandos en la consola hive 
```bash
hive> SET hive.exec.compress.output=true;
hive> SET avro.output.codec=snappy;
```
20. Ahora migraremos la data que tenemos previamente insertada en textfile a avro con el siguiente comando
```bash
hive> INSERT OVERWRITE TABLE u47774417_LANDING.PERSONA SELECT * FROM  u47774417_LANDING_TMP.PERSONA;
Query ID = u47774417_20200525094343_c1253cc9-463c-4b14-b003-1c5291121f69
Total jobs = 3
Launching Job 1 out of 3
Number of reduce tasks is set to 0 since there is no reduce operator
Job running in-process (local Hadoop)
2020-05-25 09:43:50,324 Stage-1 map = 100%,  reduce = 0%
Ended Job = job_local1469677562_0001
Stage-4 is selected by condition resolver.
Stage-3 is filtered out by condition resolver.
Stage-5 is filtered out by condition resolver.Moving data to: hdfs://vmcloudera01:8020/user/u47774417/ejercicio2/database/u47774417_landing/persona/.hive-staging_hive_2020-05-25_09-43-48_001_6408962529937321363-
1/-ext-10000
Loading data to table u47774417_landing.persona
Table u47774417_landing.persona stats: [numFiles=1, numRows=101, totalSize=6571, rawDataSize=0]
MapReduce Jobs Launched: 
Stage-Stage-1:  HDFS Read: 147685 HDFS Write: 6636 SUCCESS
Total MapReduce CPU Time Spent: 0 msec
OK
Time taken: 2.623 seconds
```
21. Como podemos observar se crean trabajos en mapreduce para migrar la data de textfile almacenada en landing_tmp a avro almacenada en landing normal para su conversion normal. para verificar vamos ejecutar un simple SELECT.
```bash
hive> SELECT * FROM u47774417_LANDING.PERSONA LIMIT 10;
OK
ID      NOMBRE  TELEFONO        CORREO  FECHA_INGRESO   EDAD    SALARIO ID_EMPRESA
1       Carl    1-745-633-9145  arcu.Sed.et@ante.co.uk  2004-04-23      32      20095   5
2       Priscilla       155-2498        Donec.egestas.Aliquam@volutpatnunc.edu  2019-02-17      34      9298    2
3       Jocelyn 1-204-956-8594  amet.diam@lobortis.co.uk        2002-08-01      27      10853   3
4       Aidan   1-719-862-9385  euismod.et.commodo@nibhlaciniaorci.edu  2018-11-06      29      3387    10
5       Leandra 839-8044        at@pretiumetrutrum.com  2002-10-10      41      22102   1
6       Bert    797-4453        a.felis.ullamcorper@arcu.org    2017-04-25      70      7800    7
7       Mark    1-680-102-6792  Quisque.ac@placerat.ca  2006-04-21      52      8112    5
8       Jonah   214-2975        eu.ultrices.sit@vitae.ca        2017-10-07      23      17040   5
9       Hanae   935-2277        eu@Nunc.ca      2003-05-25      69      6834    3
Time taken: 0.056 seconds, Fetched: 10 row(s)
```
22. crea con nano en la consola el siguiente archivo ```empresa.txt``` con el siguiente schema dentro
```bash
[u47774417@vmcloudera01 ~]$ nano empresa.txt
[u47774417@vmcloudera01 ~]$ cat empresa.txt 
{
  "name": "EMPRESA",
  "type": "record",
  "fields": [
    {"name": "ID", "type": ["string", "null"]},
    {"name": "NOMBRE", "type": ["string", "null"]}
  ]
}
```
23. Guarda el archivo ```empresa.txt``` en la siguiente ruta hdfs ```/user/u47774417/ejercicio2/schema/database/u47774417_landing```
```bash
hdfs dfs -put empresa.txt /user/u47774417/ejercicio2/schema/database/u47774417_landing
```
24. Luego en la consola de hive crea una tabla almacenada en avro que tome el esquema que previamente hemos guardado en hdfs.
```bash
CREATE TABLE u47774417_LANDING.EMPRESA
STORED AS AVRO
LOCATION '/user/u47774417/ejercicio2/database/u47774417_landing/empresa'
TBLPROPERTIES (
'avro.schema.url'='hdfs:///user/u47774417/ejercicio2/schema/database/u47774417_landing/empresa.txt',
'avro.output.codec'='snappy'
);
```
25. Ahora migraremos la data que tenemos previamente insertada en textfile a avro con el siguiente comando
```bash
hive> INSERT OVERWRITE TABLE u47774417_LANDING.EMPRESA SELECT * FROM  u47774417_LANDING_TMP.EMPRESA;
Query ID = u47774417_20200525095252_99526204-549c-4093-81ea-4c01bdbbe675
Total jobs = 3
Launching Job 1 out of 3
Number of reduce tasks is set to 0 since there is no reduce operator
Job running in-process (local Hadoop)
2020-05-25 09:52:08,618 Stage-1 map = 100%,  reduce = 0%Ended Job = job_local1579434856_0002
Stage-4 is selected by condition resolver.
Stage-3 is filtered out by condition resolver.
Stage-5 is filtered out by condition resolver.
Moving data to: hdfs://vmcloudera01:8020/user/u47774417/ejercicio2/database/u47774417_landing/empresa/.hive-staging_hive_2020-05-25_09-52-07_028_7908061219935434146-
1/-ext-10000
Loading data to table u47774417_landing.empresa
Table u47774417_landing.empresa stats: [numFiles=1, numRows=11, totalSize=325, rawDataSize=0]
MapReduce Jobs Launched: 
Stage-Stage-1:  HDFS Read: 238075 HDFS Write: 7025 SUCCESS
Total MapReduce CPU Time Spent: 0 msec
OK
Time taken: 1.93 seconds
```
26. Como podemos observar se crean trabajos en mapreduce para migrar la data de textfile almacenada en landing_tmp a avro almacenada en landing normal para su conversion normal. para verificar vamos ejecutar un simple SELECT.
```bash
hive> SELECT * FROM u47774417_LANDING.EMPRESA LIMIT 10;
OK
ID      NOMBRE
1       Walmart
2       Microsoft
3       Apple
4       Toyota
5       Amazon
6       Google
7       Samsung
8       HP
9       IBM
Time taken: 0.057 seconds, Fetched: 10 row(s)
```
27. crea con nano en la consola el siguiente archivo ```transaccion.txt``` con el siguiente schema dentro
```bash
[u47774417@vmcloudera01 ~]$ nano transaccion.txt
[u47774417@vmcloudera01 ~]$ cat transaccion.txt 
{
  "name": "TRANSACCION",
  "type": "record",
  "fields": [
    {"name": "ID_PERSONA", "type": ["string", "null"]},
    {"name": "ID_EMPRESA", "type": ["string", "null"]},
    {"name": "MONTO", "type": ["string", "null"]},
    {"name": "FECHA", "type": ["string", "null"]}
  ]
}
```
28. Guarda el archivo ```transaccion.txt``` en la siguiente ruta hdfs ```/user/u47774417/ejercicio2/schema/database/u47774417_landing```
```bash
hdfs dfs -put transaccion.txt /user/u47774417/ejercicio2/schema/database/u47774417_landing
```
29. Luego en la consola de hive crea una tabla almacenada en avro que tome el esquema que previamente hemos guardado en hdfs.
```bash
CREATE TABLE u47774417_LANDING.TRANSACCION
STORED AS AVRO
LOCATION '/user/u47774417/ejercicio2/database/u47774417_landing/transaccion'
TBLPROPERTIES (
'avro.schema.url'='hdfs:///user/u47774417/ejercicio2/schema/database/u47774417_landing/transaccion.txt',
'avro.output.codec'='snappy'
);
```
30. Ahora migraremos la data que tenemos previamente insertada en textfile a avro con el siguiente comando
```bash
hive> INSERT OVERWRITE TABLE u47774417_LANDING.TRANSACCION SELECT * FROM  u47774417_LANDING_TMP.TRANSACCION;
Query ID = u47774417_20200525095757_d62b3f6b-baeb-4ffb-9b6b-8a1218c16e8f
Total jobs = 3
Launching Job 1 out of 3
Number of reduce tasks is set to 0 since there is no reduce operator
Job running in-process (local Hadoop)
2020-05-25 09:57:47,702 Stage-1 map = 0%,  reduce = 0%
2020-05-25 09:57:48,719 Stage-1 map = 100%,  reduce = 0%Ended Job = job_local960909261_0001
Stage-4 is selected by condition resolver.
Stage-3 is filtered out by condition resolver.
Stage-5 is filtered out by condition resolver.
Moving data to: hdfs://vmcloudera01:8020/user/u47774417/ejercicio2/database/u47774417_landing/transaccion/.hive-staging_hive_2020-05-25_09-57-45_541_7331605611226974
795-1/-ext-10000
Loading data to table u47774417_landing.transaccion
Table u47774417_landing.transaccion stats: [numFiles=1, numRows=235041, totalSize=5836449, rawDataSize=0]
MapReduce Jobs Launched: 
Stage-Stage-1:  HDFS Read: 5195794 HDFS Write: 5836521 SUCCESS
Total MapReduce CPU Time Spent: 0 msec
OK
Time taken: 3.558 seconds
```
31. Como podemos observar se crean trabajos en mapreduce para migrar la data de textfile almacenada en landing_tmp a avro almacenada en landing normal para su conversion normal. para verificar vamos ejecutar un simple SELECT.
```
hive> SELECT * FROM u47774417_LANDING.TRANSACCION LIMIT 10;
OK
ID_PERSONA      ID_EMPRESA      MONTO   FECHA
18      3       1383    2018-01-21
30      6       2331    2018-01-21
47      2       2280    2018-01-21
28      1       730     2018-01-21
91      4       3081    2018-01-21
74      8       2409    2018-01-21
41      2       3754    2018-01-22
42      9       4079    2018-01-22
24      6       4475    2018-01-22
Time taken: 0.056 seconds, Fetched: 10 row(s)
```
32. Prosiguiendo con los pasos seran netamente en la consola de Hive para crear la tabla persona en universal.
```bash
hive> CREATE TABLE U47774417_UNIVERSAL.PERSONA(
    > ID STRING,
    > NOMBRE STRING,
    > TELEFONO STRING,
    > CORREO STRING,
    > FECHA_INGRESO STRING,
    > EDAD INT,
    > SALARIO DOUBLE,
    > ID_EMPRESA STRING
    > )
    > STORED AS PARQUET
    > LOCATION '/user/u47774417/ejercicio2/database/u47774417_universal/persona'
    > TBLPROPERTIES ("parquet.compression"="SNAPPY");
OK
Time taken: 0.066 seconds
```
33. Migrar la data de landing a universal implica un casteo de dato para que pase se pueda insertar con facilidad y una verificacion de id que evite la tomar la primera linea que contiene la cabera de las columnas pero primero activamos dos opciones que nos permitira una mejor comprension de datos.
```bash
hive> SET hive.exec.compress.output=true;
hive> SET parquet.compression=SNAPPY;
hive> INSERT OVERWRITE TABLE U47774417_UNIVERSAL.PERSONA
    > SELECT
    > cast(ID AS STRING),
    > cast(NOMBRE AS STRING),
    > cast(TELEFONO AS STRING),
    > cast(CORREO AS STRING),
    > cast(FECHA_INGRESO AS STRING),    > cast(EDAD AS INT),
    > cast(SALARIO AS DOUBLE),
    > cast(ID_EMPRESA AS STRING)
    > FROM U47774417_LANDING.PERSONA
    > WHERE ID != 'ID';
Query ID = u47774417_20200525101111_464e40be-df68-4afe-90aa-8474afa6fafa
Total jobs = 3
Launching Job 1 out of 3
Number of reduce tasks is set to 0 since there is no reduce operator
Job running in-process (local Hadoop)
2020-05-25 10:11:20,184 Stage-1 map = 100%,  reduce = 0%
Ended Job = job_local1341518510_0003
Stage-4 is selected by condition resolver.
Stage-3 is filtered out by condition resolver.
Stage-5 is filtered out by condition resolver.
Moving data to: hdfs://vmcloudera01:8020/user/u47774417/ejercicio2/database/u47774417_universal/persona/.hive-staging_hive_2020-05-25_10-11-18_483_704929790024198315
8-1/-ext-10000
Loading data to table u47774417_universal.persona
Table u47774417_universal.persona stats: [numFiles=1, numRows=100, totalSize=7162, rawDataSize=800]
MapReduce Jobs Launched: 
Stage-Stage-1:  HDFS Read: 5285682 HDFS Write: 5844041 SUCCESS
Total MapReduce CPU Time Spent: 0 msec
OK
Time taken: 1.983 seconds
```
34. Validemos la data en universal con un simple select.
```bash
hive> SELECT * FROM U47774417_UNIVERSAL.PERSONA LIMIT 10;
OK
1       Carl    1-745-633-9145  arcu.Sed.et@ante.co.uk  2004-04-23      32      20095.0 5
2       Priscilla       155-2498        Donec.egestas.Aliquam@volutpatnunc.edu  2019-02-17      34      9298.0  2
3       Jocelyn 1-204-956-8594  amet.diam@lobortis.co.uk        2002-08-01      27      10853.0 3
4       Aidan   1-719-862-9385  euismod.et.commodo@nibhlaciniaorci.edu  2018-11-06      29      3387.0  10
5       Leandra 839-8044        at@pretiumetrutrum.com  2002-10-10      41      22102.0 1
6       Bert    797-4453        a.felis.ullamcorper@arcu.org    2017-04-25      70      7800.0  7
7       Mark    1-680-102-6792  Quisque.ac@placerat.ca  2006-04-21      52      8112.0  5
8       Jonah   214-2975        eu.ultrices.sit@vitae.ca        2017-10-07      23      17040.0 5
9       Hanae   935-2277        eu@Nunc.ca      2003-05-25      69      6834.0  3
10      Cadman  1-866-561-2701  orci.adipiscing.non@semperNam.ca        2001-05-19      19      7996.0  7
Time taken: 0.053 seconds, Fetched: 10 row(s)
```
35. Prosiguiendo con los pasos seran netamente en la consola de Hive para crear la tabla empresa en universal.
```bash
hive> CREATE TABLE U47774417_UNIVERSAL.EMPRESA(
    > ID STRING,
    > NOMBRE STRING
    > )
    > STORED AS PARQUET
    > LOCATION '/user/u47774417/ejercicio2/database/u47774417_universal/empresa'
    > TBLPROPERTIES ("parquet.compression"="SNAPPY");
OK
Time taken: 0.105 seconds
```
36. Migrar la data de landing a universal implica un casteo de dato para que pase se pueda insertar con facilidad y una verificacion de id que evite la tomar la primera linea que contiene la cabera de las columnas.
```bash
hive> INSERT OVERWRITE TABLE U47774417_UNIVERSAL.EMPRESA SELECT * FROM U47774417_LANDING.EMPRESA WHERE ID != 'ID';
Query ID = u47774417_20200525101616_c280186e-8a38-4614-8dd5-c2b01ead8dbc
Total jobs = 3
Launching Job 1 out of 3
Number of reduce tasks is set to 0 since there is no reduce operator
Job running in-process (local Hadoop)
2020-05-25 10:16:13,934 Stage-1 map = 100%,  reduce = 0%
Ended Job = job_local624668925_0004
Stage-4 is selected by condition resolver.
Stage-3 is filtered out by condition resolver.
Stage-5 is filtered out by condition resolver.
Moving data to: hdfs://vmcloudera01:8020/user/u47774417/ejercicio2/database/u47774417_universal/empresa/.hive-staging_hive_2020-05-25_10-16-12_221_638800964104257846
1-1/-ext-10000
Loading data to table u47774417_universal.empresa
Table u47774417_universal.empresa stats: [numFiles=1, numRows=10, totalSize=444, rawDataSize=20]
MapReduce Jobs Launched: 
Stage-Stage-1:  HDFS Read: 5294935 HDFS Write: 5844568 SUCCESS
Total MapReduce CPU Time Spent: 0 msec
OK
Time taken: 1.965 seconds
```
37. Validemos la data en universal con un simple select.
```bash
hive> SELECT * FROM U47774417_UNIVERSAL.EMPRESA LIMIT 10;
OK
1       Walmart
2       Microsoft
3       Apple
4       Toyota
5       Amazon
6       Google
7       Samsung
8       HP
9       IBM
10      Sony
Time taken: 0.05 seconds, Fetched: 10 row(s)
```
38. Prosiguiendo con los pasos seran netamente en la consola de Hive para crear la tabla transaccion en universal.
```bash
hive> CREATE TABLE U47774417_UNIVERSAL.TRANSACCION(
    > ID_PERSONA STRING,
    > ID_EMPRESA STRING,
    > MONTO DOUBLE,
    > FECHA STRING    
    > )
    > STORED AS PARQUET
    > LOCATION '/user/u47774417/ejercicio2/database/u47774417_universal/transaccion'
    > TBLPROPERTIES ("parquet.compression"="SNAPPY");
OK
Time taken: 0.043 seconds
```
39. Migrar la data de landing a universal implica un casteo de dato para que pase se pueda insertar con facilidad y una verificacion de id que evite la tomar la primera linea que contiene la cabera de las columnas.
```bash
hive> INSERT OVERWRITE TABLE U47774417_UNIVERSAL.TRANSACCION SELECT cast(ID_PERSONA AS STRING), cast(ID_EMPRESA AS STRING), cast(MONTO AS STRING), cast(FECHA AS STRING) FROM U47774417_LANDING.TRANSACCION WHERE ID_PERSONA != 'ID_PERSONA';
Query ID = u47774417_20200525102323_7f8a7fd3-3343-44eb-9699-711f7b543358
Total jobs = 3
Launching Job 1 out of 3
Number of reduce tasks is set to 0 since there is no reduce operator
Job running in-process (local Hadoop)
2020-05-25 10:23:41,687 Stage-1 map = 0%,  reduce = 0%
Ended Job = job_local1727880626_0005
Stage-4 is selected by condition resolver.
Stage-3 is filtered out by condition resolver.
Stage-5 is filtered out by condition resolver.
Moving data to: hdfs://vmcloudera01:8020/user/u47774417/ejercicio2/database/u47774417_universal/transaccion/.hive-staging_hive_2020-05-25_10-23-40_159_7599212353752398592-1/-ext-10000
Loading data to table u47774417_universal.transaccion
Table u47774417_universal.transaccion stats: [numFiles=1, numRows=235040, totalSize=764613, rawDataSize=940160]
MapReduce Jobs Launched: 
Stage-Stage-1:  HDFS Read: 11141448 HDFS Write: 6609276 SUCCESS
Total MapReduce CPU Time Spent: 0 msec
OK
Time taken: 2.796 seconds
```
40. Validemos la data en universal con un simple select.
```bash
hive> SELECT * FROM U47774417_UNIVERSAL.TRANSACCION LIMIT 10;
OK
18      3       1383.0  2018-01-21
30      6       2331.0  2018-01-21
47      2       2280.0  2018-01-21
28      1       730.0   2018-01-21
91      4       3081.0  2018-01-21
74      8       2409.0  2018-01-21
41      2       3754.0  2018-01-22
42      9       4079.0  2018-01-22
24      6       4475.0  2018-01-22
67      9       561.0   2018-01-22
Time taken: 0.044 seconds, Fetched: 10 row(s)
```
41. Prosiguiendo con los pasos seran netamente en la consola de Hive para crear la tabla transaccion_enriquecida en universal.
```bash
hive> CREATE TABLE U47774417_UNIVERSAL.TRANSACCION_ENRIQUECIDA(
    > ID_PERSONA INT,
    > NOMBRE_PERSONA STRING,
    > EDAD_PERSONA INT,
    > SALARIO_PERSONA DOUBLE,
    > TRABAJO_PERSONA STRING,
    > MONTO_TRANSACCION DOUBLE,
    > FECHA_TRANSACCION STRING,
    > EMPRESA_TRANSACCION STRING     
    > )
    > STORED AS PARQUET
    > LOCATION '/user/u47774417/ejercicio2/database/u47774417_universal/transaccion_enriquecida'
    > TBLPROPERTIES ("parquet.compression"="SNAPPY");
OK
Time taken: 0.108 seconds
```
42. Para formar la tabla transaccion enriquecidad basta con hacer las siguiente uniones y los siguientes casteos e inserciones.
```bash
hive> INSERT OVERWRITE TABLE U47774417_UNIVERSAL.TRANSACCION_ENRIQUECIDA 
    > SELECT CAST(T.ID_PERSONA AS INT),
    > CAST(P.NOMBRE AS STRING),
    > CAST(P.EDAD AS INT),
    > CAST(P.SALARIO AS DOUBLE),
    > CAST(E2.NOMBRE AS STRING),
    > CAST(T.MONTO AS DOUBLE),
    > CAST(T.FECHA AS STRING),
    > CAST(E.NOMBRE AS STRING)
    > FROM U47774417_UNIVERSAL.TRANSACCION T
    > INNER JOIN U47774417_UNIVERSAL.PERSONA P ON P.ID = T.ID_PERSONA
    > INNER JOIN U47774417_UNIVERSAL.EMPRESA E ON E.ID = T.ID_EMPRESA
    > INNER JOIN U47774417_UNIVERSAL.EMPRESA E2 ON E2.ID = P.ID_EMPRESA;
Query ID = u47774417_20200525104242_04bb84b3-1895-4146-9616-45a594b9be51
Total jobs = 1
Execution log at: /tmp/u47774417/u47774417_20200525104242_04bb84b3-1895-4146-9616-45a594b9be51.log
SLF4J: Class path contains multiple SLF4J bindings.
SLF4J: Found binding in [jar:file:/opt/cloudera/parcels/CDH-5.16.2-1.cdh5.16.2.p0.8/jars/parquet-pig-bundle-1.5.0-cdh5.16.2.jar!/shaded/parquet/org/slf4j/impl/Static
LoggerBinder.class]
SLF4J: Found binding in [jar:file:/opt/cloudera/parcels/CDH-5.16.2-1.cdh5.16.2.p0.8/jars/parquet-hadoop-bundle-1.5.0-cdh5.16.2.jar!/shaded/parquet/org/slf4j/impl/Sta
ticLoggerBinder.class]
SLF4J: See http://www.slf4j.org/codes.html#multiple_bindings for an explanation.
SLF4J: Actual binding is of type [shaded.parquet.org.slf4j.helpers.NOPLoggerFactory]
2020-05-25 10:42:10     Dump the side-table for tag: 1 with group count: 10 into file: file:/tmp/u47774417/745813a9-a9ca-4472-803d-eaf0d03991bb/hive_2020-05-25_10-42
-06_944_8711112305171575679-1/-local-10004/HashTable-Stage-8/MapJoin-mapfile81--.hashtable
2020-05-25 10:42:10     Dump the side-table for tag: 1 with group count: 10 into file: file:/tmp/u47774417/745813a9-a9ca-4472-803d-eaf0d03991bb/hive_2020-05-25_10-42
-06_944_8711112305171575679-1/-local-10004/HashTable-Stage-8/MapJoin-mapfile91--.hashtable
2020-05-25 10:42:10     Dump the side-table for tag: 1 with group count: 100 into file: file:/tmp/u47774417/745813a9-a9ca-4472-803d-eaf0d03991bb/hive_2020-05-25_10-4
2-06_944_8711112305171575679-1/-local-10004/HashTable-Stage-8/MapJoin-mapfile101--.hashtable
2020-05-25 10:42:10     End of local task; Time Taken: 1.306 sec.
Execution completed successfully
MapredLocal task succeeded
Launching Job 1 out of 1
Number of reduce tasks is set to 0 since there is no reduce operator
Job running in-process (local Hadoop)
2020-05-25 10:42:13,143 Stage-8 map = 0%,  reduce = 0%
2020-05-25 10:42:14,146 Stage-8 map = 100%,  reduce = 0%
Ended Job = job_local570030125_0009
Loading data to table u47774417_universal.transaccion_enriquecida
Table u47774417_universal.transaccion_enriquecida stats: [numFiles=1, numRows=235040, totalSize=1474314, rawDataSize=1880320]
MapReduce Jobs Launched: 
Stage-Stage-8:  HDFS Read: 14527254 HDFS Write: 8083698 SUCCESS
Total MapReduce CPU Time Spent: 0 msec
OK
Time taken: 7.436 seconds
```
43. Validemos la data en universal con un simple select.
```bash
hive> SELECT * FROM U47774417_UNIVERSAL.TRANSACCION_ENRIQUECIDA LIMIT 10;
OK
18      Owen    34      4759.0  Samsung 1383.0  2018-01-21      Apple
30      Clayton 52      9505.0  HP      2331.0  2018-01-21      Google
47      Vernon  35      7109.0  Sony    2280.0  2018-01-21      Microsoft
28      Stephen 53      9469.0  HP      730.0   2018-01-21      Walmart
91      Erica   32      8934.0  Google  3081.0  2018-01-21      Toyota
74      Kaitlin 56      6515.0  Sony    2409.0  2018-01-21      HP
41      Wynne   31      19522.0 Toyota  3754.0  2018-01-22      Microsoft
42      Wanda   42      5419.0  IBM     4079.0  2018-01-22      IBM
24      Amaya   24      1801.0  HP      4475.0  2018-01-22      Google
67      Buffy   38      15116.0 Microsoft       561.0   2018-01-22      IBM
Time taken: 0.049 seconds, Fetched: 10 row(s)
```