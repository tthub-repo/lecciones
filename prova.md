Acabado el prólogo, aparece el elemento raíz `<TEI>` que engloba la totalidad del documento. Aquí irán todos los otros elementos XML-TEI: el encabezado y el texto, con la siguiente estructura:

```xml
<tei xmlns="http://www.tei-c.org/ns/1.0">
     <teiheader>
     ....
     </teiheader>
     <text>
      ....
     </text>
</tei>
```
Y esta mierda: 

```xml
<teiHeader>
    <fileDesc>
      <titleStmt>
        <title>Título del fichero XML</title>
      </titleStmt>
      <publicationStmt>
        <p>Información sobre la publicacion digital</p>
      </publicationStmt>
      <sourceDesc>
        <p>Informacion sobre el texto original</p>
      </sourceDesc>
    </fileDesc>
</teiHeader>
```