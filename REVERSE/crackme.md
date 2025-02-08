# 🏆 Write-up : Craquer son slip (200 points) 🚀

## 📌 Catégorie : Reverse Engineering

### 📝 Enoncé :
> Un crackme ni plus ni moins 💻🔍

---

## 🔍 Analyse du binaire

En ouvrant le fichier dans IDA, on remarque une fonction `check_password` qui compare l'entrée utilisateur avec une chaîne stockée dans le programme.

En lisant attentivement le code assembleur, on comprend que chaque caractère du mot de passe entré est transformé par un **XOR** avec une valeur de `enc_flag`, puis avec la longueur du flag.

Notre objectif est donc d'inverser cette opération pour retrouver la chaîne originale.

---

## 🔑 Solution

Voici le script Python utilisé pour retrouver le flag :

```python
# Chaîne chiffrée extraite du binaire
encoded_flag = [ord(c) for c in 'E"eMU!|[GaMQ`&qy!`']

# La longueur du flag est la même que la chaîne chiffrée
flag_length = len(encoded_flag)

# Déchiffrement en appliquant XOR avec la longueur du flag
decoded_flag = ''.join(chr(encoded_flag[i] ^ flag_length) for i in range(flag_length))

print("Flag:", decoded_flag)
```

---

## 🎯 Résultat

En exécutant ce script, on obtient le flag suivant :

```
W0w_G3nIUs_Cr4ck3r
```

Mission accomplie ! 🚀🔥

---

## 🏁 Conclusion

Ce challenge nous a permis de :
✅ Analyser du code assembleur
✅ Comprendre l'utilisation du XOR en protection
✅ Écrire un script pour inverser l'opération

Un super challenge pour progresser en **Reverse Engineering** ! 🎉😎

