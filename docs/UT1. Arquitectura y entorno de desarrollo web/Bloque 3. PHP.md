
## 1. Instalación e integración de PHP

Hasta este momento hemos utilizado Apache para servir recursos estáticos como páginas HTML, imágenes o documentos.

Sin embargo, las aplicaciones web modernas necesitan generar contenidos dinámicos, procesar formularios, gestionar usuarios y acceder a bases de datos.

Para ello es necesario utilizar un lenguaje de programación capaz de ejecutarse en el servidor.

Durante este módulo utilizaremos **PHP**, uno de los lenguajes más utilizados en el desarrollo de aplicaciones web.

Algunas aplicaciones populares desarrolladas en PHP son:

- Moodle.
- WordPress.
- Nextcloud.
- phpMyAdmin.
- MediaWiki.

---

### ¿Qué es PHP?

PHP (_PHP: Hypertext Preprocessor_) es un lenguaje de programación ampliamente utilizado para el desarrollo de aplicaciones web y scripts ejecutados en el servidor.

Su principal característica es que el código se ejecuta en el servidor y no en el navegador del usuario.

Por ejemplo:

```php
<?php
echo "<h1>Hola ASIR</h1>";
?>
```

El usuario nunca recibe el código PHP.

Lo que recibe es el resultado generado tras su ejecución:

```html
<h1>Hola ASIR</h1>
```

---

### PHP dentro de una aplicación web

Cuando un usuario solicita un recurso PHP, Apache no puede enviarlo directamente al navegador.

En su lugar, Apache delega el procesamiento del archivo en el intérprete de PHP.

```text
Cliente web
   │
   ▼
Apache
   │
   ▼
PHP
   │
   │ Genera HTML
   ▼
Apache
   │
   ▼
Cliente web
```

Este mecanismo permite generar contenido dinámico adaptado a cada usuario.

Por ejemplo:

- Mostrar información personalizada.
- Gestionar sesiones.
- Procesar formularios.
- Acceder a bases de datos.

---

### Instalación de PHP

En sistemas Debian y Ubuntu, PHP puede instalarse utilizando el gestor de paquetes APT.

Antes de instalar nuevos paquetes es recomendable actualizar la información de los repositorios:

```bash
sudo apt update
```

La instalación básica puede realizarse mediante:

```bash
sudo apt install php
```

Este metapaquete instala la versión recomendada por la distribución junto con los componentes básicos necesarios para trabajar con PHP.

Una vez finalizada la instalación es recomendable reiniciar Apache:

```bash
sudo systemctl restart apache2
```

---

### Paquetes principales

Tras la instalación suelen añadirse varios paquetes relacionados.

**php**

Metapaquete principal.

Instala la versión recomendada de PHP para la distribución.

**php-cli**

Permite ejecutar scripts PHP desde la línea de comandos.

Ejemplo:

```bash
php fichero.php
```

**php-common**

Incluye bibliotecas y componentes comunes utilizados por PHP.

**libapache2-mod-php**

Permite integrar PHP directamente dentro de Apache mediante el módulo `mod_php`.

Gracias a esta integración Apache puede procesar archivos PHP y enviar al navegador únicamente el contenido generado.

---

### Verificación de la instalación

Podemos comprobar la versión instalada mediante:

```bash
php -v
```

Resultado esperado:

```text
PHP 8.x.x
```

La versión exacta dependerá de la distribución utilizada.

---

### Comprobación de la integración con Apache

También podemos comprobar que Apache tiene cargado el módulo PHP:

```bash
sudo apache2ctl -M | grep php
```

Resultado habitual:

```text
php_module
```

Si aparece este módulo significa que Apache está preparado para ejecutar código PHP mediante `mod_php`.

---

### Creación de un archivo PHP de prueba

Crear el fichero:

```bash
sudo nano /var/www/html/info.php
```

Contenido:

```php
<?php
phpinfo();
?>
```

