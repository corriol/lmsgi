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

---


# Material 

En aquesta unitat usarem el llibre _Lenguajes de Marcas y Sistemas de Gestión de Información_ de Carlos Pes

* [Versió en línia](https://www.abrirllave.com/dtd/que-es-dtd.php)
* [Versió en PDF](https://www.abrirllave.com/lmsgi/libro.php)
---