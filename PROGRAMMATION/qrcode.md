
# Write-up : Gif ou Puzzle ? 🤔

**Catégorie :** Programmation 💻  
**Auteur :** AZOGg 🧙‍♂️  

---

## **Énoncé**  
Une activité suspecte a été détectée sur le réseau : des GIFs mystérieux envoyés vers un terminal anonyme 🕵️‍♂️. Nous avons intercepté un GIF contenant une série de QR codes, suggérant une technique d'exfiltration de données sophistiquée. Déjouons ce plan ! 💥  

---

## **Solution**

### **1. Objectif :**  
Le défi consiste à extraire les données cachées dans un GIF animé contenant plusieurs QR codes. Pour ce faire, nous utiliserons un script Python utilisant les bibliothèques `imageio`, `opencv-python`, et `pyzbar`.

---

### **2. Installation des bibliothèques**

Avant de commencer, assurez-vous d'avoir installé les bibliothèques nécessaires :  

```bash
pip install imageio opencv-python pyzbar
```

---

### **3. Le script Python**

Voici le script Python utilisé pour extraire les données des QR codes :  

```python
import imageio
import cv2
import pyzbar.pyzbar as pyzbar
import re
import os

def extract_qr_codes_from_gif(gif_path):
    try:
        gif = imageio.mimread(gif_path)
        decoded_qr_codes = []
        for frame in gif:
            img = cv2.cvtColor(frame, cv2.COLOR_RGB2BGR)
            decoded_objects = pyzbar.decode(img)
            for obj in decoded_objects:
                decoded_qr_codes.append(obj.data.decode('utf-8'))
        return decoded_qr_codes
    except FileNotFoundError:
        print(f"Error: File not found at {gif_path}")
        return []
    except Exception as e:
        print(f"Error processing GIF: {e}")
        return []

# Chemin du fichier GIF (utilisez des chaînes brutes pour les chemins Windows)
gif_file_path = r"C:\Users\koga9\Downloads\qrcode.gif"  # Remplacez par votre chemin

# Vérifier si le fichier existe
if not os.path.exists(gif_file_path):
    print(f"Error: File not found at {gif_file_path}")
else:
    extracted_data = extract_qr_codes_from_gif(gif_file_path)

    if extracted_data:
        print("Données extraites des QR codes :")
        flag_candidate = "".join(extracted_data)
        print(flag_candidate)

        # IMPORTANT : Adaptez ce regex au format de flag attendu par le CTF
        flag_regex = r"CTF-DLS\{[a-zA-Z0-9-]{36}\}"  
        match = re.match(flag_regex, flag_candidate)
        if match:
            print("Flag valide trouvé :", match.group(0))
        else:
            print("Composants de flag trouvés, mais ne correspondent pas au format attendu.")

    else:
        print("Aucun QR code trouvé ou une erreur est survenue.")
```

---

### **4. Analyse des données extraites**

Après avoir exécuté le script, nous obtenons une chaîne de caractères. Dans ce cas précis, il s'agissait d'une chaîne Base64 inversée :  

```
==gCxATMwETMwADIxATMwATMxADIxEDMwETMwADIwETMxADMxADIwETMxATMxADIwADMwETMwADIwATMwADMxADIxEDMwETMxADIxATMwADMxADIwATMwATMxADIxEDMwETMwADIwED
```

En inversant cette chaîne et en convertissant les données binaires résultantes, on obtient le flag :  

**`L3sQrC0d3sCEstG3n14lP0ur3xF1ltr3dEsD0nN3e5`** 🎉  

---

### **Conclusion**  

Ce challenge était une combinaison intéressante de traitement d'images et de techniques de cryptographie simples (Base64 inversé et binaire). Le plus important était de comprendre comment extraire les données des QR codes du GIF animé. 😎  
