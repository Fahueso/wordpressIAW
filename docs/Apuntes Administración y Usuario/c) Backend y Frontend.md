# Comprendiendo el Backend y Frontend en WordPress

Una vez que has instalado y configurado WordPress, es importante entender las diferencias entre el backend y el frontend, así como las opciones y herramientas disponibles en cada uno.

---

## 1. **Backend**

El backend es la parte administrativa de WordPress donde se gestionan los contenidos, configuraciones y funcionalidades del sitio. Es accesible a través de la URL del sitio seguida de `/wp-admin`.

### Opciones Principales en el Backend

1. **Escritorio**:
    - Muestra un resumen general del estado del sitio.
    - Incluye accesos rápidos a publicaciones recientes, comentarios pendientes de moderación y actualizaciones.
    - Ofrece widgets personalizables con estadísticas, enlaces útiles y más.
        
2. **Entradas**:
    - Crea y edita contenido dinámico como blogs o noticias.
    - Permite añadir categorías y etiquetas para organizar mejor el contenido.
    - Soporta el uso de imágenes destacadas y contenido multimedia.
    - Utiliza el **Editor de Bloques (Gutenberg)** para diseñar el contenido con bloques visuales.
        
3. **Medios**:
    - Administra todos los archivos subidos, como imágenes, videos y documentos.
    - Incluye opciones para agregar títulos, descripciones y texto alternativo (ALT) a los archivos.
    - Ofrece herramientas para editar imágenes simples (recortar, rotar, etc.).
        
4. **Páginas**:
    - Diseñado para contenido estático como "Acerca de", "Servicios" o "Contacto".
    - Utiliza el **Editor de Bloques (Gutenberg)** para estructurar el contenido visualmente.
    - No utiliza categorías ni etiquetas como las entradas.
    - En temas compatibles con **Full Site Editing (FSE)**, puedes editar también el diseño de la página (cabecera, pie, etc.) desde el mismo editor.
        
5. **Apariencia**:
    - **Temas**: Cambia el diseño general del sitio seleccionando e instalando temas. Los temas compatibles con FSE permiten editar plantillas completas desde el editor de bloques.
    - **Personalizar**: Ajusta colores, tipografías, imágenes de cabecera y otros aspectos visuales. En temas FSE, esta opción redirige al editor de bloques.
    - **Widgets**: Configura elementos adicionales como barras laterales, menús o pies de página. En temas FSE, los widgets se reemplazan por bloques en las plantillas.
    - **Menús**: Administra las opciones de navegación visibles para los usuarios. En temas FSE, los menús se crean como bloques dentro de las plantillas.
    - **Editor del Sitio** (solo en temas FSE):  
        Permite editar el **header, footer, plantillas de archivo, páginas 404, etc.** usando bloques, sin necesidad de tocar código.
        
6. **Plugins**:
    - Añade funcionalidades adicionales al sitio (por ejemplo, SEO, formularios de contacto, seguridad).
    - Administra la instalación, activación, desactivación y eliminación de plugins.
        
7. **Usuarios**:
    - Crea y gestiona cuentas con diferentes roles y permisos (Administrador, Editor, Autor, etc.).
    - Edita detalles del perfil como contraseñas, correos electrónicos y nombres.
        
8. **Herramientas y Ajustes**:
    - **Herramientas**: Importa o exporta contenido y accede a utilidades adicionales.
    - **Ajustes**:
        - Generales: Define el título, descripción, idioma y zona horaria del sitio.
        - Lectura: Configura la página principal y las opciones de visibilidad.
        - Enlaces permanentes: Ajusta la estructura de las URLs del sitio.

---

## 2. **Frontend**

El frontend es la parte visible del sitio, donde los usuarios interactúan con el contenido y la funcionalidad. Desde 2022, con la llegada del **Full Site Editing (FSE)**, el frontend ya no depende solo del tema clásico: también puede construirse y editarse directamente desde el editor de bloques.

### Elementos Clave en el Frontend

1. **Diseño del Tema**:
    - Determina la apariencia general del sitio (colores, tipografías, estructura).
    - En **temas clásicos**, se personaliza desde _Apariencia > Personalizar_.
    - En **temas compatibles con FSE**, el diseño se edita desde _Apariencia > Editor del Sitio_, donde puedes modificar el header, footer, plantillas y estilos globales con bloques.
        
2. **Editor del Sitio (FSE)**:
    - Disponible solo en temas compatibles con Full Site Editing.
    - Permite editar **plantillas completas** (como la página de inicio, entradas individuales, resultados de búsqueda o la página 404) usando bloques.
    - Incluye herramientas como:
        - **Estilos Globales**: cambia colores, tipografías, espaciado y márgenes en todo el sitio sin tocar código.
        - **Navegación por plantillas**: edita el header, footer o sidebar como si fueran bloques individuales.
        - **Vista previa responsiva**: revisa cómo se ve el sitio en escritorio, tablet y móvil antes de guardar.
            
