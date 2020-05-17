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