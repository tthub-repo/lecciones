---
title: Edición filológica digital con Visual Studio Code
author: Gabriel Calarco y Carles Márquez Molins
date: 2022
layout: default
lang: es
---

# Edición filológica digital con Visual Studio Code

# 1. Textos digitales y editores de código

Antes de entrar en detalles sobre qué es Visual Studio Code y para que se utiliza es importante tener en mente algunas definiciones básicas sobre el trabajo con textos en las Humanidades Digitales. Comencemos por la diferencia entre un texto digitalizado y un texto digital: mientras que el texto digitalizado puede ser definido como una colección de imágenes que reproducen las páginas de un libro en papel o similar (usualmente reunidas en un documento PDF), el texto digital se construye como una cadena de caracteres, reconocibles tanto para los lectores humanos como para las computadoras. Esto hace que el texto digital ofrezca la posibilidad de realizar algunas operaciones que no se encuentran disponibles para las digitalizaciones, como buscar una cadena de caracteres determinada, efectuar reemplazos automáticos o editar el contenido textual.  
La forma más básica del texto digital es el texto plano (.txt), que solo contiene caracteres (entre ellos, los espacios), sin añadir ningún tipo de formato a los mismos. Por otra parte, el texto digital también puede ser enriquecido con información adicional sobre la estructura del texto y la forma en que este será presentado en los dispositivos; estos datos se incorporan mediante el uso de un lenguaje de marcado, como el que ofrece la Text Encoding Initiative (TEI). Este lenguaje de marcado permite estructurar tanto en lo formal como lo semántico los textos con los que deseamos trabajar de tal forma que estos puedan ser procesados y “entendidos” por sistemas informáticos, tanto para su presentación en ediciones digitales como para operaciones de lectura distante (si deseas saber más sobre TEI puedes dirigirte a nuestros tutoriales sobre edición de textos con TEI).
Cuando queremos crear o editar un documento TEI, los procesadores de texto más usados, como Microsoft Word o WordPad, no nos serán de utilidad, ya que fácilmente se pueden agregar accidentalmente formatos y caracteres extra y/o invisibles que pueden generar problemas. Los editores de texto plano son una opción más adecuada, pero la mejor alternativa para trabajar en este tipo de documentos es utilizar un programa específicamente diseñado para editar códigos informáticos, es decir, un editor de código.


# 2. Visual Studio Code, un editor gratuito y de código abierto 

