# # Capítulo 10: Extensibilidad en HTML5

HTML5 tiene más de 100 elementos. Algunos son semánticos y otros se usan para APIs. A lo largo de la historia del HTML siempre ha habido debate sobre qué etiquetas incluir.

Ejemplos de etiquetas propuestas que no existen:
- `<person>`
- `<rant>`

No existen porque HTML no puede incluir todo, y agregar etiquetas arbitrarias rompe consistencia y validación.

---

## ¿Se pueden inventar etiquetas?
Sí puedes escribir nuevas etiquetas, pero no es buena práctica porque:

- No validan
- No son compatibles entre navegadores
- Pueden entrar en conflicto con futuras versiones del estándar

---

## Soluciones para extender HTML antes de HTML5
HTML no podía cubrir todas las necesidades semánticas, por lo que surgieron alternativas:

| Método | Descripción |
|---|---|
| Microformats | Usa atributos como `class` y `rel` para agregar semántica extra |
| RDFa | Permite añadir metadatos complejos; nació en XHTML y luego se adaptó a HTML |

---

## Microdata en HTML5
HTML5 incluye su propio sistema para extender semántica: **Microdata**.  
Permite describir datos directamente en el HTML mediante atributos especiales.

---

### Ejemplo de Microdata

```html
<div itemscope itemtype="https://schema.org/Person">
  <span itemprop="name">Juan Pérez</span>
  <span itemprop="jobTitle">Desarrollador Web</span>
  <img itemprop="image" src="juan.jpg" alt="Foto de Juan Pérez">
</div>
```

# ¿Qué es Microdata?


## Desglosemos el enunciado
- **Custom vocabularies**  
  Microdata gira en torno a vocabularios personalizados. Piensa en el “conjunto de todos los elementos HTML5” como un vocabulario. Ese vocabulario incluye elementos como `section` o `article`, pero no incluye necesariamente `person` o `event`. Si quieres representar una persona en la página, defines tu propio vocabulario y usas Microdata para incrustar esas propiedades.

- **Name/value pairs**  
  Cada vocabulario define propiedades con nombre (por ejemplo: `name`, `photo`). Para añadir una propiedad a la página, declaras su nombre en un lugar específico del HTML; Microdata tiene reglas para extraer el valor según dónde declares esa propiedad.

- **Scoped**  
  Microdata usa *scopes* basados en la jerarquía natural del DOM. Es decir, las propiedades dentro de un elemento pertenecen al vocabulario declarado para ese elemento. Esto permite usar varios vocabularios en una misma página y anidarlos entre sí.

- **Annotates the DOM**  
  Microdata no es un formato separado: **es un complemento del HTML**. Añade semántica a datos ya visibles en el DOM. Si la información no está en el DOM, quizá Microdata no sea la solución adecuada.

## Principios prácticos
- Microdata es para **dar más significado** a contenido que ya está en el HTML.
- No sustituye al HTML; lo **completa**.
- Permite **múltiples vocabularios** en la misma página y **anidamiento** entre ellos gracias al árbol del DOM.
- Es ideal cuando ya usas HTML correctamente pero necesitas metadatos adicionales.

## Ejemplo simple y anidado

```html
<!-- Vocabulario Persona -->
<div itemscope itemtype="https://schema.org/Person">
  <span itemprop="name">María López</span>
  <div itemprop="address" itemscope itemtype="https://schemaorgPostalAddress">
    <span itemprop="streetAddress">Calle Falsa 123</span>
    <span itemprop="addressLocality">Ciudad</span>
  </div>
  <span itemprop="jobTitle">Diseñadora</span>
</div>


