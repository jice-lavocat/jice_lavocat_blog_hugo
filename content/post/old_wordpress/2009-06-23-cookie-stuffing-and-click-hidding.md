+++
title="Cookie Stuffing and click hiding"
date="2009-06-23"
url= "/2009/06/cookie-stuffing-and-click-hidding/"
image="images/posts/oldwordpress/uploads/2009/06/mange_moi.jpg"
tags=["click frauding", "cookie stuffing","SEO","pixel tracking"]
+++


<p style="text-align: justify;">
  <img title="seo white hat" src="/images/posts/oldwordpress/uploads/2009/02/seo_white_hat.jpg" alt="seo white hat" width="140" height="112" >Comme le suppose le titre de ce post je parle ici de néthodes pas très honnêtes pour cacher ses cookies et utiliser de faux clics pour une utilisation que je vous laisse personnelle ( nous y reviendrons). Dans ce post je présente seulement les méthodes de mise en place du cookie stuffing ou du faux clic. Pour le reste (trouver ou placer les images, comment cacher la fraude etc.) je vous laisse les commentaires.
</p>

<h2 style="text-align: justify;">
  <!--more-->
</h2>

<h2 style="text-align: justify;">
  Le but
</h2>

<h3 style="text-align: justify;">
  Cookie Stuffing :
</h3>

<p style="text-align: justify;">
  Le but de la manipulation est de charger un cookie cible chez un utilisateur qui ne se doute de rien. En temps normal, ce cookie se lance chez votre visiteur lorsqu&#8217;il clique sur une pub affiliée, et qu&#8217;il se rend sur une boutique. Si il passe un achat avec votre cookie sur son pc, vous touchez un certain pourcentage de vente. Malheureusement, ce visiteur peut très bien visiter votre site tous les jours, voir votre pub pour un Mac Air Book Pro, et prendre sa décision d&#8217;achat grâce à vous. Cependant, il peut passer l&#8217;achat sans vous, et ne pas passer par votre bannière pour se rendre sur le site du vendeur.
</p>

<p style="text-align: justify;">
  La solution c&#8217;est le <strong>cookie stuffing</strong> : vous forcez l&#8217;upload d&#8217;un cookie sans un click volontaire. Bien entendu, cela  vous permet de mettre votre cookie &#8216;de force&#8217; sur des sites qui ne sont pas à vous ;-) .
</p>

<p style="text-align: justify;">
  <strong>Le click frauding :</strong>
</p>


  Je ne sais pas trop quel nom on donne généralement à la technique que je vais d&#8217;ecrire qui se base sur le cookie stuffing, mais je pense que <strong>click hidding</strong> ou <strong>click frauding</strong> convient (si quelqu&#8217;un le sais, n&#8217;hésitez pas à commenter). Qu&#8217; est-ce que  nous essayons de faire avec du clic frauding? Et bien tout simplement simuler un click d&#8217; un visiteur sur un lien donné ou une bannère. A quoi ça sert? Je ne pense pas avoir à vous apprendre que le traffic d&#8217;un site n&#8217;a qu&#8217;une seul vocation : apporter plus de visiteurs qui vont encore plus cliquer sur les bannière &#8230; qui vont générer des revenues.



  Une autre utilisation concerne les nouveaux médias de bookmark sociaux. En effet, on a souvent un classement de nos sites dépendant des clics. L&#8217;un des plus utilisés dans le monde francophone est certainement <a title="Wikio - Bookmark sociaux" href="http://www.wikio.fr/" target="_blank">wikio</a>, et cette astuce fonctionne aussi pour lui.


## La technique


### Le contexte

  Les deux méthodes de base qui existent pour cacher des cookies (equivalent aux clics, je parlerai donc de cookie pour mentionner les deux par la suite) sont les suivantes :

<li style="text-align: justify;">
  Utilisation d&#8217;une iframe : on crée une iframe de 1 px qui sera donc invisible au visiteur, et contiendra la page de l&#8217;affilié et sera donc similaire à un clic ou lancera ledit cookie. Cette méthode peut être améliorés en cachant le code votre iframe en l&#8217;<a title="JS obfuscator" href="http://www.daftlogic.com/projects-online-javascript-obfuscator.htm" target="_blank">obfuscant par javascript</a>.
