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

