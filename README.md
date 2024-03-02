# xml-python
## Documentació de l'activitat sobre <minidom> per a l'assignatura M04 - Llenguatge de marques.
### En la següent activitat veurem com passar informació d'un arxiu xml a un arxiu python.
<img src="https://github.com/alexpa03/xml-python/blob/main/python_logo.png?raw=true" alt="python_logo" width="300">

---
En primer lloc importarem el mòdul **minidom** del paquet estandard de pytohn **xml.dom**.
```
from xml.dom import minidom
```

Definim la variable "doc" com a importació de l'arxiu "example.xml", del que extraurem les dades que volem passar a l'arxiu python.
```
doc=minidom.parse("Practica Minidom/example.xml")
```

A continuació definim la vaiable "tag_example" per referenciar al document xml importat anteriorment. 
```
tag_example=doc.documentElement
```

Amb aquesta linia de codi estem afegint a la variable "tag_people" la funció de referenciar els elements del document "example.xml" que tinguin l'etiqueta "people".
```
tag_people=tag_example.getElementsByTagName("people")[0]
```

En aquest cas, referenciem els elements que pertanyen a l'etiqueta "person" mitjançant la definició d'aquesta nova variable "llista_tag_person". La variable "tag_people" està actuant d'etiqueta pare, de forma que s'està buscant el contingut que hi ha dins d'aquesta.
```
lista_tag_person=tag_people.getElementsByTagName("person")
```

Posteriorment, amb el "for" indiquem que es cerquin els elements dins del contingut que s'estableix en la variable "llista_tag_person". D'aquesta forma podrem realitzar certes accions amb aquests elements. 
```
for tag_person in lista_tag_person:
```
    
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
    
