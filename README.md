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

# Crear un nuevo documento XML
doc = minidom.Document()

# Crear un elemento raíz
root = doc.createElement('root')

# Agregar atributos al elemento raíz
root.setAttribute('attr', 'value')

# Agregar el elemento raíz al documento
doc.appendChild(root)

# Generar el XML
xml_str = doc.toprettyxml(indent='  ')
print(xml_str)
Este código crea un nuevo documento XML con un elemento raíz llamado 'root' y un atributo 'attr' con el valor 'value'. Luego, genera una representación en formato XML del documento.

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
<schedule>
    <day name="Monday">
        <class>
            <time>09:00 - 10:30</time>
            <subject>Mathematics</subject>
            <room>Room 101</room>
        </class>
        <class>
            <time>11:00 - 12:30</time>
            <subject>History</subject>
            <room>Room 102</room>
        </class>
    </day>
    <day name="Tuesday">
        <class>
            <time>09:00 - 10:30</time>
            <subject>Science</subject>
            <room>Room 103</room>
        </class>
        <class>
            <time>11:00 - 12:30</time>
            <subject>English</subject>
            <room>Room 104</room>
        </class>
    </day>
    <day name="Wednesday">
        <class>
            <time>09:00 - 10:30</time>
            <subject>Physics</subject>
            <room>Room 105</room>
        </class>
        <class>
            <time>11:00 - 12:30</time>
            <subject>Geography</subject>
            <room>Room 106</room>
        </class>
    </day>
    <day name="Thursday">
        <class>
            <time>09:00 - 10:30</time>
            <subject>Chemistry</subject>
            <room>Room 107</room>
        </class>
        <class>
            <time>11:00 - 12:30</time>
            <subject>Physical Education</subject>
            <room>Indoor Gym</room>
        </class>
    </day>
    <day name="Friday">
        <class>
            <time>09:00 - 10:30</time>
            <subject>Computer Science</subject>
            <room>Computer Lab</room>
        </class>
        <class>
            <time>11:00 - 12:30</time>
            <subject>Art</subject>
            <room>Art Room</room>
        </class>
    </day>
</schedule>

```
## Ahora veremos el xsl para dar formato a una tabla en html con un horario
```xsl
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

  <!-- Plantilla de inicio -->
  <xsl:template match="/">
    <html>
      <head>
        <title>Horario de Clases</title>
        <style>
          table {
            width: 100%;
            border-collapse: collapse;
          }
          th, td {
            border: 1px solid black;
            padding: 8px;
            text-align: left;
          }
        </style>
      </head>
      <body>
        <h1>Horario de Clases</h1>
        <xsl:apply-templates/>
      </body>
    </html>
  </xsl:template>

  <!-- Plantilla para los días -->
  <xsl:template match="day">
    <h2><xsl:value-of select="@name"/></h2>
    <table>
      <tr>
        <th>Hora</th>
        <th>Materia</th>
        <th>Aula</th>
      </tr>
      <xsl:apply-templates select="class"/>
    </table>
  </xsl:template>

  <!-- Plantilla para las clases -->
  <xsl:template match="class">
    <tr>
      <td><xsl:value-of select="time"/></td>
      <td><xsl:value-of select="subject"/></td>
      <td><xsl:value-of select="room"/></td>
    </tr>
  </xsl:template>

</xsl:stylesheet>
```
