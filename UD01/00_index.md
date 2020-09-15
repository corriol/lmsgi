---
layout: default
title: 1. Llenguatges de marques 
nav_order: 1
---
# Llenguatge de marques

## Concepte de llenguatge de marques.
Un llenguatge de marcat o llenguatge de marques és una forma de codificar un document que, juntament amb el text, 
incorpora etiquetes o marques que contenen informació addicional sobre l'estructura del text o la seva presentació.

El llenguatge de marques més estès és l’HTML (HyperText Markup Language, llenguatge de marcat d’hipertext), fonament del
 World Wide Web (xarxa de comunicació d’abast mundial).
 
Alguns exemples:
 
HTML 4.0
 ```html
 <h1>Anatidae</h1>
 <p>
   The family <i>Anatidae</i> includes ducks, geese, and swans,
   but <em>not</em> the closely related screamers.
 </p>
 ```
XML
```xml
<?xml version="1.0" encoding="UTF-8"?>
<note>
  <to>Tove</to>
  <from>Jani</from>
  <heading>Reminder</heading>
  <body>Don't forget me this weekend!</body>
</note> 
```
  
## Avantatges. Necessitat d'ús.

Inicialment els llenguatges de marques es van enfocar a la generació de documents però gràcies als seus avantatges
s'ha extès el seu ús envers la definició d'estructures de dades i la compartició d'informació. 

Dels avantatges destaquem:
* La facilitat de creació i lectura.
* El compliment d’estàndards d’emmagatzematge definits i públics.
* La incorporació de metadades.
* La definició de l’estructura de les dades.

## Característiques comunes.
Els llenguatges de marques són una manera de codificar un document de text
de manera que per mitjà de les marques (l’equivalent de les metadades dels
fitxers binaris) s’hi incorpora informació relativa a com s’ha de representar
el text, sobre quina estructura tenen les dades que conté, etc.
Els llenguatges de marques han destacat per una sèrie de característiques que els
han convertit en els tipus de llenguatges més usats en la informàtica actual per
emmagatzemar i representar les dades. Entre les característiques més interessants
que ofereixen els llenguatges de marques hi ha:
* Que es basen en el text pla.
* Que permeten fer servir metadades.
* Que són fàcils d’interpretar i processar.
* Que són fàcils de crear i prou flexibles per representar dades molt diverses.

Les aplicacions d’Internet i molts dels programes d’ordinador que es fan servir
habitualment fan servir d’alguna manera o altra algun llenguatge de marques.

## Identificació d'àmbits d'aplicació
Quant als àmbits d'aplicació podem definir la següent classificació:

* Documents en general:
  * Llenguatges descriptius com YAML, EBML.
  * Llenguatges de presentació com RTF, Tex, HTML
  * Llenguatges lleugers com Markdown
* Tecnologies d'internet:
  * HTML, XHTML, GladeXML, Atom, RSS, WSDL
* Lleguatges especialitzats:
  * SVG, XMPP, COLLADA 

