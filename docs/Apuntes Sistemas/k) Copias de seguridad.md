
# Copias de Seguridad en WordPress

Las copias de seguridad en WordPress son esenciales para proteger tu sitio web ante fallos, ataques o errores accidentales. Existen diferentes métodos para realizarlas, ya sea manualmente o mediante plugins especializados.

---

## 1. **Métodos de Copia de Seguridad**

### 1.1 Copia Manual

#### **Archivos del Sitio**
1. Accede al servidor vía SSH o FTP.
2. Copia todo el contenido del directorio donde está instalado WordPress:
   ```bash
   tar -czvf backup-wordpress.tar.gz /var/www/html
   ```
otra forma es mirar rsync:
```
rsync -avz --progress --link-dest=/ruta/destino_anterior/ /ruta/origen/ usuario@servidor:/ruta/destino/
```
3. Descarga este archivo a tu equipo local.

#### **Base de Datos**
1. Exporta la base de datos con el siguiente comando:
   ```bash
   mysqldump -u usuario -p database_name > backup-db.sql
   ```
2. Guarda el archivo `.sql` junto con la copia de los archivos.

---

### 1.2 Copia con WP-CLI

1. **Exportar Base de Datos**:
   ```bash
   wp db export backup-db.sql
   ```
2. **Copiar Archivos**:
   ```bash
   tar -czvf backup-wordpress.tar.gz .
   ```

---

### 1.3 Uso de Plugins

Los plugins facilitan la creación y programación de copias de seguridad automáticas.

#### **Plugins Populares**
1. **UpdraftPlus** (Gratuito y Premium)
   - Permite almacenar copias en la nube (Google Drive, Dropbox, Amazon S3, etc.).
   - Programación de backups automáticos.
   - Restauración con un clic.

2. **BackWPup** (Gratuito y Pro)
   - Soporte para bases de datos y archivos.
   - Envió de copias por correo electrónico o almacenamiento en la nube.

3. **VaultPress** (De Jetpack)
   - Solución premium con copias en tiempo real.
   - Monitorización y restauración automática.

---

## 2. **Restauración de Copias de Seguridad**

### 2.1 Restaurar Manualmente

1. **Subir Archivos**:
   - Si realizaste una copia manual, sube los archivos a `/var/www/html`.

2. **Restaurar Base de Datos**:
   ```bash
   mysql -u usuario -p database_name < backup-db.sql
   ```

### 2.2 Restaurar con WP-CLI

1. **Importar Base de Datos**:
   ```bash
   wp db import backup-db.sql
   ```
2. **Verificar el Sitio**:
   ```bash
   wp cache flush
   ```

---

## 3. **Mejores Prácticas para Copias de Seguridad**

1. **Programar Backups Automáticos**: Usa plugins o scripts cron para asegurar copias regulares.
2. **Almacenar en Ubicaciones Externas**: No guardes las copias en el mismo servidor del sitio.
3. **Probar las Restauraciones**: Asegúrate de que las copias de seguridad sean funcionales.
4. **Proteger las Copias**: Usa cifrado y almacenamiento seguro para evitar accesos no autorizados.

---


