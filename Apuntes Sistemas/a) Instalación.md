# Instalación de WordPress en un Servidor Debian/Ubuntu

En este documento se detallan los pasos para instalar WordPress en un servidor Debian con Apache, PHP y MySQL ya instalados. También se incluye una guía para desplegar WordPress en XAMPP, usando Docker-Compose y entornos de tipo cPanel, soluciones comunes para desarrollo.

---

## 1. **Preparativos Iniciales**

### 1.1 Verificación del Entorno

Antes de comenzar, asegúrate de que:

- Apache esté en ejecución: `sudo systemctl status apache2`
- PHP esté instalado y funcional: `php -v`
- MySQL esté corriendo: `sudo systemctl status mysql`

Instala paquetes adicionales necesarios:

```bash
sudo apt update
sudo apt install php-mysql php-curl php-gd php-xml php-mbstring unzip curl -y
```

Reinicia Apache para aplicar los cambios:

```bash
sudo systemctl restart apache2
```

### 1.2 Creación de la Base de Datos

1. Inicia sesión en MySQL:
   ```bash
   sudo mysql -u root -p
   ```
2. Crea una nueva base de datos:
   ```sql
   CREATE DATABASE wordpress;
   ```
3. Crea un usuario y asigna permisos:
   ```sql
   CREATE USER 'wordpressuser'@'localhost' IDENTIFIED BY 'tu_contraseña_segura';
   GRANT ALL PRIVILEGES ON wordpress.* TO 'wordpressuser'@'localhost';
   FLUSH PRIVILEGES;
   EXIT;
   ```

### ¿Por qué no usar el usuario root en MySQL?

Utilizar el usuario `root` en MySQL para aplicaciones como WordPress supone un riesgo de seguridad significativo. Algunas razones clave incluyen:

- **Exposición de privilegios**:

  - Si un atacante obtiene acceso a la base de datos a través de una vulnerabilidad en WordPress, tendría control total sobre todas las bases de datos y configuraciones.

- **Buenas prácticas de seguridad**:

  - Los usuarios con privilegios limitados minimizan el impacto potencial de un compromiso.

- **Separación de responsabilidades**:

  - Crear usuarios específicos para cada aplicación ayuda a gestionar permisos y auditorías de forma más clara y efectiva.

Por estas razones, es esencial usar un usuario dedicado con permisos limitados para garantizar la seguridad y estabilidad del sistema.

---

## 2. **Descarga e Instalación de WordPress**

### 2.1 Descarga de WordPress

1. Descarga la última versión de WordPress desde su sitio oficial:
   ```bash
   curl -O https://wordpress.org/latest.zip
   ```
2. Descomprime el archivo:
   ```bash
   unzip latest.zip
   ```
3. Mueve los archivos a la raíz del servidor web:
   ```bash
   sudo mv wordpress/* /var/www/html/
   ```

### 2.2 Configuración de Permisos

Asegúrate de que WordPress tenga los permisos necesarios:

```bash
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```

### 2.3 Configuración del Archivo `wp-config.php`

1. Copia el archivo de configuración:
   ```bash
   sudo cp /var/www/html/wp-config-sample.php /var/www/html/wp-config.php
   ```
2. Edita el archivo para incluir los detalles de la base de datos:
   ```bash
   sudo nano /var/www/html/wp-config.php
   ```
   Cambia las siguientes líneas:
   ```php
   define('DB_NAME', 'wordpress');
   define('DB_USER', 'wordpressuser');
   define('DB_PASSWORD', 'tu_contraseña_segura');
   define('DB_HOST', 'localhost');
   ```

---

## 3. **Configuración en el Navegador**

1. Accede a la dirección IP del servidor desde tu navegador:
   ```
   http://<tu-servidor>
   ```
2. Completa el asistente de instalación de WordPress:
   - Selecciona el idioma.
   - Introduce el título del sitio, el nombre de usuario, contraseña y correo electrónico.
   - Haz clic en "Instalar WordPress".

---

## 4. **Post-Instalación**

### 4.1 Configuración Básica

- Ajusta los enlaces permanentes desde "Ajustes > Enlaces Permanentes".
- Instala los plugins esenciales desde el panel de administración.

### 4.2 Seguridad

- Elimina el archivo `readme.html` para mayor seguridad:
  ```bash
  sudo rm /var/www/html/readme.html
  ```
- Instala un plugin de seguridad como Wordfence.

### 4.3 Copias de Seguridad

Configura un sistema de backups regulares con herramientas como UpdraftPlus o mediante scripts personalizados.

