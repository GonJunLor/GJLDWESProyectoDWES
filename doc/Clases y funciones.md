# FUNCIONES Y CLASES DE PHP

- [FUNCIONES Y CLASES DE PHP](#funciones-y-clases-de-php)
  - [1. Variables Superglobales](#1-variables-superglobales)
  - [2. Funciones de Salida](#2-funciones-de-salida)
  - [3. Funciones de Utilidad, Tipado y Cadenas](#3-funciones-de-utilidad-tipado-y-cadenas)
  - [4. Archivos](#4-archivos)
  - [4.1 Header](#41-header)
  - [5. Funciones de Iteración de Arrays y JSON](#5-funciones-de-iteración-de-arrays-y-json)
  - [6. Clases y Funciones de Fecha/Hora](#6-clases-y-funciones-de-fechahora)
  - [7. Base de Datos - Extensión PDO](#7-base-de-datos---extensión-pdo)
  - [8. Otras Extensiones y Clases](#8-otras-extensiones-y-clases)


<hr>

## <h2>1. Variables Superglobales</h2>

Son arrays asociativos que están siempre disponibles en todos los ámbitos del script para obtener información del entorno, el servidor y el cliente.


| Variable | Propósito / Definición | Uso Típico |
| :--- | :--- | :--- |
| **`$_SERVER`** | Contiene información creada por el **servidor web** sobre el entorno de ejecución (cabeceras, rutas, host). | Obtener la IP del usuario (`$_SERVER['REMOTE_ADDR']`) o el método de la petición (`$_SERVER['REQUEST_METHOD']`). |
| **`$_GET`** | Contiene variables pasadas al script a través de la **URL** (método **HTTP GET**), en la cadena de consulta. | Recibir datos de la URL: `index.php?id=10`. |
| **`$_POST`** | Contiene variables pasadas al script a través del método de entrada **HTTP POST**. | Recibir datos de formularios (contraseñas, textos largos, etc.). |
| **`$_REQUEST`** | Contiene una combinación de `$_GET`, `$_POST` y `$_COOKIE`. **(Uso desaconsejado)**. | Acceder a datos sin importar su origen. |
| **`$_SESSION`** | Contiene variables de **sesión** disponibles para el usuario en múltiples páginas. Requiere `session_start()`. | Mantener el estado de login o un carrito de compras. |
| **`$_COOKIE`** | Contiene variables pasadas al script a través de las **cookies HTTP**. | Leer un identificador de usuario o token de seguimiento. |
| **`$_FILES`** | Contiene información sobre los archivos **subidos** al script. | Manejar el nombre, tamaño y ubicación temporal de archivos subidos. |
| **`$_ENV`** | Contiene variables de **entorno** pasadas por el sistema operativo o el servidor web. | Acceder a claves de configuración específicas del entorno. |

<hr>

## <h2>2. Funciones de Salida</h2>

<h3 style="color:#007bff;">echo</h3>

Usada para **mostrar una o más cadenas de texto** en la salida. Es ligeramente más rápido que `print`.

**Sintaxis:**
````Bash
echo arg1, arg2, ...;
````

**Ejemplo de Uso:**
````Bash
$saludo = "Hola";
echo $saludo, " Mundo!"; # Salida: Hola Mundo!
````
https://www.php.net/manual/es/function.echo.php

<h3 style="color:#007bff;">print</h3>

Usada para **mostrar una sola cadena de texto**. Siempre devuelve el valor `1`.

**Sintaxis:**
````Bash
print arg;
````

**Ejemplo de Uso:**
````Bash
$resultado = print "Muestra esto.";
# Salida: Muestra esto. ($resultado vale 1)
````
https://www.php.net/manual/es/function.print.php

<h3 style="color:#007bff;">printf</h3>

Muestra una **cadena formateada**. Permite insertar valores en una plantilla usando especificadores de formato (`%s`, `%d`).

**Sintaxis:**
````Bash
printf(string $format, mixed ...$values): int|false
````

**Ejemplo de Uso:**
````Bash
printf("El número es: %d, la cadena es: %s", 123, "test");
# Salida: El número es: 123, la cadena es: test
````
https://www.php.net/manual/es/function.printf.php

<h3 style="color:#007bff;">var_dump</h3>

Muestra **información estructurada y detallada** sobre una variable, incluyendo su **tipo** y su **valor**. Es la herramienta de depuración más completa.

**Sintaxis:**
````Bash
var_dump(mixed $value, mixed ...$values): void
````

**Ejemplo de Uso:**
````Bash
$arr = ["a" => 1, "b" => 2];
var_dump($arr);
/* Salida:
array(2) {
  ["a"]=> int(1)
  ["b"]=> int(2)
}
*/
````
https://www.php.net/manual/es/function.var-dump.php

<h3 style="color:#007bff;">print_r</h3>

Imprime información **legible** sobre una variable. Es útil para inspeccionar **arrays** y **objetos**, mostrando sus claves y valores de forma estructurada.

**Sintaxis:**
````Bash
print_r(mixed $value, bool $return = false): string|bool
````

**Ejemplo de Uso:**
````Bash
$arr = ["a" => 1, "b" => 2];
print_r($arr);
# Salida: Array ( [a] => 1 [b] => 2 )
````
https://www.php.net/manual/es/function.print-r.php

<h3 style="color:#007bff;">phpinfo</h3>

Imprime una gran cantidad de **información sobre el estado actual de PHP**, incluyendo opciones de compilación, extensiones habilitadas y configuración.

**Sintaxis:**
````Bash
phpinfo(int $flags = INFO_ALL): bool
````

**Ejemplo de Uso:**
````Bash
# Muestra la configuración completa de PHP en el navegador
phpinfo();
````
https://www.php.net/manual/es/function.phpinfo.php

<h3 style="color:#007bff;">highlight_file</h3>

**Colorea (resalta)** el código fuente de un archivo PHP usando la sintaxis de HTML. Útil para mostrar código fuente.

**Sintaxis:**
````Bash
highlight_file(string $file_name, bool $return = false): string|bool
````

**Ejemplo de Uso:**
````Bash
# Asume que 'index.php' existe
highlight_file('index.php');
````
https://www.php.net/manual/es/function.highlight-file.php

<h3 style="color:#007bff;">exit</h3>

Es una **construcción del lenguaje** (similar a `die()`) que **termina la ejecución del script**. Opcionalmente, puede imprimir un mensaje antes de salir.

**Sintaxis:**
````Bash
exit(string|int $status = 0): void
````

**Ejemplo de Uso:**
````Bash
if ($error) {
    exit('Ocurrió un error fatal.');
}
````
https://www.php.net/manual/es/function.exit.php

<hr>

## <h2>3. Funciones de Utilidad, Tipado y Cadenas</h2>

| Elemento | Enlace | Propósito / Definición | Uso y Ejemplo |
| :--- | :--- | :--- | :--- |
| **`isset`** | [php.net](https://www.php.net/manual/es/function.isset.php) | Determina si una variable **está declarada y su valor no es `NULL`**. Fundamental para validar datos de entrada. | if (isset($_POST['usuario'])) { ... } |
| **`empty`** | [php.net](https://www.php.net/manual/es/function.empty.php) | Determina si una variable **está vacía**. (NULL, `false`, `0`, `""`, `array()`). | if (empty($nombre)) { echo "Vacío"; } |
| **`gettype`** | [php.net](https://www.php.net/manual/es/function.gettype.php) | Devuelve el **tipo de la variable** dada como una cadena (`integer`, `string`, `array`, `object`, etc.). | echo gettype(5); # integer |
| **`is_string`** | [php.net](https://www.php.net/manual/es/function.is-string.php) | Comprueba si el tipo de una variable es una **cadena de texto** (`string`). | var_dump(is_string("Hola")); # true |
| **`str_replace`** | [php.net](https://www.php.net/manual/es/function.str-replace.php) | **Reemplaza todas las ocurrencias** de una subcadena buscada por una de reemplazo. | str_replace("mundo", "universo", "Hola mundo.") |
| **`strtolower`** | [php.net](https://www.php.net/manual/es/function.strtolower.php) | **Convierte una cadena de texto a minúsculas**. | strtolower("TEXTO"); # texto |
| **`number_format`** | [php.net](https://www.php.net/manual/es/function.number-format.php) | **Formatea un número** con miles agrupados y un punto decimal. | number_format(1234.56, 2, ',', '.'); # 1.234,56 |
| **`constant`** | [php.net](https://www.php.net/manual/es/function.constant.php) | Devuelve el **valor de una constante**, dado su nombre como cadena. | constant("MAX_SIZE") |
| **`get_loaded_extensions`** | [php.net](https://www.php.net/manual/es/function.get-loaded-extensions.php) | Devuelve un **array con los nombres de todas las extensiones PHP cargadas** y disponibles. | print_r(get_loaded_extensions()); |

<hr>

## <h2>4. Archivos</h2>

| Elemento | Enlace | Propósito / Definición | Uso y Ejemplo |
| :--- | :--- | :--- | :--- |
| **`file_get_contents`** | [php.net](https://www.php.net/manual/es/function.file-get-contents.php) | **Lee todo el contenido de un archivo** en una única cadena de texto. | $data = file_get_contents('datos.txt'); |
| **`file_put_contents`** | [php.net](https://www.php.net/manual/es/function.file-put-contents.php) | **Escribe una cadena de datos en un archivo**. Sobrescribe por defecto, usa `FILE_APPEND` para añadir. | file_put_contents('log.txt', $error, FILE_APPEND); |
| **`file_exists`** | [php.net](https://www.php.net/manual/es/function.file-exists.php) | **Verifica si un archivo o directorio existe**. | if (file_exists('config.php')) { ... } |
| **`require_once`** | [php.net](https://www.php.net/manual/es/function.require-once.php) | **Incluye y evalúa un archivo** específico. Si ya fue incluido, lo omite. **Detiene la ejecución** si no se encuentra. | require_once 'clase_base.php'; |


<hr>

## <h2>4.1 Header</h2>

https://www.php.net/manual/es/function.header.php

**`header`**   

**Envía una cabecera HTTP sin procesar** al cliente (navegador). Debe invocarse **antes de cualquier salida**. 

````php
header('Location: /inicio.php'); exit; 
````

<hr>

## <h2>5. Funciones de Iteración de Arrays y JSON</h2>

| Elemento | Enlace | Propósito / Definición | Uso y Ejemplo |
| :--- | :--- | :--- | :--- |
| **`reset`** | [php.net](https://www.php.net/manual/es/function.reset.php) | **Establece el puntero interno de un array al primer elemento** y devuelve su valor. | echo reset($array); |
| **`current`** | [php.net](https://www.php.net/manual/es/function.current.php) | Devuelve el **valor del elemento actual** al que apunta el puntero. | echo current($array); |
| **`key`** | [php.net](https://www.php.net/manual/es/function.key.php) | Devuelve la **clave del elemento actual** al que apunta el puntero. | echo key($array); |
| **`next`** | [php.net](https://www.php.net/manual/es/function.next.php) | **Avanza el puntero interno** del array un lugar y devuelve el valor del nuevo elemento. | echo next($array); |
| **`json_encode`** | [php.net](https://www.php.net/manual/es/function.json-encode.php) | Devuelve la **representación JSON** de un valor PHP. Crucial para APIs. | json_encode($array_datos) |
| **`json_decode`** | [php.net](https://www.php.net/manual/es/function.json-decode.php) | **Decodifica una cadena JSON** a un valor PHP. Devuelve un objeto por defecto; usa `true` para array asociativo. | json_decode($json_string, true) |

<hr>

## <h2>6. Clases y Funciones de Fecha/Hora</h2>

<h3 style="color:#007bff;">Clase DateTime</h3>

La clase orientada a objetos para manejar fechas y horas de manera robusta.

https://www.php.net/manual/es/class.datetime.php
<hr>
  
**`format(string $format): string`**

Devuelve la fecha/hora en el **formato especificado** como cadena.

````php
$fecha->format('Y-m-d H:i:s')
````
https://www.php.net/manual/es/datetime.format.php

**`getTimestamp(): int`**

Devuelve el **timestamp UNIX** (segundos desde 1970) para el objeto `DateTime`.

````php
$fecha->getTimestamp()
````
https://www.php.net/manual/es/datetime.gettimestamp.php

**`diff(DateTimeInterface $targetObject): DateInterval`**

Calcula la **diferencia entre dos objetos `DateTime`**, devolviendo un objeto `DateInterval`.

````Bash
$diferencia = $fecha1->diff($fecha2);
````
https://www.php.net/manual/es/datetime.diff.php


<h3 style="color:#007bff;">Funciones de Configuración de Zona horaria</h3>

Funciones globales para establecer el contexto de la fecha/hora.

**`date_default_timezone_set(string $timezone_identifier): bool`**

**Establece la zona horaria predeterminada** que se utilizará en todas las funciones de fecha/hora.
````Bash
date_default_timezone_set('Europe/Madrid');
````
https://www.php.net/manual/es/function.date-default-timezone-set.php

<br>

**`setlocale(string|int $category, string|array $locales, ...): string|false`**

**Establece la configuración regional** (locale), afectando a la moneda, el alfabeto y el formateo de tiempo (usado por `strftime`).
````Bash
setlocale(LC_TIME, 'es_ES.utf8');
````
https://www.php.net/manual/es/function.setlocale.php

<br>

**`strftime(string $format, ?int $timestamp = null): string|false`**
**Formatea una fecha/hora local** según la configuración regional (locale) establecida por `setlocale`. (**Obsoleta en PHP 8.1**).
````Bash
strftime('%A, %d de %B');
````
https://www.php.net/manual/es/function.strftime.php

<hr>

## <h2>7. Base de Datos - Extensión PDO</h2>

**PDO (PHP Data Objects)** es una extensión que proporciona una interfaz uniforme para acceder a bases de datos.


<h3 style="color:#007bff;">Clase Principal: PDO</h3>

Representa la conexión a la base de datos.

https://www.php.net/manual/es/class.pdo.php

<hr>
    
**`prepare(string $query, array $options = []): PDOStatement|false`**

**Prepara una sentencia SQL** para su ejecución. Fundamental para usar sentencias preparadas y prevenir la inyección SQL.
````Bash
$stmt = $pdo->prepare('SELECT * FROM users WHERE id = :id');
````

**`query(string $query, ?int $fetchMode = null, ...$fetchModeArgs): PDOStatement|false`**

**Ejecuta una sentencia SQL directamente** y devuelve un `PDOStatement`. Se usa **solo para sentencias sin valores variables**.
````Bash
$stmt = $pdo->query('SELECT name FROM roles');
````

**`beginTransaction(): bool`**

**Inicia una transacción**, asegurando que las siguientes operaciones se traten como una única unidad atómica.
````Bash
$pdo->beginTransaction();
````

**`commit(): bool`**

**Confirma una transacción**, haciendo permanentes los cambios.
````Bash
$pdo->commit();
````

**`rollBack(): bool`**

**Revierte una transacción**, deshaciendo todos los cambios desde que se inició.
````Bash
$pdo->rollBack();
````

**`getAttribute(int $attribute): mixed`**

**Recupera el valor actual de un atributo** de la conexión PDO.
````Bash
$driver = $pdo->getAttribute(PDO::ATTR_DRIVER_NAME);
````
    


<h3 style="color:#007bff;">Clase Resultado: PDOStatement</h3>

Representa una sentencia preparada y el conjunto de resultados asociado.


    
**`execute(?array $params = null): bool`**

**Ejecuta la sentencia preparada**. Opcionalmente, se le pasa un array de valores para enlazar a los marcadores.
````Bash
$stmt->execute([':id' => 5]);
````


**`bindParam(string|int $param, mixed &$var, int $type = PDO::PARAM_STR, ...): bool`**

**Enlaza una variable PHP a un marcador** de posición. El valor se obtiene en el momento de la ejecución.
````Bash
$stmt->bindParam(':id', $valor);
````


**`fetchObject(?string $class = "stdClass", array $constructorArgs = []): object|false`**

**Obtiene la siguiente fila** del conjunto de resultados y la devuelve **como un objeto**.
````Bash
$obj = $stmt->fetchObject();
````


**`rowCount(): int`**

Devuelve el **número de filas afectadas** por la última sentencia `DELETE`, `INSERT`, o `UPDATE`.
````Bash
$count = $stmt->rowCount();
````
    


<h3 style="color:#007bff;">Clase de Excepción: PDOException</h3>

Manejo de errores de base de datos.


    
**`getMessage(): string`**

Devuelve el **mensaje de error** asociado a la excepción PDO.
````Bash
echo $e->getMessage();
````


**`getCode(): string|int`**

Devuelve el **código de error SQLSTATE** (código alfanumérico) o el código de error específico del controlador.
````Bash
echo $e->getCode();
````
    


<hr>

## <h2>8. Otras Extensiones y Clases</h2>

| Elemento | Tipo | Propósito / Definición | Uso Típico |
| :--- | :--- | :--- | :--- |
| **`MYSQLI`** | Clase/Extensión | Extensión de PHP moderna para interactuar con bases de datos **MySQL**. Soporta POO y programación procedural. | Conexión y consultas directas a MySQL. |
| **`DOMDocument`** | Clase | Clase que proporciona una forma de **trabajar con documentos HTML o XML** usando el **DOM** (Document Object Model). | Analizar (parsear) documentos HTML o construir archivos XML. |