# Geolocalización

La geolocalización es la forma de saber dónde estás en el mundo y, si quieres, compartirlo con personas de confianza.  

Hay varias formas de saber tu ubicación:  
- Usar tu dirección IP  
- La red inalámbrica a la que estás conectado  
- La torre celular a la que está conectado tu teléfono  
- Hardware GPS que calcula latitud y longitud usando satélites  

# Geolocation API

La Geolocation API permite que una página web use tu ubicación (latitud y longitud) con tu permiso.  
JavaScript en la página puede usar esta info para cosas como:  
- Encontrar negocios cerca  
- Mostrar tu ubicación en un mapa  

La mayoría de los navegadores modernos (IE 3.5+, Firefox 5+, Safari 5+, Chrome 10.6+, Opera 3+, iPhone y Android) la soportan.  

Para navegadores viejos, hay librerías que ayudan a que funcione.  

También hay APIs específicas para otros dispositivos móviles que se ven más adelante.

# Geolocation API: Cómo usarla con JavaScript

La Geolocation API te deja pedir la ubicación del usuario en la página web con su permiso.  
La función principal es `navigator.geolocation.getCurrentPosition()`, que toma una función que se llama cuando se obtiene la ubicación.

## Código básico para obtener la ubicación

```js
function get_location() {
  navigator.geolocation.getCurrentPosition(show_map);
}

function show_map(position) {
  var latitude = position.coords.latitude;
  var longitude = position.coords.longitude;
  // Aquí puedes usar la ubicación para algo, como mostrar un mapa
  console.log("Lat:", latitude, "Lon:", longitude);
}
