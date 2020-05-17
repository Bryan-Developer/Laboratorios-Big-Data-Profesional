# Laboratorio Hadoop
## Primera Parte - Creacion y Gestion de Carpetas
1. Crea una estructura de carpetas con el usuario de su preferencia dentro de hadoop en la siguiente ruta ```hdfs dfs -ls -R /user/u47774417```.
2. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/carpeta1```.
3. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/carpeta2```.
4. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/carpeta3```.
5. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/data1```.
6. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/data2```.
7. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/data3```.
8. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/carpeta1/subcarpeta1```.
9. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/carpeta1/subcarpeta2```.
10. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/carpeta1/subcarpeta3```.
11. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/data2/2017-01-27```.
12. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/data2/2017-01-28```.
13. Ejecute el siguiente comando ```hdfs dfs -mkdir -p /user/u47774417/ejercicio1/data2/2017-01-29```.
14. Ejecute el siguiente comando para visualizar la siguiente estrucutra ```hdfs dfs -ls -R /user/u47774417```
```bash
[u47774417@vmcloudera01 ~]$ hdfs dfs -ls -R /user/u47774417
drwx------+  - u47774417 u47774417          0 2020-05-17 08:01 /user/u47774417/.Trash
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:16 /user/u47774417/ejercicio1
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:17 /user/u47774417/ejercicio1/carpeta1
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:17 /user/u47774417/ejercicio1/carpeta1/subcarpeta1
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:17 /user/u47774417/ejercicio1/carpeta1/subcarpeta2
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:17 /user/u47774417/ejercicio1/carpeta1/subcarpeta3
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:15 /user/u47774417/ejercicio1/carpeta2
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:15 /user/u47774417/ejercicio1/carpeta3
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:15 /user/u47774417/ejercicio1/data1
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:19 /user/u47774417/ejercicio1/data2
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:19 /user/u47774417/ejercicio1/data2/2017-01-27
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:19 /user/u47774417/ejercicio1/data2/2017-01-28
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:19 /user/u47774417/ejercicio1/data2/2017-01-29
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:16 /user/u47774417/ejercicio1/data3
```
15. Ejecuta la ingesta de los siguientes archivos con el comando ```hdfs dfs -put [Ruta en Linux] [Ruta en hdfs]```
```bash
[u47774417@vmcloudera01 ~]$ ls
empresa.data  file.csv  persona.data  voidfile.csv
```
16. Ejecuta el siguiente comando ```hdfs dfs -put persona.data /user/u47774417/ejercicio1/carpeta1/subcarpeta1```
17. Ejecuta el siguiente comando ```hdfs dfs -put empresa.data /user/u47774417/ejercicio1/carpeta2```
18. Ejecuta el siguiente comando ```hdfs dfs -put file.csv voidfile.csv /user/u47774417/ejercicio1/data1```
19. Ejecuta el siguiente comando ```hdfs dfs -put file.csv /user/u47774417/ejercicio1/data2/2017-01-27```
19. Ejecuta el siguiente comando ```hdfs dfs -put file.csv /user/u47774417/ejercicio1/data2/2017-01-28```
20. Ejecute el siguiente comando para visualizar la siguiente estrucutra y los archivos previamente ingestados ```hdfs dfs -ls -R /user/u47774417```
```bash
[u47774417@vmcloudera01 ~]$ hdfs dfs -ls -R /user/u47774417
drwx------+  - u47774417 u47774417          0 2020-05-17 08:01 /user/u47774417/.Trash
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:16 /user/u47774417/ejercicio1
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:17 /user/u47774417/ejercicio1/carpeta1
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:33 /user/u47774417/ejercicio1/carpeta1/subcarpeta1
-rw-r--r--+  3 u47774417 u47774417       7282 2020-05-17 08:33 /user/u47774417/ejercicio1/carpeta1/subcarpeta1/persona.data
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:17 /user/u47774417/ejercicio1/carpeta1/subcarpeta2
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:17 /user/u47774417/ejercicio1/carpeta1/subcarpeta3
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:33 /user/u47774417/ejercicio1/carpeta2
-rw-r--r--+  3 u47774417 u47774417        105 2020-05-17 08:33 /user/u47774417/ejercicio1/carpeta2/empresa.data
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:15 /user/u47774417/ejercicio1/carpeta3
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:33 /user/u47774417/ejercicio1/data1
-rw-r--r--+  3 u47774417 u47774417          0 2020-05-17 08:33 /user/u47774417/ejercicio1/data1/file.csv
-rw-r--r--+  3 u47774417 u47774417          0 2020-05-17 08:33 /user/u47774417/ejercicio1/data1/voidfile.csv
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:19 /user/u47774417/ejercicio1/data2
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:33 /user/u47774417/ejercicio1/data2/2017-01-27
-rw-r--r--+  3 u47774417 u47774417          0 2020-05-17 08:33 /user/u47774417/ejercicio1/data2/2017-01-27/file.csv
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:33 /user/u47774417/ejercicio1/data2/2017-01-28
-rw-r--r--+  3 u47774417 u47774417          0 2020-05-17 08:33 /user/u47774417/ejercicio1/data2/2017-01-28/file.csv
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:19 /user/u47774417/ejercicio1/data2/2017-01-29
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:16 /user/u47774417/ejercicio1/data3
```