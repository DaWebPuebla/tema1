# El protocolo HTTP

Antes de entrar en más materia, vamos a hablar de como realmente funciona la web; ya sea a través de un navegador o de una aplicación móvil, la comunicación entre el cliente y el servidor se realiza a través del protocolo HTTP (Hypertext Transfer Protocol) y la llamada World Wide Web (WWW).

Cuando se accede a una página web, el navegador envía una solicitud HTTP al servidor web que aloja la página. El servidor procesa la solicitud y devuelve una respuesta HTTP que contiene el contenido de la página web solicitada. Este proceso se repite cada vez que se accede a una nueva página o se realiza una acción en la web.

En este apartado veremos como funciona el protocolo HTTP y como se estructura la comunicación entre el cliente y el servidor, incluyendo los métodos HTTP, los códigos de estado y los encabezados de solicitud y respuesta.

## URL (Uniform Resource Locator)

Antes de profundizar en el protocolo HTTP, es importante entender qué es una URL (Uniform Resource Locator) y cómo se utiliza para identificar recursos en la web. Una URL es una dirección que se utiliza para acceder a un recurso específico en Internet, como una página web, una imagen o un archivo.

Normalmente una URL tiene el siguiente formato:

```
http://www.ejemplo.com:80/ruta/al/recurso?parametro1=valor1&parametro2=valor2#fragmento
```

Esta URL se compone de varias partes:

* **Protocolo**: Indica el protocolo de comunicación que se utilizará para acceder al recurso. En este caso, es `http`, pero también puede ser `https` para conexiones seguras.
* **Dominio**: Es el nombre del servidor que aloja el recurso. En este caso, es `www.ejemplo.com`. Normalmente se identifica por el `fqdn` (Fully Qualified Domain Name) que es el nombre completo del dominio.
* **Puerto**: Es el número de puerto que se utilizará para la comunicación. En este caso, es `80`, que es el puerto predeterminado para HTTP. Si no se especifica un puerto, se utilizará el puerto predeterminado según el protocolo. En caso de que el puerto sea el predeterminado, no es necesario especificarlo en la URL.
* **Ruta**: Es la ubicación del recurso en el servidor. En este caso, es `/ruta/al/recurso`. La ruta puede incluir subdirectorios y el nombre del archivo que se desea acceder.
* **Parámetros de consulta**: Son pares clave-valor que se utilizan para enviar información adicional al servidor. En este caso, son `parametro1=valor1` y `parametro2=valor2`. Los parámetros de consulta se separan del resto de la URL mediante el signo de interrogación `?` y se separan entre sí mediante el signo `&`.
* **Fragmento**: Es una referencia a una sección específica del recurso. En este caso, es `#fragmento`. El fragmento se utiliza para navegar a una parte específica de la página web y no se envía al servidor en la solicitud HTTP.

!!! info
    Una URL también es identificado como URI (Uniform Resource Identifier), que es un identificador más general que puede incluir tanto URLs como URNs (Uniform Resource Names). En este curso, nos centraremos principalmente en las URLs, ya que son las más utilizadas para acceder a recursos en la web.