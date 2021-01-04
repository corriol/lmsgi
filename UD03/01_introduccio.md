---
layout: default
parent: 3. Aplicació dels llenguatges de marques a la sindicació de continguts 
nav_order: 3
has_children: false
---

# Introducció a la sindicació de continguts

La sindicació (o redifusió) de continguts web consisteix en que part del contingut 
d'una pàgina web es posa a la disposició d'altres llocs o subscriptors individuals
mitjançant un canal web, essent el format més habitual l'RSS, tot seguit
per l'Atom. Els programes informàtics compatibles amb algun d'aquests estàndards
consulten periòdicament un arxiu amb entrades que enllacen amb els articles
complets o parcials en el lloc web original. A diferència d'altres mitjans de comunicació,
els drets de redifusió de continguts web solen ser gratuïts, i no sol intervenir
un contracte entre les parts sinó una llicència de normes d'ús.

![Esquema bàsic sindicació de continguts](assets/rss-basic-scheme.png)

## Un poc d'història

Amb el sistema tradicional de navegació per Internet, per a un usuari era molt
important obtenir els enllaços dels llocs web que li interessaven i emmagatzemar-
los d'alguna manera per poder-hi tornar ràpidament. Si es volien seguir els canvis
en les pàgines web l’única manera que hi havia era anar visitant de tant en tant la
pàgina per comprovar si hi havia novetats.

L'aparició del que es va conèixer com a *Web 2.0* va complicar les coses. El Web
es va emplenar d’una gran quantitat de blogs i pàgines que publicaven informació,
i visitar-les totes per veure si hi havia canvis va passar a requerir molt de temps,
tot plegat per visitar pàgines que potser no havien canviat. S’havia d’optimitzar
d’alguna manera aquesta tasca.

L'aparició dels sistemes estàndard de sindicació va fer possible obtenir la informació
 de les actualitzacions d’un lloc web d’una manera estable per mitjà d’una
adreça. La sindicació de continguts va canviar la manera com es recupera la
informació. Ja no calia anar a buscar la informació: era la informació la que
acudia a l’usuari.

Fent servir la sindicació ja no cal que l’usuari visite les pàgines que li interessen
per a veure si hi ha canvis perquè si n’hi ha ja els rebrà. Això comporta un estalvi
de temps, ja que no caldrà visitar pàgines per descobrir que no hi ha canvis.

Un altre dels avantatges que aporta la sindicació és inherent a XML. A diferència
del que passa amb HTML, és fàcil interpretar el contingut de la informació que es
rep i, per tant, també serà fàcil poder reutilitzar-ne el contingut per fer-hi altres
tasques.

A pesar que la sindicació es veu sovint com un sistema enfocat a detectar novetats
en el Web, també s’està fent servir per a mantenir actualitzacions en altres camps.
Per exemple, alguns programes d’ordinador fan servir RSS per saber si n’han sortit
actualitzacions i d’aquesta manera mantenen els programes actualitzats.

## La sindicació de continguts en l'actualitat

En l'actualitat, amb l'eclosió de les xarxes socials i l'aparició d'altres tecnologies,
l'ús de la sindicació de continguts amb formats estandards ha disminuit i la 
redifusió de continguts s'ha centrat en la publicació en xarxes socials i en
l'ús d'altres sistemes de comparticions com les API.

No obstant, en el món del _podcast_, continua usant-se com a forma automàtica de compartir continguts.

<div markdown="1" class="alert-info alert">
Un **podcast** és fitxer de ràdio, de so o de vídeo destinat a la difusió per podcàsting. 

El **podcàsting** fa referència a la tècnica per a crear i difondre arxius de so i de vídeo 
per Internet que permet que l'usuari puga descarregar-los al seu ordinador i escoltar-los
 o veure'ls quan vulga.
</div>


## Exemple d'ús

![Esdeveniment 24h24l.org](assets/rss-example.png)

Mitjançant un _podcatcher_ podem descarregar els nous _podcasts_ publicats.

En afegir el feed (nom que rep la llista d'elements) ens mostra les novetats
que hi ha.

![gPodder exemple d'ús](assets/podcacher-exemple-1.png)

Una vegada afegit ja estem subscrits i el _podcatcher_ ens avisarà de les novetats.

![gPodder exemple d'ús 2](assets/podcacher-exemple-2.png)

<div markdown="1" class="alert-activity alert">
**Activitat 1. Sindicació de continguts**

En la següent activitat instal·larem una agregador de RSS i ens subscriurem a alguns canals.

1. Instal·la el complement de Firefox: *Feedbro*.
2. Accedeix al complement.
3. Subscriu-te als següents canals:
   1. Els podcasts de l'esdeveniment 24h24l.org.
   2. Les últimes notícies de El País
   3. Les notícies de la Portada de El Mundo.   
4. Comprova si alguna de les pàgines que consultes habitualment fa redifusió dels seus continguts. Si és així subscriu-te al seu canal.
</div>