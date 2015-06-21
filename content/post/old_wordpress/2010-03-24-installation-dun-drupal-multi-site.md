---
title: Installation d’un Drupal multi-site
author: Jice

date: 2010-03-24
url: /2010/03/installation-dun-drupal-multi-site/
Image:
  - http://digital.edipresse.com/wp-content/uploads/2009/08/drupal1.gif
categories:
  - Informatique
tags:
  - blog
  - CMS
  - Drupal
  - Installation
---
<p style="text-align: justify;">
  {{<img class="alignleft" style="margin-left: 20px; margin-right: 20px;" title="Drupal - CMS" src="http://digital.edipresse.com/wp-content/uploads/2009/08/drupal1.gif" alt="Drupal - CMS" width="250" height="250" >}}Petit article très rapide pour présenter la procédure d&#8217;installation d&#8217;un <a title="Drupal - CMS" href="http://drupal.org/" target="_blank">Drupal</a> multi-sites sur un serveur tout bête ( le plus petit mutualisé peut servir).
</p>

<p style="text-align: justify;">
  Le but d&#8217;un multi-sites est d&#8217;avoir un seul répertoire contenant le code de base, et plusieurs répertoires de petite taille comportant les éléments particuliers à chaque sites. Ce procédé est intéressant si vous construisez souvent vos sites à partir d&#8217;un même système de modules (exemple la même galerie, le même composant de forum, etc.). Les avantages concernent la mise à jour qui devient centralisée et plus rapide par conséquent.
</p>

<h2 style="text-align: justify;">
  Le principe
</h2>

<p style="text-align: justify;">
  Imaginons que votre répertoire de base est <em>/www</em>. Tout d&#8217;abord, il est nécessaire de créer un répertoire /<em>www/drupal</em> qui contiendra les fichiers d&#8217;installation de base (dézipper le contenu du fichier téléchargés sur le site de Drupal).
</p>

<p style="text-align: justify;">
  Imaginons que vous ayez à créer deux sites web : <em>site1.com</em> et <em>site2.com</em>. Avant de continuer la configuration, ilfaut rediriger vos noms de domaine vers deux dossiers spécifiques à ces sites. Par exemple, <em>/www/site1</em> et <em>/www/site2</em> Ensuite, pour chacun d&#8217;eux, il est besoin de créer un lien symbolique vers le répertoire drupal de base. Ainsi, nous allons d&#8217;abord supprimer les dossiers crées plus haut, puis les envoyer symboliquement vers notre répertoire de base.
</p>

<pre style="text-align: justify;">rmdir /www/site1</pre>

<pre style="text-align: justify;">ln -s /www/drupal /www/site1</pre>

<p style="text-align: justify;">
  A présent, il faut créer un répertoire dédié à chaque site dans votre installation de drupal. Le moteur de Drupal est assez fort techniquement, et se base sur le nom de votre dossier pour comprendre quel URL appelle quel dossier. Créez donc les dossiers <em>/www/drupal/sites/site1.com</em> et <em>/www/drupal/sites/site2.com</em>. Copiez, dans chacun de ces répertoires le fichier <em>/www/drupal/sites/all/settings.php</em>, et renseignez-y les informations concernant votre base de données.
</p>

<p style="text-align: justify;">
  La lecture du fichier settings.php vous apprendra qu&#8217;il est possible de partager des informations entre les différents sites. Vous pouvez par exemple avoir la même base concernant les users, ce qui permettra à vos utilisateurs de ne s&#8217;inscire qu&#8217;à un seul de vos sites!
</p>

<p style="text-align: justify;">
  Après cela, il faut simplement se connecter à votre site1.com, et le script d&#8217;installation se chargera du reste de l&#8217;installation.
</p>

<h2 style="text-align: justify;">
  La suite
</h2>

<p style="text-align: justify;">
  A présent, voilà comment fonctionne Drupal. Les thèmes et modules à gérer en commun sont à placer dans <em>/www/drupal/sites/all</em> , et les thèmes ou modules dédiés sont à placer dans <em>/www/drupal/sites/site1.com</em> (pour le <em>site1.com</em> par exemple).
</p>

<p style="text-align: justify;">
  Afin de bien démarrer sous Drupal, je vous propose de lire l&#8217;article suivant, qui vous donne 11 steps indispensable après une installation de Drupal : <a title="11 m ost important things after a drupal installation" href="http://timonweb.com/the-11-most-important-things-to-do-after-you-install-drupal" target="_blank">http://timonweb.com/the-11-most-important-things-to-do-after-you-install-drupal</a> . Il recense juste des modules assez indispensables. A vous de les placer dans <em>/www/drupal/sites/all</em>, mais de ne les activer sur vos sites que lorsque vous en sentez l&#8217;utilité. C&#8217;est en anglais, mais vous pouvez le traduire avec google translate si vous n&#8217;êtes pas anglophone.
</p>