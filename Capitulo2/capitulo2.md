#  Capitulo 2 deteccion de caracteristicas HTML5

## DIVING IN

HTML5 no es una sola cosa, sino un **conjunto de características individuales** (como canvas, video o geolocalización).  

* No tiene sentido preguntar si un navegador "soporta HTML5", porque no es algo unitario.  
* En cambio, se puede detectar el soporte para **cada función específica** por separado.  

## Explicación `<canvas>` en HTML5

### ¿Qué es?

- Un área para dibujar en páginas web usando JavaScript
- Como un lienzo digital donde puedes crear gráficos
- Usos comunes: juegos, gráficos estadísticos, animaciones

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

**Interfaces dinámicas**  
Para crear dashboards y elementos UI interactivos.

**Aplicaciones gráficas**  
Herramientas de diseño y edición online.

**Visualización de datos**  
Gráficos complejos y actualizaciones en tiempo real.

**Desarrollo de juegos**  
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

## Qué es el elemento `<video>`?
Es una etiqueta de HTML5 que permite mostrar videos directamente en una página web sin necesitar plugins como Flash.

## Lo básico que debes saber:

### Cómo se usa

```html
<video controls width="400">
  <source src="mi-video.mp4" type="video/mp4">
  Tu navegador no soporta video HTML5
</video>
```
# Formatos de Video en HTML5 

## Concepto Básico

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

Son como "ayudantes" que permiten ejecutar código JavaScript en segundo plano sin frenar tu página web.

### Para qué sirven:

- Hacer cálculos pesados

- Descargar datos

- Procesar información  


## ¿Cómo saber si el navegador los soporta?

### Método 1: Manual

```js
if (window.Worker) {
  console.log("¡Soporta Web Workers!");
} else {
  console.log("No soporta :(");
}
```

