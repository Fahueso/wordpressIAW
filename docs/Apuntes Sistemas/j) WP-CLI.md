# Uso de WP-CLI en WordPress

WP-CLI (WordPress Command Line Interface) es una herramienta poderosa que permite gestionar y administrar WordPress desde la línea de comandos. Facilita tareas comunes como la instalación de plugins, actualizaciones, configuraciones y más, sin necesidad de acceder al panel de administración web.

---

## 1. **Instalación de WP-CLI**

1. **Descargar WP-CLI**:
   ```
   curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
   ```

2. **Hacerlo ejecutable**:
   ```
   chmod +x wp-cli.phar
   ```

3. **Moverlo a un directorio en PATH**:
   ```
   sudo mv wp-cli.phar /usr/local/bin/wp
   ```

4. **Verificar la instalación**:
Siempre que vayamos a utilizar el nuevo comando wp, debe de hacerse a nivel de los ficheros del wordpress a manipular. En nuestro caso /var/www/html/
   ```
   wp --info
   ```

5. **Verificar permisos**:
El usuario que ejecuta un comando CLI que escriba en el sistema de archivos debe de tener permisos. Muchas veces el usuario de la carpeta /var/www/html es www-data, por lo que algunos comando requerirán sudo. Por ejemplo, este comando elimina un plugin existente en la instalación por defecto de Wordpress (Akismet):
```
 sudo -u www-data wp plugin delete akismet
```

---

## 2. **Comandos Básicos**

### 2.1 Gestión de WordPress
- **Actualizar WordPress**:
  ```
  wp core update
  ```

- **Actualizar la base de datos**:
  ```
  wp core update-db
  ```

- **Verificar el estado de WordPress**:
  ```
  wp core is-installed
  ```
  
- **Especificar una instalación concreta**:
  ```
  wp core is-installed --path=/ruta/a/wordpress
  ```
  Si hay múltiples instalaciones en el mismo servidor, usar `--path` garantiza que WP-CLI se ejecute en la instalación correcta.

### 2.2 Gestión de Plugins
- **Instalar un plugin**:
  ```
  wp plugin install plugin-name --activate
  ```

- **Actualizar todos los plugins**:
  ```
  wp plugin update --all
  ```

- **Eliminar un plugin**:
  ```
  wp plugin delete plugin-name
  ```

### 2.3 Gestión de Temas
- **Instalar un tema**:
  ```
  wp theme install theme-name --activate
  ```

- **Actualizar todos los temas**:
  ```
  wp theme update --all
  ```

- **Eliminar un tema**:
  ```
  wp theme delete theme-name
  ```

### 2.4 Gestión de Usuarios
- **Crear un usuario**:
  ```
  wp user create username email@example.com --role=author
  ```

- **Listar todos los usuarios**:
  ```
  wp user list
  ```

- **Eliminar un usuario**:
  ```
  wp user delete user-id --reassign=another-user-id
  ```

---

## 3. **Ventajas de Usar WP-CLI**

1. **Rapidez**:
   - Ejecutar comandos desde la terminal es mucho más rápido que usar la interfaz gráfica.

2. **Automatización**:
   - Ideal para tareas repetitivas o de mantenimiento en múltiples sitios.

3. **Administración Remota**:
   - Puedes gestionar WordPress en servidores remotos sin necesidad de un navegador.

4. **Compatibilidad**:
   - Funciona con la mayoría de configuraciones de WordPress y plugins.

Visitar: 
https://wp-cli.org/
https://make.wordpress.org/cli/handbook/guides/commands-cookbook/



