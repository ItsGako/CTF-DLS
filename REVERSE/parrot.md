## Write-up : Parrot 🦜

**Catégorie :** Reverse 🔍
**Points :** 200 🏆

---

### Énoncé 📜
> Ce perroquet essaye de vous dire quelque chose... 🦜🤔

---

### Analyse du binaire 🔬
En ouvrant le fichier avec IDA, on repère une variable `enc_flag` contenant une suite d'octets situés dans la section `.data` :

```
.data:00004008                 public enc_flag
.data:00004008 enc_flag        db  16h                 ; DATA XREF: flag+28↑o
.data:00004009                 db    1
.data:0000400A                 db  13h
.data:0000400B                 db  78h ; x
.data:0000400C                 db  11h
.data:0000400D                 db  19h
.data:0000400E                 db    6
.data:0000400F                 db  2Eh ; .
.data:00004010                 db  65h ; e
.data:00004011                 db  23h ; #
.data:00004012                 db  66h ; f
.data:00004013                 db  27h ; '
.data:00004014                 db  0Ah
.data:00004015                 db    1
.data:00004016                 db  3Dh ; =
.data:00004017                 db  66h ; f
.data:00004018                 db  0Ah
.data:00004019                 db  13h
.data:0000401A                 db  39h ; 9
.data:0000401B                 db  65h ; e
.data:0000401C                 db  22h ; "
.data:0000401D                 db  28h ; (
```

Ces valeurs correspondent au flag chiffré. 🧐

---

### Déchiffrement du flag 🔓

Après analyse du code, on comprend que chaque octet est chiffré avec un **XOR 0x55**.
On peut donc les récupérer avec un simple script Python :

```python
enc_flag = [0x16, 0x01, 0x13, 0x78, 0x11, 0x19, 0x06, 0x2E, 0x65, 0x23,
            0x66, 0x27, 0x0A, 0x01, 0x3D, 0x66, 0x0A, 0x13, 0x39, 0x65, 0x22, 0x28]

flag = ""
for byte in enc_flag:
    flag += chr(byte ^ 0x55)

print(f"Flag: {flag}")
```

---

### Résultat 🎉

En exécutant ce script, on obtient enfin notre flag :

```
Flag : CTF-DLS{0v3r_Th3_Fl0w}
```

🐦💬 **Le perroquet parlait en XOR !** 🎭

Bravo si tu as réussi à le comprendre et à extraire le flag ! 🎊🚀

---

**Techniques utilisées :**
✅ Analyse du binaire avec IDA 🎯
✅ Extraction de la variable `enc_flag` 🏴
✅ Détection de l'opération XOR 0x55 🤓
✅ Script de déchiffrement Python 🐍

---

🎯 **Challenge complété avec succès !** 🏆🔥

