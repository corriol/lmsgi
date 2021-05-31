---
title: "Exercicis DTD 4 repàs"
listings-no-page-break: true
nav_exclude: true
---

## Activitats de repàs
### formas.xml

El siguiente documento XML ("formas.xml") está bien formado. Sin embargo, no es válido. 
Para que lo sea, realizar los cambios necesarios en dicho documento, pero sin modificar la DTD interna.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE formas [
   <!ELEMENT formas (cuadrado, triangulo, circulo, otra)>
   <!ELEMENT cuadrado (#PCDATA)>
      <!ATTLIST cuadrado lados CDATA #REQUIRED>
   <!ELEMENT triangulo (#PCDATA)>
      <!ATTLIST triangulo lados CDATA #REQUIRED>
   <!ELEMENT circulo (#PCDATA)>
   <!ELEMENT otra EMPTY>
      <!ATTLIST otra lados CDATA #REQUIRED>
]>

<formas>
   <cuadrado lados="4">tablero</cuadrado>
   <circulo>anilla</circulo>
   <triangulo>señal</triangulo>
   <otra lados="7"/>
</formas>
```

### empresas.xml

El siguiente documento XML ("empresas.xml") está bien formado. Sin embargo, no es válido. 
Para que lo sea, realizar los cambios necesarios en dicho documento, pero sin modificar la DTD interna.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE empresas [
   <!ELEMENT empresas (empresa)*>
   <!ELEMENT empresa EMPTY>
      <!ATTLIST empresa nombre CDATA #REQUIRED>
      <!ATTLIST empresa fecha_de_fundacion CDATA #IMPLIED>
]>

<empresas>
   <empresa fecha_de_fundacion="1976">Apple</empresa>
   <empresa>Google</empresa>
   <empresa fecha_de_fundacion="1975">Microsoft</empresa>
</empresas>
```

### articulos.xml

El siguiente documento XML ("articulos.xml") está bien formado. Sin embargo, no es válido. 
Para que lo sea, realizar los cambios necesarios en dicho documento, 
pero sin modificar la DTD interna.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE articulos [
   <!ELEMENT articulos (articulo)+>
   <!ELEMENT articulo (#PCDATA)>
      <!ATTLIST articulo color CDATA #FIXED "rojo">
]>

<articulos>
   <articulo nombre="bolígrafo" color="rojo"/>
   <articulo nombre="cuaderno"/>
   <articulo nombre="rotulador" color="amarillo"/>
</articulos>
```

### geografia.xml

El siguiente documento XML ("geografia.xml") está bien formado. 
Sin embargo, no es válido. Para que lo sea, realizar los cambios necesarios en 
dicho documento, pero sin modificar la DTD interna.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE geografia [
   <!ELEMENT geografia (paises, ciudades)>
   <!ELEMENT paises (pais)*>
      <!ELEMENT pais (#PCDATA)>
         <!ATTLIST pais codpais ID #REQUIRED>
   <!ELEMENT ciudades (ciudad)*>
      <!ELEMENT ciudad (#PCDATA)>
         <!ATTLIST ciudad pais IDREF #IMPLIED>
]>

<geografia>
   <paises>
      <pais codpais="1">Argentina</pais>
      <pais codpais="2">Austria</pais>
      <pais codpais="3">Japón</pais>
      <pais codpais="4">Noruega</pais>
   </paises>
   <ciudades>
      <ciudad pais="3">Osaka</ciudad>
      <ciudad>Oslo</ciudad>
      <ciudad pais="">Sevilla</ciudad>
      <ciudad pais="3">Tokio</ciudad>
      <ciudad pais="2">Viena</ciudad>
   </ciudades>
</geografia>
```


### declaraciones.xml

El siguiente documento XML ("declaraciones.xml") está bien formado. 
Sin embargo, no es válido. Para que lo sea, realizar los cambios necesarios 
en la DTD interna de dicho documento.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE declaraciones [
   <!ELEMENT declaraciones (consonante | tipo_de_dato | variable)>
   <!ELEMENT consonante (#PCDATA)>
      <!ATTLIST consonante valor CDATA #REQUIRED>
   <!ELEMENT tipo_de_dato (#PCDATA)>
   <!ELEMENT variable (#PCDATA)>
      <!ATTLIST variable tipo CDATA #REQUIRED>
]>

<declaraciones>
   <consonante valor="3.141592">PI</consonante>
   <variable tipo="real">radio</variable>
   <variable>area</variable>
   <variable>longitud</variable>
</declaraciones>
```

### saludos.xml

El siguiente documento XML ("saludos.xml") está bien formado. Sin embargo, 
no es válido. Para que lo sea, realizar los cambios necesarios en la DTD interna de dicho documento.

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE saludos [
   <!ELEMENT saludos (saludo*)>
   <!ELEMENT saludo (#PCDATA)>
      <!ATTLIST saludo idioma (ALE | FRA | ITA) "ESP">
]>

<saludos>
   <saludo idioma="ALE">Hallo</saludo>
   <saludo>Hola</saludo>
   <saludo idioma="ITA">Ciao</saludo>
   <saludo idioma="FRA">Salut</saludo>
   <saludo idioma="POR">Olá</saludo>
</saludos>
```

### cine.xml

El siguiente documento XML ("cine.xml") está bien formado. Sin embargo, 
no es válido. Para que lo sea, realizar los cambios necesarios en la DTD interna de dicho documento.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE cine [
   <!ELEMENT peliculas (pelicula)*>
      <!ELEMENT pelicula (#PCDATA)>
         <!ATTLIST pelicula codpel ID (P1 | P2 | P3 | P4) "P0">
   <!ELEMENT actores (actor)*>
      <!ELEMENT actor (#PCDATA)>
         <!ATTLIST actor filmografia IDREF #REQUIRED>
]>

<cine>
   <peliculas>
      <pelicula>Avatar</pelicula>
      <pelicula codpel="P1">Gran Torino</pelicula>
      <pelicula codpel="P2">Invictus</pelicula>
      <pelicula codpel="P3">Million dollar baby</pelicula>
      <pelicula codpel="P4">Oblivion</pelicula>
      <pelicula codpel="P5">Unforgiven</pelicula>
   </peliculas>
   <actores>
      <actor filmografia="P1 P3 P5">Clint Eastwood</actor>
      <actor filmografia="P2 P3 P4 P5">Morgan Freeman</actor>
      <actor filmografia="P4">Tom Cruise</actor>
   </actores>
</cine>
```

### lunas.xml

El siguiente documento XML ("lunas.xml") está bien formado. Sin embargo, no es válido. 
Para que lo sea, realizar los cambios necesarios en la DTD interna de dicho documento.

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE lunas [
   <!ELEMENT luna EMPTY>
      <!ATTLIST luna numero ID #REQUIRED>
      <!ATTLIST luna nombre ID #REQUIRED>
      <!ATTLIST luna planeta #IMPLIED>
]>

<lunas>
   <luna numero="N234" nombre="Galatea"/>
   <luna numero="N479" nombre="Mimas" planeta="Saturno"/>
   <luna numero="N566" nombre="Diode" planeta="Saturno"/>
   <luna numero="N607" nombre="Miranda" planeta="Urano"/>
</lunas>
```

## Crèdits i bibliografia 

Aquests exercicis estan extrets del llibre _Lenguajes de Marcas y Sistemas de Gestión de Información_ de Carlos Pes

* [Versió en línia](https://www.abrirllave.com/dtd/que-es-dtd.php)
* [Versió en PDF](https://www.abrirllave.com/lmsgi/libro.php)

i dels apunts de Barlomé Sintes Marco:

* [https://www.mclibre.org/consultar/xml/lecciones/xml-dtd.html](https://www.mclibre.org/consultar/xml/lecciones/xml-dtd.html)


