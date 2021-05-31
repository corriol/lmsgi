---
layout: default
parent: 7. Emmagatzemament d'informació
nav_order: 6
has_children: false
---
# Introducció

Els fitxers en XML estan en un format de text estandarditzat que serveix per 
representar, emmagatzemar i transportar informació estructurada. Per tant l’XML es pot fer servir com a mètode d’emmagatzematge de dades neutre, ja que la informació emmagatzemada en fitxers XML es pot moure d’una màquina a una altra sense que hi hagi problemes. Això el fa un mètode ideal per emmagatzemar dades històriques que ens assegura que es podran tornar a llegir en el futur sense problemes.

Això ha fet que les organitzacions cada vegada tinguen una quantitat més gran de documents XML, i que en conseqüència localitzar els documents en el moment adequat siga cada cop més complicat. Per tant cal alguna manera d’organitzar les dades XML que permeta localitzar-les ràpidament.

Però no solament n’hi ha prou de localitzar els documents, ja que sovint el que es busca estarà repartit en diferents documents. També cal alguna manera de poder consultar i manipular les dades que contenen els fitxers XML. Aquest sistema de consulta ha de ser capaç de fer cerques en els documents i modificar-ne dades si cal, però sempre mantenint uns mínims d’eficiència.

Davant d’aquestes necessitats la solució se sol donar de dues maneres:

Com que majoritàriament les organitzacions ja tenen sistemes d’emmagatzematge organitzats de dades basats en dades relacionals una possible solució podria ser convertir els fitxers XML a dades relacionals:
   
   1. L’emmagatzematge de dades serà totalment organitzat i centralitzat en un punt on ja hi ha les altres dades de l’organització. El seu llenguatge de consulta, SQL, és molt conegut i es fa servir molt, de manera que no caldrà que els usuaris aprenguin un nou llenguatge.
   2. Una altra solució consisteix a crear un sistema d’emmagatzematge pensat només per als fitxers XML. Són els sistemes coneguts com a bases de dades natives XML. Aquests:
      * Proporcionen un lloc per emmagatzemar ordenadament fitxers XML.
      * Tenen el seu llenguatge de consulta propi: XQuery.

Tot i que en la teoria és fàcil fer aquesta distinció, en la pràctica molt sovint les organitzacions fan servir sistemes d’emmagatzemament mixtos, en els quals desen en dades relacionals aquelles dades que han de ser emmagatzemades o consultades, i en XML aquelles dades que han de ser representades en entorns web o que s’han d’intercanviar o transportar a altres sistemes.

L’objectiu d’aquest mòdul no és ser expert en bases de dades, per tant només veurem alguns exemples de coses que es poden fer en base de dades per treballar amb XML.

## Bases de dades relacionals

Quasi totes les organitzacions tenen les seves dades organitzades amb algun sistema relacional, ja que els sistemes gestors de bases de dades s’han convertit en un element indispensable en el funcionament de les empreses. Es fan servir per controlar moltes de les dades de funcionament de les empreses: facturació, comptabilitat, estocs…

Per tant, davant de l’aparició d’un nou tipus de dades, un dels raonaments fàcils seria: “si ja tenim un sistema d’organització de dades que funciona bé, per què no podem posar aquestes dades en el mateix sistema?”. D’aquesta manera, les dades que s’obtingueren dels fitxers XML aconseguirien un sistema molt eficient d’emmagatzematge i un mètode de manipulació d’informació que ha estat molt provat durant molts anys i que coneix molta gent.

La inclusió dels fitxers XML en els sistemes gestors de bases de dades relacionals es pot fer de dues maneres:

  1. Convertir les dades dels fitxers XML en dades relacionals:
      Aquest sistema té l’avantatge que les dades, un cop dins del sistema relacional, seran idèntiques a les ja existents.
        L’inconvenient més important és que si torna a fer falta el document XML original pot ser molt difícil regenerar-lo, ja que sovint hi haurà informació sobre l’estructura XML que no s’emmagatzemarà.
  2. Emmagatzemar els documents XML sencers en les bases de dades:
   Es posaran els fitxers XML sencers en un camp d’una taula de la base de dades, de manera que serà com les altres dades.
        Per poder-hi treballar bé caldrà que la base de dades ofereixi alguna manera mitjanament eficient de poder fer cerques en el contingut dels documents XML.

