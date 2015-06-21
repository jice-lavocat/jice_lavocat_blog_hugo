---
title: Installer WordPress sur Webfaction
author: Jice
date: 2014-03-26
url: /2014/03/installer-wordpress-sur-webfaction/
categories:
  - Informatique
tags:
  - hébergeur
  - webfaction
  - wordpress
---
{{< img src="images/posts/oldwordpress/uploads/2014/03/dashboard_webfaction.png" >}}
J&#8217;ai récemment découvert l&#8217;<a title="Webfaction - Hébergeur web" href="https://www.webfaction.com/" target="_blank">hébergeur web Webfaction</a> chez qui je suis en train de déplacer mes sites petit à petit. Je vais sans doute proposer une suite de tutoriels pour vous expliquer en français comment installer tel ou tel CMS sur la plateforme. Il faut savoir que Webfaction est un hébergeur dont le support technique est le plus rapide que je connaisse, mais qu&#8217;il souffre pour le moment d&#8217;une lacune de taille pour le marché français : **la doc et le support est en anglais**. Par contre, j&#8217;ai pu discuter avec le dirigeant de la société, et il se pourrait que cela change si la clientèle française dépasse une certaine taille critique. Avis aux intéressés {{<img src="images/smilies/icon_wink.gif" alt=";-)" class="wp-smiley" >}}

Webfaction, en gros, c&#8217;est _comme un hébergeur mutualisé_ (où on ne doit pas se concentrer sur la sécurité et l&#8217;installation de toutes les dépendances du serveur) mais avec **plein d&#8217;options pour configurer automatiquement le serveur**. Par exemple, sur un mutu, impossible d&#8217;installer des stacks complexes comme ruby on rails ou node, alors que sur webfaction cela est possible et il n&#8217;y a pas besoin de passer 3 heures à trouver comment installer toutes les dépendances.

## Utilisation du dashboard

Le panneau d&#8217;administration de Webfaction est fait maison, il faut donc s&#8217;habituer à la façon dont les informations sont présentées (c&#8217;est pas long, mais voilà quoi) :



{{<img class="aligncenter size-full wp-image-1427" alt="Dashboard Webfaction" src="images/posts/oldwordpress/uploads/2014/03/dashboard_webfaction.png" width="600" height="473" >}}

Dans la pratique (pas très grosse pour moi pour le moment), je trouve qu&#8217;on perd un peu de temps entre les différents menus dans certains cas. Par exemple, dans domain/application/website, toutes les informations pourraient se trouver sur la même page avec un système d&#8217;onglets. Bref, cela étant dit l&#8217;ensemble reste quand même **assez clair** et la **prise en main est assez rapide**.

## Création d&#8217;un compte ssh :

Avant toute chose, allez vous créer un utilisateur qui a accès au ssh, ça sera beaucoup plus pratique dans le futur. Rendez-vous sur la page d&#8217;<a title="Création utilisateur ssh - webfaction" href="https://my.webfaction.com/new-user" target="_blank">ajout d&#8217;utilisateur</a> et remplissez le formulaire (j&#8217;ai pris _/bin/bash_ comme **shell** mais ça n&#8217;a pas de grosses implications). Vous verrez, même le choix du password est &#8220;controlé&#8221; et le système vous empêchera de créer un compte avec password &#8220;faible&#8221;.

{{<img class="aligncenter size-medium wp-image-1428" alt="Add SSH user" src="images/posts/oldwordpress/uploads/2014/03/add_user_ssh-300x154.png" width="300" height="154" >}}

