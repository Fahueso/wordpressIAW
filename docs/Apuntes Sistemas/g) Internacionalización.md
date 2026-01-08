# Modelo de Internacionalización en WordPress

WordPress tiene un sistema robusto de internacionalización (i18n) y localización (l10n) que permite traducir y adaptar un sitio web o un plugin a diferentes idiomas y culturas. Este modelo facilita la creación de sitios web multilingües y accesibles globalmente.

---

## 1. **Conceptos Clave**

1. **Internacionalización (i18n):**
   - Proceso de preparar el código para que pueda traducirse fácilmente.
   - Incluye el uso de funciones específicas para envolver textos que se mostrarán en diferentes idiomas.

2. **Localización (l10n):**
   - Proceso de traducir y adaptar el contenido a un idioma y cultura específicos.
   - Incluye archivos de traducción con extensiones `.mo` y `.po`.

3. **Idiomas en WordPress:**
   - WordPress soporta más de 70 idiomas gracias a su comunidad de traducción.
   - Los idiomas del sitio pueden configurarse desde el panel de administración.

---

## 2. **Configuración del Idioma del Sitio**

1. Ve a **Ajustes > Generales** en el panel de administración.
2. En "Idioma del sitio", selecciona el idioma deseado del menú desplegable.
3. Guarda los cambios.
4. WordPress descargará automáticamente los archivos de idioma correspondientes si están disponibles.

---

## 3. **Archivos de Traducción en WordPress**

### Estructura de Archivos

1. **Archivos `.po` (Portable Object):**
   - Contienen las cadenas de texto en su idioma original y las traducciones.
   - Se editan con herramientas como Poedit.

2. **Archivos `.mo` (Machine Object):**
   - Versión compilada del archivo `.po` que WordPress utiliza para mostrar traducciones.

3. **Ubicación de Archivos de Idioma:**
   - Idiomas del núcleo de WordPress:
     ```
     /wp-content/languages
     ```
   - Idiomas de temas:
     ```
     /wp-content/themes/tu-tema/languages
     /wp-content/themes/languages/*
     ```
   - Idiomas de plugins:
     ```
     /wp-content/plugins/tu-plugin/languages
     /wp-content/plugins/languages/*
     ```

3. **Archivos json:**
* Desde hace mucho tiempo los plugins y temas pueden incluir traducciones para el editor de bloques en archivos .json ubicados en /languages/
---

## 4. **Funciones de Internacionalización en WordPress**

1. **`__()` y `_e()`**
   - `__()` devuelve una cadena traducida.
   - `_e()` imprime directamente una cadena traducida.
   ```php
   echo __( 'Hello, World!', 'text-domain' );
   _e( 'Welcome to my site.', 'text-domain' );
   ```

2. **`_x()` y `ex()`**
   - Proporcionan contexto adicional para cadenas ambiguas.
   ```php
   echo _x( 'Post', 'noun', 'text-domain' );
   ```

3. **`ngettext()`**
   - Maneja traducciones para singular y plural.
   ```php
   echo sprintf( _n( '%s comment', '%s comments', $count, 'text-domain' ), $count );
   ```

4. **`load_textdomain()`**
   - Carga archivos de traducción manualmente.
   ```php
   load_textdomain( 'text-domain', WP_LANG_DIR . '/plugins/my-plugin-es_ES.mo' );
   ```

---

## 5. **Traducción de Temas y Plugins**

1. **Añadir un Text Domain**
   - Define un "text domain" en el encabezado del archivo principal del tema o plugin.
   ```php
   /*
    * Plugin Name: Mi Plugin
    * Text Domain: mi-plugin
    */
   ```

Ejemplo: para el tema Astra podemos encontrar la identificación del dominio en la ruta `/themes/astra/inc/class-astra-after-setup-theme.php`. Podemos usar el comando `grep -Ri "Text Domain" .` para buscar en generar los `text domains` existentes.


1. **Preparar el Código para Traducción**
   - Usa funciones de internacionalización para envolver cadenas de texto.
   - Asegúrate de que el "text domain" coincida con el definido en el encabezado.

3. **Generar Archivos `.pot` (Portable Object Template)**
   - Usa herramientas como Poedit o plugins como Loco Translate para extraer las cadenas traducibles.

4. **Subir Archivos de Traducción**
   - Coloca los archivos `.mo` y `.po` en las carpetas correspondientes.

---

## 6. **Sitios Multilingües**

WordPress no tiene soporte multilingüe nativo para gestionar varios idiomas en un mismo sitio. Aunque se pueden crear versiones separadas de contenido manualmente, esto requiere una gran cantidad de trabajo y no es eficiente ni práctico para sitios más grandes o con actualizaciones frecuentes. Por ello, es necesario utilizar plugins multilingües que gestionen automáticamente el contenido en diferentes idiomas y simplifiquen la administración del sitio.

### ¿Por qué hacen falta plugins para sitios multilingües?

1. **Gestión Centralizada de Idiomas:**
   - Los plugins permiten configurar y administrar varios idiomas desde un solo panel, evitando la necesidad de crear múltiples sitios o páginas duplicadas manualmente.

2. **Traducción de Contenido:**
   - Facilitan la traducción de entradas, páginas, menús, widgets y otros elementos, proporcionando interfaces dedicadas para realizar esta tarea.

3. **SEO Multilingüe:**
   - Aseguran que cada idioma tenga una estructura de URL adecuada (por ejemplo, `example.com/en/` para inglés y `example.com/es/` para español), mejorando el SEO y la visibilidad en motores de búsqueda.

4. **Sincronización de Contenido:**
   - Los plugins gestionan la relación entre el contenido en diferentes idiomas, asegurando que las actualizaciones en un idioma puedan replicarse fácilmente en los demás.

5. **Widgets y Funciones Especializadas:**
   - Ofrecen herramientas como selectores de idioma, traducción automática y opciones avanzadas para personalizar la experiencia del usuario.

6. **Compatibilidad con Otros Plugins y Temas:**
   - Los plugins multilingües garantizan que el contenido traducido sea compatible con otros plugins y temas instalados, evitando conflictos o problemas de funcionalidad.

### Plugins Multilingües Populares

1. **Polylang:**
   - Configura varios idiomas en tu sitio.
   - Traduce entradas, páginas, menús y widgets.
   
2. **WPML (WordPress Multilingual Plugin):**
   - Solución completa para sitios multilingües con opciones avanzadas.

3. **Weglot:**
   - Servicio basado en la nube para traducción automática y manual.

4. **TranslatePress:**
   - Permite traducir el contenido directamente desde la interfaz del sitio.

---

## 7. **Mejores Prácticas para Internacionalización**

1. **Usa Funciones de WordPress:**
   - Garantiza compatibilidad futura y consistencia.

2. **Evita Cadenas de Texto Fijas:**
   - No incluyas texto directamente en HTML o PHP sin envolverlo en funciones de traducción.

3. **Usa Text Domains Únicos:**
   - Asegúrate de que cada tema o plugin tenga su propio dominio de texto.

4. **Prueba con Idiomas Diferentes:**
   - Cambia el idioma del sitio y verifica que todas las cadenas se traduzcan correctamente.

---


