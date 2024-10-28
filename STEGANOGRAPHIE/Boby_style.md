
# Write-Up: Boby Style CTF Challenge

**Challenge Name**: Boby_style  
**Description**: Le but de ce challenge est de décoder un message caché écrit dans le système "bibi-binaire" créé par le chanteur français Boby Lapointe dans les années 1960. Ce message, une fois décodé, fournit des valeurs hexadécimales qui, une fois converties en ASCII, révèlent le flag.  
**Format du Flag**: `CTF-DLS{flag}`  
**Auteur**: Los Ban DDOS  

## Étapes de Résolution

### Étape 1 : Analyse de l'encodage "bibi-binaire"
Le "bibi-binaire" est une forme de notation hexadécimale dans laquelle chaque symbole unique correspond à une valeur en base 16 (hexadécimale). Pour décoder ce message, la première étape a consisté à comprendre la correspondance entre les symboles bibi-binaires présents dans l'image et les valeurs hexadécimales standard.

### Étape 2 : Décodage des symboles
En examinant l'image, j'ai identifié chaque symbole et l'ai associé à sa valeur hexadécimale équivalente en suivant le système bibi-binaire. Cette étape a été réalisée manuellement en transcrivant chaque symbole dans son équivalent hexadécimal. Cela a donné une séquence hexadécimale du type `43 54 46 2d...`.

### Étape 3 : Conversion de l'hexadécimal en ASCII
Une fois la séquence hexadécimale obtenue, je l'ai convertie en texte ASCII. Chaque paire de caractères hexadécimaux (un octet) a été transformée en son caractère ASCII correspondant. Cette conversion m'a permis de révéler un texte lisible contenant le flag.

### Étape 4 : Formattage du flag
Enfin, le flag extrait a été mis en forme selon le format demandé, `CTF-DLS{flag}`, pour soumettre la réponse correcte.

## Conclusion
Ce challenge a permis d'explorer l'ingéniosité de l'encodage bibi-binaire inventé par Boby Lapointe. En traduisant les symboles en hexadécimal puis en ASCII, le flag a été révélé avec succès. Ce type de challenge met en avant des compétences en cryptographie et en résolution de codes historiques, tout en nécessitant un travail minutieux d'observation et de transcription manuelle.
