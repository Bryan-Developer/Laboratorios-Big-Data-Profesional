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
22. Ahora se procede a cambiar los permisos de carpetas y archivos previamente agregados o creados, se usara el siguiente comando ```hdfs dfs -chmod [codigos] [Ruta-del-archivo-hdfs]``` y para dar permisos de lectura-escritura-ejecucion, para cambiar los dueños y grupos del archivo ```hdfs dfs -chwon [-R:opcional-recursividad] [usuario:grupo] [Ruta-del-archivo-hdfs]```
23. Ejecuta el siguiente comando ```hdfs dfs -chown usuario5:grupoA /user/u47774417/ejercicio1/data1/file.csv```.
24. Ejecuta el siguiente comando ```hdfs dfs -chown -R usuario2:grupoK /user/u47774417/ejercicio1/data2```.
25. Ejecuta el siguiente comando ```hdfs dfs -chmod 755 /user/u47774417/ejercicio1/data1/file.csv```.
26. Ejecuta el siguiente comando ```hdfs dfs -chmod 700 /user/u47774417/ejercicio1/data1/voidfile.csv```.
27. Ejecuta el siguiente comando ```hdfs dfs -chmod -R 777 /user/u47774417/ejercicio1/data2```.
28. Ejecute el siguiente comando para visualizar la configuracion de permisos, dueños y grupos que previamente se realizo ```hdfs dfs -ls -R /user/u47774417```
```bash
[hdfs@vmcloudera01 u47774417]$ hdfs dfs -ls -R /user/u47774417
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
-rwxr-xr-x+  3 usuario5  grupoA             0 2020-05-17 08:33 /user/u47774417/ejercicio1/data1/file.csv
-rwx------+  3 u47774417 u47774417          0 2020-05-17 08:33 /user/u47774417/ejercicio1/data1/voidfile.csv
drwxrwxrwx+  - usuario2  grupoK             0 2020-05-17 08:19 /user/u47774417/ejercicio1/data2
drwxrwxrwx+  - usuario2  grupoK             0 2020-05-17 08:33 /user/u47774417/ejercicio1/data2/2017-01-27
-rwxrwxrwx+  3 usuario2  grupoK             0 2020-05-17 08:33 /user/u47774417/ejercicio1/data2/2017-01-27/file.csv
drwxrwxrwx+  - usuario2  grupoK             0 2020-05-17 08:33 /user/u47774417/ejercicio1/data2/2017-01-28
-rwxrwxrwx+  3 usuario2  grupoK             0 2020-05-17 08:33 /user/u47774417/ejercicio1/data2/2017-01-28/file.csv
drwxrwxrwx+  - usuario2  grupoK             0 2020-05-17 08:19 /user/u47774417/ejercicio1/data2/2017-01-29
drwxr-xr-x+  - u47774417 u47774417          0 2020-05-17 08:16 /user/u47774417/ejercicio1/data3
```
## Segunda parte - Comandos avanzados de gestion de archivos en hdfs
1. Con el siguiente comando podemos cambiar los permisos de un usuario ```hdfs dfs -setfacl -R -m [user:nombre-usuario:rwx] [ruta/hdfs]```.
2. Con el siguiente comando podemos cambiar los permisos de un grupo ```hdfs dfs -setfacl -R -m [group:nombre-grupo:rwx] [ruta/hdfs]```.
3. Ejecuta el siguiente comando ```hdfs dfs -setfacl -R -m user:usuarioA:r-- /user/u47774417/ejercicio1/carpeta2```
4. Ejecuta el siguiente comando ```hdfs dfs -setfacl -R -m user:usuarioB:rw- /user/u47774417/ejercicio1/carpeta2```
5. Ejecuta el siguiente comando ```hdfs dfs -setfacl -R -m user:usuarioC:rwx /user/u47774417/ejercicio1/carpeta2```
6. Ejecuta el siguiente comando ```hdfs dfs -setfacl -R -m group:grupoK:r-- /user/u47774417/ejercicio1/carpeta2```
7. Ejecuta el siguiente comando para visualizar los cambios previamente hechos ```hdfs dfs -getfacl /user/u47774417/ejercicio1/carpeta2```
```bash
# file: /user/u47774417/ejercicio1/carpeta2
# owner: u47774417
# group: u47774417
user::rwx
user:jupyter:rwx
user:usuarioA:r--
user:usuarioB:rw-
user:usuarioC:rwx
group::r-x
group:grupoK:r--
mask::rwx
other::r-x
default:user::rwx
default:user:jupyter:rwx
default:group::r-x
default:mask::rwx
default:other::r-x
```
8. Con el siguiente comando se establece por defecto los permisos a los proximos archivos que sean ingestados en un directorio ```hdfs dfs -setfacl -R -m default:user:usuarioA:r-- /user/u47774417/ejercicio1/carpeta2```
9. Ejecuta el siguiente comando para visualizar los cambios previamente hechos ```hdfs dfs -getfacl /user/u47774417/ejercicio1/carpeta2```
```bash
[u47774417@vmcloudera01 ~]$ hdfs dfs -getfacl /user/u47774417/ejercicio1/carpeta2
# file: /user/u47774417/ejercicio1/carpeta2
# owner: u47774417
# group: u47774417
user::rwx
user:jupyter:rwx
user:usuarioA:r--
user:usuarioB:rw-
user:usuarioC:rwx
group::r-x
group:grupoK:r--
mask::rwx
other::r-x
default:user::rwx
default:user:jupyter:rwx
default:user:usuarioA:r--
default:group::r-x
default:mask::rwx
default:other::r-x
```
10. Para validar que la informacion del archivo no se haya perdido haremos una ingesta de un archivo luego validaremos sun espacio con cksum en linux y luego al archivo en hdfs.
 ```bash
 [u47774417@vmcloudera01 ~]$ hdfs dfs -put transacciones.data /user/u47774417
[u47774417@vmcloudera01 ~]$ cksum transacciones.data 
3695388698 5129134 transacciones.data
[u47774417@vmcloudera01 ~]$ hdfs dfs -cat /user/u47774417/transacciones.data | cksum
3695388698 5129134
 ```
 11. como podemos ver no se ha perdido ni un solo bit en la transeccion.
 12. Listemos los pesos de cualquier carpeta con el siguiente ```hdfs dfs -du -s -h [ruta-hdfs] ```.
 13. Ejecutemos el siguiente comand ```hdfs dfs -du -s -h /user/u47774417``` 
