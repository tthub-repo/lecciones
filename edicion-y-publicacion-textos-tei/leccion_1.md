---
title: Introducción
author: Susanna Allés Torrent, Gabriel Calarco, Gimena del Rio Riande
date: 2022
layout: default
lang: es
---
 
Esta lección ofrece una primera aproximación a la **Text Encoding Initiative (TEI)**, un estándar de codificación informática de textos concebido especialmente para el trabajo académico en Humanidades y Ciencias Sociales. Abordamos algunos conceptos generales como la codificación de los textos, la utilidad de la TEI y sus campos de aplicación.
 
# 1. La codificación informática de los textos
 
En el ámbito de las humanidades y las ciencias sociales, el texto representa, en la mayoría de los casos, el punto de partida de muchas investigaciones. La introducción de métodos y herramientas propios de la ciencia informática llevaron hace ya más de veinte años a replantearse la importancia del texto y su procesamiento informático. La gran cantidad de textos a nuestra disposición conlleva la adopción de nuevas estrategias para la creación, la explotación y su conservación.
 
Comenzaremos por explicar algunos conceptos esenciales para entender qué son los lenguajes de marcado. Empecemos por la diferencia entre un texto digitalizado y un texto digital: mientras que el **texto digitalizado** puede ser definido como una colección de imágenes que reproducen las páginas de un libro en papel o similar (usualmente reunidas en un documento PDF), el **texto digital** se construye como una cadena de caracteres, reconocibles tanto para los lectores humanos como para las computadoras. Esto hace que el texto digital ofrezca la posibilidad de realizar algunas operaciones que no se encuentran disponibles para las digitalizaciones, como buscar una cadena de caracteres determinada, efectuar reemplazos automáticos o editar el contenido textual. Conviene aclarar que existen otros tipos de archivo en formato PDF. Junto a los textos digitalizados que aparecen en la pantalla como una imagen de la página impresa, también podemos encontrar documentos PDF que responden a las características del texto digital, ya sea porque fueron creados a partir de un procesador de texto o porque se aplicó un OCR ([Reconocimiento Óptico de Caracteres](https://es.wikipedia.org/wiki/Reconocimiento_%C3%B3ptico_de_caracteres)) sobre el documento digitalizado para que la cadena de caracteres del texto sea legible por la computadora.  
 
La forma más básica del texto digital es el **texto plano** (.txt), que solo contiene caracteres (entre ellos, los espacios), sin añadir ningún tipo de formato a los mismos. Por el contrario, el texto digital también puede ser enriquecido con información adicional sobre la estructura del texto y la forma en que este será presentado en los dispositivos; estos datos se incorporan mediante el uso de un **[lenguaje de marcado](https://es.wikipedia.org/wiki/Lenguaje_de_marcado)**. La iniciativa de marcado nace pues de la necesidad de procesar los textos desde un punto de vista informático, para que, en definitiva, no sea susceptible solo de una lectura "plana", sino para que sea procesable a través de múltiples herramientas como pueden ser programas de concordancias, análisis estilométricos, gráficos de frecuencias, segmentación gramatical o, sobre todo, su publicación web y la posibilidad de realizar búsquedas inteligentes.
 
Otro concepto importante para entender la función de la codificación informática de textos es el de los **metadatos**. Si entendemos un texto digital como un conjunto de datos (es decir, una sucesión de caracteres), toda la información referida a ellos (como su título, lengua en la que está escrito o su tipología textual) son sus metadatos. Los metadatos que pueden acompañar a los textos digitales son variados y existen varias propuestas de codificación con sus características particulares, pero todas apuntan a un mismo objetivo: proporcionar un contexto para el conjunto de datos que son los objetos digitales. Los metadatos cumplen un rol fundamental para el trabajo en humanidades, ya que permiten que los textos digitales sean clasificados, conservados y compartidos.
 
![Logo de la Text Encoding Initiative](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L1_001.png)
 
La [Text Encoding Initiative](http://www.tei-c.org/) surgió a finales de los años ochenta y fue la primera iniciativa científica destinada a la **codificación informática de textos**, actualmente es una de las más utilizadas y uno de los temas centrales en la disciplina de las humanidades. Este lenguaje de marcado nos permite estructurar tanto en lo formal como lo semántico los textos con los que deseamos trabajar de tal forma que estos puedan ser procesados y “entendidos” por sistemas informáticos, tanto para su presentación en ediciones digitales como para operaciones de [lectura distante](http://dictionaryworldliterature.org/index.php/Lectura_distante).
 
El sitio [TEI by Example](https://teibyexample.org/), dedicado a la difusión y la enseñanza de la Text Encoding Initiative,  nos ofrece la siguiente explicación sobre rol del marcado de textos con TEI:  
 
> Las computadoras solo pueden manejar datos explícitos. La función del marcado es representar material textual en forma digital a través del acto explicativo de la codificación del texto. El marcado descriptivo revela lo que el codificador piensa que son aspectos implícitos u ocultos de un texto y, por lo tanto, es un medio interpretativo que a menudo documenta la investigación académica junto a la información estructural sobre el texto. Para que esta investigación sea intercambiable, analizable, reutilizable y conservable, los textos en el campo de las humanidades deben codificarse de acuerdo con un estándar que defina un vocabulario, gramática y sintaxis comunes, dejando la implementación del estándar al codificador. Como resultado de los esfuerzos comunes de un grupo de humanistas digitales, surge la Text Encoding Initiative que propone un estándar de este tipo en sus *Guías directrices*. Estas pautas son totalmente adaptables y personalizables a los proyecto específicos de cada investigador, al tiempo que mejoran la compatibilidad con otros proyectos que utilizan este estándar (Traducción propia a partir del original en inglés: [TEI by Example](https://teibyexample.org/tutorials/TBED00v00.htm#summary)).
 
 
# 2. Aplicaciones prácticas y tipos de proyectos
 
Hay muchas razones para utilizar TEI, ya que permite capturar distinciones importantes en un texto en cualquier nivel que necesite un académico; gestionar enlaces complejos entre características textuales y entidades como personas y lugares; así como también registrar características materiales de un texto, intervenciones académicas, lecturas variantes y más. El uso más extendido de XML-TEI es, sin duda, la edición de textos. Esta es su aplicación principal y, de hecho, muchos de los proyectos de mayor envergadura contienen un componente editorial. En este sentido, podemos encontrar una gran variedad de enfoques que pueden abrazar todos los diferentes métodos y escuelas de la crítica textual, desde ediciones de textos modernos, a otras diplomáticas o de crítica genética e incluso auténticas ediciones críticas en línea.
 
## Edición como versiones de un texto 
 
Las posibilidades que ofrece la edición digital son múltiples, una opción muy utilizada es el trabajo de **comparación y presentación de textos en diferentes versiones**. En una aplicación de este concepto, la edición de *La Dama Boba* de Lope de Vega, realizada por el grupo [Prolope](http://prolope.uab.cat/) nos permite comparar los textos de diferentes testimonios de la obra en sus varios estadios, con una disposición en tres columnas:
 
![*La Dama Boba*](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L1_002.png)
<p align="center"> Fuente: <a href="http://damaboba.unibo.it/">http://damaboba.unibo.it/</a></p>
 
## Edición como traducción
 
Algunas ediciones aprovechan las posibilidades del medio digital para ofrecer los textos originales junto con sus **traducciones**, como por ejemplo la edición de las cartas de Van Gogh:
 
![Vincent Van Gogh, *The Letters*](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L1_002b.png)
<p align="center"> Fuente: <a href="http://vangoghletters.org/vg/letters.html">http://vangoghletters.org/vg/letters.html</a></p>

## Edición como enriquecimiento
Otra característica comúnmente adoptada en muchas ediciones digitales es la de acompañar al texto con una variedad de **elementos visuales** que permiten añadirle una nueva capa de información. Por ejemplo, en la edición de la *La Argentina Manuscrita* de Rui Díaz de Guzmán, realizada por el [HD CAICYT Lab](http://hdlab.space/) además de proporcionar la reproducción facsimilar de la fuente impresa a partir de la cual se realizó la edición, ciertos términos se encuentran destacados y permiten abrir una nota de información adicional al posar el cursor sobre ellos. Adicionalmente, si el término destacado se trata de un nombre de lugar, se incluye la geolocalización del mismo en el mapa. En la siguiente captura, se puede observar la nota que se despliega al situar el cursor sobre la palabra “Fortunadas”:
 
![*La Argentina Manuscrita*](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L1_003.png)
<p align="center"> Fuente: <a href="http://hdlab.space/La-Argentina-Manuscrita/">http://hdlab.space/La-Argentina-Manuscrita/</a></p>

## Edición para el análisis de redes 

Otra opción de procesamiento informático, ligado a la visualización de datos, que nos permiten los textos marcados con XML-TEI es el **análisis de redes**; es decir, el estudio computarizado de las relaciones que establecen entre sí diferentes entidades en un texto o corpus textual. En el siguiente ejemplo podemos observar un análisis de redes de las interacciones de los personajes de la obra *La vida es sueño* de Calderón de la Barca, que se ofrece en el corpus de ediciones digitales del sitio [Dracor](https://dracor.org/):
 
 
![Análisis de red de *La vida es sueño*](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L1_004.png)
<p align="center">Fuente: <a href="https://dracor.org/cal/la-vida-es-sueno">https://dracor.org/cal/la-vida-es-sueno</a></p>
 
## Proyectos de edición de autores

Otros proyectos van más allá y plantean sus ediciones como una **plataforma de recursos en torno a una obra o a un autor**; muchos de estos son verdaderos instrumentos pedagógicos y didácticos; véanse estos tres casos:
 
* [The World of Dante](http://www.worldofdante.org/)
* [Decameron Web](http://www.brown.edu/Departments/Italian_Studies/dweb/index.php)
* [The Chymistry of Isaac Newton](http://webapp1.dlib.indiana.edu/newton/)

## Catálogos

Dos recursos muy útiles a la hora de buscar ediciones en línea son los dos **catálogos** más completos hasta el momento:
 
* [G. Franzini, *A Catalogue of Digital Editions*](https://dig-ed-cat.acdh.oeaw.ac.at/)
* [P. Sahle, *Digital Scholarly Editions*](http://www.digitale-edition.de/index.html)
 
En este tutorial nos centraremos en esta primera aplicación del marcado XML-TEI, la edición de textos. Sin embargo, existen otros múltiples usos para este estándar sobre los que no nos detendremos aquí, como la catalogación de entradas en bibliotecas y archivos digitales, descripción de manuscritos, diccionarios, entre otros. 
 
# 3. La codificación de textos con TEI
 
## ¿Qué entendemos por texto?
 
Antes de seguir adelante, conviene que reflexionemos por un momento sobre **qué es un texto**. Una pregunta tan sencilla y obvia esconde en realidad una respuesta compleja y no siempre fácil de definir.
 
El texto es una idea abstracta que presupone la existencia de una secuencia de símbolos lingüísticos. ¿Pero dónde se encuentra exactamente un texto? ¿Lo debemos buscar en el original que escribió el autor o en todas las otras copias y ediciones posteriores? ¿Lo debemos extraer de la historia que se explica o en las intenciones últimas del autor? ¿O es quizás en la presentación y distribución de la página?
 
Consideremos por un momento en los siguientes ejemplos e intentemos reflexionar sobre dónde está el texto en cada uno:

![Geronimo de Quintana, *A la muy antigua, noble y coronada villa de Madrid*, 1629](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L1_005.png)

![Beatus Liebanensis, *Comentario del Apocalipsis*, códice de Fernando I y Dña. Sancha, s. XI ](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L1_006.jpg)

![*Diccionario de la lengua castellana*, Madrid: Real Academia Española, 1770](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L1_007.jpg)
 
 
Cada una de estas tipologías contiene aspectos diferentes y todos en realidad tienen un texto. El diccionario contiene voces y significados; el manuscrito antiguo puede contener diversas obras, el impreso del siglo XVII contiene un rico frontispicio con informaciones sobre la impresión, etc. Además hay otros aspectos que en realidad también forman parte del texto aunque sea desde un punto de vista físico: la estructura textual (párrafos, listas, tablas...), en el caso del manuscrito vemos letras dañadas, caracteres especiales, líneas del folio, abreviaciones, anotaciones manuscritas, correcciones de autor, errores, entre otra casuística. Todas estas variantes son tomadas en cuenta a la hora de emprender la codificación de un texto, especialmente, como veremos, en el modelado de los datos.
 
El texto, pues, no es solo el contenido textual sino que hay muchas otras variantes y componentes que debemos tener en cuenta a la hora de su codificación. Es importante que cuando afrontamos cualquier proyecto de marcado tengamos en cuenta todas y cada una de estas características que componen el "texto" en un sentido amplio. Por ello, será útil establecer una diferencia entre los conceptos de **texto** y **documento**. Mientras que el **documento** corresponde a un objeto en el mundo real que podemos escanear o digitalizar, como podría ser el caso de estas imágenes. El **texto**, en cambio, corresponde a la idea abstracta del contenido de ese documento, creado por y para una comunidad de lectores. Es esta última acepción de "texto" con la que en realidad trabajamos la mayoría de las veces al editar o codificar y requiere un análisis previo así como un cierto nivel de abstracción.
 
## Formato vs Contenido.
 
Existen diferentes tipos de lenguajes de marcado. Para simplificarlo, podemos mencionar dos tipos básicos de lenguajes informáticos, por un lado, están los que se ocupan de la **presentación** (en inglés, *Presentational markup*), es decir, de cuestiones como los diferentes tipos de fuentes, el diseño y a la distribución en la página web, etc.; y por otro lado, los **lenguajes descriptivos** (*Descriptive markup*) que se ocupan de señalar lo que son las cosas sin preocuparse de cómo aparecerán en la página web, sea cual sea su formato de salida. De hecho, en la mayoría de los casos su transformación y presentación se relega a una etapa posterior.
Un buen ejemplo de lenguaje de presentación es [HTML](https://es.wikipedia.org/wiki/HTML), que se ocupa de presentar los contenidos en los navegadores web; por el contrario, el lenguaje [XML](https://es.wikipedia.org/wiki/Extensible_Markup_Language) que utiliza TEI es descriptivo, pues se centra en el contenido semántico. Para comprender esta diferencia, imaginemos que queremos marcar el título principal de una obra: HTML lo marcaría de esta manera: `<b>Título</b>`, donde `<b>` está por “bold” o negrita; mientras que XML lo marcaría con otra etiqueta que indicara lo que es, no cómo debe aparecer: `<title type="principal">Título</title>`. El lenguaje XML-TEI, al centrarse en el contenido semántico y no en su presentación, no señala si una palabra irá o no en negrita, sino la naturaleza de ese elemento, en este caso un “título”. De esta manera, el contenido nunca está limitado a la perspectiva de un único editor, ni a un tipo determinado de uso, el texto existe y la presentación que se obtenga al final es independiente de este. Además, un documento XML puede ser transformado con facilidad a múltiples formatos, como doc, epub, html, pdf, etc. pero no siempre al revés. En definitiva, el hecho de separar en un texto la forma o su presentación de su contenido facilita la reutilización de un documento pues no contiene todavía los corsés del formato, de manera que su difusión y reciclaje es mucho más flexible.
 
## La codificación de un texto
 
Toda la información que queramos localizar y reutilizar debe ser marcada de una manera explícita a través de **marcas informáticas**. Sólo la información codificada informáticamente mediante estas marcas podrá ser buscada *a posteriori*, procesada y presentada.
 
Un marcado electrónico es un valor añadido al texto pues puede proporcionar múltiples anotaciones, difícilmente señalables en una edición en papel, como por ejemplo en qué secuencia un autor canceló y añadió ciertas correcciones.
 
Es importante antes de empezar a codificar saber qué elementos queremos aislar y cuáles son útiles para nuestro proyecto:
 
* **Divisiones estructurales dentro del texto**: título de la página, capítulo, escena, poema, línea, párrafo...
* **Elementos tipográficos puntuales**: cambios de letra, caracteres especiales...
* **Informaciones semánticas**: personas, lugares, eventos, fechas...
* **Otros elementos**: estructuras sintácticas, formas gramaticales, localización de ilustraciones, gráficos, tablas, imágenes...
 
La decisión, una vez más, dependerá de las informaciones que queramos recuperar y procesar informáticamente.
 
## ¿Cómo funciona  TEI?
 
La Text Encoding Initiative se ampara en primera instancia en el [Consorcio TEI](http://www.tei-c.org/about/organization/). Este consorcio compuesto por personas e instituciones es el responsable de desarrollar y mantener actualizadas las [***Guías directrices***](http://www.tei-c.org/Guidelines/) para el marcado de los textos en formato digital. Estas guías son una especie de manual de codificación o de recomendaciones de buenas prácticas que especifican una metodología concreta de codificación de los textos de manera que sean leídos y procesados por las computadoras.
 
A continuación, podemos leer una primera definición publicada en el sitio de TEI que nos será útil para empezar:
 
> Las *Guías directrices* para la codificación y el intercambio de textos electrónicos definen y documentan un lenguaje de marcado para la representación de las características estructurales, físicas y conceptuales de los textos. Su foco de atención es el marcado de documentos en Humanidades y Ciencias Sociales (aunque no exclusivamente), y en particular la representación de fuentes primarias para su explotación y análisis. Estas líneas directrices se expresan de forma modular, a través de esquemas XML extensibles, están acompañadas de una documentación detallada, y publicadas bajo una licencia en acceso abierto. Las *Guías directrices* son mantenidas y desarrolladas por el Consorcio TEI, a través de su Comité Técnico, con el respaldo y la participación de la comunidad TEI.
 
Veamos paso por paso los diferentes puntos básicos de esta definición:
 
* El núcleo central de la TEI son las ***Guías directrices*** que constituyen un extenso manual de uso y buenas prácticas. Su misión principal es proponer unas pautas claras para el marcado y el intercambio electrónico de los textos y ofrecer una documentación general y explicativa, que lamentablemente solo se encuentra disponible en inglés. Esta guía se actualiza periódicamente y desde el inicio de la Text Encoding Initiative varias versiones se han ido desarrollando. La versión actual es la P5 (donde P corresponde a *Proposal*) y se remontan al año 2007, aunque cada pocos meses la versión es actualizada con pequeñas mejoras.
* Las *Guías directrices* proponen un tipo concreto de lenguaje de marcado que consiste en aislar a través de **marcas** o **etiquetas** las características textuales, ya sean estructurales (como capítulos de libro, secciones, apartados, párrafos, estrofas, versos, etc.), como físicas (distribución de la página en columnas en un manuscrito), como conceptuales o semánticas (nombres de personas, de lugares, palabras clave, etc.).
* TEI es especialmente usado en las disciplinas **humanísticas**, **ciencias sociales** o **lingüística**, y en la representación de las **fuentes primarias**, tales como manuscritos (de hecho, TEI es también utilizada en algunas bibliotecas para la descripción y catalogación de sus fondos).
* El sistema de marcado TEI tiene una naturaleza modular que agrupa fenomenología diversa en un mismo **módulo**. Tiene cuatro obligatorios, que corresponden a elementos compartidos por todos y cada uno de los documentos TEI (como puede ser el elemento raíz, o el elemento párrafo). Esta característica modular permite customizar o personalizar el modelo de marcado que cada proyecto necesita.
* TEI se expresa a través del lenguaje estándar web **XML**, **Extensible Markup Language** o **[Lenguaje de Marcas Extensible](https://es.wikipedia.org/wiki/Extensible_Markup_Language)**.
* Las *Guías directrices* y otros materiales de la TEI (herramientas, catálogo de proyectos, etc.) son de **acceso abierto** y pueden consultarse libremente online, descargarse, reutilizarse e, incluso, ser susceptible de mejoras a través de la retroalimentación de los usuarios. Todo el material está disponible en [GitHub](https://github.com/TEIC/TEI).
 
## Ventajas de utilizar TEI
 
Las ventajas que ofrece el uso de TEI son múltiples y entre ellas podemos señalar:
 
* XML-TEI no depende de ningún software o programa informático y por tanto es **gratuito e independiente**. Un documento XML será siempre el mismo en cualquier sistema operativo o aplicación. Este hecho evita que se puedan dar situaciones catastróficas, en las que, por ejemplo, un programa con un formato propietario ya no se mantenga o no se utilice y los documentos queden obsoletos.
* XML-TEI ha sido **diseñado por y para la comunidad científica** que es la encargada en última instancia de promover y mejorar las guías de marcado. Cuantos más usuarios y más gente implicada haya utilizando el mismo sistema de marcado, más se avanzará hacia una propuesta sólida de codificación.
* Un marcado a través de un estándar web, independiente de cualquier software o plataforma web, como es el caso de en XML-TEI, permite y facilita la **reutilización del mismo material: en diferentes formatos**, en contextos diferentes, por diferentes usuarios. Esto permite que proyectos posteriores o contemporáneos puedan establecer un vínculo y un uso diferente del material publicado, evitando el tener que empezar de cero y avanzando en el conocimiento.
* XML-TEI se centra en el significado y el **contenido** del texto y no en su apariencia o en su presentación final (es decir, no es tan relevante el señalar un título en negrita, como definir que efectivamente se trata de un “título”).
  
## En resumen
 
A lo largo de esta lección realizamos una primera aproximación a la codificación informática de textos y presentamos las principales características de la TEI desde un punto de vista teórico. A modo de conclusión, lo que el marcado de un texto con TEI nos permite es codificar información que dependiendo del tipo de proyecto en el que se realice el marcado, puede ser de muy variada naturaleza, de forma que esta sea legible y recuperable informáticamente.
 
Si te interesa seguir ahondando en la historia de la Text Encoding Inititative y en la organización del Consorcio TEI, puedes encontrar más información sobre estos temas en el [anexo](link).
 
En la siguiente lección comenzaremos a introducirnos en la práctica del marcado TEI y echaremos un vistazo a un archivo XML para empezar a familiarizarnos con este formato de archivos.
 
# 4. Práctica: Ediciones digitales con TEI
 
Te invitamos a visitar los sitios de las siguientes ediciones digitales para compararlas entre sí:

* [The World of Dante](http://www.worldofdante.org/)
* [Poesía Medieval](http://hdlab.space//Poesia-Medieval/)
* [Mini Lazarillo](https://minilazarillo.github.io/)
* [De oratione dominica](https://scholarlyediting.org/2016/editions/de-oratione-dominica.dunning.html.type=regularized.html)
* [Van Gogh’s letters](http://vangoghletters.org/vg/)
 
Las siguientes preguntas pueden servir como guía para comenzar a pensar los diferentes enfoques de la edición digital que cada una de estas propuestas presenta, sin embargo, son solo un punto de partida, y no agotan las posibilidades de análisis que pueden surgir de esta comparación.
 
* ¿A qué tipo de público está dirigida la edición?
* ¿Qué posibilidades de interacción con el texto ofrecen al lector?
* ¿Qué recursos complementarios a la presentación del texto ofrecen?
* ¿Cuánta información se proporciona sobre el contexto de publicación de la edición?
* ¿Bajo qué licencia se publica el contenido?
* ¿La edición es producto de un trabajo individual o de la colaboración de un equipo?