3. **Patrones de Bloques**:
    
    - Diseños predefinidos de bloques que puedes insertar con un clic y personalizar.
    - Ideales para crear páginas rápidamente sin diseñar desde cero.
    - Disponibles tanto en el editor de entradas/páginas como en el Editor del Sitio.
        
4. **Enlaces de Navegación**:
    - Configurados desde _Apariencia > Menús_ (en temas clásicos) o directamente como bloques _Navegación_ en el Editor del Sitio (en temas FSE).
    - Guían a los usuarios a secciones clave del sitio (páginas, categorías, enlaces personalizados).
    - Pueden incluir submenús desplegables y estilos visuales personalizados.
        
5. **Contenido Visible**:
    - Entradas y páginas configuradas desde el backend aparecen automáticamente.
    - En temas FSE, puedes decidir **dónde y cómo** se muestran (por ejemplo, una lista de entradas en la portada o una página estática).
    - Elementos multimedia (imágenes, videos, audios) se muestran según la configuración establecida.
    - Widgets (en temas clásicos) o bloques (en temas FSE) como barras laterales, calendario o búsquedas se integran al diseño.
        
6. **Interacción del Usuario**:
    - Formularios de contacto para recopilar información de visitantes.
    - Comentarios habilitados en entradas para fomentar la interacción.
    - Botones sociales y funcionalidades como búsquedas integradas.
    - En temas FSE, estos elementos también se insertan como bloques y se pueden colocar en cualquier parte del diseño.


---

## 3. **Relación entre Backend y Frontend**

El backend y el frontend están estrechamente conectados:
- **Gestión desde el Backend**: Todo el contenido que creas o configuras en el backend se refleja en el frontend.
- **Personalización**: Cambios en temas, menús y widgets en el backend afectan directamente el diseño y funcionalidad del frontend.

---

## 4. **Diferencias entre Entradas y Páginas**

Aunque las entradas y las páginas comparten ciertas características, tienen diferencias importantes:

- **Entradas**:
  - Diseñadas para contenido dinámico, como blogs o noticias.
  - Se organizan cronológicamente y pueden incluir una fecha de publicación.
  - Usan categorías y etiquetas para mejorar la organización y facilitar búsquedas.
  - Suelen incluir opciones para que los usuarios dejen comentarios.
  - Ejemplo: Publicaciones de un blog o actualizaciones de eventos.

- **Páginas**:
  - Orientadas al contenido estático, como "Acerca de", "Contacto" o "Servicios".
  - No tienen fecha de publicación visible ni se organizan cronológicamente.
  - No utilizan categorías ni etiquetas, pero pueden incluir jerarquías (una página puede ser "hija" de otra).
  - Generalmente no incluyen comentarios por defecto.
  - Ejemplo: Una página de presentación de la empresa.

Estas diferencias te permiten decidir cuál usar según las necesidades de tu sitio.

---

## 5. **Roles en WordPress**

WordPress incluye un sistema de roles para administrar permisos de acceso y control. Los roles principales son:

- **Administrador**:
  - Tiene control total sobre el sitio.
  - Puede instalar temas, plugins, gestionar usuarios y editar cualquier contenido.

- **Editor**:
  - Puede crear, editar, publicar y borrar entradas y páginas, incluidas las de otros usuarios.
  - Ideal para responsables de contenido.

- **Autor**:
  - Puede crear, editar y publicar sus propias entradas.
  - No tiene acceso para gestionar páginas ni entradas de otros usuarios.

- **Colaborador**:
  - Puede crear y editar sus propias entradas, pero no publicarlas.
  - Necesita que un Editor o Administrador revise y publique su contenido.

- **Suscriptor**:
  - Tiene acceso limitado a leer contenido privado o protegido.
  - No puede crear ni editar contenido.

El uso de roles permite distribuir tareas y responsabilidades de forma segura y eficiente.

---

## 6. **Sugerencias para Administradores Novatos**

- Familiarízate con las opciones del backend explorando cada menú.
- Prueba diferentes temas en el frontend para entender cómo afectan el diseño.
- Activa una vista previa de tus cambios antes de publicarlos para evitar errores visibles en el frontend.
- Revisa el sitio en diferentes dispositivos para garantizar una experiencia de usuario consistente.

Con este conocimiento, podrás gestionar y personalizar WordPress de manera más efectiva, aprovechando al máximo sus capacidades tanto en el backend como en el frontend.
