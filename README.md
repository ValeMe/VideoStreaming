# VideoStreaming

El streaming también llamado retransmisión o transmisión por secuencias consiste en la distribución o descarga de datos desde un proveedor o servidor en internet mientras el usuario hace uso de los datos en cuanto estos son descargados. Por lo tanto el usuario no necesita esperar hasta que la descarga sea completada para poder comenzar a utilizar los datos. Los servicios de streaming nos permiten ver u oír transmisiones en vivo y en directo a través de reproductores web dentro de una página o un dispositivo móvil.

¿Cómo funciona el streaming?

La tecnología de streaming trabaja utilizando un buffer de datos creado en la computadora del usuario, en este buffer se almacena la información de manera temporal mientras el usuario accede a la misma. Al finalizar la sesión de streaming el buffer es eliminado automáticamente. 

El streaming puede ser utilizado bajo demanda y uno de los usos más populares es el de las emisiones de radio online y tv online en directo a través de Internet.

En este tipo de streaming la persona que realiza la transmisión envía la señal de audio/video a un servidor de streaming (broadcast server) y este almacena la información en un buffer temporal.
Los oyentes se conectan al servidor de streaming a través de un enlace único, generalmente compuesto por un puerto en el servidor de streaming de manera que tienen acceso al flujo generado por el emisor y pueden así escuchar la señal de audio en directo o visualizar la transmisión de video.

Arquitectura base de un Streaming:

![corre](https://user-images.githubusercontent.com/62611526/79805095-04779680-832b-11ea-87d2-766494ee7053.png)


 
RTMP: Es un protocolo basado en TCP (igualmente puede funcionar con otros protocolos) que se utiliza para transmitir datos multimedia entre Flash Media Server y Flash Player. La mayor utilidad de RTMP es la transferencia a través de conexiones persistentes y baja latencia. RTMP usa un puerto exclusivo (1935) para transmisión de vídeo que permite al protocolo la transmisión de baja latencia del contenido. Para las transmisiones la información se divide en fragmentos y su tamaño es negociado dinámicamente entre cliente y servidor, estos fragmentos son llamados chunks. El tamaño máximo de cada fragmento de audio es de 64 bytes y 128 bytes para vídeo y la mayoría de otros tipos de información.

RTMP puede enviar y recibir los paquetes por canales virtuales específicos que son independientes el uno del otro. Por ejemplo, hay un canal para datos de flujo de audio, uno para vídeo, etc. Estos canales en una transmisión normal pueden estar activados de forma simultánea.


Arquitectura:

![Sin títulolj](https://user-images.githubusercontent.com/62611526/79805183-31c44480-832b-11ea-8f43-f02a607b6079.png)
 

Se creará una máquina Ubuntu Server en AWS Educate, a la cual se le deberá instalar el protocolo rtmp y un cliente desde el lado del usuario. Luego se configurará el rtmp para que esté constantemente escuchando, y cuando se genere una conexión entre éste y el cliente, todos los usuarios que conozcan la URL del sistema, podrán acceder a ver el streaming.

Seguridad:

Firewall, puertos abiertos:
SSH - 22
HTTPS - 443
HTTP - 80
RTMP(Custom TCP) - 1935

Lenguajes: Se tienen dos opciones, NGINX y Python

Luego de configurar el servidor rtmp se continúa con la configuración del cliente de streaming, en el cual irá toda la información de la dirección de publicación con la cual los usuarios podrán acceder al servicio.
Y finalmente se deberá embeber en una página WEB el video en html para que el usuario pueda ingresar sin ningún inconveniente al servicio.  

El servidor rtmp se pondrá en un contenedor (Docker), ya que esto hará más rápido el proceso y habrá escalabilidad. 




Bibliografía:

https://gospelidea.com/blog/como-funciona-el-streaming

https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=33&ved=2ahUKEwiO6c3l7vfoAhUKVd8KHXQkC2YQFjAgegQIBBAB&url=http%3A%2F%2Fprofesores.elo.utfsm.cl%2F~agv%2Felo322%2F1s19%2Fprojects%2Freports%2FProtocolo_RTMP.pdf&usg=AOvVaw3i-ZwWEZVJtI-bY2tmFYyb
