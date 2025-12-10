# Sistema de Archivos de WordPress

El sistema de archivos de WordPress es la estructura que contiene todos los elementos necesarios para el funcionamiento del CMS. Comprender su organización es crucial para realizar personalizaciones, solucionar problemas y gestionar el sitio de manera eficiente.

---

## 1. **Estructura Básica del Sistema de Archivos**

Cuando instalas WordPress, los archivos principales se organizan en la siguiente estructura:

```
/wordpress
├── wp-admin
├── wp-content
├── wp-includes
├── index.php
├── wp-config-sample.php
├── wp-config.php
├── .htaccess
└── wp-load.php
```

---

## 2. **Directorios Principales**

### 2.1 `/wp-admin`

- **Descripción:** Contiene todos los archivos relacionados con el panel de administración de WordPress.
- **Funciones clave:**
  - Gestión del contenido, usuarios y configuraciones.
  - No se recomienda modificar los archivos de este directorio.
- **Archivos importantes:**
  - `admin.php`: Punto de entrada para el panel de administración.

### 2.2 `/wp-content`

- **Descripción:** Aquí se almacena todo el contenido personalizado del sitio.
- **Subdirectorios clave:**
  - `/themes`: Contiene los temas instalados en WordPress.
  - `/plugins`: Guarda los plugins instalados.
  - `/uploads`: Almacena imágenes, documentos y otros archivos subidos al sitio.
  - `/mu-plugins`: Plugins obligatorios cargados automáticamente.
- **Personalización:** Este es el único directorio donde se recomienda realizar cambios.

### 2.3 `/wp-includes`

- **Descripción:** Contiene los archivos principales del núcleo de WordPress.
- **Funciones clave:**
  - Proporciona las funciones esenciales para que WordPress funcione.
  - Incluye bibliotecas, API y archivos de configuración interna.
- **Archivos importantes:**
  - `functions.php`: Contiene funciones globales.
  - `class-wp.php`: Define la estructura principal de WordPress.

---

## 3. **Archivos Clave en la Raíz**

### 3.1 `index.php`

- **Función:** Archivo principal que inicia la carga de WordPress.
- **Nota:** Este archivo no se modifica.

### 3.2 `wp-config.php`

- **Función:** Configuración del sitio, incluyendo la conexión a la base de datos.
- **Opciones clave:**
  ```php
  define('DB_NAME', 'nombre_base_datos');
  define('DB_USER', 'usuario_base_datos');
  define('DB_PASSWORD', 'contraseña');
  define('DB_HOST', 'localhost');
  ```
- **Personalización recomendada:**
  - Configurar claves de seguridad únicas.
  - Definir prefijos personalizados para las tablas de la base de datos.

### 3.3 `.htaccess`

- **Función:** Gestiona las reglas del servidor web (principalmente Apache).
- **Funciones comunes:**
  - Configuración de enlaces permanentes.
  - Redirecciones y reglas de seguridad.

### 3.4 `wp-load.php`

- **Función:** Punto de entrada para cargar los archivos y bibliotecas principales de WordPress.

---

## 4. **Mejoras y Buenas Prácticas**

1. **Realiza backups antes de modificar archivos:**
   - Especialmente para `wp-config.php` y `.htaccess`.

2. **Mantén el núcleo intacto:**
   - Evita modificar archivos dentro de `/wp-includes` y `/wp-admin`.

3. **Protege archivos sensibles:**
   - Usa permisos seguros:
     ```bash
     chmod 640 wp-config.php
     chmod 644 .htaccess
     ```
   - Bloquea accesos no autorizados con reglas en `.htaccess` o configuraciones de Nginx.

4. **Usa un tema hijo:**
   - Para personalizar temas sin alterar los archivos originales en `/wp-content/themes`.

---

Con esta guía, puedes navegar y gestionar el sistema de archivos de WordPress de manera eficiente, manteniendo la seguridad y el rendimiento del sitio.
