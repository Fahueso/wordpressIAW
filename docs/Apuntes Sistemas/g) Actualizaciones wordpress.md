# Sistema de Actualización de WordPress

El sistema de actualización de WordPress asegura que tu sitio web esté siempre al día con las últimas características, mejoras de rendimiento y correcciones de seguridad. A continuación, se detalla cómo funciona el sistema de actualización y las mejores prácticas para gestionarlo.

---

## 1. **Tipos de Actualizaciones en WordPress**

1. **Actualizaciones de Core (Núcleo):**
   - Incluyen nuevas versiones de WordPress.
   - Se dividen en:
     - **Actualizaciones principales:** Introducen nuevas funcionalidades y mejoras significativas (por ejemplo, pasar de 6.1 a 6.2).
     - **Actualizaciones menores:** Se centran en parches de seguridad y correcciones de errores (por ejemplo, 6.1.1 a 6.1.2).

2. **Actualizaciones de Temas:**
   - Mejoran la compatibilidad, corrigen errores y añaden nuevas funcionalidades a los temas instalados.

3. **Actualizaciones de Plugins:**
   - Aseguran que los plugins funcionen correctamente con las últimas versiones de WordPress.
   - Pueden incluir nuevas características y parches de seguridad.

4. **Traducciones:**
   - Actualizaciones de los archivos de idioma para mantener las traducciones precisas.

---

## 2. **Cómo Funciona el Sistema de Actualización**

### 2.1 Actualizaciones Automáticas

WordPress realiza automáticamente las actualizaciones menores del núcleo y las traducciones, reduciendo el riesgo de vulnerabilidades.

- **Por defecto:**
  - Las actualizaciones menores y de seguridad del núcleo están habilitadas.
  - Las actualizaciones automáticas para plugins y temas deben activarse manualmente.

### 2.2 Actualizaciones Manuales

1. Accede a **Escritorio > Actualizaciones** en el panel de administración.
2. Revisa las actualizaciones disponibles para:
   - El núcleo de WordPress.
   - Plugins.
   - Temas.
3. Selecciona los elementos a actualizar y haz clic en "Actualizar".

---

## 3. **Configuración de Actualizaciones Automáticas**

1. **Para Plugins y Temas:**
   - Ve a **Plugins > Instalados** o **Apariencia > Temas**.
   - Haz clic en "Habilitar actualizaciones automáticas" junto a cada elemento.

2. **Personalización Avanzada:**
   - Agrega las siguientes líneas al archivo `wp-config.php` para configurar las actualizaciones automáticas:
     ```php
     define('WP_AUTO_UPDATE_CORE', true); // Habilita todas las actualizaciones del núcleo
     define('AUTOMATIC_UPDATER_DISABLED', false); // Habilita actualizaciones automáticas
     ```

---

## 4. **Buenas Prácticas para Gestionar Actualizaciones**

1. **Realiza Copias de Seguridad:**
   - Antes de cualquier actualización, realiza una copia de seguridad completa del sitio (archivos y base de datos).
   - Usa plugins como UpdraftPlus o herramientas del hosting.

2. **Revisa la Compatibilidad:**
   - Verifica si las actualizaciones de plugins y temas son compatibles con tu versión actual de WordPress.
   - Consulta los registros de cambios (changelogs) para detalles sobre las actualizaciones.

3. **Actualiza en un Entorno de Pruebas:**
   - Si tienes un sitio complejo, prueba las actualizaciones en un entorno de desarrollo antes de aplicarlas en producción.

4. **Mantén Todo Actualizado:**
   - Las actualizaciones regulares reducen el riesgo de vulnerabilidades y errores.

---

## 5. **Gestión de Actualizaciones con Plugins**

1. **Plugins de Gestión Automática:**
   - Usa herramientas como **Easy Updates Manager** para personalizar qué actualizaciones se aplican automáticamente.

2. **Notificaciones:**
   - Configura notificaciones por correo electrónico para estar informado sobre las actualizaciones pendientes.

---

## 6. **Errores Comunes y Cómo Solucionarlos**

1. **Problemas de Compatibilidad:**
   - Si un plugin o tema causa errores después de una actualización, desactívalo temporalmente desde **Plugins > Instalados** o **Apariencia > Temas**, seleccionando "Desactivar" junto al elemento problemático.

2. **Actualización Interrumpida:**
   - Si ves el mensaje "El sitio está en modo de mantenimiento":
     - Elimina el archivo `.maintenance` de la raíz de WordPress usando FTP.

3. **Fallo en la Actualización:**
   - Restaura la copia de seguridad más reciente y revisa los registros de error para identificar el problema.

---

## 7. **Deshabilitar Plugins desde la Base de Datos**

En casos donde un plugin problemático impida el acceso al panel de administración, puedes deshabilitarlo desde la base de datos de WordPress.

### Pasos para Deshabilitar Plugins desde SQL

1. **Accede a la Base de Datos:**
   - Usa phpMyAdmin o un cliente MySQL desde la terminal:
     ```bash
     mysql -u usuario -p
     ```
2. **Selecciona la Base de Datos:**
   ```sql
   USE nombre_de_tu_base_de_datos;
   ```
3. **Verifica los Plugins Activos:**
   - Consulta la tabla `wp_options` para encontrar la opción `active_plugins`:
     ```sql
     SELECT option_value FROM wp_options WHERE option_name = 'active_plugins';
     ```
4. **Desactiva Todos los Plugins:**
   - Actualiza el valor de `active_plugins` a una cadena vacía:
     ```sql
     UPDATE wp_options SET option_value = 'a:0:{}' WHERE option_name = 'active_plugins';
     ```
5. **Desactiva un Plugin Específico:**
   - Si necesitas desactivar un único plugin, edita manualmente el valor de `active_plugins` para eliminar su entrada. Esto requiere familiaridad con la serialización de PHP.

6. **Verifica los Cambios:**
   - Accede nuevamente al sitio para confirmar que el plugin problemático ha sido desactivado.

---

Con un sistema de actualización bien gestionado y la capacidad de deshabilitar plugins desde SQL, tu sitio WordPress estará protegido, optimizado y preparado para las últimas tecnologías.