### Convertir les dades XML en relacionals

Una solució que pot semblar senzilla però que en realitat no n’és tant consisteix a agafar les dades dels fitxers XML i transformar-les en dades relacionals. Un cop s’hagen incorporat les dades a la base de dades es podran eliminar els fitxers XML.

Com que en el document XML ja hi ha definida l’estructura de les dades, i sovint els documents XML estaran associats a un vocabulari, tindrem que:

 1. Generar l’estructura de taules relacionals es pot fer analitzant l’estructura del document XML.
 2. Es poden obtenir els camps de la definició del vocabulari o simplement observant el contingut del document XML.

I a més hi ha sistemes que permeten transformar dades XML en altres tipus de fitxers (per exemple, XSLT).

Convertir un document XML en dades relacionals

Si es parteix del document XML següent:

```xml
<?xml version="1.0"?>
<alumnes>
   <alumne>
      <nom>Frederic</nom>
      <cognom>Pi</cognom>
   </alumne>
   <alumne>
      <nom>Filomeno</nom>
      <cognom>Garcia</cognom>
   </alumne>
</alumnes>
```
És relativament senzill veure que l’estructura del document consisteix en una llista d’elements `<alumne>`. 
I que els `<alumne>` tindran dos camps de dades que són `<nom>` i `<cognom>`.

Per tant, l’estructura relacional d’aquest fitxer serà simplement crear una taula `‘alumne’` que tingui com a dades un nom i un cognom. Això és trivial amb l’ordre CREATE TABLE d’SQL:

```sql
CREATE TABLE alumne (nom VARCHAR(30), cognom VARCHAR(30))
```

Obtenir les dades per emplenar la taula tampoc no ha de ser un problema gran. Simplement cal fer INSERT de cada camp de dades:

```sql
INSERT INTO alumne VALUES("Frederic", "Pi");
INSERT INTO alumne VALUES("Filomeno", "Garcia");
```

Per no haver-ho de fer manualment el més fàcil seria crear una plantilla XSLT que faci la transformació del fitxer XML en les regles SQL.

A pesar de l’aparent senzillesa d’aquest sistema, no sempre és senzill fer aquesta conversió, ja que els sistemes relacionals i XML parteixen de conceptes bastant diferents:

* El sistema relacional està basat en dades bidimensionals sense jerarquia ni ordre, mentre que el sistema XML està basat en arbres jeràrquics en què l’ordre és significant.
* En un document XML hi pot haver dades repetides, mentre que els sistemes relacionals fugen de les repeticions.
* Les relacions i les estructures dins dels documents XML no sempre són òbvies.
* Què passa si necessitem tenir el document XML de nou? Fer el procés invers no sempre és trivial. Un dels conceptes difícils és determinar quines dades eren atributs i quines elements.

Per tant, normalment aquest no és el sistema més aconsellable però és un sistema vàlid que pot ser útil en casos concrets. 

### Sistemes relacionals amb extensions XML

Fins a l’aparició d’XML pràcticament tothom emmagatzemava les dades que s’havien de consultar o modificar ràpidament per mitjà d’algun sistema relacional. Els sistemes gestors de bases de dades han estat durant anys els reis de l’administració de dades en les organitzacions.

Però l’increment d’informació en XML que s’havia de poder consultar o que es requeria per fer tasques que abans estaven reservades a les bases de dades relacionals ha provocat que s’hagi hagut d’incloure algun tipus de suport XML en els sistemes gestors de bases de dades.

Tots els grans sistemes de bases de dades importants com Oracle, IBM DB2 o Microsoft SQL Server tenen algun tipus de suport per a XML, que normalment es concreta en el següent:

* Permetre exportar les dades relacionals en algun format XML per transportar les dades.
* Tenir alguna manera de poder emmagatzemar documents XML com a camps en taules relacionals.
* Permetre fer cerques i canvis en els documents XML emmagatzemats.
* Generar XML a partir de les dades relacionals de la base de dades.

A pesar que SQL/XML forma part de l’estàndard SQL, no tots els gestors de bases de dades el suporten.

