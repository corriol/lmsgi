---
layout: default
parent: 3. Aplicació dels llenguatges de marques a la sindicació de continguts 
nav_order: 3
has_children: false
---

# Estructura dels canals de continguts

Els canals d'informació web (_feeds_, en anglès) permeten als programes comprovar 
si hi ha  actualitzacions publicades en un lloc web. Per proporcionar un canal web, 
el propietari del lloc pot utilitzar un programari especialitzat (com ara un
 sistema de gestió de contingut) que publica una llista (o "feed") d'articles o 
 contingut recents en un format estandarditzat de lectura automàtica. 

El canal es pot descarregar mitjançant programes que l’utilitzen, com ara 
llocs web que distribueixen contingut del feed, o mitjançant programes lectors de feeds 
anomenats *agregadors* que permeten als usuaris d’Internet subscriure’s a 
canals i veure’n el contingut.

Un canal (_feed_) conté entrades, que poden ser titulars, articles de text complet,
extractes, resums o enllaços a contingut d’un lloc web juntament amb diverses metadades.

A continuació analitzarem les característiques dels dos estàndards, basats en XML,
 per a la creació de canals de continguts: RSS 2.0 i Atom 1.0.

## RSS 2.0

RSS (_RDF Site Summary_ o _Really Simple Syndication_) és un canal (_feed_) web que permet 
als usuaris i a les aplicacions accedir a actualitzacions de llocs web en un format
estandarditzat i llegible per ordinador. 

Va ser desenvoluat pel _RSS Advisory Board_ i la seua primera versió, RSS 0.90, aparegué en març de 1999.
La darrera versió, la 2.0, va apareixer en març de 2009.

<div markdown="1" class="alert-info alert">
Un format de fitxer XML estàndard garanteix la compatibilitat amb moltes màquines/programes diferents.
Els canals RSS també beneficien els usuaris que vulguen rebre actualitzacions oportunes
 de llocs web preferits o agregar dades de molts llocs.
</div>

RSS és text pla amb format XML. El format RSS en si és relativament fàcil de llegir
tant per processos automatitzats com per humans. Un _feed_ d'exemple pot tenir 
contingut com el següent:

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<rss version="2.0">
<channel>
 <title>RSS Title</title>
 <description>This is an example of an RSS feed</description>
 <link>http://www.example.com/main.html</link>
 <copyright>2020 Example.com All rights reserved</copyright>
 <lastBuildDate>Mon, 06 Sep 2010 00:01:00 +0000 </lastBuildDate>
 <pubDate>Sun, 06 Sep 2009 16:20:00 +0000</pubDate>
 <ttl>1800</ttl>

 <item>
  <title>Example entry</title>
  <description>Here is some text containing an interesting description.</description>
  <link>http://www.example.com/blog/post/1</link>
  <guid isPermaLink="false">7bd204c6-1655-4c27-aeee-53f933c5395f</guid>
  <pubDate>Sun, 06 Sep 2009 16:20:00 +0000</pubDate>
 </item>
</channel>
</rss>
```

**Diagrama d'arbre del canal RSS**
![Diagrama d'arbre del canal RSS](assets/asxm04u3_03.png)
 
Al nivell superior, un document RSS és un element `<rss>`, amb un atribut
 obligatori anomenat `version`, que especifica la versió de RSS que compleix 
 el document. 

Subordinat a l'element `<rss>` hi ha un element `<channel>` que conté informació 
sobre el canal (metadades) i el seu contingut en elements `<item>`.

Per a més detalls podeu accedir a l'especificació: 
[RSS 2.0 Specification](https://www.rssboard.org/rss-specification)

## Atom

El format de sindicació d’àtoms és un llenguatge XML que s’utilitza per a feeds web.

El format Atom es va desenvolupar com a alternativa a RSS. Ben Trott, defensor 
del nou format que es va convertir en Atom, creia que RSS tenia limitacions i defectes, 
com ara la manca d’innovació contínua i la seva necessitat de mantenir-se compatible, 
i que hi havia avantatges en un disseny nou.

Un document basat en el format Atom té la següent estructura:

```xml
<?xml version="1.0" encoding="utf-8"?>

<feed xmlns="http://www.w3.org/2005/Atom">
  <title>Example Feed</title>
  <subtitle>A subtitle.</subtitle>
  <link href="http://example.org/feed/" rel="self" />
  <link href="http://example.org/" />
  <id>urn:uuid:60a76c80-d399-11d9-b91C-0003939e0af6</id>
  <updated>2003-12-13T18:30:02Z</updated>
    
    
