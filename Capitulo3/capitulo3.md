# Capitulo 3 ¿Que significa todo esto?

# DOCTYPE 

### ¿Que es?

El **DOCTYPE** es una declaración que especifica la versión de HTML usada en una página web, ayudando al navegador a interpretarla correctamente. En HTML5, simplemente se escribe `<!DOCTYPE html>`.

```html
 <!DOCTYPE html>
```

# El Elemento `<HEAD>`

### ¿Que es?

El `<head>` es la parte del HTML que contiene metadatos, como el título, estilos y scripts, pero no se ve en la página. Va después de `<html>` y antes de `<body>`.

```html
 <Head>
```
Este es un ejemplo basico de que como es que se abre, la primer linea del codigo es el elemento `<!DOCTYPE html>` y dspues se comienza a estructurar con los elementos mencionados antes. 

```html
<!DOCTYPE html> 
<html>
  <head>
    <title>Hello Wordl</title>
  </head>
  <body>
    <!-- Aqui es donde comienzas a escribir tu codigo  -->
     <h1> 
        Hello world
     </h1>    
  </body>
</html>
```
# Enlaces `<a href>`

### ¿Que es?
El elemento `<a href>` en HTML se usa para crear enlaces (hipervínculos) a otras páginas, archivos o secciones dentro de la misma página.

Estos son algunos ejemplos sencillos, dentro de la etiqueta se escribe el texto del enlace:

```html
<a href="URL">Texto del enlace</a>
<a href="https://www.ejemplo.com">Visitar Ejemplo</a>
```
# Etiqueta `<Link>`

### ¿Que es?

Es una etiqueta que sirve para vincular una hoja de estilos **CSS** al documento, esto le indica al navegador que el archivo enlazado debe interpretarse como **CSS**. 

##  REL = STYLESHEET

### ¿Que es?

Es un atributo clave en HTML que define la relación entre el documento actual y un archivo externo vinculado (generalmente CSS).

```html
<link rel="stylesheet" href="nombre de tu hoja de estlos.css">
```

## REL = ALTERNATE

### ¿Que es?

Se utiliza para indicar una versión alternativa del documento actual. Su uso varía según el contexto, pero siempre señala una relación de alternancia con otro recurso.

```html
<link rel="alternate" hreflang="en" href="https://ejemplo.com/en/index.html">
```

## Otras Relaciones De Link 

Estos son algunos ejemplos que tambien podemos utilizar: 

1. **`rel="archives"`** Enlace a contenido histórico o archivado.

2. **`rel="external"`** Enlace a un sitio fuera del dominio actual.

3. **`rel="start"`** Antes indicaba el inicio de una serie.

4. **`rel="prev"`** Enlace a la página anterior.

5. **`rel="next"`** Enlace a la página siguiente.

6. **`rel="begin"`** Antes marcaba el inicio de recursos multimedia.

7. **`rel="first"`** Enlace al primer documento de una serie.

8. **`rel="last"`** Enlace al último documento de una serie.

9. **`rel="up"`** Enlace a un documento jerárquicamente superior.

10. **`rel="nofollow"`** Indica a los motores de búsqueda ignorar el enlace.

11. **`rel="noreferrer"`** Evita enviar la URL de origen al hacer clic.

12. **`rel="search"`** Vincula un archivo de búsqueda personalizada.  

# Nuevos Elmentos En HTML5 


## `<section>`

### ¿Que hace?
Define una sección temática dentro de un documento, agrupando contenido relacionado bajo un mismo tema. Siempre debe llevar un título (como `<h2>`, `<h3>`, etc.) para indicar su propósito.

___

## `<nav>`

### ¿Que hace?

Define una sección de una página que contiene enlaces de navegación principales, ya sea a otras páginas o a secciones internas.

___

##  `<article>`

### ¿Que hace?

En HTML representa un contenido autónomo y reutilizable dentro de una página. Es independiente del resto del contenido y tiene sentido por sí mismo.

___

##  `<aside>`

### ¿Que hace?

Se utiliza para contenido relacionado indirectamente con el contenido principal, pero que puede considerarse independiente. Es ideal para información complementaria o secundaria.

___

## `<hgroup>`

### ¿Que hace?

se utiliza para agrupar encabezados relacionados como títulos principales y subtítulos que forman parte de un mismo bloque de cabecera.

___

##  `<header>`

### ¿Que hace?

Es un contenedor diseñado para agrupar contenido introductorio o ayudas de navegación al inicio de una sección o página. No debe confundirse con el `<head>` ni es lo mismo que el encabezado visual de un sitio.
___

 ## `<footer>`

 ### ¿Que hace?

Es un contenedor diseñado para información relacionada con su sección o documento padre, como créditos, enlaces adicionales, datos legales o metadata relevante. Aunque tradicionalmente se ubica al final, su posición no está restringida técnicamente.
 ___

##  `<time>`

### ¿Que hace?

Se utiliza para marcar fechas, horas o periodos específicos en un formato legible tanto para humanos como para máquinas. Su propósito principal es proporcionar información temporal estructurada y semántica.
___

## `<mark>`

### ¿Que hace?

Se utiliza para resaltar o marcar fragmentos de texto dentro de un contenido, con el fin de indicar que son relevantes en un contexto específico. Funciona como un "marcador" visual, similar a cuando subrayamos o pintamos con rotulador un texto en papel.





