# SPRING BOOT

- [SPRING BOOT](#spring-boot)
  - [REFERENCIAS](#referencias)
  - [DESCRIPCIÓN GENERAL](#descripción-general)
  - [ESTRUCTURA DE DIRECTORIOS](#estructura-de-directorios)

## REFERENCIAS
https://spring.io/projects/spring-boot

## DESCRIPCIÓN GENERAL

Spring Boot facilita la creación de aplicaciones independientes basadas en Spring y de nivel de producción que puedes "simplemente ejecutar".

Tenemos una visión objetiva de la plataforma Spring y las bibliotecas de terceros para que puedas empezar sin complicaciones. La mayoría de las aplicaciones Spring Boot requieren una configuración mínima de Spring.

**Características**

- Crear aplicaciones Spring independientes
- Incruste Tomcat, Jetty o Undertow directamente (sin necesidad de implementar archivos WAR)
- Proporcionar dependencias de "inicio" con opiniones para simplificar la configuración de compilación
- Configurar automáticamente Spring y bibliotecas de terceros siempre que sea posible
- Proporcionar funciones listas para producción, como métricas, controles de estado y configuración externalizada.
- No requiere generación de código y no requiere configuración XML

## ESTRUCTURA DE DIRECTORIOS

Al crear el proyecto se nos descarga un archivo comprimido con todas las carpetas del proyecto organizadas de la siguiente manera:

* /.mvn: carpeta interna de Maven Wrapper en la que están los archivos que usan Maven sin tener que instalarlo globlalmente y garantizar que todos los desarrolladores tengan la misma versión.
* /src/main/java: es la carpeta más importante ya que contiene el código real de la aplicación: clases, servicios, repositorios y clase principal.
* /src/main/resources: recursos que no son código java como: application.properties o application.yml, archivos de configuración, plantillas y archivos estáticos.
* /src/main/webapp: propia de aplicaciones web tradicionales donde se situan: JSP, HTML, CSS y JS. En SpringBoot no siempre se usa.
* /src/test: código de tests: unitarios o de integración.
* /target: carpeta generada al compilar. Nunca se edita a mano.
* /webroot: no es creada por SpringBoot sino por el usuario para guardar el contenido multimedia, estilos y demás archivos manejados por el desarrollador.
* pom.xml: el archivo más importante después del código donde se define: dependencias, versión de java usada, plugins y tipo de empaquetado.
* mvnw y mvnw.cmd: script de Maven Wrapper para Linux/macOS (el primero), y Windows (el segundo).
