---
title: 'Modifier rapidement un ensemble de fichiers sous linux [BASH]'
author: Jice

date: 2008-01-01
url: /2008/01/modifier-rapidement-un-ensemble-de-fichiers-sous-linux-bash
categories:
  - Linux
tags:
  - Bash
  - Linux
  - Script
---
Vous vous trouvez sous Linux, vous désirez changer une chaîne de caractère avec une faute d&#8217;orthographe dans l&#8217;ensemble des fichiers d&#8217;un dossier? Utilisez le script suivant :

## En Bref :

{{< highlight  bash "style=colorful" >}}
#!/bin/bash
for file in *.php
do
echo “Traitement de $file …”
sed -e “s/eMssage avec erreur/Message sans erreur/g” “$file” > “$file”.tmp && mv -f “$file”.tmp “$file”
done
{{< /highlight  >}}



Pour cela, ouvrir une console :

  * _cd /chemin/dossier_ (placez vous dans le dossier concerné)
  * _touch monscript.sh_ (créer un fichier vide nommé monscript)

éditez le fichier et collez le script ci-dessus en faisant les changement nécessaire

  * _./monscript.sh_ (executer lescript en local)

## Le principe :
`for file in *.php` : Tous les fichiers du répertoire qui finissent par l&#8217;extension .

`echo “Traitement de $file …”` : On indique leur nom__

`sed -e “s/eMssage avec erreur/Message sans erreur/g” “$file” > “$file”.tmp && mv -f “$file”.tmp “$file”` : On substitue (s) le premier message par le deuxième message, à toutes les lignes (g). On applique cela à tous les fichiers que l&#8217;on traite actuellement, et on renomme les fichiers temporaires créés pour l&#8217;occasion<br />



Plus d'info sur [Sed](https://fr.wikipedia.org/wiki/Stream_Editor). 

## Remplacer un texte dans des fichiers : Méthode évoluée

A présent je veux remplacer dans l''ensemble de mes fichiers .php la chaine `<?` par la chaîne `<?php`. Evidemment, je ne veux pas remplacer les bonnes chaînes déjà existantes, sinon j'aurai : `<?<?php` ce qui ne sera pas bon.



Première méthode, je le fais à la bourrin, je remplace tous les `<?` puis je remplace les `<?<?` par `<?`.



Deuxième méthode, je suis plus doux, et je vais : chercher les fichiers .php à modifer, effectuer la modification ciblée.


Pour trouver les fichiers à modifier :

`find /rep -name "*.php" | xargs grep "<?[^php]"`
  
_ 

*Le principe* : le `find` permet de trouver les fichiers ayant l'extension .php. Le grep permet de trouver dans un fichier une expression donnée (ici `<?` privée de `php` à sa suite, voir expressions rationnelles). Le `xargs` permet de lire les fichiers envoyé par le pipe de `find`.


Si on a peur d'obtenir beaucoup de résultats on peux demander uniquement l'affichage du nom des fichiers en question :

`find /rep -name "*.php" | xargs grep -l "<?[^php]"`

... ou bien plus de précision en demandant l'affichage de la ligne :

`find /rep -name "*.php" | xargs grep -n "<?[^php]"`

Voici donc le script à utiliser pour la modification :

{{< highlight  bash "style=colorful" >}}
#!/bin/sh
old_value="<?";
new_value="<?php";
ignore_value="<?php";
SUCCESS=0
for file in $(find . -name "*.php")
do
  echo "Traitment de : $file"
  grep -q "$old_value" "$file"
  if [ $? -eq $SUCCESS ]
  # if grep -q "$word" "$filename" can replace lines 5 – 7.
  then
    mv $file $file.old2
    sed "/$ignore_value/!s/$old_value/$new_value/g" < $file.old2 > $file
    rm $file.old2
  fi
done
{{< /highlight  >}}

Placer le dans le dossier sur lequel vous souhaitez faire le traitement, et executer. Pensez à sauver auparavant, sait-on jamais.