En [Lenguaje de marcado](https://es.wikipedia.org/wiki/Lenguaje_de_marcado#Principales) trobareu més informació.

## Classificació.
 
És complicat fer una classificació dels llenguatges de marques que hi ha però
generalment s’accepta que en tenim dos grans grups basant-nos en quin és
l’objectiu bàsic del llenguatge de marques:

* **Llenguatges procedimentals i de presentació**, orientats a especificar com
s’ha de representar la informació.
* **Llenguatges descriptius o semàntics**: orientats a descriure l’estructura de
les dades que conté.
Aquesta és la classificació més acceptada però, com molt sovint passa en l’àmbit
de la Informàtica, ens podem trobar llenguatges que tinguin aspectes dels dos
grups i permetin tant definir la manera de presentar la informació com definir-ne
l’estructura.

### Procedimentals i de presentació
En aquests llenguatges el que es fa és indicar de quina manera s’ha de fer
la presentació de les dades. Ja sigui per mitjà d’informació per al disseny
(marcar negretes, títols, etc.) o de procediments que ha de fer el programari de
representació. L’exemple més popular d’aquests llenguatges és l’HTML però n’hi
ha molts més: TeX, Wikitext...
En aquests casos els documents ens poden servir per determinar de quina manera
es mostrarà el document a qui el llegeixi.

##### Latex: un llenguatge de marcat procedimental
```latex
\documentclass{article}
\usepackage{graphicx}

\begin{document}

\title{Introduction to \LaTeX{}}
\author{Author's Name}

\maketitle

\begin{abstract}
The abstract text goes here.
\end{abstract}

\section{Introduction}
Here is the text of your introduction.

\begin{equation}
    \label{simple_equation}
    \alpha = \sqrt{ \beta }
\end{equation}

\subsection{Subsection Heading Here}
Write your subsection text here.

\begin{figure}
    \centering
    \includegraphics[width=3.0in]{myfigure}
    \caption{Simulation Results}
    \label{simulationfigure}
\end{figure}

\section{Conclusion}
Write your conclusion here.

\end{document}
```

### Descriptius o semàntics
En aquests llenguatges es descriu quina estructura lògica té el document ignorant
de quina manera serà representada en els programes. Només es posen les marques
amb l’objectiu de definir les parts que donen estructura al document. L’exemple
més important és l’XML però n’hi algun altre que està tenint molt de suport, com
per exemple JSON.
En el document següent tenim un exemple d’un fitxer de marques que dóna
informació sobre persones:
```xml
<alumnes>
    <persona>
        <nom>Pere</nom>
        <cognom>Puig</cognom>
    </persona>
    <persona>
        <nom>Manel</nom>
        <cognom>Garcia</cognom>
    </persona>
</alumnes>
```
Es pot veure clarament que la informació de les marques en el document estableix
quin és el contingut de les dades: una llista d’alumnes. Amb un simple cop d’ull
resulta fàcil determinar que Pere i Manel són noms i que Puig i Garcia són
cognoms. Però per mitjà de la jerarquia de les dades es pot inferir que Pere Puig
i Manel Garcia són alumnes ja que tant nom com cognom estan englobats dins
de la marca alumnes.

Aquest document mostra quina és l’estructura de les dades que conté i a més
aquesta també es pot descobrir tot interpretant les etiquetes el seu contingut
semàntic. A partir dels coneixements que es tinguin es dedueix que Pere és el
nom d’una persona que és un alumne.

En els darrers anys, s’han desenvolupat diversos llenguatges de marques senzills i poc estandarditzats per permetre 
als autors crear text formatat a través de navegadors web, com els que s’utilitzen en wikis i en fòrums web. 
De vegades s’anomenen llenguatges de marcatge lleugers. Markdown i el llenguatge de marques utilitzat per la Viquipèdia
 en són exemples.

{:.alert .alert-activity}
<div markdown="1">
### Exercicis
1. Compara les diverses possibilitats d'exportació, a l'hora de guardar un document en LibreOffice Writer.

2. Escriu en un fitxer de text pla el següent:
	```html
	<h1> encapçalat de nivell 1 </h1>
	<h3> encapçalat de nivell 3 </h3>
	```
Obri este fitxer des del navegador. Còm es veu?
Canvia-li la extensió del fitxer per html. Canvia la visualització?

3. Busca en Internet una classificació de llenguatges de marques. Indica 3 exemples de cada tipus indicant el seu ús
principal.

4. Entra en openclipart.org, cerca "8 ball", descarrega la imatge més senzilla que veges. Obre-la amb l'editor de text.
Pots intuir l'esctructura? Mira de canviar el color de la bola des de l'editor (pista: els colors tenen el format: #000000).
</div>

## XML
### Estructura i sintaxi.
### Etiquetes.
### Ferramentes d'edició.
### Elaboració de documents XML ben formats.
### Utilització d'espais de noms en XML.
