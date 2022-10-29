---
title: Edición de fuentes primarias
author: Susanna Allés Torrent, Gabriel Calarco, Gimena del Rio Riande
date: 2022
layout: default
lang: es
---
 
En esta lección profundizaremos en el uso de TEI para la edición de fuentes primarias. En este tutorial no cubriremos la codificación para ediciones críticas, pero si te interesa aprender más sobre este tema te invitamos a explorar la lección  de nuestro tutorial
 
# 1. Fuentes primarias
 
Para la descripción de fuentes primarias existe un módulo específico: [11. Representation of Primary Sources](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/PH.html). Aun así, muchos de los elementos que nos servirán para la descripción de dichas fuentes pertenecen al módulo `core` o [Elementos comunes a todos los documentos TEI](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/CO.html). De igual manera, algunos de los elementos de este módulo son útiles si queremos llevar a cabo una edición crítica y la creación de un aparato de variantes, es decir, registrar las diferentes formas que pueda tener una palabra en manuscritos o impresos diferentes. Es importante, pues, tener en cuenta que al crear nuestro propio esquema necesitaremos seguramente integrar diferentes módulos, porque, aunque cada uno de ellos aspira a cubrir una fenomenología distinta, puede ser que nuestra tipología textual o, sencillamente, nuestro texto nos obligue a contemplar elementos que pertenecen a otros módulos.
 
La fenomenología que podemos encontrarnos en una fuente primaria es realmente muy variada, desde adiciones, supresiones, errores, lecturas inciertas, lagunas, presencia de manos diferentes, cambios de tinta, notas y glosas, daño físicos, etc. Veamos a continuación algunos de los fenómenos y de los elementos que nos podrán ser más útiles.
 
# 2. Adiciones
 
Para las adiciones usaremos el elemento [`<add>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-add.html), que pertenece al módulo `core`. Habitualmente se suele señalar con el atributo `@place` el lugar donde se ha producido dicha adición; por defecto, tenemos como valores: `above`, `below`, `bottom`, `end`, `inline`, `margin`, `opposite`, `overleaf`, `top`. Tomemos el siguiente ejemplo y veamos cómo lo podríamos codificar:
 
![Ejemplo de una adición. <a href="http://bdh.bne.es/bnesearch/detalle/bdh0000008671">*Libro de Alexandre* / Anónimo, siglo XIII. Madrid, Biblioteca Nacional de España, signatura: Vit. 5-10. Fol. 1v.</a>](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L7_001.jpg)
 
Si quisiéramos sólo señalar que aparece una adición en el margen lo podríamos señalar de la siguiente manera:
 
```xml
Los unos a los otros: faulauan entre dientes
este moço conquerra: las ençianas yentes
Felippo & Olimpias: que son sus parientes <add place="margin">sus padre & madre</add>
auian grant alegria: metien en esto mientes
```
 
# 3. Cancelaciones o omisiones
 
En el caso de las supresiones, ya sea porque se ha tachado una parte del texto, ya sea porque se ha omitido, puede utilizarse [`<del>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-del.html) (*deletion*), que también corresponde al módulo `core`. Podemos añadir un atributo `@type` para caracterizar el tipo de cancelación o de omisión. 
 
Además, el módulo de representación de fuentes primarias tiene otro elemento útil para aquellos casos en los que un fragmento largo ha sido omitido o cancelado. En estos casos, podríamos introducir el texto eliminado señalando el inicio del texto con el elemento
[`<delSpan>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-delSpan.html), acompañado del atributo `@spanTo` que apuntaría al punto de anclaje donde finaliza dicho fragmento. Véanse los ejemplos en las [*Guías directrices*](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/examples-delSpan.html%20).
 
# 4. Substituciones
 
Cuando describimos la fuente primaria y nos encontramos con una corrección o substitución de cualquier tipo la marcaremos utilizando [`<del>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-del.html) y [`<add>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-add.html), agrupados en un elemento [`<subst>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-subst.html) si lo consideramos conveniente; también podemos especificar, con el atributo `@hand`, la mano responsable de dicha corrección y, con `@resp`, el editor que ha interpretado dicha corrección en la fuente primaria. Por ejemplo:
 