Guardar el archivo y acceder desde el navegador a:

```text
http://localhost/info.php
```

---

### La función phpinfo()

La función:

```php
phpinfo();
```

muestra información detallada sobre el entorno de ejecución de PHP.

Entre otros datos podemos consultar:

- La versión instalada.
- Las extensiones cargadas.
- Las variables de entorno.
- Los módulos disponibles.
- La configuración utilizada por PHP.

Si esta página aparece correctamente en el navegador significa que:

- Apache funciona correctamente.
- PHP está instalado.
- Apache y PHP están correctamente integrados.

```text
Navegador
   │
   ▼
info.php
   │
   ▼
Apache
   │
   ▼
PHP
   │
   │ Ejecuta phpinfo()
   ▼
Respuesta HTML
```

---

### Archivo de configuración principal

PHP dispone de un archivo principal de configuración denominado:

```text
php.ini
```

En Debian suele encontrarse en una ruta similar a:

```text
/etc/php/8.x/apache2/php.ini
```

Este fichero permite configurar aspectos como:

- Límite de memoria.
- Zona horaria.
- Tamaño máximo de subida de archivos.
- Visualización de errores.
- Extensiones utilizadas.

Más adelante modificaremos algunos de estos parámetros para adaptar PHP a distintas aplicaciones web.

---

### Ubicación de los archivos PHP

Los archivos PHP pueden almacenarse en cualquier directorio publicado por Apache.

Por ejemplo:

```text
/var/www/html
```

Archivos habituales:

```text
index.php
login.php
usuarios.php
```

Cuando Apache recibe una solicitud para uno de estos archivos, delega su procesamiento en PHP antes de devolver la respuesta al navegador.

---

### Diferencia entre HTML y PHP

Supongamos dos archivos.

**Archivo HTML**

```html
<h1>Hola ASIR</h1>
```

Apache envía directamente el contenido al navegador.

**Archivo PHP**

```php
<?php
echo "<h1>Hola ASIR</h1>";
?>
```

Apache delega la ejecución en PHP.

El navegador recibe exactamente el mismo resultado:

```html
<h1>Hola ASIR</h1>
```

pero el proceso realizado en el servidor es distinto.

---

### Extensiones habituales de PHP

PHP puede ampliarse mediante extensiones que añaden funcionalidades específicas.

**php-mysql**

Permite conectar aplicaciones PHP con bases de datos MariaDB y MySQL.

```bash
sudo apt install php-mysql
```

**php-gd**

Permite trabajar con imágenes.

```bash
sudo apt install php-gd
```

**php-xml**

Permite procesar documentos XML.

```bash
sudo apt install php-xml
```

**php-curl**

Permite realizar conexiones a servicios externos.

```bash
sudo apt install php-curl
```

Las aplicaciones web suelen requerir distintas extensiones. La documentación de cada aplicación indica cuáles son necesarias.

---

### PHP-FPM

En instalaciones modernas es frecuente utilizar **PHP-FPM** (_PHP FastCGI Process Manager_).

Puede instalarse mediante:

```bash
sudo apt install php-fpm
```

PHP-FPM ejecuta PHP como un servicio independiente de Apache.

La arquitectura pasa a ser:

```text
Cliente web
   │
   ▼
Apache
   │
   ▼
PHP-FPM
   │
   ▼
Aplicación PHP
```

Esta separación ofrece ventajas en:

- Rendimiento.
- Escalabilidad.
- Gestión de recursos.
- Seguridad.

---

### mod_php frente a PHP-FPM

Existen dos formas habituales de integrar Apache y PHP.

**mod_php**

```text
Apache
└── PHP integrado
```

Ventajas:

- Configuración sencilla.
- Fácil de aprender.
- Adecuado para entornos de desarrollo.

Inconvenientes:

- Mayor consumo de memoria.
- Menor flexibilidad.

**PHP-FPM**

```text
Apache
   │
   ▼
PHP-FPM
```

