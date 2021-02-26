[https://github.com/Pilupbp/Despliegues ](#)

![](Imagen%201.png)



**Actividad 4. Tarea Individual. GIT**

![](Imagen%202.png)

Se pide que el alumno versiones y recupere los documentos creados en las actividades anteriores. Para ello se hará uso del repositorio GIT creado al inicio de las actividades. Se deberán crear:
1.	Una etiqueta que contenga la última versión de todos los documentos
2.	Una etiqueta que contenga la primera versión de cada documento
3.	Una rama que contenga únicamente la última versión de todos los documentos sin ningún commit histórico.
4.	Una rama que contenga la primera versión de cada documento
5.	Un fichero README.md que contenga la historia de commits del repositorio (formato de una línea)
Consideraciones
Para toda la actividad se valorará el orden y la claridad de la documentación, así como la facilidad de uso.
Para la entrega, se subirá un fichero comprimido con el repositorio GIT a la plataforma.
Para la entrega, es necesario la creación de un pequeño documento formal sobre la actividad (portada, explicación, etc.), indicando los comandos ejecutados para cada consulta y una captura de pantalla de la salida.


____________________________________________________________

Lo primero de todo es comprobar que tenemos instalado en nuestro terminal GIT.

![](Imagen%203.png)

Iniciamos GIT

![](Imagen%204.png)
 

Clonamos el repositorio en nuestro terminal en el que hemos subido todas las actividades y tenemos varios commits hechos.


![](Imagen%205.png) 


Entramos en nuestro repositorio:

![](Imagen%206.png)
 
Comprobamos el historial de nuestro repositorio.

 
![](Imagen%207.png)

Ahora vamos a crear una etiqueta v3.3 que contenga la última versión de la actividad 3.
Etiqueta v.2.3 que contenga la última versión de la actividad 2.
Etiqueta v.1.3 que contenga la última versión de la actividad 1.

![](Imagen%208.png)

Y las subimos:

![](Imagen%209.png) 

Hacemos lo mismo, pero que contenga la primera versión de todos los documentos:
v1.1 primera versión actividad 1
v2.1 primera versión actividad 2
v3.1 primera versión actividad 3

![](Imagen%2010.png)
 
Listamos nuestras etiquetas

![](Imagen%2011.png)

Podemos ver las etiquetas en las diferentes versiones:

![](Imagen%2012.png) 

Ahora vamos a realizar  una rama que contenga la última versión sin ningún commit histórico.
Lo primero que hacemos es crear la rama donde queremos llevar nuestros commits.

![](Imagen%2013.png) 

Creamos un commit para insertar contenido.

![](Imagen%2014.png) 

Miramos en que rama nos encontramos  y vemos que estamos en la rama principal (Main) donde tenemos nuestros commits.

![](Imagen%2015.png)
 

Con git log obtenemos es una lista de nuestros commits, con sus respectivos códigos SHA. 

![](Imagen%2016.png) 

Vamos a copiar el código SHA del commit que queremos mover a nuestra rama.

**8dc9be8734bc48553e382edb985d07067c8f8551 – Última versión act3**

**518817d60a6b2c6cec2afbe125e0663a2c1d8a19 – Última versión act2**

**861b3291848f3fce846f3f72e1277217366abac0 – Última versión act1**

Y regresamos a la rama lastversions que es donde queremos poner los commits.

![](Imagen%2017.png)
 


Usamos cherry-pick seguido del SHA.

Act1

![](Imagen%2018.png) 

Act2

![](Imagen%2019.png) 

Act3

![](Imagen%2020.png) 


Agregamos los cambios:

![](Imagen%2021.png) 


Subimos al repositorio remoto.

![](Imagen%2022.png) 

Y comprobamos que efectivamente nos ha subido los 3 commits de las últimas versiones.

![](Imagen%2023.png)
 

Ahora tenemos que meter en otra rama, las primeras versiones.
Por lo que creamos otra rama huérfana con firstversions y creamos los commit que encontraremos en el git log con primeras versiones.

**c1a3b38536aaf2d814433e21e97f87f33cf4d549 – Primera subida Act3**

**0257cd95e13425ac7fab99e27e03b5daf13dc238 – Primera subida Act2**

**bbe8526eeaecc77eb754a17ba9939340b88d86fc – Primera subida Act1**

Repetimos los pasos anteriores:

![](Imagen%2024.png) 

![](Imagen%2025.png)

![](Imagen%2026.png)

Ahora vamos a hacer una historia de commits, nos vamos a crear un alias para no poner el comando completo.

![](Imagen%2027.png)
 
Vamos a meter estos commits en un fichero README.MD

![](Imagen%2028.png) 

Descargamos a nuestro repositorio local.

![](Imagen%2029.png)
