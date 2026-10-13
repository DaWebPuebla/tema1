# Entornos Virtuales

Por último, vamos a hablar sobre los entornos virtuales, que son una herramienta fundamental para el desarrollo y despliegue de aplicaciones web. Ya sea a través de diferentes espacios en nuestro servidor o mediante contenedores, los entornos virtuales permiten aislar y gestionar las dependencias de nuestras aplicaciones web, garantizando que funcionen correctamente en diferentes entornos y evitando conflictos entre librerías y versiones.

En un mismo servidor, podemos tener múltiples aplicaciones web que requieren diferentes versiones de librerías o dependencias. Los entornos virtuales nos permiten crear un espacio aislado para cada aplicación, donde podemos instalar las dependencias necesarias sin afectar a otras aplicaciones en el mismo servidor.

## Virtual Hosts

Los Virtual Hosts son una característica de los servidores web que permiten alojar múltiples sitios web en un mismo servidor físico o virtual. Cada sitio web puede tener su propio dominio, configuración y contenido, lo que permite una gestión más eficiente de los recursos del servidor y una mejor experiencia para los usuarios finales.

Un Virtual Host se configura mediante un archivo de configuración específico para cada sitio web, donde se definen parámetros como el nombre del dominio, la ruta del directorio raíz, las reglas de redirección y las configuraciones de seguridad. Esto permite que cada sitio web funcione de manera independiente y tenga su propia configuración personalizada.

Normalmente, cada Virtual Host se configura en un archivo de configuración separado, que se encuentra en la carpeta de configuración del servidor web. Por ejemplo, en Apache, los archivos de configuración de los Virtual Hosts suelen encontrarse en la carpeta `/etc/apache2/sites-available/` en sistemas basados en Debian/Ubuntu, o en la carpeta `/etc/httpd/conf.d/` en sistemas basados en Red Hat/CentOS/Fedora.

### Ejercicio 4: Añadir varios Virtual Host en Apache

Vamos a realizar un ejercicio donde se deben de poder gestionar 2 webs en distintos dominios, para ello vamos a crear dos Virtual Host en Apache. A continuación, se muestra un ejemplo de cómo configurar dos Virtual Hosts en Apache:

Vamos a crear dos archivos de configuración para los Virtual Hosts, uno para cada sitio web. Los archivos se llamarán `ejemplo1.conf` y `ejemplo2.conf`, y se guardarán en la carpeta `/etc/apache2/sites-available/`.


Ambos archivos tendran la configuración básica de un Virtual Host, con los nombres de dominio `www.ejemplo1.com` y `www.ejemplo2.com`, y las rutas de los directorios raíz `/var/www/ejemplo1` y `/var/www/ejemplo2`, respectivamente.

!!! note
    Recuerda crear los ficheros 'index.html' en los directorios raíz de cada sitio web, para que Apache pueda servir contenido cuando se acceda a los dominios configurados. Puedes usar la siguiente plantilla básica para el contenido de los archivos 'index.html':

    ```html
    <!DOCTYPE html>
    <html lang="es">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Ejemplo 1</title>
    </head>
    <body>
        <h1>Bienvenido a Ejemplo 1</h1>
    </body>
    </html>
    ```
    Puedes reemplazar el contenido de la plantilla con el contenido que desees para cada sitio web, asegurándote de crear un archivo 'index.html' en cada directorio raíz correspondiente.

Recuerda crear los directorios raíz de los sitios web y colocar los archivos de contenido en ellos antes de habilitar los Virtual Hosts.

Cada archivo de configuración de Virtual Host debe tener la siguiente estructura básica:

```apache
<VirtualHost *:80>
    ServerName www.ejemplo1.com
    DocumentRoot /var/www/ejemplo1
    <Directory /var/www/ejemplo1>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

y para Ejemplo2:

```apache
<VirtualHost *:80>
    ServerName www.ejemplo2.com
    DocumentRoot /var/www/ejemplo2
    <Directory /var/www/ejemplo2>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

Para habilitar el Virtual Host en Apache, podemos utilizar el siguiente comando en sistemas basados en Debian/Ubuntu:

```bash
sudo a2ensite ejemplo1.conf
```

Recuerda que este fichero debe guardarse en la ruta `/etc/apache2/sites-available/` y debe tener la extensión `.conf`. Una vez habilitado el Virtual Host, debemos reiniciar Apache para que los cambios tengan efecto:

```bash
sudo systemctl restart apache2
```

Para ayudarnos a gestionar los dominios, podemos añadir entradas en el archivo `/etc/hosts` de nuestro sistema local para que apunten a la dirección IP del servidor donde se encuentran los Virtual Hosts. Por ejemplo:

```
127.0.0.1 www.ejemplo1.com
127.0.0.1 www.ejemplo2.com
```

