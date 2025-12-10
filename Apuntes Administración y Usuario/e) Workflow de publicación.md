# Workflow de Publicación de Entradas en WordPress

WordPress ofrece un flujo de trabajo completo para crear, revisar y publicar entradas. Incluye opciones avanzadas como **programación automática**, **revisión de cambios** y **protección por contraseña** (tanto a nivel de entrada como de bloque).

---

## 1. Crear una Nueva Entrada

1. **Entradas > Añadir nueva**.
2. El **editor de bloques (Gutenberg)** se carga por defecto.

### Elementos clave del editor (2025)
- **Título H1** (obligatorio para SEO).
- **Bloques de contenido** (párrafos, imágenes, galerías, CTAs, etc.).
- **Barra lateral derecha**:
    - Estado y visibilidad.
    - **Imagen destacada** (obligatoria para redes sociales).
    - **Extracto** (resumen manual para listados).
    - **Opciones de discusión** (permitir / desactivar comentarios).

---

## 2. Opciones de Visibilidad

| Tipo                         | Descripción                                        | Caso de uso                                  |
| :--------------------------- | :------------------------------------------------- | :------------------------------------------- |
| **Pública**                  | Visible para todos.                                | Blog posts, noticias.                        |
| **Protegida con contraseña** | Requiere contraseña.                               | Contenido exclusivo para clientes.           |
| **Privada**                  | Solo administradores/editores.                     | Borradores internos.                         |
| **Bloque protegido**         | Contraseña por bloque (plugin “Block Visibility”). | Secciones VIP dentro de una entrada pública. |

---

## 3. Guardar, Revisar y Previsualizar

1. **Guardar borrador** (`Ctrl + S`).
2. **Revisión de cambios**:
    - Ve a **“Revisions”** (barra lateral > Documento) para comparar versiones.
3. **Vista previa**:
    - Haz clic en **“Vista previa”** (desktop, tablet, móvil).
    - Usa el plugin **“Broken Link Checker”** para detectar enlaces rotos antes de publicar.

---

## 4. Categorías, Etiquetas y Taxonomías Personalizadas

- **Categorías**: jerarquía (p. ej. “Tecnología > Móviles”).
- **Etiquetas**: palabras clave sin jerarquía.
- **Taxonomías personalizadas**: creadas con plugins como CPT UI o código.

---

## 5. Publicación o Programación

1. Haz clic en **“Publicar”** (o **“Programar”** si eliges fecha futura).
2. **Programación automática** (requiere wp-cron. Ver apartado en apuntes sistemas):
3. **Estado final**:
    - Publicado | Programado | Borrador | Pendiente de revisión.

---

## 6. Gestión de Entradas Publicadas

- **Entradas > Todas las entradas**:
    - **Edición rápida** (título, categorías, etiquetas, estado).
    - **Mover a la papelera** o **Restaurar**.

---

## 7. Proteger Páginas y Entradas con Contraseña
### 7.1 Entrada completa
1. En la barra lateral, **Visibilidad > Protegida con contraseña**.
2. Introduce la contraseña y publica.

### 7.2 Bloque específico
- Instala **“Block Visibility”** o **“Password Protected Blocks”**.
- Selecciona el bloque → **“Proteger con contraseña”** → introduce la clave.
- Útil para descargas exclusivas dentro de una entrada pública.
