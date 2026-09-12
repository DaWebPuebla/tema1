# Instalación y Configuración de Servidores Web

En esta sección, vamos a explorar cómo instalar y configurar el servidor web Apache en un sistema operativo Linux. Apache es uno de los servidores web más populares y ampliamente utilizados, y es compatible con múltiples sistemas operativos y lenguajes de programación.

!!! note
    Antes de comenzar con la instalación y configuración de Apache, asegúrate de tener acceso a un sistema operativo Linux y privilegios de administrador (root) para realizar la instalación y configuración del servidor web. Puedes crear una máquina virtual o utilizar un entorno de desarrollo local para practicar la instalación y configuración de Apache.

## Instalación de Apache en Linux

Para instalar Apache en un sistema operativo Linux, puedes utilizar el gestor de paquetes de tu distribución. A continuación, se muestran los comandos para instalar Apache en algunas distribuciones populares de Linux:

### Distribuciones basadas en Debian/Ubuntu

Para instalar Apache en distribuciones basadas en Debian o Ubuntu, puedes utilizar el siguiente comando:

```bash
sudo apt update
sudo apt install apache2
```

Asegúrate de que el servicio de Apache se inicie automáticamente al arrancar el sistema. Puedes habilitar el servicio con el siguiente comando:

```bash
sudo systemctl enable apache2
```

Y comprobar que el servicio está activo con el siguiente comando:

```bash
sudo systemctl status apache2
```

Esto debería de mostrar que el servicio de Apache está activo y en ejecución. Podemos acceder desde dicha máquina a la dirección `http://localhost` o `http://<IP_DE_LA_MAQUINA>` para poder ver la web de bienvenida de Apache, que nos indica que el servidor web está funcionando correctamente.

### Distribuciones basadas en Red Hat/CentOS/Fedora

Para instalar Apache en distribuciones basadas en Red Hat, CentOS o Fedora, puedes utilizar el siguiente comando:

```bash
sudo dnf install httpd
```

Para comprobar que el servicio de Apache se inicie automáticamente al arrancar el sistema, puedes habilitar el servicio con el siguiente comando:

```bash
sudo systemctl enable httpd
```

Y comprobar que el servicio está activo con el siguiente comando:

```bash
sudo systemctl status httpd
```

### Ejercicio 3: Instalación de Apache en Linux

Desde tu máquina virtual o entorno de desarrollo local, realiza la instalación de Apache utilizando los comandos correspondientes a tu distribución de Linux. Asegúrate de que el servicio de Apache esté activo y en ejecución, y accede a la dirección `http://localhost` o `http://<IP_DE_LA_MAQUINA>` para verificar que el servidor web está funcionando correctamente.

Ahora, vamos a utilizar el fichero del ejercicio 2 _(Despliegue en Github Pages)_ para poder desplegarlo en nuestro servidor web Apache. Para ello, copia el fichero `index.html` en la carpeta `/var/www/html/` de tu máquina virtual o entorno de desarrollo local. Asegúrate de que el fichero tenga los permisos adecuados para que Apache pueda acceder a él.

Una vez copiado el fichero, accede a la dirección `http://localhost/index.html` o `http://<IP_DE_LA_MAQUINA>/index.html` para verificar que la aplicación web estática se ha desplegado correctamente en tu servidor web Apache.

## Instalación de MariaDB en Linux

Para instalar MariaDB en un sistema operativo Linux, puedes utilizar el gestor de paquetes de tu distribución. A continuación, se muestran los comandos para instalar MariaDB en algunas distribuciones populares de Linux:

### Distribuciones basadas en Debian/Ubuntu

Para instalar MariaDB en distribuciones basadas en Debian o Ubuntu, puedes utilizar el siguiente comando:

```bash
sudo apt update
sudo apt install mariadb-server
```

Puedes comprobar que el servicio de MariaDB está activo y en ejecución con el siguiente comando:

```bash
sudo systemctl status mariadb
```

