# Capítulo 4: Formas Simples

## Recordemos  `<canvas>`

### ¿Que es?

- `<canvas>` es una parte de HTML5 que sirve para dibujar con JavaScript.
- Al principio está vacío. Hay que usar código para que muestre algo.
- Funciona en la mayoría de los navegadores: Chrome, Firefox, Safari, Opera, Android, iPhone.
- En Internet Explorer solo funciona si usás una librería llamada `explorercanvas`.

# Coordenadas en Canvas

### ¿Cómo funciona el sistema de coordenadas?

- El canvas usa una **rejilla 2D**.
- La coordenada (0, 0) está en la **esquina superior izquierda**.
- El eje **X** aumenta hacia la **derecha**.
- El eje **Y** aumenta hacia **abajo**.

## ¿Qué se puede mostrar en el canvas?

Un ejemplo básico de coordenadas puede incluir:
- Líneas verticales y horizontales de color blanco claro.
- Líneas negras que marcan los ejes X e Y.
- Flechas al final de los ejes.
- Letras "x" y "y" para indicar los ejes.
- Texto como "(0, 0)" en la esquina superior izquierda y "(500, 375)" en la esquina inferior derecha.
- Puntos en esas esquinas para marcar las coordenadas.

# Rutas en Canvas

### ¿Qué son las rutas?

- Dibujar en canvas es como dibujar primero con lápiz y después repasar con tinta.
- Las funciones `moveTo()` y `lineTo()` son como usar un lápiz: dibujan la ruta, pero **todavía no se ve nada**.
- Para que se vea el dibujo, tenés que usar `stroke()` o `fill()`, que serían como pasar el dibujo a tinta.

# Texto en Canvas

### ¿Se puede escribir texto en canvas?

Sí. Pero no es como el texto común en HTML. Acá no hay `margin`, `padding`, ni CSS raro. Solo escribís texto en una coordenada exacta y listo.

## Propiedades importantes

```js
context.font = "bold 12px sans-serif";   // igual que en CSS
context.textAlign = "right";             // puede ser left, right, center, etc.
context.textBaseline = "top";            // puede ser top, middle, bottom, etc.
``` 
### Ejemplo de como escribir 

```js 
context.font = "bold 12px sans-serif";
context.fillText("x", 248, 43);
context.fillText("y", 58, 165);
```
# Gradientes en Canvas

### ¿Qué son los gradientes?

Los gradientes son transiciones suaves entre dos o más colores. En canvas podés usar dos tipos:

1. **Gradiente lineal**: transición de color a lo largo de una línea.
2. **Gradiente radial**: transición entre dos círculos (como un cono de color).

# ¿Qué onda con Internet Explorer y `<canvas>`?

## El problema

Internet Explorer (hasta la versión 8) **no entiende** el elemento `<canvas>` de HTML5.  
En lugar de eso, usa una cosa rara de Microsoft que se llama **VML**, que hace cosas parecidas pero no es lo mismo.

## ¿Cómo lo arreglamos?

Con una librería llamada **excanvas.js** (también le dicen ExplorerCanvas).  
Lo que hace es "engañar" a IE para que pueda usar `<canvas>`, pero usando VML por detrás.

## Ejemplo 

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Canvas con IE</title>
  <!-- Solo IE carga este script -->
  <!--[if IE]>
  <script src="excanvas.js"></script>
  <![endif]-->
  <script>
    // Esperamos a que todo cargue
    window.onload = function() {
      var canvas = document.getElementById("miCanvas");
      var ctx = canvas.getContext("2d");

      // Dibujo básico: un rectángulo rojo
      ctx.fillStyle = "red";
      ctx.fillRect(20, 20, 150, 100);
    };
  </script>
</head>
<body>
  <canvas id="miCanvas" width="400" height="200"></canvas>
</body>
</html>
```

# Ejemplo completo con `<canvas>`: El juego de Halma

## ¿Qué es Halma?

Es un juego de mesa viejito. En este ejemplo, se hizo una versión solitaria en un tablero de **9×9**.  
Empiezas con 9 piezas en una esquina (abajo a la izquierda) y debes moverlas a la esquina opuesta (arriba a la derecha) con los **menos movimientos posibles**.

## Tipos de movimientos

1. **Mover una pieza a una casilla vacía al lado** (en cualquier dirección).
2. **Saltar sobre otra pieza** (puedes hacer varios saltos seguidos, todo cuenta como un solo movimiento).
