### Planificación RA1 (Bloques de 2 Horas)

#### Módulo A: El Cliente y la Red (Sesiones 1-2)
*   **Sesión 1: ¿Cómo funciona la Web?**
    *   **Teoría (45 min):** Bloque 1. Arquitectura Cliente-Servidor, Recursos estáticos/dinámicos y DNS.
    *   **Práctica (1h 15 min):** Análisis de peticiones con F12 (Network), uso de `nslookup`/`dig` y comprobación de IPs.
*   **Sesión 2: Protocolos y Seguridad básica**
    *   **Teoría (45 min):** Bloque 1. Protocolo HTTP/HTTPS, métodos (GET/POST) y códigos de estado.
    *   **Práctica (1h 15 min):** Simulación de peticiones, análisis de cabeceras y diferencia visual entre HTTP y HTTPS.

#### Módulo B: El Servidor Web (Sesiones 3-5)
*   **Sesión 3: Instalación y Gestión de Apache**
    *   **Teoría (45 min):** Bloque 2. Instalación de Apache, `systemctl` y el `DocumentRoot`.
    *   **Práctica (1h 15 min):** Instalación de Apache, despliegue de la primera página HTML y gestión del servicio.
*   **Sesión 4: Modularidad y Virtual Hosts**
    *   **Teoría (45 min):** Bloque 2. Arquitectura modular (`a2enmod`) y concepto de Virtual Hosts.
    *   **Práctica (1h 15 min):** Activación de módulos y configuración de dos sitios web independientes en el mismo servidor.
*   **Sesión 5: Acceso, Seguridad y Directorios Personales**
    *   **Teoría (45 min):** Bloque 2. `mod_userdir`, autenticación básica (`htpasswd`) y cortafuegos (`ufw`).
    *   **Práctica (1h 15 min):** Configuración de espacios personales, restricción de acceso por contraseña y apertura de puertos en el firewall.

#### Módulo C: El Backend y los Datos (Sesiones 6-8)
*   **Sesión 6: PHP y el Motor de Aplicación**
    *   **Teoría (45 min):** Bloque 3. Instalación de PHP, flujo de procesamiento y `phpinfo()`.
    *   **Práctica (1h 15 min):** Instalación de PHP, creación de scripts dinámicos básicos y verificación de extensiones.
*   **Sesión 7: MariaDB y Gestión de Datos**
    *   **Teoría (45 min):** Bloque 3. Instalación de MariaDB, `mysql_secure_installation` y CRUD básico.
    *   **Práctica (1h 15 min):** Instalación de la BD, asegurado del root, creación de BD y **usuario específico** con privilegios. Instalación de phpMyAdmin.
*   **Sesión 8: Integración Final y Troubleshooting**
    *   **Teoría (30 min):** Bloque 3. Conexión PHP $\rightarrow$ MariaDB y Sentencias Preparadas.
    *   **Práctica (1h 30 min):** Desarrollo del script de integración final (Mostrar datos de la BD en la web). Taller de resolución de errores usando `error.log`.
