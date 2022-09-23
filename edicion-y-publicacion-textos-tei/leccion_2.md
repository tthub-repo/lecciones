---
title: El lenguaje XML
author: Susanna Allés Torrent, Gabriel Calarco, Gimena del Rio Riande
date: 2022
layout: default
lang: es
---
 
En esta lección explicamos sumariamente el funcionamiento del lenguaje XML, los programas o editores con los que podemos trabajar, así como algunos de los principios fundamentales. Al final, proponemos un breve ejercicio de creación de un documento XML.  

# 1. El estándar XML
 
**XML ([Extensible Markup Language](https://es.wikipedia.org/wiki/Extensible_Markup_Language))** es uno de los lenguajes más utilizados en el mundo de la informática, ya que es uno de los más simples, flexibles y adecuados para asegurar la interoperabilidad con una gran cantidad de aplicaciones, plataformas y lenguajes informáticos.
 
En nuestras vidas lo utilizamos casi diariamente, incluso sin saberlo: ¿sabías que detrás de un documento Word está XML? Si descomprimes un documento de Microsoft Word o OpenOffice, por ejemplo, descubrirás que el documento está compuesto por una serie de documentos XML.
 
La misión principal de XML consiste en la estructuración de cualquier tipo de datos, como puede ser el marcado electrónico de textos, de cualquier tipología, para que sean procesados por una máquina. El lenguaje utilizado para la marcación de datos es simple y legible para los seres humanos (lo que en inglés llaman *human-readable*). En el lado opuesto, un lenguaje que no puede ser leído por los humanos puede ser, por ejemplo, un código de barras o los mismos datos binarios, que pueden ser leídos por un ordenador, pero no por una persona.
 
XML constituye un método sencillo para representar datos de una manera estructurada digitalmente, como una línea de caracteres. Su funcionamiento se basa en el concepto de **marcado** que radica en aislar y marcar partes de esa cadena de datos (sean palabras, números, párrafos, etc.) con **etiquetas** o **marcas** con nombre propio para indicar una función estructural o semántica.
 
Cuando decimos que TEI se expresa a través del lenguaje XML nos referimos a que el estándar de marcado propuesto por la Text Encoding Initiative ha creado un conjunto de elementos (definidos y delimitados por las *Guías directrices*) que se expresan a través de la sintaxis del lenguaje de marcado XML. En ese sentido, podemos decir que TEI es un dialecto del lenguaje XML.
 
# 2. Editores de código

Cuando queremos crear o editar un documento XML, los procesadores de texto más usados, como Microsoft Word o WordPad, no nos serán de utilidad, ya que fácilmente se pueden agregar accidentalmente formatos y caracteres extra y/o invisibles que pueden generar problemas. Los editores de texto plano son una opción más adecuada, es posible crear y editar archivos XML-TEI con cualquiera de estos programas mientras trabajen con texto plano sin añadir ningún tipo de formato. Sin embargo la mejor alternativa para trabajar en este tipo de documentos es utilizar un programa específicamente diseñado para editar códigos informáticos. Existen varias opciones gratuitas, tales como [Atom](https://atom.io/packages/xml-tools), [Komodo](https://www.activestate.com/products/komodo-edit/), [jEdit](http://www.jedit.org/), entre muchos otros. En este tutorial usaremos el editor [Visual Studio Code](https://code.visualstudio.com/) (usualmente abreviado VS Code), ya que nos ofrece la posibilidad de instalar la extensión [Scholarly XML*](https://marketplace.visualstudio.com/items?itemName=raffazizzi.sxml) que brinda funciones adicionales, específicamente desarrolladas para trabajar con documentos XML-TEI.

## Visual Studio Code 

Para utilizar VS Code solo debes ir a la [página de descarga de la aplicación](https://code.visualstudio.com/Download) y seleccionar el instalador correspondiente según tu sistema operativo.

Una vez que hayas completado la instalación de VS Code, el próximo paso será instalar la extensión Scholarly XML. Para eso, debes seleccionar el ícono de extensiones del menú lateral de VS Code (paso 1) y en el cuadro de búsqueda ingresar la palabra “Schorlarly” (paso 2). Cuando aparezca la opción que deseamos utilizar, solo debes presionar el botón “install” (paso 3):
 
![Instalación de Scholarly XML en VS Code](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L2_001.png)
<p align="center">Pasos para instalar la extensión Scholarly XML en VS Code.</p>
 
Con esta extensión incorporamos en VS Code algunas funciones que nos serán de gran utilidad para la codificación de textos en XML-TEI:

*  VS Code nos informará si nuestros archivos son válidos y están bien formados (veremos qué significa esto en la [sección IV](link)).
*  Si estamos trabajando en TEI recibiremos sugerencias de elementos que podemos utilizar de acuerdo al esquema con el que estemos trabajando (veremos cómo funciona esto en la [siguiente lección](link)).
*  Si estamos trabajando en TEI podemos seleccionar una porción de texto y utilizar el atajo *ctrl+E* para marcarlo con una etiqueta de inicio al comienzo y una de cierre al final (el funcionamiento de estas etiquetas se explica a continuación).

VS Code también ofrece otras extensiones destinadas al trabajo con archivos XML, como [XML Complete](https://marketplace.visualstudio.com/items?itemName=rogalmic.vscode-xml-complete), que ofrece varias funcionalidades útiles para editar XML. Sin embargo, en este tutorial utilizaremos Scholarly XML ya que fue diseñada espacialmente para la codificación de textos en XML-TEI.

Entre la comunidad TEI, también ha sido muy utilizado otro editor XML llamado [oXygen](https://www.oxygenxml.com/). Aunque el programa ofrece funcionalidades específicas y muy útiles para el marcado TEI, el mayor inconveniente es que es propietario y por tanto se necesita una licencia para poder emplearlo. 
 
# 3. Reglas y conceptos generales
 
Veamos enseguida qué aspecto tiene un fichero XML e intentemos comprender la noción de marcado, así como algunas reglas generales:
 
```xml
<?xml version="1.0" encoding="UTF-8"?>
 
<lista>
   
    <libro>
        <autor id="01">Esquilo</autor>
        <titulo>Prometeo encadenado</titulo>
    </libro>
 
    <libro>
        <autor id="02">Sófocles</autor>
        <titulo>Edipo Rey</titulo>
    </libro>
   
    <libro>
        <autor id="03">Eurípides</autor>
        <titulo>Medea</titulo>
    </libro>
 
</lista>
 
<!-- Esto es un comentario -->
 
```
 
[Ejemplo 1: un documento xml (GitHub)](https://github.com/tthub-repo/ejemplos/blob/master/L2_ejemplo-1.xml).
 
A partir de este simple ejemplo, podemos constatar ya algunas ideas y reglas inherentes a todos los documentos XML:
 
* El **[marcado](https://es.wikipedia.org/wiki/Lenguaje_de_marcado)** (*markup*) consiste en aislar una porción de texto, grande o pequeña, con un significado semántico específico y señalarlo a través de una marca electrónica, que comúnmente llamamos [**etiqueta**](https://es.wikipedia.org/wiki/Etiqueta_(lenguaje_de_marcado)) (en inglés, *tag*).  
*  Las **etiquetas** indican una instrucción especial de procesamiento que el ordenador interpreta como código informático, y delimitan dónde empieza y dónde acaba ese código. Las etiquetas deben aparecer al inicio del segmento que queramos codificar a través de dos paréntesis angulares (`<...>`), y en el cierre del mismo, también con dos paréntesis angulares con la barra inclinada (`/`) al inicio. Por ejemplo, la etiqueta que utilizamos para marcar el título de las obras tiene la siguiente estructura: `<titulo>`, y la etiqueta de cierre es igual, con la salvedad de que se agrega la barra al comienzo: `</titulo>`.  Es importante recordar que los caracteres `< >` son siempre interpretados como código por nuestro ordenador, de manera que si se quieren representar en el texto como tales deberemos utilizar caracteres diferentes (`&lt;` para representar `<` y `&gt;` para `>`).
* Los [**elementos**](https://www.w3schools.com/xml/xml_elements.asp) son las unidades de información semántica compuestas de una etiqueta de apertura y de cierre. El texto que contienen las etiquetas entre los signos `< >` se conoce como **identificador**, y todo lo que aparece entre la etiqueta de apertura y de cierre es lo que se llama **contenido**. Los elementos pueden contener texto, otros elementos o estar vacíos. La estructura básica de un elemento sería la siguiente:
 
```xml
<elemento>contenido</elemento>
```
 
Y un ejemplo concreto podría ser:
 
```xml
<titulo>Medea</titulo>
```
 
Para practicar el marcado XML con elementos puedes ir al [ejercicio 1](enlace) de la sección *Práctica*
 
* Los elementos también pueden poseer **atributos** que añaden una característica adicional, y resultan de gran importancia para complementar la información que estamos marcando en el texto. El nombre del atributo se ubica en el interior de la etiqueta de apertura, después del identificador y separado de este por un espacio, a continuación (sin espacios intermedios) encontraremos el símbolo `=`, y entre comillas se incluye el **valor** de este atributo. En conclusión, la estructura sintáctica de un elemento con un atributo será la siguiente:
 
```xml
<elemento atributo="valor">Contenido</elemento>
```
 
Y un ejemplo podría ser:
 
```xml
<autor id="03">Eurípides</autor>
```

* Los nombres de los atributos deben formularse igual que los nombres de los elementos. Su orden en el interior del elemento es libre, siempre y cuando no se repita. Conviene aclarar que a lo largo de los materiales de este tutorial utilizaremos la convención tipográfica de identificar los nombres de los atributos con el signo `@` al comienzo del nombre. Por ejemplo, nos referimos al atributo `type` como `@type`. Sin embargo, es importante tener presente que esta es solo una forma convencional de referirnos a los nombres de los atributos, pero no debemos incluir el signo `@` cuando estamos introduciendo atributos en un documento XML.
 
Para practicar el uso de atributos puedes ir al [ejercicio 2](enlace) de la sección *Práctica*
 
* Los documentos XML también pueden contener **comentarios**, cuya función es que las personas puedan dejar sus notas, normalmente relativas al proceso de codificación del mismo documento. Pueden aparecer en cualquier lugar del documento mientras sea contenido; es decir, que no podrán nunca situarse al interior de una etiqueta. No tienen ningún efecto sobre el procesamiento informático, pero el uso de comentarios es considerado una buena práctica, que resulta de gran utilidad para hacer que la codificación sea comprendida más fácilmente por un lector humano, y por lo tanto ayuda a mejorar el potencial de reutilización de nuestros archivos. Los comentarios están delimitados por `<!--` y `-->`. Por ejemplo:
 
```xml
<!-- ¡esto es un comentario! -->
```
 
Para practicar el uso de comentarios puedes ir al [ejercicio 3](enlace) de la sección *Práctica*
 
* Los documentos XML poseen una **estructura arbórea**, esto significa que tienen un elemento raíz que contiene a todos los demás (en nuestro ejemplo, sería el elemento  `<lista>`), y a su vez cada elemento puede contener otros subordinados (en el ejemplo, cada elemento `<libro>` contiene a su vez a los elementos `<autor>` y `<titulo>`). Esta anidación de elementos crea una estructura jerárquica, que resulta característica de la forma en la que los datos se organizan en un documento XML.
 
# 4. Conceptos de “Válido” y “Bien formado”
 
Un documento XML debe estar [bien formado y ser válido](https://es.wikipedia.org/wiki/Validaci%C3%B3n_XML) para poder ser procesado y visualizado.

## Documento bien formado

Si nuestro documento está expresado correctamente según la gramática de XML, decimos que está **[bien formado](https://es.wikipedia.org/wiki/Validaci%C3%B3n_XML)**, esta es una condición esencial para su correcta visualización y procesamiento informático. Esto significa que tenemos que seguir determinadas reglas:
 
* Debe haber un único elemento o nodo raíz que contenga la totalidad del documento XML.
* Todos los elementos deben estar bien anidados al interior de un elemento raíz y nunca deben solaparse los unos con los otros. Así, por ejemplo, esto sería correcto:
 
```xml
 <libro>
        <autor id="03">Eurípides</autor>
        <titulo>Medea</titulo>
    </libro>
```
 
Pero no esto:
```xml
 <libro>
        <autor id="03">Eurípides
        <titulo>Medea</autor></titulo>
    </libro>
```
 
* Los elementos y los atributos son sensibles a las mayúsculas y minúsculas, de manera que si se equivocan en una sola letra, poniéndola en mayúscula en lugar de minúscula o viceversa, se encontrarán con un error.
* Todas las etiquetas de apertura (`<identificador>`) deben tener una etiqueta de cierre (`</identificador>`) correspondiente. La única excepción son los elementos vacíos, que pueden identificarse con una única etiqueta que funciona a la vez como apertura y cierre, y que se expresa con la barra inclinada al final del identificador (`<identificador/>`).
* Los valores de los atributos van siempre entre comillas (`<elemento atributo=”valor”>`).
* Un elemento no puede tener dos atributos con el mismo nombre.
* Los comentarios y las instrucciones de procesamiento nunca pueden aparecer en el interior de una etiqueta.
* Se recomienda no utilizar acentos ni espacios en los nombres de los elementos, ni en los atributos como tampoco en los valores; ya que su uso puede acarrear problemas a la hora de procesar los documentos.
 
Para practicar las reglas de la sintaxis de XML puedes ir al [ejercicio 4](enlace) de la sección *Práctica*
 
La extensión Scholarly XML, que instalamos en VS Code nos permite comprobar la correcta formación de archivos XML. Si abrimos el archivo que estamos usando como ejemplo, encontraremos un mensaje en la barra inferior que nos indicará si el documento se encuentra bien formado (*XML is well formed*):
 
![Mensaje de bien formado en VS Code](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L2_002.png)
 <p align="center">Mensaje de bien formado (<i>well formed</i>) que aparece en la marquesina inferior de la pantalla de VS Code cuando abrimos un archivo XML si tenemos instalada la extensión Scholarly XML.</p>

## Documento válido

Otra característica que resulta deseable, es que además de estar bien formado, nuestro documento sea también **válido**. Para ello, es necesario un modelo que fije la estructura básica y las posibilidades de anidación de los elementos. Los **esquemas** establecen la sintaxis que debe tener el documento XML. Si está formado según sus reglas, será válido.
 
Mientras que un documento XML debe estar siempre bien formado, el hecho de ser válido no es obligatorio, pero altamente recomendable pues establece qué tipo de marcado se ha utilizado. En el caso de TEI, siempre se usa un esquema a partir del cual validamos nuestro documento. En la próxima lección trabajaremos sobre un archivo XML-TEI asociado a un esquema y explicaremos las bases del funcionamiento de estos archivos en el proceso de codificación de un texto con TEI.
  
# 5. Práctica: XML en uso
 
## Ejercicio 1
 
Agregar a la lista que usamos como ejemplo en esta lección los siguientes libros:
 
*Ilíada*, de Homero
*Teogonía*, de Hesíodo
 
Debes crear un elemento `<libro>` para cada una de estas obras, y en su interior agregar las marcas de `<autor>` y `<titulo>` con sus respectivos contenidos:
 
## Ejercicio 2
 
Agregar el atributo `id` en los elementos `<autor>` de las entradas que colocaste en el ejercicio anterior. El valor de estos atributos debería ser `04` y `05`, respectivamente, siguiendo el orden numérico de la lista.
 
## Ejercicio 3
 
Agregar un comentario indicando cuáles son los libros que agregamos a la lista.
 
 
## Ejercicio 4
 
Identifica cuáles son los errores en el siguiente ejemplo y modifica el archivo para que esté bien formado.
 
```xml
<?xml version="1.0" encoding="UTF-8"?>
 
<lista>
   
    <obra>
        <autor id="01">Tirso de Molina
        <titulo>El burlador de Sevilla</titulo>
    </obra>
 
    <obra>
        <autor id=02>Lope de Vega</autor>
        <titulo>El caballero de Olmedo</titulo>
    </obra>
   
    <obra>
        <autor id="03">Calderón de la Barca
        <titulo>La vida es sueño</autor></titulo>
    </obra>
 
</lista>
```
