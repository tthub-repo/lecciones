---
title: Esquemas y personalización de TEI
author: Susanna Allés Torrent
date: 2019-01-15
---

# I. Principios fundamentales del esquema
En esta unidad veremos cómo llevar a cabo la personalización de un documento TEI a través de esquemas. Para ello, presentaremos de manera general la función del esquema al interno de los proyectos de edición digital en TEI, centrándonos en el lenguaje Relax NG <https://relaxng.org/>, y en la aplicación online Roma, que facilita la personalización de los esquemas que acompañan los documentos XML-TEI.

Para trabajar con un documento XML y aplicar un tipo concreto de marcado debemos tener un modelo de trabajo; una especie de guía que nos indique de qué modo debemos proceder para codificar ese texto, de manera que si interviene más de una persona, todas lleven a cabo un marcado homogéneo.

Para ello, necesitamos asociar nuestro documento XML con un esquema que sirva justamente para establecer el tipo de marcado que podemos aplicar a un documento XML. Los esquemas son ficheros autónomos que se asocian al fichero XML-TEI en su prólogo, de la siguiente manera. La comunidad TEI ofrece algunos esquemas ya construidos a los que podemos asociar nuestro documento. Por ejemplo, si quisiéramos asociar nuestro documento a un esquema general que llaman “tei all” lo haríamos así: 

```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-model href="http://www.tei-c.org/release/xml/tei/custom/schema/relaxng/tei_all.rng" type="application/xml" schematypens="http://relaxng.org/ns/structure/1.0"?>
<TEI xmlns="http://www.tei-c.org/ns/1.0">
…
</TEI>
```

Si, en cambio, quisiéramos asociar nuestro documento a un esquema que nosotros mismo hemos creado, deberíamos indicarlo a través de una URL (al interno del elemento `@href`), apuntando a la ubicación en local o en línea: 

```xml
<?xml-model href="/esquema/nuestro_esquema.rng" schematypens="http://relaxng.org/ns/structure/1.0"?>
<TEI xmlns="http://www.tei-c.org/ns/1.0">
…
</TEI>
```

En el programa oXygen, para cambiar el esquema y asociar uno nuevo debemos ir a Document > Schema > Associate Schema; obviamente puede también hacerse de manera manual.

Los esquemas, [como vimos en la Unidad 2](XX), son los responsables de la validación de nuestro documento. Recordad que una cuestión es el estar bien formado, según las normas del lenguaje XML, y la otra ser válido, según las normas de un esquema.

En general, los proyectos de edición digital no necesitan los 21 módulos ni todos los 505 elementos de las Guías directrices, de manera que es conveniente restringir y concretar lo más posible el esquema. Por otro lado, hay que tener también en cuenta que eventualmente TEI puede no ofrecer el elemento idóneo para marcar un determinado fenómeno o estructura que sí aparece en vuestro texto; en dicho caso, se podrían crear otros elementos y atributos, pero se recomienda no abusar de este método y utilizarlo con mucho cuidado, pues obtendríamos un esquema no conforme a las Guías directrices.

Un esquema establece la representación formal de los elementos y atributos cuyo uso se permitirá en el documento a codificar. Así, por ejemplo, establece cuál será el elemento raíz del documento, los nombres de los elementos utilizados, los nombres y los tipos de datos (cadena de caracteres, números, etc.), las reglas sobre cómo los elementos deben anidarse, e incluso, a veces, los valores por defecto de los atributos.

Un esquema, pues, especifica la estructura y la nomenclatura de nuestro fichero; la semántica de los elementos, por otro lado, queda como siempre relegada a las Guías directrices TEI.

## II. Tipos de esquemas

Un modelo de codificación en XML se construye a partir de una sintaxis concreta que se establece en lo que llamamos esquemas. Existen diferentes tipos de esquema, [como vimos en la Unidad 2](XXX), entre los cuales encontramos:

* DTD: responde a las siglas “Document Type Definition” y se definió al interno de la norma del lenguaje XML 1.0. Permite definir una lista de los elementos de un documento (nombre y modelo de contenido), los atributos (por nombre, tipo y categoría) y las entidades. En el campo de TEI ya no suele usarse, por considerarse demasiado rígida y ofrecer poca flexibilidad. Un tutorial simple está disponible en W3Schools DTD Tutorial <https://www.w3schools.com/xml/xml_dtd_intro.asp>, y tenéis un ejemplo en la sección de documentos de la unidad 2 curso: [Ejemplo 2: un documento XML asociado a una DTD (ejemplo-2-DTD.dtd) que valida el fichero XML (ejemplo-2.xml)](XX). 
* W3C esquema: fueron propuestos por el W3C y los primeros en expresarse en XML. Se aprobó en mayo de 2001 y una segunda edición se publicó en octubre 2004, dividida en tres partes: XML Schema Part 0 <https://www.w3.org/TR/xmlschema-0/>; Part 1 <https://www.w3.org/TR/xmlschema-1/>: Structures; Part 2: Datatypes. <https://www.w3.org/TR/xmlschema-2/> Un tutorial simple está disponible en W3Schools XML Scheme Tutorial <https://www.w3schools.com/xml/schema_intro.asp>.
* Relax NG <https://relaxng.org/>: en 2003 se estableció como norma ISO/IEC 19757-2 <https://www.iso.org/standard/52348.html>, actualizada en 2008 y es el más utilizado por la comunidad TEI.

Aquí encontraréis un artículo de E. Van der Vlist donde se comparan los tres tipos de esquema: E. Van der Vlist, «Comparing XML Schema Languages» (12 Diciembre 2001), XML.com <https://dyomedea.com/papers/2005-xmlprague/schemas-compared.pdf>.

# III. Esquema RelaxNG

Al trabajar con XML-TEI, lo más habitual es el uso de esquemas Relax NG, pues son los que permiten más granularidad y flexibilidad. Relax NG responde a las siglas: REgular LAnguage for XML Next Generation y su especificación fue publicada por el Consortium OASIS el 3 de diciembre de 2001. Poco después, en 2003, se convirtió en norma ISO (ISO/IEC 19757-2:2003) y en 2008 hubo una nueva publicación que remplazaba la segunda: ISO/IEC 19757-2:2008 <https://www.iso.org/standard/52348.html> Document Schema Definition Language (DSDL) – Part 2: Regular grammar-based validation – RELAX NG.

Relax NG se expresa en XML y es relativamente sencillo y fácil de aprender. A diferencia de las DTD, por ejemplo, admite espacios de nombre y por tanto la capacidad de trabajar con uno o con varios. Para una lista más detallada de las ventajas, véase aquí <https://www.oasis-open.org/committees/relax-ng/charter.php>.

Este tipo de esquema propone una determinada estructura para cada una de las instancias XML, estableciendo un modelo concreto de contenido tanto de los elementos como de los atributos. Al interno del esquema, todos los elementos deben ser definidos. Para dar una idea general del tipo de gramática utilizada, veamos por ejemplo de qué manera Relax NG indicaría que el elemento raíz de un documento TEI puede ser doble:

```xml
<start>
    <choice>
        <ref name="tei_TEI"/>
        <ref name="tei_teiCorpus"/>
    </choice>
</start>
```

El elemento `<start>` indica el elemento raíz, mientras que `<choice>` indica las opciones de anidación al interno de esa etiqueta. A continuación, deberíamos definir a su vez los elemento `<TEI>` y `<teiCorpus>` (de otra manera el esquema no estaría bien formado).

Tomemos otro ejemplo, el elemento `<text>` tal y como aparece definido en el esquema Relax NG según las Guías Directrices de TEI:

