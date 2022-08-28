---
title: ¿Qué es y para qué sirve el documento ODD?
author: Susanna Allés Torrent
date: 2019
layout: default
lang: es
---

# {{ page.title }}
## {{ page.author }}
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.4555607.svg)](https://doi.org/10.5281/zenodo.4555607)

En esta lección, veremos en qué consiste un documento ODD y cuál es su función en el seno de un proyecto de codificación TEI. Sus siglas proceden de la expresión "One Document Does it All", así que podemos ya hacernos una idea de la importancia de este archivo.

# I. ¿Qué es un ODD? 

Como es sabido, el sistema de codificación TEI consiste en una lista de módulos que contienen una serie de elementos con sus especificaciones. A su vez, cada uno de los elementos TEI tiene un nombre “estándar” o canónico (como pueden ser `p`, `div`, `corr`, `sic`, etc.), una descripción de su función, la indicación del modelo o clase al que pertenece, una definición de los atributos que puede contener, así como una lista de ejemplos; esta es la estructura que, de hecho, vemos cada vez que consultamos un elemento en las *Guías directrices*.

Aparte de estas especificaciones generales, el esquema utilizado para validar documentos en TEI puede ser de diferentes tipos (DTD, esquema W3C, RelaxNG), y podemos personalizarlo según nuestras necesidades. El más utilizado es el esquema RelaxNG, del que nos ocupamos en la lección ["Esquemas y personalización de TEI"](https://tthub.io/aprende/l6-esquemas/). Estos esquemas tienen como función recoger todas las referencias a los módulos, elementos, etc. que establece el modelo general de TEI; además, tenemos la posibilidad de personalizar estos esquemas, modificando módulos, elementos, atributos o clases, etc.

En todo este engranaje, hay una última etapa que es de vital importancia, y esto es, el documento ODD. Este archivo es el que conservará todas y cada una de las modificaciones y de las singularidades o especificaciones de nuestro esquema (¡pero obviamente no el de nuestro marcado XML-TEI!).

El documento ODD consiste en un archivo XML-TEI, a partir del cual podremos generar el esquema en diferentes lenguajes y recuperar la documentación de nuestro proyecto.

Veamos cuales son las prestaciones que nos ofrece el documento ODD:

* El documento ODD es el único que nos permitirá recuperar nuestro esquema personalizado. Es muy importante tener en cuenta que un esquema (RelaxNG o de otro tipo) NO puede subirse a la aplicación ROMA, y por tanto, si ya lo hemos modificado y no hemos generado una ODD, no habrá manera de recuperar las informaciones que hayamos añadido. Por ejemplo, imaginemos que hemos definido una nueva semántica para algunos de los elementos TEI, eliminado elementos y definido valores por defecto en los atributos. Pues bien, todas estas informaciones solo serán recuperables si, al finalizar la personalización, creamos el documento ODD. En la aplicación ROMA solo pueden subirse los documentos ODD, no aceptará ni esquemas ni ficheros XML-TEI codificados.
* En cualquier proyecto de edición, especialmente en las primeras etapas, es normal modificar el esquema de codificación, de manera que cada vez que lo modifiquemos deberemos crear también un documento ODD que será el responsable de generarnos el esquema deseado.
* El documento ODD también nos permitirá generar, además de los esquemas, una nueva documentación tal y como la habremos redactado para nuestro proyecto.
* En fin, el documento ODD es la pieza clave para poder difundir y compartir nuestro esquema de codificación. No solo con la comunidad TEI, sino también entre los mismos miembros de un equipo.

# II. Creación del ODD

Pasemos ahora a ver cómo podemos crear y manipular un documento ODD con la aplicación Roma. Obviamente podríamos crearlo a mano, si conocemos bien la sintaxis a utilizar, tal y como ocurría con los esquemas, pero la práctica habitual es el uso de la aplicación [Roma](https://roma2.tei-c.org/).

Para tomar una primera toma de contacto con un fichero ODD, podéis crear uno con el programa oXygen, siguiendo estos pasos:

`File > New > Framework templates > TEI > ODD Customization > Create`
 
![Programa Oxygen. Pasos a seguir para crear un documento ODD](https://tthub-repo.github.io/lecciones/img/L7_001.png)

Como puede observarse, se trata de un fichero XML-TEI normal con el prólogo XML, un elemento raíz `<TEI>`, al interior del cual tenemos un `<teiheader>` con los diferentes metadatos, y un elemento `<text>` que contiene a su vez el `<body>`. Ahora bien, los elementos que aparecen a continuación son nuevos:

![Oxygen. Estructura básica de un documento ODD](https://tthub-repo.github.io/lecciones/img/L7_002.png)
 
El elemento `<schemaSpec>` responde a "Schema Specification", es decir, señala el tipo de esquema que debe reconstruir, indicando además el elemento raíz a través del atributo `@start`.

A continuación, el documento ofrece los diferentes módulos que el esquema resultante deberá contener. Como puede verse, se trata sólo de los módulos obligatorios: `header`, `core`, `tei` y `textstructure`.

De hecho, este sería el mismo resultado que si, en la aplicación Roma, creáramos un esquema mínimo. Hagamos la prueba y sigamos estos tres pasos:

**1.** Id a la aplicación Roma y cread un esquema a partir del modelo mínimo:

![Aplicación Roma. Creación de un esquema](https://tthub-repo.github.io/lecciones/img/L7_003.png)

**2.** Cambiad los metadatos esenciales en la pestaña "Customize" o “Personalizar”:

![Roma. Personalización de un esquema](https://tthub-repo.github.io/lecciones/img/L7_004.png)
 
**3.** Si ahora quisiéramos generar un esquema RelaxNG, iríamos a la pestaña “Esquema”; si quisiéramos obtener la documentación relativa a ese esquema, seleccionaríamos la pestaña “Documentación”. Ahora lo que nos interesa es crear el documento ODD, por lo que iremos a “Guardar configuración personal”:

![Roma. Guardar configuración personal](https://tthub-repo.github.io/lecciones/img/L7_005.png)
 
Al pulsar, se descargará de manera automática el fichero ODD, que si abrimos con el programa oXygen, veremos que contiene la misma estructura y los mismos módulos obligatorios; además de la descripción que añadimos en la pestaña “Personalizar” se reflejan en el documento obtenido, como en la imagen siguiente:

![Oxygen. Documento ODD](https://tthub-repo.github.io/lecciones/img/L7_006.png)
 
Aparecen los siguientes elementos y atributos:

* `schemaSpec` es la definición formal del esquema TEI.
* `@ident` contiene el identificador que corresponde al nombre del archivo que le hemos consignado.
* `@docLang` indica la lengua de la documentación, en nuestro caso el español `es`.
* `@prefix`: `tei_` es el prefijo que se utilizará para todas las definiciones de los casos TEI.
* `@key`: es el responsable de llamar a los identificadores de los módulos y todo el contenido que hay en ellos.

En resumen, una personalización mínima de TEI, registrada en un documento ODD, contendrá siempre los módulos obligatorios. De ser de otra manera, ya no sería un fichero TEI, sino otra cosa; y cada uno de esos módulos, incluye a su vez una lista de elementos y atributos predefinidos.

Hagamos otra prueba, retomando nuestro archivo ODD que hemos creado y siguiendo estos ocho pasos:

1. En la página principal de Roma, escoged la opción “Upload Customization” y elegid vuestro archivo ODD creado anteriormente con Roma:

![Roma. Subida del documento ODD](https://tthub-repo.github.io/lecciones/img/L7_007.png)

2. Como se puede ver, hemos recuperado las informaciones que habíamos introducido:

![Roma. Informaciones del esquema personalizado](https://tthub-repo.github.io/lecciones/img/L7_008.png)

3. Ahora vayamos a la pestaña de “Módulos” y añadamos el módulo `verse`:

![Roma. Adición del módulo verse en el esquema](https://tthub-repo.github.io/lecciones/img/L7_009.png)
 
4. Hagamos click en el módulo `verse`, eliminemos los elementos `<metDecl>` y `<metSym>` y guardemos los cambios:

![Roma. Modificaciones del esquema](https://tthub-repo.github.io/lecciones/img/L7_010.png)
 
5. Al interno del elemento `<caesura>` haremos un solo cambio: ampliaremos la “Descripción”:

![Roma. Modificación de la descripción de un elemento](https://tthub-repo.github.io/lecciones/img/L7_011.png)

6. Al interno del elemento `<rhyme>`, modificaremos los valores de los atributos en la pestaña correspondiente “Modificación de atributos” y señalando los valores en la casilla “Lista de valores”. En nuestro caso, señalaremos el tipo de rima en “consonante” o “asonante”, separados por comas y sin espacios. Esta modificación nos simplificaría la tarea al codificar, preestableciendo nuestros valores:

![Roma. Modificaciones de los valores de un atributo](https://tthub-repo.github.io/lecciones/img/L7_012.png)
 
7. Si quisiéramos generar el esquema correspondiente iríamos a la pestaña “Esquema” y seleccionaríamos el tipo de esquema deseado:

![Roma. descarga del esquema RelaxNG](https://tthub-repo.github.io/lecciones/img/L7_013.png)
 
8. El esquema que nos hemos bajado debería ir a asociado ahora a un documento XML-TEI. Podemos hacer la prueba: cread un nuevo documento XML-TEI, asociad el esquema en el prólogo del documento, y codificad un pequeño poema. Al codificar, veremos que el mismo programa nos ofrece los valores que hemos establecido en el esquema (paso 6), tal y como vemos en la Figura siguiente:

![Oxygen. Valores por defecto establecidos en el esquema](https://tthub-repo.github.io/lecciones/img/L7_014.png)

9. Generemos finalmente el documento ODD, clicando en “Guardar configuración personal” y abramos el documento con oXygen:

![Oxygen. Documento ODD final](https://tthub-repo.github.io/lecciones/img/L7_015.png)
 
Como vemos, el resultado es la suma de los cambios realizados en nuestro esquema:

* Se ha añadido el módulo `verse`, señalando los dos elementos que hemos eliminado.
* Se recoge la nueva descripción del elemento `<caesura>`.
* Así como se añaden los valores al atributo `@type` a través de una lista de valores (`<valList>`) y los valores individuales (`<valItem>`).

A partir de ahora, cada vez que subamos este documento ODD a la aplicación Roma recuperaremos el mismo esquema, conservando siempre las modificaciones que hemos llevado a cabo. Uno puede imaginarse cuánto tiempo nos llevaría modificar nuestro esquema, si tuviéramos que incorporar toda la personalización cada vez que quisiéramos realizar algún cambio!

Resumiendo, lo que siempre debemos tener para trabajar en cualquier proyecto de edición digital es el documento XML-TEI, el esquema RNG, y la ODD. En un símil culinario, la ODD constituiría la receta y la lista de los ingredientes, el esquema la instrucciones sobre cómo prepararla, y el documento XML-TEI el trabajo de llevar a cabo el manjar. 
 

# III. Bibliografía

* [Getting Started with P5 ODD](http://www.tei-c.org/guidelines/customization/getting-started-with-p5-odds/), TEI Consortium 
* [TEI ODD Wiki](https://wiki.tei-c.org/index.php/ODD)
* [Understanding ODD](http://tei.oucs.ox.ac.uk/Talks/2011-06-18-odd/), digital.humanities@oxford (University of Oxford)


