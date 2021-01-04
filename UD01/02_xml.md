---
layout: default
parent: 1. Llenguatges de marques
nav_order: 1
has_children: false
---
# XML
{: .no_toc }

1. TOC
{:toc}

## Introducció

XML (_eXtensible Markup Language_, Llenguatge de Marcat extensible) és un llenguatge
desenvolupat per W3C (World Wide Web Consortium) que està basat en SGML (_Standard
Generalized Markup Language_, Llenguatge de Marcat Generalitzat Estàndard).

{:.alert .alert-info}
<div markdown="1" class="info">

### El _World Web Consortium_  
{:.no_toc .nocount }

El _World Wide Web Consortium_ (W3C) és la principal organització internacional d’estàndards per a la _World Wide Web_.
 Fundat el 1994 i actualment dirigit per Tim Berners-Lee, el consorci està format per organitzacions membres que
  mantenen personal a temps complet treballant junts en el desenvolupament d’estàndards per a la _World Wide Web_. 
  El W3C també es dedica a l'educació i divulgació, desenvolupa programari i serveix de fòrum obert per a la 
  discussió sobre la web.
  
  [Especificació de XML 1.0](https://www.w3.org/TR/xml/)

</div>


XML és un llenguatge utilitzat per a l'emmagatzematge i intercanvi de dades estructurades entre diferents plataformes.

XML és un metallenguatge, és a dir, pot ser emprat per a definir altres llenguatges, anomenats *dialectes XML*.
 Per exemple, alguns llenguatges basats en XML són:

* GML (_Geography Markup Language_, Llenguatge de Marcat Geogràfic).
* MathML (_Mathematical Markup Language_, Llenguatge de Marcat Matemàtic).
* RSS (_Really Simple Syndication_, Sindicació Realment Simple).
* SVG (_Scalable Vector Graphics_, Gràfics vectorials escalables).
* XHTML (_eXtensible HyperText Markup Language_, Llenguatge de Marcat d'Hipertext extensible).

## Estructura i sintaxi

Els documents XML estan formats per text pla (sense format) i contenen marques (etiquetes) definides pel desenvolupador.
**Cada etiqueta representa un element**. Aquestes marques, és recomanable que siguen el més descriptives possible i, per escriure-les, s'utilitzen els caràcters
 menor que "<", major que ">" i barra inclinada (_slash_) "/".

Si en un document XML es vol guardar el nom Elsa, es pot escriure:
```xml
<nom> Elsa </nom>
```
La sintaxi utilitzada en l'exemple és la bàsica per escriure un element en XML:

```xml
<etiqueta> valor </etiqueta>
```
Cal observar que, entre l'etiqueta d'inici (`<nom>`) i l'etiqueta de fi (`</ nom>`) s'ha escrit la dada (`valor`) que es 
vol emmagatzemar. En aquest cas `Elsa`. 


### Elements buits

En un document XML, un element pot no contenir cap valor. En aquest cas cal escriure:

```xml
<etiqueta> </ etiqueta>
```
Es pot expressar el mateix escrivint:
```xml
<etiqueta />
```

Per escriure l'element `nom` buit, es pot escriure:
```xml
<nom> </nom>
```
O també:

```xml
<nom />
```
### Relacions pare-fill entre elements

D'altra banda, un element (pare) pot contenir a un altre o altres elements (fills):

```xml
<persona>
   <nom> Elsa </nom>
   <dona />
   <data-de-naixement>
      <dia> 18 </dia>
      <mes> 6 </mes>
      <any> 1996 </any>
   </data-de-naixement>
   <ciutat> Pamplona </ciutat>
</persona>
```

En aquest exemple, l'element "persona" conté quatre elements (fills): "nom", "dona", "data de naixement" i "ciutat". 
I l'element "data de naixement" conté altres tres elements (fills): "dia", "mes" i "any".

Vegeu que, de tots els elements que apareixen en aquest exemple, només l'element "dona" està buit.

### Element arrel d'un document XML

Tot document XML ha de tenir un únic element arrel (pare) del que descendiran tots els altres. En aquest cas, 
l'element arrel és "persona". Gràficament, l'estructura d'elements d'aquest document es pot representar com es mostra 
a continuació:

![Estructra d'elements d'un document XML persona - Exemple d'el tutorial de XML de {Abrirllave.com](assets/arbol-xml-persona.gif)

D'aquesta manera, l'estructura de qualsevol document XML es pot representar com un arbre invertit d'elements. 
Es diu que els elements són els que donen estructura semàntica a el document.

#### Elements amb contingut mixt

Un element pot contenir contingut mixt, és a dir, text i altres elements:

```xml
<persona>
   <nom>Elsa</ nom> viu a <ciutat>Pamplona</ ciutat>.
</ persona>
```
En aquest exemple, l'element "persona" conté els elements "nom" i "ciutat", a més dels textos "viu en" i ".".

## Normes de sintaxi bàsiques en XML

En un document XML, tots els noms dels elements són _case sensitive_, és a dir, sensibles a lletres minúscules i 
majúscules, havent de complir les següents normes:

>Poden contenir lletres minúscules, lletres majúscules, números, punts ".", Guions mitjans "-" i guions baixos "_".

>Així mateix, poden contenir el caràcter dos punts ":". No obstant això, el seu ús es reserva per quan es 
 defineixin espais de noms.

>El primer caràcter ha de ser una lletra o un guió baix "_".

D'altra banda, cal tenir en compte que darrere del nom d'una etiqueta es permet escriure un espai en blanc o un salt 
de línia. Per exemple, sintàcticament és correcte escriure:

```xml
<ciutat> Pamplona </ ciutat
>
```

Ara bé, no hi pot haver un salt de línia o un espai en blanc abans del nom d'una etiqueta:

```xml
<
ciutat> Pamplona </ ciutat>
```
Els següents elements no estan escrits correctament per incomplir alguna regla de sintaxi:

```xml
<ciudad>Pamplona</ciudad>
<día>18</dia>
<mes>6<mes/>
<ciudad>Pamplona</finciudad>
<_rojo>
<2colores>Rojo y Naranja</2colores>
< Aficiones >Cine, Bailar, Nadar</ Aficiones >
<persona><nombre>Elsa</persona></nombre>
<color favorito>azul</color favorito>
```
S'hauria d'escriure:

```xml
<ciudad>Pamplona</ciudad>
<día>18</día>
<mes>6</mes>
<ciudad>Pamplona</ciudad>
<_rojo/>
<colores2>Rojo y Naranja</colores2>
<Aficiones >Cine, Bailar, Nadar</Aficiones >
<persona><nombre>Elsa</nombre></persona>
<color.favorito>azul</color.favorito>
<color-favorito>azul</color-favorito>
<color_favorito>azul</color_favorito>
```
Les lletres no angleses (á, Á, ñ, Ñ ...) estan permeses. No obstant això, és recomanable no utilitzar-les per 
reduir possibles incompatibilitats amb programes que puguin no reconèixer-les.

Pel que fa al caràcter guió "-" i a punt ".", Encara que també estan permesos per nomenar etiquetes, 
igualment s'aconsella evitar el seu ús; el guió perquè podria confondre amb el signe menys, i el punt perquè, 
per exemple a l'escriure color.favorito, podria interpretar-se que favorito és una propietat de l'objecte color.

{:.alert .alert-activity }
<div markdown="1" class="activity">
### Activitat 2. Errors de sintaxi
{: .no_toc .nocount } 

Revisa el següent document XML, detecta els errors i reescriu-lo correctament
```xml
<?xml version="1.0" encoding="UTF-8"?>
<frutas>  
</frutas>
< frutas >
   < fruta >
      < nombre >cereza< nombre \>
   < fruta \>
   < fruta >
      < nombre >naranja< nombre \>
   < fruta \>
< frutas \>
```
</div>


## Atributs en XML

Els elements d'un document XML poden tenir atributs definits en l'etiqueta d'inici. Un atribut serveix per proporcionar
 informació extra sobre l'element que el conté.

Donats els següents dades d'un producte:

* Codi: G45
* Nom: Barret de llana
* Color: negre
* Preu: 12.56

La seva representació en un document XML podria ser, per exemple:
```xml
<producte cod = "G45">
   <nom color = "negre" preu = "12.56"> Barret de llana </ nom>
</ producte>
```
En aquest exemple s'han escrit tres atributs: codi, color i preu. Cal observar que, els seus valors ( "G45", 
"negre" i "12.56") s'han escrit entre cometes dobles ("). Tanmateix, també poden anar entre cometes simples ( ').

Si, per exemple, l'atribut `codi` es volgués representar com un element, es podria escriure:

```xml
<producte>
   <codi> G45 </ codi>
   <nom color="negre" preu="12.56">Barret de llana</ nom>
</ producte>
```
Com es pot apreciar, ara el valor del codi no s'ha escrit entre cometes dobles.

{:.alert .alert-info }
<div markdown="1" class="activity">
### Elements i atributs
{:.no_toc .nocount }

Un element és un component lògic d’un document XML. Els elements solen tenir entitat pròpia. El contingut d’un element 
és tot  el que es troba entre les etiquetes d’obertura i tancament, inclús si contenen altres elements (fills).

Per contra, els atributs solen representar propietats o característiques dels elements.
</div>


### Normes de sintaxi

Els noms dels atributs han de complir les mateixes normes de sintaxi que els noms dels elements. A més, tots els
 atributs d'un element han de ser únics. Per exemple, és incorrecte escriure:

```
<dades x="3" x="4" i="5" />
```

No obstant això, sí que és correcte escriure:

```xml
<dades x="3" X="4" i="5" />
```
Els atributs continguts en un element, com en aquest cas x, X i y, han de separar amb espais en blanc, i no és 
significatiu el seu ordre.

{:.alert .alert-activity }
<div markdown="1" class="activity">
### Activitat 3. Creació de documents XML
{: .no_toc .nocount }
Escriu un document XML que emmagatzeme la següent informació:

### Ciutats     
{: .no_toc }

| Nom |	País | Continent |
| --- | ---- | --------- | 
| Nueva Delhi | India  | Àsia |
| Lisboa | Portugal | Europa |
| El Cairo | Egipto | África |

Nota: el continent es respresentarà mitjançant un atribut. 


### Fets històrics
{: .no_toc }

![Fets històrics](assets/01-taula-fets-XML.png)

Nota: la descripció de cada fet cal representar-la mitjançant un atribut, la resta d'informació no. 

</div>

## Declaració XML

La declaració XML que es pot escriure al principi d’un document XML comença amb els caràcters "<?" i acaba amb "?>". 

### Versió i codificació 

Un document XML podria contenir la següent declaració XML:

```xml
<?xml version="1.0" encoding="UTF-8"?>
```
En aquesta declaració XML, està indicant que 1.0 és la versió de XML utilitzada en el document i UTF-8 
(8-bit _Unicode Transformation Format_, Formato de Transformación Unicode de 8 bits) és la codificació de caràcters 
empleada.

En un document XML no és obligatori que aparega la declaració XML. Ara bé, si la inclou, ha d'aparèixer en la primera 
línia del document, i el caràcter "<" ha de ser el primer de dita línia, és dir, abans no poden aparèixer espais en blanc.

### Atribut _standalone_

En una declaració XML, a més de la versió i la codificació dels atributs, també es pot escriure l’atribut `standalone`,
 que pot prendre dos valors ("yes" o "no"):

```xml
<?xml version= "1.0" encoding="UTF-8" standalone="yes"?>
```
En escriure `standalone="yes"` s'està indicant que el document és independent d'altres, com per exemple d'una 
DTD (_Document Type Definition_, Definició de Tipo de Documento) externa (o vorem més endavant). En cas contrari, 
significarà que el document no és independent.

En un document XML, escriure la declaració XML és opcional. Pero, si s'escriu, l'atribut `version` és obligatori.
No obstant, els atributs `encoding` i `standalone` són opcionals i, per defecte, els seus valors són "UTF-8" i "no", 
respectivament.

Per una altra part, quan s’escriu l’atribut `encoding`, sempre haurà d’aparèixer després de la versió. I, l'atribut
`standalone`, sempre que existisca, haurá d'estar en l'últim lloc.
 
## Referència a altres entitats

En XML alguns caràcters que són especials pel seu significat (veure taula) i, per escriure'ls en un document XML, es poden utilitzar
 les referències a entitats mostrades en la següent taula:

| Carácter |	Entidad |	Referencia a entidad
| -- | -- | :--: |
| < (menor que)	| lt (_less than_) |	`&lt;`
| > (mayor que)	| gt (_greater than_)	| `&gt;`
| " (comilla doble)	| quot (_quotation mark_) | `&quot;`
| ' (comilla simple) | apos (_apostrophe_) | `&apos;`
| & (ampersand) |	amp (_ampersand_) |	`&amp;`

Donat l'arxiu "entidades.xml":

```xml
<?xml version="1.0" encoding="UTF-8"?>
<entidades>
   <menor_que>&lt;</menor_que>
   <mayor_que>&gt;</mayor_que>
   <comilla_doble>&quot;</comilla_doble>
   <comilla_simple>&apos;</comilla_simple>
   <ampersand>&amp;</ampersand>
</entidades>
```

En obrir-lo en Google Chrome es podrà visualitzar:

![Visualització de l'arxiu entidades.xml a Google Chrome - Exemple d'el tutorial de XML de Abrirllave.com](assets/entidades-xml-chrome.gif)


Al navegador web, es pot veure que on s'han escrit les referències a entitats en el document XML (per exemple), 
es mostren els caràcters corresponents (per exemple <).

### Caràcters problemàtics en XML: menor que (<) i ampersand (&)

En un document XML, el caràcter "<" és problemàtic perquè indica el començament d'una etiqueta. Per tant, 
en comptes d'escriure, per exemple:

```xml
<condicion>a<b</condicion>
```
Caldria utilitzar la referència a entitat escrivint:

```xml
<condicion>a&lt;b</condicion>
```
El caràcter ">" sí que pot utilitzar-se en el text contingut en un element, i no és incorrecte escriure, per exemple:

```xml
<condicion>a>b</condicion>
```
Ara bé, es recomana fer ús de la seva referència a entitat (`&gt;`)

En un document XML, el caràcter _ampersand_ també és problemàtic, ja que s'utilitza per indicar el començament d'una 
referència a entitat. Per exemple, no és correcte escriure:
```xml
<condicion>a==1 && b==2</condicion>
```
En el seu lloc s'ha d'escriure el següent:
```xml
<condicion>a==1 &amp;&amp; b==2</condicion>
```

### Ús de la cometa doble ( ") i de la cometa simple ( ') en atributs

Si el valor d'un atribut s'escriu entre cometes dobles ( "), aquest valor no podrà contenir aquest caràcter. 
Per exemple, no és correcte escriure:

```
<dato caracter="comilla doble(")"/>
```

Per a això, cal utilitzar la referència a entitat com es mostra a continuació:

```xml
<dato caracter="comilla doble(&quot;)"/>
```

De la mateixa manera passa amb la cometa simple ( '), sent incorrecte escriure, per exemple:

```
<dato caracter='comilla simple(')'/>
```

Pel que, en aquest cas, caldria usar com es mostra tot seguit:

```xml
<dato caracter='comilla simple(&apos;)'/>
```

D'altra banda, els valors d'atributs escrits entre cometes dobles ( ") sí que poden contenir el caràcter cometa simple
 ( ') i al revés. Per exemple, és correcte escriure:

```xml
<dato caracter="comilla simple(')"/>
<dato caracter='comilla doble(")'/>
```

En aquests casos, *no és obligatori fer servir les referències a entitats, però sí recomanable*.

### Referències de caràcters en XML

En un document XML es poden escriure referències de caràcters Unicode amb els símbols & #, seguits de la valor decimal
 o hexadecimal de l'caràcter Unicode que es vulgui representar i, finalment, afegint el caràcter punt i coma ";".

Representació del caràcter Euro (€) en XML

Donat el document XML "productos.xml":

```xml
<?xml version="1.0" encoding="UTF-8"?>
<productos>
   <nombre precio="12.56&#8364;">Gorro de lana</nombre>
   <nombre precio="16.99&#x20AC;">Gorro polar</nombre>
</productos>
```

En visualitzar en un navegador web, es podrà veure el següent:

![Visualització de l'arxiu productos.xml a Google Chrome - Exemple d'el tutorial de XML de {Abrirllave.com](assets/productos-xml-chrome.gif)

Cal observar que, en aquest cas, per representar el símbol de l'Euro (€), la primera vegada s'ha utilitzat el seu valor 
decimal (`&#8364`) en Unicode i, la segona vegada, el seu valor hexadecimal (`&#x20AC`).

## Comentaris en XML

Per escriure comentaris en un document XML, aquests s'han d'escriure entre els caràcters "<!-" i "->". Per exemple:

```xml
<!-- Això és un comentari escrit en un document XML -->
```
Donat el fitxer XML "letras.xml":
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!--Ejemplo uso de comentarios.-->
<a>
   <b>
      <c cantidad="4">cccc</c>
      <d cantidad="2">dd</d>
   </b>
   <e>
      <f cantidad="8">ffffffff</f>
      <!--g puede aparecer varias veces.-->
      <g cantidad="5">ggggg</g>
      <g cantidad="2">gg</g>
   </e>
</a>
```
En un navegador es veurà:

![Visualització de l'arxiu letras.xml a Google Chrome - Exemple d'el tutorial de XML de {Abrirllave.com](assets/letras-xml-chrome.gif)

En un document XML, no es poden escriure comentaris dins de les etiquetes. Per exemple, no és correcte escriure:

```xml
<element <!-- element buit -> />
```
D'altra banda, cal tenir en compte que en els comentaris d'un document XML no està permès utilitzar dos guions seguits:

```xml
<!-- dos guions seguits -- en un comentari dóna error ->
```

De manera que, no és possible niar comentaris en un document XML.

## Seccions CDATA en XML

Un document XML pot contenir seccions CDATA (_Character DATA_) per escriure text que no es desitja que sigui analitzat. 
Per exemple, això pot ser útil quan es vol escriure text que continga algun dels caràcters problemàtics: menor que `<` 
o ampersand `&`.

En un document XML, per incloure una secció CDATA, s'escriu començant amb la cadena de caràcters 
"<! [CDATA [" i acabant amb els caràcters "]]>".

Una secció CDATA pot contenir, per exemple, el codi font d'un programa escrit en llenguatge C:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ejemplo_CDATA>
<![CDATA[
#include <stdio.h>
int main()
{
   float nota;
   printf( "\n   Introduzca nota (real): " );
   scanf( "%f", &nota );
   if ( 5 <= nota )
      printf( "\n   APROBADO" );
   return 0;
}
]]>
</ejemplo_CDATA>
```
En un navegador web es visualitzarà cosa semblant a:

![Visualització de l'arxiu ejemplo_cdata.xml a Google Chrome - Exemple d'el tutorial de XML de {Abrirllave.com](assets/ejemplo_cdata_chrome.gif)

Dins d'una secció CDATA no es pot escriure la cadena "]]>". En conseqüència, no es poden niar seccions CDATA.

D'altra banda, no està permès escriure espais en blanc o salts de línia en les cadenes d'inici "<! [CDATA [" o fi "]]>" 
d'una secció CDATA

## Ferramentes d'edició
Per a editar documents XML és suficient en disposar d'un editor de text pla, com Pluma o GEdit, però també podem utilitzar
alguns editors específics com XML Copy Editor o un IDE amb algun connector com Visual Studido Code amb XML Tools.  

## Elaboració de documents XML ben formats

Es diu que un document XML està ben format (well-formed document) quan no té errors de sintaxi. Això inclou els
 següents aspectes:

 * Els noms dels elements i els seus atributs han d'estar escrits correctament.
 * Els valors dels atributs han d'estar escrits entre cometes dobles o simples.
 * Els atributs d'un element s'han de separar amb espais en blanc.
 * S'han d'utilitzar referències a entitats on siga necessari.
 * Hi ha d'haver un únic element arrel.
 * Tot element ha de tenir un element pare, excepte l'element arrel.
 * Tots els elements han de tenir una etiqueta d'obertura i una altra de tancament.
 * Les etiquetes han d'estar correctament niades.
  * La declaració XML ha d'estar en la primera línia escrita correctament.
 * Les seccions `CDATA` i els comentaris han d'estar correctament escrits.


{:.alert .alert-activity}
<div markdown="1" class="activity">


### Activitat 4: Els mòduls de DAW
{:.no_toc .nocount }

Crea un document XML que emmagatzeme els mòduls del cicle de DAW indicant les hores de cada mòduls i el curs en què
s'imparteix.
</div>

{:.alert .alert-activity}
<div markdown="1" class="activity">

### Activitat 5: Documents XML ben format
{:.no_toc .nocount }

[Enunciat de l'activitat ](assets/docsbenformats.pdf)

</div>

## Utilització d'espais de noms en XML
Els espais de noms XML són un mecanisme per assegurar que els elements i els atributs d'un document XML tinguen noms
 únics. Estan definits en una recomanació del W3C. El problema que resolen és l'ambigüitat que sorgeix quan un document
  XML conté noms d'elements o d'atributs provinents de diversos vocabularis i en resulten diversos elements o atributs
   homònims (amb el mateix nom): si a cada vocabulari se li dóna un espai de noms diferent, es resol l'ambigüitat. 
   
 Per exemple:
 
 ```xml
 <carta>
    <palo>Corazones</palo>
    <numero>7</numero>
 </carta>
``` 

```xml
 <carta>
    <carnes>
       <filete_de_ternera precio="12.95"/>
       <solomillo_a_la_pimienta precio="13.60"/>
    </carnes>
    <pescados>
       <lenguado_al_horno precio="16.20"/>
       <merluza_en_salsa_verde precio="15.85"/>
    </pescados>
 </carta>
```

De forma que, si se inclouen els elements `<carta>` en un document XML, s'origina un conflicte de noms. Per a resoldre'l,
 es poden utilitzar espais de noms (XML Namespaces). Per exemple, escrivint:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<e1:ejemplo xmlns:e1="http://www.abrirllave.com/ejemplo1"
   xmlns:e2="http://www.abrirllave.com/ejemplo2">
  
   <e1:carta>
      <e1:palo>Corazones</e1:palo>
      <e1:numero>7</e1:numero>
   </e1:carta>
  
   <e2:carta>
      <e2:carnes>
         <e2:filete_de_ternera precio="12.95"/>
         <e2:solomillo_a_la_pimienta precio="13.60"/>
      </e2:carnes>
      <e2:pescados>
         <e2:lenguado_al_horno precio="16.20"/>
         <e2:merluza_en_salsa_verde precio="15.85"/>
      </e2:pescados>
   </e2:carta> 
</e1:ejemplo>
```

Per a definir un espai de noms s'utilitza la següent sintaxí:

```
xmlns:prefijo="URI"
```

En l'exemple, observa que, `xmlns` és un atribut que s'ha utilitzat en l'etiqueta d'inici de l'element `<ejemplo>` i, 
en aquest cas, s'han definit dos espais de noms que fan referència a los siguientes URI (_Uniform Resource Identifier_, 
Identificador Uniforme de Recurs):

* http://www.abrirllave.com/ejemplo1
* http://www.abrirllave.com/ejemplo2

Los prefixes definits són e1 i e2, respectivament. S'han afegit els prefixes a les etiquetes que apareixen en el 
document: `<e1:carta>`, `<e2:carta>`, `<e1:palo>`, etc.

### Definició d'un espai de noms per defecte

D'altra banda, es pot definir un espai de noms per defecte mitjançant la següent sintaxi:

```
xmlns = "URI"
```

D'aquesta manera, tant l'element on s'ha definit l'espai de noms, com tots els seus successors (fills, fills de fills, 
etc.), han de pertànyer a aquest espai de noms. Per exemple:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ejemplo xmlns="http://www.abrirllave.com/ejemplo1">
  
   <carta>
      <palo>Corazones</palo>
      <numero>7</numero>
   </carta>
    
</ejemplo>
```
En el següent exemple, inicialment es defineix un espai de noms per defecte per a l'element `<ejemplo>` i els continguts
 en ell. Ara bé, posteriorment, es defineix un segon espai de noms, que per defecte afecta el segon element <carta> 
 que apareix en el document i als seus successors: `<carnses>`, `<pescados>`, `<filete_de_ternera>` ...

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ejemplo xmlns="http://www.abrirllave.com/ejemplo1">
  
   <carta>
      <palo>Corazones</palo>
      <numero>7</numero>
   </carta>

   <carta xmlns="http://www.abrirllave.com/ejemplo2">
      <carnes>
         <filete_de_ternera precio="12.95"/>
         <solomillo_a_la_pimienta precio="13.60"/>
      </carnes>
      <pescados>
         <lenguado_al_horno precio="16.20"/>
         <merluza_en_salsa_verde precio="15.85"/>
      </pescados>
   </carta>

</ejemplo>
```

En un document XML, per indicar que determinats elements -o tots- no pertanyen a cap espai de noms, s'escriu l'atribut 
`xmlns` buit, és a dir, `xmlns = ""`.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<ejemplo xmlns="http://www.abrirllave.com/ejemplo1">
  
   <carta>
      <palo>Corazones</palo>
      <numero>7</numero>
   </carta>

   <carta xmlns="http://www.abrirllave.com/ejemplo2">
      <carnes>
         <filete_de_ternera precio="12.95"/>
         <solomillo_a_la_pimienta precio="13.60"/>
      </carnes>
      <pescados xmlns="">
         <lenguado_al_horno precio="16.20"/>
         <merluza_en_salsa_verde precio="15.85"/>
      </pescados>
   </carta>

</ejemplo>
```
En aquest cas, l'element <peixos> i els seus fills, no pertanyen a cap espai de noms.

## Bibliografia, webgrafia i crèdits

* Wikipedia contributors. (2020, September 13). Markup language. _In Wikipedia, The Free Encyclopedia._ 
Retrieved 15:51, September 15, 2020, from 
[https://en.wikipedia.org/w/index.php?title=Markup_language&oldid=978142210](https://en.wikipedia.org/w/index.php?title=Markup_language&oldid=978142210)
* Carlos Pes. (Febrer de 2017). _Lenguajes de Marcas y Sistemas de Gestión de Información (LMSGI)_  disponible en 
[Tutorial de LMSGI](http://www.abrirllave.com/lmsgi/) 
* Bartolomé Sintés Marco. (Juny de 2020). _XML: Lenguaje de marcas extensible_, disponible 
en [https://www.mclibre.org/consultar/xml/](https://www.mclibre.org/consultar/xml/)