![Ejemplo de una corrección. <a href="http://bdh.bne.es/bnesearch/detalle/bdh0000008671">*Libro de Alexandre* / Anónimo, siglo XIII. Madrid, Biblioteca Nacional de España, signatura: Vit. 5-10. Fol. 51v.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L7_003.jpg) 
 
```xml
Bien auie y x mill carros: de los sauios senneros
que eran por escrito: del rey sos conseieros
los unos clerigos: los otros caualleros
<subst hand="#copista">
<del>quien</del>
<add place="margin">quier</add>
</subst> los coñosçerie: que eran compañeros
```
 
# 5. Abreviaturas
 
Las abreviaturas pueden codificarse de maneras diferentes, la más
sencilla de las cuales es simplemente marcar la abreviatura dentro del
elemento [`<abbr>`](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-abbr.html). Pero en la mayoría de los casos, vale la pena indicar la forma expandida. En el siguiente ejemplo podemos ver diferentes casos de abreviaturas:
 
![Ejemplos de abreviaturas. <a href="http://bdh.bne.es/bnesearch/detalle/bdh0000008671">*Libro de Alexandre* / Anónimo, siglo XIII. Madrid, Biblioteca Nacional de España, signatura: Vit. 5-10. Fol. 51v.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L7_004.jpg) 
 
Para ello, podemos proceder de la siguiente manera:
 
```xml
Y estaua don <expan><abbr>Jupite</abbr><ex>r</ex></expan>: <expan><abbr>co</abbr><ex>n</ex></expan> çirios çelestiales 
yua <expan><abbr>ap</abbr><ex>r</ex><abbr>es</abbr></expan> apres del fuego: <expan><abbr>co</abbr><ex>n</ex></expan> muchos cappellanes
andaua esse <expan><ex>con</ex><abbr>uie</abbr><ex>n</ex><abbr>to</abbr></expan>: <expan><abbr>co</abbr><ex>n</ex></expan> diex carros cabdales
que eran de fin oro: & de piedras <expan><abbr>c</abbr><ex>ri</ex><abbr>stales</abbr></expan>.
```
 
Como se puede observar, cada abreviatura se sitúa en el interior de `<expan>`, mientras que la forma abreviada aparece dentro de `<abbr>` y la expansión en el elemento `<ex>`. Esta opción puede llegar a recargar el marcado, por lo que a veces se prefiere este otro sistema en el que el elemento `<choice>` contiene la forma abreviada en el interior del elemento `<abbr>` y la forma expandida completa en el elemento `<expan>`:
 
```xml
Y estaua don  <choice>
   <abbr>Jupite</abbr>
   <expan>Jupiter</expan>
</choice>: 
<choice>
   <abbr>co</abbr>
   <expan>con</expan>
</choice> çirios çelestiales
yua <choice>
   <abbr>apes</abbr>
   <expan>apres</expan>
</choice> del fuego: <choice>
   <abbr>co</abbr>
   <expan>con</expan>
</choice> muchos cappellanes
andaua esse <choice>
   <abbr>uieto</abbr>
   <expan>conuiento</expan>
</choice>: <choice>
   <abbr>co</abbr>
   <expan>con</expan>
</choice> diex carros cabdales
que eran de fin oro: & de piedras <choice>
   <abbr>cstales</abbr>
   <expan>cristales</expan>
</choice>.
```

# 6. Establecer diferentes manos de un manuscrito
 