### Distribuciones basadas en Red Hat/CentOS/Fedora

Para instalar MariaDB en distribuciones basadas en Red Hat, CentOS o Fedora, puedes utilizar el siguiente comando:

```bash
sudo dnf install mariadb-server
```

Y para comprobar que el servicio de MariaDB está activo y en ejecución, puedes utilizar el siguiente comando:

```bash
sudo systemctl status mariadb
```

### Configuración de MariaDB

Vamos a realizar la configuración inicial de MariaDB para asegurar que el servidor de base de datos esté protegido y listo para su uso. Ejecuta el siguiente comando para iniciar el script de seguridad de MariaDB:

```bash
sudo mysql_secure_installation
```

Este script te guiará a través de una serie de pasos para configurar la seguridad de MariaDB, incluyendo la configuración de la contraseña del usuario root, la eliminación de usuarios anónimos y la desactivación del acceso remoto para el usuario root.

!!! warning
    Asegúrate de seguir las instrucciones del script y configurar una contraseña segura para el usuario root de MariaDB. Esto es importante para proteger tu servidor de base de datos y garantizar la seguridad de tus aplicaciones web.

!!! info
    Para más información sobre la instalación y configuración de Apache y MariaDB en Linux, puedes consultar la documentación oficial de Apache en [Apache HTTP Server Documentation](https://httpd.apache.org/docs/) y la documentación oficial de MariaDB en [MariaDB Knowledge Base](https://mariadb.com/kb/en/).

## Instalación de PHP en Linux

Para instalar PHP en un sistema operativo Linux, puedes utilizar el gestor de paquetes de tu distribución. A continuación, se muestran los comandos para instalar PHP en algunas distribuciones populares de Linux:

### Distribuciones basadas en Debian/Ubuntu

Para instalar PHP en distribuciones basadas en Debian o Ubuntu, puedes utilizar el siguiente comando:

```bash
sudo apt update
sudo apt install php libapache2-mod-php php-mysql
```

En este caso se instalan varios paquetes de PHP, incluyendo el módulo de Apache para PHP y el módulo de MySQL para PHP, que permite la conexión a bases de datos MariaDB/MySQL desde aplicaciones web desarrolladas en PHP.

### Distribuciones basadas en Red Hat/CentOS/Fedora

Para instalar PHP en distribuciones basadas en Red Hat, CentOS o Fedora, puedes utilizar el siguiente comando:

```bash
sudo dnf install php php-mysqlnd
```

En este caso se instalan varios paquetes de PHP, incluyendo el módulo de MySQL para PHP, que permite la conexión a bases de datos MariaDB/MySQL desde aplicaciones web desarrolladas en PHP.

### Ejercicio 4: Instalación y Comprobación de PHP en Linux

Desde tu máquina virtual o entorno de desarrollo local, realiza la instalación de PHP utilizando los comandos correspondientes a tu distribución de Linux. Asegúrate de que el módulo de Apache para PHP y el módulo de MySQL para PHP estén instalados correctamente.

Una vez instalado PHP, vamos a crear un archivo de prueba para verificar que PHP está funcionando correctamente en nuestro servidor web Apache. Crea un archivo llamado `info.php` en la carpeta `/var/www/html/` con el siguiente contenido:

```php
<?php
phpinfo();
?>
```

Una vez creado el archivo, accede a la dirección `http://localhost/info.php` o `http://<IP_DE_LA_MAQUINA>/info.php` para verificar que PHP está funcionando correctamente en tu servidor web Apache. Deberías ver una página con información detallada sobre la configuración de PHP en tu servidor.

!!! info
    Para más información sobre la instalación y configuración de PHP en Linux, puedes consultar la documentación oficial de PHP en [PHP Manual](https://www.php.net/manual/en/install.php). Recuerda que aprenderás más sobre la sintaxis de PHP y cómo desarrollar aplicaciones web dinámicas en PHP en el módulo de _Desarrollo de aplicaciones web En Entorno Servidor_ (DAW) de este curso.