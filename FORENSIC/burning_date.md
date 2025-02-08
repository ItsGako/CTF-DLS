# 🔥 Write-up : Burning DATA 🔥

## 📌 Catégorie : Forensic

### 📝 Enoncé :
> Un technicien de chez OVH a perdu l'accès à ses disques. Ne sachant que faire, il pense faire appel au général Xavier Odeon Ragenet, membre du RAID.
>
> Pouvez-vous réussir à retrouver ses données avant qu'il ne contacte le général ?

---

## 🕵️‍♂️ Analyse des disques

### 1️⃣ Préparation des images disque
On configure les images disque en tant que périphériques loopback :
```bash
sudo losetup /dev/loop0 disk1.img
sudo losetup /dev/loop1 disk3.img
```

### 2️⃣ Analyse initiale des fichiers
On identifie les types de fichiers et partitions :
```bash
file disk1.img file disk2.hs file disk3.img
sudo gdisk /dev/loop0  # Vérification de la structure du disque
sudo blkid /dev/loop0  # Identification du RAID
```

---

## 🛠️ Reconstruction du RAID

### 3️⃣ Installation et assemblage du RAID
On s'assure que `mdadm` est bien installé et on assemble le RAID :
```bash
sudo apt update && sudo apt install mdadm
sudo mdadm --assemble --scan  # Assemblage automatique
# ou
sudo mdadm --assemble /dev/md0 /dev/loop0 /dev/loop1
```

On vérifie l’état du RAID :
```bash
cat /proc/mdstat
```

---

## 📂 Montage et extraction des données

### 4️⃣ Montage du système de fichiers
On monte le RAID pour explorer son contenu :
```bash
sudo mkdir /mnt/raid
sudo mount /dev/md0 /mnt/raid
```

### 5️⃣ Récupération du flag 🎯
```bash
ls /mnt/raid
cp /mnt/raid/FLAG.png ~/Downloads/
```

En ouvrant la photo `FLAG.png`, on découvre le flag :
```
CTF-DLS{}
```

---

## 🧹 Nettoyage
Après récupération des données, on démonte proprement les disques :
```bash
sudo umount /mnt/raid
sudo mdadm --stop /dev/md0
sudo losetup -d /dev/loop0
sudo losetup -d /dev/loop1
```

---

## 🏁 Conclusion

✅ On a identifié la structure des disques.
✅ On a monté un RAID pour récupérer les fichiers.
✅ On a retrouvé et extrait le flag depuis `FLAG.png`.

🔎 **Le fichier `disk2.hs`** nous a aidés à mieux comprendre la structure des fichiers, bien qu'il n'ait pas été essentiel pour récupérer le flag.

⚡ **Flexibilité & Adaptation** : En forensic, il faut savoir s’adapter aux découvertes et ajuster sa méthode. Ici, on a exploré plusieurs pistes avant de confirmer que les disques étaient en RAID.

Mission accomplie ! 🚀🔥