Puede ser que en algunos casos nos encontremos con una fuente en la que aparecen manos diferentes y queramos describir los aspectos físicos o externos del manuscrito ([`physDesc`](https://tei-c.org/release/doc/tei-p5-doc/en/html/ref-physDesc.html)); en el caso que queramos señalarlas, las codificaremos con el elemento [`<handNote>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-handNote.html) que se halla en el tei Header (`/TEI/teiHeader/fileDesc/sourceDesc/msDesc/physDesc/handDesc`). Además, le podemos atribuir un identificador propio a cada una de las manos:
 
```xml
<physDesc>
    <handDesc>
      <handNote xml:id="copista">El copista del manuscrito</handNote>
     <handNote xml:id="lector">Un lector posterior que anotó el manuscrito</handNote>
    </handDesc>
</physDesc>
```
 
Así, podemos también señalar cuando se produce un cambio de mano en nuestra fuente, gracias al elemento [`<handShift>`](http://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-handShift.html). En el siguiente ejemplo, podríamos señalar que la segunda mitad del primer verso fue añadida por un lector posterior:
 
 
![Ejemplos de cambio de mano. <a href="http://bdh.bne.es/bnesearch/detalle/bdh0000008671">*Libro de Alexandre* / Anónimo, siglo XIII. Madrid, Biblioteca Nacional de España, signatura: Vit. 5-10. Fol. 51v.](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L7_005.jpg) 
 
```xml
El ñino mano & mano  <handShift resp="Lector">toliose la capiella</handShift>
poso cerca l maestro: a los pies de la siella
daua grandes sospiros: ca tenie grant maziella
pareçiage la rancura: del cor enna maxiella
```
 
# 7. Daños
 
Si nuestro texto posee alguna zona dañada, frecuente en los manuscritos e impresos antiguos, podemos marcar dicho pasaje con el elemento [`<damage>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-damage.html). En su interior pueden utilizarse diversos atributos, como `@agent` para marcar el motivo del daño; o bien, en aquellos casos en que el daño atañe a un fragmento largo del texto podemos utilizar, como en `<delSpan>`, el elemento [`<damageSpan>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-damageSpan.html) con el atributo `@spanTo` que apuntará hacia el anclaje que indica el final del texto dañado. Por ejemplo:
 
![Ejemplo de un daño. [*Libro de Alexandre* / Anónimo, siglo XIII. Madrid, Biblioteca Nacional de España, signatura: Vit. 5-10. Fol. 3v.](http://bdh.bne.es/bnesearch/detalle/bdh0000008671)](https://raw.githubusercontent.com/tthub-repo/lecciones/master/edicion-y-publicacion-textos-tei/img/L7_007.jpg) 
 
```xml
<damage>non</damage> se me podria celar: quanto ual vn accento
```
#  8. Otros elementos
 
En fin, hay otra serie de fenómenos que quizás queramos marcar como por
ejemplo:
 
* [`<surplus>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-surplus.html): para indicar un texto en la fuente que el editor considera superficial o redundante.
 
* [`<space>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-space.html) para indicar el espacio vacío en nuestra copia, como sucede en la Figura \ref{L5_space}
 
* [`<fw>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-fw.html) (forme work) para indicar los números originales de las páginas, o incluso la numeración de los cuadernos o los hilitos de los encabezados.
 
 
 
# 9. Intervenciones editoriales
 
En general, podemos diferenciar aquellos fenómenos primarios que "objetivamente" encontramos en nuestra fuente, de aquellos otros, secundarios, que corresponden a una intervención del editor o del que codifica. En calidad de editores del texto electrónico, debemos visualizar la intervención como una unidad en la que hay etapas o elementos diferentes. El elemento encargado de recoger estos marcados editoriales alternativos es `<choice>`, y puede utilizarse en los siguientes casos:

* Corrección de errores: ante un error, se utiliza el elemento `<sic>` para marcar el error aparente; con el elemento `<corr>`, en cambio, se recoge la corrección de dicho error:
 
```xml
<p>[...] la lluvia  en los tiempos de bochorno, 
<choice>
<sic>frecuentemaete</sic>
<corr>frecuentemente</corr>
</choice> 
produce diversas clases de sapos [...]</p>
```
 
* Regularización de formas ortográficas: la forma original que aparece en el texto se marca con el elemento `<orig>`, mientras que su forma regularizada, con el elemento `<reg>`:

```xml
<p>[...] El pueblo está situado en un terreno elevado, 
<choice>
<orig>á</orig>
<reg>a</reg>
</choice> 
orillas del Río de la Plata [...]</p>
```
 
 
Otros elementos que pueden sernos de utilidad como editores de una fuente primaria son:
 
* [`<unclear>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/ref-unclear.html) para la transcripción y la codificación de aquellas lecturas inciertas. Normalmente se acompaña del atributo `@resp` para indicar la responsabilidad del editor, y de `@reason` para señalar el motivo.
 
* [`<supplied>`](https://www.tei-c.org/release/doc/tei-p5-doc/es/html/examples-supplied.html) indica el texto que ha sido restablecido por el editor.  
 
 
# 10. Reproducción facsimilar de la fuente
 
La práctica más habitual para conectar una página de la fuente primaria a su reproducción fotográfica es a través del uso del atributo `@facs`. Este atributo apunta hacia el conjunto o una parte de la imagen en cuestión que corresponde al contenido del elemento. Por ejemplo, si quisiéramos asociar cada página con su imagen respectiva, lo más sencillo sería incluir el atributo en el interior del cambio de página y crear una estructura de este tipo:
 
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
 
Las imágenes también pueden codificarse y anotarse describiéndolas en general o por zonas concretas y permitiendo, por ejemplo, una transcripción fina por línea. Este tema reviste algo más de complejidad, por lo que quienes quieran profundizar en él, pueden remitirse a las mismas *Guías directrices* y a la [Representación de fuentes primarias](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/PH.html#PHFAX).
 
# 11. Práctica: Edición de fuentes primarias
 
## 11.1. Enunciado
 
En este ejercicio volveremos sobre el texto del *El Gallardo catalán*, de Lope de Vega, sobre el que ya trabajamos en el ejercicio de drama de la lección anterior. Si ya realizaste ese ejercicio puedes usar el documento TEI que ya creaste en la lección anterior y continuar directamente al paso 3 de las indicaciones. En cambio, si no realizaste ese ejercicio, a continuación tienes la información necesaria:
 
llevarás a cabo la codificación de las dos primeras páginas de la obra teatral de Lope de Vega, *El Gallardo catalán*, publicada en la *Segunda parte de las Comedias* de Lope de Vega Carpio, Madrid, por Alonso Martín, a costa de Alonso Pérez, 1610 y disponible en la [Biblioteca Miguel de Cervantes](http://www.cervantesvirtual.com/obra-visor/el-gallardo-catalan--1/html/). Encontrarás las imágenes más abajo y siguiendo los links a las páginas [69r](http://www.cervantesvirtual.com/obra-visor/el-gallardo-catalan--1/html/ff88cee8-82b1-11df-acc7-002185ce6064_2.html) y [69v](http://www.cervantesvirtual.com/obra-visor/el-gallardo-catalan--1/html/ff88cee8-82b1-11df-acc7-002185ce6064_3.html).
 
Aquí van las indicaciones, paso a paso, que te ayudarán a completar el ejercicio:
 
**[Paso 1]** Comienza por crear un documento XML-TEI con su declaración XML, elemento raíz, `<teiHeader>`, y `<text>`.
 
**[Paso 2]** En el `<teiHeader>` se debe incluir la siguiente información:
 
- `<title>`: título del ejercicio "Codificación de texto dramático y fuente primaria (Lope de Vega)"
 
- En `<sourceDesc>` debe aparecer la fuente original en la que se basa su edición. Para ello, sugiero que utilices el siguiente esquema:
 
```
<bibl>
    <author></author>
    <title></title>
    <pubPlace></pubPlace>
    <publisher></publisher>
    <date></date>
    <biblScope></biblScope>
</bibl>
```
También puedes añadir la indicación de la versión digital, distinguiendo un `<bibl type="impreso">` y uno de copia digital `<bibl type="digital">`con la referencia a la Biblioteca Miguel de Cervantes.
 
**[Paso 3]** Para describir las características de la fuente primaria utiliza los elementos:
`<abbr>`, para marcar las abreviaturas (opcionalmente pueden agregarse los elementos `<choice>`y `<expan>` para señalar en paralelo la versiòn abreviada y su expansión);
`<add>`, para marcar las adiciones (opcionalmente puede agregarse el atributo `@place` para indicar en donde se ubica la adiciòn);
`<del>`,  para marcar las cancelaciones u omisiones;
`<fw>`, para marcar otros elementos tipográficos de la fuente primaria que consideren relevantes.
 
**[Paso 4]** Lo ideal es que mientras realizas la codificación te asegures de que tu documento está bien formado y es válido, para ello es necesario asociar el documento TEI a un esquema RelaxNG, tal como se explica en la [lección 2](enlace).
 
## 11.2. Reproducciones
 
![Ed. 1610, fol. 69r](https://raw.githubusercontent.com/tthub-repo/ejercicios/master/img/8.Lope_fol.69r.jpg)
![Ed. 1610, fol. 69v](https://raw.githubusercontent.com/tthub-repo/ejercicios/master/img/8.Lope_fol.69v.jpg)

 
 