Ventajas:

- Mejor rendimiento.
- Menor consumo de recursos.
- Mayor escalabilidad.
- Separación clara entre servidor web y motor de aplicación.

Inconvenientes:

- Configuración más compleja.

---

### ¿Cuál utilizaremos?

Durante las primeras prácticas utilizaremos normalmente la integración clásica basada en:

```text
Apache
└── mod_php
```

porque resulta más sencilla para comprender el funcionamiento de PHP.

No obstante, es importante conocer que muchos entornos profesionales utilizan:

```text
Apache + PHP-FPM
```

o incluso:

```text
Nginx + PHP-FPM
```

debido a sus ventajas de rendimiento.

---

### Problemas habituales

**El código PHP aparece en pantalla**

Si al acceder a un archivo PHP se muestra el código fuente:

```php
<?php
phpinfo();
?>
```

en lugar del resultado generado, PHP no está configurado correctamente.

Comprobar:

```bash
sudo apache2ctl -M | grep php
```

y verificar que aparece:

```text
php_module
```

**Página en blanco**

Puede deberse a:

- Errores de programación.
- Problemas de configuración.
- Extensiones no instaladas.

Revisar:

```bash
sudo tail /var/log/apache2/error.log
```

**Archivo no encontrado**

Comprobar:

- Ruta correcta.
- Nombre del fichero.
- Permisos de acceso.
- Ubicación dentro del DocumentRoot.

---

### Relación con la arquitectura multicapa

Dentro de una arquitectura web típica:

```text
Cliente
   │
   ▼
Apache
   │
   ▼
PHP
   │
   ▼
MariaDB
```

cada componente desempeña una función diferente:

|Componente|Función|
|---|---|
|Apache|Servidor web|
|PHP|Lógica de aplicación|
|MariaDB|Almacenamiento de datos|

Esta será la arquitectura básica utilizada durante gran parte del módulo.

---

### Buenas prácticas

- Verificar siempre la instalación mediante `phpinfo()`.
- Eliminar el archivo `info.php` una vez finalizadas las pruebas.
- Mantener PHP actualizado.
- Instalar únicamente las extensiones necesarias.
- Revisar periódicamente los registros de errores.
- Documentar las extensiones instaladas.

> En un servidor real no es recomendable mantener accesible públicamente la página `phpinfo()`, ya que proporciona información detallada sobre la configuración del sistema.

---

## 2. Pruebas de funcionamiento con PHP

Una vez instalado PHP e integrado con Apache, es necesario comprobar que el entorno funciona correctamente antes de comenzar a desarrollar aplicaciones web.

Las pruebas de funcionamiento permiten verificar que:

- Apache está procesando correctamente los archivos PHP.
- El intérprete PHP funciona adecuadamente.
- Las extensiones instaladas están disponibles.
- No existen errores de configuración.
- El entorno está preparado para el desarrollo de aplicaciones web.

---

### Objetivos de las pruebas

Antes de continuar con el desarrollo debemos asegurarnos de que:

- Los archivos PHP se ejecutan correctamente.
- No se muestran errores de configuración.
- Apache y PHP trabajan conjuntamente.
- El servidor devuelve las respuestas esperadas.

Una instalación aparentemente correcta puede ocultar problemas que solo se detectan al ejecutar código PHP.

---

### Primera prueba: phpinfo()

La comprobación más habitual consiste en utilizar la función:

```php
phpinfo();
```

Crear el archivo:

```bash
sudo nano /var/www/html/info.php
```

Contenido:

```php
<?php
phpinfo();
?>
```

Acceder desde el navegador a:

```text
http://localhost/info.php
```

Si todo funciona correctamente aparecerá una página con información detallada sobre PHP.

Esta prueba confirma que:

- Apache funciona.
- PHP está instalado.
- Apache ejecuta correctamente los scripts PHP.

---

### Segunda prueba: salida de texto