```xml
	<define name="tei_text">
    <element name="text">
    <!-- Aquí aparece la documentación que concierne al elemento: -->
      <a:documentation xmlns:a="http://relaxng.org/ns/compatibility/annotations/1.0"> contiene un único texto de cualquier tipo, sea este unitario o combinado, p.ej. un texto en verso o teatral, una recopilación de ensayos, una novela, un diccionario, o una fragmento de corpus. [4. 15.1. ]</a:documentation>
    <!-- Al interior de <text> podemos encontrar un grupo de elementos: -->
         <group>
            <zeroOrMore>
         <!-- En este punto pueden aparecer ninguna o múltiples veces una serie de elementos permitidos en cualquier punto de un documento XML-TEI. Véase la lista aquí: http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-model.global.html -->
                <ref name="tei_model.global"/>
             </zeroOrMore>
             <optional>
   <!-- Opcionalmente podemos tener un elemento <front> al interno de <text> -->
                <ref name="tei_front"/>
                 <zeroOrMore>
                     <ref name="tei_model.global"/>
                  </zeroOrMore>
               </optional>
               <choice>
  <!-- Debemos elegir entre incluir un elemento <body> o un elemento <group> -->
                   <ref name="tei_body"/>
                   <ref name="tei_group"/>
                </choice>
                <zeroOrMore>
                   <ref name="tei_model.global"/>
                </zeroOrMore>
                <optional>
    <!-- Opcionalmente podemos tener un elemento <back> al interno de <text> -->
                    <ref name="tei_back"/>
                    <zeroOrMore>
                       <ref name="tei_model.global"/>
                     </zeroOrMore>
                 </optional>
             </group>
<!-- Aquí la lista de los tipos de atributos que puede contener el elemento <text> -->
           <ref name="tei_att.global.attributes"/>
           <ref name="tei_att.declaring.attributes"/>
           <ref name="tei_att.typed.attributes"/>
          <empty/>
    </element>
</define>
```

Para llevar a cabo un proyecto de edición digital y de marcado XML-TEI es indispensable tener un esquema creado a nuestra medida. El esquema es el que nos permite establecer qué tipo de elementos necesitamos para marcar determinados fenómenos textuales, para poder localizarlos y procesarlos posteriormente. También supone que podamos establecer los atributos, los valores e incluso el orden de todos ellos.

Normalmente en un proyecto hay múltiples personas trabajando en la codificación, por lo que es muy importante que todos codifiquen de la misma manera y con los mismos procedimientos y elementos.

Para la creación de un esquema el proceso siempre es el mismo. Tal y [como vimos en el Tema 1](XXX), la condición indispensable es que analicemos el texto y que definamos qué elementos aparecen en el mismo, tanto cuestiones estructurales, como semánticas. Una vez hemos elaborado la lista de fenómenos que nos gustaría codificar, deberemos encontrar la manera de expresarlo según las Guías directrices y elaborar nuestro esquema Relax NG propio.

# IV. Aplicación Roma

La sintaxis de los esquemas puede parecer complicada a simple vista, pero el esquema Relax NG realmente es el más sencillo y podríamos crearlo y modificarlo a mano. Aún así, el consorcio TEI pone a nuestra disposición una serie de customizaciones <http://www.tei-c.org/guidelines/customization/> y hasta una plataforma, llamada Roma, para la creación y la manipulación de un esquema a nuestra medida.

En este apartado vamos a ver cómo funciona Roma y cómo construir un esquema a nuestra medida.
Hay dos opciones a la hora de construir un esquema:
* Elegir un esquema ya creado por la comunidad TEI, como puede ser la ya mencionada versión mínima, llamada TEI Lite o, más recientemente, TEI Simple, o la que incluye todos los elementos TEI All. En este enlace encontraréis los diferentes modelos. El programa oXygen también contiene estos esquemas.
* Crear un nuevo modelo a partir de la aplicación Roma. Aquí encontraréis las indicaciones ofrecidas por el Consorcio TEI.

Esta es la interfaz de inicio de la plataforma ROMA:

![Aplicación Roma, pantalla de inicio](img/L9_001.png)

 Las opciones disponibles son las siguientes:
 
