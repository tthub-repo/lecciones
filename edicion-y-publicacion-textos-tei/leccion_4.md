---
title: Prosa I: elementos más comunes
author: Susanna Allés Torrent, Gabriel Calarco, Gimena del Rio Riande
date: 2022
layout: default
lang: es
---
 
En la lección anterior vimos aquellos elementos que constituían la estructura obligatoria y básica de un documento TEI. Aquí, vamos a centrarnos en una serie de elementos o etiquetas que pueden utilizarse en cualquier documento, incluso en la versión más minimalista [TEI Lite](https://tei-c.org/guidelines/customization/lite/). La panorámica que ofreceremos no es completa, pero corresponde a los más utilizados.
  
# 1. Los módulos obligatorios y el marcado de textos en prosa
 
En primer lugar, conviene recordar que el sistema de codificación TEI se divide en módulos, cada uno destinado a una tipología textual, como verso, drama, transcripciones de discurso, diccionarios, etc. Cada uno de estos módulos se encuentra explicado en las [*Guías directrices*](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/index.html). A su vez, los módulos pueden ser obligatorios u optativos. En esta lección nos centraremos en los primeros. Los módulos obligatorios son cuatro: [`tei`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ST.html), [`core`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/CO.html), [`header`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/HD.html), [`textstructure`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/DS.html); sin estos no tendríamos un documento válido.
 
Los módulos optativos, en cambio, responden a tipologías textuales concretas y los veremos con más detalle en las siguientes lecciones.
 
Las [*Guías directrices*](https://tei-c.org/guidelines/p5/) de TEI no tienen un módulo específico para la codificación de prosa, pues se trata de un término algo genérico y difícil de definir. La mayoría de los elementos utilizados para codificar textos en prosa pertenecen al módulo [`core`](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/CO.html) y [`textstructure`](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/DS.html), es decir, los elementos que aparecen integrados en la estructura TEI por defecto.
Dado que los tipos textuales que se valen de la prosa como medio de expresión son sumamente variados dividiremos el trabajo de marcado de textos en prosa en dos lecciones complementarias. Comenzaremos por los elementos generales y comunes en todos los documentos TEI (a excepción de los párrafos `<p>` y las divisiones `<div>` que ya fueron trabajados en la lección anterior), como cuestiones de puntuación o de tipografía, la presentación del texto en la fuente original, la referenciación de  nombres, fechas y medidas, entre otros aspectos. Todos estos elementos se encuentran explicados en la sección ["3. Elements Available in All TEI Documents"](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/CO.html) de las *Guías directrices*.
 
# 2. Títulos y encabezados
 
Los encabezados y títulos de cualquier tipo se marcan con el elemento
[`<head>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-head.html) que puede llevar diversos atributos, como `@type`, para indicar el tipo de título. Por ejemplo:
 
```xml
<head type="Principal">Unidad 1</head>
<head type="parte">PARTE I</head>
<head type="apartado">1. Introducción</head>
```
 
# 3. Puntuación
 
De manera general, y especialmente en prosa, la puntuación del texto no suele codificarse; pero en algunos casos donde el marcado debe ser extremadamente sutil, se puede marcar. El elemento utilizado es:
 
* [`<pc>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-pc.html) (punctuation character): utilizado para codificar el punto, el signo de interrogación y de exclamación, los puntos suspensivos, las comillas (aunque podrían eliminarse si se utiliza `<q>` o `<quote>`), apóstrofes, paréntesis, etc.
 
```xml
<s>
<seg>Está visto<pc>:</pc></seg>
<seg>quieren cebarme</seg><pc>.</pc>
</s>
```
 
Si deseamos marcar diferentes signos de puntuación y diferenciarlos entre sí, podemos utilizar el atributo `@type` para especificar el tipo de signo. Por ejemplo:
 
```xml
<p>Los primeros habitantes de este pueblo pusiéronles cada uno su marca a todos los que pudieron tomar echándolos después dentro de sus cercas<pc type=”puntoycoma”>;</pc> pero multiplícanse tan rápidamente que viéronse luego obligados a soltarlos<pc type=”coma”>,</pc> y hoy van y los matan según precisan de ellos<pc type=”coma”>,</pc> o tienen ocasión de preparar para la venta una cantidad de cueros<pc type=”punto”>.</pc></p>
```
La codificación de la puntuación puede ser interesante en aquellos casos en que se quiera dar fe de los diferentes cambios a lo largo de la historia. A veces, la ausencia o presencia de un punto, por ejemplo, puede cambiar el sentido.
 
# 4. Elementos tipográficos
 
Todos los textos impresos poseen elementos tipográficos diversos como pueden ser la cursiva, la negrita, las versalitas, incluso fuentes diversas, tamaño de la fuente, etc. La naturaleza de estos elementos tipográficos en las fuentes escritas pueden ser de diversa naturaleza:
 
* una palabra o frase en una lengua extranjera, un arcaísmo, un barbarismo, una palabra técnica, etc.
* una palabra o frase sobre la que se quiere poner un énfasis especial, que se resaltaría al hablar.
* una palabra o frase que en realidad no forma parte del discurso del texto, como las referencias cruzadas, los títulos o los encabezados, etc.
* cadenas narrativas diferentes, como un monólogo interno o un comentario.
* la atribución a una referencia externa al texto, como un discurso directo o una citación.
 
Ahora bien, como explicamos anteriormente, el sistema TEI no se concentra tanto en la apariencia del texto como en señalar qué son las cosas. De esta manera, al encontrarnos, por ejemplo con un extranjerismo, quizás no nos interesará tanto señalar que aparece en cursiva, como indicar que se trata de una palabra extranjera. Sea cual sea la opción que se elija, TEI ofrece la posibilidad de marcar estos elementos tipográficos de una manera general, sin implicaciones semánticas. El elemento utilizado a tal propósito es `<hi>` (*highlight*), que por lo general suele tener un atributo `@rend` (*rendition*) que indica de qué manera aparece en el texto:
 
```xml
<hi rend="italic">Palabra o frase en cursiva</hi>
<hi rend="bold">Palabra o frase en negrita</hi>
<hi rend="small-caps">Palabra o frase en versalitas</hi>
```
 
El valor de los elementos es libre, con lo cual nada nos impide señalarlo en otra lengua, por ejemplo:
 
```xml
<hi rend="cursiva">Palabra o frase en cursiva</hi>
```
 
Podemos encontrar además otros elementos que en lugar de referir a las características visuales de la frase o palabra que marcan, describen en cambio la característica que las individualiza y da lugar al tratamiento tipográfico diferenciado. Por ejemplo:
 
* [`<foreign>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-foreign.html) indica una palabra o frase perteneciente a otra lengua; normalmente posee el atributo `@xml:lang` para definir la lengua:
 
```xml
<p>El papa Francisco recuerda los conflictos activos en el mundo en la bendición
<foreign xml:lang="lat">urbi et orbi</foreign></p>
```
 
* [`<emph>`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-emph.html) indica una palabra o frase a la que se atribuye un énfasis especial:
 
```xml
<p>Aquí, como en todas partes, la gente es muy aficionada al dinero. Y digo mal <emph>como en todas partes</emph>: en las ciudades populosas, en los grandes centros de civilización, hay otras distinciones que se ambicionan tanto o más que el dinero, porque abren camino y dan crédito y consideración en el mundo</p>
```
 
* [`<distinct>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-distinct.html) indica un término diferente lingüísticamente (arcaísmo, tecnicismo, dialectalismo, coloquialismo, etc.).
* [`<mentioned>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-mentioned.html) es utilizado para señalar una palabra mencionada o citada.
* [`<soCalled>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-soCalled.html) contiene una palabra o expresión respecto a la cual el autor manifiesta su rechazo de responsabilidad.
 
Finalmente la decisión de marcar una palabra en cursiva con el elemento `<hi>` y el atributo `@rend`, o utilizar un elemento que señale la causa de que esa palabra haya sido puesta en cursiva (como `<forgein>` o `<emph>`), dependerá de las decisiones editoriales tomadas en torno a la codificación de un texto. Es por este tipo de decisiones que varios profesionales dedicados a la edición digital señalan que codificar un texto con TEI implica proponer una hipótesis de lectura.
 
# 5. Milestones
 
Dentro de la categoría que las *Guías directrices* denominan *Milestones* podemos encontrar diversos elementos que nos serán de utilidad para marcar diferentes características físicas del documento. Entre estos elementos encontramos:
 
* [`<milestone>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-milestone.html): marca un punto límite separando cualquier tipo de sección de un texto.
* [`<gb>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-gb.html) (*gathering begins*) puede indicar el inicio o final de la foliación de un manuscrito, por ejemplo donde empieza y donde acaba un cuaderno.
* [`<pb>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-pb.html) (*page break*): indica el cambio de página.
* [`<lb>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-lb.html) (*line break*): indica el cambio de línea.
* [`<cb>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-cb.html) (*column break*): indica el cambio de columna.
Al utilizar este tipo de marcas muchas veces nos encontraremos con elementos vacíos. Por ejemplo, si queremos señalar el comienzo de una línea en el documento fuente podremos utilizar el elemento `<pb>`, pero entre la etiqueta de apertura y la de cierre no introduciremos ningún contenido. En estos casos, para simplificar la tarea de codificación podemos utilizar la sintaxis de XML para crear elementos vacíos que se abren y se cierran con la misma etiqueta. Para el ejemplo de `<pb>` podemos utilizar tanto dos etiquetas para abrir y cerrar el elemento: `<pb></pb>`, como una etiqueta vacía: `<pb/>`. A diferencia de las etiquetas de cierre que tienen la barra inclinada al comienzo, los elementos vacíos que unen apertura y cierre en una misma etiqueta la tienen al final.
 
# 6. Nombres, números y fechas
 
En múltiples ocasiones podemos encontrar en los textos nombres (ya sean topónimos, antropónimos, etc.), números y fechas. TEI propone para ello una serie de elementos que nos serán de gran utilidad.
 
## Nombres
 
Un elemento general para codificar todo tipo de nombres o incluso frases es `<name>`; como ya señalamos al inicio de esta lección existe un módulo específico para el marcado de nombres de lugar, de persona, etc. 
 
Los atributos más utilizados, a parte de `@xml:id`, son `@type` para especificarlos aparte, y `@key` o `@ref` para referirse a un identificador concreto. Por ejemplo, supongamos esta frase: “Pepita Jiménez era hija de Francisca Gálvez quien la quería casar con D. Gumersindo”, la podríamos marcar de la siguiente manera:
 
```xml
<p><name xml:id="PJ">Pepita Jiménez</name> era hija de
<name xml:id="FG">Francisca Gálvez</name> que la hizo casar con
<name xml:id="#Gu">D. Gumersindo</name></p>
```
 
una vez establecidos los identificadores, podríamos referirnos a los personajes con facilidad en el fragmento que sigue:
 
```xml
<p>Era, con todo, tan inverosímil y tan desatinado el suponer que un hombre, que había pasado ochenta años sin querer casarse, pensase en tal locura cuando ya tenía un pie en el sepulcro, que ni la <rs ref="#FG">madre de Pepita</rs>, ni <name ref="#PJ">Pepita</name> mucho menos, sospecharon jamás los en verdad atrevidos pensamientos de <name ref="#Gu">D. Gumersindo</name>.</p>
```
 
Otra forma de referenciar nombres con el atributo `@ref` es a través de un archivo de autoridades como [VIAF](http://viaf.org/) (Virtual International Authority File), que nos permitirá asignar un identificador a estos elementos en forma de un enlace permanente (URI: Identificador de Recursos Uniforme). Si abrimos la página principal de VIAF ([viaf.org](http://viaf.org/)) encontraremos un cuadro de búsquedas (es conveniente acotar los criterios de búsqueda para no obtener una cantidad excesiva de resultados; por ejemplo, para buscar el nombre “Perú”, es conveniente elegir la categoría “Geographic Names” en la pestaña “Select Field”):
 
![Búsqueda de entidades en VIAF](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L4_001.png)
 
Si entramos a la página de VIAF para Perú, encontraremos el enlace permanente o *permalink* (destacado en rojo) que nos permitirá referenciar el elemento al que estemos agregando este atributo en nuestro archivo TEI
 
![Entrada de una entidad en VIAF](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L4_002.png)

El elemento referenciado, quedaría entonces de la siguiente forma:
 
```xml
Antes de decir nada de mi viaje al <name type="lugar" ref="http://viaf.org/viaf/159434034">Perú</name>
```
 
## Deícticos
 
Otro elemento que puede servirnos para marcar entidades es `<rs>` (*referring string*), que indica un nombre con una denominación genérica o una cadena de referencia. Por ejemplo:
 
```xml
anotaré lo que observé de remarcable en <name type="ciudad" ref="http://viaf.org/viaf/1331145424662786830473">Buenos Aires</name>
mientras permanecí
<rs ref="http://viaf.org/viaf/1331145424662786830473">allí</rs>.
```
 
## Fechas
 
En lo que concierne a las fechas, se utiliza el elemento [`<date>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-date.html) y se regulariza su formato (de manera que la máquina la interprete correctamente) en el interior del atributo `@when`, cuyo formato es: año-mes-día. He aquí algunos ejemplos.
 
```xml
<date when="1980-03-23">23 de marzo de 1980</date>
<date when="1980"> el año 1980</date>
<date when="1999-10">octubre de 1999</date>
<date when="--02-14">cada 14 de febrero</date>
<date from="2014-02-10" to="2014-02-20"> del 10 de febrero al
20 de octubre de 2014</date>
```
 
Opcionalmente, se pueden especificar los diferentes sistemas de calendario (juliano, gregoriano, etc.) con el atributo `@calendar`:
 
```xml
<date when="1541" calendar="#juliano">1541</date>
```
 
En estos casos suele describirse el tipo de calendario utilizado en el elemento [`<calendar>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-calendar.html) en el TEI Header.
 
Podemos, además, especificar la hora con el elemento [`<time>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-time.html) que suele también incluir el atributo `@when` para regularizar la forma:
 
```xml
<time when="08:48:00">8:48</time>
```
 
## Números y medidas
 
En lo que toca a los números y las medidas, se utilizan los elementos [`<num>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-num.html), para cualquier tipo de número (y a veces acompañados de los `@type`, `@value`), y [`<measure>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-measure.html) para marcar una cantidad (seguido opcionalmente de los atributos `@type`, `@quantity`, `@unit`, `@comodity`).
 
```xml
<num value="52">LII</num>
<num type="cardinal" value="15">quince</num>
<num type="percentage" value="20">veinte por ciento</num>
<num type="ordinal" value="6">6º</num>
<measure type="peso"><num>4</num> quilos de harina </measure>
```
 
# 7. Notas
 
En muchos casos, podemos encontrarnos con notas o anotaciones de naturaleza diversa. El elemento para codificarlas es [`<note>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-note.html), que sirve tanto para las que se encuentran en el texto impreso como las que son añadidas por el editor digital.
 
El elemento `<note>` tiene una serie de atributos que nos serán de gran utilidad, entre ellos destacamos:
 
* `@type`: permite caracterizar la nota en cuestión, si se trata de una nota al margen, de una nota a pie de página, etc.
* `@place`: es especialmente útil cuando se transcribe un manuscrito que posee notas en los márgenes; así por ejemplo podemos indicar la localización física de la nota.
* `@xml:id`: se utiliza, como hemos visto, para dar un identificador único a la nota en cuestión, de manera que podamos referirnos a esta con facilidad y crear, si lo deseamos, un enlace a la misma
* `@target`: lo utilizaríamos para conectar la referencia con la nota o viceversa.
 
Las notas pueden marcarse de dos maneras diferentes; una opción es situarla donde aparece la referencia a la misma en el cuerpo del texto (Opción 1); la otra consiste en crear una zona separada (una `<div type=“notas”>` por ejemplo) y apuntar a la referencia a través del `@target`:
 
Opción 1:
 
```xml
<head>Historia y organización<note n="1">Todas las discusiones e informaciones relativas a TEI desde sus inicios se encuentran en el repositorio de la lista TEI</note></head>
```
 
Opción 2:
 
```xml
<head>Historia y organización<ref target="nota1" xml:id="referencia1">1</ref></head>
....
[...]
<div type="notas">
<note xml:id="nota1" target="#referencia1">Todas las discusiones e informaciones relativas a TEI desde sus inicios se encuentran en el repositorio de la lista TEI </note>
</div>
```
 
# 8. Práctica: Codificación de un texto en prosa
 
Este ejercicio consiste en el marcado de un texto en prosa, concretamente, el inicio de la novela de *El Quijote* en una edición facsímil que se halla en la Biblioteca Virtual Miguel de Cervantes:
 
> [Miguel de Cervantes], *El ingenioso hidalgo don Quijote de la Mancha*, compuesto por Miguel de Cervantes Saavedra; edición ilustrada con las notas de Pellicer, Clemencín y otros, Madrid: Lib. Española; Barcelona: Plus Ultra, 1857. <http://bib.cervantesvirtual.com/FichaObra.html?Ref=14052&portal=0>
 
Este ejercicio se compone de tres partes: el enunciado, el texto a codificar y la imagen correspondiente. 
 
## Enunciado
 
1. Primero crea un documento XML-TEI con su declaración XML, elemento raíz, `<teiHeader>`, y `<text>`.
2. Completa los elementos obligatorios del encabezado (puedes repasarlos en la [lección 3](https://tthub.io/aprende/tutorial/edicion-y-publicacion-textos-tei/leccion3/encabezado_teiheader) con la información sobre la fuente que antes indicamos.
3. En el elemento `<body>` incluye el texto propiamente dicho. En resumen, los elementos que debes marcar a partir de la imagen son los siguientes:
 
* Título o encabezado general de la obra: "Don Quijote de la Mancha"
* Título de nivel 2: "Parte Primera"
* Título de nivel 2: "Capítulo Primero"
* Subtítulo del nivel 2: “Que trata de la condición y ejercicio del famoso hidalgo Don Quijote de la Mancha”
* El texto en prosa: “En un lugar de la Mancha...”
* Paginación
* Nota a pie de página
 
Estos son los elementos que deberemos marcar según las directrices de la TEI, utilizando los elementos vistos hasta ahora.
 
Aquí van unas pistas:
 
4. Para cada uno de los niveles deberemos crear una división, todas ellas anidadas según su jerarquía. Utiliza para ello el elemento `<div>` y añade un `@type` para especificar cada uno de estos niveles.
 
5. A continuación, copia el texto que se os ofrece más abajo en su `<div>` correspondiente. Para ello, utiliza el elemento `<head>` para todos los títulos, incluido el argumento del primer capítulo. Emplea el elemento `<p>` para incluir el texto “En un lugar de la mancha...”, aunque el párrafo no termine allí.

6. Marca el principio y el final de las páginas con `<pb/>` (*page break*) acompañado de su atributo `@n` con el valor del número de la página que viene a continuación (números 57 y 58). Si deseas realizar un marcado aún más granular, también puedes añadir los `<lb/>` (*line begining*) al comienzo de cada línea de la fuente impresa.

7. Marca los diferentes nombres que aparecen en el texto, ya sean nombres propios (`<persName>`) o de lugar (`<placeName>`), puedes intentar utilizar el atributo `@ref` para referenciarlos con un diccionario de autoridades como VIAF, pero ten en cuenta que en ocasiones puedes toparte con nombres que no aparecen listados en estos diccionarios.

8. Puedes añadir otros elementos que creas oportuno, como por ejemplo las notas a pie de página, colocando una `<div type="notas">` en el elemento `<back>`.

9. Comprueba que el documento esté bien formado y sea válido.

## El texto a codificar
 
```
Don Quijote de la Mancha
Primera parte
Capítulo I
Que trata de la condición y ejercicio del famoso hidalgo Don Quijote de la Mancha
En un lugar de la Mancha, de cuyo nombre no quiero acordarme, no ha mucho tiempo que vivía un hidalgo de los de lanza en astillero, adarga antigua, rocín flaco y galgo corredor. Una olla de algo más vaca que carnero, salpicón las más noches, duelos y quebrantos los sábados, lantejas los viernes, algún palomino de añadidura los domingos, consumían las tres partes de su hacienda (1). El resto della concluían sayo de velarte, calzas de velludo para las fiestas, con sus pantuflos de lo mesmo, y los días de entresemana se honraba con su vellorí de lo más fino. Tenía en su casa una ama que pasaba de los cuarenta, y una sobrina que no llegaba a los veinte, y un mozo de campo y plaza, que así ensillaba el rocín como tomaba la podadera. Frisaba la edad de nuestro hidalgo con los cincuenta años; era de complexión recia, seco de carnes, enjuto de rostro, gran madrugador y amigo de la caza. Quieren decir que tenía el sobrenombre de Quijada, o Quesada, que en esto hay alguna (...)
(1) Cervantes nota la económica mezquindad con que vivían los hidalgos manchegos, convirtiendo en salpicón para cena los restos de carne de la comida (...)
```
 
## La imagen del texto
 
![Imagen facsímil](https://raw.githubusercontent.com/tthub-repo/ejercicios/master/img/Quijote_1.jpg)