Una vez verificada la instalación conviene realizar una prueba sencilla utilizando código propio.

Crear el archivo:

```bash
sudo nano /var/www/html/prueba.php
```

Contenido:

```php
<?php

echo "<h1>PHP funciona correctamente</h1>";

?>
```

Acceder a:

```text
http://localhost/prueba.php
```

Resultado esperado:

```text
PHP funciona correctamente
```

Si el navegador muestra el código PHP en lugar del mensaje generado, existe un problema de integración entre Apache y PHP.

---

### Tercera prueba: fecha y hora del servidor

Una de las ventajas de PHP es la posibilidad de generar contenido dinámico.

Modificar el archivo:

```php
<?php

echo "<h1>Servidor operativo</h1>";
echo "<p>Fecha y hora: " . date("d/m/Y H:i:s") . "</p>";

?>
```

Cada vez que se recargue la página aparecerá una hora diferente.

Esta prueba demuestra que el código se ejecuta en el servidor antes de enviarse al navegador.

---

### Cuarta prueba: variables y operaciones

Crear el archivo:

```php
<?php

$a = 10;
$b = 20;

echo "<p>Suma: " . ($a + $b) . "</p>";

?>
```

Resultado esperado:

```text
Suma: 30
```

Con esta prueba comprobamos que PHP interpreta correctamente variables y expresiones.

---

### Quinta prueba: información del servidor

PHP proporciona información sobre la petición y el entorno mediante variables predefinidas.

Crear el archivo:

```php
<?php

echo "<p>Servidor: " . $_SERVER['SERVER_NAME'] . "</p>";
echo "<p>Software: " . $_SERVER['SERVER_SOFTWARE'] . "</p>";

?>
```

Esta prueba permite observar cómo PHP puede acceder a información proporcionada por Apache.

---

### Comprobación de extensiones instaladas

Podemos verificar qué extensiones están disponibles mediante:

```bash
php -m
```

La salida mostrará una lista similar a:

```text
curl
gd
mysqli
pdo_mysql
xml
```

Esta comprobación resulta muy útil antes de instalar aplicaciones como Moodle o WordPress.

---

### Comprobación desde la línea de comandos

PHP también puede ejecutarse sin utilizar Apache.

Crear el archivo:

```bash
nano prueba.php
```

Contenido:

```php
<?php

echo "Hola desde PHP\n";

?>
```

Ejecutar:

```bash
php prueba.php
```

Resultado:

```text
Hola desde PHP
```

Esto confirma que el intérprete PHP funciona correctamente desde la consola.

---

### Consulta de la configuración de PHP

Podemos consultar la configuración activa mediante:

```bash
php --ini
```

Resultado típico:

```text
Loaded Configuration File: /etc/php/8.x/apache2/php.ini
```

También podemos consultar parámetros concretos:

```bash
php -i | grep memory_limit
```

o

```bash
php -i | grep upload_max_filesize
```

---

### Diagnóstico de errores

Durante las pruebas pueden aparecer distintos problemas.

**Se muestra el código PHP en el navegador**

Ejemplo:

```php
<?php
echo "Hola";
?>
```

Posibles causas:

- PHP no está instalado.
- El módulo PHP no está cargado.
- Apache no se ha reiniciado tras la instalación.

Comprobar:

```bash
sudo apache2ctl -M | grep php
```

**Página completamente en blanco**

Posibles causas:

- Error en el script.
- Configuración incorrecta de PHP.
- Extensiones faltantes.

Consultar:

```bash
sudo tail /var/log/apache2/error.log
```

**Error 500 Internal Server Error**

Suele indicar un problema durante la ejecución del script.

Comprobar:

```bash
sudo tail /var/log/apache2/error.log
```

para localizar la causa concreta.

---

### Eliminación del archivo phpinfo()

Una vez finalizadas las pruebas es recomendable eliminar el archivo:

```text
info.php
```

ya que proporciona información detallada sobre el servidor.

