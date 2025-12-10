# Uso de Polylang en WordPress

**Polylang** es un plugin gratuito y popular que permite crear sitios multilingües en WordPress. Ofrece una solución flexible para gestionar y traducir contenido, menús, widgets y más, sin necesidad de conocimientos avanzados de programación.

---

## 1. **Instalación de Polylang**

1. Accede al panel de administración de WordPress.
2. Ve a **Plugins > Añadir nuevo**.
3. Busca "Polylang" en el campo de búsqueda.
4. Haz clic en "Instalar ahora" y luego en "Activar".
5. Una vez activado, aparecerá un nuevo menú llamado **Idiomas** en el panel de administración.

---

## 2. **Configuración Inicial**

### 2.1 Añadir Idiomas

1. Ve a **Idiomas > Idiomas**.
2. Haz clic en "Añadir nuevo idioma".
3. Selecciona:
   - **Idioma:** Escoge el idioma que deseas añadir.
   - **Código de idioma:** Se genera automáticamente.
   - **Nombre en inglés:** Se genera automáticamente.
   - **Orden:** Define el orden en el que aparecerán los idiomas en el selector.
4. Haz clic en "Añadir".
5. Repite estos pasos para cada idioma que necesites.

### 2.2 Configurar Idioma Predeterminado

1. En la lista de idiomas, selecciona uno como predeterminado haciendo clic en el icono de estrella.

---

## 3. **Traducción de Contenido**

### 3.1 Entradas y Páginas

1. Ve a **Entradas > Todas las entradas** o **Páginas > Todas las páginas**.
2. Verás columnas adicionales para cada idioma configurado.
3. Para traducir:
   - Haz clic en el icono de "+" junto al idioma deseado.
   - Introduce el contenido traducido y publícalo.

### 3.2 Menús

1. Ve a **Apariencia > Menús**.
2. Crea un menú para cada idioma:
   - Selecciona el idioma correspondiente desde el desplegable.
   - Añade las páginas traducidas al menú.
   - Guarda los cambios.
3. Asigna cada menú a su ubicación según el idioma.

---

## 4. **Selector de Idioma**

### 4.1 En temas clásicos (no FSE)

#### A. Añadir al menú
1. Ve a **Apariencia > Menús**.
2. En la lista de elementos, marca **“Language Switcher”** y pulsa **Añadir al menú**.
3. Reordena si es necesario y guarda.

#### B. Añadir como widget

1. Ve a **Apariencia > Widgets**.
2. Arrastra el widget **“Language Switcher”** a la barra lateral o pie.
3. Elige el formato (lista, desplegable o banderas) y guarda.

---

### 4.2 En temas FSE (Full Site Editing)

> Desde Polylang 3.4+ ya no necesitas plugins extra.

1. Ve a **Apariencia > Editor del Sitio**.
2. Abre la plantilla donde quieras el selector (por ejemplo, **Cabecera** o **Pie**).
3. Haz clic en **+** y busca el bloque **“Language Switcher”** (o “Selector de idioma”).
4. Inserta el bloque y, en la barra lateral, elige:
    - **Mostrar nombre del idioma**, **código** o **bandera**.
    - **Ocultar el idioma actual** (opcional).
5. Guarda la plantilla.
    
---

## 5. **Opciones Avanzadas**

### 5.1 Traducción de URLs

1. Ve a **Idiomas > Ajustes**.
2. Configura cómo se manejarán las URLs para cada idioma:
   - **URL con prefijo:** Ejemplo: `example.com/en/`.
   - **Subdominios:** Ejemplo: `en.example.com` (requiere configuración avanzada en DNS).
   - **Dominio por idioma:** Ejemplo: `example.com` y `example.fr`.

### 5.2 Traducción de Categorías y Etiquetas

1. Ve a **Entradas > Categorías** o **Entradas > Etiquetas**.
2. Haz clic en "Editar" junto a la categoría o etiqueta que deseas traducir.
3. Completa la traducción para cada idioma.
4. Guarda los cambios.

### 5.3 Sincronización de Contenido

La sincronización de contenido en Polylang permite mantener coherencia entre las traducciones al replicar ciertos elementos comunes automáticamente en todos los idiomas configurados. Esto evita realizar ajustes manuales en cada versión del contenido.

1. Ve a **Idiomas > Ajustes > Sincronización**.
2. Activa la sincronización para los elementos que desees:
   - **Campos personalizados:** Mantén consistencia en los datos adicionales configurados para las entradas y páginas.
   - **Imagen destacada:** La misma imagen se aplicará a todas las versiones del contenido.
   - **Comentarios:** Sincroniza la sección de comentarios entre los diferentes idiomas para que compartan las mismas discusiones.
3. Haz clic en "Guardar cambios" para aplicar la configuración.

### 5.4 Traducción de Medios

Polylang también permite traducir elementos de la biblioteca de medios para que cada idioma tenga sus propios recursos visuales y textos asociados.

1. Ve a **Medios > Biblioteca**.
2. Selecciona el elemento de medios (por ejemplo, una imagen) que deseas traducir.
3. En la barra lateral, verás opciones para asignar el idioma o crear traducciones del mismo elemento.
4. Agrega una descripción, texto alternativo y leyenda en cada idioma según sea necesario.
5. Guarda los cambios para asegurarte de que los medios reflejen correctamente las traducciones configuradas.

---

## 6. **Ventajas de Polylang**

1. **Gestión Centralizada:**
   - Configura y administra todos los idiomas desde un solo lugar.
2. **Gratuito y Flexible:**
   - La versión gratuita es suficiente para la mayoría de los sitios.
3. **Compatibilidad:**
   - Compatible con la mayoría de temas y plugins.
4. **SEO Optimizado:**
   - Estructura de URL amigable para motores de búsqueda.