* *Build up*: Construir un modelo personalizado a partir de una versión mínima con sólo los cuatro módulos obligatorios. El proceso consiste en añadir módulos y personalizar los elementos y atributos.
* *Reduce*: Construir un modelo personalizado a partir una versión máxima con todos los módulos TEI. El proceso consiste en eliminar módulos y elementos y atributos.
* *Create a new customization starting from a template*: Crear un modelo a partir de una de las plantillas propuestas por TEI.
* *Use or modify an existing TEI-defined customization*: Crear un modelo a partir de la modificación del modelo TEI Lite.
* *Upload a customization*: Sección para subir a la plataforma un modelo ya existente en forma de documento ODD.

Elegiremos la primera opción Build up, es decir, crearemos un esquema a partir de una versión mínima que sólo contiene los módulos obligatorios. La siguiente pantalla corresponde a los metadatos:

![Aplicación Roma, personalización](img/L9_002.png)
 
En este caso las opciones que se nos ofrecen son las siguientes:

* *Title*
* *Filename*
* *Namespace for new elements*
* *Prefix for TEI pattern names in schema*
* *Language*
* *Author name*
* *Description*

Cambiemos las informaciones por defecto por las nuestras y seleccionemos como lengua de la interfaz el “Español”:
 
![Aplicación Roma, cambio de idioma](img/L9_003.png)

Y guardamos el esquema, clicando el botón rojo “Save”.

Fijaros que lo único que ha cambiado es el nombre de nuestro esquema que en lugar de llamarse “My extension TEI”, ahora tiene el nombre que le hemos dado “Mi primer esquema”.

Veamos ahora las otras opciones:

1.	Nuevo: retrocede a la pantalla de inicio.
2.	Personalizar: corresponde a la pantalla donde hemos creado el título y los otros metadatos del esquema.
3.	Lengua: En este apartado tenemos la posibilidad de elegir entre diferentes lenguas, esto nos proporcionará una documentación de los elementos en la lengua escogida (siempre que exista una traducción). En nuestro caso, podemos escoger “Español”, aunque debemos tener en cuenta que la más actualizada y completa es la versión en inglés (Ya habéis visto en las Guías directrices como no todos los elementos y secciones están traducidas al español).
4.	Módulos: esta es una de las pantallas más importantes, pues es aquí donde elegiremos qué módulos vamos a incluir en nuestro esquema:
 
![Aplicación Roma, lista de los módulos](img/L9_004.png)

Como veis, la columna de la izquierda contiene todos y cada uno de los módulos TEI, mientras que el de la derecha recoge sólo los obligatorios: core, tei, header, textstructure. A partir de aquí, debemos saber a qué módulos pertenecen los fenómenos textuales que queremos codificar. Por lo general, si trabajamos con textos teatrales, tendremos que incluir el módulo drama, si trabajamos con poesía el módulo verse, si trabajamos con diccionarios el módulo dictionaries, etc.

Podemos acceder a cada uno de los módulos y ver todos los elementos que contiene. Por ejemplo, si accedemos al módulo textcrit, observamos la lista completa:

![Aplicación Roma, lista de elementos del módulo textcrit](img/L9_005.png)
 
Una vez al interno de los módulos podemos “Excluir” aquellos elementos que no necesitemos para nuestra codificación. En lo que concierne al “Nombre” conviene dejarlo tal y como está para no provocar confusiones con el sistema estándar TEI de nombres de elementos, es decir, si cambiamos, por ejemplo, `<app>` por `<aparato>`, la etiqueta en nuestro documento XML-TEI aparecería como `<aparato>` y no como `<app>`. Además, tenemos la posibilidad de modificar los atributos, manteniendo los que nos interesan y suprimiendo los que no necesitamos.

Al interior de cada uno de los elementos, tenemos la posibilidad de detallar ulteriormente la “Descripción” de ese elemento. Dicha descripción es la que aparecerá en el apartado correspondiente de la documentación. Por ejemplo, retomemos el elemento `<app>` e imaginemos que queremos encuadrarlo en nuestro proyecto, de manera que sea útil a las personas que elaborarán la codificación, o incluso, para nosotros mismos.

![Aplicación Roma, descripción personalizada de un elemento](img/L9_006.png)
 
