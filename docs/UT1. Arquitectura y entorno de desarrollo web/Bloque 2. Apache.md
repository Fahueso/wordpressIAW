# 2.1. Entornos de desarrollo web

Antes de comenzar a desarrollar aplicaciones web es necesario disponer de un entorno de trabajo adecuado.

Un **entorno de desarrollo web** es el conjunto de herramientas, servicios y configuraciones que permiten desarrollar, probar y desplegar aplicaciones web.

En este módulo trabajaremos principalmente con aplicaciones basadas en tecnologías como:

- Apache o Nginx.
- PHP.
- MariaDB.
- Herramientas de desarrollo y administración.

El objetivo es disponer de un entorno que reproduzca, en la medida de lo posible, las condiciones reales de ejecución de una aplicación web.

## ¿Por qué son necesarios diferentes entornos?

Durante el desarrollo de una aplicación es habitual realizar cambios, corregir errores y probar nuevas funcionalidades.

Si estas modificaciones se realizaran directamente sobre la aplicación utilizada por los usuarios, cualquier error podría provocar interrupciones del servicio o pérdida de información.

Por este motivo las organizaciones suelen utilizar diferentes entornos para cada fase del ciclo de vida de la aplicación.

```text
Desarrollo
   │
   ▼
Pruebas
   │
   ▼
Producción
```

## Entorno de desarrollo

Es el entorno utilizado por desarrolladores y administradores para crear, modificar y probar aplicaciones.

En él se realizan tareas como:

- Programar nuevas funcionalidades.
- Corregir errores.
- Realizar pruebas iniciales.
- Experimentar con configuraciones.

Un entorno de desarrollo típico podría estar formado por:

```text
Equipo del desarrollador
├── Apache
├── PHP
├── MariaDB
├── Git
└── Visual Studio Code
```

### Ventajas

- Configuración sencilla.
- Permite realizar pruebas rápidas.
- No afecta a usuarios reales.
- Facilita el aprendizaje y la experimentación.

### Inconvenientes

- Puede diferir del entorno final de producción.
- Puede generar conflictos entre distintas versiones de software.
- Los errores de configuración afectan únicamente al equipo local.

Durante este módulo gran parte del trabajo se realizará en este tipo de entorno.

## Entorno de pruebas

También denominado entorno de **preproducción** o **staging**.

Su objetivo es comprobar que la aplicación funciona correctamente antes de ser puesta a disposición de los usuarios.

En este entorno se realizan:

- Pruebas funcionales.
- Comprobaciones de seguridad.
- Verificación de configuraciones.
- Pruebas de actualización o despliegue.

Sus características suelen ser similares a las del entorno de producción, aunque sin usuarios reales.

## Entorno de producción

Es el entorno utilizado por los usuarios finales.

Las aplicaciones desplegadas en producción deben ofrecer:

- Disponibilidad.
- Estabilidad.
- Seguridad.
- Rendimiento.

Ejemplos de entornos de producción son:

- La plataforma Aules de la Generalitat Valenciana.
- El portal web de una empresa.
- Un servidor Nextcloud corporativo.

Los cambios realizados en este entorno deben estar cuidadosamente controlados.

## Stacks de desarrollo web

Para ejecutar una aplicación web es necesario disponer de varios componentes que trabajen conjuntamente.

El conjunto de tecnologías utilizadas recibe el nombre de **stack**.

### Stack LAMP

Uno de los stacks más utilizados es **LAMP**:

```text
L → Linux
A → Apache
M → MariaDB (o MySQL)
P → PHP
```

Muchas aplicaciones web, como WordPress, Moodle o Nextcloud, pueden ejecutarse sobre este stack.

### Stack LEMP

Otra alternativa habitual es **LEMP**:

```text
L → Linux
E → Engine-X (Nginx)
M → MariaDB (o MySQL)
P → PHP
```

La principal diferencia es que Apache es sustituido por Nginx como servidor web.

## Virtualización

Una forma habitual de crear entornos aislados consiste en utilizar máquinas virtuales.

La virtualización permite ejecutar varios sistemas operativos independientes sobre un mismo equipo físico.

```text
Equipo físico
├── Máquina virtual 1
│   ├── Apache
│   └── PHP
└── Máquina virtual 2
    └── MariaDB
```

Gracias a esta técnica es posible separar servicios y realizar pruebas sin afectar al sistema principal.

### Ventajas de las máquinas virtuales

- Alto nivel de aislamiento.
- Facilitan las pruebas y experimentación.
- Permiten crear instantáneas y restaurar estados anteriores.
- Reproducen entornos reales de trabajo.

### Inconvenientes

- Consumen más memoria y almacenamiento.
- Requieren un sistema operativo completo en cada máquina virtual.
- Su arranque es más lento.

## Contenedores

Los contenedores constituyen una alternativa más ligera a las máquinas virtuales.

En lugar de virtualizar un sistema operativo completo, los contenedores comparten el sistema operativo anfitrión y ejecutan únicamente las aplicaciones y dependencias necesarias.

```text
Sistema anfitrión
├── Contenedor Apache
├── Contenedor PHP
└── Contenedor MariaDB
```

### Ventajas de los contenedores

- Menor consumo de recursos.
- Arranque muy rápido.
- Fácil distribución de aplicaciones.
- Configuraciones reproducibles.
- Mayor facilidad de despliegue.

### Inconvenientes

- Menor aislamiento que una máquina virtual.
- Administración inicial más compleja.

## Máquinas virtuales y contenedores

Aunque ambos mecanismos permiten aislar aplicaciones, existen diferencias importantes.

### Máquinas virtuales

```text
Equipo anfitrión
└── Máquina virtual
    ├── Sistema operativo
    ├── Apache
    ├── PHP
    └── MariaDB
```

- Incluyen un sistema operativo completo.
- Mayor aislamiento.
- Mayor consumo de recursos.

### Contenedores

```text
Equipo anfitrión
├── Contenedor Apache
├── Contenedor PHP
└── Contenedor MariaDB
```

- Comparten el sistema operativo anfitrión.
- Menor consumo de recursos.
- Despliegue más rápido.

## Docker

Actualmente una de las tecnologías de contenedores más utilizadas es **Docker**.

Docker permite crear, distribuir y ejecutar aplicaciones mediante contenedores.

Por ejemplo, un entorno Docker podría incluir:

```text
Contenedor Apache
   │
   ▼
Contenedor PHP
   │
   ▼
Contenedor MariaDB
```

De esta forma es posible reproducir el mismo entorno de desarrollo en distintos equipos y simplificar el despliegue de aplicaciones.

## Objetivo de este entorno

A lo largo de este módulo construiremos un entorno basado principalmente en:

```text
Apache
   │
PHP
   │
MariaDB
```

que nos permitirá desarrollar, probar y desplegar aplicaciones web.

Al finalizar este bloque deberás ser capaz de preparar un entorno funcional para ejecutar aplicaciones web, verificar su funcionamiento y solucionar los problemas más habituales de configuración.

## 2.2 Servidores web más utilizados

### Apache HTTP Server

Apache HTTP Server, conocido habitualmente como **Apache**, es uno de los servidores web más utilizados del mundo.

Se trata de un proyecto de software libre desarrollado por la **Apache Software Foundation**.

Entre sus características principales destacan:

- Software libre y de código abierto.
- Multiplataforma.
- Gran estabilidad y madurez.
- Amplia documentación.
- Arquitectura modular.
- Amplia compatibilidad con aplicaciones PHP.

Apache es especialmente popular en entornos educativos y empresariales debido a su facilidad de configuración y a la gran cantidad de documentación disponible.

Además, forma parte del conocido stack **LAMP**:

```text
Linux
Apache
MariaDB
PHP
```

que utilizaremos durante este módulo.

### Nginx

Nginx (pronunciado _engine-ex_) es otro de los servidores web más utilizados actualmente.

Fue diseñado con el objetivo de ofrecer un alto rendimiento y un consumo reducido de recursos.

Entre sus características destacan:

- Alto rendimiento.
- Bajo consumo de memoria.
- Arquitectura basada en eventos.
- Excelente capacidad para gestionar un gran número de conexiones simultáneas.
- Utilización frecuente como balanceador de carga y proxy inverso.

Actualmente muchas aplicaciones web utilizan Nginx como alternativa a Apache o como complemento a éste.

### Microsoft IIS

IIS (_Internet Information Services_) es el servidor web desarrollado por Microsoft para sus sistemas operativos Windows Server.

Entre sus características se encuentran:

- Integración con Windows.
- Herramientas gráficas de administración.
- Compatibilidad con tecnologías Microsoft.
- Integración con Active Directory.
- Soporte para aplicaciones ASP.NET.

