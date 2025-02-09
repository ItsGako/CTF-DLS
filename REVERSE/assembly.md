# 🏛️ L'Assembly nationale - Writeup

## 📌 Informations

- **Nom** : L'Assembly nationale
- **Catégorie** : Reverse
- **Points** : 100
- **Auteur** : La\_Kil

## 📜 Énoncé

> Michelle de la comptabilité semble encore avoir été victime de phishing ! 😱 Heureusement, le fichier malveillant a été extrait pour analyse. 🔍 À vous de découvrir la vraie nature de ce malware ! 💀

---

## 🚀 Solution

### 📥 Étape 1 : Téléchargement et première analyse

On commence par récupérer le fichier et vérifier son contenu. Une approche simple consiste à utiliser `ndisasm` pour voir son désassemblage :

```bash
┌──(kali㉿kali)-[~/Downloads]
└─$ echo -ne "\xC7\x44\x24\x04\x41\x54\x51\x21\xC7\x44\x24\x04\x6F\x24\x72\x71\xC7\x44\x24\x08\x2C\x28\x2B\x2E\xC7\x44\x24\x0C\x24\x25\x7B\x28\xC7\x44\x24\x10\x43\x12\x40\x1A\xC7\x44\x24\x14\x45\x40\x44\x13\xC7\x44\x24\x18\x19\x1A\x1C\x48\xC7\x44\x24\x1C\x15\x18\x4D\x1C\xC7\x44\x24\x20\x01\x52\x57\x0B\xC7\x44\x24\x24\x01\x48\xC3\x10\x31\xC9\x31\xD2\x31\xC0\x8A\x14\x0C\xB0\x10\x66\x01\xC8\x30\xC2\x88\x14\x0C\x66\xFF\xC1\x66\x83\xF9\x28\x75\xEA\x31\xC0\x31\xFF\xFE\xC0\x66\xFF\xC7\x48\x89\xE6\xB2\x27\x0F\x05\xB0\x3C\x48\x31\xF6\x0F\x05" | ndisasm -b 32 -
```

### 🔍 Étape 2 : Analyse du code

Le désassemblage nous donne un aperçu des instructions exécutées. On remarque une boucle qui applique une transformation sur des octets placés sur la pile. Cela indique une potentielle **obfuscation** du message caché ! 🕵️

### 📝 Étape 3 : Déchiffrement

On extrait les valeurs modifiées et on inverse le processus d'obfuscation avec un petit script Python :

```python
# Valeurs stockées sur la pile (en little endian)
data = [
    0x21515441,
    0x7172246f,
    0x2e2b282c,
    0x287b2524,
    0x1a401243,
    0x13444045,
    0x481c1a19,
    0x1c4d1815,
    0x0b575201,
    0x10c34801
]

# Convertir en bytes
encoded_bytes = b"".join(d.to_bytes(4, 'little') for d in data)

# Appliquer la transformation XOR
decoded_bytes = bytearray()
for i in range(len(encoded_bytes)):
    decoded_bytes.append(encoded_bytes[i] ^ (0x10 + i))

# Affichage du message décodé
print("Message décodé :", decoded_bytes.decode(errors='ignore'))

```

### 🏆 Étape 4 : Récupération du flag

L'exécution de ce script révèle enfin notre flag tant convoité ! 🎉

```
QEC2{1df411588e7c3b9aeb4136c95c31ce85}
```

---

## 🎯 Conclusion

Ce challenge nous a permis d'explorer l'obfuscation en assembleur et de pratiquer la rétro-ingénierie sur un petit morceau de shellcode. 💻🔬 Un excellent exercice pour renforcer ses compétences en reverse engineering ! 🚀

À bientôt pour de nouveaux défis ! 😉🔥

