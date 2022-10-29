---
title: Prosa II: elementos para textos expositivos
author: Susanna Allés Torrent, Gabriel Calarco, Gimena del Rio Riande
date: 2022
layout: default
lang: es
---
  
En la lección anterior comenzamos a ver algunos de los elementos de los módulos obligatorios de TEI para el marcado de textos en prosa. En esta segunda parte continuaremos profundizando en esta temática deteniéndonos en algunos elementos característicos de tipologías textuales en prosa diferentes a las novelas o cuentos, como los textos expositivos, en donde encontraremos elementos más específicos como listas, citas, notas y referencias cruzadas, así como los elementos comunes con los que ya estuvimos trabajando tales como párrafos y divisiones. 
 
# 1. Modelización
 
Al afrontar la codificación de un texto, debemos, en primer lugar, llevar a cabo un análisis del documento, aislando las unidades estructurales de las que se compone. Partamos de un ejemplo concreto y veamos de qué manera podría ser codificado:
 
![Análisis estructural de un texto](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L5_001.png)
 
En este caso tenemos diferentes elementos que deberemos marcar, como por ejemplo:
 
* Las divisiones que corresponden a la primera parte, a los apartados (1, 2...) y a los subapartados (1.1., 1.2., etc.)
* Los títulos o encabezados
* Los párrafos
* Las citas bibliográficas
* Las listas
* Las referencias cruzadas
* Un índice de términos específicos.
 
A partir de aquí, la idea consiste en encontrar un elemento TEI que responda a cada uno de estos conceptos y expresarlo tal y como proponen las *Guías directrices*.

# 2. Elementos más utilizados
 
## Divisiones
 
Para marcar los apartados y subapartados del texto utilizaremos el elemento `<div>`. Recordemos que las `<div>` pueden anidarse unas dentro de otras y pueden contener
prácticamente todos los otros elementos TEI, y puede complementarse con diversos atributos como:
 
* `@type` para especificar y caracterizar el tipo de división.
* `@n` para otorgarle una numeración precisa, aunque no es obligatorio pues el procesador puede localizar fácilmente su orden de aparición a partir del elemento padre.
 
## Encabezados
 
Para los encabezados utilizaremos el elemento `<head>`, con el que ya nos hemos encontrado en la lección 4. En nuestro documento, se podrían codificar como `<head>` todo lo que aparece en negrita y que hemos incluido en los cuadros verdes. Ahora bien, si quisiéramos clasificarlos en vista, por ejemplo, de una presentación podríamos establecer tipologías diferentes:
 
```xml
<head type="Principal">Unidad 1</head>
<head type="parte">PARTE I</head>
<head type="apartado">1. Introducción</head>
```
 
Aun así, no sería ni mucho menos obligatorio porque los diversos `<head>` son localizables por el procesador a partir del elemento del que forman parte, de manera que cada `<head>` podría tener una presentación diferente en función del elemento padre al que pertenece.
 
## Párrafos
 
Como ya hemos visto, los párrafos se marcan con el elemento `<p>`. Sin embargo, a veces una sección textual no corresponde exactamente a la noción de párrafo, y en ese caso podría utilizarse el elemento `<ab>` (*anonymous block*). Por ejemplo, en nuestro documento, podríamos marcar el texto introductorio con `<ab>` y relegar el elemento `<p>` para los párrafos de los apartados y subapartados.
 
 
## Citas 
 