Es habitual encontrarlo en organizaciones cuya infraestructura está basada principalmente en tecnologías Microsoft.

### Comparativa básica

| Característica          | Apache        | Nginx     | IIS            |
| ----------------------- | ------------- | --------- | -------------- |
| Software libre          | Sí            | Sí        | No             |
| Multiplataforma         | Sí            | Sí        | No             |
| Integración con Windows | Limitada      | Limitada  | Excelente      |
| Compatibilidad con PHP  | Muy buena     | Muy buena | Buena          |
| Administración gráfica  | Limitada      | Limitada  | Sí             |
### ¿Cuál utilizaremos?

Durante este módulo trabajaremos principalmente con **Apache HTTP Server** por varios motivos:

- Es uno de los servidores web más difundidos.
- Existe una gran cantidad de documentación y recursos de aprendizaje.
- Se integra fácilmente con PHP y MariaDB.
- Es la base de numerosas aplicaciones web como Moodle, WordPress o Nextcloud.
- Permite comprender los conceptos fundamentales que posteriormente pueden aplicarse a otros servidores web.

No obstante, los conceptos estudiados serán aplicables también a otros servidores como Nginx o IIS.

## 2.3 Apache HTTP Server

### Origen de Apache

Apache comenzó a desarrollarse en la década de los 90 como una evolución de un servidor web anterior desarrollado por el National Center for Supercomputing Applications (NCSA).

Actualmente el desarrollo y mantenimiento de Apache está coordinado por la **Apache Software Foundation (ASF)**, una organización sin ánimo de lucro responsable de numerosos proyectos de software libre.

### ¿Por qué es tan utilizado?

Apache ha mantenido su popularidad durante años debido a varias características que lo convierten en una solución muy flexible.

Entre sus principales ventajas destacan:

- Es software libre y de código abierto.
- Puede utilizarse gratuitamente.
- Funciona en diferentes sistemas operativos.
- Dispone de una amplia documentación.
- Es altamente configurable.
- Permite ampliar funcionalidades mediante módulos.
- Se integra fácilmente con PHP y otros lenguajes de programación.
- Cuenta con una gran comunidad de usuarios y desarrolladores.

Estas características han convertido a Apache en uno de los servidores web más utilizados tanto en entornos educativos como empresariales.

### Funciones habituales de Apache

Gracias a su sistema modular, Apache puede realizar tareas muy diversas:

- Publicar páginas web.
- Servir imágenes y documentos.
- Ejecutar aplicaciones PHP.
- Gestionar conexiones seguras mediante HTTPS.
- Autenticar usuarios.
- Registrar accesos y errores.
- Redirigir peticiones.
- Hospedar múltiples sitios web en un mismo servidor.

Por ello es habitual encontrar Apache en servidores web corporativos, plataformas educativas y aplicaciones de gestión empresarial.

## 2.4 Arquitectura modular de Apache

Una de las principales razones del éxito de Apache es su **arquitectura modular**.

Apache ha sido diseñado de forma que las funcionalidades básicas del servidor se encuentran en un núcleo reducido, mientras que las características adicionales se incorporan mediante módulos que pueden activarse o desactivarse según las necesidades de cada instalación.

Gracias a este diseño, un administrador puede configurar un servidor ligero con únicamente las funcionalidades necesarias o ampliar su capacidad añadiendo nuevos módulos.

```text
Apache
├── Núcleo del servidor
├── Módulos de autenticación
├── Módulos de seguridad
├── Módulos SSL
├── Módulos PHP
├── Módulos de reescritura
└── Otros módulos
```

### Ventajas de una arquitectura modular

Este diseño proporciona numerosas ventajas:

- Permite adaptar el servidor a distintas necesidades.
- Reduce el consumo de recursos.
- Facilita la administración del sistema.
- Permite incorporar nuevas funcionalidades sin modificar el núcleo.
- Incrementa la seguridad al mantener únicamente los módulos necesarios.
- Simplifica las actualizaciones y el mantenimiento.

Gracias a esta flexibilidad, el mismo servidor Apache puede utilizarse para alojar un pequeño sitio web personal o una aplicación empresarial de gran tamaño.

### Módulos en Apache

Un módulo es un componente software que añade una funcionalidad concreta al servidor web.

Por ejemplo:

- Soporte para HTTPS.
- Autenticación de usuarios.
- Reescritura de URL.
- Ejecución de aplicaciones PHP.
- Generación de estadísticas.
- Control de acceso.

Cuando un módulo no es necesario puede permanecer desactivado, evitando consumir recursos y reduciendo la superficie de ataque del sistema.

### Gestión de módulos en Debian

En sistemas basados en Debian y Ubuntu, los módulos suelen almacenarse en:

```text
/etc/apache2/mods-available
```

Esta carpeta contiene los módulos disponibles para el servidor.

Cuando un módulo se activa, Apache crea los enlaces correspondientes en:

```text
/etc/apache2/mods-enabled
```

Por tanto:

```text
mods-available
   │
   ▼
Módulo disponible

mods-enabled
   │
   ▼
Módulo cargado por Apache
```

### Activación y desactivación de módulos

Apache proporciona herramientas específicas para gestionar módulos.

**Activar un módulo**

```bash
sudo a2enmod nombre_modulo
```

Ejemplo:

```bash
sudo a2enmod rewrite
```

**Desactivar un módulo**

```bash
sudo a2dismod nombre_modulo
```

Ejemplo:

```bash
sudo a2dismod rewrite
```

Tras realizar cambios es necesario reiniciar o recargar el servicio:

```bash
sudo systemctl restart apache2
```

### Comprobación de módulos cargados

Podemos consultar los módulos cargados por Apache mediante el comando:

```bash
sudo apache2ctl -M
```

La salida mostrará una lista de todos los módulos actualmente activos.

Ejemplo simplificado:

```text
rewrite_module
ssl_module
alias_module
dir_module
php_module
```

### Algunos módulos habituales

Apache dispone de decenas de módulos. A continuación se muestran algunos de los más utilizados.

**mod_alias**

Permite crear alias para acceder a directorios o recursos utilizando rutas diferentes.

Ejemplo:

```text
http://servidor/manual
```

puede apuntar a una carpeta distinta dentro del sistema de archivos.

**mod_dir**

Gestiona las páginas predeterminadas de un directorio.

Por ejemplo:

```text
index.html
index.php
```

Cuando un usuario accede a:

```text
http://servidor/
```

Apache buscará automáticamente uno de estos archivos.

**mod_autoindex**

Permite generar listados de directorios cuando no existe una página de inicio.

Por ejemplo:

```text
http://servidor/documentos/
```

podría mostrar el contenido de esa carpeta.

**mod_rewrite**

Uno de los módulos más utilizados.

Permite modificar y reescribir URL.

Por ejemplo:

```text
https://web.com/producto.php?id=25
```

puede transformarse en:

```text
https://web.com/productos/25
```

Las URL resultantes son más legibles y fáciles de recordar.

**mod_ssl**

Añade soporte para comunicaciones seguras mediante HTTPS.

Gracias a este módulo Apache puede:

- Utilizar certificados digitales.
- Cifrar las comunicaciones.
- Garantizar la autenticidad del servidor.

Actualmente es uno de los módulos más importantes en cualquier servidor web.

**mod_userdir**

Permite que cada usuario del sistema disponga de un directorio web personal.

Por ejemplo:

```text
http://servidor/~usuario
```

Esta funcionalidad ha sido utilizada tradicionalmente en entornos educativos y de desarrollo.

### Módulos de autenticación

Apache incluye diversos módulos relacionados con la autenticación y autorización de usuarios.

Entre ellos destacan:

- `mod_auth_basic`
- `mod_authn_*`
- `mod_authz_*`

Estos módulos permiten:

- Solicitar usuario y contraseña.
- Validar credenciales.
- Restringir el acceso a determinados recursos.
- Controlar permisos.

Más adelante utilizaremos algunos de ellos para proteger recursos web.

### Arquitectura modular y seguridad

Una buena práctica de administración consiste en activar únicamente los módulos necesarios para el funcionamiento del servidor.

Cuantos más módulos estén cargados:

- Mayor será el consumo de recursos.
- Más compleja será la administración.
- Mayor será la superficie de ataque.

Por este motivo es habitual revisar periódicamente los módulos activos y deshabilitar aquellos que no sean necesarios.

## 2.5 Instalación de Apache

Una vez comprendido el papel que desempeña Apache dentro de una aplicación web, el siguiente paso consiste en instalarlo y verificar su correcto funcionamiento.

En este módulo utilizaremos sistemas basados en Debian GNU/Linux, por lo que la instalación se realizará mediante el gestor de paquetes **APT**.

