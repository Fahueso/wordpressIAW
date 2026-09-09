# 1. Bases de datos con MariaDB

En los bloques anteriores hemos preparado el servidor web (Apache) y el motor de aplicación (PHP). El último componente del stack LAMP que nos queda por instalar es el **sistema gestor de bases de datos**.

Sin este componente, Apache y PHP pueden generar contenido dinámico, pero no pueden almacenar información de forma permanente: usuarios, cursos, productos, mensajes, etc.

En este módulo utilizaremos **MariaDB**, un SGBD compatible con MySQL y muy extendido en distribuciones Linux como Debian y Ubuntu.

```text
Cliente web
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

---

## 1.1 Instalación de MariaDB

### Requisitos previos

Como en instalaciones anteriores, es recomendable actualizar la información de los repositorios antes de instalar software nuevo:

```bash
sudo apt update
```

### Instalación del paquete

MariaDB se distribuye en Debian y Ubuntu mediante el paquete:

```text
mariadb-server
```

La instalación se realiza con:

```bash
sudo apt install mariadb-server
```

Este paquete instala tanto el servidor de bases de datos como el cliente de línea de comandos necesario para administrarlo.

### Comprobación del servicio

Tras la instalación, MariaDB suele arrancar automáticamente como servicio gestionado por systemd.

```bash
sudo systemctl status mariadb
```

Resultado esperado:

```text
Active: active (running)
```

Al igual que con Apache, disponemos de los comandos habituales de gestión del servicio:

```bash
sudo systemctl start mariadb
sudo systemctl stop mariadb
sudo systemctl restart mariadb
sudo systemctl reload mariadb
```

### Comprobación de la versión instalada

```bash
mariadb --version
```

Ejemplo de resultado:

```text
mariadb  Ver 15.1 Distrib 10.x.x-MariaDB
```

---

## 1.2 Seguridad básica de la instalación

Una instalación recién realizada de MariaDB no está configurada de forma segura por defecto. Por ello, el propio paquete incluye un script de configuración inicial.

### El script mysql_secure_installation

```bash
sudo mysql_secure_installation
```

Este asistente interactivo permite, entre otras cosas:

- Establecer una contraseña para el usuario `root` de la base de datos.
- Eliminar usuarios anónimos.
- Deshabilitar el acceso remoto del usuario `root`.
- Eliminar la base de datos de prueba (`test`).
- Recargar los privilegios para aplicar los cambios inmediatamente.

Durante el proceso se realizan preguntas similares a:

```text
Set root password? [Y/n]
Remove anonymous users? [Y/n]
Disallow root login remotely? [Y/n]
Remove test database and access to it? [Y/n]
Reload privilege tables now? [Y/n]
```

> Es importante no saltarse este paso: una instalación de MariaDB sin asegurar es una de las causas más habituales de compromisos de seguridad en servidores web.

---

## 1.3 Acceso al cliente de MariaDB

Una vez asegurada la instalación, podemos acceder a la consola de administración:

```bash
sudo mariadb -u root -p
```

El sistema solicitará la contraseña establecida en el paso anterior.

Si el acceso es correcto, aparecerá un prompt similar a:

```text
MariaDB [(none)]>
```

Desde aquí podemos ejecutar sentencias SQL directamente sobre el servidor.

Para salir de la consola:

```sql
EXIT;
```

---

## 1.4 Operaciones básicas de administración

### Crear una base de datos

```sql
CREATE DATABASE tienda;
```

### Listar las bases de datos existentes

```sql
SHOW DATABASES;
```

Resultado habitual:

```text
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| tienda             |
+--------------------+
```

### Seleccionar una base de datos

```sql
USE tienda;
```

### Crear una tabla

```sql
CREATE TABLE productos (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(100) NOT NULL,
    precio DECIMAL(10,2) NOT NULL
);
```

### Insertar datos

```sql
INSERT INTO productos (nombre, precio) VALUES ('Teclado', 25.90);
INSERT INTO productos (nombre, precio) VALUES ('Ratón', 12.50);
```

### Consultar datos

```sql
SELECT * FROM productos;
```

Estas operaciones corresponden al **CRUD** (Create, Read, Update, Delete) ya estudiado en el Bloque 1 al hablar de bases de datos en aplicaciones web.

---

## 1.5 Usuarios y privilegios

Por motivos de seguridad, **las aplicaciones web nunca deben conectarse a la base de datos utilizando el usuario `root`**.

Lo habitual es crear un usuario específico con permisos limitados a la base de datos que necesita utilizar.

### Crear un usuario

```sql
CREATE USER 'appweb'@'localhost' IDENTIFIED BY 'contraseña_segura';
```

### Conceder privilegios sobre una base de datos concreta

```sql
GRANT ALL PRIVILEGES ON tienda.* TO 'appweb'@'localhost';
```

### Aplicar los cambios

```sql
FLUSH PRIVILEGES;
```

### Comprobar los privilegios de un usuario

```sql
SHOW GRANTS FOR 'appweb'@'localhost';
```

### Revocar privilegios

```sql
REVOKE ALL PRIVILEGES ON tienda.* FROM 'appweb'@'localhost';
```

### Eliminar un usuario

```sql
DROP USER 'appweb'@'localhost';
```

---

## 1.6 phpMyAdmin

Administrar bases de datos mediante la consola es fundamental para comprender su funcionamiento, pero en el día a día resulta habitual utilizar una herramienta gráfica.

**phpMyAdmin** es una aplicación web escrita en PHP que permite administrar bases de datos MariaDB o MySQL desde el navegador.

De hecho, phpMyAdmin es en sí misma un buen ejemplo práctico de aplicación del stack LAMP completo:

```text
Cliente web
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

