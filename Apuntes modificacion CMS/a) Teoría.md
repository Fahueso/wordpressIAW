# ¿Qué es un _hook_ en WordPress?

WordPress tiene cientos de puntos estratégicos en su ejecución donde permite que tú “te enganches” para añadir o modificar comportamiento.  
A esos puntos se les llama **hooks**.

Hay dos tipos:

|Tipo de hook|Para qué sirve|Ejemplo|
|---|---|---|
|**Action**|Ejecutar código en un momento concreto|Añadir un menú, cargar CSS, enviar un email|
|**Filter**|Modificar un dato antes de que WordPress lo use o lo muestre|Cambiar el contenido de un post, modificar el título|

---

# 🔧 ¿Qué es `add_action()`?

## Definición sencilla

`add_action()` sirve para decirle a WordPress:

> “Cuando llegues a este punto del proceso, ejecuta esta función mía”.

Es como decir:  
**“Cuando WordPress haga X, yo quiero hacer Y”.**

---

## Estructura

```php
add_action( 'nombre_del_hook', 'mi_funcion' );
```

- **`nombre_del_hook`** → el momento exacto donde quieres engancharte.
- **`mi_funcion`** → la función que quieres ejecutar.

---

## Ejemplo real

```php
add_action('admin_menu', 'crear_menu_personalizado');

function crear_menu_personalizado() {
    add_menu_page('Mi menú', 'Mi menú', 'manage_options', 'mi-menu', 'mi_pagina');
}
```

Aquí ocurre lo siguiente:

1. WordPress está construyendo el menú del admin.
2. Llega al hook **`admin_menu`**.
3. Como tú te enganchaste ahí, ejecuta tu función `crear_menu_personalizado()`.
4. Esa función añade un menú nuevo.

---

## Analogía

Imagina que WordPress es un tren con muchas estaciones.  
En cada estación (hook), tú puedes subirte y hacer algo.

`add_action` = “Cuando el tren llegue a la estación X, haz esto”.

---

# 🎛️ ¿Qué es `add_filter()`?

## Definición sencilla

`add_filter()` sirve para **modificar un dato** antes de que WordPress lo use o lo muestre.

Es como decir:

> “Antes de mostrar este contenido, pásalo por mi función para cambiarlo”.

---

## Estructura

```php
add_filter( 'nombre_del_filtro', 'mi_funcion' );
```

Tu función **recibe un valor**, lo modifica y **debe devolverlo**.

---

## Ejemplo real

```php
add_filter('the_content', 'añadir_mensaje');

function añadir_mensaje($contenido) {
    return $contenido . '<p>Gracias por leer.</p>';
}
```

Aquí:

1. WordPress está a punto de mostrar el contenido de una entrada.
2. Llega al filtro **`the_content`**.
3. Te da el contenido original en `$contenido`.
4. Tú lo modificas.
5. Devuelves el contenido nuevo.
6. WordPress muestra tu versión modificada.

---

## Analogía

Piensa en un filtro de café:

- WordPress pone el café (el contenido original).
- Tu filtro lo transforma (añade texto, cambia palabras, etc.).
- WordPress sirve el café filtrado (contenido modificado).

---

# Diferencia clara entre `add_action` y `add_filter`

|`add_action`|`add_filter`|
|---|---|
|Ejecuta código|Modifica datos|
|No devuelve nada|Debe devolver el valor modificado|
|“Haz algo en este momento”|“Cambia este valor antes de usarlo”|
|Ejemplos: crear menú, cargar scripts, enviar emails|Ejemplos: modificar contenido, título, excerpt|

---

# 🧩 Ejemplos

## Ejemplo de acción

```php
add_action('init', function() {
    error_log('WordPress ha iniciado');
});
```

## Ejemplo de filtro

```php
add_filter('the_title', function($titulo) {
    return '👉 ' . $titulo;
});
```


Perfecto, Francisco. Aquí tienes un **apunte claro, corto y didáctico** que explica **qué es un shortcode** y **cómo se crea**, sin entrar en plugins todavía. Ideal para tus alumnos.

---

#  **¿Qué es un shortcode?**

Un **shortcode** es una palabra o etiqueta escrita entre corchetes que WordPress reemplaza por contenido dinámico cuando se muestra la página.

Ejemplos:

```
[year]
[galeria]
[contacto]
```

Tú escribes eso en una entrada o página, y WordPress lo sustituye por:

- una fecha
- una tabla
- una galería
- un formulario
- o cualquier contenido generado por código

---

# 🧩 **¿Para qué sirve un shortcode?**

Sirve para insertar funciones avanzadas sin escribir código en el editor.

Permite:

- reutilizar funciones
- insertar contenido dinámico
- mostrar datos generados por PHP
- añadir elementos personalizados

---

# 🛠️ **Cómo se crea un shortcode

Para que un shortcode funcione, WordPress necesita que exista **un código que lo registre**.

Ese código dice:

- el nombre del shortcode
- qué debe devolver cuando se use

La estructura básica es:

```php
add_shortcode('nombre', function() {
    return 'Contenido que aparecerá en la página';
});
```

Después, en una página escribes:

```
[nombre]
```

Y WordPress lo sustituye por:

```
Contenido que aparecerá en la página
```

---

# 🧪 **Ejemplo sencillo**

Código:

```php
add_shortcode('year', function() {
    return date('Y');
});
```

Uso en una página:

```
© [year]
```

Resultado:

```
© 2026
```