### Requisitos previos

Para instalar software en el sistema es necesario disponer de permisos de administración.

Podemos ejecutar los comandos utilizando `sudo` o trabajando directamente con el usuario `root`.

Antes de instalar cualquier paquete es recomendable actualizar la información de los repositorios:

```bash
sudo apt update
```

### Instalación de Apache

Apache se distribuye en Debian mediante el paquete:

```text
apache2
```

La instalación se realiza con el siguiente comando:

```bash
sudo apt install apache2
```

Durante el proceso se instalarán también algunos paquetes adicionales necesarios para el funcionamiento del servidor.

### Paquetes instalados

Además del servidor web, suelen instalarse componentes auxiliares como:

**apache2-data**

Contiene recursos comunes utilizados por Apache:

- Páginas de error.
- Iconos.
- Archivos estáticos.
- Configuraciones básicas.

**apache2-utils**

Incluye herramientas de administración y diagnóstico.

Algunas de las más utilizadas son:

_ab_

Permite realizar pruebas de rendimiento sobre un servidor web.

Ejemplo:

```bash
ab -n 1000 -c 10 http://localhost/
```

_htpasswd_

Permite crear y gestionar ficheros de usuarios para autenticación básica.

### Inicio automático del servicio

Tras la instalación, Apache suele iniciarse automáticamente.

Podemos comprobar el estado del servicio mediante:

```bash
sudo systemctl status apache2
```

Si el servidor está funcionando correctamente observaremos un resultado similar a:

```text
Active: active (running)
```

### Gestión del servicio

Los sistemas Linux actuales utilizan normalmente **systemd** para gestionar servicios.

**Iniciar Apache**

```bash
sudo systemctl start apache2
```

**Detener Apache**

```bash
sudo systemctl stop apache2
```

**Reiniciar Apache**

```bash
sudo systemctl restart apache2
```

**Recargar la configuración**

```bash
sudo systemctl reload apache2
```

**Consultar el estado**

```bash
sudo systemctl status apache2
```

### Estructura básica de directorios

Después de la instalación encontraremos varios directorios importantes.

**Directorio de configuración**

```text
/etc/apache2
```

Contiene los archivos de configuración del servidor.

Entre ellos destacan:

```text
apache2.conf
ports.conf
```

y diversos subdirectorios para módulos y sitios web.

**Directorio de contenido web**

```text
/var/www/html
```

Es el directorio utilizado por defecto para publicar páginas web.

Cualquier archivo almacenado aquí podrá ser servido por Apache.

### Primera comprobación

Una vez instalado Apache, podemos abrir un navegador y acceder a:

```text
http://localhost
```

Si todo funciona correctamente aparecerá la página de bienvenida de Apache.

Esta página confirma que:

- Apache está instalado.
- El servicio está funcionando.
- El servidor acepta conexiones HTTP.

### Publicación de nuestra primera página

Podemos añadir una página de prueba:

**Crear el archivo**

```bash
sudo nano /var/www/html/prueba.html
```

Contenido:

```html
<!DOCTYPE html>
<html>
<head>
<title>Mi primer servidor web</title>
</head>
<body>
<h1>Servidor Apache funcionando correctamente</h1>
</body>
</html>
```

**Guardar cambios**

Una vez guardado el fichero, al acceder nuevamente a:

```text
http://localhost/prueba.html
```

el navegador mostrará nuestra página.


### Problemas habituales durante la instalación

**El puerto 80 está ocupado**

Si otro servicio utiliza el puerto 80, Apache no podrá iniciarse.

Podemos identificar el proceso que está utilizando dicho puerto:

```bash
sudo ss -tulpn | grep :80
```

**Error de configuración**

Si Apache no arranca después de modificar algún fichero:

```bash
sudo apache2ctl configtest
```

suele proporcionar información suficiente para localizar el problema.

**Página no accesible**

Comprobar:

- Que el servicio esté activo.
- Que el cortafuegos permita conexiones.
- Que exista un archivo `index.html`.
- Que los permisos sean correctos.

### Comprobación mediante la dirección IP

Además de utilizar `localhost`, también podemos acceder mediante la dirección IP del equipo.

La forma más sencilla de conocerla es:

```bash
hostname -I
```

Como alternativa podemos utilizar:

```bash
ip addr
```

Supongamos que la dirección IP es:

```text
192.168.1.100
```

Podemos acceder desde el navegador mediante:

```text
http://192.168.1.100
```

Si la página se muestra correctamente, Apache está atendiendo solicitudes a través de la red.

### Comprobación mediante herramientas de terminal

También es posible verificar el funcionamiento utilizando herramientas de línea de comandos.

**Utilizando curl**

```bash
curl http://localhost
```

El servidor devolverá el contenido HTML de la página solicitada.

Ejemplo:

```html
<h1>Apache funciona correctamente</h1>
```

**Utilizando wget**

```bash
wget -O - http://localhost
```

Estas herramientas son especialmente útiles en servidores sin entorno gráfico.

### Registros del servidor

Apache registra información sobre su funcionamiento en distintos archivos de log.

Estos registros son fundamentales para detectar incidencias.

**Registro de errores**

```text
/var/log/apache2/error.log
```

Permite consultar:

- Errores de configuración.
- Problemas de permisos.
- Fallos de módulos.
- Errores internos del servidor.

Visualización rápida:

```bash
sudo tail /var/log/apache2/error.log
```

**Registro de accesos**

```text
/var/log/apache2/access.log
```

Contiene información sobre las solicitudes realizadas al servidor.

Ejemplo:

```text
192.168.1.50 - - [01/Sep/2026:10:15:21 +0200] "GET /index.html HTTP/1.1" 200 1234
```

Esta información permite conocer:

- Qué recurso se ha solicitado.
- Qué método HTTP se ha utilizado.
- Qué código de respuesta ha devuelto el servidor.
- El tamaño de la respuesta enviada.
- La fecha y hora del acceso.

## 2.7 Configuración básica de Apache

Una vez instalado y comprobado el funcionamiento del servidor web, el siguiente paso consiste en conocer cómo se organiza su configuración.

Apache dispone de una estructura jerárquica de archivos y directorios que permite configurar distintos aspectos de su funcionamiento sin necesidad de modificar el núcleo del servidor.

Comprender esta estructura resulta fundamental para administrar correctamente un servidor web.

### Directorio de configuración

En sistemas Debian y Ubuntu, los archivos de configuración de Apache se encuentran en:

```text
/etc/apache2
```

Podemos explorar su contenido mediante:

```bash
ls /etc/apache2
```

Una instalación típica contiene archivos y directorios similares a los siguientes:

```text
apache2.conf
ports.conf
mods-available
mods-enabled
conf-available
conf-enabled
sites-available
sites-enabled
```

### Archivo principal de configuración

El archivo principal de Apache es:

```text
/etc/apache2/apache2.conf
```

Este fichero contiene la configuración global del servidor.

Entre otros aspectos permite definir:

- Configuración general de Apache.
- Directivas comunes para todo el servidor.
- Configuración de directorios.
- Inclusión de otros archivos de configuración.
- Parámetros de seguridad y funcionamiento.

Aunque gran parte de la configuración diaria se realiza mediante otros archivos más específicos, algunas configuraciones globales requieren modificar este fichero.

### Configuración de puertos

Apache utiliza el archivo:

```text
/etc/apache2/ports.conf
```

para definir los puertos en los que escuchará conexiones entrantes.

Por ejemplo:

```apache
Listen 80
```

La directiva `Listen` indica que Apache aceptará conexiones TCP en el puerto 80.

También es habitual encontrar:

```apache
Listen 443
```

para conexiones HTTPS.

Por tanto, este fichero determina qué puertos utilizará Apache para recibir las solicitudes de los clientes.

### Sitios web disponibles

Apache permite alojar varios sitios web en un mismo servidor.

Las configuraciones de los distintos sitios se almacenan en:

```text
/etc/apache2/sites-available
```

Por ejemplo:

```bash
ls /etc/apache2/sites-available
```

puede mostrar:

```text
000-default.conf
default-ssl.conf
```

Este directorio contiene los sitios definidos, independientemente de que estén activos o no.

### El sitio por defecto

Durante la instalación se crea normalmente un sitio denominado:

```text
000-default.conf
```

Este archivo define el sitio web predeterminado del servidor.

Apache utilizará esta configuración cuando no exista otra más específica que deba responder a la solicitud recibida.

### Sitios web activos

Los sitios que realmente utilizará Apache se encuentran en:

```text
/etc/apache2/sites-enabled
```

Normalmente este directorio contiene enlaces simbólicos a los archivos almacenados en:

