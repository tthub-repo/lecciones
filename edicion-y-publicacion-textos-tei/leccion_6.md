---
title: Codificación de textos en verso y textos dramáticos
author: Susanna Allés Torrent, Gabriel Calarco, Gimena del Rio Riande
date: 2022
layout: default
lang: es
---
 
En las lecciones anteriores nos dedicamos a los elementos de TEI más comúnmente usados para codificar textos en prosa. Ahora continuaremos explorando otras tipologías textuales: verso y drama. A continuación veremos un ejemplo de cada una de estas tipologías y al final de la lección podrás encontrar un ejercicio de cada una para poner en práctica lo aprendido.
 
# 1. Poesía
 
Centrémonos ahora en los elementos básicos para codificar composiciones en verso y veamos cómo funciona el vocabulario propuesto por TEI. En el apartado [Verse](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/VE.html) de las *Guías directrices* podrás encontrar información mucho más detallada.
 
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
 
## Estrofas
 
La totalidad del poema suele contenerse en el elemento [`<lg>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-lg.html) (*line group*), mientras que el título, una vez más, se sitúa en el interior de un elemento `<head>`; cada uno de los versos se codifica con el elemento que indica la línea: [`<l>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-l.html). Así mismo, para marcar las estrofas también se utiliza `<lg>`, pues permite la anidación de otros elementos idénticos en su interior (es decir que el `<lg>` que utilizamos para marcar al poema completo puede contener en su interior otros `<lg>` que utilizaremos para las estrofas) .
 
El elemento `<lg>` puede poseer una serie de atributos, tanto a nivel de poema, como a nivel de estrofa, entre los cuales podemos destacar:
 
* `@type` para indicar de qué tipo de composición se trata.
* `@rhyme` para indicar el tipo de rima de la estrofa.
* `@met` para indicar la estructura métrica de la estrofa.
* `@n` para señalar, por ejemplo, el número de estrofa.
* `@xml:id` para otorgar un identificador a cada estrofa.
 
## Versos
 
También el verso (`<l>`) puede tener sus atributos:
 
* `@n` para indicar el número del verso.
* `@rhyme` para indicar la rima del verso.
* `@xml:id` para otorgar un identificador a cada verso.
 