### Instalación

```bash
sudo apt install phpmyadmin
```

Durante la instalación, el asistente preguntará:

- Qué servidor web se debe configurar automáticamente (seleccionar `apache2`).
- Si se desea configurar una base de datos para phpMyAdmin mediante `dbconfig-common`.
- La contraseña de administrador de MariaDB.

### Acceso

Una vez finalizada la instalación, phpMyAdmin suele quedar accesible en:

```text
http://localhost/phpmyadmin
```

Si el asistente no configuró Apache automáticamente, puede ser necesario habilitar la configuración manualmente:

```bash
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
sudo a2enconf phpmyadmin
sudo systemctl reload apache2
```

> Al igual que con `phpinfo()`, en un entorno de producción real conviene restringir el acceso a phpMyAdmin (por IP, autenticación adicional o directamente eliminarlo) para reducir la superficie de ataque.

---

## 1.7 Copias de seguridad básicas

Aunque las copias de seguridad se estudiarán con más detalle en otros módulos, es importante conocer las herramientas básicas que ofrece MariaDB.

### Exportar una base de datos

```bash
mysqldump -u root -p tienda > tienda_backup.sql
```

### Restaurar una base de datos

```bash
mysql -u root -p tienda < tienda_backup.sql
```

Estas herramientas resultan útiles antes de realizar cambios importantes en la estructura de una base de datos, o como parte de la documentación de un proyecto.

---

## 1.8 Resolución de problemas habituales

### MariaDB no arranca

```bash
sudo systemctl status mariadb
sudo journalctl -u mariadb
```

### Acceso denegado (Access denied for user)

Suele deberse a:

- Contraseña incorrecta.
- Usuario sin privilegios sobre la base de datos.
- Usuario definido para un host distinto de `localhost`.

Comprobar los privilegios:

```sql
SHOW GRANTS FOR 'usuario'@'localhost';
```

### PHP no puede conectar con MariaDB

Comprobar que la extensión está instalada y cargada:

```bash
php -m | grep mysqli
sudo apache2ctl -M | grep php
```

Revisar el registro de errores de Apache:

```bash
sudo tail /var/log/apache2/error.log
```

### El puerto de MariaDB está ocupado

Por defecto MariaDB escucha en el puerto 3306:

```bash
sudo ss -tulpn | grep :3306
```

---

## 1.9 Buenas prácticas

- Ejecutar siempre `mysql_secure_installation` tras la instalación.
- No utilizar el usuario `root` de la base de datos en las aplicaciones.
- Crear un usuario específico con privilegios mínimos para cada aplicación.
- Utilizar siempre sentencias preparadas para evitar inyección SQL.
- Restringir el acceso a herramientas como phpMyAdmin.
- Realizar copias de seguridad periódicas con `mysqldump`.
- Revisar los registros ante cualquier error de conexión.

