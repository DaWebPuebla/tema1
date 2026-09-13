# Configuración de Apache

En la anterior sección, hemos instalado Apache en nuestro servidor Linux. Ahora vamos a configurar Apache para que pueda servir nuestras aplicaciones web de manera eficiente y segura.

## Inicio y parada del servicio de Apache

Vamos a comenzar por lo básico: cómo iniciar y detener el servicio de Apache. Para ello, utilizaremos los siguientes comandos:

```bash
# Para iniciar el servicio de Apache
sudo systemctl start apache2  # En Debian/Ubuntu
sudo systemctl start httpd    # En Red Hat/CentOS/Fedora
```

Para detener el servicio de Apache, utilizaremos los siguientes comandos:

```bash
# Para detener el servicio de Apache
sudo systemctl stop apache2   # En Debian/Ubuntu
sudo systemctl stop httpd     # En Red Hat/CentOS/Fedora
```

Y también podemos reiniciar el servicio de Apache utilizando los siguientes comandos:

```bash
# Para reiniciar el servicio de Apache
sudo systemctl restart apache2  # En Debian/Ubuntu
sudo systemctl restart httpd    # En Red Hat/CentOS/Fedora
```

Además, podemos recargar la configuración de Apache sin detener el servicio utilizando los siguientes comandos:

```bash
# Para recargar la configuración de Apache
sudo systemctl reload apache2  # En Debian/Ubuntu
sudo systemctl reload httpd    # En Red Hat/CentOS/Fedora
```

!!! warning
    Es importante tener en cuenta que los comandos anteriores requieren privilegios de administrador (root) para ejecutarse. Asegúrate de utilizar `sudo` antes de cada comando para obtener los permisos necesarios.

## Configuración de ficheros de Apache

En primer lugar, toda la configuración de apache se realiza a través de ficheros de configuración; dependiendo de nuestro Sistema Operativo, estos ficheros se encuentran en diferentes ubicaciones. Por ejemplo, en distribuciones basadas en Debian/Ubuntu, los ficheros de configuración se encuentran en la carpeta `/etc/apache2/`, mientras que en distribuciones basadas en Red Hat/CentOS/Fedora, se encuentran en la carpeta `/etc/httpd/`.

El fichero de configuración principal de Apache es `apache2.conf` en Debian/Ubuntu y `httpd.conf` en Red Hat/CentOS/Fedora. Este fichero contiene la configuración global del servidor web, incluyendo directivas de seguridad, módulos habilitados y configuraciones de rendimiento.

Veamos un ejemplo de cómo se ve el fichero de configuración principal de Apache en Debian/Ubuntu:

```bash
# /etc/apache2/apache2.conf
# Configuración global de Apache
ServerRoot "/etc/apache2"
Listen 80
LoadModule mpm_prefork_module /usr/lib/apache2/modules/mod_mpm_prefork.so
<Directory />
    Options FollowSymLinks
    AllowOverride None
    Require all denied
</Directory>
<Directory /var/www/>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require all granted
</Directory>
# Otras configuraciones...
```

Vemos que hay una serie de directivas que controlan el comportamiento del servidor web, como la ubicación de los archivos del servidor, los módulos cargados y las configuraciones de seguridad.

Veamos algunas de estas directivas en detalle:

* `ServerRoot`: Especifica la ubicación del directorio raíz del servidor web. En este caso, se encuentra en `/etc/apache2`.
* `Listen`: Especifica el puerto en el que Apache escuchará las solicitudes entrantes. En este caso, está configurado para escuchar en el puerto 80, que es el puerto predeterminado para HTTP. Podemos cambiar este puerto si queremos que Apache escuche en un puerto diferente, por ejemplo, el puerto 8080. Para ello, simplemente cambiamos la directiva `Listen` a `Listen 8080` y reiniciamos el servicio de Apache.
* `LoadModule`: Carga los módulos de Apache que proporcionan funcionalidades adicionales al servidor web. En este caso, se está cargando el módulo `mod_mpm_prefork`, que es un módulo de procesamiento de solicitudes que utiliza un modelo de procesos prefork para manejar las solicitudes entrantes.
* `<Directory>`: Define las configuraciones específicas para un directorio en particular. En este caso, se están definiendo configuraciones para el directorio raíz `/` y para el directorio `/var/www/`, que es donde se encuentran los archivos de nuestras aplicaciones web. La directiva `Options` controla las opciones disponibles para el directorio, `AllowOverride` controla si se permiten archivos `.htaccess` en el directorio y `Require` controla quién tiene acceso al directorio.


Existen muchas más directivas que podemos configurar en el fichero de configuración principal de Apache, pero estas son algunas de las más importantes y comunes. A medida que avancemos en el curso, veremos cómo configurar otras directivas y módulos para mejorar la seguridad, el rendimiento y la funcionalidad de nuestro servidor web Apache.

### Configuración de Directorios

Al usar la directiva `<Directory>`, podemos especificar configuraciones específicas para diferentes directorios en nuestro servidor web. Por ejemplo, podemos configurar un directorio para que solo sea accesible desde ciertas direcciones IP, o podemos habilitar la autenticación para un directorio específico.

Veamos un ejemplo de cómo configurar un directorio para que solo sea accesible desde una dirección IP específica:

