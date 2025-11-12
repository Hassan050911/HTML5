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
```
# Modelo de Datos de Microdata

Microdata funciona con **pares nombre/valor** y vocabularios definidos por el autor. Para crear un vocabulario propio, se necesita un **namespace**, normalmente un URL del dominio del autor.  
Ejemplo de namespace para representar una persona:  
`http://data-vocabulary.org/Person`

---

## Propiedades del vocabulario
Ejemplo de propiedades básicas para una persona:

- `name`: nombre completo (texto)
- `photo`: URL de imagen
- `url`: enlace asociado (sitio personal, perfil, etc.)

Estas propiedades suelen tener una estructura natural en HTML, incluso antes de Microdata:

- Nombre → elemento `<h1>`
- Imagen → `<img>`
- Enlace → `<a>`
- Contenedor general → `<section>`

---

## HTML sin microdata

```html
<section>
  <h1>Mark Pilgrim</h1>
  <p><img src="http://www.example.com/photo.jpg" alt="[me smiling]"></p>
  <p><a href="http://diveintomark.org/">weblog</a></p>
</section>
```

# Marking Up People

Microdata permite describir personas en HTML usando el vocabulario **Person**.  
Se definen propiedades con `itemprop` dentro de un ámbito marcado con `itemscope` y `itemtype`.

- `itemscope` inicia el ámbito del vocabulario.  
- `itemtype` indica el tipo de datos (por ejemplo, `Person`).  
- `itemprop` marca cada propiedad (nombre, foto, dirección, etc.).  

El vocabulario **Person** incluye propiedades como:
- `name`: nombre de la persona.  
- `photo`: imagen.  
- `title`: puesto o cargo.  
- `affiliation`: empresa u organización.  
- `address`: dirección (puede tener subpropiedades como `locality` o `postal-code`).  
- `url`: enlaces personales.  

Estas etiquetas añaden significado semántico al contenido visible en la página sin alterar su estructura.

# Marking Up Organizations

Microdata también puede describir **organizaciones o empresas** usando el vocabulario `Organization`.  
Se usa cuando se quiere marcar información como el nombre, dirección, teléfono o página web de una entidad.

---

#### Conceptos clave

- **`itemscope`**: define el ámbito del vocabulario.  
- **`itemtype`**: indica el tipo de microdata, en este caso `"http://data-vocabulary.org/Organization"`.  
- **`itemprop`**: marca cada propiedad específica (por ejemplo, `name`, `address`, `tel`, `url`).  

---

#### Propiedades principales del vocabulario *Organization*

| Propiedad | Descripción |
|------------|--------------|
| `name` | Nombre de la organización. |
| `url` | Enlace al sitio web de la organización. |
| `address` | Dirección, puede contener subpropiedades como `street-address`, `locality`, `region`, `postal-code`, `country-name`. |
| `tel` | Número telefónico de la organización. |
| `geo` | Coordenadas geográficas (`latitude`, `longitude`). |

---

#### Notas importantes

- El uso de **microdata** no cambia la estructura visual de la página.  
- Se pueden combinar múltiples vocabularios (por ejemplo, `Organization` y `Geo`).  
- La etiqueta `<meta>` permite agregar **datos invisibles**, útiles para información como coordenadas.  
- Los datos invisibles deben mantenerse actualizados con el texto visible.  

# MARKING UP EVENTS

El tema **Marking Up Events** explica cómo usar **microdatos (microdata)** en **HTML5** para describir eventos de forma que los motores de búsqueda comprendan mejor la información, especialmente útil para calendarios, conferencias o agendas.

Para lograrlo, se agregan los atributos `itemscope` y `itemtype` al elemento `<article>`, indicando que el contenido describe un **evento**, con el tipo `http://data-vocabulary.org/Event`.

### Propiedades principales del vocabulario de eventos

| Propiedad | Descripción |
|------------|--------------|
| `summary` | Nombre del evento |
| `url` | Enlace a la página del evento |
| `location` | Lugar o sede (puede incluir organización o dirección) |
| `description` | Descripción del evento |
| `startDate` | Fecha y hora de inicio (formato ISO) |
| `endDate` | Fecha y hora de fin (formato ISO) |
| `duration` | Duración del evento (formato ISO) |
| `eventType` | Tipo o categoría del evento |
| `geo` | Coordenadas geográficas (latitud y longitud) |
| `photo` | Enlace a una imagen relacionada |

### Aplicación de las propiedades

1. **Nombre del evento:**  
   Se usa `itemprop="summary"` dentro de un `<h1>`.

2. **Imagen:**  
   Se marca con `itemprop="photo"` en el elemento `<img>`.

3. **Descripción:**  
   Se usa `itemprop="description"` en un párrafo `<p>`.

4. **Fechas:**  
   Las fechas de inicio y fin se indican con `<time>` y los atributos `itemprop="startDate"` y `itemprop="endDate"`.

5. **Ubicación:**  
   Puede incluir una organización (`Organization`) con dirección (`Address`), ambas definidas con sus respectivos `itemscope` y `itemtype`.

6. **Coordenadas:**  
   Se utilizan elementos `<meta>` con `itemprop="latitude"` y `itemprop="longitude"` dentro de un contenedor `geo`.

7. **Enlace:**  
   El `itemprop="url"` se agrega al `<a href>` correspondiente.

El uso correcto de microdatos permite que los motores de búsqueda generen **Rich Snippets**, mostrando la información del evento directamente en los resultados, con fecha, lugar y enlace.

# MARKING UP REVIEWS

Este tema muestra cómo mejorar la web mediante *markup* con **microdata**, aplicándolo a reseñas de negocios o productos.





