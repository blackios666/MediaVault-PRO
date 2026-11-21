# Guía para publicar MediaVault PRO en GitHub

## 1. Crear el repositorio

1. Entra en https://github.com/new
2. Nombre: `MediaVault-PRO`
3. Visibilidad: **Public** para que las descargas sean accesibles a visitantes sin cuenta.
4. Descripción sugerida: `Descargas oficiales de MediaVault PRO para iPhone | BLACK IOS · Música, biblioteca multimedia y ecualizador.`
5. **No incluyas tu proyecto Theos, `vendor/`, claves de firma ni archivos secretos.** Este paquete es suficiente para crear una página de descargas.

## 2. Personalizar antes de subir

Sustituye `USUARIO_GITHUB` por tu nombre real de usuario de GitHub en:

- `README.md`
- `docs/config.js`

(En `docs/config.js` sustituye únicamente el valor de `githubUser`.)

El enlace de descarga cambia automáticamente cuando publiques una nueva Release con el mismo nombre de IPA.

## 3. Subir al repositorio

Sube los archivos y carpetas de este paquete (sin subir el ZIP contenedor). Si usas la web de GitHub: Add file → Upload files → Commit changes.

**No incluyas una IPA en el commit inicial**: GitHub ofrece una sección especializada para los archivos de versiones.

## 4. Crear la descarga

1. En tu repositorio abre **Releases → Draft a new release**.
2. Tag: `v2.4.0` (usa la versión real de tu IPA).
3. Título: `MediaVault PRO v2.4.0`.
4. Pega el contenido de `RELEASE_NOTES_v2.4.0.md`.
5. En *Attach binaries*, sube el archivo **`MediaVault-PRO.ipa`**.
6. Opcional: genera `SHA256SUMS.txt` con `python scripts/generar_sha256.py MediaVault-PRO.ipa` y súbelo también.
7. Publica la Release como estable solamente cuando la hayas probado.

## 5. Enlace para Blogger

En la plantilla Blogger coloca:

```javascript
var MV_IPA_URL = 'https://github.com/USUARIO_GITHUB/MediaVault-PRO/releases/latest/download/MediaVault-PRO.ipa';
```

Reemplaza `USUARIO_GITHUB`. Este enlace funciona **solo después** de publicar una Release estable con un recurso que se llame exactamente `MediaVault-PRO.ipa`.

## 6. Publicar la web opcional en GitHub Pages

En el repositorio: **Settings → Pages → Build and deployment → Deploy from a branch**. Elige `main` y carpeta `/docs`. Cuando se publique, estará disponible en una URL similar a:

`https://USUARIO_GITHUB.github.io/MediaVault-PRO/`

Es una landing independiente. Si ya utilizas Blogger, puedes mantener Blogger como página principal y usar únicamente Releases para alojar la IPA.

## 7. Próximas versiones

Publica cada versión con un **tag nuevo** y adjunta siempre el archivo llamado exactamente `MediaVault-PRO.ipa` si quieres mantener estable el enlace de Blogger.

## Seguridad

- Nunca compartas certificados, perfiles de firma privados, cuentas, claves de API, cookies o tokens.
- No publiques el código del proyecto si deseas mantenerlo privado.
- No confundas el ZIP de «Source code» que GitHub genera automáticamente con la IPA adjunta.
- Publica un hash SHA-256 para que las personas comparen el archivo descargado.