Una vez hecho esto, deberíamos poder acceder a los sitios web `www.ejemplo1.com` y `www.ejemplo2.com` desde nuestro navegador, siempre y cuando el servidor Apache esté en funcionamiento y los Virtual Hosts estén correctamente configurados.

## Máquinas Virtuales

Las máquinas virtuales son entornos virtuales que permiten ejecutar un sistema operativo completo y sus aplicaciones en un entorno aislado dentro de un servidor físico. Cada máquina virtual tiene su propio sistema operativo, recursos de hardware y configuraciones, lo que permite ejecutar múltiples sistemas operativos y aplicaciones en un mismo servidor físico sin interferencias entre ellos.

Se pueden crear varias máquinas virtuales en un mismo servidor físico utilizando software de virtualización, como VMware, VirtualBox o KVM. Cada máquina virtual puede tener su propio sistema operativo y configuraciones, lo que permite ejecutar diferentes aplicaciones web con diferentes dependencias y versiones de librerías en el mismo servidor físico.

Además, cada máquina virtual puede configurarse con diferentes recursos de hardware, como memoria RAM, CPU y almacenamiento, lo que permite adaptar el entorno virtual a las necesidades específicas de cada aplicación web. Esto facilita la gestión de recursos y garantiza un rendimiento óptimo para cada aplicación web alojada en el servidor.

## Contenedores

Otro de los enfoques modernos para gestionar entornos virtuales es el uso de contenedores, como Docker. Los contenedores permiten empaquetar una aplicación junto con todas sus dependencias y configuraciones en un único paquete que puede ejecutarse de manera consistente en cualquier entorno.

Un contenedor es una unidad ligera y portátil que encapsula una aplicación y su entorno de ejecución, lo que permite que la aplicación se ejecute de manera aislada del sistema operativo subyacente. Esto facilita el despliegue y la gestión de aplicaciones web, ya que los contenedores pueden ejecutarse en diferentes entornos sin preocuparse por las diferencias en las configuraciones del sistema.

### Ventajas de los contenedores

Los contenedores ofrecen varias ventajas en comparación con los entornos virtuales tradicionales, como:

* **Portabilidad**: Los contenedores pueden ejecutarse en cualquier sistema que tenga un motor de contenedores compatible, lo que facilita el despliegue de aplicaciones en diferentes entornos, como desarrollo, pruebas y producción.
* **Aislamiento**: Cada contenedor se ejecuta de manera aislada del sistema operativo y de otros contenedores, lo que permite evitar conflictos entre aplicaciones y garantizar que cada aplicación tenga su propio entorno de ejecución.
* **Eficiencia**: Los contenedores son más ligeros que las máquinas virtuales tradicionales, ya que comparten el mismo núcleo del sistema operativo y utilizan menos recursos, lo que permite ejecutar más contenedores en el mismo hardware y mejorar la eficiencia del sistema.
* **Escalabilidad**: Los contenedores facilitan la escalabilidad de las aplicaciones web, ya que se pueden crear y destruir contenedores de manera rápida y sencilla para adaptarse a cambios en la demanda de tráfico, lo que permite mejorar la disponibilidad y el rendimiento de las aplicaciones web.

En el siguiente temna, vamos a explorar cómo utilizar contenedores para desplegar aplicaciones web y cómo aprovechar las ventajas de los contenedores para mejorar la eficiencia y la escalabilidad de nuestras aplicaciones.

## Despliegue en la Nube

El despliegue de aplicaciones web en la nube se ha convertido en una práctica común en el desarrollo de software moderno. La nube ofrece una infraestructura flexible y escalable que permite a los desarrolladores desplegar y gestionar aplicaciones web de manera eficiente, sin preocuparse por la gestión de servidores físicos o la configuración del hardware.

A través de máquinas virtuales, contenedores y servicios de plataforma como servicio (PaaS), los desarrolladores pueden desplegar aplicaciones web en la nube de manera rápida y sencilla, aprovechando las ventajas de la infraestructura en la nube para mejorar la disponibilidad, el rendimiento y la escalabilidad de sus aplicaciones.

Se pueden utilizar diferentes proveedores de servicios en la nube, como Amazon Web Services (AWS), Microsoft Azure o Google Cloud Platform (GCP), para desplegar aplicaciones web en la nube. Cada proveedor ofrece una amplia gama de servicios y herramientas para facilitar el despliegue y la gestión de aplicaciones web, lo que permite a los desarrolladores centrarse en la creación de aplicaciones innovadoras y funcionales.

En siguientes temas, vamos a explorar cómo desplegar aplicaciones web en la nube utilizando diferentes servicios y herramientas, y cómo aprovechar las ventajas de la nube para mejorar el rendimiento, la escalabilidad y la disponibilidad de las aplicaciones web.