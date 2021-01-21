---
marp: true
size: 4:3
theme: marjal
paginate: true
header: 4. Definició d'esquemes i vocabularis en XML
footer: Llenguatge de Marques i Sistemes de Gestió  2020-21
---
<!--
_backgroundColor: #369
_color: white 
_class: lead
-->

# 4. Definició d'esquemes i vocabularis en XML
---
## Objectius:
* Entendre la necessitat de descriure la informació transmesa en els documents XML i les seves regles.
* Identificar les tecnologies relacionades amb la definició de documents XML.
* Analitzar l'estructura i la sintaxis específica utilitzada en la descripció.
* Crear descripcions de documents XML.
* Utilitzar descripcions en l'elaboració i la validació de documents XML.
* Associar les descripcions amb els documents.
* Documentar descripcions.
---
## Continguts
1. ~~Definició de l'estructura i la sintaxi de documents XML.~~
2. ~~XML: estructura i sintaxi~~.
3. ~~Etiquetes~~.
4. ~~Ferramentes d'edició~~.
5. Elaboració de documents XML vàlids ~~i ben formats~~.
6. ~~Utilització d'espais de noms en XML~~.
7. ~~Definició, referenciació i prefixos~~.
8. ~~Avantatges d'utilització d'espais de noms~~.
9. ~~Etiquetes, instruccions de processament, referència a entitats, declaració de tipus de document.~~
---
10. Utilització de mètodes de definició de documents XML.
11. Creació de descripcions.
12. Associació de descriptors amb documents XML.
13. Validació.
14. Ferramentes de creació i validació.
15. Extensibilitat dels esquemes. Tipus derivats. Esquemes múltiples documents.
16. Documentació d'especificacions.
---
<!-- Scoped style -->
<style scoped>
section {
  font-size: 26px;
}
</style>
## Criteris d'avaluació

1. S'ha establert la necessitat de descriure la informació transmesa en els documents XML i
les seves regles.
2. S'han identificat les tecnologies relacionades amb la definició de documents XML.
3. **S'ha analitzat l'estructura i la sintaxis específica utilitzada en la descripció.**
4. **S'han creat descripcions de documents XML.**
5. **S'han utilitzat descripcions en l'elaboració i la validació de documents XML.**
6. S'han associat les descripcions amb els documents.
7. S'utilitzen eines específiques.
8. S'han documentat les descripcions.

---

<!--
_color: #369
_class: lead
header: 4. Definició d'esquemes i vocabularis en XML / Introducció

-->
# 1. Introducció
--- 

## XML

 * En la unitat 1 vas aprendre a crear document XML ben formats.
 * En la unitat 2: XHTML, un dialecte XML per a crear pàgines web.
 * En la unitat 3: RSS i Atom dialectes per a crear canals RSS.

Tant en les unitat 2 i 3 els documents creats eren *ben formats* i *vàlids*.

---


L'objectiu de la següent unitat és aprendre com es poden definir les normes
estructurals per a poder crear els nostres propis dialectes XML i a partir de
les regles poder definir documents XML vàlids.

Dita estructura es pot definir amb els següents llenguatges:
* DTD (_Document Type Definition_, Definició de Tipus de Document).
* XML Schema.
* RELAX NG (_REgular LAnguage for XML Next Generation_).
--- 

**Activitat 1. Ús de XMLCopyEditor**

Valida el canal creat en la unitat anterior amb XMLCopyEditor utilitzant
l'esquema [rss20.xsd](assets/rss20.xsd).

---
# Què és DTD?

DTD (_Document Type Definition_, Definició de Tipus de Document) serveix per 
definir l'estructura d'un document SGML o XML, permetent la seva validació.

Un document XML és vàlid (_valid_) quan, a més d'estar ben format, no incompleix cap de les normes establertes en la seva estructura.
 
Hi ha altres mètodes que també permeten validar documents XML, com ara XML Schema o RELAX NG.

