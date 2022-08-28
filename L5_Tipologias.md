---
title: La codificación de tipologías textuales (prosa, poesía, drama, fuentes primarias y edición crítica)
author: Susanna Allés Torrent
date: 2019
layout: default
lang: es
---

# {{ page.title }}
## {{ page.author }}

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4555173.svg)](https://doi.org/10.5281/zenodo.4555173)

Esta lección ofrece la oportunidad de trabajar con más detalles con algunos módulos de la Text Encoding Initiative y algunas de las tipologías textuales más comunes. Aun así, es importante retener que para una información completa debemos siempre dirigirnos a las Guías directrices. Sólo así obtendremos una información detallada sobre las restricciones y el uso adecuado de los elementos, su estructura y su semántica.

# I. Prosa

Las [*Guías directrices*](https://tei-c.org/guidelines/p5/) de TEI no tienen un módulo específico para la codificación de prosa, pues se trata de un término algo genérico y difícil de definir. La mayoría de los elementos utilizados para codificar textos en prosa pertenecen al módulo [core](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/CO.html) y [textstructure](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/DS.html), es decir, los elementos que aparecen integrados en la estructura TEI por defecto y que explicamos en la [Estructura básica y elementos comunes de los documentos XML-TEI (L3)](https://tthub.io/aprende/l3-basicos-tei/).

Al afrontar la codificación de un texto, debemos, en primer lugar, llevar a cabo un análisis del documento, aislando las unidades estructurales de las que se compone. Partamos de un ejemplo concreto y veamos de qué manera podría ser codificado:

![Análisis estructural de un texto \label{L5_estructura}](https://tthub-repo.github.io/lecciones/img/L5_001.png)

En la Figura \ref{L5_estructura} tenemos diferentes elementos que deberemos marcar, como
por ejemplo:

* Las divisiones que corresponden a la primera parte, a los apartados (1, 2...) y a los subapartados (1.1., 1.2., etc.)
* Los títulos o encabezados
* Los párrafos
* Las citas bibliográficas
* Las listas
* Los números de página
* Las referencias cruzadas

A partir de aquí, la idea consiste en encontrar un elemento TEI que responda a cada uno de estos conceptos y expresarlo tal y como proponen las *Guías directrices*.

## [`<div>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-div.html) (divisiones)

Generalmente, las diferentes partes del texto se delimitan con un elemento genérico llamado `<div>`; de esta manera podemos crear una serie de divisiones jerárquicas tales como partes, capítulos, subcapítulos, secciones, subsecciones, etc. Debemos siempre recordar que las `<div>` pueden anidarse unas dentro de otras y pueden contener
prácticamente todos los otros elementos TEI.

Es muy frecuente que el elemento `<div>` conlleve, además, diversos
atributos, entre ellos:

* `@type` para especificar y caracterizar el tipo de división.
* `@n` para otorgarle una numeración precisa, aunque no es obligatorio pues el procesador puede localizar fácilmente su orden de aparición a partir del elemento padre.

## [`<p>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-p.html) (párrafos) y [`<ab>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-ab.html) (bloques anónimos)

El elemento `<p>` indica un párrafo y puede aparecer en cualquier tipo
de texto. Los párrafos no pueden anidarse unos en el interior de los otros,
sino que deben situarse consecutivamente y, normalmente, aparecen en el
interior de un elemento `<div>`.

A veces una sección textual no corresponde exactamente a la noción de
párrafo, y en ese caso podría utilizarse el elemento `<ab>` (anonymous
block). Por ejemplo, en nuestro documento, podríamos marcar el texto
introductorio con `<ab>` y relegar el elemento `<p>` para los párrafos
de los apartados y subapartados.

## [`<head>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-head.html) (títulos y encabezados)

Los encabezados y títulos de cualquier tipo se marcan con el elemento
`<head>` que puede conllevar, como en los casos anteriores, diversos
atributos, como `@type`, para indicar el tipo de título.

En nuestro documento, se podrían codificar como `<head>` todo lo que
aparece en negrita y que hemos incluido en los cuadros verdes. Ahora
bien, si quisiéramos clasificarlos en vista, por ejemplo, de una
presentación podríamos establecer tipologías diferentes:

```xml
<head type="Principal">Unidad 1</head>
<head type="parte">PARTE I</head>
<head type="apartado">1. Introducción</head>
```

Aun así, no sería ni mucho menos obligatorio porque los diversos `<head>` son localizables por el procesador a partir del elemento del que forman parte, de manera que cada `<head>` podría tener una presentación diferente en función del elemento padre al que pertenece.

## [`<cit>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-cit.html) (citas)

Las citas pueden ser de muchos tipos diferentes, pero las más habituales son aquellas en que se reproducen de manera literal las palabras de otra fuente, acompañadas de la indicación bibliográfica. En estos casos, se utiliza el elemento `<cit>` que debe estar formado, a su vez, por `<quote>` que encierra propiamente las palabras de la cita, y por `<bibl>` que debe contener la referencia bibliográfica:

```xml
<cit>
	<quote>The TEI Guidelines for Electronic Text Encoding and Interchange define and document a markup language for representing the structural, renditional, and  conceptual features of 
	</quote> 
	<bibl>TEI Consortium</bibl>
</cit>
```

En un trabajo en prosa, y especialmente en monografías y trabajos de investigación, la bibliografía suele codificarse separadamente, tal y como lo haríamos tradicionalmente. Puede ir incluida en el `<teiHeader>`, pero también en el `<front>`, `<back>` o incluso dentro de `<text>` creando una división especial, del tipo:

```xml
<div type="bibliografia">
```

Cada ítem bibliográfico debe tener su identificador (`@xml:id`) para que
pueda ser fácilmente localizable y recuperable. De esta manera, cuando
en el cuerpo del texto nos aparezca una cita de ese ítem bibliográfico
nos referimos a él con el atributo `@corresp` al interior del elemento
`<bibl>`:

```xml
<bibl corresp="#Guidelines">TEI Consortium</bibl>
```

## [`<list>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-list.html) (listas)

En los textos en prosa aparecen en muchos casos listas de elementos que, en TEI, deben marcarse con el elemento `<list>`, y cada uno de los ítems se codifica con el elemento `<item>`.

Si a cada ítem lo antecede un título podríamos utilizar `<label>`; pero, quizás, lo más interesante sean los diferentes tipos de listas que podemos crear a partir del atributo `@type`, para indicar el tipo de contenido (TEI propone como valores: `gloss`, `index`, `instructions`, `litany`, `syllogism`), y los atributos `@rend` o `@style` para determinar el tipo de presentación, donde los valores propuestos son: `numbered`, `inline`, `bulleted`, `simple`.

## Referencias cruzadas

Es también habitual que en un texto en prosa nos encontremos con referencias cruzadas que apunten al interior del documento o a una fuente externa. Los elementos para indicar este tipo de referencias y enlaces son [`<ref>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-ref.html) y [`<ptr/>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-ptr.html). La diferencia básica entre los dos es que el primero puede tener contenido y corresponde en realidad al típico enlace tal cual estamos acostumbrados a ver, mientras que `<ptr/>` (pointer) es un elemento vacío e indica sólo que en ese punto del texto aparece algo que crea un enlace, como por ejemplo un tipo concreto de imagen.

El posible resultado final -recordad que no hay una sola manera correcta de codificar- para un texto en prosa es el que encontraréis en el [Ejemplo en prosa (L5_Ejemplo_prosa.xml)](https://github.com/tthub-repo/ejemplos/blob/master/L5_Ejemplo_prosa.xml).

## Ejemplos

Para ver otros ejemplos de prosa, consultad el corpus en abierto de
novelas españolas y latinoamericanas en el CLiGS textbox:

* [Collection of 19th Century Spanish-American Novels (1880-1916)](https://github.com/cligs/textbox/blob/master/spanish/novela-hispanoamericana), Ulrike Henny-Krahmer (ed.) (24 novelas)

* [Corpus of Spanish Novels from 1880-1940](https://github.com/cligs/textbox/blob/master/spanish/novela-espanola), José Calvo Tello (ed.) (39 novelas)

* [Corpus of Spanish Short Stories from 1880-1940](https://github.com/cligs/textbox/blob/master/spanish/cuentos-espanoles), José Calvo Tello (ed.) (20 colecciones de narraciones breves y 302 narraciones)

Sugiero también que sigáis el tutorial de la parte correspondiente de *TEI By Example*:
[Module 3: Prose](http://teibyexample.org/modules/TBED03v00.htm)

# II. Poesía 

Centrémonos ahora en los elementos básicos para codificar composiciones en verso y véamos cómo funciona el vocabulario propuesto por TEI. En el apartado de [6. Verse](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/VE.html) de las *Guías directrices* se encuentra información mucho más detallada. 

Tomemos ahora este soneto de Federico García Lorca:

> Tengo miedo a perder la maravilla  
> de tus ojos de estatua y el acento  
> que de noche me pone en la mejilla  
> la solitaria rosa de tu aliento. 
 
> Tengo pena de ser en esta orilla  
> tronco sin ramas; y lo que más siento  
> es no tener la flor, pulpa o arcilla,  
> para el gusano de mi sufrimiento.  

> Si tú eres el tesoro oculto mío,  
> si eres mi cruz y mi dolor mojado,  
> si soy el perro de tu señorío,  

> no me dejes perder lo que he ganado  
> y decora las aguas de tu río  
> con hojas de mi otoño enajenado.  

La totalidad del poema suele contenerse en el elemento [`<lg>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-lg.html) (line
group), mientras que el título, una vez más, se sitúa en el interior de un
elemento `<head>`; cada uno de los versos se codifica con el elemento
que indica la línea: [`<l>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-l.html). Así mismo, para marcar las estrofas también
se utiliza `<lg>`, pues permite la anidación de otros elementos
idénticos en su interior.

El elemento `<lg>` puede poseer una serie de atributos, tanto a nivel de
poema, como a nivel de estrofa, entre los cuales podemos destacar:

* `@type` para indicar de qué tipo de composición se trata
* `@rhyme` para indicar el tipo de rima de la estrofa
* `@n` para señalar, por ejemplo, el número de estrofa
* `@xml:id` para otorgar un identificador a cada verso

También el verso (`<l>`) puede tener sus atributos:

* `@n` para indicar el número del verso
* `@rhyme` para indicar la rima del verso
* `@xml:id` para otorgar un identificador a cada verso

El vocabulario TEI prevé un elemento específico para codificar las rimas: [`<ryhme>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-rhyme.html); este puede aparecer tanto a final de verso como en su interior, donde sea que aparezca la rima:

```xml 
<lg type="cuarteto" n="1">
	<l n="1">Tengo miedo a perder la marav<rhyme>illa</rhyme></l>
	<l n="2"> de tus ojos de estatua y el ac<rhyme>ento</rhyme></l>
	<l n="3"> que me pone de noche en la mej<rhyme>illa</rhyme></l>
	<l n="4">la solitaria rosa de tu ali<rhyme>ento</rhyme>.</l>
</lg>
```

Además, el elemento `<rhyme>` puede contener el atributo `@label` para señalar el tipo de rima, normalmente indicado con una letra del
alfabeto:

```xml
marav<rhyme label="a">`illa`</rhyme>
```

Pero también puede indicarse en el interior del elemento `<div>`, `<lg>`
e incluso `<l>`:

```xml
<lg type="soneto" rhyme="ababababcdcdcd"> 
	<head>Soneto de la dulce queja</head> 
	<lg type="cuarteto" n="1" rhyme="abab">
		<l n="1" rhyme="a">Tengo miedo a perder la marav<rhyme>illa</rhyme></l>
		<l n="2" rhyme="b"> de tus ojos de estatua y el ac<rhyme>ento</rhyme> </l>
		<l n="3" rhyme="a"> que me pone de noche en la mej<rhyme>illa</rhyme> </l>
		<l n="4" rhyme="b">la solitaria rosa de tu ali<rhyme>ento</rhyme>.</l>
	</lg>
	<!-- más estrofas... -->
<lg>
```

En el caso que apareciera el nombre del poeta, podríamos codificarlo en el interior del elemento [`<signed>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-signed.html).

Si tuviéramos una serie de poemas, las estrategias a seguir podrían ser
varias pero la más sencilla sería marcar cada poema independientemente
en un elemento `<lg>`:

```xml
<div type="poemas">
	<lg type="poema" n="1">
		<head>poema 1</head>
          <lg>
            <l>verso 1</l>
            <l>verso 2</l>
            <l>verso 3</l>
          </lg>
	</lg>
	<lg type="poema" n="2">
          <head>poema 1</head>
          <lg>
            <l> verso 1</l>
            <l>verso 2</l>
            <l>verso 3</l>
          </lg>
	</lg>
	<lg type="poema" n="3">
          <head>poema 1</head>
          <lg>
            <l>verso 1</l>
            <l>verso 2</l>
            <l>verso 3</l>
          </lg>
	</lg>
</div>
```
Encontraréis otro ejemplo de marcado en nuestro Repositorio de ejemplos en GitHub: [Ejemplo en verso](https://github.com/tthub-repo/ejemplos/blob/master/L5_ejemplo_poema.xml). 

Existen muchos otros elementos relacionados con las composiciones
métricas, para más detalles os remito al módulo correspondiente [6. Verse](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/VE.html). Así
también, para completar esta sección, os dejo el enlace a la sección de
[Module 4: Poetry](https://teibyexample.org/modules/TBED04v00.htm) del *TEI By Example*

# III. Drama

Los textos dramáticos se caracterizan por tener una estructura más bien fija y unos elementos recurrentes: actos, escenas, acotaciones, indicaciones escénicas, diálogos, etc.

Las *Guías directrices*, al igual que sucedía con las obras en verso, dedica un módulo específico a las obras dramáticas (véase [7. Performance texts](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/DR.html), que os he dejado en formato pdf en la sección documentos.

En primer lugar, es necesario crear la estructura general en la que acomodar el texto. Tal y como hemos procedido en las otras ocasiones, se podría establecer una división general para cada una de las escenas y para cada uno de los actos o jornadas, añadiendo un atributo `@type` para definirlas:

```xml
<div type="acto" n="1">
	<head>Acto Primero</head>
	<div type="escena">
		<head>Escena I</head>
          <!-- ... -->
	</div>
</div>
<div type="acto" n="2">
	<head>Acto Segundo</head>
	<div type="escena">
		<head>Escena I</head>
          <!-- ... -->
</div>
```

Cada una de las divisiones puede o no ir acompañado de un título,
elemento aceptado en todos los documentos TEI.

Para los diálogos se utilizan los elementos [`<sp>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-sp.html) (speech) que están
constituidos de la persona que habla [`<speaker>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-speaker.html) y del diálogo en sí,
normalmente marcado en un simple `<p>`, aunque nada impediría que se
utilizara `<l>` o `<lg>`, especialmente en aquellos casos en que se
tratara de una versificación; o incluso podría también utilizar el
elemento `<seg>`, pero en ningún caso el texto podría ir directamente
dentro del elemento `<sp>` sin estructurar. Un diálogo quedaría así:

```xml
<sp who="#personaje1">
	<speaker>Personaje 1</speaker> Diálogo
</sp>
<sp who="#personaje2">
	<speaker>Personaje 2</speaker> Diálogo
</sp>
```

En lo que concierne los personajes es importante crear de antemano una lista de todos los personajes que intervienen y otorgarles un identificador. Esta información puede colocarse o bien en una `<div>` creada a propósito, o bien (más recomendable) en el elemento `<front>`, que precede el `<body>`. Allí podríamos incluir dicha lista gracias al elemento `<castlist>`:

```xml
<front>
      <castList>
        <head>Personajes</head>
        <castItem>
          <role xml:id="#personaje1">Personaje 1</role> <roleDesc>Descripción del personaje 2</roleDesc>
        </castItem>
        <castItem>
          <role xml:id="#personaje2">Personaje 2</role> <roleDesc>Descripción del personaje 2</roleDesc>
        </castItem>
      </castList>
</front>
```

De esta manera cada vez que un personaje hable se podrá marcar en el interior de `<sp>` con el atributo `@who`, para que todas sus intervenciones sean fácilmente localizables. De hecho, se podría eliminar la etiqueta `<speaker>` y recuperar la abreviación del
personaje justamente a través del identificador que aparece como valor en el atributo `@who` en el interior de `<sp>`. Es decir que podríamos expresar lo mismo de esta forma:

```xml
<sp who="#personaje1">Diálogo</sp>
<sp who="#personaje2">Diálogo</sp>
```

Las indicaciones dramáticas o acotaciones, aquellas normalmente realizadas por el dramaturgo, pueden incluirse dentro del elemento [`<stage>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-stage.html). También aquí se prevé la opción de añadir un atributo `@type` para caracterizar las diferentes acotaciones o tipos de indicaciones, por ejemplo:

```xml
<sp who="#personaje1">Diálogo</sp>
<sp who="#personaje2">Diálogo</sp>
<stage type="personajes">Descripción de los personajes que se encuentran en la escena.</stage>
<stage type="decorado">Descripción del decorado en la escena.</stage>
```

En el interior del elemento `<stage>` podemos utilizar otros elementos que
pueden sernos útiles en alguna ocasión como por ejemplo:

* [`<move>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-move.html): para indicar los movimientos de los personajes. Podríamos incluso especificar los movimiento con el atributo `@type`, que conlleva unos valores predifinidos por defecto de entrada, salida y en escena: `entrance` o `exit` y `onStage`; así también podemos añadir el atributo `@who` para identificar fácilmente de qué personaje se trata y `@where` para señalar hacia dónde es el movimiento.
* [`<sound>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-sound.html): para describir fenómenos de sonido, añadiendo si es necesario el atributo `@type`.
* [`<view>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-view.html): para describir el contexto visual de una parte del escenario, tal y como lo debe visualizar el espectador.
* [`<camera>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-camera.html) para dar indicaciones al cámara en el caso de grabaciones video, como películas.
* [`<caption>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-caption.html) para recoger las palabras que deberán proyectarse en pantalla.
* [`<tech>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/examples-tech.html) otras informaciones técnicas.

En el [Repositorio de ejemplos en GitHub](https://github.com/tthub-repo/ejemplos/) encontraréis un [ejemplo sencillo de codificación](https://github.com/tthub-repo/ejemplos/blob/master/L5_ejemplo_drama.xml) y otro ejemplo con el inicio de una obra dramática en verso de [Lope de Vega, *Amar sin saber a quien*](https://github.com/tthub-repo/ejemplos/blob/master/L5_ejemplo_drama_Lope_Amar_sin_saber_a_quien.xml). Mirad la reproducción digital que aparece en la [Biblioteca Cervantes Virtual](http://bib.cervantesvirtual.com/servlet/SirveObras/00363959755781806410046/ima0000.htm) y confrontadla con la codificación que he propuesto. [Aquí](http://bib.cervantesvirtual.com/servlet/SirveObras/01260529543471504100035/p0000001.htm#I_0_) encontraréis también una edición digital en HTML.

Recomiendo consultar otros recursos: en este caso el [Module 5: Drama](http://teibyexample.org/modules/TBED05v00.htm) en *TEI by Example*, poniendo especial atención a los [ejemplos](http://teibyexample.org/examples/TBED05v00.htm), y la consulta de las [*Guías directrices*](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/DR.html).

# IV. Fuentes primarias

Para la descripción de fuentes primarias existe un módulo específico: [11. Representation of Primary Sources](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/PH.html). Aun así, muchos de los elementos que nos servirán para la descripción de dichas fuentes pertenecen al módulo core o [Elementos comunes a todos los documentos TEI](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/CO.html). De igual manera, algunos de los elementos de este módulo son útiles si queremos llevar a cabo una edición crítica y la creación de un aparato de variantes, es decir, registrar las diferentes formas que pueda tener una palabra en manuscritos o impresos diferentes. Es importante, pues, tener en cuenta que al crear nuestro propio esquema necesitaremos seguramente integrar diferentes módulos, porque, aunque cada uno de ellos aspira a cubrir una fenomenología distinta, puede ser que nuestra tipología textual o, sencillamente, nuestro texto nos obligue a contemplar elementos que pertenecen a otros módulos.

Los elementos específicos del módulo sobre fuentes primarias son los
siguientes:

> [addSpan,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-addSpan.html)
> [am](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-am.html)[,
> damage,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-damage.html)
> [damageSpan,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-damageSpan.html)
> [delSpan,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-delSpan.html)
> [ex,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-ex.html)
> [facsimile,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-facsimile.html)
> [fw](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-fw.html)[,
> handNotes,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-handNotes.html)
> [handShift,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-handShift.html)
> [line,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-line.html)
> [listTranspose](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-listTranspose.html),
> [metamark,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-metamark.html)
> [mod](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-mod.html)[,
> redo](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-redo.html)[,
> restore,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-restore.html)
> [retrace,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-retrace.html)
> [sourceDoc,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-sourceDoc.html)
> [space,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-space.html)
> [subst,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-subst.html)
> [substJoin,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-substJoin.html)
> [supplied,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-supplied.html)
> [surface](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-surface.html)[,
> surfaceGrp](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-surfaceGrp.html)[,
> surplus](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-surplus.html)[,
> transpose,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-transpose.html)
> [undo,](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-undo.html)
> [zone](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-zone.html)

La fenomenología que podemos encontrarnos en una fuente primaria es realmente muy variada, desde adiciones, supresiones, errores, lecturas inciertas, lagunas, presencia de manos diferentes, cambios de tinta, notas y glosas, daño físicos, etc. Veamos a continuación algunos de los fenómenos y de los elementos que nos podrán ser más útiles.

## Descripción de la fuente primaria

Muy frecuentemente nos encontramos con documentos en los que ha habido algún tipo de intervención, como son las adiciones, cancelaciones o substituciones.

### a. Adiciones

Para las adiciones usaremos el elemento [`<add>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-add.html), que pertenece al módulo `Core`. Habitualmente se suele señalar con el atributo `@place` el lugar donde se ha producido dicha adición; por defecto, tenemos como valores: `above`, `below`, `bottom`, `end`, `inline`, `margin`, `opposite`, `overleaf`, `top`. Tomemos el ejemplo que aparece en la Figura \ref{L5_add} y veamos cómo lo podríamos codificar:

![Ejemplo de una adición. [*La primera y segunda parte de Plutharcho* / traducida por Alfonso de Palencia, Sevilla, 1491. BNE, Inc/314-Inc/315, f. 2r](http://bdh.bne.es/bnesearch/detalle/bdh0000005043) \label{L5_add}](https://tthub-repo.github.io/lecciones/img/L5_002.png)

Si quisiéramos sólo señalar que aparece una adición en el margen lo podríamos señalar de la siguiente manera:

```xml
doctrina: y en integridad de costumbres: 
e no poco dichoso en ser maestro de tan 
mentado <add place="margin">nombrado</add> 
emperador de los Romanos
```

### b. Cancelaciones o omisiones

En el caso de las supresiones, ya sea porqué se ha tachado una parte del texto ya sea porqué se ha omitido puede utilizarse [`<del>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-del.html) (deletion), que también corresponde al módulo core. Podemos añadir un atributo `@type` para caracterizar el tipo de cancelación o de omisión. Retomando el mismo ejemplo de la Figura \ref{L5_add}:

```xml
doctrina: y en integridad de costumbres:
e no poco dichoso en ser maestro de tan
<del>mentado</del>
<add place="margin">nombrado</add>
emperador de los Romanos
```

Además, el módulo de representación de fuentes primarias tiene otro elemento útil para aquellos casos en los que un fragmento largo ha sido omitido o cancelado. En estos casos, podríamos introducir el texto eliminado señalando el inicio del texto con el elemento
[`<delSpan>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-delSpan.html), acompañado del atributo `@spanTo` que apuntaría al punto de anclaje donde finaliza dicho fragmento. Véanse los ejemplos en las [*Guías directrices*](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/examples-delSpan.html%20).

### c. Substituciones

Cuando describimos la fuente primaria y nos encontramos con una corrección o substitución de cualquier tipo la marcaremos utilizando [`<del>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-del.html) y [`<add>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-add.html), agrupados en un elemento [`<subst>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-subst.html) si lo consideramos conveniente; también podemos especificar, con el atributo `@hand`, la mano responsable de dicha corrección y, con `@resp`, el editor que ha interpretado dicha corrección en la fuente primaria. Por ejemplo:

```xml
doctrina: y en integridad de costumbres:
e no poco dichoso en ser maestro de tan
<subst hand="#lector" resp="#SAT">
<del type="tachado">mentado</del>
<add place="margin">nombrado</add>
</subst> emperador de los Romanos
```

### d. Abreviaturas

Las abreviaturas pueden codificarse de maneras diferentes, la más
sencilla de las cuales es simplemente marcar la abreviatura dentro del
elemento [`<abbr>`](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-abbr.html). Pero en la mayoría de los casos, vale la pena indicar la forma expandida. En la Figura \ref{L5_abbr} (extraído del mismo folio anterior) podemos ver diferentes casos de abreviaturas:

![Ejemplos de abreviaturas. [*La primera y segunda parte de Plutharcho* / traducida por Alfonso de Palencia, Sevilla, 1491. BNE, Inc/314-Inc/315, f. 2r](http://bdh.bne.es/bnesearch/detalle/bdh0000005043) \label{L5_abbr}](https://tthub-repo.github.io/lecciones/img/L5_003.png)

Para ello, podemos proceder de la siguiente manera:

```xml
gua griega: <expan><abbr>quisiero</abbr><ex>n</ex></expan> dar obra a la tan prouechosa traducçion: cada uno dellos <expan><abbr>segu<ex>n</ex>d</abbr>
</expan> lo <expan><abbr>q</abbr><ex>ue</ex></expan> <expan><abbr>p</abbr><ex>er</ex>miti<abbr>a</abbr><ex>n</ex></expan> sus negoçios particulares de que no podian vacar: saluo breue <expan><abbr>tie<ex>m</ex>po</abbr></expan>. 
```

Como veis, cada abreviatura se sitúa en el interior de `<expan>`, mientras que la forma abreviada aparecen dentro de `<abbr>` y la expansión en el elemento `<ex>`. Esta opción puede llegar a cargar el marcado, por lo que a veces se prefiere este otro sistema en el que el elemento `<choice>` contiene la forma abreviada en el interior del elemento `<abbr>` y la forma expandida completa en el elemento `<expan>`:

```xml
lengua griega: <choice>
   <abbr>quisiero</abbr>
   <expan>quisieron</expan>
</choice> dar obra a la tan prouechosa traducçión: cada uno dellos <choice>
   <abbr>segud</abbr>
   <expan>segund</expan>
</choice> lo <choice>
   <abbr>q</abbr>
   <expan>que</expan>
</choice> <choice>
   <abbr>pmitia</abbr>
   <expan>permitian</expan></choice> sus negoçios particulares de que no podian vacar: saluo breve tiempo.
```

### e. Establecer diferentes manos de un manuscrito

Puede ser que en algunos casos nos encontremos con una fuente en la que aparecen manos diferentes y queramos describir los aspectos físicos o externos del manuscrito ([`physDesc`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-physDesc.html)); en el caso que queramos señalarlas, las codificaremos con el elemento [`<handNote>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-handNote.html) que se halla en el tei Header (/TEI/teiHeader/fileDesc/sourceDesc/msDesc/physDesc/handDesc). Además, le podemos atribuir un identificador propio a cada una de las manos:

```xml
<physDesc>
    <handDesc>
      <handNote xml:id="copista">El copista del manuscrito</handNote>
     <handNote xml:id="Lector">Un lector posterior que anotó el manuscrito</handNote>
    </handDesc>
</physDesc>
```

Así, podemos también señalar cuando se produce un cambio de mano en nuestra fuente, gracias al elemento [`<handShift>`](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-handShift.html). Por ejemplo, retomando un ejemplo anterior, podríamos señalar que la palabra griega fue añadida por un lector posterior:

```xml
quos <handShift resp="Lector">φἰλαγρος</handShift> appellant graeci.
```

### f. Daños

Si nuestro texto posee alguna zona dañada, frecuente en los manuscritos e impresos antiguos, podemos marcar dicho pasaje con el elemento [`<damage>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-damage.html). En su interior pueden utilizarse diversos atributos, como `@agent` para marcar el motivo del daño; o bien, en aquellos casos en que el daño atañe a un fragmento largo del texto podemos utilizar, como en `<delSpan>`, el elemento [`<damageSpan>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-damageSpan.html) con el atributo `@spanTo` que apuntará hacia el anclaje que indica el final del texto dañado.

### g. Otros elementos

En fin, hay otra serie de fenómenos que quizás queramos marcar como por
ejemplo:

* [`<fw>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-fw.html) (forme work) para indicar los números originales de las páginas, o incluso la numeración de los cuadernos o los hilitos de los encabezados.  
* [`<space>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-space.html) para indicar el espacio vacío en nuestra copia, como sucede en la Figura \ref{L5_space}

![Ejemplo de un espacio. Plutarco, *Vitae illustrium Virorum*, Nicolas Jenson, Venecia 1478, f. 115v. [Bayerische Staatsbibliothek, München, BSB-Ink P-626 - GW M34480](http://daten.digitale-sammlungen.de/0006/bsb00060043/images/index.html?id=00060043&groesser=&fip=193.174.98.30&no=&seite=236) \label{L5_space}](https://tthub-repo.github.io/lecciones/img/L5_004.png)

Podríamos codificar este fenómeno de la siguiente manera, señalando el espacio en blanco y aportando incluso la cantidad aproximada de las letras omitidas y el tipo de unidad (unit) del tipo de medida (caracteres, milímetros, centímetros, etc.).:

```xml
... quos 
<space quantity="10" unit="chars"/>
<supplied resp="#SAT">φἰλαγρος</supplied> 
appellant graeci. Hanc...
```

* [`<surplus>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-surplus.html): para indicar un texto en la fuente que el editor considera
superficial o redundante.

## Intervenciones editoriales

En general, podemos diferenciar aquellos fenómenos primarios que "objetivamente" encontramos en nuestra fuente, de aquellos otros, secundarios, que corresponden a una intervención del editor o del que codifica. En este sentido, podemos utilizar:

* [`<unclear>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-unclear.html) para la transcripción y la codificación de aquellas lecturas inciertas. Normalmente se acompaña del atributo `@resp` para indicar la responsabilidad del editor, y de `@reason` para señalar el motivo.
* [`<supplied>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/examples-supplied.html) indica el texto que ha sido restablecido por el editor. En el ejemplo de la Figura \ref{L5_space}, sabíamos qué palabra debía ir en el espacio en blanco con lo cual hemos podido marcarlo con este elemento, pues lo hemos restablecido. 
* En lo que concierne las correcciones en calidad de editores del texto electrónico, debemos utilizar los elementos `<sic>` y `<corr>`, y agrupados al interior de `<choice>`. En la siguiente Figura \ref{L5_corr}:

![Ejemplo de una corrección editorial. [*La primera y segunda parte de Plutharcho* / traducida por Alfonso de Palencia, Sevilla, 1491. BNE, Inc/314-Inc/315, f. 165v](http://bdh-rd.bne.es/viewer.vm?id=0000005043&page=1) \label{L5_corr}](https://tthub-repo.github.io/lecciones/img/L5_005.png)

```xml
... Aqueste mas luenga mente 
<choice>
   <sic>qua</sic>
   <corr resp="#SAT">que</corr>
</choice> la razon queria ...
```

## Reproducción facsimilar de la fuente

La práctica más habitual para conectar una página de la fuente primaria a su reproducción fotográfica es a través del uso del atributo `@facs`. Este atributo apunta hacia el conjunto o una parte de la imagen en cuestión que corresponde al contenido de elemento. Por ejemplo, si quisiéramos asociar cada página con su imagen respectiva, lo más sencillo sería incluir el atributo en el interior del cambio de página y crear una estructura de este tipo:

```xml
<TEI xmlns="http://www.tei-c.org/ns/1.0">
	<teiHeader>
	<!--... -->
	</teiHeader>
	<text>
		<body>
        	<pb facs="pagina1.png"/>
        	<!-- El texto de la página número 1-->
			<pb facs="pagina2.png"/>
      <!-- El texto de la página número 2-->
		<body>
	<text>
```

Las imágenes pueden también codificarse y anotarse describiéndolas en general o por zonas concretas y permitiendo, por ejemplo, una transcripción fina por línea. Este tema reviste algo más de complejidad, por lo que me remito a las mismas *Guías directrices* y a la [Representación de fuentes primarias](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/PH.html#PHFAX) para aquellos que quieran profundizar. 


# V. Edición crítica

Con el fin de llevar a cabo ediciones científicas, TEI propone un módulo para la creación de un aparato crítico: [12. Critical Apparatus](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/TC.html). Ahora nos centraremos básicamente en dos aspectos: cómo establecer una lista de manuscritos y cómo codificar las diferentes lecturas o variantes.

Los elementos del módulo relativo a la creación de un aparato crítico son:

> [app](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-app.html)
> [lacunaEnd](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-lacunaEnd.html)
> [lacunaStart](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-lacunaStart.html)
> [lem](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-lem.html)
> [listApp](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-listApp.html)
> [listWit](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-listWit.html)
> [rdg](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-rdg.html)
> [rdgGrp](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-rdgGrp.html)
> [variantEncoding](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-variantEncoding.html)
> [wit](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-wit.html)
> [witDetail](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-witDetail.html)
> [witEnd](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-witEnd.html)
> [witStart](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-witStart.html)
> [witness](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-witness.html)

## Lista de testimonios

La lista de los testimonios utilizados en la edición se sitúan en el `teiHeader`, más preceisamente en `fileDesc>sourceDesc`, en el interior del elemento `<listWit>`:

```xml
<listwit>
    <witness xml:id="testimonio1"></witness>
    <witness xml:id="testimonio2"></witness>
    <witness xml:id="testimonio3"></witness>
    <witness xml:id="testimonio4"></witness>
</listwit>
```

Cada manuscrito se codifica con el elemento `<witness>` y debe tener un identificador, de manera que cuando establezcamos las variantes textuales podamos referirnos a él de manera directa. Podemos utilizar otros elementos en su interior y escribir las informaciones básicas, como por ejemplo su referencia completa:

```xml
<listwit>
     <witness xml:id="NLV">Napoli, Biblioteca Nazionale Vittorio 
     Emanuele III di Napoli, ms. LV BB 20</witness>
     <witness xml:id="NXXX">Firenze, Biblioteca Nazionale Centrale 
     di Firenze, Magl. XXX, 154</witness>
     <witness xml:id="M211">Madrid, Biblioteca Nacional de España, 
     RES/423</witness>
</listwit>
```

## Variantes y aparato crítico

La codificación de una edición puede llevarse a cabo de muchas maneras diferentes. Lo más habitual, y más práctico, es marcar todas las lecturas del texto en un mismo documento y a medida que aparecen en el texto. El procedimiento recomendado sería el que vemos en este esquema:

```xml
<l>línea 1</l>
<l>línea 2
	<app>
		<rdg wit="#testimonio1">variante1</rdg>
		<rdg wit="#testimonio2">variante2</rdg>
		<rdg wit="#testimonio3">variante3</rdg>
	</app> </l>
<l>línea 3</l>
```

El marcado, pues, es el responsable de registrar todas las variantes textuales, cada una conectada con el identificador del testimonio correspondiente. De esta manera, si quisiéramos recuperar todas las variantes del `#testimonio1`, por ejemplo, el proceso es extremadamente fácil. Es decir, al mismo tiempo que marcamos las variantes, estamos en realidad construyendo el aparato crítico que recuperaremos a posteriori bajo la forma que deseemos.

Existe también la posibilidad de señalar el lema principal de entre las variantes textuales, es decir `<lem>` contiene el lema o variante que hemos aceptado en nuestro texto, mientras que `<rdg>` contiene solo una variante:

```xml
<l>línea 1</l>
<l>línea 2
	<app>
		<lem wit="#testimonio1">lema</lem>
		<rdg wit="#testimonio1">variante1</rdg>
		<rdg wit="#testimonio2">variante2</rdg>
		<rdg wit="#testimonio3">variante3</rdg>
	</app> 
</l>
<l>línea 3</l>
```

En estos casos `<lem>` contiene el lema o texto base de la variante textual (presente o no en algún testimonio), mientras que `<rdg>` (reading) contiene una sola lectura o variante textual de un manuscrito o impreso concreto.

Recomiendo, además de la sección [Aparato crítico en las *Guías directrices*](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/TC.html) y de los ejemplos en nuestro [Repositorio de Ejemplos en GitHub](https://github.com/tthub-repo/ejemplos/blob/master/L5_ejemplo_aparato_critico.xml), los materiales que aparecen en el [Module 7: Critical Editing](https://teibyexample.org/modules/TBED07v00.htm) de *TEI By Example*. Además, un excelente tutorial es el propuesto por Marjorie Burghart y Elena Pierazzo: [Digital Scholarly Editions: Manuscripts, Texts and TEI Encoding](https://teach.dariah.eu/course/view.php?id=32&section=0) (2017). En fin, para aquellos interesados en trabajar con aparatos críticos, pueden experimentar una posible visualización con el [TEI Critical Apparatus TextBox](http://teicat.huma-num.fr/) y consultar el trabajo realizado para la edición crítica digital de las [Soledades de Góngora](http://soledades.uni-koeln.de/#/critical?d=doc_1&e=critical) cuyos documentos XML-TEI están en [GitHub](https://github.com/arojascastro/soledades).

### Cita propuesta: 

Allés Torrent, Susanna (2019). "La codificación de tipologías textuales (prosa, poesía, drama, fuentes primarias y edición crítica)". *TTHUB. Text Technologies Hub: Recursos sobre tecnologías del texto y edición digital* (v.2). <https://tthub.io/aprende/l5-tipologias/> DOI: [10.5281/zenodo.4555173](https://doi.org/10.5281/zenodo.4555173)


[^1]: Para una primera aproximación, véase la lección [Las *Guías directrices*, su manejo y su traducción al español (L4)](https://tthub.io/aprende/l4-guias/).
