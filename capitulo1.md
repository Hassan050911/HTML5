# Capitulo 1 ¿Como hemos llegado aqui?
 
Este libro trata especificamente de HTML5 y no de otras versiones, para comprender eszte libro primero debe comprender algunos detalles tecnicos especificamente los tipos de **MIME**.

## MINE TYPES

Los encabezados (headers) son importantes porque le dicen al navegador como interpretar el marco de la pagina que sigue, el encabezado mas importante se llama "Content-type" :

                          Content-Type: text/html

"text/html" se denomina el "Content-Type" o "Type MIME" de la página.   

MIME (Multipurpose Internet Mail Extensions) se usa en la web para indicar el tipo de archivo que se está enviando o recibiendo.  Las imágenes tienen sus propios tipos MIME 
 
* image/jpeg para imágenes JPEG
* image/png para imágenes PNG 

Todo tiene su propio tipo MIME cada lenguaje tiene su tipos de MINE, la web se ejecuta con tipos MIME. Todo lo que hemos visto en las paginas web HTML (imágenes, scripts, vídeos, PDF, etc) con una URL se han creado con un tipo de MIME especifico en el encabezado Content-Type. 

### W3C (World Wide Web Consortium)

Es una organización internacional que desarrolla estándares y pautas para garantizar el crecimiento y la accesibilidad de la World Wide Web (WWW). 

## IMG Etiqueta

Para usar la etiqueta `<IMG>` requiere el argumento **SRC="url"**,  esto nombra un archivo de bitmap o pixmap  para que el navegador pueda extraer de la red e interpretarlo como una imagen, para incrustarla en el texto en el punto de aparición de la etiqueta.

            <IMG SRC="file://foobar.com/foo/bar/blargh.xbm">


<img src="https://www.gtush.com/wp-content/uploads/2018/06/leon-portada.jpg">


Este es un ejemplo de la etiqueta **`<IMG>`** con el argumento "**SRC="url**" , esto no es una etiqueta de cierre, solo es una etiqueta independiente. 

### XBM & XPM

* XBM (X BitMap): Imágenes en blanco y negro, definidas como código ASCII.

* XPM (X PixMap): Soporte básico para colores.

### Mosaic 

* El primer navegador web gráfico, creado por Marc Andreessen y Eric Bina en el NCSA.
* La versión para Unix se llamaba X Mosaic.

Los navegadores web deben ser compatibles con múltiples formatos de imagen, como XBM y XPM (populares en Unix). Si un navegador no soporta un formato, puede mostrar un marcador de posición (ej: X Mosaic usaba un mapa de bits predeterminado).

## La propuesta de la etiqueta IMG

* Marc Andreessen propuso la etiqueta "IMG" con el atributo "SRC" (source), similar a lo que usamos hoy.

                         <IMG SRC="ruta/imagen.xbm">

* Tony Johnson respondió con una idea similar pero con diferencias clave:
saba "ICON" en lugar de "IMG".
Incluía un atributo NAME para imágenes "predefinidas" en el navegador.

               <ICON name="NoEntry" href="ruta/NoEntry.xbm">

## Propuestas alternativas para incluir contenido 

 Etiqueta  `<INCLUDE>`

 Propuesta por Tony para incluir documentos dentro de otro. Su objetivo era permitir la inclusión de imágenes y otros contenidos sin necesidad de especificar el tipo de archivo.

                              <INCLUDE HREF="...">

Relacionado con la llegada de HTTP2, que aún no estaba implementado. Alternativa:

                       <A HREF="..." INCLUDE>See photo</A>

para compatibilidad con navegadores antiguos.

## Respuesta de Tim Berners-Lee

Tim propuso la siguiente solución:

               <A NAME=fig1 HREF="..." REL="EMBED, PRESENT">Figure</A>

Propuso el uso de valores `REL` para diferenciar la forma en que los navegadores presentan contenido.   

## An Unbroken Line

### La evolución de HTTP y HTML

* HTTP aún existe. Evolucionó con éxito de 0.9 a 1.0 y más tarde a 1.1. Y sigue evolucionando.

* HTML aún existe. Aquel rudimentario formato de datos —que ni siquiera soportaba imágenes en línea— evolucionó con éxito a 2.0, 3.2, 4.0.

* HTML es una línea inquebrantable, aunque retorcida y llena de ramas muertas en su árbol evolutivo. Sin embargo, aquí estamos en 2010, y páginas de 1990 aún se renderizan en navegadores modernos.

### HTML: una conversación en constante cambio

HTML siempre ha sido un diálogo entre desarrolladores de navegadores, autores, entusiastas de los estándares y otros apasionados de las etiquetas angulares. La mayoría de las versiones exitosas de HTML han sido "retro-especificaciones", adaptándose a la realidad mientras intentaban dirigir su evolución.

Cualquier intento de mantener HTML "puro" ignorando a los navegadores o autores ha sido un fracaso. HTML nunca ha sido puro, y los intentos de reemplazarlo han sido espectaculares fracasos.

### Evolución de navegadores y sistemas operativos

### Navegadores:

* Netscape Navigator fue abandonado en 1998 y luego reescrito desde cero para crear Mozilla Suite, que más tarde dio origen a Firefox.

* Internet Explorer tuvo sus humildes inicios en Microsoft Plus para Windows 95, junto con temas de escritorio y un juego de pinball.

Algunos de los mismos desarrolladores de la web de los 90s siguen participando en los estándares actuales. Muchos de ellos estuvieron involucrados en predecesores de HTML, que se remontan a los años 80s o incluso antes.

No todos los códigos publicados ganan: Andrew, Intermedia y HyTime también lanzaron sus propias versiones, pero no prevalecieron.

El `img` original de Marc Andreessen no especificaba un formato de gráficos común, no definía cómo el texto debía fluir alrededor de la imagen y no tenía texto alternativo o contenido de respaldo para navegadores más antiguos.

## A Timeline of HTML Development 1997 TO 2004

### Evolución de HTML y XHTML

* En discusiones, se acordó que extender HTML 4.0 o convertirlo en una aplicación XML era difícil. La solución fue comenzar de nuevo con una suite de etiquetas basadas en XML.

* El W3C reactivó el HTML Working Group con el objetivo de crear esta suite de etiquetas en XML. En diciembre de 1998, publicaron un borrador que reformulaba HTML en XML, sin agregar nuevos elementos o atributos. Esto se convirtió en XHTML 1.0.

* XHTML 1.0 introdujo un nuevo tipo MIME: application/xhtml+xml, pero para facilitar la migración desde HTML 4, permitió seguir sirviendo documentos como text/html bajo las directrices del Apéndice C.

### XHTML Extended Forms y el inicio de XForms

* En agosto de 1999, el HTML Working Group publicó un borrador de XHTML Extended Forms, declarando que la nueva generación de formularios no sería compatible con navegadores anteriores.

* Se renombró como XForms y en octubre de 2003 se publicó la primera edición de XForms 1.0.

### XHTML 1.1 y el fin del Apéndice C

* En mayo de 2001, el HTML Working Group lanzó XHTML 1.1, agregando pocas funciones nuevas a XHTML 1.0, pero eliminando el Apéndice C.

* A partir de XHTML 1.1, todos los documentos debían servirse con application/xhtml+xml, marcando el fin de la compatibilidad con el antiguo text/html.

## EVERYTHING YOU KNOW ABOUT XHTML IS WRONG

### El problema de los tipos MIME

Los navegadores han sido siempre "permisivos" con HTML. Si olvidabas una etiqueta de cierre como `</head>`, el navegador lo interpretaba de todas formas. Si anidabas mal etiquetas `<b><i></b></i>`, simplemente lo corregía internamente.

Este comportamiento condujo a la proliferación de páginas HTML "rotas". Se estima que más del 99% de las páginas web contienen al menos un error, pero al no haber mensajes de error visibles, nadie las corregía.

### "draconian error handling"

En 1997, el W3C publicó XML, estableciendo que cualquier error debía ser fatal para los programas que lo consumieran. Esto se conoció como manejo draconiano de errores, en referencia a las severas leyes del líder griego Draco.

Cuando XHTML reformuló HTML como una sintaxis basada en XML, aplicó esta misma política: cualquier error, por mínimo que fuera, interrumpía la carga de la página y mostraba un mensaje de error al usuario.

### ¿Realmente estás usando XHTML?

Si tu página se sirve con `text/html`, sigue siendo interpretada con un parser HTML "permisivo". Sin el tipo MIME `application/xhtml+xml`, tu XHTML no es más que XML solo de nombre.

## A Competing Vision

### El Debate en 2004

En junio de 2004, el W3C organizó el Workshop on Web Applications and Compound Documents. Participaron representantes de navegadores, empresas de desarrollo web y miembros del W3C.

Entre ellos, Mozilla Foundation y Opera Software propusieron una visión alternativa para el futuro del web: en lugar de abandonar HTML 4, plantearon su evolución con nuevas funcionalidades para aplicaciones modernas.

### Principios Claves de la Propuesta

**Compatibilidad y migración sencilla**

* La tecnología web debe basarse en HTML, CSS, DOM y JavaScript.

* Debe ser utilizable en IE6 y otros navegadores existentes sin necesidad de complementos.

**Manejo de errores bien definido**

* Los navegadores no deben inventar su propio sistema de errores.

* Se deben especificar reglas claras de recuperación de errores, evitando fallos catastróficos.

**Uso práctico**

* Cada nueva característica debe justificarse con un caso de uso real.

* Se deben solucionar problemas previos sin agregar complejidad innecesaria.

**El scripting es esencial**

* JavaScript es parte fundamental de la web, pero se debe preferir el marcado declarativo cuando sea posible.

* El código debe ser independiente de dispositivos.

**Evitar perfiles específicos para dispositivos**

* Las funciones deben ser compatibles entre navegadores de escritorio y móviles.

 **Proceso abierto**

* La evolución de la web debe ser transparente, con acceso público a discusiones y borradores.

 ## WHAT WORKING GROUP?

 

