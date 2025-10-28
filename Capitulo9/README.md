# Capítulo 9: A Form of Madness

HTML5 le da un upgrade enorme a los formularios web. Ahora tenemos nuevos **atributos** y **tipos de input** que hacen que todo sea más fácil y rápido para el usuario. Lo mejor: si un navegador no los soporta, simplemente funciona como antes.

---

## 1. Placeholder

El `placeholder` es ese texto que aparece dentro de un campo vacío y que desaparece cuando haces clic o empiezas a escribir. Super útil para dar una pista al usuario.

## **Ejemplo:**
```html
<form>
  <input name="q" placeholder="Buscar en marcadores e historial">
  <input type="submit" value="Buscar">
</form>
``` 
# Autofocus Fields

HTML5 agrega el atributo `autofocus` para que un campo de formulario reciba automáticamente el foco al cargar la página. Antes, esto se hacía con JavaScript, pero tenía varios problemas:

- Puede molestar a usuarios avanzados o con necesidades      especiales.
- Si presionas espacio para desplazar la página, el foco en el input hace que se escriba un espacio en lugar de desplazarse.
- Scripts de autofocus pueden mover el foco inesperadamente si el usuario empieza a escribir en otro campo mientras la página carga.

Con el atributo `autofocus`:

- Es solo HTML, no script.
- Se comporta igual en todos los sitios.
- Los navegadores o extensiones pueden permitir al usuario desactivar esta función.
- Los navegadores que no lo soportan simplemente lo ignoran.

## Ejemplo básico:

```html
<form>
  <input name="q" autofocus>
  <input type="submit" value="Search">
</form> 
```

## Autofocus con fallback (para navegadores antiguos)

```html
<form name="f">
  <input id="q" autofocus>
  <script>
    if (!("autofocus" in document.createElement("input"))) {
      document.getElementById("q").focus();
    }
  </script>
  <input type="submit" value="Go">
</form>
```
# Email Addresses (type="email")

Antes de HTML5, los formularios web tenían solo unos cuantos tipos de campos:

| Campo | Código HTML | Nota |
|-------|------------|------|
| Checkbox | `<input type="checkbox">` | Se puede activar o desactivar |
| Radio button | `<input type="radio">` | Se puede agrupar con otros inputs |
| Password | `<input type="password">` | Muestra puntos en lugar de caracteres |
| Drop-down | `<select><option>…</option></select>` | Lista desplegable |
| File picker | `<input type="file">` | Abre un diálogo de archivos |
| Submit | `<input type="submit">` | Botón para enviar el formulario |
| Plain text | `<input type="text">` | Tipo de texto, se puede omitir el atributo `type` |

Todos estos campos **siguen funcionando** en HTML5, así que si actualizas tu DOCTYPE, no necesitas cambiar nada.  

---

## Nuevo tipo: email

HTML5 agrega 13 nuevos tipos de campos, y uno de ellos es para **direcciones de correo**:

```html
<form>
  <input type="email">
  <input type="submit" value="Go">
</form>
```
## Numbers as Spinboxes (type="number")

El siguiente tipo de campo en HTML5 son los **números**.  
Pedir un número parece fácil, pero no siempre lo es. No siempre se quiere “cualquier número”, sino uno **dentro de un rango** o con ciertas condiciones (por ejemplo, solo enteros o múltiplos de 10).  
HTML5 pensó en eso y añadió el tipo `number`.

---

## Ejemplo básico

```html
<input 
  type="number" 
  min="0" 
  max="10" 
  step="2" 
  value="6">
```

## Qué hace cada atributo

- type="number" → Define que el campo solo acepta números.
- min="0" - Valor mínimo permitido.
- max="10" - Valor máximo permitido.
- step="2" - Define los saltos entre valores (0, 2, 4, 6, 8, 10).
- value="6" - Valor inicial mostrado al cargar la página

## Numbers as Sliders (type="range")

Los *spinboxes* no son la única forma de pedir números.  
También existen los **sliders**, esos controles con una barra que se mueve para elegir un valor.

---

## Ejemplo

```html
<input 
  type="range"
  min="0"
  max="10"
  step="2"
  value="6">
  ```
  ## Atributos
Los atributos son los mismos que en type="number":

- min - Valor mínimo permitido.
- max - Valor máximo.
- step - Tamaño del salto entre valores.
- value - Valor inicial.Atributos

La diferencia está solo en la interfaz.
En lugar de escribir un número, el usuario mueve el control deslizante.

## Date Pickers

En **HTML4** no existía una forma nativa para elegir fechas, por eso se usaban librerías como **Dojo**, **jQuery UI**, **YUI** o **Closure Library**.  
El problema era que todas esas soluciones dependían de JavaScript y de integrarse al framework.

Con **HTML5** esto cambió, ya que ahora incluye controles nativos para elegir fechas y horas sin necesidad de programar.  
De hecho, existen **seis tipos diferentes** de campos relacionados con el tiempo:

| Tipo de input | Descripción |
|----------------|-------------|
| `type="date"` | Selecciona una fecha completa (día, mes y año). |
| `type="month"` | Selecciona solo el mes y el año (por ejemplo, para la fecha de vencimiento de una tarjeta). |
| `type="week"` | Permite elegir una semana específica del año. |
| `type="time"` | Permite seleccionar una hora. |
| `type="datetime"` | Fecha y hora (con zona horaria). |
| `type="datetime-local"` | Fecha y hora local (sin zona horaria). |

### Ejemplo básico

```html
<form>
  <input type="date">
</form>
```

## Search Boxes

Este tema es sencillo, pero tiene detalles interesantes.  
Pensemos en los cuadros de búsqueda (search boxes) que vemos en cualquier sitio:  
Google, Amazon, Newegg o incluso en blogs.  
Casi todos usan el clásico:

```html
<input type="text">
```
## Color Pickers

HTML5 también introdujo el elemento:

```html
<input type="color">
```
Este permite elegir un color desde un selector visual y devuelve su valor en formato hexadecimal (por ejemplo, #ffcc00).

## Form Validation

HTML5 no solo trajo nuevos tipos de input, también introdujo algo muy útil:  
la **validación automática de formularios** sin necesidad de JavaScript.

### ¿Qué es la validación?

Es el proceso en el que el navegador revisa que los datos ingresados sean correctos antes de enviar el formulario.  
Por ejemplo, que un correo tenga el formato correcto o que un número esté dentro de un rango permitido.

### Ejemplo básico

```html
<form>
  <label for="email">Correo electrónico:</label>
  <input type="email" id="email" required>
  <input type="submit" value="Enviar">
</form>
```

## Tipos de validación automática

- type="email" - valida que el texto sea un correo válido.
- type="url" - valida que sea una dirección web.
- type="number" - valida números, considerando los atributos min y max.

## Required Fields

HTML5 también permite marcar ciertos campos como **obligatorios**.  
Esto evita que el usuario envíe el formulario sin completar la información necesaria.

### ¿Cómo se usa?

Solo necesitas agregar el atributo `required` al campo que quieres hacer obligatorio.

```html
<form>
  <input id="q" required placeholder="Escribe algo...">
  <input type="submit" value="Buscar">
</form>
```




