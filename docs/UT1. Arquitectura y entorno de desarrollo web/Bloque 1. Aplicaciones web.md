# Bloque 1. Aplicaciones web

## 1. ¿Qué es una aplicación web?

Una **aplicación web** es un programa informático al que accedemos a través de un navegador web utilizando una red, normalmente Internet o una intranet.

A diferencia de las aplicaciones de escritorio, no es necesario instalar la aplicación completa en el equipo del usuario. Gran parte del procesamiento se realiza en uno o varios servidores remotos.

Son ejemplos de aplicaciones web:

- Moodle
- Nextcloud
- WordPress
- phpMyAdmin
- GitLab

Cuando utilizamos cualquiera de estas aplicaciones, nuestro navegador intercambia información con uno o varios servidores que procesan las peticiones y generan las respuestas.

## 2. Arquitectura cliente-servidor

La mayoría de los servicios que utilizamos diariamente funcionan siguiendo una arquitectura denominada **cliente-servidor**.

En este modelo, una aplicación se divide en dos partes:

- **Cliente**: realiza solicitudes y presenta la información al usuario.
- **Servidor**: recibe las solicitudes, las procesa y devuelve una respuesta.

La comunicación entre ambos se realiza a través de una red, que puede ser Internet o una red local.

Gracias a esta arquitectura es posible centralizar la información y los servicios en uno o varios servidores, permitiendo que múltiples clientes accedan simultáneamente a ellos.

![[Pasted image 20260901173311.png]]

Por ejemplo:

1. El cliente solicita un recurso o servicio.
2. El servidor recibe la solicitud.
3. El servidor la procesa.
4. El servidor genera una respuesta.
5. El cliente recibe el resultado.

### Ejemplos de arquitecturas cliente-servidor

|Servicio|Cliente|Servidor|
|---|---|---|
|Correo electrónico|Thunderbird|Servidor de correo|
|Web|Firefox|Servidor web|
|Bases de datos|MySQL Workbench|Servidor MySQL|
|Compartición de archivos|Explorador de archivos|Servidor de ficheros|

### Ventajas

- Permite compartir recursos entre múltiples usuarios.
- Facilita la administración centralizada.
- Simplifica el mantenimiento de la información.
- Permite controlar la seguridad y los permisos desde el servidor.
- Facilita la escalabilidad del sistema.

### Inconvenientes

- Si el servidor deja de funcionar, el servicio puede quedar inaccesible.
- El rendimiento depende de la red y de la capacidad del servidor.
- La administración puede resultar compleja en sistemas grandes.

## 2.1 Arquitectura cliente-servidor en aplicaciones web

### Cliente web

El **cliente web** es el dispositivo o programa que utiliza el usuario para acceder a una aplicación web.

En la mayoría de los casos, el cliente es un **navegador web**, que se encarga de solicitar información al servidor y mostrar la respuesta al usuario. También puede ser una aplicación móvil o cualquier otro programa capaz de comunicarse con un servidor web.

Algunos ejemplos de clientes web son:

- Google Chrome
- Mozilla Firefox
- Microsoft Edge
- Safari

Cuando un usuario escribe una dirección web o pulsa un enlace, el navegador envía una petición al servidor y espera una respuesta.

### Servidor web

Un **servidor web** es el software encargado de recibir peticiones de los clientes web y devolver los recursos solicitados.

Entre sus funciones principales se encuentran:

- Recibir peticiones de los navegadores.
- Enviar páginas web.
- Servir imágenes, hojas de estilo y otros archivos.
- Redirigir peticiones.
- Colaborar con otros componentes para generar contenido dinámico.

Los servidores web más utilizados son:

- Apache HTTP Server.
- Nginx.
- Microsoft IIS.

Es importante no confundir el **servidor web**, que es un programa, con el **servidor**, que es la máquina donde se ejecuta dicho programa.

Así, una misma máquina puede ejecutar varios servicios al mismo tiempo.

### Ejemplo de navegación web

Cuando un usuario accede a una página web se produce un intercambio de información entre el cliente web y el servidor web.

1. El usuario escribe la dirección de una página web en el navegador.
2. El navegador (cliente web) envía una petición al servidor.
3. El servidor web recibe la petición y la gestiona.
4. El servidor web devuelve la respuesta al cliente.
5. El navegador interpreta la respuesta y muestra la página web al usuario.

## 3. Comunicación en la web

### 3.1 Recursos web