[Visual Studio Code](https://code.visualstudio.com/) (usualmente abreviado VS Code) es un editor de código gratuito que nos ofrece una gran variedad de funciones adicionales a las que puede ofrecer un editor de texto plano. Una de las principales ventajas de VS Code es que nos ofrece la posibilidad de instalar extensiones con funciones adicionales, entre las cuales podemos encontrar algunas específicamente desarrolladas para trabajar con documentos XML-TEI.
Para utilizar VS Code solo debes ir a la 
[página de descarga de la aplicación](https://code.visualstudio.com/Download)  y seleccionar el instalador correspondiente según tu sistema operativo. Al ejecutar el archivo descargado el instalador te irá guiando por los diferentes pasos de la instalación.
Una vez completada la instalación podemos abrir el programa y empezar a editar nuestro primer archivo. Puedes abrir un archivo nuevo en blanco con los comandos “ctrl + O” o seleccionando la opción “New file” de la pestaña “File” del menú superior. Alternativamente puedes abrir una carpeta completa y explorar su su contenido (subcarpetas y archivos) desde la barra izquierda del programa en la pestaña “explorer” (el primer ícono del menú de la barra izquierda del editor), para esto puedes utilizar los comandos crtl + K, ctrl+O` o seleccionando la opción “Open folder” de la pestaña “File”.
Como complemento al tutorial, también te ofrecemos esta tabla con alguno de los atajos que pueden ser de más utilidad a la hora de trabajar con TEI en VS Code. Te sugiero que la tengas a mano cuando utilices VS Code, ya que te ahorrará tiempo a la hora de trabajar allí en tus textos:

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

Para más información, pueden consultar la [lista completa de atajos de VS Code para Windows](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf) o presionar ‘Crtl+K’ seguido de ‘Ctrl+S’ en VS Code para abrir la lista de atajos y editarlos. 
Como ya señalamos, una de las principales ventajas de utilizar VS Code como editor de código es que nos permite acceder a una variedad de extensiones que le añaden nuevas funcionalidades al programa. A continuación explicaremos brevemente algunas de las que pueden llegar a resultar más útiles para editar archivos codificados con TEI.

# 3. Scholarly XML 

Una de las extensiones que nos resultarán más útiles al momento de trabajar sobre archivos TEI en VS Code es *Scholarly XML*, ya que fue diseñada especialmente para la codificación de textos en XML-TEI y nos permitirá incorporar algunas funciones que nos serán de gran utilidad:
 
* Siempre que nuestro documento TEI se encuentre asociado a un esquema Relax NG, VS Code nos informará si nuestros archivos son válidos y están bien formados.

* Si estamos trabajando en TEI recibiremos sugerencias de elementos que podemos utilizar de acuerdo con el esquema con el que estemos trabajando.

* Permite seleccionar una porción de texto y utilizar el atajo ‘*Ctrl+E*’ para marcarlo con una etiqueta de inicio al comienzo y una de cierre al final.

Para instalar esta extensión debes seleccionar el ícono de extensiones del menú lateral de VS Code (paso 1) y en el cuadro de búsqueda ingresar la palabra “*schorlarly*” (paso 2). Cuando aparezca la opción de deseamos utilizar, solo debes presionar el botón “*install*” (paso 3):

![Fig. 1 Pasos para instalar la extensión Scholarly XML en VS Code.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen1.png)

<!-- Fig. 1 Pasos para instalar la extensión Scholarly XML en VS Code. -->

# 4. TEI Publisher

VS Code nos permite realizar visualizaciones de los textos codificados con TEI que pueden servirnos como una primera aproximación a las transformaciones XSLT. Sin entrar en mayores detalles, baste por el momento decir que las transformaciones XSLT ([eXtensible Stylesheet Language Transformations](https://es.wikipedia.org/wiki/Extensible_Stylesheet_Language_Transformations)) nos permiten traducir nuestros documentos XML-TEI a otros dialectos del lenguaje XML. En proyectos de Humanidades Digitales, y especialmente en el campo de la Edición Digital Filológica, la transformación más habitual es a [HTML](https://es.wikipedia.org/wiki/HTML), ya que este formato nos permitirá poner nuestros textos marcados con TEI a disposición del público y determinar qué aspectos del marcado TEI se reflejarán en la presentación del texto en el navegador y de qué forma. Sin embargo, este proceso requiere del manejo de varias tecnologías complementarias cuya curva de aprendizaje, si bien está lejos de ser inaccesible, requiere de una dedicación considerable, de la que en muchos casos puede no disponerse. Por este motivo se han desarrollado algunas herramientas que ayudan a simplificar este proceso. Una de las principales iniciativas en las que se ha venido trabajando en este sentido es [TEI Publisher](https://teipublisher.com/index.html), un proyecto colaborativo y sin fin de lucro, que ofrece una [plataforma en línea](https://teipublisher.com/exist/apps/tei-publisher/index.html?tab=0) orientada a la edición digital de textos codificados en XML-TEI Recientemente TEI Publisher desarrolló una extensión para VS Code que nos permite elegir entre varias [hojas de estilo](https://es.wikipedia.org/wiki/Hoja_de_estilo) para generar visualizaciones de nuestros textos marcados con TEI. Para instalar esta extensión debes ir a la pestaña de extensiones del VS Code (1), ingresar el texto “TEI Publisher” en el buscador (2) y hacer clic en el botón “install” (3):

![Fig. 2 Búsqueda de la extensión.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen2.png)

<!-- Fig. 2 Búsqueda de la extensión. -->

Una vez que se complete la instalación verás que un nuevo ícono con el logo de *TEI Publisher* aparece en la barra lateral izquierda, debajo de la pestaña de extensiones. En ese ícono podremos encontrar la primera de dos funciones que nos ofrece *TEI Publisher* para trabajar con archivos TEI en VS Code, que consiste en un buscador de identificadores permanentes para el marcado de entidades (puedes volver a la unidad anterior para refrescar lo que aprendimos sobre el marcado de entidades). Para usar esta herramienta, primero debes abrir la pestaña de *TEI Publisher* (1), ingresar el nombre de la entidad que deseas marcar en el cuadro de búsqueda (2), y opcionalmente también puedes seleccionar el tipo de entidad que vas a buscar (personas, lugares, organizaciones o términos) (3). Luego de hacer clic en el botón azul con una la lupa (4), aparecerá una lista de resultados, a continuación, debes seleccionar el nombre de la entidad en el texto que estás marcando (5) y hacer clic en el botón con el signo “+” que aparece al lado del resultado que mejor se ajuste a tu búsqueda (6). El resultado será que la extensión introducirá las etiquetas del elemento TEI que corresponde al tipo de entidad que estamos marcando y añadirá un atributo @ref cuyo valor es un identificador permanente proporcionado por la DNB (*Deutschen National Bibliothek* - Biblioteca Nacional Alemana):

![Fig. 3. Marcado de entidades con la extensión de TEI Publisher.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen3.png)

<!-- Fig. 3. Marcado de entidades con la extensión de TEI Publisher. -->


Esta función puede tener su utilidad para facilitar un marcado fuertemente centrado en el reconocimiento de entidades; sin embargo, no es el motivo principal por el cual instalamos la extensión. Como ya anunciamos nuestro objetivo es obtener una primera visualización de nuestros textos codificados con TEI, con este fin vamos a usar la segunda función que nos ofrece la extensión de *TEI Publisher*. Esta función solo aparece visible en la pantalla cuando tenemos un documento XML-TEI abierto en el VS Code, y lo podemos encontrar en la barra superior en el costado derecho. Al hacer clic en este ícono se desplegará una lista de hojas de estilo en formato ODD entre las cuales podemos elegir:

![Fig. 4. Selección de plantilla de estilo con la extensión de TEI Publisher.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen4.png)

<!-- Fig. 4. Selección de plantilla de estilo con la extensión de TEI Publisher. -->


Si seleccionamos la primera opción, por ejemplo, y se la aplicamos a un texto en prosa codificado con TEI, obtendremos el siguiente resultado:

![Fig. 5. Resultado de la visualización en HTML con la extensión de TEI Publisher.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen5.png)

<!-- Fig. 5. Resultado de la visualización en HTML con la extensión de *TEI Publisher*. -->

Puedes probar otras alternativas de hojas de estilo sobre sus archivos TEI y comparar los resultados. Encontrarás que algunas ofrecen mejores resultados que otras, eso dependerá del tipo de texto con el que estemos trabajando y principalmente de la propuesta de marcado que hayamos adoptado. Sin embargo, debes tener en cuenta que esta función está pensada para generar una previsualización rápida de los textos y no para su presentación final al público. Aunque esta extensión nos ofrece la posibilidad de generar una visualización de nuestros archivos XML mientras estamos trabajando en VS Code, dista mucho de agotar todas las posibilidades de presentación que podemos generar a partir de nuestros textos marcados con TEI.

# 5. Otras extensiones para trabajar con XML-TEI en VS Code

A continuación, se presentarán brevemente otras 4 extensiones que pueden ser de utilidad para trabajar con XML-TEI. Son 1) *Git History*; 2) *XML*; 3) *XML Tools* y 4) *xslt-transform*.

## 5.1. Git y Git History

Para saber un poco más cómo trabajar con Git conviene acercarse a su uso en VS Code. Este editor de código posee soporte nativo para Git, lo único que hemos de hacer es instalar este control de versiones para nuestro sistema operativo descargándolo desde el siguiente enlace: https://git-scm.com/downloads. 
Primeramente nos acercaremos al control de código fuente de VS Code.

![Fig. 6. Ubicación del Control de código fuente en VS Code.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen6.png)

<!-- Fig. 6. Ubicación del Control de código fuente en VS Code. -->


En segundo lugar, abrimos una carpeta que ya contenga un repositorio git. Si todavía no tenemos una habremos de clonarla desde GitHub. Aquí es importante señalar que es preciso estar registrado en GitHub para poder emplear Git. El registro es gratuito, y la plataforma GitHub nos permitirá, entre otras cosas, almacenar y compartir nuestro código.

![Fig. 7. Abrimos la carpeta que contiene el repositorio git.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen7.png)

<!-- Fig. 7. Abrimos la carpeta que contiene el repositorio git. -->


Una vez abierta la carpeta, podemos seleccionar uno de los archivos y pedirle a Git que nos muestre el historial de este. Lo que se muestra en la Figura 9 es dicho historial.

![Fig. 8. Solicitamos el acceso al historial del archivo.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen8.png)

<!-- Fig. 8. Solicitamos el acceso al historial del archivo. -->


![Fig. 9. Visualizamos el historial del archivo, desde el que se pueden realizar acciones como acceder a su localización en GitHub.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen9.png)

<!-- Fig. 9. Visualizamos el historial del archivo, desde el que se pueden realizar acciones como acceder a su localización en GitHub. -->

Los propósitos de [*Git History*](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory) son claros: 1) ver y buscar registros de *git* al tiempo que gráficos y detalles; 2) visualizar una copia previa del trabajo; 3) visualizar y buscar en el historial (por ejemplo, visualizar el historial de toda o de una de las ramas (*branches*); esto es lo que se denomina git log; o visualizar el historial de un autor). Mediante esta extensión también se pueden comparar ramas, compromisos (*commit*) o comparar archivos entre compromisos.

## 5.2. XML

[*XML*](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-xml) es una distribución desarrollada por RedHat, quienes han contribuido, por ejemplo, al desarrollo de distribuciones de Linux como Fedora o de programas como Libreoffice. Esta extensión se centra en dotar al VS Code de las herramientas necesarias para reconocer adecuadamente el XML. Así, permite el cierre automático de las etiquetas (por ejemplo, al escribir `<p>`, también se escribirá automáticamente `</p>`). También añade soporte para XSL y para renombrar etiquetas. Este segundo funciona de la siguiente manera:

![Fig. 10. Selección de un fragmento de código para el cambio de nombre del símbolo.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen10.png)

<!-- Fig. 10. Selección de un fragmento de código para el cambio de nombre del símbolo. -->

![Fig. 11. Escribimos el símbolo por el que queremos cambiar el símbolo actual.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen11.png)

<!-- Fig. 11. Escribimos el símbolo por el que queremos cambiar el símbolo actual. -->


![Fig. 12. Vemos el resultado en VsCode.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen12.png)

<!-- Fig. 12. Vemos el resultado en VsCode. -->

Pueden consultarse todas las funciones de esta extensión en el enlace facilitado anteriormente.

## 5.3. XML Tools

Por otro lado, *XML Tools* (<https://marketplace.visualstudio.com/items?itemName=DotJoshJohnson.xml>) tiene una serie de características que son: 1) dar formato al XML, 2) visualización del árbol de XML (es decir, cómo está estructurado el documento), evaluación de XPath –lenguaje pensado para transformar documentos XML–; 3) enhebrado de XQuery –lenguaje pensado para consultar documentos XML–; 4) ejecución de XQuery y 5) compleción del código de XQuery. 
Veamos un ejemplo de otra de sus funciones, simplificar el XML:

![Fig. 13. Nuestro código en XML.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen13.png)

<!-- Fig. 13. Nuestro código en XML. -->

![Fig. 14. Búsqueda en el panel de comandos del proceso de simplificación de XML.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen14.png)

<!-- Fig. 14. Búsqueda en el panel de comandos del proceso de simplificación de XML. -->

La caja de comandos se puede abrir con *Ctrl + shift + P* o haciendo clic derecho en cualquier punto del documento y seleccionar dicho panel.

![Fig. 15 Resultado del XML simplificado.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen15.png)

<!-- Fig. 15 Resultado del XML simplificado. -->

## 5.4. xslt-transform

El cometido de la última extensión, [xslt-transform](<https://marketplace.visualstudio.com/items?itemName=SvenAGN.xslt-transform>), es transformar el XML en el que hemos trabajado a un HTML o un PDF mediante el lenguaje XSLT. Mostraremos un ejemplo de cómo transformar un XML en HTML en VS Code:

En primer lugar, instalamos la extensión *xslt-transform*.

![Fig. 16 Abrimos nuestro archivo en VS Code.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen16.png)

<!-- Fig. 16 Abrimos nuestro archivo en VS Code. -->

![Fig. 17 Buscamos el comando que nos permite hacer la transformación mediante XSLT (XSLT: Run Transformation)](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen17.png)

<!-- Fig. 17 Buscamos el comando que nos permite hacer la transformación mediante XSLT (XSLT: Run Transformation). -->

Tras este paso, cargaremos el archivo .xsl o .xslt que hayamos preparado para la transformación. En nuestro caso, hemos partido de un archivo .xsl que ha generado Susanna Allés Torrent y lo hemos modificado para los propósitos de este tutorial.

![Fig. 18 Guardamos el archivo resultante de la transformación como .html](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen18.png)

<!-- Fig. 18 Guardamos el archivo resultante de la transformación como .html -->

![Fig. 19 Disfrutamos del resultado en un HTML sencillo.](https://raw.githubusercontent.com/CarlesMarquez/TutorialVSCode/main/img/Imagen19.png)

<!-- Fig. 19 Disfrutamos del resultado en un HTML sencillo. -->

# 6. Conclusiones

Como hemos visto a lo largo del tutorial, VS Code destaca, entre otras cosas, por ser un editor de código libre y gratuito, lo que lo convierte en una herramienta accesible para cualquier tipo de usuario. Además, hemos aprendido a instalar extensiones en VS Code, unos añadidos que le aportan gran versatilidad a este programa. En primer lugar, nos hemos centrado en la extensión *Scholarly XML* y en *TEI Publisher*, las cuales nos serán de gran ayuda al trabajar en XML-TEI. También se ha ofrecido una tabla con los atajos más habituales y útiles para VS Code. Por otra parte, hemos hecho un breve repaso de otras extensiones que pueden resultar provechosas para todo aquel que desee trabajar en XML-TEI con VS Code (*Git History*, *XML*, *XML Tools* y *xslt-transform*). En definitiva, VS Code es un programa con mucho potencial –buena parte de él se lo añaden las extensiones– y que nos va a permitir trabajar perfectamente con XML, con otros lenguajes de marcado e incluso con lenguajes de programación. 
