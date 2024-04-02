# Repositori xml-python d'Alejandro Pelaez Almoguera, de 1er DAW
### | Activitat per a l'assignatura de Llenguatge de Marques (M04) |
#### A continuació veurem una documentació sobre una activitat sobre com passar informació d'un arxiu xml a un arxiu python. 
---
<img src="https://github.com/alexpa03/xml-python/blob/main/xml-icon.png?raw=true" alt="xml_logo" width="115"><img src="https://github.com/alexpa03/xml-python/blob/main/python_logo.png?raw=true" alt="python_logo" width="130">
---

> Informació sobre "markdown" extreta de --> [tutorialmarkdown.com](https://tutorialmarkdown.com/guia "markdown")

---
El contongut de l'arxiu "**example.xml**" del que s'extreu la informació durant l'activitat és el següent:

```xml
<?xml version="1.0"?>
<example>
    <company>OpenAI</company>
    <people>
        <person id="P001">
            <name gender="male">John</name>
            <age>30</age>
            <naixement>1985-11-24</naixement>
        </person>

        <person id="P002">
            <name gender="female">Jane</name>
            <age>21</age>
            <naixement>2002-05-11</naixement>
        </person>
    </people>
</example>
```
---
## Procés

En primer lloc importarem el mòdul "**minidom**" del paquet estandard de python "**xml.dom**".
```
from xml.dom import minidom
```
Definim la variable "**doc**" com a importació de l'arxiu "**example.xml**", del que extraurem les dades que volem passar a l'arxiu python.
```
doc=minidom.parse("Practica Minidom/example.xml")
```
A continuació definim la vaiable "**tag_example**" per referenciar al document xml importat anteriorment. 
```
tag_example=doc.documentElement
```
Amb aquesta linia de codi estem afegint a la variable "**tag_people**" la funció de referenciar els elements del document "**example.xml**" que tinguin l'etiqueta "**people**".
```
tag_people=tag_example.getElementsByTagName("people")[0]
```
En aquest cas, referenciem els elements que pertanyen a l'etiqueta "**person**" mitjançant la definició d'aquesta nova variable "**llista_tag_person**". La variable "**tag_people**" està actuant d'etiqueta pare, de forma que s'està buscant el contingut que hi ha dins d'aquesta.
```
lista_tag_person=tag_people.getElementsByTagName("person")
```
Posteriorment, amb el "**for**" indiquem que es cerquin els elements dins del contingut que s'estableix en la variable "**llista_tag_person**". D'aquesta forma podrem realitzar certes accions amb aquests elements. 
```
for tag_person in lista_tag_person:
```
Finalment, realiztem el mateix process constantment definint diferents variables amb l'objectiu d'agafar dades que pertanyen a altres etiquetes pare i imprimir-les en pantalla.

    
    tag_name=tag_person.getElementsByTagName("name")[0]
    valor_name=tag_name.firstChild.data
    valor_age=tag_person.getElementsByTagName("age")[0].firstChild.data
    valor_id=tag_person.getAttribute("id")
    valor_gender=tag_name.getAttribute("gender")
    valor_naixement=tag_person.getElementsByTagName("naixement")[0].firstChild.data
    print ("----------------------------------")
    print(f"El nom és {valor_name}")
    print(f"L'id és {valor_id}")
    print(f"El sexe és {valor_gender}")
    print(f"L'edat és {valor_age}")
    print(f"La data de naixement és {valor_naixement}")
    print("----------------------------------")
   > Tot aquest contingut es localitza dins del "**for**" mencionat anteriorment. 


Com a resultat, el programa en python mostrarà les dades de les persones enregistrades en l'arxiu xml que hi ha al principi del document:

<img src="https://github.com/alexpa03/xml-python/blob/main/programa.png?raw=true)https://github.com/alexpa03/xml-python/blob/main/programa.png?raw=true" alt="programa" width="600">

## Conclusió

Aquesta activitat m'ha fet aprendre a treballar amb fitxers xml a Python mitjançant l'ús del paquet "minidom". A més, he conegut formes molt eficients de navegar per la informació dels fitxers, així com a adonar-me de la importància de la jerarquia de les dades i dels elements.
    
