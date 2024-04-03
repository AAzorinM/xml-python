# xml-python
## Lenguaje de Marcas apuntes
### Minidom
#### Introducción a Minidom
Minidom es un módulo en Python que proporciona una API de alto nivel para trabajar con XML. Es parte de la biblioteca estándar de Python y permite analizar, manipular y generar documentos XML de manera sencilla.

Características principales de Minidom
Facilidad de uso: Minidom proporciona una interfaz fácil de entender y utilizar, lo que facilita trabajar con documentos XML en Python.

Modelo de objetos de documento (DOM): Utiliza el modelo de objetos de documento (DOM) para representar documentos XML. Esto significa que los documentos XML se representan como un árbol de nodos, lo que permite acceder y manipular los elementos de manera programática.

Compatibilidad con estándares: Minidom cumple con los estándares XML DOM definidos por el World Wide Web Consortium (W3C), lo que garantiza la compatibilidad con otras herramientas y bibliotecas que trabajan con XML.

Uso básico de Minidom
A continuación, se muestra un ejemplo básico de cómo utilizar Minidom para crear un documento XML:

python
from xml.dom import minidom

- Crear un nuevo documento XML
doc = minidom.Document()

- Crear un elemento raíz
root = doc.createElement('root')

- Agregar atributos al elemento raíz
root.setAttribute('attr', 'value')

- Agregar el elemento raíz al documento
doc.appendChild(root)

