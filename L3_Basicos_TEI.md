---
title: Estructura básica y elementos comunes de los documentos XML-TEI[^1]
author: Susanna Allés Torrent
date: 2019
layout: default
lang: es
---

# {{ page.title }}
## {{ page.author }}
### {{ page.date }}
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.3531506.svg)](https://doi.org/10.5281/zenodo.3531506)

# I. Introducción

En esta lección nos centraremos en la estructura básica de los documentos XML-TEI, viendo solo aquellos elementos obligatorios e indispensables para empezar a trabajar con un documento TEI válido y bien formado.

Recapitulando algunas nociones básicas, recordaremos que XML-TEI es:

* un marco de trabajo basado en el lenguaje de marcado XML que define una serie de guías directrices y recomendaciones para marcar electrónicamente textos de cualquier disciplina y de cualquier época.
* al ser XML, TEI es a su vez independiente de cualquier programa y plataforma.
* el objetivo final es el de organizar y estructurar los textos electrónicamente de manera que puedan ser procesados y explotados por las computadoras.
* el tipo de marcado utilizado puede ser personalizado según las necesidades de cada texto o cada proyecto.

En la [lección *El lenguaje XML (eXtensible Markup Language) y algunos conceptos generales*](https://tthub.io/aprende/l2-xml/) explicamos los mecanismos que rigen el lenguaje XML, y ahora, debemos empezar a trabajar con las etiquetas que son propias del sistema TEI.

Un documento TEI es un documento XML de manera que sigue la misma sintaxis que cualquier otro documento XML. En esta imagen se reproduce la estructura mínima de un documento XML-TEI, que básicamente se compone de:

* el prólogo XML
* el encabezado
* el cuerpo del texto

![Estructura básica de un documento XML-TEI](https://tthub-repo.github.io/lecciones/img/L3_001.jpg)

En el prólogo del documento XML-TEI encontramos los elementos típicos de un documento XML:

* La declaración XML nos indica que se trata de un documento XML y que el tipo de codificación utilizado es el UTF-8.
* La asociación del modelo de esquema: en este caso se trata de un esquema RelaxNG (.rng). Es la misma asociación que establecían las DTD a través del DOCTYPE (como se ve en el [Ejemplo 2](https://github.com/tthub-repo/ejemplos/blob/master/L2_ejemplo-2.xml)). Gracias a esta indicación sabemos que este documento XML-TEI depende de un esquema concreto, el [TEI-Lite](http://www.tei-c.org/Guidelines/Customization/Lite/), que es un modelo minimalista de TEI donde se contemplan los elementos obligatorios y algunos de los más utilizados.

Acabado el prólogo, aparece el elemento raíz `<TEI>` que engloba la totalidad del documento. Aquí irán todos los otros elementos XML-TEI: el encabezado y el texto, con la siguiente estructura:

```xml
<tei xmlns="http://www.tei-c.org/ns/1.0">
     <teiheader>
     ....
     </teiheader>
     <text>
      ....
     </text>
</tei>
```

# II. Encabezado (teiHeader)

El documento XML-TEI consiste en dos grandes secciones: el encabezado que recibe el nombre de [`<teiHeader>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-teiHeader.html), y el del texto propiamente dicho, llamado [`<text>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-text.html).

En el encabezado encontramos los metadatos, es decir, las diferentes informaciones relativas al texto que estamos marcando.

Por ahora veamos cuáles son las partes obligatorias que debe tener cualquier documento XML-TEI:

```xml
<teiHeader>
    <fileDesc>
      <titleStmt>
        <title>Título del fichero XML</title>
      </titleStmt>
      <publicationStmt>
        <p>Información sobre la publicación digital</p>
      </publicationStmt>
      <sourceDesc>
        <p>Información sobre el texto original</p>
      </sourceDesc>
    </fileDesc>
</teiHeader>
```

En nuestro repositorio de ejemplos en GitHub, también encontraréis un ejemplo ([L3_documentoXML-TEI.xml](https://github.com/tthub-repo/ejemplos/blob/master/L3_documentoXML-TEI.xml)). 

El `<teiHeader>` tiene un solo elemento obligatorio, llamado [`<fileDesc>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-fileDesc.html). Este elemento es el responsable de contener tanto la información sobre el fichero XML-TEI con el que estamos trabajando, como los detalles de la fuente primaria:

* [`<titleStmt>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-titleStmt.html) contiene la información sobre el título del fichero propiamente dicho; éste a su vez debe ir dentro de un elemento más específico llamado `<title>`.
* [`<publicationStmt>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-publicationStmt.html) recoge la información sobre la publicación digital; la información debe ir organizada en párrafos: `<p>`
* [`<sourceDesc>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-sourceDesc.html) contiene la información de la fuente original.

Pongamos un ejemplo de la Biblioteca Virtual Miguel de Cervantes; imaginemos que estamos haciendo la edición digital de una edición antigua de la La Regenta (tal y como aparece en [este caso](http://www.cervantesvirtual.com/obra/la-regenta--1/). El encabezado podría marcarse de esta manera:

```xml
	<teiheader>
		<filedesc>
     		<titlestmt>
				<title>La Regenta, por Leopoldo Alas (Clarin); prólogo 
				de Benito Pérez Galdós</title>
			</titlestmt>
            <publicationstmt>
                <pubplace>Alicante</pubplace>        
                <publisher>Biblioteca Virtual Miguel de Cervantes</publisher>
                <date>2000</date>      
            </publicationstmt>
            <sourcedesc>La Regenta, por Leopoldo Alas (Clarin). Prólogo 
            de Benito Pérez Galdós, Madrid, Librería de Fernando 
            Fe 1900</sourcedesc>
        </filedesc>
    </teiheader>
```

Podéis encontrar este documento, en nuestro Repositorio de Ejemplos en Github ([L3_Ejemplo_novela.xml](https://github.com/tthub-repo/ejemplos/blob/master/L3_Ejemplo_novela.xml)). 
                                               
En el `<titleStmt>` hemos incluido el nombre del archivo que, en este caso, puede ser igual al de la obra original. Nada impediría que decidiéramos titularlo de una manera diferente, por ejemplo, “Edición digital de la Regenta (1900)”. En el elemento de `<publicationStmt>` aparece la información relativa a la publicación digital, en este caso el lugar (Alicante), el editor (Biblioteca Virtual Miguel de Cervantes) y el año de la publicación (2000).

Por otro lado, en el elemento `<sourceDesc>` debe aparecer la información de la obra original. Aquí se señala la información de la edición original de 1900. Podríamos, además, enriquecer las informaciones con la localización de la obra original, la división en tomos o cualquier otro dato que consideráramos pertinentes.

En las [*Guías directrices*](https://tei-c.org/guidelines/P5/) de TEI encontraréis toda la documentación relativa al [`teiHeader`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-teiHeader.html), así como múltiples ejemplos.

# III. Cuerpo del documento

El cuerpo del documento corresponde al elemento `<text>` que puede contener, a su vez, tres (sub)elementos:

* [`<front>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-front.html): se utiliza para marcar elementos paratextuales que preceden el texto, tales como prefacios, prólogos, cartas dedicatorias, una lista de personajes, etc. No es obligatorio.
* [`<body>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-body.html): se consagra al texto propiamente dicho del documento y es obligatorio.
* [`<back>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-back.html): puede utilizarse para añadir los apéndices, índices, cronologías, bibliografías, etc. No es obligatorio.

Siguiendo con el ejemplo anterior podríamos marcar el texto con la siguiente estructura:

```xml
<text>
    <front>
		<div type="prologo">
		</div> 
	</front>
	<body>
		<div type="tomo" n="1">
			<div type="capitulo" n="1"> ... </div>
			<div type="capitulo" n="2"> ... </div>
			<div type="capitulo" n="3"> ... </div>
		</div>
		<div type="tomo" n="2">
			<div type="capitulo" n="1"> ... </div>
			<div type="capitulo" n="2"> ... </div>
			<div type="capitulo" n="3"> ... </div>
		</div>
    </body>
</text>
```
En línea de máxima, como sucede con los nombres de los elementos y de los atributos, es mejor no utilizar acentos ni espacios tampoco en los valores de los atributos. 

# IV. Divisiones 

Uno de los elementos más utilizados en el cuerpo del documento es el de “división”, [`<div>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-div.html), que es utilizado para marcar cualquier tipo de sección estructural del texto, como tomos o volúmenes, libros, capítulos, partes, apartados, etc.

Del ejemplo anterior, se puede observar cómo hemos utilizado el elemento `<div>` para:

* caracterizar el “prólogo”.
* diferenciar los diferentes “tomos”.
* estructurar los diferentes “capítulos”.

Al afrontar cualquier estructuración de un texto, es pues un buen ejercicio empezar identificando las diferentes secciones del texto con `<div>` diferentes. Normalmente, cada una de las `<div>` tiene un atributo `@type` que ayuda a caracterizar esa sección en particular. El valor que puede conllevar `@type` es libre, con lo cual podemos utilizar el que mejor nos convenga (ej. libro, capítulo, escena, acto, poema, estrofa, etc.) y en la lengua que queramos.

Otro atributo muy utilizado es el `@xml:id` que asigna un identificador único a aquella sección particular del texto. Este mecanismo es imprescindible en el caso que queramos aislar determinadas porciones del texto. Por ejemplo, con este mecanismo al buscar una palabra podremos recuperar fácilmente en qué sección del libro estaba. El `@xml:id` se puede utilizar en una gran variedad de elementos, como bien podéis imaginaros es realmente útil en los casos de capítulos, líneas, versos, páginas, etc. Además, identificando las secciones de esta manera facilitamos el que otras partes del documento apunten a esa sección en concreto; de hecho, para la creación de “links”, este es un requisito indispensable: para crear un enlace necesitamos decirle al ordenador que vaya de un punto hacia otro, es decir, de un punto hacia un identificador concreto. Un elemento `<div>` con los atributos mencionados tendría esta forma:

```xml
<div type="tomo" xml:id="tomo_1" > ...</div>
```

El texto o la masa textual se incluye siempre al interior de elementos más concretos; no podemos añadir texto directamente dentro del elemento `<div>`. Por eso, en el caso que tengamos párrafos, utilizaremos el elemento `<p>`, en el caso que tuviéramos otros fragmentos de texto que no fueran párrafos, se podrían utilizar otros elementos más genéricos, como `<ab>` “anonymous block”, que indica cualquier unidad textual sin una semántica concreta (como es el caso, por ejemplo de “párrafo”, o “frase”).


# V. Elementos comunes de todo documento TEI

En primer lugar, conviene recordar que el sistema de codificación TEI se divide en módulos, cada uno destinado a una tipología textual: verso, drama, transcripciones de discurso, diccionarios, etc. Cada uno de estos módulos es descrito en las [*Guías directrices*](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/index.html). A su vez, los módulos pueden ser obligatorios o optativos. Así, los módulos obligatorios son cuatro: [`tei`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ST.html), [`core`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/CO.html), [`header`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/HD.html), [`textstructure`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/DS.html); sin estos no tendríamos un documento válido. Los módulos optativos, en cambio, responden a tipologías textuales concretas.

Ahora, veremos aquellos elementos generales y comunes en todos los documentos TEI, como pueden ser párrafos, cuestiones de puntuación o de tipografía, nombres, fechas, abreviaturas, listas, notas a pie de página o de otra naturaleza, indexación, entre otros aspectos. Todos estos elementos se encuentran explicados en la sección ["3. Elements Available in All TEI Documents"](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/CO.html) de las *Guías directrices*. 

Más arriba vimos aquellos elementos que constituían la estructura obligatoria y básica de un documento TEI. Vamos, aquí, a centrarnos en el módulo llamado «core», que contiene una serie de elementos o etiquetas que pueden utilizarse en cualquier documento, incluso en la versión más minimalista [TEI Lite](https://tei-c.org/guidelines/customization/lite/). La panorámica que ofreceremos no es completa, pero corresponde a los más utilizados.

Vamos a dividir los elementos en: Párrafos, Cuestiones de puntuación, Elementos tipográficos, Citas, Nombres, números, fechas, Listas, notas, anotaciones, indexación, referencias, y un último apartado con Otros elementos frecuentemente utilizados.

## Párrafos

El párrafo es la unidad más pequeña en la que un texto en prosa puede dividirse. El elemento utilizado para marcar los párrafos es `<p>`.

```xml
<p>El único defecto que hallan en mi es el de que estoy muy delgadito, a fuerza de estudiar. Para que engorde se proponen no dejarme estudiar ni leer un papel mientras aquí permanezca, y además hacerme comer cuantos primores de cocina y de repostería se confeccionan en el lugar. Está visto: quieren cebarme. No hay familia conocida que no me haya enviado algún obsequio. Ya me envían una torta de bizcocho, ya un cuajado, ya una pirámide de piñonate, ya un tarro de almibar.</p>
<p>Los obsequios que me hacen no son sólo estos presentes enviados a casa, sino que también me han convidado a comer tres o cuatro personas de las más importantes del lugar.</p>
<p>Mañana como en casa de la famosa Pepita Jiménez, de quien Vd. habrá oído hablar sinduda alguna. Nadie ignora aquí que mi padre la pretende.</p>
```
(Juan Valera, *Pepita Jiménez*, Cap. I)

En los casos, por ejemplo, que quisiéramos dividir ulteriormente un párrafo, podríamos utilizar otros elementos como [`<s>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-s.html) (segment) para dividir otro tipo de segmentos, como por ejemplo, las frases:

```xml
<s type="frase">El único defecto que hallan en mí es el de que estoy muy delgadito, a fuerza de estudiar.</s> 
<s type="frase">Para que engorde se proponen no dejarme estudiar ni leer un papel mientras aquí permanezca, y además hacerme comer cuantos primores de cocina y de repostería se confeccionan en el lugar.</s> 
<s type="frase">Está visto: quieren cebarme.</s> 
<s>No hay familia conocida que no me haya enviado algún obsequio.</s> 
<s type="frase">Ya me envían una torta de bizcocho, ya un cuajado, ya una pirámide de piñonate, ya un tarro de almíbar.</s>
```
(Juan Valera, *Pepita Jiménez*, Cap. I)

El elemento `<p>` puede contener una gran variedad de elementos en su interior, prácticamente todos los que veremos a continuación.

## Puntuación

De manera general, y especialmente en prosa, la puntuación del texto no suele codificarse; pero en algunos casos donde el marcado debe ser extremadamente sutil, se puede marcar. El elemento utilizado es:

* [`<pc>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-pc.html) (punctuation character): utilizado para codificar el punto, el signo de interrogación y de exclamación, los puntos suspensivos, las comillas (aunque podrían eliminarse si se utiliza `<q>` o `<quote>`), apóstrofes, paréntesis, etc.

```xml
<s>
<seg>Está visto<pc>:</pc></seg> 
<seg>quieren cebarme</seg><pc>.</pc>
</s>
```

La codificación de la puntuación puede ser interesante en aquellos casos en que se quiera dar fe de los diferentes cambios a lo largo de la historia. A veces, la ausencia o presencia de un punto, por ejemplo, puede cambiar el sentido.

## Elementos tipográficos

Todos los textos impresos poseen elementos tipográficos diversos como pueden ser la cursiva, la negrita, las versalitas, incluso fuentes diversas, tamaño de la fuente, etc. La naturaleza de estos elementos tipográficos en las fuentes escritas pueden ser de diversa naturaleza:

* una palabra o frase en una lengua extranjera, un arcaísmo, un barbarismo, una palabra técnica, etc.
* una palabra o frase sobre la que se quiere poner un énfasis especial, que se resaltaría al hablar.
* un palabra o frase que en realidad no forma parte del discurso del texto, como las referencias cruzadas, los títulos o los encabezados, etc.
* cadenas narrativas diferentes, como un monólogo interno o un comentario.
* la atribución a una referencia externa al texto, como un discurso directo o una citación.

Ahora bien, como explicamos anteriormente, el sistema TEI no se concentra tanto en la apariencia del texto como en señalar qué son las cosas. De esta manera, al encontrarnos, por ejemplo con un extranjerismo, quizás no nos interesará tanto señalar que aparece en cursiva, como indicar que se trata de una palabra extranjera. Sea cual sea la opción que se elija, TEI ofrece la posibilidad de marcar estos elementos tipográficos de una manera general, sin implicaciones semánticas. El elemento utilizado a tal propósito es `<hi>` (highlight), que por lo general suele tener un atributo `@rend` (rendition) que indica de qué manera aparece en el texto:

```xml
<hi rend="italic">Palabra o frase en cursiva</hi>
<hi rend="bold">Palabra o frase en negrita</hi>
<hi rend="small-caps">Palabra o frase en versalitas</hi>
```

El valor de los elementos es libre, con lo cual nada nos impide señalarlo en otra lengua, por ejemplo:

```xml
<hi rend="cursiva">Palabra o frase en cursiva</hi>
```

Podemos encontrar además otros elementos que responden a las tipografías diversas anteriormente mencionadas:

* [`<foreign>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-foreign.html) indica una palabra o frase perteneciente a otra lengua; normalmente posee el atributo `@xml:lang` para definir la lengua. Por ejemplo,

```xml
<p>El papa Francisco recuerda los conflictos activos en el mundo en la bendición 
<foreign xml:lang="lat">urbi et orbi</foreign></p>
```

```xml
Te espero en el <foreign xml:lang="en">lobby</foreign>
```

* [`<emph>`]() indica una palabra o frase a la que se atribuye un énfasis especial:

```xml
<p>Aquí, como en todas partes, la gente es muy aficionada al dinero. Y digo mal <emph>como en todas partes</emph>: en las ciudades populosas, en los grandes centros de civilización, hay otras distinciones que se ambicionan tanto o más que el dinero, porque abren camino y dan crédito y consideración en el mundo</p>
```

* [`<distinct>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-distinct.html) indica un término diferente lingüísticamente (arcaísmo, tecnicismo, dialectalismo, coloquialismo, etc.).
* [`<mentioned>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-mentioned.html) es utilizado para señalar una palabra mencionada o citada.
* [`<soCalled>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-soCalled.html) contiene una palabra o expresión respecto a la cual el autor manifiesta su rechazo de responsabilidad:

```xml
<p>El mencionado <soCalled>manuscrito</soCalled>, fielmente trasladado a la estampa, es como sigue.</p>
```

## Citas

La marcas tipográficas también pueden utilizarse, como es sabido, para señalar citas de diferente naturaleza, ya sea un pensamiento, un discurso indirecto o directo, o incluso una cita literaria o bibliográfica. TEI ofrece una gran variedad de elementos para señalar estos fenómenos entre los que destacan:

* [`<q>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-q.html) (quoted) puede utilizarse para marcar el estilo directo, un pensamiento o algún término técnico, normalmente en las fuentes escritas aparece entre comillas:

```xml
<p>Al día siguiente, Bioy me llamó desde Buenos Aires. Me dijo que tenía a la vista el artículo sobre Uqbar, en el volumen XXVI de la Enciclopedia. No constaba el nombre del heresiarca, pero si la noticia de su doctrina, formulada en palabras casi idénticas a las repetidas por él, aunque -tal vez- literariamente inferiores. Él había recordado:  <q xml:lang="en">Copulation and mirrors are abominable</q>. El texto de la Enciclopedia decía: <q>Para uno de esos gnósticos, el visible universo era una ilusión o (más precisamente) un sofisma. Los espejos y la paternidad son abominables (<foreign xml:lang="en">mirrors and fatherhood are hateful</foreign>) porque lo multiplican y lo 
divulgan.</q> Le dije, sin faltar a la verdad, que <q>me gustaria 
ver ese articulo</q>. A los pocos días lo trajo. Lo cual me sorprendió, 
porque los escrupulosos índices cartográficos de la Erdkunde de Ritter 
ignoraban con plenitud el nombre de Uqbar.</p>
```
(Borges, *Ficciones*)

* [`<said>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-said.html) (speech or thought) discurso hablado o pensamiento:

```xml
<p> Así es que un día ambas se quedaron atónitas y pasmadas cuando, después de varios requiebros, entre burlas y veras, D. Gumersindo soltó con la mayor formalidad y a boca de jarro la siguiente categórica pregunta:</p> 
<said>Muchacha, ¿quieres casarte conmigo?</said>
<p> Pepita, aunque la pregunta venía después de mucha broma, y pudiera tomarse por broma, y aunque inexperta de las cosas del mundo, por cierto instinto adivinatorio que hay en las mujeres y sobre todo en las mozas, por cándidas que sean, conoció que aquello iba por lo serio, se puso colorada como una guinda, y no contestó nada. La madre contestó por ella:</p>
<said>Niña, no seas mal criada; contesta a tu tío lo que debes contestar: Tío, con mucho gusto; cuando Vd. quiera.</said>
```
(J. Valera, *Pepita Jiménez*)

* [`<quote>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-quote.html) pasaje atribuido a una fuente externa:

```xml
<p> No conozco aún a Pepita Jiménez. Todos dicen que es muy linda. Yo sospecho que será una beldad lugareña y algo rústica. Por lo que de ella se cuenta, no acierto a decidir si es buena o mala moralmente; pero sí que es de gran despejo natural. Pepita tendrá veinte años; es viuda; solo tres años estuvo casada. Era hija de doña Francisca Gálvez, viuda, como Vd. sabe, de un capitán retirado <quote>Que le dejo a su muerte, Solo su honrosa espada por herencia,</quote> según dice el poeta. Hasta la edad de diez y seis años vivió Pepita con su madre en la mayor estrechez, casi en la miseria.</p>
```

* [`<cit>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-cit.html) se utiliza para citar de manera completa una referencia bibliográfica:

```xml
    <p>El pasaje nos recuerda al 
    <cit>
      <quote>"Arma virumque cano,..."</quote>
       <bibl>(<author>Virgilio</author>, 
      <title>Eneida</title>, I)</bibl>
    </cit></p>
```

## Nombres, números y fechas

En múltiples ocasiones podemos encontrar en los textos nombres (ya sean topónimos, antropónimos, etc.), números y fechas. TEI propone para ello una serie de elementos que nos serán de gran utilidad.

### Nombres

Un elemento general para codificar todo tipo de nombres o incluso frases es `<name>`; más adelante, veremos como existe un módulo específico para el marcado de nombres de lugar, de persona, etc. Otro elemento recurrente es `<rs>` (referring string) que indica un nombre con una denominación genérica o una cadena de referencia.

Los atributos más utilizados, a parte de `@xml:id`, son `@type` para especificarlos ulteriormente, y `@key` o `@ref` para referirse a un identificador concreto. Por ejemplo, supongamos esta frase: “Pepita Jiménez era hija de Francisca Gálvez quien la quería casar con D. Gumersindo”; la podríamos marcar de la siguiente manera:

```xml
<p><name xml:id="PJ">Pepita Jiménez</name> era hija de 
<name xml:id="FG">Francisca Gálvez</name> que la hizo casar con 
<name ref="#Gu">D. Gumersindo</name></p>
```

una vez establecidos los identificadores, podríamos referirnos a los personajes con facilidad en el fragmento que sigue:

```xml
<p>Era, con todo, tan inverosímil y tan desatinado el suponer que un hombre, que había pasado ochenta años sin querer casarse, pensase en tal locura cuando ya tenía un pie en el sepulcro, que ni la <rs ref="#FG">madre de Pepita</rs>, ni <name ref="#PJ">Pepita</name> mucho menos, sospecharon jamás los en verdad atrevidos pensamientos de <name ref="#Gu">D. Gumersindo</name>.</p>
```

### Fechas

En lo que concierne a las fechas, se utiliza el elemento [`<date>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-date.html) y se regulariza su formato (de manera que la máquina la interprete correctamente) al interior del `@when`, cuyo formato es: año-mes-día. He aquí algunos ejemplos.

```xml
<date when="1980-03-23">23 de marzo de 1980</date>
<date when="1980"> el año 1980</date>
<date when="1999-10">octubre de 1999</date>
<date when="--02-14">cada 14 de febrero</date>
<date from="2014-02-10" to="2014-02-20"> del 10 de febrero al 
20 de octubre de 2014</date>
```

Opcionalmente, se pueden especificar los diferentes sistemas de calendario (juliano, gregoriano, etc.) con `@calendar`:

```xml
<date when="1541" calendar="#juliano">1541</date>
```

En estos casos suele describirse el tipo de calendario utilizado en el elemento [`<calendar>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-calendar.html) en el TEI Header.

Podemos, además, especificar la hora con el elemento [`<time>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-time.html) que suele también incluir el atributo `@when` para regularizar la forma:

```xml
<time when="08:48:00">8:48</time>
```

### Números y medidas

En lo que toca a los números y las medidas, se reducen al uso de los elementos [`<num>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-num.html), para cualquier tipo de número (y a veces acompañados de los `@type`, `@value`), y de [`<measure>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-measure.html) para marcar una cantidad (seguido opcionalmente de los atributos `@type`, `@quantity`, `@unit`, `@comodity`).

```xml
<num value="52">LII</num>
<num type="cardinal" value="15">quince</num>
<num type="percentage" value="20">veinte por ciento</num>
<num type="ordinal" value="6">6º</num>
<measure type="peso"><num>4</num> quilos de harina </measure>
```

## Listas, notas, anotaciones, indexación, referencias

### Listas

Las listas suelen ser un fenómeno habitual en muchos de los textos impresos. Los elementos más comunes que pueden constituir una lista son los siguientes:

* [`<list>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-list.html) secuencia de ítems que conforman una lista.
* [`<item>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-item.html) un componente de una lista.
* [`<label>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-label.html) etiqueta asociada a un ítem.

```xml
<list>
	<head>Ingredientes:</head>
	<item n="1">Harina</item>
	<item n="2">Huevos</item>
	<item n="3">Azucar</item>
</list>
<list type="gloss">
  <head>Lista de medidas (traducción)</head>
  <label>height</label>
  <item>altura</item>
  <label>width</label>
  <item>ancho</item>
  <label>depth</label>
  <item>fondo</item>
</list>
```

Pueden también establecerse diferentes tipos de lista a través del atributo `@type`, que tiene estos valores por defecto:

* `bulleted`: ítems precedidos de puntos o marcas similare.
* `inline`: ítems presentados en prosa continua, sin saltos de página.
* `numbered`: ítems precedidos de un número.
* `simple`: ítems presentados como bloques, pero sin puntos ni números.

```xml
<list rend="numbered">
  <head>Lista de temas a estudiar</head>
  <item n="1">¿Qué es la TEI y qué aplicaciones prácticas tiene?</item>
  <item n="2">Principios fundamentales de un documento XML</item>
  <item n="3">La estructura básica de un documento TEI</item>
  <item n="4">Elementos generales a todos los documentos TEI (core)</item>
  <item n="5">...</item>
</list>
```

### Notas

En muchos casos, podemos encontrarnos con notas o anotaciones de naturaleza diversa. El elemento para codificarlas es [`<note>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-note.html), que sirve tanto para las que se encuentran en el texto impreso como las que son añadidas por el editor digital.

El elemento `<note>` tiene una serie de atributos que nos serán de gran utilidad, entre ellos destacamos:

* `@type`: permite caracterizar la nota en cuestión, si se trata de una nota al margen, de una nota a pie de página, etc.
* `@place`: es especialmente útil cuando se transcribe un manuscrito que posee notas en los márgenes; así por ejemplo podemos indicar la localización física de la nota.
* `@xml:id`: se utiliza, como hemos visto, para dar un identificador único a la nota en cuestión, de manera que podamos referirnos a esta con facilidad y crear, si lo deseamos, un enlace a la misma
* `@target`: lo utilizaríamos para conectar la referencia con la nota o viceversa.

Las notas pueden marcarse de dos maneras diferentes; una opción es situarla donde aparece la referencia a la misma en el cuerpo del texto (Opción 1); la otra consiste en crear una zona separada (una `<div type=“notas”>` por ejemplo) y apuntar a la referencia a través del `@target`:

Opción 1:

```xml
<head>Historia y organización<note n="1">Todas las discusiones e informaciones relativas entorno a TEI desde sus inicios se encuentran en el repositorio de la lista TEI</note></head>
```

Opción 2:

```xml
<head>Historia y organización<ref target="nota1" xml:id="referencia1">1</ref></head>
....
[...]
<div type="notas">
<note xml:id="nota1" target="#referencia1">Todas las discusiones e informaciones relativas entorno a TEI desde sus inicios se encuentran en el repositorio de la lista TEI </note>
</div>
```

### Indexación

En algunas ocasiones podemos también encontrarnos con índices de términos, para ello podemos utilizar estos dos elementos:

* [`<index>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-index.html) marca una entrada de índice, puede llevar `@indexName`; en su interior pueden anidarse diferentes índices.
* [`<term>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-term.html) marca un término en el interior del índice.

Puede ocurrir que la fuente original no tenga un índice, pero que queramos construir uno. Esto puede hacerse de diferentes maneras, una de ellas sería utilizando los dos elementos anteriores y marcar los términos que queramos introducir en un nuevo índice. Por ejemplo, imaginemos que queremos hacer un índice de personajes:

```xml
<index indexName="Personajes"><term xml:id="PJ">Pepita</term></index> tendrá veinte años; es viuda; sólo tres años estuvo casada. Era hija de doña <index indexName="Personajes"> <term xml:id="FG">Francisca Gálvez</term></index>, viuda, como Vd. sabe, de un capitán retirado.
```
De esta manera sería fácil autogenerar un índice con los nombres de los personajes, por ejemplo, con un simple script en XSLT.

### Enlaces y referencias

Una de las ventajas de crear un hipertexto es justamente la posibilidad que tenemos de conectar las diferentes secciones del texto a otras y establecer todo tipo de enlaces. En TEI los enlaces pueden realizarse de dos maneras, con los siguientes elementos:

* [`<ptr>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-ptr.html) (pointer) un indicador hacia otra localización
* [`<ref>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-ref.html) (reference) define una referencia hacia otra localización, normalmente contiene un texto que funciona como el enlace. Ambos suelen utilizar, entre otros, el atributo `@target` que toma la forma de una referencia URI.

## Otros elementos

Existen mucho otros elementos entre los cuales podríamos destacar los cambios editoriales, tales como los errores, correcciones, adiciones, supresiones, etc. y otros elementos pertenecientes a la estructura física del texto, como los saltos de línea, de página o de columna.

### Cambios editoriales

Como ocurre en la edición de fuentes escritas, a veces debemos señalar el proceso de constitución de un texto en sus diferentes fases (copistas, editor papel, editor digital, etc.). Para recoger las intervenciones editoriales disponemos de una serie de elementos básicos que podemos utilizar en todos los documentos TEI. Para entender la codificación de estos fenómenos debemos visualizar la intervención como una unidad en la que hay etapas o elementos diferentes. El elemento encargado de recoger estos marcados editoriales alternativos es [`<choice>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-choice.html), y puede utilizarse en los siguientes casos:

* Corrección de errores: ante un error, se utiliza el elemento `<sic>` para marcar el error aparente; con el elemento `<corr>`, en cambio, se recoge la corrección de dicho error:

```xml
<p>Hasta cinco mujeres han venido a verme que 
<choice>
   <sic>todos</sic><corr>todas</corr>
</choice> han sido mis amas y me han abrazado y besado.</p>
```

* Regularización de formas ortográficas: la forma original que aparece en el texto se marca con el elemento `<orig>`, mientras que su forma regularizada, con el elemento `<reg>`:

```xml
<choice>
   <orig>Comiença</orig>
   <reg>Comienza</reg>
</choice> la
<choice>
   <orig>ystoria</orig>
    <reg>historia</reg>
</choice>...
```

* Abreviatura: la forma abreviada aparece en el elemento `<abbr>`, mientras que la forma expandida bajo `<expan>`:

```xml
<p>...un largo 
<choice>
    <abbr>etc.</abbr>
     <expan>etcétera</expan>
</choice>
</p>
```

Hay otro tipo de intervenciones que pueden codificarse de manera aislada, como las adiciones, las eliminaciones, las omisiones, e incluso las lecturas dudosas:

* [`<add>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-add.html): adición al texto, como por ejemplo una glosa marginal.
* [`<del>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-del.html): una eliminación en el texto, como una tachadura.
* [`<gap>`](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-gap.html): indica un punto donde el material ha sido omitido; puede tener el atributo `@reason` para señalar el motivo.
* [`<unclear>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-unclear.html): indica una lectura dudosa.

### Milestones

Dentro de la categoría que las *Guías directrices* denominan “Milestone” encontramos diversos elementos que pueden indicar ciertas características físicas del documento. Entre estos elementos encontramos:

* [`<milestone>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-milestone.html): marca un punto límite separando cualquier tipo de sección de un texto.
* [`<gb>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-gb.html) (gathering begins) puede indicar el inicio o final de la folación de un manuscrito, por ejemplo donde empieza y donde acaba un cuaderno.
* [`<pb>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-pb.html) (page break): indica el cambio de página.
* [`<lb>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-lb.html) (line break): indica el cambio de línea.
* [`<cb>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-cb.html) (column break): indica el cambio de columna


# VI. Bibliografía

* Burnard, L. (2014), What is the Text Encoding Initiative. How to add intelligent markup to digital resources, Marserille: OpenEdition Press <https://books.openedition.org/oep/681>

## Tutoriales:

* "Module 1: Common Structure and Elements." *TEI by Example*, <http://teibyexample.org/modules/TBED01v00.htm>
* Schreibman, Susan & Roman Bleier. "[Text encoding and the TEI](https://teach.dariah.eu/course/view.php?id=23)". #dariahTeach. DH Teaching material, 2017.


### Cita propuesta: 

Allés Torrent, Susanna (2019). "Estructura básica y elementos comunes de los documentos XML-TEI". *TTHUB. Text Technologies Hub: Recursos sobre tecnologías del texto y edición digital*. <https://tthub.io/aprende/l3-basicos-tei/> DOI: [10.5281/zenodo.3531506](https://doi.org/10.5281/zenodo.3531506)



[^1]: Estos materiales fueron creados en el marco del certificado de [Experto Universitario en Humanidades Digitales](http://linhd.uned.es/p/experto-universitario-humanidades-digitales-2019/), ofrecido desde 2014 por el Laboratorio de Innovación en Humanidades Digitales de la Universidad Nacional de Educación a Distancia. 