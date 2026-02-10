Es un plugin muy seguro, muy usado, y permite añadir pequeños fragmentos de código PHP sin crear un plugin completo.

- No rompe el sitio si el código falla (tiene protección).
- Permite activar/desactivar cada snippet.
- Puedes organizar los snippets por categorías.
- Perfecto para enseñar hooks (`add_action`, `add_filter`).


# Cómo instalar Code Snippets (paso a paso)

1. Entra en **Escritorio → Plugins → Añadir nuevo**.
2. Busca: **Code Snippets**.
3. Instálalo y actívalo.
4. Aparecerá un nuevo menú: **Snippets**.

---


# Cómo crear un snippet de prueba

1. Ve a **Snippets → Add New**.
2. Pon un título:  
    **“Prueba de add_action”**
3. En el área de código, pega algo como:

```php
add_action('init', function() {
    error_log('El hook init se ha ejecutado');
});
```

4. Marca **Run snippet everywhere**.
5. Guarda y activa.

Ahora, cada vez que cargues WordPress, verás en el log:

```
El hook init se ha ejecutado
```

---

# Ejemplo `add_filter`

1. Crear snippet nuevo.
2. Título:  
    **“Modificar título con add_filter”**
3. Código:

```php
add_filter('the_title', function($titulo) {
    return '👉 ' . $titulo;
});
```

4. Activar.

Ahora todos los títulos del sitio tendrán un emoji delante.

---

# Ejemplo `add_action` en el admin

```php
add_action('admin_notices', function() {
    echo '<div class="notice notice-success"><p>Este es un mensaje desde un hook.</p></div>';
});
```

Se verá el mensaje en el panel de administración.



# Codigos de ejemplo que vienen con el plugin

* Hacer que los nombres de archivos subidos estén en minúsculas
* Desactivar barra de administracion
* Permitir emoticonos

# Reto

* Crea un shortcode que imprima la tabla de multiplicar del 5

