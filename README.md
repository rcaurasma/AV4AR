# MVP WebAR (gratis) con Video + Formulario (Google Forms)

Este proyecto usa **A-Frame + AR.js** (gratuitos) para una experiencia rápida:
- Escanean un **QR** -> abre esta página.
- Aparece un **escenario AR** con un botón "Ver video".
- Tras el video, se muestra un **formulario de Google** embebido.

## Pasos rápidos

1) Reemplaza el formulario de Google
- Crea tu Google Form.
- Clic en "Enviar" -> icono `</>` (Insertar HTML).
- Copia el `src` del `iframe` (algo como `https://docs.google.com/forms/d/e/ID/viewform?embedded=true`).
- Abre `index.html` y reemplaza:
  - `REEMPLAZA_CON_URL_EMBED_DE_TU_GOOGLE_FORM`
- Opcional: el botón "Abrir en nueva pestaña" usará automáticamente el enlace no embebido.

2) Subir a GitHub Pages (gratis)
- Crea un repo nuevo (por ejemplo `webar-stand-mvp`).
- Sube `index.html` (y este `README.md` si quieres).
- En GitHub: Settings -> Pages -> Branch `main` -> `/ (root)` -> Save.
- Espera 1–2 minutos. Tendrás una URL como:
  - `https://tu-usuario.github.io/webar-stand-mvp/`

3) Genera el código QR
- Usa un generador como [QRCode Monkey](https://www.qrcode-monkey.com/).
- Pon la URL de GitHub Pages.
- Imprime el QR para el stand.

4) Imprime el **marcador HIRO** (necesario para AR.js marker-based)
- Descarga e imprime el marcador HIRO:
  - [HIRO marker (JPG)](https://raw.githubusercontent.com/AR-js-org/AR.js/master/three.js/data/images/HIRO.jpg)
- Coloca el marcador en la mesa. Indica a los visitantes que apunten con la cámara.

## Notas de compatibilidad

- Requiere HTTPS para acceso a la cámara (GitHub Pages ya es HTTPS).
- iOS y Android soportados en navegadores modernos (Safari/Chrome).
- El video **se reproduce tras un clic** (políticas de autoplay).
- Si el usuario no concede permisos de cámara, aparece **modo sin AR** con botones para ver video y llenar el formulario.

## Personalizaciones rápidas

- Reemplazar el efecto 3D:
  - En `index.html`, cambia la `<a-box>` por un modelo glTF cargado en `<a-assets>`:
    ```html
    <a-asset-item id="logoModel" src="ruta-a-tu-modelo.glb"></a-asset-item>
    ...
    <a-entity gltf-model="#logoModel" position="0 0 0" scale="0.5 0.5 0.5"></a-entity>
    ```
- Texto del botón en AR: edita el `<a-text value="Ver video">`.
- Colores: cambia `color="#FF5722"` del botón AR.

## Problemas comunes

- La cámara no se abre:
  - Asegúrate de que estás en HTTPS y diste **permiso de cámara**.
  - Prueba en otro navegador si el dispositivo es muy antiguo.
- El video no auto-reproduce:
  - Es normal; el **primer clic** del usuario lo habilita.
- El iframe del formulario no carga:
  - Verifica que el enlace sea el **embed** (`.../viewform?embedded=true`).
  - Si no, usa el botón "Abrir en nueva pestaña".

## Créditos
- [A-Frame](https://aframe.io/)
- [AR.js](https://ar-js-org.github.io/AR.js-Docs/)