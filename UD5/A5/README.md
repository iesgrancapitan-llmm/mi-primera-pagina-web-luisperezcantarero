# UD5 A5. Validación. Conceptos

1. **Indica con una X las afirmaciones verdaderas:**

- [ ] Los DTDs son más ricos y poderosos que los XML Schemas

- [ ] Los DTDs están escritos de acuerdo a la sintaxis XML

- [x] XML Schemas soportan tipos de datos

- [x] XML Schemas soportan namespaces
- [ ] XML Schemas tienen el nodo raíz schema con la URL que contiene la definición de todos los elementos y atributos que se pueden utilizar en un esquema. Eso quiere decir que para programar en XML se necesita estar conectado a Internet.
- [x] En XSD, el atributo xmlns crea un espacio de nombres para cada URL referenciada. Así si hubiese dos elementos con el mismo nombre se diferencian claramente.



2. A continuación aparece la declaración de un esquema XSD. Indica los siguientes elementos:

- prólogo. Define la versión del lenguaje XML y el juego de caracteres utilizado
  - Este prólogo indica que el documento utiliza la versión 1.0 de XML y que el juego de caracteres es UTF-8.
- prefijo del espacio de nombres (opcional)
  - En este caso, el prefijo utilizado para el espacio de nombres XML Schema es xs. Este prefijo es opcional en el sentido de que se podría utilizar cualquier otro valor como prefijo, siempre y cuando se declare apropiadamente
- espacio de nombres XMLSchema
  - El espacio de nombres de XML Schema se define a través de una URI (Uniform Resource Identifier), que en este caso es http://www.w3.org/2001/

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema 
    xmlns:xs="http://www.w3.org/2001/XMLSchema">
		...
<xs:schema />
```
1. A continuación aparece la vinculación de un esquema a un documento XML. Indica (con una X) si está en nuestro sistema de ficheros local o es un esquema público.

- [x] esquema local

- [ ] esquema público
```xml
<factura num="num_fact_1234"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:noNamespaceSchemaLocation="factura.xsd">
	...
</factura>
```

- [ ] esquema local

- [x] esquema público
```xml
<factura num="num_fact_1234"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.miempresa.com/factura.xsd">
...
</factura>	
```
  
5. De los siguientes tipos predefinidos por el espacio de nombres XMLSchema del W3C, marca con una X los numéricos:
- [ ] normalizedString
- [ ] dateTimeStamp
- [ ] language
- [ ] IDREFS
- [ ] dayTimeDuration
- [ ] NMTOKEN
- [ ] NMTOKENS
- [ ] Name
- [ ] NCName
- [ ] ID
- [ ] IDREF
- [ ] ENTITY
- [x] integer
- [ ] yearMonthDuration
- [x] nonPositiveInteger
- [x] negativeInteger
- [x] long
- [x] int
- [x] short
- [x] byte
- [ ] token
- [x] nonNegativeInteger
- [x] unsignedLong
- [x] unsignedInt
- [ ] ENTITIES
- [x] unsignedShort
- [x] unsignedByte
- [x] positiveInteger

6. Adjunta un fichero .xsd con el siguiente diseño:
```xml
<!-- definición de elementos simples -->
<!-- definición de atributos -->
<!-- definición de elementos  complejos -->
<!-- definición de los tipos simples -->
<!-- definición de los tipos complejos -->
<!-- elemento raíz -->
```
Fichero [XSD](/UD5/A3/ficheros/factura.xsd)

7. Con respecto a la validación con XSD indica:
- Un esquema es un documento *XML* al que se le coloca la extensión _.xsd_ . Al ser un archivo XML tiene la estructura habitual de todo documento XML con la obligación de que el elemento _raiz_ se llame _schema_ .
- Etiqueta que identifica la raíz de un documento XML Schema: 
- Etiquetas que identifican las partes de un esquema:
  - Elementos, definidos con etiquetas _xs:element_. Para indicar los elementos permitidos en los documentos que sigan el esquema.
  - Atributos, etiqueta _xs:attribute_.
  - Tipos simples, que permiten definir los tipos simples de datos que podrá utilizar el documento XML. Lo hace la etiqueta _xs:simpleType_ .
  - Tipos complejos, mediante la etiqueta _xs:complexType_
  - Documentación, información utilizable por aplicaciones que manejen los esquemas. Etiquetas _xs:annotation_ y _xs:documentation_.
- Componentes locales y globales en un esquema:
  - En ámbito _global_. Se trata de los elementos del esquema que se coloquen dentro de la etiqueta raíz schema y que no están dentro de ninguna otra. Estos elementos se pueden utilizar en cualquier parte del esquema.
  - En ámbito _local_ . Se trata de elementos definidos dentro de otros elementos. En ese caso se pueden utilizar sólo dentro del elemento en el que están inmersos y no en todo el documento. Es decir si, por ejemplo, si dentro de la definición de un atributo colocamos la definición de un tipo de datos, este tipo de datos sólo se puede utilizar dentro del elemento xs:attribute en el que se encuentra la definición del tipo de datos.
- Dentro de la etiqueta xs:element, indica:
  - atributos obligatorios: El atributo name (que define el nombre del elemento) y, dependiendo del contexto, puede ser necesario especificar también el atributo type (que define el tipo de datos del elemento) o proporcionar una definición de tipo anónima directamente dentro del elemento (con xs:complexType o xs:simpleType).
  - atributos optativos: incluyen, pero no se limitan a, minOccurs (el número mínimo de veces que el elemento debe aparecer), maxOccurs (el número máximo de veces que el elemento puede aparecer), default (el valor por defecto para el elemento), fixed (un valor fijo que el elemento debe tener), y ref (para referenciar a otro elemento definido globalmente), entre otros.

8. Definición de un elemento vacío en XSD
   
   Para definir un elemento vacío en XSD (XML Schema Definition), es decir, un elemento que no contiene texto ni otros elementos, se utiliza la construcción <xs:element> combinada con <xs:complexType>, y se especifica que este tipo complejo no tiene contenido mediante <xs:sequence/> sin elementos dentro o directamente con <xs:complexType/>.

De interés
- https://jorgesanchez.net/manuales/xml/xml-validacion.html
- https://www.w3schools.com/xml/el_restriction.asp
- https://lm-xml-apuntes.readthedocs.io/apuntes/40_esquemas_xml.html#tipos-de-elementos
