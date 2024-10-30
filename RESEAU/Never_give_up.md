
# Write-Up: Never Give Up CTF Challenge 💻

**Challenge Name**: Never give up  
**Valeur**: 100 points  
**Description**: Ce challenge consiste à trouver un flag caché dans une capture réseau (fichier `.pcapng`). En analysant les paquets ICMP, le flag se dévoile via des messages encodés en Base64. 📡  
**Format du Flag**: `CTF-DLS{flag}`  
**Auteur**: Cybertoto  

## Étapes de Résolution 🚀

### Étape 1 : Analyse de la capture réseau 🕵️‍♂️
En ouvrant le fichier `never-give-up.pcapng` dans **Wireshark**, j'ai observé un grand nombre de paquets utilisant le protocole **ICMP**. Ces paquets contenaient des données suspectes sous forme de chaînes encodées en Base64, ce qui indiquait que le flag pourrait être caché parmi ces messages.

### Étape 2 : Décodage des messages en Base64 🔍
J'ai parcouru chaque paquet ICMP contenant des données en Base64, que j'ai décodées à la main. Voici les résultats fréquents obtenus après décodage :
- `"Le flag"`
- `"Le flag est CTF-DLS{"`
- `"Et non"`
- `"Toujours pas"`

Ces messages semblaient être des indications trompeuses, nous encourageant à continuer la recherche dans les paquets suivants.

### Étape 3 : Identification du paquet contenant le flag 🧩
Après avoir examiné de nombreux paquets, le paquet **383/384** contenait une chaîne en Base64 différente : `Q1RGLURMU3tyMWNLcjBsbF8xc19pTl95MHVyX0hlNGR9==`.

### Étape 4 : Décodage du flag 🎉
En décodant cette chaîne Base64 (`Q1RGLURMU3tyMWNLcjBsbF8xc19pTl95MHVyX0hlNGR9==`), j'ai obtenu le flag complet :

```
CTF-DLS{r1cKr0ll_1s_iN_y0ur_He4d}
```

### Étape 5 : Soumission du flag 📤
Le flag décodé a ensuite été soumis dans le format requis `CTF-DLS{flag}`, ce qui a permis de compléter avec succès ce challenge.

## Conclusion 🎊
Ce challenge démontre l'importance de l’analyse minutieuse des captures réseau, notamment des paquets ICMP. En décodant les messages encodés en Base64, j'ai pu extraire le flag. Ce type de challenge permet de renforcer les compétences en analyse de trafic réseau et en encodage. La persévérance était essentielle pour trouver le flag caché parmi des messages trompeurs, rendant le challenge encore plus gratifiant à résoudre.