```text
sites-available
```

```text
sites-available
   │
   ▼
000-default.conf
   │
   ▼
sites-enabled
```

Por tanto:

- `sites-available` contiene los sitios definidos.
- `sites-enabled` contiene los sitios activos.

Cuando Apache arranca únicamente carga las configuraciones presentes en `sites-enabled`.

---

### Activación de sitios web

Apache incorpora herramientas específicas para gestionar sitios web.

**Activar un sitio**

```bash
sudo a2ensite nombre_sitio
```

Ejemplo:

```bash
sudo a2ensite miweb.conf
```

**Desactivar un sitio**

```bash
sudo a2dissite nombre_sitio
```

Ejemplo:

```bash
sudo a2dissite miweb.conf
```

Después de cualquier modificación es necesario recargar la configuración:

```bash
sudo systemctl reload apache2
```

---

### Configuraciones adicionales

Apache también permite incorporar configuraciones complementarias mediante:

```text
/etc/apache2/conf-available
```

Estas configuraciones suelen utilizarse para:

- Alias.
- Documentación.
- Configuraciones compartidas.
- Opciones generales reutilizables.

Las configuraciones activas aparecen en:

```text
/etc/apache2/conf-enabled
```

---

### Activación de configuraciones

**Activar una configuración**

```bash
sudo a2enconf nombre_configuracion
```

Ejemplo:

```bash
sudo a2enconf apache2-doc
```

**Desactivar una configuración**

```bash
sudo a2disconf nombre_configuracion
```

Después de cualquier cambio:

```bash
sudo systemctl reload apache2
```

---

### Jerarquía de la configuración

Durante el arranque, Apache procesa de forma automática los principales archivos y directorios de configuración.

De forma simplificada:

```text
apache2.conf
   │
   ├── ports.conf
   ├── mods-enabled
   ├── conf-enabled
   └── sites-enabled
```

A partir de estos elementos Apache construye la configuración efectiva del servidor.

Por este motivo es importante recordar que Apache trabaja principalmente con los elementos activos (`*-enabled`), no con todos los disponibles (`*-available`).

---

### DocumentRoot

Cada sitio web necesita un directorio desde el que publicar sus recursos.

Este directorio recibe el nombre de **DocumentRoot**.

Por ejemplo:

```apache
DocumentRoot /var/www/html
```

indica que Apache buscará los recursos del sitio en:

```text
/var/www/html
```

Cuando un usuario solicita:

```text
http://servidor/index.html
```

Apache buscará el fichero:

```text
/var/www/html/index.html
```

dentro del DocumentRoot configurado para ese sitio.

---

### Directorio de publicación por defecto

En las instalaciones estándar de Debian y Ubuntu, el sitio web predeterminado utiliza:

```text
/var/www/html
```

como DocumentRoot.

Por ello, los archivos almacenados en dicho directorio pueden ser publicados directamente por Apache.

Por ejemplo:

```bash
echo "<h1>Hola ASIR</h1>" | sudo tee /var/www/html/index.html
```

---

### Modificación de la página principal

Podemos sustituir la página predeterminada por una propia.

Editar:

```bash
sudo nano /var/www/html/index.html
```

Contenido de ejemplo:

```html
<!DOCTYPE html>
<html>
<head>
<title>Servidor Apache</title>
</head>
<body>
<h1>Configuración básica completada</h1>
</body>
</html>
```

Al acceder a:

```text
http://localhost
```

Apache mostrará la nueva página.

---

### Recarga y reinicio del servidor

Después de modificar la configuración es necesario aplicar los cambios.

**Recargar la configuración**

```bash
sudo systemctl reload apache2
```

Apache vuelve a leer los archivos de configuración sin detener completamente el servicio.

**Reiniciar el servidor**

```bash
sudo systemctl restart apache2
```

Apache detiene y vuelve a iniciar todos sus procesos.

Siempre que sea posible es preferible utilizar `reload`, ya que provoca una interrupción mínima o nula del servicio.

---

### Validación de la configuración

Antes de aplicar cambios es recomendable verificar la sintaxis de los archivos modificados.

```bash
sudo apache2ctl configtest
```

Si la configuración es correcta aparecerá:

```text
Syntax OK
```

Esta comprobación ayuda a evitar errores que podrían impedir el arranque del servidor.

---

### Buenas prácticas

- Mantener los sitios personalizados en `sites-available`.
- Activar únicamente los sitios necesarios.
- Utilizar comentarios en los archivos de configuración.
- Documentar los cambios realizados.
- Realizar copias de seguridad antes de modificar configuraciones importantes.
- Validar siempre la configuración mediante `apache2ctl configtest`.
- Utilizar `reload` siempre que sea posible.

---

### Ideas clave

Al finalizar este apartado debes ser capaz de:

- Identificar la estructura de configuración de Apache.
- Comprender la función de `apache2.conf` y `ports.conf`.
- Diferenciar sitios definidos y sitios activos.
- Comprender el papel del sitio por defecto `000-default.conf`.
- Explicar qué es un `DocumentRoot`.
- Activar y desactivar sitios mediante `a2ensite` y `a2dissite`.
- Activar y desactivar configuraciones mediante `a2enconf` y `a2disconf`.
- Modificar el contenido publicado por Apache.
- Validar la configuración antes de aplicarla.
- Aplicar cambios mediante `reload` o `restart`.

## 2.7 Directorios personales

Apache permite que cada usuario del sistema disponga de un espacio web propio dentro de su directorio personal.

Esta funcionalidad resulta especialmente útil en entornos educativos y de desarrollo, ya que permite que varios usuarios publiquen sus páginas web sin necesidad de modificar la configuración principal del servidor.

Cada usuario podrá publicar contenido en su propio directorio y acceder a él mediante una URL específica.

Por ejemplo:

```text
/home/alumno/public_html
```

podrá ser accesible desde:

```text
http://localhost/~alumno
```

---

### El módulo mod_userdir

La funcionalidad de directorios personales se proporciona mediante el módulo:

```text
mod_userdir
```

Este módulo permite asociar un directorio de cada usuario a una dirección web específica.

De esta forma, Apache será capaz de localizar y servir automáticamente los contenidos publicados por cada usuario.

---

### Activación del módulo

Para habilitar esta funcionalidad debemos activar el módulo correspondiente.

```bash
sudo a2enmod userdir
```

Una vez activado, es necesario recargar la configuración del servidor:

```bash
sudo systemctl reload apache2
```

También podemos comprobar que el módulo está cargado:

```bash
sudo apache2ctl -M | grep userdir
```

Si todo funciona correctamente aparecerá una salida similar a:

```text
userdir_module
```

---

### Configuración básica

Al activar el módulo se utiliza una configuración similar a la siguiente:

```apache
<IfModule mod_userdir.c>
    UserDir public_html
    UserDir disabled root
</IfModule>
```

La directiva:

```apache
UserDir public_html
```

indica que Apache buscará el contenido web de cada usuario dentro de un directorio denominado:

```text
public_html
```

situado en su directorio personal.

Por ejemplo:

```text
/home/alumno/public_html
```

Por motivos de seguridad, el usuario `root` suele tener esta funcionalidad deshabilitada:

```apache
UserDir disabled root
```

---

### Creación del directorio personal

Cada usuario debe crear su propio directorio de publicación.

```bash
mkdir ~/public_html
```

Podemos verificar su creación mediante:

```bash
ls ~
```

Debería aparecer:

```text
public_html
```

---

### Creación de una página de prueba

Una vez creado el directorio, podemos publicar una página sencilla.

Crear el archivo:

```bash
nano ~/public_html/index.html
```

Contenido:

```html
<!DOCTYPE html>
<html>
<head>
<title>Página personal</title>
</head>
<body>
<h1>Mi espacio web personal</h1>
</body>
</html>
```

Guardar el archivo y cerrar el editor.

---

### Acceso al contenido publicado

Si el módulo está correctamente configurado, podremos acceder a la página mediante:

```text
http://localhost/~usuario
```

Por ejemplo:

```text
http://localhost/~alumno
```

Apache buscará automáticamente:

```text
/home/alumno/public_html/index.html
```

y enviará su contenido al navegador.

```text
Navegador
   │
   ▼
http://localhost/~alumno
   │
   ▼
Apache
   │
   ▼
/home/alumno/public_html/index.html
```

---

### Permisos de acceso

Para que Apache pueda publicar el contenido, debe tener permisos suficientes para acceder al directorio `public_html`.

La configuración exacta dependerá de la política de permisos del sistema.

Un ejemplo habitual consiste en permitir la lectura y ejecución sobre el directorio publicado:

```bash
chmod 755 ~/public_html
```

