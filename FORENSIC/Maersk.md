
# Write-Up: Maersk CTF Challenge 🚢

**Challenge Name**: Maersk  
**Valeur**: 100 points  
**Description**: Ce challenge a pour objectif de découvrir un flag caché dans une image Docker en simulant un cas d'espionnage industriel. Une fois l'image analysée, le flag a été récupéré à partir d'un fichier qui avait été supprimé après déchiffrement. 🔍  
**Format du Flag**: `CTF{flag}`  
**Auteur**: Florent  

## Étapes de Résolution 🚀

### Étape 1 : Téléchargement de l'image Docker 🐳
La première étape a été de télécharger l'image Docker avec la commande suivante :

```bash
docker pull fvln/decipher-flag
```

### Étape 2 : Installation de Dive 🔧
Pour explorer l'image et ses couches, j'ai installé l'outil **dive** :

```bash
sudo snap install dive
```

### Étape 3 : Analyse de l'image avec Dive 🔍
En exécutant la commande suivante, j'ai ouvert l'interface de dive :

```bash
dive fvln/decipher-flag
```

Cela m'a permis de visualiser les différentes couches de l'image et de repérer les fichiers intéressants.

### Étape 4 : Identification des fichiers cachés 🗂️
Dans l'interface dive, j'ai remarqué les fichiers `cleartext_flag.txt` et `decipher.sh` en rouge dans le répertoire `/data`. Étant donné que le fichier cleartext avait été supprimé, j'ai compris qu'il était crucial de trouver un moyen de le récupérer.

### Étape 5 : Récupération de l'ID de la couche 5 🔑
Pour accéder à la couche contenant les fichiers, j'ai récupéré l'ID de la couche 5, qui était nécessaire pour extraire les fichiers :

```bash
1804c04e63bb
```

### Étape 6 : Exécution du conteneur Docker 🐋
J'ai ensuite exécuté le conteneur pour explorer son contenu :

```bash
docker run -it --entrypoint /bin/bash 1804c04e63bb
```

À l'intérieur du conteneur, j'ai trouvé le fichier `ciphered_flag.txt`, mais pas le script de déchiffrement.

### Étape 7 : Sauvegarde de l'image Docker en tarball 🗃️
Pour récupérer le fichier manquant, j'ai sauvegardé l'image Docker dans un fichier tar :

```bash
docker save -o decipher-flag.tar fvln/decipher-flag
```

### Étape 8 : Extraction du tarball 📦
J'ai ensuite extrait le fichier tar pour accéder à ses couches :

```bash
tar -xvf decipher-flag.tar
```

### Étape 9 : Recherche dans les couches extraites 🔍
En cherchant dans les couches extraites, j'ai trouvé le fichier `cleartext_flag.txt` dans la couche 5, que j'ai pu afficher avec :

```bash
cat path/to/cleartext_flag.txt
```

### Étape 10 : Découverte du Flag 🎉
Finalement, j'ai découvert le flag :

```
CTF{Beware_of_devops!}
```

## Conclusion 🎊
Ce challenge a démontré l'importance des compétences en forensic et en analyse d'images Docker. En utilisant des outils comme dive et en explorant les couches de l'image, j'ai pu récupérer le flag qui avait été caché dans le conteneur. Ce type de challenge souligne la nécessité d'une approche méthodique pour résoudre des problèmes de sécurité.
