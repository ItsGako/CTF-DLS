
# Défi CTF : Maersk 🚢

## Description
Le défi tourne autour de l'espionnage industriel impliquant une image Docker d'un concurrent de Maersk. La tâche consiste à extraire un drapeau caché du conteneur Docker en utilisant des techniques forensiques. Ce défi vaut **100 points** ! 🎯

## Étapes franchies

1. **Tirer l'image Docker** :
   Tout d'abord, j'ai exécuté la commande pour tirer l'image Docker du dépôt public :
   ``bash
   docker pull fvln/decipher-flag
   ```

2. **Exploration de l'image Docker** :
   Pour inspecter les couches de l'image Docker et identifier les fichiers d'intérêt, j'ai utilisé l'outil `dive` :
   ``bash
   dive fvln/decipher-flag
   ```
   - J'ai trouvé que l'image contenait plusieurs couches, et j'étais particulièrement intéressé par la cinquième couche, où se trouvaient des fichiers comme `cleartext_flag.txt` et `decipher.sh`.

3. **Accéder à la couche** :
   Après avoir réalisé que le script `decipher.sh` n'était pas disponible dans le conteneur, j'ai eu besoin d'extraire les fichiers de la couche. J'ai sauvegardé l'image Docker dans un fichier tar :
   ``bash
   docker save -o decipher-flag.tar fvln/decipher-flag
   ```

4. **Extraire la couche** :
   J'ai extrait le fichier tar pour accéder à son contenu :
   ``bash
   tar -xvf decipher-flag.tar
   ```
   - J'ai trouvé un répertoire correspondant aux couches, et j'ai ciblé spécifiquement la couche contenant `cleartext_flag.txt` :
   ``bash
   tar -xf /home/gako/7db0a850bd5757b09c66f9bedf7d1b10900508d8b21a732930ffd2d81289190e/layer.tar -C maersk
   ```
   - Ceci a extrait le contenu dans un dossier nommé `maersk`, où je trouve le répertoire `/data`.

5. **Récupération du drapeau** :
   Dans le répertoire `/data`, j'ai trouvé le fichier `cleartext_flag.txt`. J'ai affiché son contenu en utilisant :
   ``bash
   cat /data/cleartext_flag.txt
   ```
   - Le drapeau révélé était : **CTF{Beware_of_devops!}** 🎉

## Conclusion
Ce défi a mis en évidence l'importance de l'analyse forensique et la capacité à extraire des informations cachées des images Docker. Il a nécessité de la patience et des compétences en résolution de problèmes pour naviguer efficacement à travers les couches et les fichiers. 🚀

---
*Flag found : CTF{Beware_of_devops!}*
