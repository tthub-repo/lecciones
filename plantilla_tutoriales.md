---
title: Título de la lección
author: Autor o autores
date: 2022
layout: default
lang: es
---
 
En este primer párrafo se añade una introducción sobre la lección.

# 1. Título

Los títulos de primer nivel son los que aparecerán en el menú de la izquierda y van precedido con una almohadilla, con o sin número `# 1. Título`. Consejos: elige un título breve, sin tipografías. 

## Subtítulo 

Los subtítulos aparecen en el menú de la derecha para poder navegar la página mejor y van precedido por dos almohadillas `## Subtítulo`. 

Las listas pueden ser con puntos: 

```markdown
* Item 1 de la lista 
* Item 2 de la lista
* etc. 
```

o con números: 

```markdown
1. Item 1 de la lista 
2. Item 2 de la lista
3. etc. 
```

Las cuestiones tipográficas son simples: el asterisco para la `*cursiva*` (*cursiva*) y el doble asterisco para las `**negritas**` (**negritas**). 

Los enlaces o hipervínculos se escriben así: `[texto del enlace](URL_al_enlace)`, por ejemplo: 

[Visual Studio Code](https://code.visualstudio.com/)

Las imagenes deben siempre llegar el siguiente formato: `![Leyenda que debe aparecer abajo de la imagen](URL)`

Por ejemplo:

![*La Dama Boba*, http://damaboba.unibo.it/](https://raw.githubusercontent.com/gabrielcalarco/lecciones/master/img/L1_013.png)

Al escribir código, si se trata de un término breve en el cuerpo del documento, se señala con un asterisco, `, por ejemplo, `<etiqueta codig>`. En otras ocasiones se aportan fragmentos de código que debemos marcar de la siguiente manera: 

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
Las citas separadas en un renglón aparecen con un parentesis triangular de cierre: 

> Esto es una cita... Las computadoras solo pueden manejar datos explícitos. La función del marcado es representar material textual en forma digital a través del acto explicativo de la codificación del texto.

## Otros consejos: 

1. Lo ideal es que cada tutorial se componga de lecciones y cada lección de una parte teórica o de explicación, y otra de Práctica donde se propone un ejercicio. 
2. El tutorial debe ponerse en una carpeta y los autores pueden trabajar o bien en su GitHub, compartiendo el repositorio a tthub-repo, susannalles, Gimena y gabrielcalarco. Una vez el tutorial esté completo, se migra a <https://github.com/tthub-repo/lecciones> 