El vocabulario TEI prevé un elemento específico para codificar las rimas: [`<ryhme>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-rhyme.html); este puede aparecer tanto a final del verso como en su interior, donde sea que aparezca la rima:
 
```xml
<lg type="cuarteto" n="1">
  <l n="1">Tengo miedo a perder la marav<rhyme>illa</rhyme></l>
  <l n="2"> de tus ojos de estatua y el ac<rhyme>ento</rhyme></l>
  <l n="3"> que me pone de noche en la mej<rhyme>illa</rhyme></l>
  <l n="4">la solitaria rosa de tu ali<rhyme>ento</rhyme>.</l>
</lg>
```
 
Además, el elemento `<rhyme>` puede contener el atributo `@label` para señalar el tipo de rima, normalmente indicado con una letra del alfabeto:
 
```xml
marav<rhyme label="a">`illa`</rhyme>
```
 
Pero también puede indicarse en el interior del elemento `<div>`, `<lg>` e incluso `<l>`:
 
```xml
<lg type="soneto" met=”4x11” rhyme="ababababcdcdcd">
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
 
## Serie de poemas
 
Si tuviéramos una serie de poemas, las estrategias a seguir podrían ser varias pero la más sencilla sería marcar cada poema independientemente en un elemento `<lg>`:
 
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
Pueden encontrar otro ejemplo de marcado en nuestro Repositorio de ejemplos en GitHub: [Ejemplo en verso](https://github.com/tthub-repo/ejemplos/blob/master/L5_ejemplo_poema.xml).
 
Existen muchos otros elementos relacionados con las composiciones métricas, para más detalles pueden consultarse el módulo correspondiente [6. Verse](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/VE.html) de las *Guías directrices*; y la sección de [Module 4: Poetry](https://teibyexample.org/modules/TBED04v00.htm) de *TEI By Example*.
 
# 2. Drama
 
Los textos dramáticos se caracterizan por tener una estructura más bien fija y unos elementos recurrentes: actos, escenas, acotaciones, indicaciones escénicas, diálogos, etc.  Las *Guías directrices*, al igual que sucedía con las obras en verso, dedica un módulo específico a las obras dramáticas (véase [7. Performance texts](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/DR.html)).

## Estructura
 
Para codificar obras dramáticas, en primer lugar, es necesario crear la estructura general en la que acomodar el texto. Tal como hemos procedido en otras ocasiones, se podría establecer una división general para cada una de las escenas y para cada uno de los actos o jornadas, añadiendo un atributo `@type` para definirlas:
 
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
 
Cada una de las divisiones puede o no ir acompañada de un título, elemento aceptado en todos los documentos TEI.
 
## Diálogos
 
Para los diálogos se utilizan los elementos [`<sp>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-sp.html) (*speech*) que están constituidos de la persona que habla [`<speaker>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-speaker.html) y del diálogo en sí, normalmente marcado en un simple `<p>`, aunque nada impediría que se utilizara `<l>` o `<lg>`, especialmente en aquellos casos en que se tratara de una versificación; o incluso podría también utilizar el elemento `<seg>`, pero en ningún caso el texto podría ir directamente dentro del elemento `<sp>` sin estructurar. Un ejemplo de diálogo codificado en TEI tendría la siguiente estructura:
 
```xml
<sp who="#personaje1">
  <speaker>Personaje 1</speaker> Diálogo
</sp>
<sp who="#personaje2">
  <speaker>Personaje 2</speaker> Diálogo
</sp>
```
 
## Personajes
 
En lo que concierne a los personajes es importante crear de antemano una lista de todos los personajes que intervienen y otorgarles un identificador. Esta información puede colocarse o bien en una `<div>` creada a propósito, o bien (más recomendable) en el elemento `<front>`, que precede el `<body>`. Allí podríamos incluir dicha lista gracias al elemento `<castlist>`:
 
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
Este es un ejemplo más de cómo el lenguaje de TEI muchas veces permite expresar lo mismo de diferentes maneras, y cada propuesta de marcado debe ser entendida como una aproximación singular al texto.
 
## Indicaciones dramáticas
 
Las indicaciones dramáticas o acotaciones, aquellas normalmente realizadas por el dramaturgo, pueden incluirse dentro del elemento [`<stage>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-stage.html). También aquí se prevé la opción de añadir un atributo `@type` para caracterizar las diferentes acotaciones o tipos de indicaciones, por ejemplo:
 
```xml
<sp who="#personaje1">Diálogo</sp>
<sp who="#personaje2">Diálogo</sp>
<stage type="personajes">Descripción de los personajes que se encuentran en la escena.</stage>
<stage type="decorado">Descripción del decorado en la escena.</stage>
```
 
En el interior del elemento `<stage>` podemos utilizar otros elementos que
pueden sernos útiles en alguna ocasión como por ejemplo:
 
* [`<move>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-move.html) para indicar los movimientos de los personajes. Podríamos incluso especificar los movimientos con el atributo `@type`, que conlleva unos valores predifinidos por defecto de entrada, salida y en escena: `entrance` o `exit` y `onStage`; así también podemos añadir el atributo `@who` para identificar fácilmente de qué personaje se trata y `@where` para señalar hacia dónde es el movimiento.
* [`<sound>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-sound.html) para describir fenómenos de sonido, añadiendo si es necesario el atributo `@type`.
* [`<view>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-view.html) para describir el contexto visual de una parte del escenario, tal y como lo debe visualizar el espectador.
* [`<camera>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-camera.html) para dar indicaciones al cámara en el caso de grabaciones video, como películas.
* [`<caption>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/ref-caption.html) para recoger las palabras que deberán proyectarse en pantalla.
* [`<tech>`](https://www.tei-c.org/release/doc/tei-p5-doc/en/html/examples-tech.html) otras informaciones técnicas.
 
<span style="color:red">Cambiar enlaces</span> En el [Repositorio de ejemplos en GitHub](https://github.com/tthub-repo/ejemplos/) puede encontrarse un [ejemplo sencillo de codificación](https://github.com/tthub-repo/ejemplos/blob/master/L5_ejemplo_drama.xml) y otro ejemplo con el inicio de una obra dramática en verso de [Lope de Vega, *Amar sin saber a quien*](https://github.com/tthub-repo/ejemplos/blob/master/L5_ejemplo_drama_Lope_Amar_sin_saber_a_quien.xml). También puedes ver la reproducción digital que aparece en la [Biblioteca Cervantes Virtual](https://www.cervantesvirtual.com/descargaPdf/amar-sin-saber-a-quien--1/) y confrontarla con la codificación que proponemos. [Aquí](https://www.cervantesvirtual.com/obra-visor/amar-sin-saber-a-quien--0/html/) encontraréis también una edición digital en HTML.
 
Otros recursos que pueden ser de utilidad son el [Module 5: Drama](http://teibyexample.org/modules/TBED05v00.htm) en *TEI by Example*, con especial atención a los [ejemplos](http://teibyexample.org/examples/TBED05v00.htm), y la consulta de las [*Guías directrices*](http://www.tei-c.org/release/doc/tei-p5-doc/en/html/DR.html).

# 3. Práctica: texto en verso

## Enunciado
 
En esta práctica, debes codificar el soneto “Éste que ves, engaño colorido”, de la poeta mexicana Sor Juana Inés de la Cruz.
  
1. Empezaremos por crear un documento XML-TEI con su declaración XML, elemento raíz, `<teiHeader>`, y `<text>`.
2. Para completar los datos del encabezado debes utilizar la siguiente información sobre la fuente:

* Título: Obras escogidas / Sonetos I
* Autora: Juana Inés de la Cruz, Sor, 1651-1695
* Publicación: Alicante : Biblioteca Virtual Miguel de Cervantes, 2003
* Notas de reproducción original: Edición digital basada en la 14ª ed. de Madrid, Espasa Calpe, 1976.
 
 
3. Al igual que en los ejercicios anteriores, debes copiar el texto a codificar en el elemento `<body>`.
4. Usa el elemento  `<lg>` para marcar la totalidad del poema y, luego, para marcar cada una de las estrofas puedes añadir el atributo `@type` para distinguir las diferentes estrofas. Puedes utilizar también los atributos `@met` (en cuyo valor consignaremos la cantidad de versos de cada estrofa y la cantidad de sílabas de los mismos con el formato “4x11”)  y `@rhyme` (cuyo valor será la estructura de rimas representada con letras con el formato “ABBA”) para añadir la información métrico rimática de cada estrofa. También puedes numerarlas utilizando el atributo `@n`.
5. Usa el elemento `<l>` para marcar los versos, puedes incluir el atributo `@n` para numerarlos.
6. Usa el elemento `<rhyme>` para marcar las rimas a final de verso, usando el atributo `@label` para asignarles una etiqueta, que debe coincidir con la designación de la rima en el atributo `@rhyme` de la estrofa (por ejemplo “A” o “B”).
 
## Texto a codificar

```
Éste que ves, engaño colorido,
que, del arte ostentado los primores,
con falsos silogismos de colores
es cauteloso engaño del sentido;
 
éste en quien la lisonja ha pretendido
excusar de los años los horrores
y venciendo del tiempo los rigores
triunfar de la vejez y del olvido:
 
es un vano artificio del cuidado;
es una flor al viento delicada;
es un resguardo inútil para el hado;
 
es una necia diligencia errada;
es un afán caduco, y, bien mirado,
es cadáver, es polvo, es sombra, es nada.
```

Fuente: [Sor Juana Inés de la Cruz. Obras escogidas. Espasa-Calpe: Madrid. 1976.](https://www.cervantesvirtual.com/obra-visor/obras-escogidas--0/html/c7822235-3f49-4a31-9ea3-485840a7c278_3.html)
 
# 4. Práctica: texto dramático

En este ejercicio debes llevar a cabo la codificación de las dos primeras páginas que corresponden a la obra teatral de Lope de Vega, *El Gallardo catalán*, publicada en la *Segunda parte de las Comedias* de Lope de Vega Carpio, Madrid, por Alonso Martín, a costa de Alonso Pérez, 1610 y disponible en la [Biblioteca Miguel de Cervantes](http://www.cervantesvirtual.com/obra-visor/el-gallardo-catalan--1/html/). Encontrarás las imágenes más abajo y siguiendo los links a las páginas [69r](http://www.cervantesvirtual.com/obra-visor/el-gallardo-catalan--1/html/ff88cee8-82b1-11df-acc7-002185ce6064_2.html) y [69v](http://www.cervantesvirtual.com/obra-visor/el-gallardo-catalan--1/html/ff88cee8-82b1-11df-acc7-002185ce6064_3.html).

Debes estructurar todo el documento en función de las secciones del texto, crear una lista de personajes y otorgarles un identificador.

Los elementos que obligatoriamente debes utilizar son: `<sp>`, `<speaker>`, `<stage>` con los atributos vistos en el módulo.

Aquí van las indicaciones, paso a paso, que te ayudarán a completar el ejercicio:

1. Comienza por crear un documento XML-TEI con su declaración XML, elemento raíz, `<teiHeader>`, y `<text>`.
2. En el `<teiHeader>` se debe incluir la siguiente información:

* `<title>`: título del ejercicio "Codificación de texto dramático y fuente primaria (Lope de Vega)".
* `<publicationStmt>`: las informaciones sobre dónde se ha realizado la codificación del archivo (por ejemplo, TTHub, 2022).

3. En `<sourceDesc>` debe aparecer la fuente original en la que se basa su edición. Para ello, puedes utilizar el siguiente esquema:

```xml
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

4. En `<text>` puede añadirse el elemento `<front>` y la lista de personajes que intervienen en la obra, con `<castList>`. En las [*Guías directrices*](https://tei-c.org/release/doc/tei-p5-doc/en/html/examples-castList.html) encontrarás más información. Cada uno de los personajes, debe ir marcado con un elemento `<castItem>`: el nombre propiamente dicho puede ir en `<role>` con un `@xml:id`, mientras que la explicación puede ir en <roleDesc>. Por ejemplo:

```xml
 <castItem>
     <role xml:id="Clavela">Clavela</role>
     <roleDesc>Dama</roleDesc>
 </castItem>
```

5. En el `<body>`, puede situarse una `<div>`que recoja todo el contenido de la jornada 1. Las indicaciones escénicas pueden ir marcadas con `<stage>`. Por ejemplo, `<stage type="entrance">Sale Clavela y don Remón</stage>`
.
6. El resto de la codificación debería ser de este modo indicando quien habla y especificando la estructura poética:

```xml
<sp who="#Clavela">
   <speaker>Clavela</speaker>
   <lg type="cuarteto" n="1">
       <l n="1"> ....</l>
       <l n="2"> ....</l>
   </lg>
</sp>
```

 7. Lo ideal es que mientras realizas la codificación te asegures de que tu documento está bien formado y es válido, para ello es necesario asociar nuestro documento TEI a un esquema RelaxNG, tal como se explica en la [lección 2](enlace). <span style="color:red">Cambiar enlaces</span> 
