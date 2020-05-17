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