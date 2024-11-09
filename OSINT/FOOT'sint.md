
# Write-Up: FOOT'sint ⚽️

**Nom du Challenge**: FOOT'sint  
**Valeur**: 50 points  
**Catégorie**: OSINT  
**Auteur**: OncleSmaks  
**Format du Flag**: `CTF-DLS{vm_buteur_transfert}`  

## Énoncé 📝

> Un joueur était de passage dans un club français, saurez-vous retrouver sa valeur marchande au moment de rejoindre le club (Chiffre en million) ?

> L'équipe adverse a gagné un match crucial grâce à deux erreurs de défense commises par le joueur présent sur la photo. Ces erreurs défensives ont contribué à 2 buts de l’équipe adverse, quel est le nom du joueur qui les a inscrits ? (Nom de famille)

> Ce joueur a commencé sa carrière professionnelle dans un club de son pays natal, trouvez ce club. Un ancien joueur de l’équipe présente sur la photo a été transféré dans le club en question, pour combien de million d’euros a-t-il été transféré (Chiffre en million) ?

## Étapes de Résolution 🚀

### Étape 1 : Identification du joueur sur la photo 📸
En observant la photo fournie (`fichier.png`), j'ai identifié le joueur comme étant **Dalbert Henrique**, qui a joué pour le Stade Rennais pendant la saison 2020-2021.

### Étape 2 : Valeur marchande du joueur au moment de son transfert 💶
Après avoir confirmé son passage au Stade Rennais, j'ai recherché sa **valeur marchande** lors de son arrivée au club. Elle était de **9 millions d'euros**.

### Étape 3 : Nom du joueur ayant marqué les buts suite aux erreurs de Dalbert 🎯
Lors d'un match crucial, deux erreurs défensives de Dalbert ont permis à **Timo Werner** de marquer **2 buts** sous forme de pénalties. Werner jouait alors pour Chelsea.

### Étape 4 : Club d'origine de Werner et transfert d'un ancien joueur de Rennes vers ce club 🔄
- **Club d'origine de Timo Werner** : Werner a commencé sa carrière professionnelle au **VfB Stuttgart** en Allemagne.
- **Transfert d'un joueur de Rennes vers Stuttgart** : **Serhou Guirassy**, ancien joueur rennais, a été transféré à Stuttgart pour une somme de **9 millions d'euros**.

### Étape 5 : Formatage du flag 📝
En suivant le format donné pour le flag, nous obtenons :

**Flag** : `CTF-DLS{9_werner_9}` 🎉

## Conclusion 🎊
Ce challenge OSINT mêle recherches historiques et sportives pour retracer la carrière de joueurs et leurs transferts. Grâce aux informations trouvées, le flag a été obtenu avec succès !