</li>
<li style="text-align: justify;">
  Utilisation d&#8217;une image : on va créer une image dont l&#8217;url externe sera celle du site cible. Cela aura un effet similaire : charger la page et le cookie.
</li>

Dans la suite de ce post je vous donne des précisions sur la deuxième méthode que j&#8217;ai utilisé pour avoir quelque chose comme 2000 clics en 5 ou 6 heures pour un concours bidon.

<img class="aligncenter size-full wp-image-511" title="android" src="/images/posts/oldwordpress/uploads/2009/06/android.png" alt="android" width="600" height="281" >

<br class="spacer_" />

Le but était de faire le plus de clics (réels) sur une URL donnée. Dans mon cas c&#8217;étais androidparty.be/Jice. Cependant, afin de cacher un brin la fraude, pour retirer l&#8217;URL du referer sur lequel nous allons injecter notre code, j&#8217;ai créé une adresse du type miniurl (bit.ly ou autre). Si vous avez des idées pour cacher votre referer, ou utiliser un aléatoire ( un petit script suffit, mais on passe toujours par des referer qui font douter comme les rétrecisseurs d&#8217;url).

### Le code


Le code que j'ai mis en place se base sur deux articles que vous retrouverez en fin de page. Il utilise le module <a title="Apache Mod Rewrite et Url Rewriting" href="http://www.apache-mod-rewrite.fr" target="_blank">apache mod-rewrite</a> pour regarder si le referer est humain ou si il s&#8217;agit d&#8217;un site. Dans le cas d&#8217;un humain il va afficher une image banal. Dans le cas d&#8217;un site, il va regarder si l'ip a déjà été utilisée dans les 12 dernières heures, et si c'est le cas a affiché la-dite image. Sinon, il envoie notre code grâce a la fonction php <a title="Php header" href="http://www.php.net/header" target="_blank">header</a>.



  Tout d&#8217;abord on utilise une image innocente, comme <em>pixel.gif</em>, qui va nous servir d&#8217;image à afficher lorsque l&#8217;on a des doutes sur la provenance de l&#8217;ip (sans referer, ou moteur de recherche etc). Je vous laisse en commentaire préciser quelles sont les ip ou conditions à attribuer à l&#8217;affichage de l&#8217;image.

  Ensuite, il faut définir le comportement à utiliser pour l&#8217;appel d&#8217;une fausse image que l&#8217;on appellera <em>fake_pixel.gif</em>. Cette image n&#8217;existe pas réellement, il s&#8217;agit juste d&#8217;un pointeur vers notre fichier malicieux <em>pixel.php</em>. On crée donc le fichier <em>.htaccess </em>qui va bien :



{{< highlight  bash "style=colorful" >}}
RewriteEngine On
RewriteBase /
RewriteRule fake_pixel.gif pixel.php [L]
{{< /highlight  >}}




Vous allez peut être devoir modifier rewritebase si vous ne lancer pas le script à partir de la racine.

Cela permet l'appel du fichier pixel.php de manière 'invisible'. Vous pouvez donc l'appeler par toute page grâce à la balise classique, et personne ne se doutera qu'elle appelle en réalité un script php :

`<img src="fake_pixel.gif" alt="" >`

Cela vous le placerez dans les pages victimes de votre cookie stuff. Celles-ci peuvent se trouver sur votre site &#8230; ou pas ;-)

Voyons à présent ce que contient le fichier pixel.php :

