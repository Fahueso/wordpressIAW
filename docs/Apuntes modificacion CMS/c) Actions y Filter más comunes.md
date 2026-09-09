# **ACTIONS más comunes (acciones)**

Las **actions** permiten ejecutar código cuando WordPress llega a un punto concreto del proceso.

|Action|Cuándo se ejecuta|Para qué sirve|
|---|---|---|
|**init**|Cuando WordPress arranca|Registrar shortcodes, CPT, taxonomías|
|**wp_enqueue_scripts**|Antes de cargar scripts del front|Añadir CSS y JS al tema|
|**admin_enqueue_scripts**|Antes de cargar scripts del admin|Añadir CSS/JS al panel|
|**admin_notices**|Al mostrar avisos en el admin|Mostrar mensajes personalizados|
|**wp_head**|Dentro del `<head>` del front|Insertar meta tags, estilos, scripts|
|**wp_footer**|Antes del `</body>`|Scripts, contadores, mensajes|
|**template_redirect**|Antes de cargar una plantilla|Redirecciones, comprobaciones|
|**save_post**|Al guardar una entrada|Automatizar tareas al guardar|
|**login_enqueue_scripts**|En la pantalla de login|Personalizar el login|

---

# 🟩 **FILTERS más comunes (filtros)**

Los **filters** permiten modificar datos ANTES de que WordPress los use o los muestre.

|Filter|Qué modifica|Para qué sirve|
|---|---|---|
|**the_content**|El contenido de la entrada|Añadir texto antes/después|
|**the_title**|El título de la entrada|Cambiar o decorar títulos|
|**excerpt_length**|Longitud del extracto|Cambiar número de palabras|
|**excerpt_more**|Texto “leer más”|Personalizar el final del extracto|
|**upload_mimes**|Tipos de archivo permitidos|Permitir SVG, WebP, etc.|
|**widget_text**|Contenido de widgets|Permitir HTML o shortcodes|
|**login_message**|Mensaje en login|Añadir avisos en login|
|**body_class**|Clases del `<body>`|Añadir clases personalizadas|
