# Capítulo 5: Video en HTML5

## Antes de HTML5

Antes no había una forma directa de poner videos en una página web. Se usaban programas externos como Flash o QuickTime.  
Con HTML5 se agregó una manera estándar usando la etiqueta `<video>`.

---

## Compatibilidad con navegadores

| Navegador        | Soporte desde versión |
|------------------|------------------------|
| Chrome           | 3.0+                  |
| Firefox          | 3.5+                  |
| Safari           | 3.0+                  |
| Opera            | 10.5+                 |
| IE               | 9.0+                  |
| iPhone           | 1.0+                  |
| Android          | 2.0+                  |

---

## ¿Qué es un container de video?

Es lo que normalmente conocemos como el "formato" ( `.mp4`, `.webm`, `.ogv`).  
Dentro del archivo hay pistas de audio y video, y también puede haber datos extras como portada, idioma, título, etc.

---

## ¿Qué es un códec?

Un códec es como un traductor. Comprime y descomprime el audio o video.  
Hay dos tipos:
- **Con pérdida (lossy):** más ligero pero pierde calidad.
- **Sin pérdida (lossless):** calidad máxima pero pesa mucho.

### Códecs de video más comunes:

- **H.264:** Muy usado, compatible con casi todo.
- **Theora:** Libre de licencia.
- **VP8:** También libre y propiedad de Google.

### Códecs de audio:

- **MP3:** Clásico, hasta 2 canales.
- **AAC:** Más moderno, permite hasta 48 canales.
- **Vorbis:** Libre y común en WebM y Ogg.

---

## Compatibilidad en la web

No todos los navegadores soportan los mismos formatos, por eso lo mejor es subir 3 versiones del video:

- `.webm` con VP8 + Vorbis  
- `.mp4` con H.264 + AAC  
- `.ogv` con Theora + Vorbis

---

## Cómo usar `<video>` en HTML

### Opción rápida:

```html
<video src="mi_video.webm"></video>
```