Com que SQL (el llenguatge de consulta de dades relacional per excel·lència) no tenia suport per a XML el 2003, es va modificar l’estàndard del llenguatge SQL per afegir l’extensió SQL/XML.
SQL/XML

SQL/XML és una extensió de l’estàndard SQL que permet treballar amb el llenguatge XML per mitjà d’instruccions SQL.

Aquesta extensió va ser desenvolupada per un grup en el qual hi havia les grans empreses de bases de dades (Microsoft, Oracle, IBM, SyBase, DataDirect Tecnologies…) i ja està implementada en algun sistema de bases de dades.

A pesar de participar en l’elaboració de l’estàndard, Microsoft va anunciar que no tenia intenció d’incorporar SQL/XML en el Microsoft SQL Server. En comptes d’això, el Microsoft SQL Server fa servir un sistema propi anomenat Microsoft SQLXML o OPENXML per treballar amb SQL i XML.

SQL/XML defineix tota una sèrie de funcions per a publicació de fitxers XML a partir de dades relacionals, defineix un tipus de dades XML i una manera de consultar i manipular les dades XML emmagatzemades.

## XQuery

Una de les necessitats més bàsiques a l’hora de poder fer cerques en les dades és disposar d’un llenguatge per fer consultes que sigui prou potent per poder cobrir les necessitats dels que l’han de fer servir. Per aquest motiu es va desenvolupar el llenguatge XQuery.

XQuery és un llenguatge de consultes pensat per convertir-se en la manera estàndard de recuperar dades de col·leccions de documents XML.

Es tracta d’un llenguatge funcional, de manera que en comptes de dir-li quines són les passes per fer una tasca el que es fa és avaluar les expressions contra el fitxer XML i generar un resultat. A diferència dels llenguatges de programació habituals, en XQuery s’especifica què és el que es vol i no la manera com ho ha de fer per obtenir-ho.

Xquery 3.0

Ja està en desenvolupament una nova versió d’XQuery que permetrà incrementar la potència de les consultes tot afegint clàusules noves com group by o el control d’errors dinàmics. La podeu consultar a www.w3.org/TR/xquery-30

Entre les característiques més interessants d’XQuery, aquest permet:

    Seleccionar la informació segons criteris. Ordenar, agrupar, afegir dades.
    Filtrar la informació que es vulgui del flux de dades.
    Cercar informació en un document o en un grup de documents.
    Unir dades de múltiples documents.
    Transformar i reestructurar XML.
    No estar limitat a la cerca, ja que pot fer operacions numèriques i de manipulació de caràcters.
    Pot treballar amb espais de noms i amb documents definits per mitjà de DTD o XSD.

Una part important d’XQuery 1.0 és el llenguatge XPath 2.0, que és la part que li permet fer les seleccions d’informació i la navegació pel document. 

## Bases de dades natives XML

Si no entrem en detalls tècnics, la definició d’una base de dades és un lloc en el qual es poden emmagatzemar dades. En el cas d’una base de dades en XML, consistiria simplement en emmagatzemar els fitxers XML en un punt concret del sistema operatiu.

L’increment de documents XML a emmagatzemar ha fet que, malgrat que l’emmagatzematge es pugui fer manualment, sigui interessant disposar d’alguna manera d’automatitzar el procés. Per facilitar aquesta automatització han aparegut les bases de dades natives XML (NXD).

Quan es parla de bases de dades natives XML es fa referència a bases de dades dissenyades per contenir i emmagatzemar dades en format XML.

A diferència del que passa amb les bases de dades relacionals, que fa molts anys que funcionen i tenen darrere seu una base teòrica important, les NXD no tenen uns estàndards definits per fer les coses i la teoria que les suporta no està gaire definida. Això fa que sovint cada base de dades faci les coses d’una manera que pot ser totalment diferent de com ho fa una altra.

Les bases de dades natives XML es fan servir sobretot per emmagatzemar dades que contenen:

    Contingut narratiu.
    Que són menys previsibles que les que s’emmagatzemen normalment en bases de dades relacionals.
    Que han de generar sortides per a entorns web.
    Que s’han de transportar d’un sistema a un altre.