Podemos comprobar los permisos mediante:

```bash
ls -ld ~/public_html
```

Si Apache no puede acceder al directorio, la página no será visible aunque exista correctamente.

---

### Página predeterminada

Cuando un usuario accede a:

```text
http://localhost/~usuario
```

Apache busca automáticamente una página de inicio dentro del directorio personal.

Los nombres más habituales son:

```text
index.html
index.php
```

Si no encuentra ninguno de ellos, el comportamiento dependerá de la configuración del servidor.

---

### Ejecución de PHP en directorios personales

Por motivos de seguridad, las distribuciones Debian y Ubuntu suelen deshabilitar la ejecución de PHP dentro de los directorios personales de los usuarios.

Esto significa que:

```text
index.html
```

funcionará correctamente, pero un archivo como:

```text
index.php
```

puede no ejecutarse aunque PHP esté instalado.

Esta restricción se configura normalmente en un archivo similar a:

```text
/etc/apache2/mods-available/php*.conf
```

donde suele aparecer un bloque parecido a:

```apache
<IfModule mod_userdir.c>
    <Directory /home/*/public_html>
        php_admin_flag engine Off
    </Directory>
</IfModule>
```

La directiva:

```apache
php_admin_flag engine Off
```

impide que Apache ejecute código PHP dentro de los directorios personales.

Si se desea permitir la ejecución de PHP será necesario modificar esta configuración y reiniciar Apache.

> En entornos reales esta restricción suele mantenerse por motivos de seguridad.

---

### Ventajas de los directorios personales

- Cada usuario dispone de su propio espacio web.
- No es necesario crear un sitio independiente para cada alumno.
- Facilita las prácticas de desarrollo web.
- Permite aislar el trabajo de distintos usuarios.
- Simplifica las pruebas en entornos educativos.

---

### Limitaciones

- No suele utilizarse en entornos de producción.
- Requiere una correcta configuración de permisos.
- PHP suele estar deshabilitado por defecto.
- Resulta menos flexible que el uso de Virtual Hosts.

---

### Buenas prácticas

- Mantener los archivos personales dentro de `public_html`.
- Utilizar permisos adecuados.
- Evitar publicar información sensible.
- Verificar el funcionamiento con una página HTML sencilla antes de utilizar otras tecnologías.
- Comprobar los registros de Apache cuando aparezcan errores de acceso.

---

### Ideas clave

Al finalizar este apartado debes ser capaz de:

- Explicar qué son los directorios personales de Apache.
- Comprender la función del módulo `mod_userdir`.
- Activar y verificar el funcionamiento del módulo.
- Crear un directorio `public_html`.
- Publicar contenido web personal.
- Acceder a dicho contenido mediante la URL `http://localhost/~usuario`.
- Comprender las limitaciones relacionadas con los permisos y la ejecución de PHP.

## 2.8 Ampliación gestión de módulos en Apache

### Estructura de los módulos

La mayoría de los módulos están formados por dos archivos:

**Archivo `.load`**

Indica a Apache qué módulo debe cargarse.

Ejemplo:

```text
rewrite.load
```

**Archivo `.conf`**

Contiene la configuración asociada al módulo.

Ejemplo:

```text
rewrite.conf
```

No todos los módulos disponen de un archivo de configuración, pero muchos de ellos sí lo utilizan.

---

### Módulos habituales

A continuación se muestran algunos de los módulos más utilizados durante la administración de servidores Apache.

**mod_alias**

Permite crear alias para directorios y recursos.

Por ejemplo:

```text
http://servidor/manual
```

puede apuntar a una ubicación diferente dentro del sistema de archivos.

Se utiliza frecuentemente para simplificar rutas de acceso.

**mod_dir**

Gestiona las páginas de inicio de cada directorio.

Por ejemplo:

```text
index.html
index.php
```

Cuando un usuario accede a:

```text
http://servidor/
```

Apache buscará automáticamente uno de estos archivos para mostrarlo.

**mod_autoindex**

Permite generar listados automáticos de directorios cuando no existe una página de inicio.

Por ejemplo:

```text
http://servidor/documentos/
```

podría mostrar el contenido de la carpeta.

Esta funcionalidad suele deshabilitarse en entornos de producción por motivos de seguridad.

**mod_rewrite**

Es uno de los módulos más utilizados.

Permite modificar y reescribir URL.

Ejemplo:

```text
https://web.com/producto.php?id=25
```

puede transformarse en:

```text
https://web.com/productos/25
```

Gracias a ello es posible utilizar URL más legibles y amigables para los usuarios.

**mod_ssl**

Añade soporte para HTTPS.

Permite:

- Utilizar certificados digitales.
- Cifrar las comunicaciones.
- Verificar la identidad del servidor.

Actualmente es imprescindible en prácticamente cualquier sitio web publicado en Internet.

**mod_userdir**

Permite que cada usuario disponga de un directorio web personal.

Por ejemplo:

```text
http://localhost/~alumno
```

Este módulo fue estudiado en el apartado anterior.

**mod_status**

Proporciona información sobre el estado del servidor.

Puede utilizarse para consultar:

- Conexiones activas.
- Procesos en ejecución.
- Estadísticas de funcionamiento.

Es especialmente útil para tareas de monitorización.

---

### Módulos de autenticación

Apache dispone de varios módulos destinados al control de acceso.

Entre los más importantes se encuentran:

```text
mod_auth_basic
mod_authn_*
mod_authz_*
```

Estos módulos permiten:

- Solicitar usuario y contraseña.
- Verificar credenciales.
- Restringir el acceso a recursos.
- Aplicar permisos.

Más adelante utilizaremos algunos de ellos para proteger directorios y páginas web.

---

### Buenas prácticas

Aunque Apache permite activar numerosos módulos, es recomendable habilitar únicamente aquellos que realmente sean necesarios.

Activar módulos innecesarios puede provocar:

- Mayor consumo de recursos.
- Configuraciones más complejas.
- Incremento de la superficie de ataque.
- Mayor dificultad de mantenimiento.

Una buena práctica consiste en revisar periódicamente los módulos activos y deshabilitar aquellos que no se utilicen.

---

### Ejemplo práctico

Activar HTTPS y reescritura de URL:

```bash
sudo a2enmod ssl
sudo a2enmod rewrite
sudo systemctl reload apache2
```

Comprobar la carga de los módulos:

```bash
sudo apache2ctl -M | grep ssl
sudo apache2ctl -M | grep rewrite
```

Si aparecen:

```text
ssl_module
rewrite_module
```

la activación se ha realizado correctamente.

---

### Ideas clave

Al finalizar este apartado debes ser capaz de:

- Explicar qué es un módulo de Apache.
- Diferenciar módulos instalados y módulos activos.
- Activar y desactivar módulos mediante `a2enmod` y `a2dismod`.
- Consultar los módulos cargados por Apache.
- Reconocer la función de módulos habituales como `mod_ssl`, `mod_rewrite` o `mod_userdir`.
- Comprender la relación entre modularidad, rendimiento y seguridad.
- Aplicar buenas prácticas en la gestión de módulos.

## 2.9 Control de accesos

En muchas ocasiones no todos los recursos publicados por un servidor web deben estar disponibles para cualquier usuario.

Por ejemplo:

- Paneles de administración.
- Intranets corporativas.
- Áreas privadas de usuarios.
- Documentación interna.
- Herramientas de gestión.

Apache incorpora diferentes mecanismos que permiten controlar quién puede acceder a determinados recursos.

Estos mecanismos pueden basarse en:

- Usuario y contraseña.
- Dirección IP.
- Grupos de usuarios.
- Reglas de autorización.

---

### Autenticación y autorización

Aunque suelen utilizarse conjuntamente, son conceptos diferentes.

**Autenticación**

La autenticación consiste en verificar la identidad de un usuario.

Por ejemplo:

```text
Usuario: alumno
Contraseña: ********
```

El servidor comprueba si las credenciales son correctas.

La pregunta que responde es: ¿Quién eres?

**Autorización**

La autorización determina qué recursos puede utilizar un usuario autenticado.

Por ejemplo:

```text
Usuario autenticado
   │
   ├── Acceso permitido a /privado
   │
   └── Acceso denegado a /admin
```

La pregunta que responde es: ¿Qué puedes hacer?

---

### Métodos de autenticación en Apache

Apache soporta varios mecanismos de autenticación.

Los más habituales son:

- Autenticación básica (Basic Authentication).
- Autenticación Digest.
- Bases de datos.
- LDAP.
- Directorios corporativos.

En este módulo estudiaremos principalmente la autenticación básica.

---

### Autenticación básica