Supongamos que queremos hacer la edición crítica de una obra lírica del siglo de Oro. Para ello, en primer lugar, deberemos seleccionar los módulos que nos interesen, en este caso, textcrit y verse. Pero también podemos prever que codificaremos los nombres de los personajes y los diferentes lugares que aparecen en el texto, en ese caso incluimos: namesdates.

Una vez añadidos los diferentes módulos que nos interesan veremos en la columna de la derecha los módulos seleccionados:

![Aplicación Roma, modulos seleccionados para el esquema](img/L9_007.png)

5.	Añadir elemento: A continuación, podríamos pasar a la pestaña “Añadir elemento”, en el caso que quisiéramos crear un nuevo elemento que no nos proporciona TEI; para ello, tendríamos que adjudicarle una clase de modelo y una clase de atributos. Esta práctica debe evitarse en línea de máxima a no ser que sea estrictamente necesario.
6.	Cambiar clase: Lo mismo sucede con esta pestaña; podría darse el caso que un determinado elemento no tuviera los atributos que necesitamos, en tal caso, podríamos modificarlos y añadir de nuevos en esta sección.
7.	Esquema: esta sección permite escoger el tipo de esquema que queremos: DTD, W3C, RelaxNG, etc.

Este es uno de los momentos cruciales, pues aquí es donde podremos obtener un esquema en el formato que deseemos. Las opciones que se nos ofrecen son las siguientes:

* Relax NG schema (compact syntax) .rnc
* Relax NG schema (XML syntax) .rng
* ISO Schematron
* Schematron
* W3C Schema .xsd
* DTD .dtd

Escogeremos la opción Relax NG schema (XML syntax) (no “compact syntax”) y pulsaremos “Generate”; acto seguido se nos descargará el esquema que hemos elaborado:
 
![Aplicación Roma, cambio de idioma](img/L9_008.png)

8.	Documentación: Permite escoger que tipo de formato se prefiere para la documentación del esquema. Tenemos la posibilidad de bajarnos en un único documento la descripción de cada uno de los elementos y atributos elegidos en nuestro esquema según las Guías directrices. Los formatos pueden ser:

* HTML web page
* PDF
* TEI Lite
* TEI ODD

La opción más útil es la HTML, pues nos generará un simple documento HTML donde tendremos todos los elementos y atributos incluidos en nuestro esquema para poder consultarlos fácilmente en forma de página web:

![Aplicación Roma, descarga de la documentación en html](img/L9_003.png)

9.	Guardar configuración personal: Esta pantalla también es de vital importancia porqué es la que genera el fichero ODD que veremos en el siguiente y último tema. En pocas palabras, se trata de un fichero XML que recoge todas las características del esquema personalizado y permite rehacerlo cuantas veces lo deseemos, conservando las modificaciones hechas. Si no se conserva este documento, no se podrá recuperar la personalización que hemos creado. 
10.	Sanity Checker: Permite comprobar las decisiones hechas para tu personalización. Normalmente, si no has incluido nuevos elementos o eliminado partes esenciales, suele dar positivo.


# V. Recursos

Aquí podréis ver el esquema Relax NG Lite que proponen la Guías directrices: <http://www.tei-c.org/release/xml/tei/custom/schema/relaxng/tei_lite.rng>. Lo podéis abrir con el programa oXygen e intentar entender la estructura (File > Open URL > Pegad la URL en “File URL” y pulsar “OK”).

## Lecturas y tutoriales: 

Eric van der Vlist, *Relax NG*, O’Reilly & Associates, 2003. Acceso al libro en versión digital <http://books.xmlschemata.org/relaxng/page2.html>.

OASIS Consortium, *Relax NG Tutorial* (Committee Specification 3 December 2001), <https://relaxng.org/tutorial-20011203.html>.

E. Van der Vlist, «Relax NG, Compared» (23 Enero 2002), XML.com <http://eric.van-der-vlist.com/blog/2006/07/06/2814_relax_ng_and_w3c_xml_schema_compared_continued/>