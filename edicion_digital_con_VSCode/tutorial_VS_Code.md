---
title: Edición filológica digital con Visual Studio Code
author: Gabriel Calarco, Carles Márquez Molins
date: 2022
layout: default
lang: es
---

En este breve tutorial explicamos cómo utilizar el software de código abierto [Visual Studio Code](https://code.visualstudio.com/) para el trabajo con documentos en XML-TEI. Además, mostramos cómo instalar el plugin [Scholarly XML](https://marketplace.visualstudio.com/items?itemName=raffazizzi.sxml) creado por Raffaele Viglianti y concebido para validar este tipo de archivos con esquemas RELAX NG y facilitar el autocompletado, junto con otras extensiones de interés para el trabajo de edición filológica digital

# 1. Textos digitales y editores de código

Antes de entrar en detalles sobre qué es [Visual Studio Code](https://code.visualstudio.com/) y para qué se utiliza es importante tener en mente algunas definiciones básicas sobre el trabajo con textos en las Humanidades Digitales. Comencemos por la diferencia entre un texto digitalizado y un texto digital: mientras que el texto digitalizado puede ser definido como una colección de imágenes que reproducen las páginas de un libro en papel o similar (normalmente reunidas en un documento PDF), el texto digital se construye como una cadena de caracteres, reconocibles tanto para los lectores humanos como para las computadoras. Esto hace que el texto digital ofrezca la posibilidad de realizar algunas operaciones que no se encuentran disponibles para las digitalizaciones, como buscar una cadena de caracteres determinada, efectuar reemplazos automáticos o editar el contenido textual.  

La forma más básica del texto digital es el texto plano (.txt), que sólo contiene caracteres (entre ellos, los espacios), sin añadir ningún tipo de formato a los mismos. Por otra parte, el texto digital también puede ser enriquecido con información adicional sobre la estructura del texto y la forma en que este será presentado en los dispositivos; estos datos se incorporan mediante el uso de un lenguaje de marcado, como el que ofrece la [Text Encoding Initiative](https://tei-c.org/) (TEI). Este lenguaje de marcado permite estructurar formal y semánticamente los textos con los que deseamos trabajar de tal forma que estos puedan ser procesados y “entendidos” por sistemas informáticos, tanto para su presentación en ediciones digitales como para operaciones de lectura distante (si deseas saber más sobre TEI puedes dirigirte a [nuestros tutoriales](https://tthub.io/aprende) sobre edición de textos con TEI).

Cuando queremos crear o editar un documento XML-TEI, los procesadores de texto más usados, como Microsoft Word o WordPad, no nos son de utilidad, ya que fácilmente se pueden agregar accidentalmente formatos y caracteres extra y/o invisibles que pueden generar problemas. Los editores de texto plano son una opción más adecuada, pero la mejor alternativa para trabajar en este tipo de documentos es utilizar un programa específicamente diseñado para editar códigos informáticos, es decir, un editor de código.


# 2. VS Code, un editor gratuito y de código abierto 

[Visual Studio Code](https://code.visualstudio.com/) (normalmente abreviado VS Code) es un editor de código abierto que nos ofrece una gran variedad de funciones adicionales a las que posee un editor de texto plano. Desde el punto de vista de la edición filológica digital, VS Code brinda la posibilidad de instalar diversas extensiones entre las cuales encontramos algunas específicamente desarrolladas para trabajar con documentos XML-TEI.

Para utilizar VS Code solo debes ir a la [página de descarga de la aplicación](https://code.visualstudio.com/Download) y seleccionar el instalador correspondiente según tu sistema operativo. Al ejecutar el archivo descargado el instalador te irá guiando por los diferentes pasos. Una vez completada la instalación podemos abrir el programa y empezar a editar nuestro primer archivo. Puedes abrir un archivo nuevo en blanco con los comandos `ctrl + O` o seleccionando la opción `New file` de la pestaña `File` del menú superior. Alternativamente puedes abrir una carpeta completa y explorar su contenido (subcarpetas y archivos) desde la barra izquierda del programa en la pestaña `Explorer` (el primer ícono del menú de la barra izquierda del editor), para esto puedes utilizar los comandos `crtl + K, ctrl+O` o seleccionando la opción `Open folder` de la pestaña `File`.

Como complemento al tutorial, también te ofrecemos esta tabla con alguno de los atajos que pueden ser de más utilidad a la hora de trabajar con TEI en VS Code. Os sugerimos que la tengas a mano cuando trabajes con este programa, ya que te ahorrará tiempo a la hora de codificar tus textos:


| **Atajo del teclado**        | **Función**                                          |
|------------------------------|------------------------------------------------------|
| Ctrl + C                     | Copiar                                               |
| Ctrl + X                     | Cortar                                               |
| Ctrl + V                     | Pegar                                                |
| Ctrl + S                     | Guardar los cambios en el documento                  |
| Alt + ↑ o ↓                  | Mover línea hacia arriba o hacia abajo               |
| Ctrl + Shift + K             | Borrar línea                                         |
| Ctrl + }                     | Convertir línea en comentario (y viceversa)          |
| Ctrl + ‘+’                   | Incrementar el aumento de la pantalla                |
| Ctrl + -                     | Disminuir el aumento de la pantalla                  |
| Ctrl + F                     | Buscar secuencia de caracteres en el documento       |
| Ctrl + H                     | Buscar y reemplazar                                  |
| Ctrl + Shift + P             | Abre la barra de comandos (para funciones avanzadas) |

Para más información, pueden consultar la [lista completa de atajos de VS Code para Windows](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf) o presionar `Crtl+K` seguido de `Ctrl+S` en VS Code para abrir la lista de atajos y editarlos. 

Como ya señalamos, una de las principales ventajas de utilizar VS Code como editor de código es que nos permite acceder a una variedad de extensiones que le añaden nuevas funcionalidades al programa. A continuación instalaremos diferentes extensiones que nos permitirán realizar un trabajo completo a la hora de trabajar con documentos en XML-TEI, desde la codificación a una simple trasformación. 

# 3. Scholarly XML

Una de las extensiones que nos resultarán más útiles al momento de trabajar con archivos TEI en VS Code es [Scholarly XML](https://marketplace.visualstudio.com/items?itemName=raffazizzi.sxml), ya que fue diseñada especialmente para la codificación de textos en XML-TEI. 

Para instalar esta extensión debes seleccionar el ícono de extensiones del menú lateral de VS Code (paso 1) y en el cuadro de búsqueda ingresar la palabra `schorlarly` (paso 2). Cuando aparezca la opción que desees utilizar, solo debes presionar el botón `install` (paso 3):

![Pasos para instalar la extensión Scholarly XML en VS Code.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen1.png)

Instalar esta extensión en VS Code nos permitirá incorporar algunas funciones que nos serán de gran utilidad:
 
* Siempre que nuestro documento TEI se encuentre asociado a un esquema Relax NG, VS Code nos informará si nuestros archivos son válidos y están bien formados.
* Si estamos trabajando en TEI recibiremos sugerencias de elementos que podemos utilizar de acuerdo con el esquema con el que estemos trabajando.
* Permite seleccionar una porción de texto y utilizar el atajo `Ctrl+E` para marcarlo con una etiqueta de inicio al comienzo y una de cierre al final.

![Elementos sugeridos por Scholarly XML en VS Code en base al esquema.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen1b.jpg)

Gracias a estas funciones adicionales (en particular la posibilidad de validar documentos a partir de un esquema, que resulta fundamental para el trabajo con este tipo de archivos), VS Code es una herramienta sumamente útil y efectiva para la edición de textos digitales con TEI, cuyas prestaciones son coparables a las de los programas con licencias pagas, aunque con la ventaja de que al tratarse de una aplicación gratuita se encuentra al alcance de toda la comunidad.

# 4. TEI Publisher

VS Code nos permite realizar visualizaciones de los textos codificados con TEI que pueden servirnos como una primera aproximación a las transformaciones XSLT. Sin entrar en mayores detalles, baste por el momento decir que las transformaciones XSLT ([eXtensible Stylesheet Language Transformations](https://es.wikipedia.org/wiki/Extensible_Stylesheet_Language_Transformations)) nos permiten traducir nuestros documentos XML-TEI a otros dialectos del lenguaje XML. En proyectos de Humanidades Digitales, y especialmente en el campo de la edición digital filológica, la transformación más habitual es hacia un formato web en [HTML](https://es.wikipedia.org/wiki/HTML). Esta transformación, de XML a HTML a través de XSLT, nos permitirá poner nuestros textos marcados con TEI en línea a disposición del público y determinar qué aspectos del marcado TEI se reflejarán en la presentación del texto en el navegador y de qué forma. Sin embargo, este proceso requiere del manejo de varias tecnologías complementarias cuya curva de aprendizaje, si bien está lejos de ser inaccesible, requiere de una dedicación considerable, de la que en muchos casos puede no disponerse. Por este motivo se han desarrollado algunas herramientas que ayudan a simplificar este proceso. Una de las principales iniciativas en las que se ha venido trabajando en este sentido es [TEI Publisher](https://teipublisher.com/index.html), un proyecto colaborativo y sin fines de lucro, que ofrece una [plataforma en línea](https://teipublisher.com/exist/apps/tei-publisher/index.html?tab=0) orientada a la edición digital de textos codificados en XML-TEI. Recientemente TEI Publisher desarrolló una extensión para VS Code que nos permite elegir entre varias [hojas de estilo](https://es.wikipedia.org/wiki/Hoja_de_estilo) para generar visualizaciones de nuestros textos marcados con TEI. Para instalar esta extensión debes ir a la pestaña de extensiones del VS Code (Paso 1), ingresar el texto “TEI Publisher” en el buscador (2) y hacer clic en el botón “install” (3):

![Búsqueda de la extensión.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen2.png)


Una vez que se complete la instalación verás que un nuevo ícono con el logo de *TEI Publisher* aparece en la barra lateral izquierda, debajo de la pestaña de extensiones. En ese ícono podremos encontrar la primera de dos funciones que nos ofrece *TEI Publisher* para trabajar con archivos TEI en VS Code, que consiste en un buscador de identificadores permanentes para el marcado de entidades. Para usar esta herramienta, primero debes abrir la pestaña de *TEI Publisher* (Paso 1), ingresar el nombre de la entidad que deseas marcar en el cuadro de búsqueda (2), y opcionalmente también puedes seleccionar el tipo de entidad que vas a buscar (personas, lugares, organizaciones o términos) (3). Después de hacer clic en el botón azul con una la lupa (4), aparecerá una lista de resultados, a continuación, debes seleccionar el nombre de la entidad en el texto que estás marcando (5) y hacer clic en el botón con el signo `+` que aparece al lado del resultado que mejor se ajuste a tu búsqueda (6). El resultado será que la extensión introducirá las etiquetas del elemento TEI que corresponde al tipo de entidad que estamos marcando y añadirá un atributo `@ref` cuyo valor es un identificador permanente proporcionado por la DNB ([*Deutschen National Bibliothek*](https://www.dnb.de/EN/Professionell/Standardisierung/GND/gnd_node.html)):

![Marcado de entidades con la extensión de TEI Publisher.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen3.png)


Esta función puede tener su utilidad para facilitar un marcado fuertemente centrado en el reconocimiento de entidades; sin embargo, no es el motivo principal por el cual instalamos la extensión. Como ya anunciamos nuestro objetivo es obtener una primera visualización de nuestros textos codificados con TEI, con este fin vamos a usar la segunda función que nos ofrece la extensión de *TEI Publisher*. Esta función solo aparece visible en la pantalla cuando tenemos un documento XML-TEI abierto en el VS Code, y lo podemos encontrar en la barra superior en el costado derecho. Al hacer clic en este ícono se desplegará una lista de hojas de estilo en formato ODD entre las cuales podemos elegir:

![Selección de plantilla de estilo con la extensión de TEI Publisher.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen4.png)



Si seleccionamos la primera opción, por ejemplo, y se la aplicamos a un texto en prosa codificado con TEI, obtendremos el siguiente resultado:

![Resultado de la visualización en HTML con la extensión de TEI Publisher.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen5.png)

Puedes probar otras alternativas de hojas de estilo sobre sus archivos TEI y comparar los resultados. Encontrarás que algunas ofrecen mejores resultados que otras, eso dependerá del tipo de texto con el que estemos trabajando y principalmente de la propuesta de marcado que hayamos adoptado. Sin embargo, debes tener en cuenta que esta función está pensada para generar una previsualización rápida de los textos y no para su presentación final al público. Aunque esta extensión nos ofrece la posibilidad de generar una visualización de nuestros archivos XML mientras estamos trabajando en VS Code, dista mucho de agotar todas las posibilidades de presentación que podemos generar a partir de nuestros textos marcados con TEI.

# 5. Otras extensiones para XML-TEI en VS Code

A continuación, se presentarán brevemente otras 4 extensiones que pueden ser de utilidad para trabajar con XML-TEI. Son 1) *Git History*; 2) *XML*; 3) *XML Tools* y 4) *xslt-transform*.

## 5.1. Git y Git History

El editor VS Code posee soporte nativo para Git, lo único que debemos hacer es instalar este control de versiones para nuestro sistema operativo descargándolo desde el siguiente enlace: https://git-scm.com/downloads. 

Primeramente nos acercaremos al control de código fuente de VS Code al que se puede acceder con el atajo de teclado `Ctrl + Mayús + G`. 

![Control de código fuente en VS Code.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen6.png)


En segundo lugar, abrimos una carpeta que ya contenga un repositorio Git. Si todavía no tenemos una, tendremos que clonarla desde GitHub. Aquí es importante señalar que es preciso estar registrado en GitHub para poder emplear Git. El registro es gratuito, y la plataforma GitHub nos permitirá, entre otras cosas, almacenar y compartir nuestro código. A continuación, abriremos la carpeta que contenga el repositorio Git.

![Carpeta que contiene el repositorio git.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen7.png)

Una vez abierta la carpeta, podemos seleccionar uno de los archivos y pedirle a Git que nos muestre el historial de este. Para ello, solicitaremos acceso al historial del archivo. En las imágenes siguientes se muestra, primero, cómo acceder a la solicitud del historial y, segundo, la visualización del historial del archivo, desde el que se pueden realizar acciones como acceder a su localización en GitHub.

![Solicitud del historial del archivo.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen8.png)


![Visualización del historial del archivo](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen9.png)

Los objetivos de [*Git History*](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory) son: 1) ver y buscar registros de Git al tiempo que gráficos y detalles; 2) visualizar una copia previa del trabajo; 3) visualizar y buscar en el historial (por ejemplo, visualizar el historial de toda o de una de las ramas (*branches*); esto es lo que se denomina Git log; o visualizar el historial de un autor). Mediante esta extensión también se pueden comparar ramas, compromisos (*commit*) o comparar archivos entre compromisos.

## 5.2. XML

La extensión [*XML*](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-xml) es una distribución desarrollada por RedHat, quienes han contribuido, por ejemplo, al desarrollo de distribuciones de Linux como Fedora o de programas como Libreoffice. Esta extensión se centra en dotar a VS Code de las herramientas necesarias para reconocer adecuadamente el XML. Así, permite el cierre automático de las etiquetas (por ejemplo, al escribir `<p>`, también se escribirá automáticamente `</p>`). También añade soporte para XSL y para renombrar etiquetas. Este segundo funciona de la siguiente manera:

En primer lugar, seleccionamos un fragmento de código para el cambio de nombre del símbolo. A continuación, seleccionamos cuál es el símbolo por el que queremos reemplazar el símbolo actual. En este caso reemplazaremos `<p>` y `</p>` por `<l>` y `</l>`. La primera imagen que sigue a esta explicación muestra el fragmento de código seleccionado y el menú desde el que seleccionaremos la opción de renombrar el símbolo.

![Cambio de nombre del símbolo.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen10.png)

En esta segunda imagen vemos cuál es el símbolo por el que decidimos reemplazar el símbolo actual.

![Paso previo al reemplazo](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen11.png)

Finalmente, visualizamos el resultado en VS Code. Como habíamos dicho, en este caso hemos reemplazado `<p>` y `</p>` por `<l>` y `</l>`.

![Resultado en VS Code.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen12.png)


Pueden consultarse todas las funciones de esta extensión en el enlace facilitado anteriormente.

## 5.3. XML Tools

Por otro lado, [*XML Tools*](https://marketplace.visualstudio.com/items?itemName=DotJoshJohnson.xml) tiene una serie de características que son: 1) formato del XML, 2) visualización del árbol de XML (es decir, cómo está estructurado el documento), evaluación de XPath –lenguaje pensado para navegar y parsear los documentos XML–; 3) enhebrado de XQuery –lenguaje pensado para consultar documentos XML–; 4) ejecución de XQuery y 5) compleción del código de XQuery. 

Veamos un ejemplo de otra de sus funciones, simplificar el XML:

![Nuestro código en XML.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen13.png)



![Búsqueda en el panel de comandos del proceso de simplificación de XML.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen14.png)


La caja de comandos se puede abrir con `Ctrl+shift+P` o haciendo clic derecho en cualquier punto del documento y seleccionando dicho panel.

![Resultado del XML simplificado.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen15.png)


## 5.4. xslt-transform

El cometido de la última extensión, [*xslt-transform*](https://marketplace.visualstudio.com/items?itemName=SvenAGN.xslt-transform), es transformar el XML en una salida HTML o un PDF mediante el lenguaje XSLT. Mostraremos un ejemplo de cómo transformar un XML en HTML en VS Code:

En primer lugar, instalamos la extensión *xslt-transform* y, seguidamente, abrimos nuestro archivo en VS Code. 
 
![Nuestro archivo en VS Code.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen16.png)

En segundo lugar, buscamos el comando que nos permite hacer la transformación mediante XSLT (XSLT: Run Transformation).

![Comando XSLT: Run Transformation](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen17.png)


Tras este paso, cargaremos el archivo .xsl o .xslt que hayamos preparado para la transformación. En nuestro caso, hemos partido de un archivo .xsl que ha generado Susanna Allés Torrent y lo hemos modificado para los propósitos de este tutorial. Después de esto, guardaremos el archivo resultante de la transformación como .html y disfrutaremos del resultado, que puede verse en la última imagen.

![Guardamos el archivo como .html](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen18.png)



![Resultado en HTML.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion_digital_con_VSCode/img/Imagen19.png)



# 6. Conclusiones

Como hemos visto a lo largo del tutorial, VS Code destaca, entre otras cosas, por ser un editor de código abierto y de carácter gratuito, lo que lo convierte en una herramienta accesible para cualquier tipo de usuario. Además, hemos aprendido a instalar extensiones en VS Code, unos añadidos que le aportan gran versatilidad a este programa. En primer lugar, nos hemos centrado en la extensión *Scholarly XML* y en *TEI Publisher*, las cuales nos serán de gran ayuda al trabajar en XML-TEI. También se ha ofrecido una tabla con los atajos más habituales y útiles para VS Code. Por otra parte, hemos hecho un breve repaso de otras extensiones que pueden resultar provechosas para todo aquel que desee trabajar en XML-TEI con VS Code (*Git History*, *XML*, *XML Tools* y *xslt-transform*). En definitiva, VS Code es un programa con mucho potencial –buena parte de él se lo añaden las extensiones– y que nos va a permitir trabajar cómodamente con XML, con otros lenguajes de marcado e incluso con lenguajes de programación. 
