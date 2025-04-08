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

## Explicacion  `<canvas text>` en HTML5