```bash
 [u47774417@vmcloudera01 ~]$ hdfs dfs -du -s -h /user/u47774417
4.9 M  14.7 M  /user/u47774417
```
14. Como se observa se suma todos los pesos dentro de la carpeta que hemos apuntado.
15. Visualizemos el numero de replicas del archivo ```transacciones.data```, se puede hacer con el comando listar de hdfs pero el de modificar el numero de replicas se hace con ```hdfs dfs -setrep -w 5 -R [ruta-hdfs]``` con la opcion ```-R``` se hace de manera recursiva pero tambien se puede con un archivo.
```bash
[u47774417@vmcloudera01 ~]$ hdfs dfs -setrep -w 5 -R /user/u47774417/transacciones.data
[u47774417@vmcloudera01 ~]$ hdfs dfs -ls /user/u47774417/transacciones.data
-rw-r--r--+  5 u47774417 u47774417    5129134 2020-05-17 09:22 /user/u47774417/transacciones.data
```
16. Otra aplicacion de hdfs nos permite setear el tamaño del bloque hdfs al momento de hacer la ingesta del archivo esto se pude hacer para archivos pequeños, se hace con el siguiente comando ```hdfs dfs -D dfs.blocksize=102400 -put [ruta-linux] [ruta-hdfs]``` y con el siguiente comando vamos a validar el tamaño del bloque ```hdfs fsck [ruta-hdfs] -files -blocks```
```bash
[u47774417@vmcloudera01 ~]$ hdfs dfs -D dfs.blocksize=104857600 -put transacciones-2018-01-23.data /user/u47774417
[u47774417@vmcloudera01 ~]$ hdfs fsck /user/u47774417/transacciones-2018-01-23.data -files -blocks
Connecting to namenode via http://vmcloudera01:50070/fsck?ugi=u47774417&files=1&blocks=1&path=%2Fuser%2Fu47774417%2Ftransacciones-2018-01-23.data
FSCK started by u47774417 (auth:SIMPLE) from /10.0.0.4 for path /user/u47774417/transacciones-2018-01-23.data at Sun May 17 09:52:16 UTC 2020
/user/u47774417/transacciones-2018-01-23.data 1336418 bytes, 1 block(s):  Under replicated BP-729111694-10.0.0.4-1581184687852:blk_1073827385_86618. Target Replicas is 3 but found 1 live replica(s), 0 decommissioned replica(s), 0 decommissioning replica(s).
0. BP-729111694-10.0.0.4-1581184687852:blk_1073827385_86618 len=1336418 Live_repl=1

Status: HEALTHY
 Total size:    1336418 B
 Total dirs:    0
 Total files:   1
 Total symlinks:                0
 Total blocks (validated):      1 (avg. block size 1336418 B)
 Minimally replicated blocks:   1 (100.0 %)
 Over-replicated blocks:        0 (0.0 %)
 Under-replicated blocks:       1 (100.0 %)
 Mis-replicated blocks:         0 (0.0 %)
 Default replication factor:    3
 Average block replication:     1.0
 Corrupt blocks:                0
 Missing replicas:              2 (66.666664 %)
 Number of data-nodes:          1
 Number of racks:               1
FSCK ended at Sun May 17 09:52:16 UTC 2020 in 14 milliseconds


The filesystem under path '/user/u47774417/transacciones-2018-01-23.data' is HEALTHY
```