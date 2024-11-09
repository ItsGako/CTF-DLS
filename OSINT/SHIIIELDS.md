
# Write-Up: SHIIIELDS 🛡️

**Nom du Challenge**: SHIIIELDS  
**Valeur**: 25 points  
**Catégorie**: OSINT  
**Auteur**: SoyFabinho  
**Format du Flag**: `CTF-DLS{jj_mm_yyyy_hh_mm_ss}`  

## Énoncé 📝

> À quelle date et quelle heure le premier post LinkedIn de l'association Shields a-t-il été posté ?

## Étapes de Résolution 🚀

### Étape 1 : Recherche du compte LinkedIn de l'association 📲
En effectuant une recherche LinkedIn pour "**SHIELDS DLS**", j'ai trouvé le profil LinkedIn officiel de l'association **Shields**.

### Étape 2 : Identification du premier post 📜
En parcourant les publications du compte, j'ai identifié le tout premier post. Pour obtenir les détails exacts, j'ai cliqué sur les **trois petits points** en haut à droite du post pour copier le lien direct :
**[Lien vers le post](https://www.linkedin.com/posts/shields-dls_salut-jeune-padawan-de-la-s%C3%A9curit%C3%A9-en-ces-activity-6785621428499730432-lt_8?utm_source=share&utm_medium=member_desktop)**.

### Étape 3 : Récupération de la date et heure exactes 🕒
Pour obtenir la date et l'heure précises, j'ai utilisé l'outil en ligne **[LinkedIn Post Date Extractor](https://trevorfox.com/linkedin-post-date-extractor.html)** :
1. J'ai collé l'URL du post dans l'outil.
2. L'outil m'a retourné la date exacte en heure locale : **Wed Apr 07, 2021, 07:56:59 PM GMT+2**.

### Étape 4 : Formatage du flag 📝
En suivant le format demandé pour le flag, j'ai transformé la date et l'heure en : `CTF-DLS{07_04_2021_19_56_59}`.

## Conclusion 🎉
Ce challenge OSINT a permis de combiner des recherches LinkedIn avec un outil d'extraction de dates pour identifier le tout premier post de l'association Shields. En appliquant le bon format, le flag a été obtenu avec succès ! 🎊