{{< highlight  php "style=colorful" >}}
<?php
if(!$_SERVER['HTTP_REFERER']){
  header("Content-type: image/gif");
  readfile('pixel.gif');
} else {
  $targ=veriff_add("list_ip.txt"); //ip sont enregistrées et comparées
  if($targ){
    header("Location: http://tinyurl.com/androidparty-Jice");
  } else {
    header("Content-type: image/gif");
    header("Status: 200",true);
    readfile('pixel.gif');
  }
}?>
{{< /highlight >}}


  Voilà donc le code. Si le referer n&#8217;existe pas, on renvoie l&#8217;image directement. Sinon on compare avec notre liste d&#8217;ip et on l&#8217;ajoute si l&#8217;ip n&#8217;a pas déjà été utilisée dans les xx heures. La fonction *veriff_add* vous est personnelle. C&#8217;est elle qui enregistre vos ip, et ajoute une fonction aléatoire pour ne pas envoyer toutes les ips d&#8217;un seul coup sur la cible.


## Améliorations :

<p style="text-align: justify;">
  Avec le script actuel, lors de la première connexion d'une cible, celle-ci distingue effectivement qu'il manque une image. Je voulais essayer de faire de l&#8217;<strong>ajax </strong>pour palier ce problème, mais le manque de temps (et une soutenance de stage en préparation) m&#8217;en a empêché.  Le but est d&#8217;afficher quand même, pour une premiere connexion, une image après avoir chargée la page cible. J&#8217;ai essayé avec la fonction buffer de php, mais sans succès. Si vous avez des idées, je suis preneur.
</p>

<p style="text-align: justify;">
  Ce soucis d&#8217;image absente ne vaut que si vous voulez injecter un lien. Si vous voulez injecter un cookie pré-construit, qui ressemble à celui d&#8217;un affilié quelconque, le header de l&#8217;image peut toujours être envoyé après l&#8217; enregistrement du cookie (voir lien article 2 ci-dessous).
</p>

<p style="text-align: justify;">
  <strong>Où poser votre image cible?</strong> Et bien en premier lieux sur tous vos sites. Comme ca, ils lanceront tous une connexion vers votre affilié ou concours. Plus barbare/bucheron, vous pouvez aller injecter votre image sur certains sites sociaux à forte population. Nénamoins, mon meilleur résultat a eu lieu avec un fameux moteur de petites annonces US &#8230; dans la section rencontre pour adultes 8-)   (on s&#8217;en doutait pas tiens) .
</p>

<p style="text-align: justify;">
  Une autre idée serait de profiter du <a title="Vol de bande passante / hot linking d'images" href="http://www.apache-mod-rewrite.fr/empecher-le-vol-de-bande-passante" target="_blank">hotlinking</a> de certaines de vos images pour pointer vers votre script malicieux. Quelques modifications pourraient même être réalisées pour afficher néanmoins la bonne image aux visiteurs des sites qui vous volent la bande passante. Le schéma serait le suivant :
</p>

  * pour toute demande d&#8217;image provenant de l&#8217;extérieur, on renvoie en URL rewrite vers un fichier redir_img.php
  * Ce fichier prend en argument l&#8217;adresse de l&#8217;image demandée
  * Il utilise une modification du script ci-dessus pour envoyer notre lien, et/ou afficher la bonne image.

Ca demande un peu plus de code, mais c&#8217;est une bonne façon de faire payer son travail ( et ses images) : **piquer les visiteurs des pompeurs** :-D


<h2 style="text-align: justify;">
  Les ressources annexes :
</h2>

<p style="text-align: justify;">
  Article 1 servant de base à ce post : <a title="Cookie Stuffing" href="http://www.esrun.co.uk/blog/cookie-stuffing-revisited/" target="_blank">http://www.esrun.co.uk/blog/cookie-stuffing-revisited</a>
</p>

<p style="text-align: justify;">
  Article 2 servant de base à ce post : <a title="Cookie stuffing par image" href="http://www.siteduzero.com/tutoriel-3-4731-images-cookies-loading.html" target="_blank">http://www.siteduzero.com/tutoriel-3-4731-images-cookies-loading.html</a>
</p>

<p style="text-align: justify;">
  L&#8217;utilisation sur Wikio :  <a title="Fraude clic wikio" href="http://www.deliciouscadaver.com/comment-forcer-vos-visiteurs-a-voter-pour-vous.html" target="_blank">http://www.deliciouscadaver.com/comment-forcer-vos-visiteurs-a-voter-pour-vous.html</a>
</p>