La autenticación básica es el mecanismo más sencillo para proteger recursos web.

Cuando un usuario intenta acceder a un recurso protegido, el navegador muestra una ventana solicitando:

```text
Usuario
Contraseña
```

Si las credenciales son válidas, Apache permite el acceso.

```text
Cliente
   │
   ▼
Apache
   │
   │ Solicita credenciales
   ▼
Usuario
   │
   │ Introduce usuario y contraseña
   ▼
Apache
   │
   │ Verifica credenciales
   ▼
Acceso permitido o denegado
```

---

### El módulo mod_auth_basic

La autenticación básica se implementa mediante el módulo:

```text
mod_auth_basic
```

Podemos comprobar si está activo:

```bash
sudo apache2ctl -M | grep auth_basic
```

Si fuera necesario activarlo:

```bash
sudo a2enmod auth_basic
sudo systemctl reload apache2
```

---

### Creación del archivo de contraseñas

Apache almacena los usuarios y contraseñas en un fichero especial.

Para crearlo utilizamos la herramienta:

```bash
htpasswd
```

**Crear el fichero e introducir el primer usuario**

```bash
sudo htpasswd -c /etc/apache2/.htpasswd alumno
```

El sistema solicitará la contraseña:

```text
New password:
Re-type new password:
```

**Añadir usuarios adicionales**

Una vez creado el fichero no debemos utilizar la opción `-c`, ya que sobrescribiría el contenido existente.

```bash
sudo htpasswd /etc/apache2/.htpasswd profesor
```

Podemos añadir tantos usuarios como necesitemos.

---

### Protección de un directorio

Supongamos que queremos proteger el directorio:

```text
/var/www/html/privado
```

Creamos la carpeta:

```bash
sudo mkdir /var/www/html/privado
```

y una página de prueba:

```bash
echo "<h1>Zona privada</h1>" | sudo tee /var/www/html/privado/index.html
```

---

### Configuración de la autenticación

Podemos añadir una configuración similar a la siguiente:

```apache
<Directory "/var/www/html/privado">
    AuthType Basic
    AuthName "Acceso restringido"
    AuthUserFile /etc/apache2/.htpasswd
    Require valid-user
</Directory>
```

---

### Explicación de las directivas

**AuthType**

Indica el tipo de autenticación utilizado.

```apache
AuthType Basic
```

En este caso utilizamos autenticación básica.

**AuthName**

Define el texto mostrado al usuario en la ventana de autenticación.

```apache
AuthName "Acceso restringido"
```

**AuthUserFile**

Indica la ubicación del archivo que contiene los usuarios y contraseñas.

```apache
AuthUserFile /etc/apache2/.htpasswd
```

**Require valid-user**

Permite el acceso a cualquier usuario incluido en el archivo de contraseñas.

```apache
Require valid-user
```

---

### Aplicación de cambios

Después de modificar la configuración debemos comprobar su sintaxis:

```bash
sudo apache2ctl configtest
```

Si el resultado es:

```text
Syntax OK
```

podemos aplicar los cambios:

```bash
sudo systemctl reload apache2
```

---

### Comprobación del funcionamiento

Al acceder a:

```text
http://localhost/privado
```

el navegador solicitará las credenciales configuradas.

Si el usuario y la contraseña son correctos:

```text
Acceso permitido
```

En caso contrario:

```text
401 Unauthorized
```

---

### Restricción a usuarios concretos

No siempre es necesario permitir el acceso a todos los usuarios registrados.

Por ejemplo:

```apache
Require user profesor
```

únicamente permitirá acceder al usuario:

```text
profesor
```

También es posible especificar varios usuarios:

```apache
Require user profesor administrador
```

---

### Control de acceso por dirección IP

Apache también puede restringir accesos según el origen de la conexión.

Por ejemplo:

```apache
<Directory "/var/www/html/interna">
    Require ip 192.168.1.0/24
</Directory>
```

Esto permite el acceso únicamente desde equipos de la red:

```text
192.168.1.x
```

---

### Combinación de criterios

Es posible combinar distintos mecanismos de control de acceso.

Por ejemplo:

```text
Usuario válido
+
IP autorizada
```

Esto incrementa la seguridad del recurso protegido.

---

### Limitaciones de la autenticación básica

La autenticación básica presenta algunas limitaciones:

- El navegador envía las credenciales en cada solicitud.
- No cifra la información por sí misma.
- Requiere HTTPS para proteger adecuadamente las contraseñas.

Por este motivo es recomendable utilizar siempre:

```text
HTTPS + Autenticación básica
```

cuando se protejan recursos reales.

---

### Buenas prácticas

- Utilizar HTTPS en recursos protegidos.
- Limitar el acceso únicamente a los usuarios necesarios.
- Proteger los archivos de contraseñas.
- Comprobar periódicamente los permisos configurados.
- Revisar los registros de acceso para detectar intentos no autorizados.
- Eliminar usuarios que ya no necesiten acceso.

---

Para cerrar por completo el RA1 en lo que respecta al servidor web, conviene abordar dos aspectos adicionales: la seguridad en las comunicaciones (HTTPS) y el uso de plataformas integradas de desarrollo.

## 2.10 HTTPS con certificado autofirmado

En el apartado 2.8 activamos el módulo `mod_ssl` al hablar de la gestión de módulos, pero sin llegar a configurar un certificado real. Vamos a completarlo con un certificado autofirmado, válido para entornos de desarrollo.

### Activar el módulo SSL

```bash
sudo a2enmod ssl
sudo systemctl restart apache2
```

### Activar el sitio SSL por defecto

```bash
sudo a2ensite default-ssl
sudo systemctl reload apache2
```

### Generar un certificado autofirmado

```bash
sudo openssl req -x509 -nodes -days 365 \
  -newkey rsa:2048 \
  -keyout /etc/ssl/private/apache-selfsigned.key \
  -out /etc/ssl/certs/apache-selfsigned.crt
```

Durante el proceso se solicitarán datos como el país, la organización o el nombre del servidor (`Common Name`).

### Configurar el sitio para utilizar el certificado

En el archivo:

```text
/etc/apache2/sites-available/default-ssl.conf
```

se deben indicar las rutas al certificado y a la clave privada:

```apache
SSLCertificateFile      /etc/ssl/certs/apache-selfsigned.crt
SSLCertificateKeyFile   /etc/ssl/private/apache-selfsigned.key
```

### Aplicar y comprobar

```bash
sudo apache2ctl configtest
sudo systemctl reload apache2
```

Acceder a:

```text
https://localhost
```

El navegador mostrará una advertencia de seguridad, ya que el certificado no está firmado por una autoridad reconocida. Esto es normal y esperado en un certificado autofirmado utilizado en desarrollo.

> En un servidor con nombre de dominio público, lo habitual es sustituir este certificado por uno emitido gratuitamente mediante **Let's Encrypt** y la herramienta `certbot`, que además renueva los certificados automáticamente.

---

## 2.11 Plataformas integradas de desarrollo

Hasta ahora hemos instalado cada componente del stack de forma manual e independiente. Existen alternativas que integran todos los componentes en un único paquete o configuración, pensadas para agilizar el desarrollo y las pruebas.

### XAMPP

**XAMPP** es una de las plataformas integradas más conocidas. Incluye Apache, PHP, MariaDB y otras herramientas (como phpMyAdmin) preconfiguradas y listas para funcionar, disponible para Windows, Linux y macOS.

Resulta especialmente útil para:

- Entornos de desarrollo local.
- Aprendizaje y pruebas rápidas.
- Equipos donde no se desea configurar cada componente manualmente.

Su principal inconveniente es que su configuración suele diferir bastante de un servidor de producción real basado en Linux.

### Docker Compose

Una alternativa más cercana a los entornos profesionales actuales consiste en definir el stack completo mediante **contenedores Docker**, ya presentados en el Bloque 1.

Un archivo `docker-compose.yml` puede definir los tres servicios del stack LAMP:

```yaml
version: "3.8"

services:
  apache:
    image: php:8.2-apache
    ports:
      - "8080:80"
    volumes:
      - ./www:/var/www/html
    depends_on:
      - mariadb

  mariadb:
    image: mariadb:10.11
    environment:
      MYSQL_ROOT_PASSWORD: rootpass
      MYSQL_DATABASE: tienda
      MYSQL_USER: appweb
      MYSQL_PASSWORD: contraseña_segura
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
```

Levantar el entorno completo:

```bash
docker compose up -d
```

Comprobar los contenedores en ejecución:

```bash
docker compose ps
```

Este enfoque permite reproducir el mismo entorno en cualquier máquina con Docker instalado, y es habitual en flujos de trabajo profesionales de integración continua y despliegue.

