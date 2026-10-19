# Telmex 2026 - Carga Remota Autorizada (Sin Verificación GPS)

Portal web complementario para la carga y sincronización de evidencias fotográficas (cajas y casetas) de la campaña **Imagen Telmex 2026** sin el requisito de geolocalización o verificación GPS en sitio.

Diseñado específicamente para casos excepcionales donde un contratista solicita autorización previa a Mesa de Control para subir evidencias fuera de sitio (problemas de cobertura, autorizaciones especiales de liquidación o reportes extemporáneos).

---

## 🔐 Control de Acceso y Sistema Anti-Abuso

Para evitar que los contratistas abusen del enlace y suban fotos sin permiso, el portal cuenta con **dos capas de seguridad**:

### 1. Bloqueo por PIN Temporal (Para el Contratista)
* Al ingresar a la página web, el contratista encuentra una pantalla de bloqueo protegida.
* Requiere ingresar un **PIN de autorización temporal** (ej. `2026`).
* La autorización queda guardada en la sesión activa del navegador; al cerrar o expirar, vuelve a bloquearse automáticamente.
* Cada evidencia guardada registra el PIN utilizado y queda etiquetada en Linkaform con la leyenda:
  `[CARGA REMOTA AUTORIZADA - PIN: XXXX]`.

### 2. Panel de Mesa de Control / Administrador (Para Ti)
* Acceso directo desde el botón **`⚙️ Mesa de Control`** o el candado superior.
* Clave de Administrador por defecto: `pci2026` (o configurable en `auth_config.json`).
* **Interruptor Maestro:** Puedes cambiar el estado del portal a **Habilitado** o **Deshabilitado** con 1 clic. Si está deshabilitado, ningún contratista podrá ingresar.
* **Generador de PIN para WhatsApp:** Botón que genera un PIN aleatorio de 4 dígitos y copia el texto al portapapeles listo para enviarse por mensaje.
* **Edición Global vía GitHub:** Puedes editar el archivo [`auth_config.json`](auth_config.json) directamente en GitHub (desde el celular o PC) para cambiar el PIN activo o poner `"enabled": false` globalmente.

---

## 🛠️ Funcionamiento Técnico

1. **Sin Verificación de GPS:**
   * No solicita permisos obligatorios de geolocalización satelital.
   * La búsqueda se realiza directamente por **ID de elemento** (ej: `ZIH0061`, teléfono) o mediante filtros jerárquicos de **Estado** y **Área de Trabajo**.
   * Las coordenadas enviadas a Linkaform toman automáticamente las registradas en el catálogo oficial (`lat_original` y `lon_original`).
2. **Evidencias Fotográficas:**
   * Permite tanto **Tomar Foto con Cámara** como **📁 Subir desde Galería / Archivo** (ideal para fotos ya capturadas o enviadas por el técnico).
3. **Sincronización con Linkaform:**
   * Conectado a la forma pública `142786` (Cajas / Casetas Celaya).
   * Almacenamiento previo en Linkaform Cloud Storage (`api/infosync/cloud_upload/`) y creación de respuestas en `api/infosync/form_answer/`.
   * Funciona Offline-First: guarda el lote en almacenamiento local y permite el envío masivo en cuanto haya conexión.

---

## 🌐 Enlace Público de Producción

* **URL de GitHub Pages:** [https://pahernandez-sys.github.io/imagen-telmex-remoto/](https://pahernandez-sys.github.io/imagen-telmex-remoto/)
* **Repositorio:** [https://github.com/pahernandez-sys/imagen-telmex-remoto](https://github.com/pahernandez-sys/imagen-telmex-remoto)
