# Despliegue de Aplicaciones Web

En este apartado, vamos a centrarnos en como realmente se despliega una aplicación web en un entorno de producción. El despliegue de aplicaciones web es un proceso crítico que implica la preparación, configuración y puesta en marcha de la aplicación para que esté disponible para los usuarios finales.

Vamos a comenzar explorando las herramientas de las que disponemos para desplegar aplicaciones web:

* **Sistema Operativo**: El sistema operativo en el que se ejecuta la aplicación web es fundamental para su despliegue. Dependiendo del sistema operativo, pueden existir diferentes herramientas y configuraciones disponibles. Los sistemas operativos más comunes para el despliegue de aplicaciones web son Linux, Windows y macOS.
* **Servidores web**: Los servidores web son programas que se encargan de recibir solicitudes HTTP de los clientes (navegadores) y devolver respuestas con el contenido solicitado. Algunos ejemplos populares de servidores web son Apache, Nginx y Microsoft IIS. Estos servidores pueden configurarse para manejar diferentes tipos de aplicaciones web, como aplicaciones estáticas o dinámicas.
* **SGDB**: Los sistemas de gestión de bases de datos (SGBD) son esenciales para las aplicaciones web que requieren almacenamiento y recuperación de datos. Algunos ejemplos populares de SGBD son MySQL, PostgreSQL, MongoDB y SQLite. Estos sistemas permiten a las aplicaciones web interactuar con bases de datos para almacenar información de usuarios, productos, transacciones y más.
* **Lenguajes de programación y frameworks**: Dependiendo del lenguaje de programación y el framework utilizado para desarrollar la aplicación web, el proceso de despliegue puede variar. Por ejemplo, aplicaciones desarrolladas con PHP, Python (Django, Flask), Ruby on Rails o Node.js pueden requerir configuraciones específicas en el servidor web y en el entorno de ejecución.

Es importante mencionar que dependiendo de la tecnología utilizada para desarrollar la aplicación web, el proceso de despliegue puede variar. Por ejemplo, una aplicación web desarrollada con PHP puede requerir un servidor web con soporte para PHP, mientras que una aplicación desarrollada con Node.js puede requerir un entorno de ejecución específico y la instalación de dependencias.

Vamos a ver un ejemplo de herramientas para desplegar aplicaciones web:

* **Linux**: Es un sistema operativo de código abierto ampliamente utilizado para el despliegue de aplicaciones web. Ofrece estabilidad, seguridad y flexibilidad, y es compatible con una amplia gama de servidores web y SGBD.
* **Apache**: Es uno de los servidores web más populares y ampliamente utilizados. Es compatible con múltiples sistemas operativos y lenguajes de programación, y ofrece una amplia gama de características y configuraciones para el despliegue de aplicaciones web.
* **MySQL**: Es un sistema de gestión de bases de datos relacional ampliamente utilizado en aplicaciones web. Es compatible con múltiples sistemas operativos y lenguajes de programación, y ofrece una amplia gama de características y configuraciones para el almacenamiento y recuperación de datos en aplicaciones web.
* **PHP**: Es un lenguaje de programación ampliamente utilizado para el desarrollo de aplicaciones web dinámicas.   

Si te fijas, cada primera letra de cada herramienta forma la palabra **LAMP**, que es un acrónimo que hace referencia a un conjunto de tecnologías utilizadas para el desarrollo y despliegue de aplicaciones web. LAMP significa Linux, Apache, MySQL y PHP, y es una combinación popular de tecnologías que se utilizan juntas para crear aplicaciones web dinámicas y escalables.

Cuando se despliega una aplicación web utilizando la pila LAMP, se instala y configura cada componente de la pila en un servidor web. El sistema operativo Linux proporciona la base para ejecutar el servidor web Apache, que maneja las solicitudes HTTP y sirve el contenido de la aplicación web. MySQL se utiliza para almacenar y recuperar datos de la aplicación, mientras que PHP se utiliza para procesar la lógica de negocio y generar contenido dinámico.

En la siguiente sección, vamos a explorar cómo desplegar aplicaciones web utilizando la pila LAMP y otras tecnologías populares, así como las mejores prácticas para garantizar un despliegue exitoso y seguro.

## Despliegue de aplicaciones web en la nube

Hoy en día, muchas aplicaciones web se despliegan en la nube, utilizando servicios de infraestructura como Amazon Web Services (AWS), Microsoft Azure o Google Cloud Platform (GCP). Estos servicios ofrecen una amplia gama de herramientas y servicios para el despliegue, escalado y gestión de aplicaciones web, lo que facilita el proceso de despliegue y permite a los desarrolladores centrarse en la creación de aplicaciones web innovadoras y funcionales.

En este curso, vamos a explorar cómo desplegar aplicaciones web en la nube utilizando diferentes servicios y herramientas, y cómo aprovechar las ventajas de la nube para mejorar el rendimiento, la escalabilidad y la disponibilidad de las aplicaciones web.

### Ejercicio 2: Despliegue usando Github Pages

Vamos a desplegar una aplicación web estática utilizando Github Pages, un servicio gratuito que permite alojar sitios web directamente desde un repositorio de GitHub. Este servicio es ideal para proyectos personales, portafolios y documentación de proyectos.

En primer lugar, necesitaremos una web estática que quedamos desplegar; vamos a utilizar el siguiente fragmento HTML como ejemplo:

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mi Aplicación Web</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <header>
        <h1>Bienvenido a Mi Aplicación Web</h1>
    </header>
    <main>
        <p>Esta es una aplicación web estática desplegada en GitHub Pages.</p>
    </main>
    <footer>
        <p>&copy; 2026 Mi Aplicación Web. Todos los derechos reservados.</p>
    </footer>
</body>
</html>
```

Copia este fichero en un archivo llamado `index.html`. Ahora, vamos a ir a la web de Github. Si no tienes una cuenta, crea una.

!!! info
    Github es una plataforma de desarrollo colaborativo que permite a los desarrolladores alojar y gestionar proyectos de software utilizando el sistema de control de versiones Git. Puedes encontrar más información sobre Github en [Github](https://github.com).

Vamos a seguir los siguientes pasos para desplegar nuestra aplicación web estática en Github Pages:

1. Crea un nuevo repositorio en tu cuenta de Github. LLamalo `nombreusuario.github.io`, donde `nombreusuario` es tu nombre de usuario en Github. Asegúrate de marcar la opción "Initialize this repository with a README".

!!! warning
    Es importante que el nombre del repositorio siga el formato `nombreusuario.github.io`, ya que esto es necesario para que Github Pages pueda generar la URL correcta para tu sitio web. Debe respetar las mayúsculas y minúsculas, y no debe contener espacios ni caracteres especiales.

2. Desde la propia web de github de nuestro repositorio, sube el archivo `index.html` que hemos creado anteriormente. Puedes hacerlo haciendo clic en el botón "Add file" y seleccionando "Upload files". Luego, arrastra y suelta el archivo `index.html` en la ventana de carga de archivos.
3. Una vez que hayas subido el archivo, haz clic en el botón "Commit changes" para guardar los cambios en el repositorio. Marca la opción "Commit directly to the main branch" y haz clic en "Commit changes".
4. Ahora, ve a la pestaña "Settings" de tu repositorio y desplázate hacia abajo hasta la sección "Pages". En la sección "Source", selecciona la rama "main" y haz clic en "Save". Esto habilitará Github Pages para tu repositorio.
5. Accede a la URL `https://nombreusuario.github.io` en tu navegador, reemplazando `nombreusuario` con tu nombre de usuario de Github. Deberías ver tu aplicación web estática desplegada y accesible públicamente.


