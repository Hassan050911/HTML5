# Capítulo 8: Let’s Take This Offline

## ¿Qué es una aplicación web offline?

Una aplicación web offline parece algo contradictorio, ya que las páginas web necesitan conexión para descargarse. Sin embargo, **HTML5** permite descargar los recursos (HTML, CSS, JavaScript, imágenes, etc.) cuando estás conectado y usarlos sin conexión.

## ¿Cómo funciona?

Todo se basa en un **archivo manifest**, que es una lista de URLs con los recursos que el navegador debe guardar en caché.  

### El navegador:
1. Descarga los archivos indicados en el manifest.  
2. Los guarda localmente.  
3. Los actualiza cuando hay cambios.  
4. Usa las copias locales cuando no hay conexión.

## Responsabilidad del desarrollador

El navegador puede detectar si estás **online** u **offline**, y lanzar eventos cuando el estado cambia. Pero el manejo de los datos y su sincronización con el servidor depende del **desarrollador**. HTML5 solo brinda las herramientas para trabajar sin conexión; el resto lo hace el programador.

## Soporte en navegadores

| Navegador | Soporte |
|------------|----------|
| IE | ✗ |
| Firefox | ✓ |
| Safari | ✓ |
| Chrome | ✓ |
| Opera | ✗ |
| iPhone | ✓ |
| Android | — |

# The Cache Manifest

## ¿Qué es el cache manifest?

El **cache manifest** es un archivo que lista todos los recursos (HTML, CSS, JS, imágenes, etc.) que una aplicación web necesita para funcionar sin conexión. Se declara en el documento HTML con el atributo `manifest` dentro de la etiqueta `<html>`.

```html
<!DOCTYPE HTML>
<html manifest="/cache.manifest">
  <body>
    ...
  </body>
</html>
```
El archivo debe tener la extensión `.manifest` y el tipo de contenido `text/cache-manifest.`

## Estructura del archivo `manifest`

Cada archivo comienza con:
```
CACHE MANIFEST
```
Luego puede incluir tres secciones:

### 1. Sección CACHE

Contiene los recursos que se descargarán y estarán disponibles sin conexión.
Ejemplo:
```
CACHE MANIFEST
/clock.css
/clock.js
/clock-face.jpg
```
Estos archivos se guardan localmente y pueden usarse sin conexión.

### 2. Sección NETWORK

Define los recursos que no deben guardarse y siempre se cargarán desde internet.
Ejemplo:

```
CACHE MANIFEST
NETWORK:
  /tracking.cgi
CACHE:
  /clock.css
  /clock.js
  /clock-face.jpg
```
`/tracking.cgi` nunca se almacena, ya que su función es rastrear visitas.

### 3. Sección FALLBACK

Permite mostrar un archivo de reemplazo cuando un recurso no esté disponible.
Ejemplo:

```
CACHE MANIFEST
FALLBACK:
  / /offline.html
NETWORK:
  *
```
* FALLBACK define que si una página no está en caché, se mostrará /`offline.html.`
* El asterisco * indica que cualquier otro recurso puede descargarse si hay conexión.

## Ventajas

* Permite usar partes del sitio sin conexión.
* Evita errores cuando no hay red.
* Mejora la velocidad al cargar desde caché.
* Soporta aplicaciones “abiertas” que se expanden al navegar.

# The Flow of Events 

Hasta ahora se ha explicado cómo funcionan las aplicaciones web offline y el cache manifest, pero el proceso real involucra una serie de **eventos DOM** que el navegador ejecuta sobre el objeto `window.applicationCache`.  Estos eventos permiten al desarrollador saber en qué estado está la caché de la aplicación.

## Flujo de eventos principales

1. **checking**  
   - Ocurre cuando el navegador detecta el atributo `manifest` en la etiqueta `<html>`.  
   - Se dispara **siempre**, incluso si ya se visitó la página antes.

2. **downloading**  
   - Se ejecuta si el navegador nunca ha visto el manifest antes.  
   - Inicia la descarga de todos los archivos listados.  
   - Durante la descarga se lanzan varios eventos **progress**, indicando el avance.  
   - Cuando termina exitosamente, se dispara el evento **cached** → la app ya está lista para usarse offline.

3. **noupdate**  
   - Si ya se había visitado la página y el manifest **no ha cambiado**, el navegador lanza este evento.  
   - Indica que todo está actualizado y no se descargará nada nuevo.

4. **updateready**  
   - Si el manifest **ha cambiado**, el navegador vuelve a descargar **todos los recursos** listados.  
   - Después de actualizar todo correctamente, lanza este evento.  
   - La nueva versión queda lista, pero **no se activa automáticamente**.  
   - Para usarla sin recargar la página se llama:  
     ```js
     window.applicationCache.swapCache()
     ```

5. **error**  
   - Se dispara cuando ocurre algún problema durante el proceso.  
   - Posibles causas:
     - El archivo manifest devuelve error HTTP 404 o 410.  
     - La página HTML que apunta al manifest no se descargó bien.  
     - El manifest cambió mientras se actualizaba.  
     - Algún recurso listado no pudo descargarse correctamente.

       