```bash
<Directory /var/www/mi_aplicacion>
    Options Indexes FollowSymLinks
    AllowOverride None
    Require ip 192.168.1.100
    Require host example.com
</Directory>
```
Aquí, estamos configurando el directorio `/var/www/mi_aplicacion` para que solo sea accesible desde la dirección IP `192.168.1.100` y desde el host `example.com`. Esto permitirá que solo los usuarios que accedan desde esa dirección IP o desde ese host puedan ver el contenido del directorio.

### Ficheros .htaccess

Hemos comentado anteriormente que la directiva `AllowOverride` controla si se permiten archivos `.htaccess` en un directorio. Los archivos `.htaccess` son archivos de configuración que se pueden colocar en un directorio específico para anular la configuración global de Apache para ese directorio.

Estos ficheros son útiles para realizar configuraciones específicas para un directorio sin tener que modificar el fichero de configuración principal de Apache. Por ejemplo, podemos utilizar un archivo `.htaccess` para habilitar la autenticación en un directorio específico, redirigir URLs o habilitar la compresión de archivos.

Veamos un ejemplo de cómo habilitar la autenticación en un directorio utilizando un archivo `.htaccess`:

```bash
# /var/www/mi_aplicacion/.htaccess
AuthType Basic
AuthName "Área Restringida"
AuthUserFile /var/www/mi_aplicacion/.htpasswd
Require valid-user
```

En este ejemplo, estamos configurando la autenticación básica para el directorio `/var/www/mi_aplicacion`. La directiva `AuthType` especifica el tipo de autenticación que se utilizará, `AuthName` define el nombre del área restringida que se mostrará al usuario, `AuthUserFile` especifica la ubicación del archivo que contiene los nombres de usuario y contraseñas, y `Require valid-user` indica que solo los usuarios válidos podrán acceder al directorio.

#### Fichero .htpasswd

El archivo `.htpasswd` es un archivo que contiene los nombres de usuario y contraseñas para la autenticación básica en Apache. Este archivo se puede generar utilizando la herramienta `htpasswd`, que viene incluida con Apache. Para generar un archivo `.htpasswd`, podemos utilizar el siguiente comando:

```bash
# Generar un archivo .htpasswd con un usuario llamado "usuario"
htpasswd -c /var/www/mi_aplicacion/.htpasswd usuario
```

Este comando creará un archivo `.htpasswd` en la ubicación especificada y añadirá un usuario llamado "usuario". Se nos pedirá que ingresemos una contraseña para el usuario, y el comando generará un hash de la contraseña y lo almacenará en el archivo `.htpasswd`.

Un fichero `.htpasswd` puede contener múltiples usuarios y contraseñas, y cada línea del archivo representa un usuario y su contraseña encriptada. Por ejemplo, un archivo `.htpasswd` podría verse así:

```
usuario:$apr1$3G5f8JkL$K1j2l3m4n5o6p7q8r9s0t1u2v
admin:$apr1$4H6g9KjM$L2m3n4o5p6q7r8s9t0u1v2w3x
```

!!! warning
    Es importante tener en cuenta que los archivos `.htaccess` y `.htpasswd` deben tener permisos adecuados para garantizar la seguridad de la aplicación web. Asegúrate de que estos archivos no sean accesibles públicamente y que solo los usuarios autorizados puedan acceder a ellos.

!!! info
    Las contraseñas almacenadas en el archivo `.htpasswd` están encriptadas utilizando un algoritmo de hash, lo que significa que no se almacenan en texto plano. Esto proporciona una capa adicional de seguridad para proteger las credenciales de los usuarios.

## Instalación de módulos adicionales en Apache

Otro aspecto importante de la configuración de Apache es la instalación de módulos adicionales que proporcionan funcionalidades adicionales al servidor web. Apache viene con una serie de módulos preinstalados, pero también podemos instalar módulos adicionales según nuestras necesidades.

!!! info
    Un modulo de Apache es un componente que extiende la funcionalidad del servidor web. Los módulos pueden proporcionar características adicionales, como soporte para diferentes lenguajes de programación, autenticación, compresión de archivos, reescritura de URLs y mucho más.

Por ejemplo, podemos instalar el módulo `mod_rewrite`, que permite reescribir URLs y crear reglas de redirección. Para instalar este módulo en Debian/Ubuntu, podemos utilizar el siguiente comando:

```bash
sudo a2enmod rewrite
sudo systemctl restart apache2
```

En Red Hat/CentOS/Fedora, podemos instalar el módulo `mod_rewrite` utilizando el siguiente comando:

```bash
sudo yum install mod_rewrite
sudo systemctl restart httpd
```

Podemos verificar que el módulo `mod_rewrite` está habilitado utilizando el siguiente comando:

```bash
apache2ctl -M | grep rewrite  # En Debian/Ubuntu
httpd -M | grep rewrite        # En Red Hat/CentOS/Fedora
```

Otros módulos populares que podemos instalar en Apache, pueden ser:

* `mod_ssl`: Proporciona soporte para HTTPS y certificados SSL/TLS.
* `mod_headers`: Permite modificar las cabeceras HTTP de las respuestas del servidor web.
* `mod_deflate`: Permite la compresión de archivos para mejorar el rendimiento de la aplicación web.
* `mod_security`: Proporciona un firewall de aplicaciones web para proteger la aplicación web contra ataques y vulnerabilidades.
* `mod_jk`: Permite la integración de Apache con servidores de aplicaciones Java, como Tomcat.