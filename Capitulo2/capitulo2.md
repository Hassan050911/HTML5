#  Capitulo 2 Deteccion De caracteristicas HTML5

HTML5 no es una sola cosa, sino un **conjunto de características individuales** (como canvas, video o input types).  

* No tiene sentido preguntar si un navegador "soporta HTML5", porque no es algo unitario.  
* En cambio, se puede detectar el soporte para **cada función específica** por separado.  

## Explicación `<canvas>` en HTML5

### ¿Qué es?

* Un área para dibujar en páginas web usando JavaScript
* Como un lienzo digital donde puedes crear gráficos
* Usos comunes: juegos, gráficos estadísticos, animaciones

### ¿Cómo verificar compatibilidad?

```js
// Función para detectar soporte de canvas
function soportaCanvas() {
  return !!document.createElement('canvas').getContext;
}

if (soportaCanvas()) {
  console.log("Canvas está soportado");
} else {
  console.log("Canvas no está soportado");
}
```

###  Usos comunes

* **Interfaces dinámicas** 
Para crear dashboards y elementos UI interactivos.

* **Aplicaciones gráficas**  
Herramientas de diseño y edición online.

* **Visualización de datos**  
Gráficos complejos y actualizaciones en tiempo real.

* **Desarrollo de juegos**  
Ideal para juegos 2D en navegador, desde simples hasta complejos.

# Detección del API de Texto en Canvas (Canvas Text API)

## ¿Qué es?
El Canvas Text API permite dibujar texto dentro de un elemento `<canvas>`. Es importante saber que algunos navegadores pueden soportar canvas pero no esta funcionalidad específica.

## El problema
Si intentas usar funciones de texto sin verificar soporte:

```js
const ctx = canvas.getContext('2d');
ctx.fillText("Texto de prueba", 10, 10); 
```
# Elemento `<video>` en HTML5

## ¿Qué es el elemento `<video>`?
Es una etiqueta de HTML5 que permite mostrar videos directamente en una página web sin necesitar plugins como Flash.

### ¿Cómo se usa?

```html
<video controls width="400">
  <source src="mi-video.mp4" type="video/mp4">
</video>
```

# Formatos de Video en HTML5 

## ¿Que es?

Los formatos de video son como "idiomas" que los navegadores entienden. No todos los navegadores soportan los mismos formatos, por eso hay que verificar cuál funciona.

## Problema Principal

- **H.264 (MP4)**: Funciona en Safari/iPhone, pero tiene licencias de pago

- **Theora (Ogg)**: Gratis, funciona en Firefox y navegadores libres

- **WebM**: Nuevo formato libre, soportado por Chrome y Firefox

## Cómo Saber qué Formatos Soporta el Navegador

Se usa el método `canPlayType()`:

```js
// Crear elemento video (sin mostrarlo)
var video = document.createElement('video');

// Preguntar si soporta MP4
var soportaMP4 = video.canPlayType('video/mp4; codecs="avc1.42E01E"');

// Preguntar si soporta Ogg
var soportaOgg = video.canPlayType('video/ogg; codecs="theora"');
```

# Local Storage en HTML5 

## ¿Qué es?

Es como una memoria que tienen los navegadores para guardar información de tu página web. A diferencia de las cookies:

- Guarda más datos (hasta 10MB)

- La info NO se envía al servidor automáticamente

- Solo se accede con JavaScript

## ¿Cómo saber si funciona?

```js
// Forma simple de comprobar
if (typeof localStorage !== 'undefined') {
    console.log("Tu navegador soporta Local Storage");
} else {
    console.log("No soportado :(");
}
```
# Web Workers 

## ¿Que es?

Son como "ayudantes" que permiten ejecutar código JavaScript en segundo plano sin frenar tu página web.

### Para qué sirven:

* Hacer cálculos pesados

* Descargar datos

* Procesar información  

## ¿Cómo saber si el navegador los soporta?

### Método : Manual

```js
function supports_web_workers() {
  return !!window.Worker; 
}
```

### Método : Modernizr 
```js
if (Modernizr.webworkers) {
  // El navegador soporta Web Workers nativamente
  const worker = new Worker('worker-script.js');
} else {
  // No hay soporte nativo, considerar alternativas
}
```
# Geolocalizacion 

La geolocalización es el proceso tecnológico que permite identificar la posición exacta de un dispositivo o usuario en el mundo, con la opción de compartir esta información de forma controlada. Para determinar la ubicación, utiliza múltiples fuentes como la dirección IP para aproximación por red, las conexiones Wi-Fi cercanas para triangulación de señales, las torres de telefonía celular para posicionamiento móvil y los sistemas GPS que calculan coordenadas precisas mediante satélites.
# Input Types

## ¿Que es?
 
Los input types son los valores del atributo type en la etiqueta `<input>`, que definen el tipo de dato que el usuario puede ingresar.

## ¿Cuales son? 
1. `<input type="search">` → Para cuadros de búsqueda.  
2. `<input type="number">` → Para spinboxes (números).  
3. `<input type="range">` → Para sliders (deslizadores).  
4. `<input type="color">` → Para selectores de color.  
5. `<input type="tel">` → Para números de teléfono.  
6. `<input type="url">` → Para direcciones web.  
7. `<input type="email">` → Para direcciones de correo.  
8. `<input type="date">` → Para selectores de fecha.  
9. `<input type="month">` → Para meses.  
10. `<input type="week">` → Para semanas.  
11. `<input type="time">` → Para horas.  
12. `<input type="datetime">` → Para fechas y horas absolutas.  
13. `<input type="datetime-local">` → Para fechas y horas locales. 
