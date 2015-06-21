---
title: Générer des pages html dynamiques (changer l’extension php)
author: Jice

date: 2008-07-23
url: /2008/07/generer-des-pages-html-dynamiques-changer-lextension-php/
btc_comment_counts:
  - 'a:0:{}'
btc_comment_summary:
  - 'a:0:{}'
categories:
  - Informatique
  - PHP
tags:
  - Apahce
  - Htaccess
  - PHP
  - Server
  - web
---
### Le principe :

<p align="justify">
  Vous avez des pages html tout ce qu&#8217;il y a de plus statiques. Vous voulez y intégrer du php pour je ne sais quelle raison. Il faut donc se débrouiller pour demander à votre serveur d&#8217;interpréter les pages .htm ou .html comme du php. Pour cela, si vous êtes administrateur, ce n&#8217;est pas trop difficile, ça passe par la <a href="../../index.php?view=article&catid=43%3Aos-a-hardware&id=90%3Aconfigurer-son-apache2&option=com_content&Itemid=63&lang=fr">configuration d&#8217;apache</a>.
</p>

<p align="justify">
  Si vous n&#8217;êtes pas l&#8217;administrateur de votre système vous devrez ruser, et utiliser à bon escient votre .htaccess.
</p>

### Application :

<p align="justify">
  Vous devez vous occuper d&#8217;un gros site, sur lequel on a tout codé au début en html. Les pages sont déjà très bien indexées, mais vous voulez en savoir plus sur vos visiteurs. Comme vous ne maitriser pas le serveur, et que l&#8217;on vous a interdit le mod_rewrite, vous ne pouvez pas faire d&#8217;url rewriting, et donc pas de redirections 301 vers des pages php. La solutions? Transformer les pages html en pages dynamiques.
</p>

<p align="justify">
  Une fois que c&#8217;est fais vous pourrez ajouter votre script php sur les pages, et tout cela juste avec le .htaccess et un peu de travail.
</p>

### La technique :

<p align="justify">
  Il existe, pour votre serveur, deux moyens d&#8217;appeler php : en tant que module ou en tant que script CGI. Pour le vérifier, créer une page info.php qui contient uniquement le code :
</p>

> <p align="justify">
>   <em><?php</em>
> </p>
> 
> <p align="justify">
>   <em>phpinfo();</em>
> </p>
> 
> <p align="justify">
>   <em>?></em>
> </p>

<p align="justify">
  Cela vous permettra de voir comment tourne le php chez vous à la ligne : <strong>SERVER API</strong>. Si vous avez comme résultat &#8220;Server API Apache 2.0 Handler&#8221; alors le php tourne comme un module et ça sera simple. Sinon, vous avez le résultat &#8220;Server API CGI&#8221; et là, ça sera un peu plus complexe.
</p>

#### Module

Créer un .htaccess à la racine de votre répertoire web que vous remplirez de la façon suivante :

>  _AddType application/x-httpd-php .html .htm .php
  
> AddHandler x-httpd-php .html_

Si cela ne marche pas, regardez les liens ci-dessous (les ressources).

#### CGI

Il faut tout d&#8217;abord savoir où est installer le module php. Créez un fichier test.php que vous remplirez de la sorte :

> _<?php_
> 
> _echo &#8220;<br /><br />Whereis php? <br />&#8221;;
  
> $last_line = system(&#8216;which php&#8217;, $retval);
  
> echo $last_line;_
> 
> _?>_

Le résultat obtenu dépendra du serveur. Pour ma part, j&#8217;ai :

> _php: /usr/local/bin/php /usr/local/man/man1/php.1.gz php: /usr/local/bin/php /usr/local/man/man1/php.1.gz_

Ainsi, je repère que le php de base est installé à /usr/local/bin/php. Je mets cette information de côté.

Maintenant je crée un fichier .htaccess que je rempli de la façon suivante :

> _Options +ExecCGI +Includes
  
> AddHandler server-parsed htm
  
> AddHandler cgi-script .htm_

<p align="justify">
  Vous pouvez aussi remplacer l&#8217;extension <em>htm </em>par ce que vous voulez. Votre site sera un peu &#8220;customisé&#8221;.
</p>

<p align="justify">
  A partir de maintenant, le serveur ne vois plus vos pages comme des documents, mais comme des programmes, il va devoir les exécuter. Il faut donc vous assurez que celles-ci soit exécutables (et pas seulement &#8220;lisibles&#8221;). Ouvrez un shell, et tapez :
</p>

> <p align="justify">
>   <em>chmod -R +x *.htm</em>
> </p>

<p align="justify">
  Les fichiers .htm sont maintenant autorisés à être exécutés. Il ne reste plus qu&#8217;une étape.
</p>

<p align="justify">
  Ajouter, en début de chacun de vos fichiers .htm la ligne suivante :
</p>

> <p align="justify">
>   <em>#!/usr/local/bin/php (rappelez-vous, je l&#8217;ai eu ci-dessus avec le fichier test.php)</em>
> </p>

<p align="justify">
  Le retour à la ligne entre le code et votre page web est INDISPENSABLE. Vos obtiendrez une grosse erreur 500 sinon.
</p>

<p align="justify">
  Voilà, normalement c&#8217;est bon, vos pages .htm sont lisibles par le CGI php. Vous obtenez donc des pages htm dynamiques.
</p>

### Les ressources :

Si jamais tout cela ne marche pas, survolez les forums du net. Essayez entre autres :

<a href="http://www.webmasterworld.com/forum88/603.htm" target="_blank">http://www.webmasterworld.com/forum88/603.htm</a>

<a href="http://www.modwest.com/help/kb5-1.html" target="_blank">http://www.modwest.com/help/kb5-1.html </a>