---
```xml
<marcadores>
   <pagina>
      <nombre>Abrirllave</nombre>
      <descripcion>Tutoriales de informática.</descripcion>
      <url>http://www.abrirllave.com/</url>
   </pagina>
   <pagina>
      <nombre>Wikipedia</nombre>
      <descripcion>La enciclopedia libre.</descripcion>
      <url>http://www.wikipedia.org/</url>
   </pagina>
   <pagina>
      <nombre>W3C</nombre>
      <descripcion>World Wide Web Consortium.</descripcion>
      <url>http://www.w3.org/</url>
   </pagina>
</marcadores>
```
---

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE marcadores [
   <!ELEMENT marcadores (pagina)*>
   <!ELEMENT pagina (nombre, descripcion, url)>
   <!ELEMENT nombre (#PCDATA)>
   <!ELEMENT descripcion (#PCDATA)>
   <!ELEMENT url (#PCDATA)>
]>

<marcadores>
   <pagina>
      <nombre>Abrirllave</nombre>
      <descripcion>Tutoriales de informática.</descripcion>
      <url>http://www.abrirllave.com/</url>
   </pagina>
   <pagina>
      <nombre>Wikipedia</nombre>
      <descripcion>La enciclopedia libre.</descripcion>
      <url>http://www.wikipedia.org/</url>
   </pagina>
   <pagina>
      <nombre>W3C</nombre>
      <descripcion>World Wide Web Consortium.</descripcion>
      <url>http://www.w3.org/</url>
   </pagina>
</marcadores>
```
---
### Associar una DTD a un document XML /1
S'indica mitjançant l'etiqueta DOCTYPE. La DTD pot estar inclosa en el propi document,
ser un document extern o combinar-dues.

```xml
<!DOCTYPE nombre [
     ... declaraciones ...
    ]>
```

```xml
   <!DOCTYPE nombre SYSTEM "uri">
```

```xml
<!DOCTYPE nombre SYSTEM "uri" [
   ... declaraciones ...
]>
```
---
### Associar una DTD a un document XML /2
La DTD pot estar en un document extern i, si va a ser utilitzada per diverses 
aplicacions, la sintaxi és la següent:

```xml
<!DOCTYPE nombre PUBLIC "fpi" "uri">
```
Es pot combinar una DTD externa amb una DTD interna, amb la sintaxi:

```xml
<!DOCTYPE nombre PUBLIC "fpi" "uri" [
     ... declaraciones ...
]>
```
--- 
### Associar una DTD a un document XML /3

En tots aquests casos:
- `nombre` és el nom del tipus de document XML, que ha de coincidir amb el nom de l'element arrel del document XML.
- `uri` és el camí (absolut o relatiu) fins a la DTD.
- `fpi` és un identificador públic formal (_Formal Public Identifier_).

---

## Declaracions

Les DTDs descriuen l'estructura dels documents XML mitjançant declaracions. 
Hi ha quatre tipus de declaracions:

* Declaracions d'entitats
* Declaracions de notacions
* Declaracions d'elements, que indiquen els elements permesos en un document i el seu contingut (que pot ser simplement text o altres elements).
* Declaracions d'atributs, que indiquen els atributs permesos en cada element i el tipus o valors permesos de cada element.
---
### Declaracions d'elements

Les declaracions dels elements segueixen la següent sintaxi:

```xml
<!ELEMENT nomElement (contingut)>
```
en què "nomElement" és el nom de l'element, i "(contingut)" una expressió que 
descriu el contingut de l'element.

Per definir el contingut de l'element es poden utilitzar els termes 
EMPTY, (#PCDATA) o ANY o escriure expressions més complexes.

---
### Declaracions d'elements
`EMPTY`: vol dir que l'element és buit.

```xml
<!DOCTYPE exemple [
      <! ELEMENT exemple EMPTY>
    ]>
```
    
`(#PCDATA)`: vol dir que l'element pot contenir text. #PCDATA ha d'escriure entre parèntesis.
 
```xml
<!DOCTYPE exemple [
   <!ELEMENT exemple (#PCDATA)>
    ]>
```
---
`ANY`: vol dir que l'element pot contenir qualsevol cosa (text i altres elements). ANY s'ha d'escriure sense parèntesis.
    
```xml
<!DOCTYPE exemple [
   <!ELEMENT exemple ANY>
   <!ELEMENT a ANY>
]>
```
---
### Declaracion d'elements. Cardinalitat
Per indicar que un element pot o ha de contenir altres elements s'han 
d'indicar els elements, utilitzant els connectors i modificadors següents:

`,` (Coma): vol dir que l'element conté els elements en l'ordre indicat.
    
```xml
<!DOCTYPE exemple [
   <!ELEMENT exemple (a, b)>
   <!ELEMENT a EMPTY>
   <!ELEMENT b EMPTY>
]>
```

---
`|` (o lògic): vol dir que l'element conté un dels dos elements.
    
```xml
<!DOCTYPE exemple [
   <!ELEMENT exemple (a | b)>
   <!ELEMENT a EMPTY>
   <!ELEMENT b EMPTY>
]>
```
---

`?`: Vol dir que l'element pot aparèixer o no, però només una vegada.    

```xml
<!DOCTYPE exemple [
   <!ELEMENT exemple (a, b?)>
   <!ELEMENT a EMPTY>
   <!ELEMENT b EMPTY>
]>
```
`*`: Vol dir que l'element pot no aparèixer o aparèixer una o més vegades.
   
```xml
<!DOCTYPE exemple [
      <!ELEMENT exemple (a *, b)>
      <!ELEMENT a EMPTY>
      <!ELEMENT b EMPTY>
]>
```
---

`+`: Vol dir que l'element ha d'aparèixer una o més vegades (no pot no aparèixer).

```xml
<!DOCTYPE exemple [
   <!ELEMENT exemple (a +, b)>
   <!ELEMENT a EMPTY>
   <!ELEMENT b EMPTY>
]>
```
---
`()`: Permet agrupar expressions.
    
```xml
<!DOCTYPE exemple [
   <!ELEMENT exemple (a, (a | b))>
   <!ELEMENT a EMPTY>
   <!ELEMENT b EMPTY>
]>
```

---
### Corregir errors

#### Exercici 1
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE numeros [
  <!ELEMENT numeros (#PCDATA)>
]>

<numeros>
  <numero>25</numero>
</numeros>
```
--- 
### Exercici 2
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE letras [
  <!ELEMENT letras (letra)>
  <!ELEMENT letra (#PCDATA)>
]>

<letras>
  <letra>m</letra>
  <letra>uve doble</letra>
</letras>
```

---

#### Exercici 3
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE colores [
  <!ELEMENT colores (color*)>
  <!ELEMENT color (#PCDATA)>
]>

<colores>
  <color>azul marino</color>
  negro
  <color>amarillo</color>
</colores>
```
---
#### Exercici 4

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE flores [
  <!ELEMENT flores (flor+)>
  <!ELEMENT flor (#PCDATA)>
]>

<flores>
</flores>
```
---

## Declaració d'atributs

Una declaració d'atributs segueix la següent sintaxi:

```
<!ATTLIST nombreElemento nombreAtributo tipoAtributo valorInicialAtributo>
```
en la que:

* "nombreElemento" es el nombre del elemento para el que se define un atributo.
* "nombreAtributo" es el nombre del atributo.
* "tipoAtributo" es el tipo de datos.
* "valorInicialAtributo" es el valor predeterminado del atributo (aunque también puede indicar otras cosas).

---
Para definir varios atributos de un mismo elemento, se puede utilizar una o varias declaraciones de atributos. 
Los siguientes ejemplos son equivalentes:

```xml
<!ATTLIST nombreElemento nombreAtributo1 
  tipoAtributo1 valorInicialAtributo1>
<!ATTLIST nombreElemento nombreAtributo2 
  tipoAtributo2 valorInicialAtributo2>
```

```xml
<!ATTLIST nombreElemento
  nombreAtributo1 tipoAtributo1 valorInicialAtributo1
  nombreAtributo2 tipoAtributo2 valorInicialAtributo2
>
```

---
<style scoped>table { font-size: 60%; }</style>

The attribute-type can be one of the following:

| Type |  	Description |
|--|--|
| CDATA  |	The value is character data |
| (en1\|en2) | 	The value must be one from an enumerated list |
| ID | 	The value is a unique id |
| IDREF | 	The value is the id of another element|
| IDREFS 	| The value is a list of other ids|
| NMTOKEN | 	The value is a valid XML name |
| NMTOKENS | The value is a list of valid XML names |
| ENTITY | The value is an entity |
| ENTITIES | The value is a list of entities |
| NOTATION | The value is a name of a notation |
| xml: | 	The value is a predefined xml value |

---
Los tipos de atributos son los siguientes:

`CDATA`: el atributo contiene caracteres (sin restricciones). 

```xml
<!DOCTYPE ejemplo [
  <!ELEMENT ejemplo EMPTY>
  <!ATTLIST ejemplo color CDATA #REQUIRED>
]>
```

```
<ejemplo color="" />
```

```
<ejemplo color="amarillo" />
```
```xml
<ejemplo sabor="dulce" />
<!-- ERROR: el atributo "sabor" no está definido -->
```

---
NMTOKEN: el atributo sólo contiene letras, dígitos, y los caracteres 
punto ".", guion "-", subrayado "_" y dos puntos ":".

```xml
<!DOCTYPE ejemplo [
  <!ELEMENT ejemplo EMPTY>
  <!ATTLIST ejemplo color NMTOKEN #REQUIRED>
]>

<ejemplo color="" />

<ejemplo color="azul-marino" />

<ejemplo color="1" />

<ejemplo color="azul marino" />

<ejemplo color="#F0F0F0" />
```
---
`NMTOKENS`: el valor puede contener uno o varios valores de tipo NMTOKEN separados
 por espacios en blanco.
```xml
<!DOCTYPE ejemplo [
  <!ELEMENT ejemplo EMPTY>
  <!ATTLIST ejemplo color NMTOKENS #REQUIRED>
]>

<ejemplo color="" />

<ejemplo color="1" />

<ejemplo color="azul marino" />

<ejemplo color="2*2" />                           
```
---
`valores`: el atributo sólo puede contener uno de los términos de una lista. 
La lista se escribe entre paréntesis, con los términos separados por una barra vertical "|".

```xml
<!DOCTYPE ejemplo [
   <!ELEMENT ejemplo EMPTY>
   <!ATTLIST ejemplo color (azul|blanco|rojo) #REQUIRED>
]>

<ejemplo color="" />

<ejemplo color="azul" />

<ejemplo color="verde" />
<!-- ERROR: "verde" no está en la lista de valores -->
```
---
`ID`: el valor del atributo (no el nombre) **debe ser único** y no se puede repetir 
en otros elementos o atributos.

```xml
<!DOCTYPE ejemplo [
  <!ELEMENT ejemplo (libro*)>
  <!ELEMENT libro (#PCDATA) >
  <!ATTLIST libro codigo ID #REQUIRED>
]>

<ejemplo>
  <libro codigo="L1">Poema de Gilgamesh</libro>
  <libro codigo="L2">Los preceptos de Ptah-Hotep</libro>
</ejemplo>

<ejemplo>
  <libro codigo="1">Poema de Gilgamesh</libro>            
  <!-- ERROR: el valor de un atributo de tipo ID no puede empezar con un número -->
  <libro codigo="L2">Los preceptos de Ptah-Hotep</libro>
</ejemplo>

<ejemplo>
  <libro codigo="L1">Poema de Gilgamesh</libro>
  <libro codigo="L1">Los preceptos de Ptah-Hotep</libro>
  <!-- ERROR: no se puede repetir un atributo de tipo ID -->
</ejemplo>
```
---
`IDREF`: el valor del atributo debe coincidir con el valor del atributo ID de otro elemento.

```xml
<!DOCTYPE ejemplo [
  <!ELEMENT ejemplo ((libro|prestamo)*)>
  <!ELEMENT libro (#PCDATA) >
  <!ATTLIST libro codigo ID #REQUIRED>
  <!ELEMENT prestamo (#PCDATA) >
  <!ATTLIST prestamo libro IDREF #REQUIRED>
]>

<ejemplo>
  <libro codigo="L1">Poema de Gilgamesh</libro>
  <prestamo libro="L1">Numa Nigerio</prestamo>
</ejemplo>

<ejemplo>
  <libro codigo="L1">Poema de Gilgamesh</libro>
  <prestamo libro="L2">Numa Nigerio</prestamo>            
  <!-- ERROR: el valor "L2" no es ID de ningún elemento -->
</ejemplo>
```
---

`IDREFS`: una serie de valores separados por espacios 
que coinciden con el valor del atributo ID de otros elementos.

```xml
<!DOCTYPE ejemplo [
  <!ELEMENT ejemplo ((libro|prestamo)*)>
  <!ELEMENT libro (#PCDATA) >
  <!ATTLIST libro codigo ID #REQUIRED>
  <!ELEMENT prestamo (#PCDATA) >
  <!ATTLIST prestamo libro IDREFS #REQUIRED>
]>
<ejemplo>
  <libro codigo="L1">Poema de Gilgamesh</libro>
  <libro codigo="L2">Los preceptos de Ptah-Hotep</libro>
  <prestamo libro="L1 L2">Numa Nigerio</prestamo>
</ejemplo>
<ejemplo>
  <libro codigo="L1">Poema de Gilgamesh</libro>
  <libro codigo="L2">Los preceptos de Ptah-Hotep</libro>
  <prestamo libro="L1">Numa Nigerio</prestamo>
</ejemplo>
<ejemplo>
  <libro codigo="L1">Poema de Gilgamesh</libro>
  <libro codigo="L2">Los preceptos de Ptah-Hotep</libro>
  <prestamo libro="L3">Numa Nigerio</prestamo>            
  <!-- ERROR: el valor "L3" no es ID de ningún elemento -->
</ejemplo>
```


---
Los valores iniciales de los atributos son los siguientes:

`#REQUIRED`: el atributo es obligatorio, aunque no se especifica ningún valor predeterminado.

```xml
<!DOCTYPE ejemplo [
   <!ELEMENT ejemplo EMPTY>
   <!ATTLIST ejemplo color CDATA #REQUIRED>
]>

<ejemplo color="" />
<ejemplo color="amarillo" />
<ejemplo color="azul marino #000080" />
<ejemplo />
```

---

`#IMPLIED`: el atributo no es obligatorio y no se especifica ningún valor predeterminado.
    
```xml
<!DOCTYPE ejemplo [
  <!ELEMENT ejemplo EMPTY>
  <!ATTLIST ejemplo color CDATA #IMPLIED>
]>

<ejemplo />
 
<ejemplo color="" />

<ejemplo color="amarillo" />
  
<ejemplo color="azul marino #000080" />
```
---

`#FIXED` valor: el atributo tiene un valor fijo.

```xml
<!DOCTYPE ejemplo [
      <!ELEMENT ejemplo EMPTY>
      <!ATTLIST ejemplo color CDATA #FIXED "verde">
    ]>

<ejemplo />

<ejemplo color="verde" />

<ejemplo color="" />                              

<ejemplo color="amarillo" />                      
```
---
`valor`: el atributo tiene un valor predeterminado.

```xml
<!DOCTYPE ejemplo [
  <!ELEMENT ejemplo EMPTY>
  <!ATTLIST ejemplo color CDATA "verde">
]>

<ejemplo />

<ejemplo color="" />

<ejemplo color="amarillo" />

<ejemplo color="verde" />
```
---

## Exercicis

### DTD - Ejercicio 3-1 - Datos personales

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE persona [
  <!ELEMENT persona EMPTY>
  <!ATTLIST persona nombre CDATA #IMPLIED>
]>

<persona dni="03141592E" />
```
---
### DTD - Ejercicio 3-2 - Película
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE pelicula [
  <!ELEMENT pelicula EMPTY>
  <!ATTLIST pelicula titulo CDATA #IMPLIED>
]>

<pelicula titulo="La diligencia" genero="oeste" />
```

---
### DTD - Ejercicio 3-3 - Cuadros

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE cuadros [
  <!ELEMENT cuadros (cuadro*)>
  <!ELEMENT cuadro EMPTY>
  <!ATTLIST cuadro titulo ID #REQUIRED>
  <!ATTLIST cuadro autor CDATA #REQUIRED>
]>

<cuadros>
  <cuadro titulo="Adán y Eva" autor="Alberto Durero" />
  <cuadro autor="Lucas Cranach, el viejo" titulo="Adán y Eva" />
</cuadros>
```
---

### DTD - Ejercicio 4-1 - Libro

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE libro [
  <!ELEMENT libro EMPTY>
  <!ATTLIST libro autor NMTOKEN #REQUIRED>
]>

<libro autor="Mario Vargas LLosa" />
```
---
### DTD - Ejercicio 4-2 - Inventores

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE inventores [
  <!ELEMENT inventores>
  <!ELEMENT inventor EMPTY>
  <!ATTLIST inventor invento CDATA #REQUIRED>
  <!ATTLIST inventor nombre ID #REQUIRED>
]>

<inventores>
  <inventor nombre="Robert Adler" invento="Mando a distancia" />
  <inventor nombre="Laszlo Josef Biro" invento="Bolígrafo" />
  <inventor nombre="Josephine Garis Cochran" invento="Lavaplatos" />
  <inventor invento="Fuego" />
</inventores>
```

--- 
`ENTITY`: el valor del atributo es alguna entidad definida en la DTD.
Entities are used to define shortcuts to special characters.

```xml
<!ENTITY entity-name "entity-value"> 
```

```xml
<!DOCTYPE author[
<!ENTITY writer "Vicent">
<!ENTITY copyright "Copyright Vicent .">
<!ELEMENT author (#PCDATA)>
]>

<author>&writer;&copyright;</author>
```
---

`ENTITIES`: el valor del atributo es alguna de las entidades de una lista de entidades definida en la DTD.
`NOTATION`: el valor del atributo es alguna notación definida en la DTD.

Atributos de tipo ENTITIES en DTD

En una DTD, los atributos declarados ENTITIES son aquellos cuyo valor puede contener uno o varios valores de tipo ENTITY separados por espacios en blanco.

---
### Uso de ENTITIES y NOTATION

```xml
<?xml version="1.0" encoding="UTF-8" standalone="no"?>
<!DOCTYPE animales [
   <!ELEMENT animales (grupos)*>
   <!ELEMENT grupos EMPTY>
   <!ATTLIST grupos imagenes ENTITIES #REQUIRED>
   
   <!ENTITY ballena SYSTEM "ballena.gif" NDATA gif>
   <!ENTITY delfin SYSTEM "delfin.gif" NDATA gif>
   <!ENTITY elefante SYSTEM "elefante.gif" NDATA gif>
   <!ENTITY leon SYSTEM "leon.gif" NDATA gif>
   <!ENTITY oso SYSTEM "oso.gif" NDATA gif>

   <!NOTATION gif SYSTEM "image/gif">
]>

<animales>
   <grupos imagenes="ballena"/>
   <grupos imagenes="ballena delfin"/>
   <grupos imagenes="elefante leon oso"/>
   <grupos imagenes="ballena elefante"/>
</animales>
```
---



## Crèdits i bibliografia 

En aquesta unitat usarem com a referència el llibre _Lenguajes de Marcas y Sistemas de Gestión de Información_ de Carlos Pes

* [Versió en línia](https://www.abrirllave.com/dtd/que-es-dtd.php)
* [Versió en PDF](https://www.abrirllave.com/lmsgi/libro.php)

i de Barlomé Sintes Marco:

* [https://www.mclibre.org/consultar/xml/lecciones/xml-dtd.html](https://www.mclibre.org/consultar/xml/lecciones/xml-dtd.html)

---