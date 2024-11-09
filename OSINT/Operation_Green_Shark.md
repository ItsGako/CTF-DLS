
# Write-Up: Operation Green Shark 🦈

**Nom du Challenge**: Operation Green Shark  
**Valeur**: 100 points  
**Catégorie**: OSINT  
**Auteur**: Whiterose  
**Format du Flag**: `CTF-DLS{NOM_DU_POINT_DE_LA_PRISE_DE_VUE|AAAA_MM_JJ}`  

## Énoncé 📝

> Suite à une perquisition, les services de renseignements ont trouvé une carte SD contenant une photo sensible d'un navire de guerre français. Après analyses par le labo, il est certain que l'image n'a subi aucune modification (pas inversée, ni retouchée).  
> **Objectif** : Retrouver les informations suivantes :  
> - Nom du lieu où a été prise la photo  
> - Date de la prise de la photo  

> **Format du Flag** : `CTF-DLS{NOM_DU_POINT_DE_LA_PRISE_DE_VUE|AAAA_MM_JJ}`

## Étapes de Résolution 🚀

### Étape 1 : Identification du navire ⚓
En utilisant **Google Lens** pour une recherche d’image inversée sur la photo fournie, j’ai rapidement identifié le navire comme étant le **Charles de Gaulle**, le porte-avions de la Marine nationale française.

### Étape 2 : Recherche de la date 📅
En cherchant des informations sur les passages du Charles de Gaulle dans des ports français, j’ai trouvé plusieurs articles relatant son arrivée à **Brest le 13 mars 2020** dans le cadre d’une mission en Atlantique et mer du Nord. Cette date est confirmée par l'article suivant :  
**[Le Charles de Gaulle arrive à Brest pour une mission en Atlantique - Le Point](https://www.lepoint.fr/societe/le-charles-de-gaulle-arrive-a-brest-en-vue-d-une-rare-mission-en-atlantique-et-mer-du-nord-13-03-2020-2367079_23.php)**.

### Étape 3 : Localisation du point de prise de vue 🌉
Pour identifier le lieu exact de la prise de vue, j'ai analysé le fond de l’image, où l'on aperçoit un pont. Des recherches plus poussées m'ont permis de conclure qu'il s'agit du **Pont de l'Iroise** situé à Brest. 

Ensuite, en cherchant un point de vue permettant d’apercevoir le Charles de Gaulle avec le pont en arrière-plan, le site **Pointe des Espagnols** est ressorti comme un emplacement probable et pertinent pour cette vue lointaine.

### Étape 4 : Formatage du flag 📝
En suivant le format demandé, j’ai remplacé les espaces par des underscores et mis les noms en majuscules, ce qui donne le flag suivant :  
`CTF-DLS{POINTE_DES_ESPAGNOLS|2020_03_13}`.

## Conclusion 🎉
Ce challenge OSINT a exigé des recherches approfondies en reconnaissance d'image, en analyse géographique, et en vérification de sources d'actualité. Grâce à Google Lens, à des articles de presse, et à l’analyse de points de vue, j’ai pu identifier le lieu et la date exacts pour obtenir le flag. 🎊
