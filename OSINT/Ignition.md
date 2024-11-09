
# Write-Up: Ignition 🚀

**Nom du Challenge**: Ignition  
**Valeur**: 200 points  
**Catégorie**: OSINT  
**Auteur**: N0x  
**Format du Flag**: `CTF-DLS{NOM:JJ/MM/AAAA}`  

## Énoncé 📝

> Lors d'une enquête, cette photo a été récupérée. Trouvez les informations suivantes :  
> - Nom du site géographique où cette photo a été prise (en majuscules, accent inclus)
> - Date de la prise de la photo

> **Format du Flag** : `CTF-DLS{NOM:JJ/MM/AAAA}`

## Étapes de Résolution 🚀

### Étape 1 : Analyse de la photo avec Google Lens 🔍
En utilisant **Google Lens** pour une recherche d'image inversée, nous avons identifié que la photo avait probablement été prise en **Guyane Française**. En bas de la photo, nous avons pu distinguer l'inscription **"GUY"**, ce qui renforce cette hypothèse.

### Étape 2 : Indices supplémentaires sur la photo 🕵️
Une observation plus attentive a révélé une autre inscription : **IGN France**, indiquant que cette photo faisait partie d'une collection de l’Institut national de l'information géographique et forestière (IGN).

### Étape 3 : Recherche dans les archives IGN 🗂️
Nous nous sommes rendus sur le site de l’IGN pour explorer les archives photographiques en Guyane. En utilisant le site **[Remonter le temps - IGN](https://remonterletemps.ign.fr/telecharger/)**, nous avons recherché dans les années 1980 les photos correspondant à la Guyane.

Nous avons pu retrouver l'image correspondante par tâtonnement. La photo choisie affichait une date de mission correspondant au **15 octobre 1987**. Voici le lien vers l’image trouvée :  
**[IGN Photo](https://remonterletemps.ign.fr/telecharger/?lon=-52.801002&lat=5.230748&z=13.2&layer=pva&year=1986&mission=92PHQ4781)**.

### Étape 4 : Localisation du site géographique 🌍
En utilisant Google Maps pour localiser précisément le lieu, nous avons identifié le site comme étant celui du **Lancement Diamant**.

### Étape 5 : Formatage du flag 📝
En suivant le format demandé, nous avons formaté le flag comme suit :  
`CTF-DLS{DIAMANT:15/10/1987}`

## Conclusion 🎉
Ce challenge a requis une analyse attentive de la photo et des recherches OSINT sur des archives cartographiques historiques. Grâce aux informations trouvées sur l'IGN et une localisation par Google Maps, nous avons pu identifier le lieu et la date pour compléter le flag. 🎊