### Comparativa

|Aspecto|Instalación manual|XAMPP|Docker Compose|
|---|---|---|---|
|Similitud con producción|Alta|Baja|Alta|
|Facilidad de instalación|Baja|Alta|Media|
|Aislamiento entre proyectos|Bajo|Bajo|Alto|
|Reproducibilidad|Baja|Media|Alta|
|Uso habitual en ASIR|Aprendizaje inicial|Pruebas rápidas|Desarrollo profesional|

---

### Ideas clave

Al finalizar este apartado debes ser capaz de:

- Activar `mod_ssl` y generar un certificado autofirmado para Apache.
- Configurar un sitio HTTPS y comprobar su funcionamiento.
- Explicar la diferencia entre un certificado autofirmado y uno emitido por una autoridad de certificación (por ejemplo, Let's Encrypt).
- Explicar qué es una plataforma integrada de desarrollo y poner ejemplos (XAMPP, Docker Compose).
- Valorar las ventajas e inconvenientes de cada enfoque para preparar un entorno de desarrollo o pruebas.

---

## 2.12 Virtual Hosts: varios sitios en un mismo servidor

En el apartado 2.6 vimos que Apache organiza los sitios web mediante `sites-available` y `sites-enabled`, y que el sitio por defecto (`000-default.conf`) responde cuando no existe una configuración más específica.

Sin embargo, un mismo servidor Apache puede alojar **varios sitios web independientes**, cada uno con su propio dominio y su propio `DocumentRoot`. Esta funcionalidad se conoce como **Virtual Hosts** (hosts virtuales).

```text
Apache (una sola instalación)
├── miweb1.local   →  /var/www/miweb1
└── miweb2.local   →  /var/www/miweb2
```

Esto permite, por ejemplo, que un mismo servidor aloje varias aplicaciones o varios proyectos de prácticas sin necesidad de instalar Apache varias veces.

---

### Tipos de Virtual Hosts

Apache admite dos formas principales de distinguir entre sitios:

**Basados en IP**

Cada sitio se asocia a una dirección IP diferente del servidor.

Requiere disponer de varias IP configuradas en la máquina, por lo que es menos habitual en entornos de prácticas.

**Basados en nombre (name-based)**

Todos los sitios comparten la misma dirección IP y el mismo puerto. Apache distingue entre ellos utilizando la cabecera `Host` que envía el navegador en cada petición HTTP.

Es el mecanismo más utilizado actualmente y el que emplearemos en este apartado.

```text
Navegador
   │
   │ Host: miweb1.local
   ▼
Apache (misma IP, puerto 80)
   │
   ├── ¿Host = miweb1.local?  →  /var/www/miweb1
   └── ¿Host = miweb2.local?  →  /var/www/miweb2
```

---

### Preparar los directorios de cada sitio

Creamos un directorio independiente para cada sitio web:

```bash
sudo mkdir -p /var/www/miweb1/public_html
sudo mkdir -p /var/www/miweb2/public_html
```

Creamos una página de prueba en cada uno, para poder diferenciarlos visualmente:

```bash
echo "<h1>Sitio 1: miweb1.local</h1>" | sudo tee /var/www/miweb1/public_html/index.html
echo "<h1>Sitio 2: miweb2.local</h1>" | sudo tee /var/www/miweb2/public_html/index.html
```

Asignamos permisos adecuados:

```bash
sudo chown -R $USER:$USER /var/www/miweb1/public_html
sudo chown -R $USER:$USER /var/www/miweb2/public_html
sudo chmod -R 755 /var/www/miweb1
sudo chmod -R 755 /var/www/miweb2
```

---

### Crear los archivos de configuración

Cada Virtual Host se define en su propio archivo dentro de `sites-available`.

**Sitio 1**

```bash
sudo nano /etc/apache2/sites-available/miweb1.conf
```

```apache
<VirtualHost *:80>
    ServerName miweb1.local
    ServerAdmin admin@miweb1.local
    DocumentRoot /var/www/miweb1/public_html

    ErrorLog ${APACHE_LOG_DIR}/miweb1_error.log
    CustomLog ${APACHE_LOG_DIR}/miweb1_access.log combined
</VirtualHost>
```

**Sitio 2**

```bash
sudo nano /etc/apache2/sites-available/miweb2.conf
```

```apache
<VirtualHost *:80>
    ServerName miweb2.local
    ServerAdmin admin@miweb2.local
    DocumentRoot /var/www/miweb2/public_html

    ErrorLog ${APACHE_LOG_DIR}/miweb2_error.log
    CustomLog ${APACHE_LOG_DIR}/miweb2_access.log combined
</VirtualHost>
```

---

### Explicación de las directivas

**ServerName**

Indica el dominio que identifica a este Virtual Host. Es la directiva clave: Apache la compara con la cabecera `Host` de cada petición para decidir qué sitio debe responder.

**DocumentRoot**

Directorio raíz desde el que se publican los recursos de ese sitio concreto (ya estudiado en el apartado 2.6).

**ErrorLog y CustomLog**

Permiten que cada sitio tenga sus propios registros de errores y accesos, en lugar de compartir los registros globales de Apache. Esto facilita mucho el diagnóstico cuando se administran varios sitios a la vez.

---

### Activar los sitios

Utilizamos la herramienta ya conocida `a2ensite`:

```bash
sudo a2ensite miweb1.conf
sudo a2ensite miweb2.conf
```

Es recomendable desactivar el sitio por defecto para evitar confusiones durante las pruebas:

```bash
sudo a2dissite 000-default.conf
```

Validamos la configuración y aplicamos los cambios:

```bash
sudo apache2ctl configtest
sudo systemctl reload apache2
```

---

### Resolución de nombres local

Como `miweb1.local` y `miweb2.local` no son dominios reales registrados en Internet, necesitamos indicarle a nuestro propio equipo cómo resolverlos. Esto se hace editando el fichero `hosts`:

```bash
sudo nano /etc/hosts
```

Añadimos las siguientes líneas (sustituyendo la IP si accedemos desde otro equipo de la red):

```text
127.0.0.1   miweb1.local
127.0.0.1   miweb2.local
```

> Este mecanismo recuerda directamente al funcionamiento de DNS estudiado en el Bloque 1: aquí simulamos "a mano", en un único equipo, lo que un servidor DNS real haría para toda una red.

---

### Comprobación

Accedemos desde el navegador a:

```text
http://miweb1.local
http://miweb2.local
```

Cada dirección debería mostrar la página correspondiente a su propio `DocumentRoot`, confirmando que Apache está distinguiendo correctamente ambos sitios a partir del nombre.

También podemos comprobarlo desde la terminal indicando la cabecera `Host` manualmente:

```bash
curl -H "Host: miweb1.local" http://localhost
curl -H "Host: miweb2.local" http://localhost
```

---

### Comprobación de los registros independientes

```bash
sudo tail /var/log/apache2/miweb1_access.log
sudo tail /var/log/apache2/miweb2_access.log
```

Cada fichero debe reflejar únicamente las peticiones realizadas al sitio correspondiente.

---

### Buenas prácticas

- Utilizar siempre `ServerName` explícito en cada Virtual Host, para evitar advertencias de Apache al arrancar.
- Mantener un archivo de configuración independiente por sitio dentro de `sites-available`.
- Usar registros (`ErrorLog`/`CustomLog`) separados por sitio en entornos con varias aplicaciones.
- Desactivar el sitio por defecto cuando ya no sea necesario.
- Documentar en `/etc/hosts` (o en el DNS real, en producción) los nombres utilizados por cada Virtual Host.

---

### Ideas clave

Al finalizar este apartado debes ser capaz de:

- Explicar qué es un Virtual Host y diferenciar los basados en IP de los basados en nombre.
- Crear y activar varios Virtual Hosts basados en nombre en un mismo servidor Apache.
- Configurar `DocumentRoot`, `ServerName` y registros independientes para cada sitio.
- Utilizar el fichero `/etc/hosts` para resolver nombres de dominio locales de prueba.
- Comprobar mediante navegador y `curl` que cada Virtual Host responde correctamente.

## 2.13 Cortafuegos: apertura de puertos con ufw

Instalar y configurar Apache no es suficiente para garantizar que el servidor sea accesible: también es necesario que el **cortafuegos** del sistema permita el tráfico correspondiente.

En sistemas Debian y Ubuntu, la herramienta más habitual para gestionar el cortafuegos de forma sencilla es **ufw** (_Uncomplicated Firewall_), una interfaz simplificada sobre `iptables`.

---

### Comprobar el estado del cortafuegos

```bash
sudo ufw status
```

Resultado habitual si aún no se ha activado:

```text
Status: inactive
```

O bien, si ya está activo:

```text
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
```

---

### Perfiles de aplicación registrados por Apache

Cuando se instala Apache, el propio paquete registra automáticamente varios **perfiles de aplicación** que ufw puede utilizar, evitando tener que recordar números de puerto concretos.

```bash
sudo ufw app list
```

Salida habitual:

```text
Available applications:
  Apache
  Apache Full
  Apache Secure
  OpenSSH
```

|Perfil|Puertos que abre|
|---|---|
|Apache|80 (HTTP)|
|Apache Secure|443 (HTTPS)|
|Apache Full|80 y 443 (HTTP y HTTPS)|

Podemos consultar el detalle de un perfil concreto:

```bash
sudo ufw app info "Apache Full"
```

---

### Permitir el tráfico web

Lo habitual, una vez configurado HTTPS (apartado 2.10), es permitir ambos puertos a la vez:

```bash
sudo ufw allow "Apache Full"
```

Si únicamente se está trabajando con HTTP (por ejemplo, en las primeras prácticas antes de configurar el certificado):

```bash
sudo ufw allow "Apache"
```

También es posible indicar los puertos directamente, sin depender del perfil registrado:

```bash
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
```

---

### No perder el acceso por SSH

Antes de activar ufw en un servidor al que se accede en remoto, es imprescindible permitir también el tráfico SSH. De lo contrario, se perdería el acceso al propio servidor en el momento de activar el cortafuegos.

```bash
sudo ufw allow OpenSSH
```

> Este paso se olvida con frecuencia y es una de las causas más habituales de "bloqueo" accidental de un servidor en prácticas. Conviene comprobar siempre las reglas activas antes de activar ufw.

---

### Activar el cortafuegos

Una vez añadidas las reglas necesarias:

```bash
sudo ufw enable
```

El sistema pedirá confirmación, ya que puede interrumpir conexiones activas:

```text
Command may disrupt existing ssh connections. Proceed with operation (y|n)?
```

---

### Comprobar las reglas activas

```bash
sudo ufw status verbose
```

Ejemplo de salida:

```text
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere
Apache Full                ALLOW       Anywhere
```

---

### Eliminar una regla

```bash
sudo ufw delete allow "Apache"
```

### Desactivar el cortafuegos

```bash
sudo ufw disable
```

---

### Diagnóstico: ¿el problema es Apache o el cortafuegos?

Cuando un sitio web no es accesible desde otro equipo de la red, conviene aislar si el problema está en Apache o en el cortafuegos.

```text
¿Responde en localhost?
   │
   ├── No  →  Problema en Apache (ver apartado 2.5)
   │
   └── Sí  →  ¿Responde desde otro equipo?
                  │
                  ├── No  →  Revisar ufw / cortafuegos de red
                  └── Sí  →  Correcto
```

Comandos útiles para esta comprobación:

```bash
curl http://localhost
sudo ufw status
sudo ss -tulpn | grep -E ':80|:443'
```

---

### Buenas prácticas

- Permitir siempre el acceso SSH antes de activar ufw en un servidor remoto.
- Utilizar los perfiles de aplicación (`Apache`, `Apache Full`) en lugar de recordar números de puerto.
- Revisar periódicamente las reglas activas con `ufw status verbose`.
- Cerrar los puertos que ya no sean necesarios.
- Documentar qué reglas se han añadido y por qué, como parte de la documentación del servidor.

---

### Ideas clave

Al finalizar este apartado debes ser capaz de:

- Explicar la función de un cortafuegos en la seguridad de un servidor web.
- Consultar el estado y las reglas activas de ufw.
- Permitir el tráfico HTTP y HTTPS mediante los perfiles de aplicación de Apache.
- Evitar la pérdida de acceso remoto al activar ufw, permitiendo antes el tráfico SSH.
- Diagnosticar si un problema de acceso se debe a Apache o al cortafuegos.

## 2.14 Documentación de las prácticas realizadas

El último criterio de evaluación del RA1 exige explícitamente que **se documenten los procedimientos realizados**. No basta con que un servidor funcione: en un entorno profesional, cualquier configuración debe quedar registrada para que pueda mantenerse, auditarse o reproducirse por otra persona (o por uno mismo, meses después).

---

### ¿Por qué documentar?

- Permite reproducir la configuración en otro servidor.
- Facilita el diagnóstico de problemas futuros.
- Es imprescindible para el trabajo en equipo.
- Suele ser un requisito explícito en la evaluación de las prácticas.
- Es una competencia profesional en sí misma, no solo un "extra".

---

### Qué debe incluir una buena documentación técnica

Como mínimo, cada práctica debería recoger:

1. **Objetivo**: qué se quería conseguir.
2. **Entorno de partida**: sistema operativo, versión, IP o nombre del equipo.
3. **Pasos realizados**: comandos ejecutados, en orden, con una breve explicación de cada uno.
4. **Configuración aplicada**: fragmentos relevantes de los ficheros modificados.
5. **Comprobaciones realizadas**: cómo se ha verificado que todo funciona.
6. **Problemas encontrados y solución**: cualquier incidencia relevante durante el proceso.

---

### Plantilla básica

A continuación se propone una plantilla sencilla, en formato Markdown, que puede reutilizarse en cada práctica de este módulo:

````markdown
# Práctica: [título de la práctica]

## Objetivo
[Qué se quiere conseguir con esta práctica]

## Entorno
- Sistema operativo:
- Dirección IP / nombre del equipo:
- Software instalado previamente:

## Procedimiento

### 1. [Primer paso]
Comando(s) ejecutado(s):
```bash
comando --opcion
```
Explicación breve de qué hace y por qué es necesario.

### 2. [Segundo paso]
...

## Configuración aplicada
Fragmento del fichero modificado (indicando la ruta):

```apache
# /etc/apache2/sites-available/ejemplo.conf
...
```

## Comprobación
Cómo se ha verificado que la práctica funciona correctamente
(capturas, salida de comandos, código de estado HTTP, etc.).

## Incidencias
Problemas encontrados durante la práctica y cómo se resolvieron.

## Conclusiones
Qué se ha aprendido o qué se haría de forma diferente.
````

---

### Ejemplo aplicado (resumido)

````markdown
# Práctica: Instalación y aseguramiento de Apache

## Objetivo
Instalar Apache HTTP Server en Debian, comprobar su funcionamiento
y proteger el acceso al puerto mediante ufw.

## Entorno
- Sistema operativo: Debian 12
- Dirección IP: 192.168.1.100

## Procedimiento

### 1. Instalación del servidor web
```bash
sudo apt update
sudo apt install apache2
```
Instala Apache junto con sus dependencias básicas.

### 2. Comprobación del servicio
```bash
sudo systemctl status apache2
```
Resultado: Active (running).

### 3. Apertura del cortafuegos
```bash
sudo ufw allow OpenSSH
sudo ufw allow "Apache Full"
sudo ufw enable
```

## Comprobación
Acceso desde navegador a http://192.168.1.100 → se muestra
la página de bienvenida de Apache.

## Incidencias
Ninguna.

## Conclusiones
La instalación de Apache es sencilla, pero es fundamental no
olvidar la configuración del cortafuegos para no dejar el
servidor inaccesible ni innecesariamente expuesto.
````

---

### Herramientas útiles para documentar

- **Markdown**: formato ligero, legible tanto en texto plano como renderizado; es el recomendado para este módulo.
- **Capturas de pantalla**: útiles para mostrar resultados visuales (páginas web, mensajes de error).
- **Control de versiones (Git)**: permite llevar un historial de cambios en la propia documentación y en los ficheros de configuración.
- **Diagramas simples**: como los utilizados a lo largo de estos apuntes, ayudan a explicar arquitecturas y flujos.

> No es necesario redactar un documento extenso para cada comando: la clave es que cualquier persona (incluido uno mismo, tiempo después) pueda reproducir el proceso siguiendo la documentación.

---

### Buenas prácticas

- Documentar a la vez que se trabaja, no al final de memoria.
- Incluir siempre los comandos exactos utilizados, no una descripción vaga.
- Explicar el _porqué_ de cada decisión de configuración, no solo el _qué_.
- Guardar la documentación junto con el resto del material de la práctica.
- Mantener un formato consistente entre todas las prácticas del módulo.

---

### Ideas clave

Al finalizar este apartado debes ser capaz de:

- Explicar por qué documentar los procedimientos es un criterio de evaluación explícito del RA1.
- Identificar los elementos mínimos que debe incluir una documentación técnica.
- Aplicar una plantilla estructurada para documentar una práctica de instalación o configuración.
- Utilizar Markdown como herramienta de documentación técnica en este módulo.