<entry>
  <title>Atom-Powered Robots Run Amok</title>
  <link href="http://example.org/2003/12/13/atom03" />
  <link rel="alternate" type="text/html" 
    href="http://example.org/2003/12/13/atom03.html"/>
  <link rel="edit" href="http://example.org/2003/12/13/atom03/edit"/>
  <id>urn:uuid:1225c695-cfb8-4ebb-aaaa-80da344efa6a</id>
  <updated>2003-12-13T18:30:02Z</updated>
  <summary>Some text.</summary>
    <content type="xhtml">
      <div xmlns="http://www.w3.org/1999/xhtml">
        <p>This is the entry content.</p>
      </div>
    </content>
    <author>
      <name>John Doe</name>
      <email>johndoe@example.com</email>
    </author>
</entry>

</feed>
```
Per a més detalls: [RFC 4287 - The Atom Syndication Format](https://tools.ietf.org/html/rfc4287)


## Validació

<div markdown="1" class="alert-info alert">
Com que tant RSS com Atom són documents XML, es podrà comprovar que
són correctes fent servir les mateixes eines de comprovació que es fan servir
en XML.
</div>

Malgrat que és possible fer servir els validadors d’XML, el més normal és fer
servir programes específics per validar RSS i Atom com el _Feed Validation Service_ de W3C
 ([validator.w3.org/feed](https://validator.w3.org/feed))


<div markdown="1" class="alert-activity alert">
**Activitat 2. Creació d'un feed RSS**

Eres el creador de la web receptari-exemple.org i actualment tens en la 
pàgina principal el següent contingut.

```html
<!DOCTYPE html>
<html lang="ca">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Receptari</title>
</head>

<body>
  <header>
    <h1>Receptari exemplar</h1>
  </header>
  <main>
    <article>
      <h2>Arròs al forn</h2>
      <time datetime="2020-12-13 08:00:00">diumenge, 13 de desembre de 
        2020</time>
      <p>La peculiaritat d'aquest arròs, com indica el mateix nom, és 
        que està cuinat al forn. I,
        igual que la paella i altres arrossos valencians, també és un 
        plat d'origen popular, que en aquest cas s'elaborava a partir 
        de les restes del putxero. És per això que entre els seus 
        ingredients no falten els cigrons, les costelles de porc i la 
        botifarra. Aquest plat és especialment típic en comarques com 
        la Costera, on a Xàtiva se celebra des de fa
        uns quants anys el Concurs Nacional d'Arròs al Forn.</p>
      <p><a href="/2020/12/arros-al-forn.html">Continua llegint</a></p>
    </article>
    <article>
      <h2>Paella valenciana</h2>
      <time datetime="2020-04-06 13:20:00">dilluns, 6 d’abril de
       2020</time>
      <p>La paella és el màxim estendard de la cuina valenciana i 
      probablement també de l'espanyola, a causa del seu reconeixement 
      gastronòmic a escala mundial. El seu origen, com el de tots els 
      plats de la cuina popular, deriva de la conjunció dels aliments que
      cada família tenia al seu abast, especialment en la zona de 
      l'horta de València, que es proveïa de verdures fresques. 
      A més, antigament era costum criar pollastres i conills per 
      a ús familiar, per la qual cosa, si a tot això unim l'abundància
      de l'arròs conreat en l'Albufera, el resultat és aquest 
      plat genuïnament valencià que rep el nom del recipient en el 
      qual es cuina.</p>
      <p><a href="/2020/04/paella-valenciana.html">Continua llegint</a></p>
    </article>
    <article>
      <h2>Olleta</h2>
      <time datetime="2019-12-28 18:20:00">divendres, 28 de desembre de 
      2019</time>
      <p>L'olleta és el plat més representatiu a la zona de la muntanya 
      d'Alacant i a l'interior de València. Es tracta d'un putxero suculent,
      similar a un potatge caldós però dels més refinats de tot Espanya, 
      i per això es reconegut a escala nacional. El seu sabor intens
      i perfumat deriva de la fragància aromàtica dels embotits i, 
      una vegada desgreixat, aconsegueix un punt sublim.</p>
      <p><a href="/2019/12/olleta.html">Continua llegint</a></p>
    </article>
  </main>
  <footer>
  </footer>
</body>
</html>
```
Crea el canal RSS en la versió 2.0 perquè els usuaris s'assabenten quan publiques noves receptes.

Valida l'arxiu.
</div>