```bash
sudo rm /var/www/html/info.php
```

En entornos de producción este archivo nunca debería permanecer accesible.

---

### Lista de verificación

Antes de continuar con la integración de bases de datos conviene verificar:

- [ ] PHP está instalado.
- [ ] Apache ejecuta correctamente scripts PHP.
- [ ] `phpinfo()` funciona.
- [ ] Las páginas PHP generan contenido dinámico.
- [ ] Las extensiones necesarias están disponibles.
- [ ] No existen errores en los registros.
- [ ] El archivo `info.php` ha sido eliminado tras las pruebas.

---

### Ideas clave

Al finalizar este apartado debes ser capaz de:

- Verificar la correcta integración entre Apache y PHP.
- Crear y ejecutar scripts PHP sencillos.
- Utilizar `phpinfo()` para diagnosticar problemas.
- Comprobar las extensiones instaladas.
- Ejecutar PHP desde la línea de comandos.
- Consultar la configuración de PHP.
- Diagnosticar errores habituales durante la ejecución de scripts.
- Aplicar una metodología sistemática de pruebas del entorno PHP.

---

## 3. Conexión con bases de datos (MariaDB)

Una vez instalado MariaDB (ver el bloque correspondiente) y comprobado que funciona correctamente, el siguiente paso es conectar una aplicación PHP con la base de datos. Esto es lo que realmente cierra el ciclo completo del stack LAMP.

PHP ofrece principalmente dos formas de conectarse a MariaDB/MySQL: la extensión **MySQLi** y la capa de acceso a datos **PDO**.

### Extensión necesaria

Ambas requieren tener instalada la extensión correspondiente (ya vista en el Bloque 2):

```bash
sudo apt install php-mysql
sudo systemctl restart apache2
```

Podemos comprobar que la extensión está cargada:

```bash
php -m | grep mysqli
```

### Conexión con MySQLi (orientado a objetos)

```php
<?php

$servidor = "localhost";
$usuario  = "appweb";
$password = "contraseña_segura";
$bd       = "tienda";

$conexion = new mysqli($servidor, $usuario, $password, $bd);

if ($conexion->connect_error) {
    die("Error de conexión: " . $conexion->connect_error);
}

echo "Conexión establecida correctamente.";

$conexion->close();

?>
```

### Consulta de datos con MySQLi

```php
<?php

$conexion = new mysqli("localhost", "appweb", "contraseña_segura", "tienda");

$resultado = $conexion->query("SELECT nombre, precio FROM productos");

while ($fila = $resultado->fetch_assoc()) {
    echo "<p>" . $fila['nombre'] . " - " . $fila['precio'] . " €</p>";
}

$conexion->close();

?>
```

### Conexión con PDO

PDO ofrece una interfaz común válida para distintos motores de bases de datos, no solo MariaDB/MySQL.

```php
<?php

$servidor = "mysql:host=localhost;dbname=tienda;charset=utf8mb4";
$usuario  = "appweb";
$password = "contraseña_segura";

try {
    $pdo = new PDO($servidor, $usuario, $password);
    $pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    echo "Conexión establecida correctamente.";
} catch (PDOException $e) {
    die("Error de conexión: " . $e->getMessage());
}

?>
```

### Consulta de datos con PDO

```php
<?php

$pdo = new PDO("mysql:host=localhost;dbname=tienda;charset=utf8mb4", "appweb", "contraseña_segura");

$consulta = $pdo->query("SELECT nombre, precio FROM productos");

foreach ($consulta as $fila) {
    echo "<p>" . $fila['nombre'] . " - " . $fila['precio'] . " €</p>";
}

?>
```

### MySQLi frente a PDO

|Característica|MySQLi|PDO|
|---|---|---|
|Motores soportados|Solo MySQL/MariaDB|Varios (MySQL, PostgreSQL, SQLite...)|
|Estilo de programación|Procedimental u orientado a objetos|Orientado a objetos|
|Sentencias preparadas|Sí|Sí|
|Uso recomendado|Aplicaciones ligadas a MySQL/MariaDB|Aplicaciones que puedan cambiar de motor|

