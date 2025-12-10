# Roles y Capacidades en WordPress

WordPress gestiona los permisos de los usuarios mediante un sistema de **roles y capacidades**. Esto permite controlar lo que cada usuario puede o no puede hacer dentro del sitio.

---

## 1. ¿Qué son los Roles en WordPress?

Un **rol** es un conjunto de **capacidades** asignadas a un usuario. WordPress trae seis roles predeterminados:

|Rol|Alcance|Caso de uso típico|
|:--|:--|:--|
|**Super Administrador** (solo Multisitio)|Control total sobre **toda la red** de sitios|Redes corporativas o campus universitarios|
|**Administrador**|Control total sobre **un solo sitio**|Webmasters, desarrolladores|
|**Editor**|Publica/edita **todo el contenido**|Jefes de contenido|
|**Autor**|Publica/edita **sus propias entradas**|Blogueros invitados|
|**Colaborador**|Escribe, pero **no publica**|Redactores externos|
|**Suscriptor**|Solo lee y gestiona su perfil|Usuarios de membresía básica|

---

## 2. ¿Qué son las Capacidades?

Las **capacidades** (capabilities) son permisos granulares. Ejemplos:

- `edit_posts` – editar entradas propias
- `edit_others_posts` – editar entradas ajenas
- `publish_posts` – publicar entradas
- `manage_options` – acceder a **Ajustes**
- `install_plugins` – instalar plugins (solo Admin)
- `delete_site` – eliminar el sitio (Multisitio)

Se pueden añadir/quitar con **código**, **WP-CLI** o plugins.

---

## 3. Cómo Gestionar Roles y Capacidades

### 3.1 Desde el Escritorio

1. **Usuarios > Todos los usuarios**
2. Editar usuario → desplegable **Rol** → Guardar.

### 3.2 Con WP-CLI

```bash
# Listar roles
wp role list

# Añadir capacidad
wp cap add editor delete_users

# Quitar capacidad
wp cap remove editor delete_users

# Crear rol personalizado
wp role create redactor_redes "Redactor RRSS" --clone=author
```

### 3.3 Plugins recomendados (2025)

- **User Role Editor** – interfaz gráfica, export/import de roles.
- **Members** – control de acceso por contenido, shortcodes `[members_only]`.
- **PublishPress Capabilities** – auditoría de permisos y copias de seguridad de roles.
    

---

## 4. Mejores Prácticas

1. **Principio de mínimo privilegio**  
    Nunca des `administrator` si solo necesita `editor`.
2. **Roles por funciones, no por personas**  
    Crea roles como “SEO Manager” o “Soporte” en lugar de “Juan” o “Ana”.
3. **Auditoría trimestral**  
    Revisa con **PublishPress Capabilities** o **WP Activity Log** quién tiene qué.
4. **Seguridad extra**
    - Desactiva el editor de archivos (`define('DISALLOW_FILE_EDIT', true);`).
    - Usa **Two-Factor** para administradores.
5. **Multisitio**
    - Solo **Super Admin** puede instalar plugins/temas en toda la red.
    - Cada sitio puede tener sus propios administradores limitados.