Une fois ce compte créer, vous pouvez vous connecter à votre serveur depuis chez vous en utilisant aussi bien des outils de ftp (comme winscp) ou ssh (comme putty) pour voir ce qui se passe dessus (j&#8217;ai un vieil article sur <a title="Les outils pour administrer un serveur à distance - SFTP et SSH - Adminoob" href="http://www.adminoob.com/2008/08/18/les-outils-windows-indispensables-a-ladministration-serveur-a-distance/" target="_blank">les outils pour administrer un serveur à distance</a> si vous débutez).

## Créer votre site WordPress sur Webfaction

Maintenant voici les étapes principales pour créer votre blog wordpress sur Webfaction.

### Créer un &#8220;nouveau site web&#8221;

Rendez-vous dans la section _domains/websites_ et cliquez sur _Websites_ puis <a title="Ajouter un site webfaction" href="https://my.webfaction.com/new-website" target="_blank">Add a new website</a>. Cette section va vous permettre de configurer (côté serveur) quelle application sera gérée par votre sous-domaine.

Voilà  à quoi ressemblera votre &#8220;site web&#8221; après sa création :

{{<img class="aligncenter size-full wp-image-1431" alt="Ajouter un site web sur Webfaction (panneau principal)" src="images/posts/oldwordpress/uploads/2014/03/add_website.png" width="600" height="388" >}}

Pour cela, donnez d&#8217;abord un nom &#8220;name&#8221; à votre site web pour vous en rappeler facilement. Ensuite, il faut préciser quel domaine(s) et/ou sous-domaine(s) vont accéder à cette application. Pour cet exemple j&#8217;en ai mis un seul :

{{<img class="aligncenter" alt="Ajouter un domaine (webfaction)" src="images/posts/oldwordpress/uploads/2014/03/create_comain.png" width="600" height="81" >}}

Enfin, il faut dire au serveur quel application (WordPress) nous allons héberger sur ce nom de domaine. Pour cela on crée une nouvelle application, et on choisira WordPress dans la liste proposée.

<p style="text-align: center;">
  <a href="images/posts/oldwordpress/uploads/2014/03/create_application.png">{{<img class="aligncenter  wp-image-1432" alt="Ajouter une application (webfaction)" src="images/posts/oldwordpress/uploads/2014/03/create_application.png" width="600" /></a>  <img class="aligncenter  wp-image-1434" alt="Détail création d'une application" src="images/posts/oldwordpress/uploads/2014/03/new_application.png" width="600" >}}
</p>

<h3 style="text-align: left;">
  Faire pointer ses DNS vers Webfaction
</h3>

<p style="text-align: left;">
  Après avoir sauvé cette configuration, il suffit d&#8217;aller chez votre registar et faire pointer vos domaine vers votre serveur webfaction.L&#8217;adresse IP du server est résumée dans votre liste d&#8217;application :
</p>

<p style="text-align: left;">
  <a href="images/posts/oldwordpress/uploads/2014/03/dns_server.png">{{<img class="aligncenter size-full wp-image-1435" alt="Adresse Ip de votre application sur webfaction" src="images/posts/oldwordpress/uploads/2014/03/dns_server.png" width="600" height="40" >}}</a>
</p>

<p style="text-align: left;">
  Ci-dessus on voit que l&#8217;adresse ip de mon nouveau serveur est <em>37.58.75.242</em>. Je vais devoir aller pointer mon sous-domaine <em>wordpress.lavocat.name</em> vers cette adresse IP. Vous allez créer un nouveau champ A qui pointera vers l&#8217;adresse IP de votre serveur webfaction. Dans cet exemple, j&#8217;utilise dreamhost comme registar (mais la manipulation se trouve expliquée facilement sur le web pour tous les registar) :
</p>

<p style="text-align: left;">
  {{<img class="aligncenter size-full wp-image-1436" alt="Configuration dns dreamhost" src="images/posts/oldwordpress/uploads/2014/03/dns_dreamhost.png" width="600" height="235" >}}
</p>

<p style="text-align: left;">
  Et comme beaucoup d&#8217;entre vous sont aussi chez OVH, je mets ci-dessous à quoi ça ressemble :
</p>

<p style="text-align: left;">
  <a href="images/posts/oldwordpress/uploads/2014/03/dns_ovh.png">{{<img class="aligncenter size-full wp-image-1440" alt="Configuration d'un champs DNS A sous OVH" src="images/posts/oldwordpress/uploads/2014/03/dns_ovh.png" width="479" height="262" >}}</a>
</p>

<p style="text-align: left;">
  Voilà, la configuration DNS et serveur est finie. Maintenant, passons à la base de données.
</p>

<h2 style="text-align: left;">
  Connexion à votre nouveau Wordress sur Webfaction
</h2>

Voilà, l&#8217;ensemble des opérations ont été accomplies. Si la propagation de DNS est finie (peut prendre de 5 minutes à lpusieurs heures), vous allez pouvoir accéder à votre nouveau blog à l&#8217;adresse que vous avez uutilisée. Chez moi ça marche donc ici : <a title="Wordpress de test sur webfaction" href="http://wordpress.lavocat.name/" target="_blank">http://wordpress.lavocat.name/</a>

Maintenant, l&#8217;essentiel est de vous y connecter pour le configurer et ajouter du contenu. Pour cela, vous devez retourner dans _Domains / Applications_ puis _Applications_ et cliquer sur le nom du blog que vous venez de créer. Dessus vous avez toutes les informations concernant votre site et la base de données qui a été créée en même temps. Votre login initial est &#8220;admin&#8221; et le mot de passe est affiché dans le tableau dans la section &#8220;extra info&#8221; :

# [{{<img class="aligncenter size-full wp-image-1443" alt="Login de WordPress généré automatiquement" src="images/posts/oldwordpress/uploads/2014/03/login_wordpress.png" width="600" height="339" >}}

## Voir vos fichiers

Pour voir vos fichiers, il faut vous connecter avec votre compte principal de FTP (et non pas celui créer spécialement pour le ssh au début). C&#8217;est une situation un peu bizarre, mais j&#8217;imagine que ça protège un peu plus vos one-click install.