Cuando un usuario accede a una página web, realmente está solicitando uno o varios **recursos web** ubicados en un servidor.

Un recurso web es cualquier elemento que puede ser almacenado, localizado y enviado a través de una red para ser utilizado por una aplicación o un usuario.

#### ¿Qué puede ser un recurso web?

Algunos ejemplos de recursos web son:

- Páginas HTML.
- Imágenes.
- Hojas de estilo CSS.
- Archivos JavaScript.
- Vídeos.
- Archivos PDF.
- Documentos descargables.
- Datos almacenados en bases de datos.
- Contenido generado dinámicamente por una aplicación web.

Por tanto, un recurso web no tiene por qué ser un archivo físico almacenado en el servidor. También puede ser información generada en el momento de atender una solicitud.

#### Recursos estáticos y dinámicos

Los recursos web pueden clasificarse en dos grandes grupos.

**Recursos estáticos**

Son aquellos cuyo contenido no cambia entre una solicitud y otra.

El servidor simplemente localiza el recurso y lo envía al cliente.

Ejemplos:

- Un archivo HTML.
- Una imagen JPG o PNG.
- Un documento PDF.
- Un archivo CSS.

Si dos usuarios solicitan el mismo recurso estático, ambos recibirán exactamente el mismo contenido.

**Recursos dinámicos**

Son aquellos cuyo contenido se genera en el momento en que el usuario realiza una solicitud.

Normalmente intervienen otros componentes además del servidor web:

- Aplicaciones.
- Bases de datos.
- Servicios externos.

Ejemplos:

- La bandeja de entrada de un correo electrónico.
- Los mensajes de una red social.
- El catálogo de una tienda online.
- El contenido de Moodle después de iniciar sesión.

Dos usuarios diferentes pueden recibir respuestas distintas aunque soliciten aparentemente la misma página.

#### Una página web está formada por varios recursos

Cuando un usuario visita una página web, el navegador suele solicitar múltiples recursos.

Por ejemplo, una página puede estar formada por:

```text
index.html
├── estilos.css
├── logo.png
├── menu.js
└── fondo.jpg
```

Aunque el usuario vea una única página, el navegador realiza múltiples solicitudes para obtener todos los elementos necesarios.

Por este motivo, el rendimiento de una página web depende en gran medida de:

- El número de recursos solicitados.
- Su tamaño.
- El tiempo necesario para obtenerlos.

#### Identificación de recursos

Cada recurso disponible en un servidor debe poder identificarse de forma única.

Para ello se utiliza una dirección que permite localizarlo.

Por ejemplo:

```text
/imagenes/logo.png
/documentos/horario.pdf
/index.html
```

Sin embargo, estas rutas solo tienen sentido dentro de un servidor concreto.

Para poder localizar recursos a través de Internet se utilizan las URL, que estudiaremos en el siguiente apartado.

### 3.2 URL

Cuando utilizamos una aplicación web, necesitamos una forma de indicar al navegador qué recurso queremos solicitar. Para ello utilizamos una **URL**.

Las siglas URL provienen de _Uniform Resource Locator_ (Localizador Uniforme de Recursos).

Una URL es una dirección que permite localizar un recurso en una red, normalmente Internet.

Algunos ejemplos de URL son:

```text
https://www.aules.edu.gva.es/fp
https://portal.edu.gva.es
https://es.wikipedia.org/wiki/Internet
```

Cuando escribimos una URL en el navegador, éste utiliza la información contenida en ella para localizar el recurso solicitado y mostrarlo al usuario.

#### Componentes de una URL

Una URL está formada por varias partes.

Por ejemplo:

