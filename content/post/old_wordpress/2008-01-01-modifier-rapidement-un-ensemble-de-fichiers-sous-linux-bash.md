---
title: 'Modifier rapidement un ensemble de fichiers sous linux [BASH]'
author: Jice

date: 2008-01-01
url: /2008/01/modifier-rapidement-un-ensemble-de-fichiers-sous-linux-bash/
btc_comment_counts:
  - 'a:0:{}'
btc_comment_summary:
  - 'a:0:{}'
categories:
  - Linux
tags:
  - Bash
  - Linux
  - Script
---
Vous vous trouvez sous Linux, vous désirez changer une chaîne de caractère avec une faute d&#8217;orthographe dans l&#8217;ensemble des fichiers d&#8217;un dossier? Utilisez le script suivant :

### En Bref :

> _#!/bin/bash_
> 
> _for file in *.php_
> 
> _do_
> 
>  _echo &#8220;Traitement de $file &#8230;&#8221;_
> 
>  _sed -e &#8220;s/eMssage avec erreur/Message sans erreur/g&#8221; &#8220;$file&#8221; > &#8220;$file&#8221;.tmp && mv -f &#8220;$file&#8221;.tmp &#8220;$file&#8221;_
> 
> _done_

Pour cela, ouvrir une console :

  * _cd /chemin/dossier_ (placez vous dans le dossier concerné)
  * _touch monscript.sh_ (créer un fichier vide nommé monscript)

éditez le fichier et collez le script ci-dessus en faisant les changement nécessaire

  * _./monscript.sh_ (executer lescript en local)

**Le principe** :

__for file in *.php <- Tous les fichiers du répertoire qui finissent par l&#8217;extension .php__

_ _echo &#8220;Traitement de $file &#8230;&#8221; <- On indique leur nom__

_ _sed -e &#8220;s/eMssage avec erreur/Message sans erreur/g&#8221; &#8220;$file&#8221; > &#8220;$file&#8221;.tmp && mv -f &#8220;$file&#8221;.tmp &#8220;$file&#8221;__ 

<p align="justify">
  <em><em><- On substitue (s) le premier message par le deuxième message, à toutes les lignes (g). On applique cela à tous les fichiers que l&#8217;on traite actuellement, et onrenomme les fichiers temporaires créés pour l&#8217;occasion<br /> </em></em>
</p>

Plus d&#8217;info sur : <a title="SED" href="http://fr.wikipedia.org/wiki/Sed_(logiciel)" target="_blank">http://fr.wikipedia.org/wiki/Sed_(logiciel)</a>

### Remplacer un texte dans des fichiers : Méthode évoluée

<p align="justify">
  A présent je veux remplacer dans l&#8217;ensemble de mes fichiers .php la chaine &#8220;<?&#8221; par la chaîne &#8220;<?php&#8221;. Evidemment, je ne veux pas remplacer les bonnes chaînes déjà existantes, sinon j&#8217;aurai : &#8220;<?<?php&#8221; ce qui ne sera pas bon.
</p>

<p align="justify">
  Première méthode, je le fais à la bourrin, je remplace tous les &#8220;<?&#8221; puis je remplace les &#8220;<?<?&#8221; par &#8220;<?&#8221;.
</p>

<p align="justify">
  Deuxième méthode, je suis plus doux, et je vais : chercher les fichiers .php à modifer, effectuer la modification ciblée.
</p>

Pour trouver les fichiers à modifier :

  * _find /rep -name &#8220;*.php&#8221; | xargs grep &#8220;<?[^php]&#8221;
  
_ 

<p align="justify">
  <strong>Le principe</strong>: le find permet de trouver les fichiers ayant l&#8217;extension .php. Le grep permet de trouver dans un fichier une expression donnée (ici &#8220;<?&#8221; privée de &#8220;php&#8221; à sa suite, voir expressions rationnelles). Le xargs permet de lire les fichiers envoyé par le pipe de find.
</p>

<p align="justify">
  Si on a peur d&#8217;obtenir beaucoup de résultats on peux demander uniquement l&#8217;affichage du nom des fichiers en question :
</p>

  * _find /rep -name &#8220;*.php&#8221; | xargs grep -l &#8220;<?[^php]&#8221;_

> &#8230; ou bien plus de précision en demandant l&#8217;affichage de la ligne :

  * _find /rep -name &#8220;*.php&#8221; | xargs grep -n &#8220;<?[^php]&#8221;_

Script à utiliser pour la modification :

>  _#!/bin/sh</p> 
> 
> old_value=&#8221;<?&#8221;;
  
> new_value=&#8221;<?php&#8221;;
  
> ignore_value=&#8221;<?php&#8221;;
  
> SUCCESS=0
> 
> for file in $(find . -name &#8220;*.php&#8221;)
  
> do
  
> echo &#8220;Traitment de : $file&#8221;
  
> grep -q &#8220;$old_value&#8221; &#8220;$file&#8221;
  
> if [ $? -eq $SUCCESS ]
  
> \# if grep -q &#8220;$word&#8221; &#8220;$filename&#8221; can replace lines 5 &#8211; 7.
  
> then
  
> mv $file $file.old2
  
> sed &#8220;/$ignore\_value/!s/$old\_value/$new_value/g&#8221; < $file.old2 > $file
  
> rm $file.old2
  
> fi
  
> done</em></blockquote> 
> 
> On le place dans /html et on exécute. Pensez à sauver auparavant, sait-on jamais.