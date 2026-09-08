# Introducción

Es habitual que los desarrolladores web se centren en la creación de aplicaciones y sitios web, pero a menudo descuidan el proceso de despliegue. El despliegue es una parte crucial del ciclo de vida del desarrollo web, ya que implica poner en producción una aplicación para que los usuarios puedan acceder a ella.

El despliegue de aplicaciones web puede ser un proceso complejo que requiere conocimientos técnicos y habilidades específicas. En este tema, exploraremos los conceptos fundamentales del despliegue de aplicaciones web, incluyendo la configuración de servidores, la optimización del rendimiento, la seguridad y las mejores prácticas para garantizar un despliegue exitoso.

Durante este curso, aprenderás a desplegar aplicaciones web en diferentes entornos y plataformas, utilizando herramientas y tecnologías modernas. También discutiremos los desafíos comunes que enfrentan los desarrolladores durante el despliegue y cómo superarlos.

Hasta ahora, se ha visto la creación de webs como un conjunto de archivos que se suben a un servidor web, pero en la actualidad, el despliegue de aplicaciones web implica mucho más que simplemente subir archivos. Incluye la configuración del servidor, la gestión de bases de datos, la implementación de medidas de seguridad y la optimización del rendimiento para garantizar una experiencia de usuario fluida.

Podemos distinguir según este proceso las webs en 2 tipos:

* Webs estáticas: Son aquellas que no requieren procesamiento del lado del servidor y se componen principalmente de archivos HTML, CSS y JavaScript. Estas webs son rápidas y fáciles de desplegar, pero tienen limitaciones en cuanto a interactividad y funcionalidad.
* Webs dinámicas: Son aquellas que requieren procesamiento del lado del servidor y pueden interactuar con bases de datos y otros servicios. Estas webs son más complejas de desplegar, pero ofrecen una mayor funcionalidad y capacidad de personalización para los usuarios.

## Webs Estáticas

Las webs estáticas son aquellas que no requieren procesamiento del lado del servidor y se componen principalmente de archivos HTML, CSS y JavaScript. Estas webs son rápidas y fáciles de desplegar, pero tienen limitaciones en cuanto a interactividad y funcionalidad.

Este tipo de webs es ideal para sitios web simples, como blogs, portafolios o páginas de información, donde el contenido no cambia con frecuencia. Al no depender de un servidor para generar contenido dinámico, las webs estáticas pueden ser alojadas en servidores web simples o incluso en servicios de alojamiento gratuito.

!!! note
    Esta web es un ejemplo de una web estática, ya que se compone principalmente de archivos HTML, CSS y JavaScript, y no requiere procesamiento del lado del servidor para generar contenido dinámico.

Es importante conocer que existen generadores de páginas estáticas, como Jekyll, Hugo o Mkdocs, que permiten crear webs estáticas de manera más eficiente y con funcionalidades adicionales, como la integración con sistemas de control de versiones y la generación automática de contenido a partir de plantillas.

### Ejercicio 1: Generar una web estática con Mkdocs

En este ejercicio, aprenderás a generar una web estática utilizando Mkdocs, una herramienta de generación de sitios web estáticos basada en Markdown. Mkdocs es fácil de usar y permite crear documentación y sitios web de manera rápida y eficiente.

Para eta práctica, necesitarás tener instalado Python. Puedes usar una máquina virtual o un entorno de desarrollo local para instalar Python y Mkdocs. Una vez que tengas Python instalado, puedes instalar Mkdocs utilizando el siguiente comando:

```bash
pip install mkdocs # uso del gestor pip para instalar mkdocs
```

Una vez instalado Mkdocs, puedes crear un nuevo proyecto utilizando el siguiente comando:

```bash
mkdocs new my-project # crea un nuevo proyecto llamado my-project
```

Este comando generará una estructura de directorios básica para tu proyecto, incluyendo un archivo de configuración `mkdocs.yml` y un directorio `docs` donde puedes agregar tus archivos Markdown.

Dentro de la carpeta de tu proyecto, puedes agregar tus archivos Markdown en el directorio `docs`.

Para mostrar tu sitio web localmente, puedes utilizar el siguiente comando:

```bash
mkdocs serve # inicia un servidor local para previsualizar tu sitio web
```

Si entras a la dirección `http://localhost:8000` en tu navegador, podrás ver tu sitio web estático generado por Mkdocs. A medida que realices cambios en tus archivos Markdown, el servidor se actualizará automáticamente para reflejar los cambios.

