# Gestión de Menús en WordPress

Los menús siguen siendo la columna vertebral de la navegación, pero desde la llegada del **Full Site Editing (FSE)** hay dos formas de trabajarlos: la clásica (temas tradicionales) y la moderna (temas FSE). .

---

## 1. Acceder a la Configuración de Menús

|Tipo de tema|Ruta|
|:--|:--|
|**Clásico**|**Apariencia > Menús**|
|**FSE**|**Apariencia > Editor del Sitio > Navegación** (o directamente el bloque _Navigation_)|

---

## 2. Añadir Elementos al Menú

### 2.1 Temas Clásicos

1. En **Apariencia > Menús**, marca las casillas de:
    - **Páginas**
    - **Entradas**
    - **Categorías**
    - **Enlaces personalizados** (URL + texto)
        
2. Pulsa **“Añadir al menú”**.

![[Pasted image 20251210231318.png]]
### 2.2 Temas FSE

1. Inserta el bloque **“Navigation”** (o edita el existente).
2. Dentro del bloque, haz clic en **“+”** y elige:
    - Páginas
    - Entradas
    - Categorías
    - Enlaces personalizados (icono de enlace)
3. Reordena arrastrando los elementos.

![[Pasted image 20251210231347.png]]
---

## 3. Organizar los Elementos

|Acción|Clásico|FSE|
|:--|:--|:--|
|Reordenar|Arrastrar y soltar|Arrastrar y soltar|
|Submenú|Sangrar a la derecha|Sangrar a la derecha (o usar el bloque _Submenu_)|
|Guardar|“Guardar menú”|Guarda la plantilla (Ctrl + S)|

---

## 4. Asignar el Menú a una Ubicación

### 4.1 Temas Clásicos

1. En **“Configuración del menú > Ubicaciones del tema”**:
    - Marca la casilla correspondiente (p. ej. “Menú Principal”).
2. Guarda.

![[Pasted image 20251210231415.png]]
### 4.2 Temas FSE

- No hay “ubicaciones” predefinidas; el menú es un bloque que insertas donde necesites:
    - **Header** (cabecera)
    - **Footer** (pie)
    - **Sidebar** (barra lateral)
        
- Puedes tener **varios bloques Navigation** (p. ej. uno para móvil, otro para desktop).
    

---

## 5. Personalización Avanzada

| Función                    | Clásico                                     | FSE                                                                    |
| :------------------------- | :------------------------------------------ | :--------------------------------------------------------------------- |
| **Abrir en nueva pestaña** | Opciones de pantalla → “Destino del enlace” | Panel lateral del bloque → “Abrir en nueva pestaña”                    |
| **Descripción**            | Opciones de pantalla → “Descripción”        | No disponible (usa bloques de texto adicionales si el tema lo permite) |
| **Clases CSS**             | Opciones de pantalla → “Clases CSS”         | Panel lateral → “Avanzado > Clases CSS”                                |
| **Iconos**                 | Plugins (p. ej. _Menu Icons_)               | Bloques de iconos dentro del _Navigation_                              |

---

## 6. Edición en Tiempo Real

### 6.1 Personalizador (temas clásicos)

- **Apariencia > Personalizar > Menús** → vista previva en vivo.


### 6.2 Editor del Sitio (FSE)

- **Apariencia > Editor del Sitio** → selecciona la plantilla _Header_ o _Footer_.
- Edita el bloque _Navigation_ y ve los cambios al instante.

---

## 7. Mejores Prácticas

- **Menú móvil “hamburguesa”**:
    - Temas FSE: el bloque _Navigation_ incluye el toggle automático en móvil.
    - Temas clásicos: revisa que el tema sea _responsive_ o usa un plugin como _WP Responsive Menu_.

- **Accesibilidad**:
    - Añade `aria-label` a los enlaces (en FSE: campo “Etiqueta ARIA” en el panel del bloque).
    - Asegúrate de que el menú sea navegable con teclado (Tab, Enter, Escape).
- **SEO**:
    - Usa textos descriptivos (“Contacto” mejor que “Más”).
    - Evita menús excesivamente largos (> 7 elementos principales).
- **Rendimiento**:
    - Limita el número de elementos en el menú principal.
    - Usa **menús condicionales** (p. ej. con _Conditional Menus_) para mostrar opciones distintas según el rol del usuario.
- **Multilingüe**:
    - Con Polylang o WPML, crea un menú por idioma y asígnalo a la misma ubicación (temas clásicos) o duplica el bloque _Navigation_ (FSE).