---

## 4. Sentencias preparadas y seguridad

Construir consultas SQL concatenando directamente datos introducidos por el usuario es una práctica insegura, ya que expone la aplicación a ataques de **inyección SQL**.

### Ejemplo inseguro (NO utilizar)

```php
<?php
// Código vulnerable a inyección SQL. Solo con fines ilustrativos.
$usuario = $_GET['usuario'];
$consulta = "SELECT * FROM usuarios WHERE nombre = '$usuario'";
?>
```

Un usuario malicioso podría manipular el parámetro `usuario` para alterar el significado de la consulta.

### Solución: sentencias preparadas con MySQLi

```php
<?php

$conexion = new mysqli("localhost", "appweb", "contraseña_segura", "tienda");

$stmt = $conexion->prepare("SELECT nombre, precio FROM productos WHERE nombre = ?");
$stmt->bind_param("s", $nombreBuscado);

$nombreBuscado = "Teclado";
$stmt->execute();

$resultado = $stmt->get_result();

while ($fila = $resultado->fetch_assoc()) {
    echo "<p>" . $fila['nombre'] . " - " . $fila['precio'] . " €</p>";
}

$stmt->close();
$conexion->close();

?>
```

### Solución: sentencias preparadas con PDO

```php
<?php

$pdo = new PDO("mysql:host=localhost;dbname=tienda;charset=utf8mb4", "appweb", "contraseña_segura");

$stmt = $pdo->prepare("SELECT nombre, precio FROM productos WHERE nombre = :nombre");
$stmt->execute(['nombre' => 'Teclado']);

foreach ($stmt as $fila) {
    echo "<p>" . $fila['nombre'] . " - " . $fila['precio'] . " €</p>";
}

?>
```

Las sentencias preparadas separan el código SQL de los datos, de forma que estos últimos nunca se interpretan como parte de la consulta.

> Esta es una de las primeras buenas prácticas de seguridad que debe interiorizar cualquier persona que desarrolle o administre aplicaciones web con acceso a bases de datos.

---

## 5. Prueba de integración completa: Apache + PHP + MariaDB

Para comprobar que todo el stack funciona correctamente de extremo a extremo, podemos crear una pequeña página de prueba.

### Crear la base de datos y los datos de prueba

```sql
CREATE DATABASE prueba_lamp;
USE prueba_lamp;

CREATE TABLE mensajes (
    id INT AUTO_INCREMENT PRIMARY KEY,
    texto VARCHAR(255) NOT NULL
);

INSERT INTO mensajes (texto) VALUES ('Apache, PHP y MariaDB funcionan correctamente');
```

### Crear el usuario de la aplicación

```sql
CREATE USER 'lampuser'@'localhost' IDENTIFIED BY 'lamp1234';
GRANT ALL PRIVILEGES ON prueba_lamp.* TO 'lampuser'@'localhost';
FLUSH PRIVILEGES;
```

### Crear la página PHP

```bash
sudo nano /var/www/html/prueba_lamp.php
```

```php
<?php

$pdo = new PDO("mysql:host=localhost;dbname=prueba_lamp;charset=utf8mb4", "lampuser", "lamp1234");
$pdo->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

$resultado = $pdo->query("SELECT texto FROM mensajes");

foreach ($resultado as $fila) {
    echo "<h1>" . htmlspecialchars($fila['texto']) . "</h1>";
}

?>
```

### Comprobación

```text
http://localhost/prueba_lamp.php
```

Si el navegador muestra el mensaje almacenado en la base de datos, todo el stack está correctamente instalado, configurado e integrado:

```text
Cliente web  →  Apache  →  PHP  →  MariaDB  →  Apache  →  Cliente web
```

---