---

## 5. **Despliegue en XAMPP**

XAMPP es una herramienta popular para desarrollar sitios WordPress de forma local. Estos son los pasos para instalar WordPress en XAMPP:

### 5.1 Preparar el Entorno

1. Descarga e instala XAMPP desde su sitio oficial: [apachefriends.org](https://www.apachefriends.org/).
2. Inicia los servicios de Apache y MySQL desde el Panel de Control de XAMPP.

### 5.2 Crear la Base de Datos

1. Accede a phpMyAdmin desde: `http://localhost/phpmyadmin`.
2. Crea una nueva base de datos llamada `wordpress`.
3. No es necesario crear un usuario adicional en este caso, puedes usar el usuario `root` sin contraseña (solo para entornos locales).

### 5.3 Instalar WordPress

1. Descarga WordPress desde [wordpress.org](https://wordpress.org/).
2. Extrae los archivos y cópialos a la carpeta `htdocs` de XAMPP (por ejemplo, `C:\xampp\htdocs\wordpress`).
3. Accede a `http://localhost/wordpress` desde tu navegador.
4. Completa el asistente de instalación ingresando:
   - **Nombre de la base de datos**: `wordpress`.
   - **Usuario**: `root`.
   - **Contraseña**: (dejar en blanco).
5. Haz clic en "Instalar WordPress".

### 5.4 Configuración Posterior

- Configura enlaces permanentes desde el panel de administración.
- Realiza ajustes visuales y funcionales según las necesidades del proyecto.

---

## 6. **Despliegue con Docker-Compose**

Docker-Compose es una herramienta que permite configurar y ejecutar múltiples contenedores Docker. Estos son los pasos para desplegar WordPress con Docker-Compose:

### 6.1 Crear el Archivo `docker-compose.yml`

1. Crea un archivo llamado `docker-compose.yml`.
2. Añade el siguiente contenido:
   ```yaml
   version: '3.8'
   services:
     db:
       image: mysql:5.7
       volumes:
         - db_data:/var/lib/mysql
       restart: always
       environment:
         MYSQL_ROOT_PASSWORD: tu_contraseña_segura
         MYSQL_DATABASE: wordpress
         MYSQL_USER: wordpressuser
         MYSQL_PASSWORD: tu_contraseña_segura

     wordpress:
       image: wordpress:latest
       ports:
         - "8080:80"
       restart: always
       volumes:
         - wordpress_data:/var/www/html
       environment:
         WORDPRESS_DB_HOST: db:3306
         WORDPRESS_DB_USER: wordpressuser
         WORDPRESS_DB_PASSWORD: tu_contraseña_segura
         WORDPRESS_DB_NAME: wordpress

   volumes:
     db_data:
     wordpress_data:
   ```

### 6.2 Ejecutar Docker-Compose

1. Abre una terminal en la carpeta donde se encuentra el archivo `docker-compose.yml`.
2. Ejecuta el siguiente comando:
   ```bash
   docker-compose up -d
   ```

### 6.3 Acceder al Sitio

1. Abre tu navegador y accede a:
   ```
   http://localhost:8080
   ```
2. Completa el asistente de instalación de WordPress.

### 6.4 Detener y Reiniciar el Servicio

- Para detener los contenedores:
  ```bash
  docker-compose down
  ```
- Para reiniciar los contenedores:
  ```bash
  docker-compose up -d
  ```
# Fichero alternativo docker-compose:

```bash
version: '3'

services:
  # Database
  db:
    image: mysql:5.7
    volumes:
      - db_data:/var/lib/mysql
    restart: always
    environment:
      MYSQL_ROOT_PASSWORD: password
      MYSQL_DATABASE: wordpress
      MYSQL_USER: wordpress
      MYSQL_PASSWORD: wordpress
    networks:
      - wpsite
  # phpmyadmin
  phpmyadmin:
    depends_on:
      - db
    image: phpmyadmin/phpmyadmin
    restart: always
    ports:
      - '8080:80'
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: password 
    networks:
      - wpsite
  # Wordpress
  wordpress:
    depends_on:
      - db
    image: wordpress:latest
    ports:
      - '8000:80'
    restart: always
    volumes: ['./:/var/www/html/otroworpress']
    environment:
      WORDPRESS_DB_HOST: db:3306
      WORDPRESS_DB_USER: wordpress
      WORDPRESS_DB_PASSWORD: wordpress
    networks:
      - wpsite
networks:
  wpsite:
volumes:
  db_data:
```