!!! info
    Puedes encontrar más información sobre Mkdocs y su documentación oficial en [Mkdocs](https://www.mkdocs.org/). Además de encontrar información sobre la sintaxis de markdown en [Markdown Guide](https://www.markdownguide.org/).

## Webs Dinámicas

Las webs dinámicas son aquellas que requieren procesamiento del lado del servidor y pueden interactuar con bases de datos y otros servicios. Estas webs son más complejas de desplegar, pero ofrecen una mayor funcionalidad y capacidad de personalización para los usuarios.

Normalmente, las webs dinámicas se desarrollan utilizando lenguajes de programación del lado del servidor, como PHP, Python, Ruby o Node.js, y frameworks web que facilitan la creación de aplicaciones web interactivas. Estas webs pueden generar contenido dinámico en función de las solicitudes del usuario y pueden ofrecer funcionalidades avanzadas, como autenticación de usuarios, gestión de contenido y comercio electrónico.

Estas webs, pueden conectarse a bases de datos u otros servicios externos para almacenar y recuperar información, lo que permite a los desarrolladores crear aplicaciones web más complejas y personalizadas. Además, pueden crearse servicios web y APIs que permitan la comunicación entre diferentes aplicaciones y sistemas.

Algunos de los frameworks web más populares para el desarrollo de aplicaciones web dinámicas incluyen Django (Python), Ruby on Rails (Ruby), Laravel (PHP) y Express.js (Node.js). Estos frameworks proporcionan herramientas y bibliotecas que facilitan el desarrollo de aplicaciones web robustas y escalables.

Durante este curso, nos centraremos en el despliegue de aplicaciones web dinámicas en algunas ocasiones de diferentes frameworks y tecnologías, explorando las mejores prácticas para garantizar un despliegue exitoso y seguro.

## Aplicaciones Web

Las aplicaciones web son programas que se ejecutan en un navegador web y se acceden a través de Internet. Estas aplicaciones pueden variar desde simples sitios web estáticos hasta complejas aplicaciones interactivas que requieren bases de datos y procesamiento del lado del servidor.

Las aplicaciones web dinámicas permiten a los usuarios interactuar con la aplicación, enviar datos y recibir respuestas en tiempo real. Estas aplicaciones pueden incluir funcionalidades como formularios de contacto, sistemas de autenticación de usuarios, paneles de administración y comercio electrónico.

Existen diferentes tipos de aplicaciones web, que se pueden clasificar según su complejidad y funcionalidad. Algunos ejemplos incluyen:

* Aplicaciones web de una sola página (SPA): Estas aplicaciones cargan una sola página HTML y utilizan JavaScript para actualizar dinámicamente el contenido sin recargar la página completa. Ejemplos populares incluyen Gmail y Trello.
* Aplicaciones web de múltiples páginas (MPA): Estas aplicaciones consisten en varias páginas HTML que se cargan por separado. Cada página puede tener su propio contenido y funcionalidad. Ejemplos incluyen sitios web de comercio electrónico y blogs.
* Aplicaciones web progresivas (PWA): Estas aplicaciones combinan lo mejor de las aplicaciones web y las aplicaciones móviles, ofreciendo funcionalidades como notificaciones push, acceso sin conexión y rendimiento optimizado. Ejemplos incluyen Twitter Lite y Pinterest.
* Aplicaciones web en tiempo real: Estas aplicaciones permiten la comunicación en tiempo real entre el cliente y el servidor, utilizando tecnologías como WebSockets. Ejemplos incluyen aplicaciones de chat y colaboración en línea.

## La nube (cloud)

La nube, o cloud computing, se refiere a la entrega de servicios informáticos a través de Internet. Estos servicios incluyen almacenamiento, bases de datos, servidores, redes y software, entre otros. La nube permite a los desarrolladores y empresas acceder a recursos informáticos de manera flexible y escalable, sin necesidad de mantener infraestructura física propia.

En muchas ocasiones, el despliegue de aplicaciones web se realiza en entornos de nube, lo que ofrece ventajas como la escalabilidad, la disponibilidad y la reducción de costos. Los proveedores de servicios en la nube, como Amazon Web Services (AWS), Microsoft Azure y Google Cloud Platform (GCP), ofrecen una amplia gama de servicios y herramientas para facilitar el despliegue y la gestión de aplicaciones web.

En este curso, utilizaremos servicios en la nube para desplegar aplicaciones web, explorando las mejores prácticas y estrategias para garantizar un despliegue exitoso y seguro. Aprenderemos a configurar entornos de nube, gestionar recursos y optimizar el rendimiento de nuestras aplicaciones web en la nube.

!!! info
    En este curso se utilizará la nube de Amazon Web Services (AWS) para desplegar aplicaciones web, pero los conceptos y prácticas aprendidas se pueden aplicar a otros proveedores de servicios en la nube.