#### Enlace para mas información sobre minidom;
[python minidom](https://docs.python.org/es/3.10/library/xml.dom.minidom.html)
## EJEMPLOS DOM
Supongamos que tenemos el siguiente documento XML llamado example.xml:

```xml
<root>
    <element id="1">Elemento 1</element>
    <element id="2">Elemento 2</element>
    <element id="3">Elemento 3</element>
</root>
```
Y queremos usar Minidom para iterar sobre los elementos <element> e imprimir el texto y el valor del atributo id de cada uno:

```python
from xml.dom import minidom

# Cargar el documento XML
doc = minidom.parse("example.xml")

# Obtener la lista de elementos <element>
elements = doc.getElementsByTagName("element")

# Iterar sobre los elementos e imprimir información
for element in elements:
    element_id = element.getAttribute("id")
    element_text = element.firstChild.data
    print("ID:", element_id)
    print("Texto:", element_text)
```
Este código abrirá el archivo XML example.xml, buscará todos los elementos <element>, e imprimirá el texto y el valor del atributo id de cada uno de ellos.

El resultado esperado sería:

makefile
ID: 1
Texto: Elemento 1
ID: 2
Texto: Elemento 2
ID: 3
Texto: Elemento 3

XSLT (Extensible Stylesheet Language Transformations)
Introducción a XSLT
XSLT es un lenguaje de transformación utilizado para convertir documentos XML en otros formatos, como HTML, XML o texto plano. Se utiliza principalmente para aplicar estilos y estructurar la presentación de los datos XML.

Características principales de XSLT
Separación de datos y presentación: XSLT permite definir estilos y reglas de transformación de manera independiente de los datos, lo que facilita la creación de documentos con una presentación coherente.

Extensibilidad: Se pueden definir funciones y extensiones personalizadas en XSLT para manipular los datos durante la transformación. Esto proporciona una gran flexibilidad para adaptar la transformación a las necesidades específicas del proyecto.

Basado en estándares: XSLT está basado en estándares XML definidos por el W3C, lo que garantiza la interoperabilidad y la compatibilidad con otras herramientas y tecnologías XML.

Uso básico de XSLT
A continuación, se muestra un ejemplo básico de una hoja de estilos XSLT que transforma un documento XML en HTML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:template match="/">
    <html>
      <head>
        <title>Resultado de la transformación XSLT</title>
      </head>
      <body>
        <h1>Resultado de la transformación XSLT</h1>
        <xsl:apply-templates/>
      </body>
    </html>
  </xsl:template>
</xsl:stylesheet>
```
Esta hoja de estilos XSLT toma un documento XML como entrada y genera un documento HTML que contiene los elementos y atributos del documento XML transformado según las reglas definidas en la hoja de estilos.

## A continuación veremos un ejemplo de creacion de una tabla con un horario de clases de un xml con un xsl:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<?xml-stylesheet type="text/xsl" href="horario.xsl"?>
<horari header="https://i.ibb.co/ykHW3gB/school.jpg">
    <colors>
        <!-- Pista: genera classes CSS que es diguin M01, M02, etc... -->
        <color codi="M01">#ff9999</color>
        <color codi="M02">#99ff99</color>
        <color codi="M03">#9999ff</color>
        <color codi="M04">#ffff99</color>
        <color codi="M08">#cc99ff</color>
        <color codi="M09">#ff99ff</color>
        <color codi="M10">#ffcc99</color>
        <color codi="M11">#99ffff</color>
    </colors>
    <links nom="Enllaços directes">
        <!-- Pista: els hauràs d'ordenar pq a la imatge es veuen en un ordre diferent! -->
        <link>
            <nom>Moodle</nom>
            <url>https://moodle.insjoaquimmir.cat/</url>
        </link>
        <link>
            <nom>Institut Joaquim Mir</nom>
            <url>https://agora.xtec.cat/iesjoaquimmir/</url>
        </link>
         <link>
            <nom>Departament d'Educació</nom>
            <url>https://educacio.gencat.cat/ca/inici</url>
        </link>
        <link>
            <nom>IsardVDI</nom>
            <url>https://pilotfp.gencat.isardvdi.com/login/joaquimmir</url>
        </link>
        <link>
            <nom>IEduca</nom>
            <url>https://joaquimmir.ieduca.com</url>
        </link>
    </links>
    <setmana>
        <!-- L'horari el pots fer amb <table> o fent servir flex -->
        <dia nom="Dilluns">
            <modul>
                <codi>M01</codi>
                <nom>Sistemes Operatius</nom>
            </modul>
            <modul>
                <codi>M02</codi>
                <nom>Bases de Dades</nom>
            </modul>
            <modul>
                <codi>M03</codi>
                <nom>Programació</nom>
            </modul>
            <modul>
                <codi>M04</codi>
                <nom>Marques</nom>
            </modul>
            <modul>
                <codi>M09</codi>
                <nom>Implantació</nom>
            </modul>
            <modul>
                <codi>M11</codi>
                <nom>EIE</nom>
            </modul>
        </dia>
        <dia nom="Dimarts">
            <modul>
                <codi>M01</codi>
                <nom>Sistemes Operatius</nom>
            </modul>
            <modul>
                <codi>M10</codi>
                <nom>FOL</nom>
            </modul>
            <modul>
                <codi>M08</codi>
                <nom>Desplegament</nom>
            </modul>
            <modul>
                <codi>M03</codi>
                <nom>Programació</nom>
            </modul>
            <modul>
                <codi>M11</codi>
                <nom>EIE</nom>
            </modul>
            <modul>
                <codi>M09</codi>
                <nom>Implantació</nom>
            </modul>
        </dia>
        <dia nom="Dimecres">
            <modul>
                <codi>M02</codi>
                <nom>Bases de Dades</nom>
            </modul>
            <modul>
                <codi>M10</codi>
                <nom>FOL</nom>
            </modul>
            <modul>
                <codi>M08</codi>
                <nom>Desplegament</nom>
            </modul>
            <modul>
                <codi>M04</codi>
                <nom>Marques</nom>
            </modul>
            <modul>
                <codi>M09</codi>
                <nom>Implantació</nom>
            </modul>
            <modul>
                <codi>M11</codi>
                <nom>EIE</nom>
            </modul>
        </dia>
        <dia nom="Dijous">
            <modul>
                <codi>M01</codi>
                <nom>Sistemes Operatius</nom>
            </modul>
            <modul>
                <codi>M02</codi>
                <nom>Bases de Dades</nom>
            </modul>
            <modul>
                <codi>M03</codi>
                <nom>Programació</nom>
            </modul>
            <modul>
                <codi>M10</codi>
                <nom>FOL</nom>
            </modul>
            <modul>
                <codi>M04</codi>
                <nom>Marques</nom>
            </modul>
            <modul>
                <codi>M11</codi>
                <nom>EIE</nom>
            </modul>
        </dia>
        <dia nom="Divendres">
            <modul>
                <codi>M01</codi>
                <nom>Sistemes Operatius</nom>
            </modul>
            <modul>
                <codi>M02</codi>
                <nom>Bases de Dades</nom>
            </modul>
            <modul>
                <codi>M10</codi>
                <nom>FOL</nom>
            </modul>
            <modul>
                <codi>M08</codi>
                <nom>Desplegament</nom>
            </modul>
            <modul>
                <codi>M04</codi>
                <nom>Marques</nom>
            </modul>
            <modul>
                <codi>M09</codi>
                <nom>Implantació</nom>
            </modul>
        </dia>
    </setmana>
</horari>
```
## Ahora veremos el xsl para dar formato a una tabla en html con un horario
```xsl
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:output method="html" indent="yes"/>
    <xsl:template match="/horari">
        <head>
            <style type="text/css">
                table {
                    width: 100%;
                    border-collapse: separate;
                    border-spacing: 5px;
                }
                th, td {
                    border: 1px solid black;
                    padding: 20px;
                    text-align: center;
                }
                th {
                    background-color: lightgray;
                }
                .M01, .M02, .M03, .M04, .M08, .M09, .M10, .M11 {
                    position: relative;
                    z-index: 1;
                }
                .M01 { background-color: #ff9999; }
                .M02 { background-color: #99ff99; }
                .M03 { background-color: #9999ff; }
                .M04 { background-color: #ffff99; }
                .M08 { background-color: #cc99ff; }
                .M09 { background-color: #ff99ff; }
                .M10 { background-color: #ffcc99; }
                .M11 { background-color: #99ffff; }
                .M01::after, .M02::after, .M03::after, .M04::after, .M08::after, .M09::after, .M10::after, .M11::after {
                    content: '';
                    position: absolute;
                    top: -5px;
                    left: -5px;
                    right: -5px;
                    bottom: -5px;
                    background-color: inherit;
                    z-index: -1;
                }
                ul {
                    text-align: center;
                }
                img {
                    max-width: 100%;
                    height: auto;
                }
            </style>
        </head>
        <html>
            <body>
                <img src="{@header}" width="auto"/>
                <table>
                    <tr>
                        <xsl:for-each select="setmana/dia">
                            <th>
                                <xsl:value-of select="@nom"/>
                            </th>
                        </xsl:for-each>
                    </tr>
                    <tr>
                        <xsl:for-each select="setmana/dia">
                            <td>
                                <xsl:for-each select="modul">
                                    <p class="{codi}">
                                        <xsl:value-of select="codi"/>
                                        <xsl:text> - </xsl:text>
                                        <xsl:value-of select="nom"/>
                                    </p>
                                </xsl:for-each>
                            </td>
                        </xsl:for-each>
                    </tr>
                </table>
                <ul>
                    <h1><xsl:value-of select="links/@nom"/></h1>
                    <xsl:for-each select="links/link">
                        <xsl:sort select="nom"/>
                        <li>
                            <a href="{url}">
                                <xsl:value-of select="nom"/>
                            </a>
                        </li>
                    </xsl:for-each>
                </ul>
            </body>
        </html>
    </xsl:template>
</xsl:stylesheet>
```
### Así es como quedaría el ejemplo anterior en una web;
![Captura de pantalla 2024-04-03 194344](https://github.com/AAzorinM/xml-python/assets/165803047/66c74c93-57a5-4fbe-82f8-4bcc27f5d750)