Las citas pueden ser de muchos tipos diferentes, pero las más habituales son aquellas en que se reproducen de manera literal las palabras de otra fuente, acompañadas de la indicación bibliográfica. En estos casos, se utiliza el elemento [`<cit>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-cit.html) que debe estar formado, a su vez, por `<quote>` que encierra propiamente las palabras de la cita, y por `<bibl>` que debe contener la referencia bibliográfica:
 
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
 
## Listas
 
Las listas suelen ser un fenómeno habitual en muchos de los textos en prosa. Los elementos más comunes que pueden constituir una lista son los siguientes:
 
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
 
* `bulleted`: ítems precedidos de puntos o marcas similares.
* `inline`: ítems presentados en prosa continua, sin saltos de página.
* `numbered`: ítems precedidos de un número.
* `simple`: ítems presentados como bloques, pero sin puntos ni números.
En nuestro ejemplo, nos encontramos con una lista numerada, por lo que la podríamos codificar de la siguiente forma:
 
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
El elemento `<list>` sirve para listas genéricas que responden más bien a un formato presentacional. En muchos casos, cuando tenemos listas semánticas, donde el contenido es más específico, las *Guías directrices* de TEI contemplan elementos más concretos, como por ejemplo `<listBibl>` para una lista de bibliografía, o `<castList>` para una lista de personajes.
 
 
## Referencias cruzadas
 
Es también habitual que en un texto en prosa nos encontremos con referencias cruzadas que apunten al interior del documento o a una fuente externa. Los elementos para indicar este tipo de referencias y enlaces son [`<ref>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-ref.html) y [`<ptr/>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-ptr.html). La diferencia básica entre los dos es que el primero puede tener contenido y corresponde en realidad al típico enlace tal cual estamos acostumbrados a ver, mientras que `<ptr/>` (*pointer*) es un elemento vacío e indica sólo que en ese punto del texto aparece algo que crea un enlace, como por ejemplo un tipo concreto de imagen.
 
Ambos suelen utilizar, entre otros, el atributo `@target` que toma la forma de una referencia URI.
 
## Indexación
 
En algunas ocasiones podemos también encontrarnos con índices de términos, para ello podemos utilizar estos dos elementos:
 
* [`<index>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-index.html) marca una entrada de índice, puede llevar `@indexName`; en su interior pueden anidarse diferentes índices.
* [`<term>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-term.html) marca un término en el interior del índice.
 
Puede ocurrir que la fuente original no tenga un índice, pero que queramos construir uno. Esto puede hacerse de diferentes maneras, una de ellas sería utilizando los dos elementos anteriores y marcar los términos que queramos introducir en un nuevo índice. En nuestro texto de ejemplo, podríamos marcar los conceptos específicos de XML-TEI. De esta manera sería fácil autogenerar un índice de todos estos términos, por ejemplo, con un simple script en XSLT. Para esto, debemos marcar estos conceptos de la siguiente forma: 
 
```xml
La Guidelines proponen un tipo concreto de lenguaje de marcado que consiste en aislar a través de “<index indexName="conceptosXMLTEI"><term xml:id="mrc">marcas</term></index>” o “<index indexName="conceptosXMLTEI"> <term xml:id="etq">etiquetas</term></index>”.
```
 
# 3. Ejemplos
 
El posible resultado final -recordemos que no hay una sola manera correcta de codificar- para un texto en prosa puede ser como el que se encuentra en el [Ejemplo de codificación: Prosa](https://tthub.io/aprende/ejemplos/ejemplo-prosa). 
 
Para ver otros ejemplos de prosa, recomendamos el corpus en abierto de novelas españolas y latinoamericanas en el CLiGS textbox:
 
* [Collection of 19th Century Spanish-American Novels (1880-1916)](https://github.com/cligs/textbox/blob/master/spanish/novela-hispanoamericana), Ulrike Henny-Krahmer (ed.) (24 novelas)
* [Corpus of Spanish Novels from 1880-1940](https://github.com/cligs/textbox/blob/master/spanish/novela-espanola), José Calvo Tello (ed.) (39 novelas)
* [Corpus of Spanish Short Stories from 1880-1940](https://github.com/cligs/textbox/blob/master/spanish/cuentos-espanoles), José Calvo Tello (ed.) (20 colecciones de narraciones breves y 302 narraciones) 
 
# 4. Práctica: Codificación de un texto expositivo
 
## Enunciado
  
1. Comenzarás por crear un documento XML-TEI con su declaración XML, elemento raíz, `<teiHeader>`, y `<text>`.
2. Al igual que en el ejercicio anterior, debes copiar el texto a codificar en el elemento `<body>`.
3. Usa el elemento `<head>` para marcar los títulos, `<div>` para marcar las secciones del texto y `<p>` para los párrafos.
4. Marca las citas con elemento `<cit>`, indicando su fuente con el elemento `<bibl>`.
5. Marca las listas con `<list>` e indicar el tipo al que pertenece con el atributo `@type`.
6. Marca los términos acompañadas de enlaces con los elementos `<ref>` y `<ptr/>`.
7. Marca los conceptos propios del lenguaje de TEI con el elemento `<term>`.
8. Comprueba que el documento sea válido y esté bien formado.
 
## El texto a codificar

```
Las *Guías directrices* de la Text Encoding Initiative, su manejo y su traducción al español
 
I. Introducción
 
La Text Encoding Initiative se sustenta en primer lugar en las *Guías directrices*(http://www.tei-c.org/Guidelines/) que establecen un modelo concreto de codificación. Estas pautas son publicadas por el mismo Consorcio, en acceso abierto, en su página oficial. La versión actual es la P5 (donde P corresponde a "Proposal") y se remontan al año 2007, aunque cada pocos meses la versión es actualizada con pequeñas mejoras. Su problema principal es que no son muy amigables, si se considera que su edición en papel llega casi a las 2.000 páginas. Aún así, constituyen el núcleo de cualquier trabajo en TEI, y su consulta es siempre inevitable.
 
Empecemos con la definición que ofrece la misma página web del Consorcio TEI:
 
The TEI Guidelines for Electronic Text Encoding and Interchange define and document a markup language for representing the structural, renditional, and conceptual features of texts. They focus (though not exclusively) on the encoding of documents in the humanities and social sciences, and in particular on the representation of primary source materials for research and analysis. These guidelines are expressed as a modular, extensible XML schema, accompanied by detailed documentation, and are published under an open-source license. The Guidelines are maintained and developed by the TEI Consortium, through its Technical Council, with the support and participation of the TEI community.
(TEI Consotium, https://tei-c.org/Guidelines/)
 
De esta definición podemos establecer, pues, diferentes puntos:
 
*  Las *Guías directrices* pretenden definir un modelo concreto de codificación basado en el lenguaje XML.
* El modelo se acompaña de una documentación detallada que razona y ejemplifica el tipo de codificación para cada una de las fenomenologías textuales.
* Su objetivo principal es el de representar los rasgos de la estructura, de la presentación y de la semántica textuales.
* Es un modelo destinado especialmente a documentos procedentes de las disciplinas en Humanidades y Ciencias Sociales y, sobre todo, pensado para la codificación de fuentes primarias para su análisis, procesamiento, edición y explotación.
* Establece un sistema modular donde cada uno de los módulos define una serie de fenomenologías textuales con soluciones específicas.
* Todo documento TEI se basa en un esquema XML.
* Es un sistema de código abierto y por tanto tenemos acceso de manera gratuita.
* Las *Guías directrices* se sostienen gracias a 1) el Consorcio TEI, 2) el Technical Council, y 3) la comunidad de usuarios.
```