[https://aules.edu.gva.es:443/fp/login/index.php](https://aules.edu.gva.es/fp/login/index.php)

Podemos distinguir los siguientes componentes:

**Protocolo**

Indica cómo se realizará la comunicación entre el cliente y el servidor.

En el ejemplo: `https`

Otros protocolos habituales son: `http`, `ftp`

Más adelante estudiaremos con detalle los protocolos HTTP y HTTPS.

**Nombre del servidor o dominio**

Identifica el servidor donde se encuentra el recurso solicitado.

En el ejemplo: `aules.edu.gva.es`

Los usuarios utilizan nombres de dominio porque son más fáciles de recordar que las direcciones IP.

**Puerto**

Indica el servicio concreto al que debe conectarse el cliente dentro del servidor.

En el ejemplo: `443`

Si el puerto no aparece explícitamente, el navegador utilizará el puerto predeterminado asociado al protocolo.

Algunos puertos habituales son:

|Protocolo|Puerto por defecto|
|---|---|
|HTTP|80|
|HTTPS|443|
|FTP|21|

**Ruta**

Indica la ubicación del recurso dentro del servidor.

En el ejemplo: `/fp/login/`

Puede entenderse como la ruta hasta la carpeta donde se encuentra el recurso solicitado.

**Recurso**

Es el elemento concreto que se desea obtener.

En el ejemplo: `index.php`

El recurso puede ser:

- Una página HTML.
- Una imagen.
- Un documento PDF.
- Un vídeo.
- Un programa ejecutado en el servidor.
- Cualquier otro recurso accesible desde la Web.

#### Interpretando una URL

Tomemos como ejemplo la siguiente dirección:

[https://aules.edu.gva.es/fp/login/index.php](https://aules.edu.gva.es/fp/login/index.php)

Podemos interpretarla de la siguiente forma:

- Utiliza el protocolo **HTTPS**.
- El servidor se llama **aules.edu.gva.es**.
- Se accederá al puerto predeterminado de HTTPS (443).
- El recurso se encuentra dentro de la ruta **/fp/login/**.
- El recurso solicitado es **index.php**.

#### Observación

En muchas ocasiones no es necesario indicar el nombre del recurso.

Por ejemplo: [https://www.wikipedia.org](https://www.wikipedia.org/)

En estos casos el servidor suele devolver automáticamente una página predeterminada, como `index.html` o `index.php`, según su configuración.

### 3.3 Resolución de nombres (DNS)

Los seres humanos utilizamos nombres para identificar los recursos de Internet porque son más fáciles de recordar que las direcciones IP.

Por ejemplo, resulta más sencillo recordar `aules.edu.gva.es` que una dirección IP como `213.0.8.18`.

Sin embargo, los equipos de una red no utilizan nombres para comunicarse entre sí, sino direcciones IP.

Por este motivo es necesario un mecanismo que permita traducir los nombres de dominio a direcciones IP.

#### ¿Qué es DNS?

DNS son las siglas de **Domain Name System** (Sistema de Nombres de Dominio).

Es un sistema distribuido cuya función consiste en traducir nombres de dominio a direcciones IP y viceversa.

Gracias al DNS, los usuarios pueden acceder a los servicios utilizando nombres fáciles de recordar en lugar de direcciones IP numéricas.

#### Funcionamiento básico

Cuando un usuario escribe una dirección web en su navegador, se realizan los siguientes pasos de forma simplificada:

1. El usuario introduce una dirección web.
2. El navegador identifica el nombre de dominio.
3. Se consulta un servidor DNS.
4. El servidor DNS devuelve la dirección IP asociada al dominio.
5. El navegador se conecta a esa dirección IP.
6. El servidor responde a la solicitud.

#### Ejemplo

Supongamos que el usuario escribe [https://aules.edu.gva.es](https://aules.edu.gva.es/)

El navegador debe averiguar la dirección IP asociada al dominio `aules.edu.gva.es`.

Para ello consulta uno o varios servidores DNS.

Una vez obtenida la dirección IP, ya puede establecer la comunicación con el servidor correspondiente.

#### Estructura de un nombre de dominio

Un nombre de dominio está organizado de forma jerárquica.

Por ejemplo: `aules.edu.gva.es`

Puede dividirse en varias partes:

|Elemento|Significado|
|---|---|
|es|Dominio de nivel superior (España)|
|gva|Organización|
|edu|Subdominio relacionado con educación|
|aules|Servicio o equipo concreto|

Cada organización puede crear sus propios subdominios para organizar sus servicios.

#### Comprobación de la resolución DNS

Los sistemas operativos incorporan herramientas para comprobar la resolución de nombres.

Por ejemplo:

```text
nslookup wikipedia.org
dig wikipedia.org
```

Estas herramientas permiten conocer la dirección IP asociada a un dominio y comprobar si la resolución de nombres funciona correctamente.

#### Problemas habituales relacionados con DNS

Algunos problemas frecuentes son:

- El dominio no existe.
- El servidor DNS no responde.
- El registro DNS es incorrecto.
- La información almacenada en caché de nombres está desactualizada.

En estos casos el navegador no podrá localizar el servidor aunque éste esté funcionando correctamente.

### 3.4 Protocolos de comunicación

Para que dos equipos puedan intercambiar información es necesario que ambos sigan unas reglas comunes.

Estas reglas reciben el nombre de **protocolos de comunicación**.

Un protocolo define aspectos como:

- Cómo se inicia una comunicación.
- Cómo se intercambian los datos.
- Qué formato tienen los mensajes.
- Cómo se detectan errores.
- Cómo finaliza la comunicación.

Si dos equipos no utilizan el mismo protocolo, no podrán entenderse entre sí.

#### Ejemplo cotidiano

Podemos comparar un protocolo con las normas de una conversación.

Cuando dos personas hablan utilizan un idioma común y siguen ciertas normas:

- Una persona habla.
- La otra escucha.
- Se intercambian mensajes.
- Ambas entienden el significado de las palabras.

En las redes ocurre algo parecido. Los dispositivos deben utilizar protocolos comunes para poder comunicarse.

#### Protocolos y servicios

Cada servicio de red suele utilizar uno o varios protocolos específicos.

Por ejemplo:

|Servicio|Protocolo|
|---|---|
|Navegación web|HTTP, HTTPS|
|Correo electrónico|SMTP, POP3, IMAP|
|Transferencia de archivos|FTP|
|Resolución de nombres|DNS|

Cuando utilizamos una aplicación web, el navegador y el servidor deben utilizar el mismo protocolo para poder intercambiar información correctamente.

#### Protocolos en capas

Las comunicaciones en red se organizan habitualmente en capas.

Cada capa realiza una función concreta y utiliza protocolos específicos.

![[Pasted image 20260901183448.png|484]]

Gracias a esta organización, cada protocolo puede centrarse en una tarea determinada.

#### Protocolo IP

El protocolo IP (_Internet Protocol_) permite identificar los equipos de una red mediante direcciones IP y encaminar los datos hasta su destino.

Su función principal es hacer llegar los datos desde el equipo de origen hasta el equipo de destino.

Por ejemplo:

```text
192.168.1.10 ─────► 192.168.1.20
```

#### Protocolo TCP

El protocolo TCP (_Transmission Control Protocol_) proporciona una comunicación fiable entre dos equipos.

Entre sus funciones principales se encuentran:

- Controlar que los datos lleguen correctamente.
- Detectar errores.
- Reenviar información si se pierde durante la transmisión.
- Mantener una conexión entre los equipos.

TCP es uno de los protocolos más utilizados en Internet.

#### Relación entre TCP e IP

TCP e IP suelen trabajar conjuntamente.

- IP se encarga de llevar los datos hasta el destino.
- TCP se encarga de que los datos lleguen completos y en el orden correcto.

Por esta razón suele hablarse del conjunto de protocolos **TCP/IP**.

#### Protocolos utilizados en la Web

Cuando un usuario accede a una página web intervienen varios protocolos.

![[Pasted image 20260901183307.png]]

Cada protocolo realiza una tarea específica para que la comunicación pueda completarse correctamente.

### 3.5 HTTP y HTTPS

Una vez que el navegador ha localizado el servidor mediante DNS y ha establecido una conexión utilizando TCP/IP, es necesario disponer de un protocolo que permita intercambiar información entre cliente y servidor web.

Los protocolos más utilizados para este fin son **HTTP** y **HTTPS**.

#### ¿Qué es HTTP?

HTTP son las siglas de **HyperText Transfer Protocol** (Protocolo de Transferencia de Hipertexto).

Es el protocolo utilizado por navegadores y servidores web para intercambiar información.

HTTP define:

- Cómo se solicitan los recursos.
- Cómo se envían las respuestas.
- El formato de los mensajes intercambiados.
- Los códigos utilizados para indicar el resultado de una operación.

La comunicación HTTP sigue un modelo de **petición-respuesta**.

```text
Cliente Web
   │
   │ Petición HTTP
   ▼
Servidor Web
   │
   │ Respuesta HTTP
   ▼
Cliente Web
```

#### ¿Qué es HTTPS?

HTTPS significa **HyperText Transfer Protocol Secure**.

Funciona igual que HTTP, pero incorpora mecanismos de seguridad que permiten proteger la información intercambiada entre cliente y servidor.

Gracias a HTTPS:

- Los datos viajan cifrados.
- Se evita que terceros puedan leer la información transmitida.
- Se verifica la identidad del servidor.
- Se protege la integridad de los datos.

Actualmente la mayoría de los sitios web utilizan HTTPS.

#### Diferencias entre HTTP y HTTPS

|Característica|HTTP|HTTPS|
|---|---|---|
|Seguridad|No cifra la información|Cifra la información|
|Puerto habitual|80|443|
|Certificado digital|No|Sí|
|Recomendado para aplicaciones web|No|Sí|

#### Peticiones HTTP

Las peticiones HTTP utilizan diferentes métodos según la operación que desea realizar el cliente.

Los más utilizados son:

**GET**

Solicita información al servidor. Se utiliza para:

- Consultar páginas web.
- Obtener imágenes.
- Descargar documentos.
- Leer información.

Ejemplo:

```text
GET /index.html
```

**POST**

Envía información al servidor para que sea procesada. Se utiliza habitualmente en:

- Formularios.
- Procesos de autenticación.
- Envío de datos.

Ejemplo:

```text
POST /login
```

#### Respuestas HTTP

Cuando el servidor recibe una petición devuelve una respuesta. La respuesta incluye:

- Un código de estado.
- Información adicional.
- El contenido solicitado (si procede).

#### Códigos de estado HTTP

Los códigos de estado indican el resultado de una petición.

**Respuestas correctas (2xx)**

|Código|Significado|
|---|---|
|200|OK|
|201|Creado correctamente|

**Redirecciones (3xx)**

|Código|Significado|
|---|---|
|301|Redirección permanente|
|302|Redirección temporal|

**Errores del cliente (4xx)**

|Código|Significado|
|---|---|
|400|Solicitud incorrecta|
|401|No autorizado|
|403|Acceso prohibido|
|404|Recurso no encontrado|

**Errores del servidor (5xx)**

|Código|Significado|
|---|---|
|500|Error interno del servidor|
|503|Servicio no disponible|

#### Certificados digitales

Para utilizar HTTPS es necesario instalar un **certificado digital** en el servidor web. Un certificado digital permite:

- Identificar al servidor.
- Cifrar las comunicaciones.
- Generar confianza en los usuarios.

Cuando visitamos una página HTTPS, el navegador comprueba la validez del certificado antes de intercambiar información.

Por este motivo aparece un candado en la barra de direcciones.

#### Analizando una petición HTTP

Los navegadores modernos incluyen herramientas para inspeccionar las comunicaciones con el servidor.

Por ejemplo, en Firefox o Chrome:

1. Abrir las herramientas de desarrollador (F12).
2. Acceder a la pestaña **Red** o **Network**.
3. Recargar la página.

Podremos observar:

- Las URL solicitadas.
- Los métodos utilizados.
- Los códigos de estado.
- El tamaño de los recursos descargados.
- El tiempo empleado en cada petición.

## 4. Aplicaciones web modernas

### 4.1 Limitaciones del modelo simple cliente-servidor

Hasta ahora hemos estudiado cómo un cliente web solicita recursos a un servidor web y recibe una respuesta. Este modelo es suficiente para publicar recursos estáticos como:

- Páginas HTML.
- Imágenes.
- Hojas de estilo CSS.
- Documentos PDF.
- Archivos JavaScript.

En estos casos, el servidor simplemente localiza el recurso solicitado y lo envía al cliente.

Sin embargo, las aplicaciones web modernas necesitan ofrecer funcionalidades mucho más avanzadas.

Por ejemplo:

- Gestionar cuentas de usuario.
- Validar credenciales de acceso.
- Procesar formularios.
- Almacenar información de forma permanente.
- Generar contenido personalizado.
- Mantener sesiones de usuario.
- Aplicar permisos y restricciones de acceso.

Estas tareas no pueden resolverse únicamente enviando archivos almacenados en el servidor.

#### Un ejemplo real

Imaginemos una plataforma educativa como Moodle.

Cuando dos alumnos acceden a la misma dirección web, ambos realizan una solicitud al servidor. Sin embargo, cada alumno debe ver:

- Sus cursos.
- Sus tareas pendientes.
- Sus calificaciones.
- Sus mensajes.

La información mostrada depende del usuario que haya iniciado sesión. Por tanto, la respuesta no puede estar almacenada previamente en un único archivo HTML. Debe generarse dinámicamente en función de la información disponible.

#### La necesidad de procesar información

Supongamos un formulario de inicio de sesión:

```text
Usuario: alumno1
Contraseña: ********
```

El servidor debe:

1. Recibir los datos enviados por el usuario.
2. Comprobar si las credenciales son correctas.
3. Consultar la información almacenada.
4. Determinar los permisos del usuario.
5. Generar una respuesta adecuada.

Para realizar este proceso es necesario ejecutar código y acceder a información almacenada previamente.

#### La necesidad de almacenar datos

Muchas aplicaciones web trabajan con grandes cantidades de información:

- Usuarios.
- Productos.
- Cursos.
- Pedidos.
- Mensajes.
- Configuraciones.

Guardar toda esta información en archivos estáticos sería poco práctico y difícil de mantener.

Por este motivo las aplicaciones web suelen utilizar sistemas gestores de bases de datos que permiten almacenar y recuperar información de forma eficiente.

#### Hacia una arquitectura más compleja

Las limitaciones del modelo simple cliente-servidor han provocado la aparición de arquitecturas más avanzadas.

En una aplicación web moderna suelen intervenir varios componentes especializados:

```text
Cliente web
   │
   ▼
Servidor web
   │
   ▼
Motor de aplicación
   │
   ▼
Base de datos
```

Cada componente realiza una función específica:

- El servidor web recibe las solicitudes.
- El motor de aplicación ejecuta la lógica de negocio.
- La base de datos almacena la información.

Esta separación facilita el desarrollo, el mantenimiento y la escalabilidad de las aplicaciones web.

En los siguientes apartados estudiaremos con detalle cada uno de estos componentes.

### 4.2 Motores de aplicación

En el apartado anterior hemos visto que un servidor web es suficiente para servir recursos estáticos, pero no para implementar las funcionalidades de una aplicación web moderna.

Cuando una aplicación necesita procesar información, validar usuarios, consultar bases de datos o generar contenido personalizado, es necesario incorporar un componente capaz de ejecutar código. Este componente recibe el nombre de **motor de aplicación**.

#### ¿Qué es un motor de aplicación?

Un motor de aplicación es el software encargado de ejecutar la lógica de negocio de una aplicación web.

Su función consiste en:

- Procesar las solicitudes recibidas.
- Ejecutar el código de la aplicación.
- Validar datos introducidos por los usuarios.
- Gestionar sesiones de usuario.
- Consultar y modificar datos almacenados.
- Generar respuestas dinámicas.

A diferencia del servidor web, que se limita principalmente a recibir solicitudes y servir recursos, el motor de aplicación es quien realiza el trabajo necesario para construir la respuesta.

#### Funcionamiento

Cuando un usuario solicita una página dinámica, el proceso suele ser similar al siguiente:

```text
Cliente web
   │
   ▼
Servidor web
   │
   ▼
Motor de aplicación
   │
   ▼
Base de datos
   │
   ▼
Motor de aplicación
   │
   ▼
Servidor web
   │
   ▼
Cliente web
```

El servidor web recibe la solicitud, pero delega el procesamiento en el motor de aplicación.

Una vez generada la respuesta, ésta es enviada de nuevo al servidor web para que la entregue al cliente.

#### Tareas habituales

Entre las tareas realizadas habitualmente por los motores de aplicación se encuentran:

**Gestión de formularios**

Por ejemplo:

```text
Nombre: Juan
Correo: juan@email.com
```

El motor de aplicación recibe los datos enviados por el usuario y realiza las comprobaciones necesarias antes de procesarlos.

**Autenticación de usuarios**

Cuando un usuario inicia sesión:

```text
Usuario: fperez
Contraseña: ********
```

el motor de aplicación verifica las credenciales y determina si el acceso está permitido.

**Gestión de sesiones**

Después de iniciar sesión, la aplicación debe recordar quién es el usuario mientras navega por distintas páginas.

Esta tarea suele recaer en el motor de aplicación.

**Acceso a bases de datos**

Gran parte de la información utilizada por las aplicaciones web se encuentra almacenada en bases de datos.

El motor de aplicación puede:

- Consultar información.
- Insertar nuevos registros.
- Actualizar datos existentes.
- Eliminar información.

**Generación de contenido dinámico**

Dos usuarios pueden solicitar la misma página y recibir contenidos diferentes.

Por ejemplo, en Moodle cada alumno visualizará:

- Sus cursos.
- Sus tareas.
- Sus calificaciones.

El contenido se genera dinámicamente para cada usuario.

#### Tecnologías utilizadas

Existen diferentes tecnologías capaces de actuar como motores de aplicación. Algunas de las más utilizadas son:

- PHP
- Java
- Python
- JavaScript (Node.js)

La función que realizan es similar, aunque cada una utiliza herramientas y entornos diferentes.

#### Contenedores de aplicaciones  

Algunas tecnologías utilizan software específico para gestionar la ejecución de aplicaciones web.  

Este software recibe el nombre de **contenedor de aplicaciones** o **servidor de aplicaciones**, dependiendo de sus características.  

Su función consiste en:  
- Ejecutar las aplicaciones.  
- Gestionar recursos.  
- Administrar sesiones.  
- Controlar el ciclo de vida de la aplicación.  
- Facilitar el despliegue.  

Por ejemplo, las aplicaciones Java suelen ejecutarse sobre contenedores como:  
- Apache Tomcat.  
- WildFly.  
- GlassFish.  

En estas arquitecturas suele existir una separación clara entre:  
  
```text  

Servidor web  
↓  
Contenedor de aplicaciones  
↓  
Base de datos
```

Por ejemplo:
```text
Cliente web  
│  
▼  
Apache  
│  
▼  
Tomcat  
│  
▼  
PostgreSQL

```

### El caso de PHP

Las aplicaciones PHP también necesitan un entorno de ejecución especializado.

Sin embargo, tradicionalmente PHP se ha integrado directamente con el servidor web mediante módulos como `mod_php`, por lo que la separación entre servidor web y motor de aplicación resulta menos evidente.

```text

Cliente web  
│  
▼  
Apache
│  
▼  
PHP integrado
│  
▼  
MariaDB
```

En instalaciones modernas es frecuente utilizar **PHP-FPM**, donde la separación es más clara:

```text
Cliente web  
│  
▼  
Apache  
│  
▼  
PHP-FPM  
│  
▼  
MariaDB
```

PHP-FPM no suele considerarse un servidor de aplicaciones completo como Tomcat o WildFly. Sin embargo, desempeña una función similar, ya que es el componente encargado de ejecutar el código de la aplicación PHP cuando recibe solicitudes desde el servidor web.
#### Servidor web y motor de aplicación

Es importante distinguir ambos conceptos:

|Componente|Función principal|
|---|---|
|Servidor web|Recibir solicitudes y servir recursos|
|Motor de aplicación|Ejecutar la lógica de negocio|
|Base de datos|Almacenar información|

Aunque en algunas tecnologías la separación no siempre es evidente, conceptualmente cumplen funciones diferentes dentro de una aplicación web.

### 4.3 Bases de datos

Las aplicaciones web modernas manejan grandes cantidades de información. Para almacenar y gestionar estos datos de forma eficiente utilizan sistemas gestores de bases de datos.

Sin una base de datos sería muy complicado mantener organizada la información necesaria para el funcionamiento de aplicaciones como Moodle, WordPress o Nextcloud.

#### ¿Qué es una base de datos?

Una **base de datos** es un conjunto organizado de información que puede almacenarse, consultarse y modificarse de forma eficiente.

Algunos ejemplos de información que puede almacenarse son:

- Usuarios.
- Contraseñas.
- Cursos.
- Productos.
- Pedidos.
- Mensajes.
- Configuraciones.
- Calificaciones.

La base de datos permite que la información permanezca disponible incluso cuando la aplicación deja de ejecutarse o el servidor se reinicia.

#### ¿Por qué son necesarias?

Imaginemos una plataforma educativa con cientos de profesores y miles de alumnos.

La aplicación necesita almacenar:

- Los datos de cada usuario.
- Los cursos matriculados.
- Las tareas entregadas.
- Las calificaciones obtenidas.
- Los mensajes enviados.

Guardar toda esta información en archivos individuales sería difícil de administrar y muy poco eficiente.

Las bases de datos proporcionan mecanismos para:

- Organizar la información.
- Realizar búsquedas rápidas.
- Mantener la integridad de los datos.
- Controlar el acceso a la información.
- Gestionar grandes volúmenes de datos.

#### Sistemas gestores de bases de datos

Una base de datos suele gestionarse mediante un software especializado denominado **Sistema Gestor de Bases de Datos (SGBD)**.

Su función consiste en:

- Crear bases de datos.
- Almacenar información.
- Realizar consultas.
- Modificar registros.
- Controlar permisos de acceso.
- Garantizar la integridad de los datos.

Algunos SGBD muy utilizados son:

- MariaDB
- MySQL
- PostgreSQL
- Oracle Database

En este módulo trabajaremos principalmente con **MariaDB**, aunque los conceptos estudiados son aplicables a otros gestores.

#### Bases de datos en una aplicación web

La base de datos no suele comunicarse directamente con el navegador.

La comunicación se realiza a través del motor de aplicación.

```text
Cliente web
   │
   ▼
Servidor web
   │
   ▼
Motor de aplicación
   │
   ▼
Base de datos
```

De esta forma, los usuarios no acceden directamente a la información almacenada, sino que es la aplicación quien controla qué datos pueden consultarse o modificarse.

#### Ejemplo: inicio de sesión

Supongamos que un usuario intenta acceder a una aplicación web.

```text
Usuario: alumno1
Contraseña: ********
```

El proceso podría ser el siguiente:

1. El usuario introduce sus credenciales.
2. El navegador envía la información al servidor.
3. El motor de aplicación recibe los datos.
4. La aplicación consulta la base de datos.
5. Se verifica si las credenciales son correctas.
6. Se genera la respuesta correspondiente.

```text
Cliente web
   │
   ▼
Servidor web
   │
   ▼
PHP
   │
   │ Consulta usuarios
   ▼
MariaDB
```

#### Operaciones habituales

Las aplicaciones web realizan constantemente operaciones sobre las bases de datos. Las más habituales son:

**Crear información**

Por ejemplo:

- Registrar un nuevo usuario.
- Crear un curso.
- Añadir un producto.

**Consultar información**

Por ejemplo:

- Mostrar las tareas pendientes.
- Listar los productos disponibles.
- Consultar las calificaciones de un alumno.

**Modificar información**

Por ejemplo:

- Actualizar una contraseña.
- Cambiar los datos de un usuario.
- Modificar un pedido.

**Eliminar información**

Por ejemplo:

- Borrar una cuenta de usuario.
- Eliminar un mensaje.
- Suprimir un curso.

Estas cuatro operaciones suelen conocerse como **CRUD**:

- **Create**
- **Read**
- **Update**
- **Delete**

#### Ejemplos reales

**Moodle**

La base de datos almacena:

- Usuarios.
- Cursos.
- Tareas.
- Cuestionarios.
- Calificaciones.

**WordPress**

La base de datos almacena:

- Entradas.
- Páginas.
- Comentarios.
- Usuarios.
- Configuración del sitio.

**Nextcloud**

La base de datos almacena:

- Usuarios.
- Configuración.
- Permisos.
- Información de los archivos.

#### Ventajas de utilizar bases de datos

- Permiten almacenar grandes cantidades de información.
- Facilitan las búsquedas y consultas.
- Mejoran la organización de los datos.
- Permiten gestionar permisos y acceso.
- Garantizan la integridad de la información.
- Facilitan la realización de copias de seguridad.

### 4.4 Arquitectura multicapa

Las aplicaciones web modernas suelen organizarse siguiendo una arquitectura multicapa.

La idea principal consiste en dividir la aplicación en varias capas, cada una encargada de una responsabilidad concreta.

Esta separación facilita el mantenimiento, la ampliación y la reutilización del software.

#### Capas principales

Una aplicación web típica se divide en tres capas:

```text
┌─────────────────────┐
│     Presentación    │
└──────────┬──────────┘
           │
┌──────────▼──────────┐
│      Aplicación     │
└──────────┬──────────┘
           │
┌──────────▼──────────┐
│         Datos       │
└─────────────────────┘
```

#### Capa de presentación

Se encarga de la interacción con el usuario.

Su función es:

- Mostrar información.
- Recoger datos.
- Permitir la navegación.

#### Capa de aplicación

Contiene la lógica de negocio de la aplicación.

Su función es:

- Procesar las solicitudes.
- Aplicar las reglas de funcionamiento.
- Coordinar el acceso a los datos.

#### Capa de datos

Se encarga del almacenamiento y recuperación de la información utilizada por la aplicación.

#### Flujo de información

Cuando un usuario realiza una operación, la información suele fluir entre las distintas capas.

```text
Usuario
   │
   ▼
Presentación
   │
   ▼
Aplicación
   │
   ▼
Datos
```

La respuesta sigue el camino inverso hasta llegar nuevamente al usuario.

#### Ventajas

- Facilita el mantenimiento.
- Favorece el trabajo en equipo.
- Permite reutilizar componentes.
- Reduce el impacto de los cambios.
- Mejora la escalabilidad.

#### Separación lógica y física

Las capas representan una separación lógica de responsabilidades.

No es necesario que cada capa se ejecute en un servidor diferente. En aplicaciones pequeñas todas pueden encontrarse en la misma máquina, mientras que en sistemas más complejos pueden distribuirse entre varios servidores.