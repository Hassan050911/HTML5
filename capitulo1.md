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

Para usar la etiqueta IMG requiere el argumento **SRC="url"**,  esto nombra un archivo de bitmap o pixmap  para que el navegador pueda extraer de la red e interpretarlo como una imagen, para incrustarla en el texto en el punto de aparición de la etiqueta.

     <IMG SRC="file://foobar.com/foo/bar/blargh.xbm">


<img src="https://www.gtush.com/wp-content/uploads/2018/06/leon-portada.jpg">


Este es un ejemplo de la etiqueta "**IMG**" con el argumento "**SRC="url**" , esto no es una etiqueta de cierre, solo es una etiqueta independiente. 

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







  
