![][image-1]
### Actividad 1. Tarea Individual. Comandos.
### Pilar Bermejo 2 DAW
[[https://github.com/Pilupbp/despliegueAppWeb][1]
](#)
La administración de un servidor web y/o un servidor de aplicaciones requiere unos conocimientos básicos de comandos de consola que permite visualizar qué está pasando en nuestro servidor. Se pide practicar y crear una guía de uso para las siguientes problemáticas que nos podemos encontrar:
##### 1.	¿Cómo sabemos si tenemos conexión a internet? Pista: ifconfig, ping
##### 2.	¿Cómo sabemos si nuestro servidor es accesible desde Internet? Pista: ufw, netstat
##### 3.	¿Cómo sabemos a quién pertenece una dirección web (URL)? Pista: dig, nslookup
##### 4.	¿Cómo probamos que podemos acceder a un servidor? Pista: curl, wget
##### 5.	¿Qué otros comandos te han hecho falta?
Para toda la actividad se valorará el orden y la claridad de la documentación, así como la facilidad de uso.
Para la entrega, es necesaria la creación y subida a la plataforma de un pequeño documento formal sobre la actividad (portada, explicación, etc.) y una guía “how-to” que describa y permita resolver las preguntas planteadas en la actividad\*.
Nótese que más adelante se pedirá que se realicen tareas con un repositorio GIT que contenga la documentación de esta actividad. 
* Se recomienda crear un repositorio GitHub para almacenar la guía "how-to" en formato texto y/o Markdown.
Se considerará a la hora de evaluar la facilidad de uso de dicha guía que se explique de manera clara y sencilla:

1. Qué hace el comando
2. Cómo se usa
3. Por qué responde a la pregunta
4. Cómo se interpreta la salida
---- 

## GUÍA DE USO:

### 1. ¿CÓMO SABEMOS SI TENEMOS CONEXIÓN A INTERNET?

PING: Este comando ping es una de las herramientas básicas de diagnóstico de redes. 

##### 1.1 ¿Qué hace?
Permite comprobar si es posible establecer una conexión IP hacia un determinado host mediante el protocolo **ICMP (Protocolo de Mensajes de Control de Internet)**. De esta forma se puede determinar **si el ruteo de paquetes IP desde y hacia el host destino funciona correctamente.**

##### 1.2 ¿Cómo se usa?
*$ ping dominioejemplo.com* (podría ser también una IP si la conocemos.
- Especificando el número ECHO\_REQUEST: especificar el número de paquetes o solicitudes que el usuario desea realizar.
*$ ping –c  dominioejemplo.com*(\* es el número de pings que deseas realizar.)

- Con ping audible:  emite un pitido para verificar si el host está activo o no.
*$ ping –a dominioejemplo.com*
- Estableciendo intervalos: La opción –i permite al usuario establecer intervalos en segundos entre cada paquete.
*$ ping –i 2 –c 7 dominioejemplo.com*. Los números 2 y 7 los puedes cambiar por el tiempo que desees.
- Recibiendo solo el resumen del comando Ping de Linux:
*$ ping –c 7 –q dominioejemplo.com*. Usando -c 7 para realizar siete solicitudes, pero solo recibimos el resumen debido a que se agregó -q.
- Inundando la red con el comando Ping: permite a los usuarios enviar 100 o más paquetes por segundo, con la ayuda del siguiente comando:
*$ ping –f dominioejemplo.com*

##### 1.3	¿Por qué responde a la pregunta?
Porque si no tenemos ningún problema al ejecutarlo y se enviaron los paquetes y devolvieron es que tenemos conexión a internet y funciona perfectamente.

##### 1.4	¿Cómo se interpreta la salida?


![][image-2]

El resultado indica que se enviaron ocho paquetes de prueba de 64 bytes desde el host 216.58.211.238 y se devolvieron. TTL son las siglas de tiempo de vida, la latencia, que es el tiempo de conexión.

TRACEROUTE: Es otro comando que puede ser bastante útil en caso de que la **conexión con el host haya sido perdida**, porque podemos entender a qué punto la conexión ha sido perdida.


##### 1.1 ¿Qué hace?
Determina la ruta para alcanzar un host mediante el envío de paquetes “echo” de **protocolo ICMP** a la dirección de destino con un tiempo de vida TTL. Si el TTL antes de reenviarlo llega a 0 antes de alcanzar el destino nos devuelve el mensaje “Tiempo de espera agotado…”

##### 1.2 ¿Cómo se usa?

*$ traceroute dominioejemplo.com* ( o como en el ping, la IP si la conocemos) .

##### 1.3 ¿Por qué responde a la pregunta?
Porque podemos ver los diferentes **saltos en los diferentes nodos porque se establece la conexión**, si no se establece y no tuviéramos conexión a internet nos devolvería el mensaje mencionado anteriormente.

##### 1.4 ¿Cómo se interpreta la salida?\*\* ![][image-3]

Lo primero que hace el comando al ser ejecutado es mostrar la dirección **IP real del dominio de la web que hemos elegido.** Luego nos dice todos los nodos y routers por los que pasa el mensaje de prueba que hemos enviado, sus direcciones IP y la** latencia **de cada uno de ellos hasta llegar a su destino.


IFCONFIG:

##### 1.1 ¿Qué hace?
Muestra el estado de las **interfaces actualmente activas. **Información de la IP de cada interface y la dirección MAC, IPV6, IPV4…

##### 1.2 ¿Cómo se usa?
Si ponemos solo el **comando ifconfig** muestra el estado de todas las interfaces, incluso las que están inactivas. 
Si ponemos **ifconfig seguido del nombre de la interface**, solo muestra el estado de la interface que hemos indicado.

*$ ifconfig* Muestra el estado de todas las interfaces, incluso las que están inactivas.

*$ ifconfig lo0* (Accedemos a loopback 0, dirección especial que los hosts utilizan para dirigir el tráfico hacia ellos mismos)  


##### 1.3¿Por qué responde a la pregunta?
Porque sabemos si nos ha asignado una IP de Red y sabemos si el **puerto está activo y transmitiendo. **

##### 1.4 ¿Cómo se interpreta la salida?
![][image-4]
Puedo ver si el puerto está activo, la dirección IP que tiene y la MAC.

### 2. ¿CÓMO SABEMOS SI NUESTRO SERVIDOR ES ACCESIBLE DESDE INTERNET?

NETSTAT:

##### 1.1 ¿Qué hace?
Nos permite **supervisar las conexiones de red** tanto entrantes como salientes, así como ver tablas de enrutamiento, estadísticas de la interfaz, etc.

##### 1.2 ¿Cómo se usa?

*$ netstat -a* (lista todos los puertos TCP y UDP en estado de escucha)
*$ netstat -at* (solo puertos TCP)
*$ netstat -au * (solo puertos UDP)
*$ netstat -l * (Todas las conexiones en estado de escucha, con -lt todos los TCP y con -lu todos los UDP)


##### 1.3 ¿Por qué responde a la pregunta?** Nos indica qué **puertos están abiertos y si los programas están escuchando\*\* en los puertos permitiéndonos llevar un mejor control sobre estos. Nos ofrece una vía fácil para supervisar y solucionar problemas relacionados con la red y determinar el rendimiento del tráfico de red

##### 1.4 ¿Cómo se interpreta la salida?\*\* ![][image-5]
Tipo de protocolo, dirección local y remota y el Estado.

Podríamos utilizar otro comando para ver en que estado está nuestro firewall que nos permitirá establecer determinadas conexiones entrantes y salientes. Aunque mediante comandos no hemos podido realizarlo en el equipo. Podemos ver si lo tenemos activado y su configuración.

![][image-6]


UFW:
Comando que nos permite configurar reglas y administrar el firewall. Pero no hemos podido ejecutarlo en el Terminal de MAC.


### 3. ¿CÓMO SABEMOS A QUIÉN PERTENECE UNA DIRECCIÓN WEB (URL)?

HOST:

##### 1.1 ¿Qué hace?
**Devuelve los registros DNS** (habilita un enlace entre nombres de dominio y direcciones IP con la que están asociados) **configurados para un dominio.** No incluye los registros configurados para los subdominios.

##### 1.2 ¿Cómo se usa?

*$ host nombrededominio.com*

##### 1.3 ¿Por qué responde a la pregunta?
Porque con la información que devuelve **obtenemos la dirección IP **a la que está asociado ese dominio.

##### 1.4 ¿Cómo se interpreta la salida?
![][image-7]
Nos devuelve la dirección IP .

DIG:

##### 1.1 ¿Qué hace?
Ofrece la misma consulta que HOST pero con más información

##### 1.2 ¿Cómo se usa?

*$ dig nombrededominio.com*

##### 1.3 ¿Por qué responde a la pregunta?
A devolvernos los registros DNS podemos **ver a la IP a la que está asociado el dominio.**

##### 1.4 ¿Cómo se interpreta la salida?
![][image-8]


NSLOOKUP:

##### 1.1 ¿Qué hace?
Nos permite averiguar si el **servidor DNS que tenemos configurado está traduciendo correctamente las URL **a sus correspondientes direcciones IP.

##### 1.2 ¿Cómo se usa?
Primero ejecutamos el comando y a continuación las URL que queramos conocer las IP´s.

*$ nslookup*
*www.google.com*
*www.telefonicaeducaciondigital.com*

##### 1.3 ¿Por qué responde a la pregunta?
Nos da información sobre un dominio determinado.

##### 1.4 ¿Cómo se interpreta la salida?
![][image-9]
 

WHOIS:

##### 1.1 ¿Qué hace?
Sirve para para consultar la información sobre un dominio de Internet, **quién es el dueño del dominio**, cuándo expira el dominio, quién es el registrar o registrador del dominio, sus DNS-s, etc…

##### 1.2 ¿Cómo se usa?

*$ whois nombredeldominio.com*

##### 1.3 ¿Porqué responde a la pregunta?
Porque nos ofrece datos de quién es el dueño del dominio o donde está registrado, DNS, etc…

##### 1.4 ¿Cómo se interpreta la salida?
![][image-10]
Nos da la información del registrador con contactos administrativo y técnico, en esta ocasión nos devuelve Verisign que opera una gran variedad de infraestructuras de red que incluye dos de los trece servidores de internet.


### 4. ¿CÓMO PROBAMOS QUE PODEMOS ACCEDER A UN SERVIDOR?

CURL:
Lo primero es comprobar que Curl está instalado con el comando *$ curl --version*
![][image-11]

##### 1.1 ¿Qué hace?
La función de Curl es similar a la de Wget que veremos más adelante. Curl no es un software especializado en descargas, sino que está **diseñado para la comunicación general a través de redes**, por lo que ofrece aún más ventajas.

Con este comando podremos **comprobar si un servidor es accesible**, el fucionamiento es similar al del comando ping visto anteriormente, sin embargo, debido a los protocolos y las opciones disponibles, Curl se puede utilizar con más flexibilidad. Además, ping trabaja en la capa de Internet, mientras que Curl funciona sobre la capa de aplicación. Eso significa que ping verifica si la máquina está en red. En cambio, el Curl siguiente comprueba si un servidor reacciona y cómo lo hace.

##### 1.2 ¿Cómo se usa?

*$ curl nombrededominio.com* (es el uso más simple) Y obtenemos si podemos acceder a la URL.
Si el servidor no se puede conectar obtendremos un error del tipo (Could not resolve host)

Opciones de archivo de comandos CURL:
-O guarda el archivo en el directorio de trabajo actual con el mismo nombre de archivo que el remoto.
-o permite especificar un nombre de archivo o ubicación diferente.
Tiene más usos cuando tienes un servidor Proxy para hacer una solicitud GET o POST. También se puede usar para verificar que cookie se descargan en cualquier URL. También es compatible con FTP y se pueden descargar archivos de un servidor remoto.

*$ curl -v nombredominio.com* Si deseamos validar.

##### 1.3 ¿Por qué responde a la pregunta?
El comando nos dice si podemos acceder a la URL o si no podemos conectar al servidor.

##### 1.4 ¿Cómo se interpreta la salida?
![][image-12]
 
WGET:

##### 1.1 ¿Qué hace?
Podemos usarlo para **recuperar contenido** y archivos de varios servidores web.

##### 1.2 ¿Cómo se usa?
Uno de los ejemplos más básicos de este comando es **descargar una página completa** y almacenarla en nuestro directorio de trabajo actual.

Antes de eso hemos tenido que instalarlo mediante el comando *$ brew install wget*

*$ wget www.nombrededominio.com*

*$ wget -p www.nombrededominio.com* (descargamos una página completa con hojas de estilo imágenes de línea)

*$wget -r www.nombrededominio.com* (se descarga recursivamente hasta 5 niveles del sitio)

##### 1.3 ¿Por qué responde a la pregunta?
Porque nos muestra cómo podemos acceder a servidores a **descargar la información que necesitemos.** Aunque algunos servidores pueden hable bloqueado el acceso a wget.

##### 1.4 ¿Cómo se interpreta la salida?
![][image-13]
![][image-14]



### 5. ¿QUÉ OTROS COMANDOS TE HAN HECHO FALTA?

Los comandos que me han ido haciendo falta los he ido indicando a lo largo de la actividad.
Únicamente he utilizado el comando *clear* para limpiar la pantalla y realizar las capturas.



[1]:	https://github.com/Pilupbp/despliegueAppWeb

[image-1]:	computacion-nube.png width=800
[image-2]:	Imagen%201.png "1.1 Ping a google.com"
[image-3]:	Imagen%202.png "1.2 Traceroute a google.com"
[image-4]:	Imagen%203.png "1.3 Ifconfig"
[image-5]:	Imagen%204.png "1.4 Comando netstat -a"
[image-6]:	Imagen%2013.png "Firewall"
[image-7]:	Imagen%205.png "1.5 Comando Host"
[image-8]:	Imagen%206.png "1.6 Respuesta consulta dig"
[image-9]:	Imagen%207.png "1.7 Comando nslookup"
[image-10]:	Imagen%208.png "1.8 Whois"
[image-11]:	Imagen%209.png "1.9 Comprobando Curl"
[image-12]:	Imagen%2010.png "1.10 Datos de ejecución de Curl con -v"
[image-13]:	Imagen%2011.png "1.11 Comando Wget"
[image-14]:	Imagen%2012.png "1.12 Archivo descargado."