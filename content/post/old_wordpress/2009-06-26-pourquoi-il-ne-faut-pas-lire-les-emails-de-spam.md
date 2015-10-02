---
title: Pourquoi il ne faut pas lire les emails de spam
author: Jice

date: 2009-06-26
url: /2009/06/pourquoi-il-ne-faut-pas-lire-les-emails-de-spam/
Image:
  - images/posts/oldwordpress/uploads/2009/02/seo_black_hat.jpg
categories:
  - Informatique
tags:
  - Black hat
  - Email
  - Spam
---
<p style="text-align: justify;">
  <img class="alignleft size-full wp-image-119" style="margin: 5px;" title="Black Hat" src="/images/posts/oldwordpress/uploads/2009/02/seo_black_hat.jpg" alt="Spammeur SEO" width="140" height="112" >Sur ce blog j&#8217;ai beaucoup parlé de spam seo. Cela consiste uniquement à s&#8217;approprier les techniques permettant de mieux se positionner sur google. Une autre signification au mot spam est plus souvent utilisée : celle du spam par email. Dans cet article je vous explique pourquoi, selon moi, il ne faut pas lire les messages de spam, ou en tout cas activer le code html inclus dedans.<!--more-->
</p>

<h2 style="text-align: justify;">
  Le but des spammers
</h2>

<p style="text-align: justify;">
  Les spammers par email achètent, ou se procurent ( grâce à des sites à eux, ou en piratant d&#8217;autre sites, ou en lancant des robots collecteur d&#8217;emails) des listes d&#8217;email énormes (100 000 adresse c&#8217;est une petite liste). Vous pouvez voir des annonces passer sur certains forums anglophones (voir le post &#8216;<a title="Je suis un spammer - Liens utiles" href="http://localhost/oldblog/2009/02/je-suis-un-spammeur/">Je suis un spammer</a>&#8216; où j&#8217;en cite sûrement).
</p>

<p style="text-align: justify;">
  Ces listes sont, pour les plus simples, seulement composées d&#8217;email. Mais il m&#8217;est arrivé d&#8217;en voir passer avec les coordonnées complètes de toutes les cibles. Ca fait froid dans le dos!
</p>

<p style="text-align: justify;">
  Un spammeur par email va faire de la pub pour du viagra, du porn ou du poker. On appelle ca  <strong>Les 3 P du net</strong> : Porn, Poker, Pillules. Il ne va en règle général pas collecter de visite&#8230; mais il arrive que, une fois sur un million, il effectue une conversion ( si quelqu&#8217;un me retrouve les chiffres, je suis preneur, je pense que l&#8217;an dernier c&#8217;était 1/1 000 000 le taux de conversion d&#8217;un spam).
</p>

<p style="text-align: justify;">
  Ce taux est ridicule, mais il suffit à ces gens là pour faire recette.
</p>

<p style="text-align: justify;">
  <h2 style="text-align: justify;">
    Les recommandations
  </h2>
  
  <p style="text-align: justify;">
    Je pense que si vous êtes sur mon blog vous devez savoir comment utiliser un minimum le net. Vous devez savoir en premier lieux qu&#8217;il ne faut <strong>JAMAIS laisser son adresse apparaître en clair sur le web</strong>.
  </p>
  
  <p style="text-align: justify;">
    Un autre conseil peut être souvent de se créer une adresse <em>poubelle </em>sur laquelle vous inscrirez vos compte internet de sites un peu douteux. En effet, allez vous inscrire sur un site spammy russe, vous pouvez être sur que votre adresse sera revendue rapidement.
  </p>
  
  <p style="text-align: justify;">
    Il faut aussi savoir que les spammers n&#8217;utilisent pas de vrais comptes et qu &#8216;il ne sert à rien de leur envoyer des emails de menace pour leur demander gentillement d&#8217;arrêter. En général le mail est envoyé d&#8217;une adresse qui n&#8217;existe pas, à partir d&#8217;un serveur piraté qui n&#8217;est pas à eux. Ils le récupèrent en profitant de failles web, et y installent des scripts d&#8217;automatisation. Le reste du temps, ce sont des utilisateurs lambda, comme vous et moi, qui possèdent des virii sur leur pc, et qui envoient ces spams sans le savoir.
  </p>
  
  <h2 style="text-align: justify;">
    Qu&#8217;est-ce qui rend une liste d&#8217;emails intéressante ?
  </h2>
  
  <p style="text-align: justify;">
    Le fait que ses adresses email soient correctes. Il est donc primordial de ne pas faire savoir au spammer qu&#8217;il a atteint votre adresse email. Sinon il peut se constituer une liste d&#8217;adresses valides qu&#8217;il revendra encore à d&#8217;autres spammeurs, et votre calvaire n&#8217;est pas fini.
  </p>
  
  <p style="text-align: justify;">
    La plus évidente arnaque de certains spam est la suivante : ils vous avertissent que leur message n&#8217;est pas un spam, et v<strong>ous propose de vous désabonner</strong>. Sur la page en question, ils demandent que vous rentriez l&#8217;email sur lequel vous avez reçu le spam.
  </p>
  
  <p style="text-align: justify;">
    &#8230; Vous avez compris ce qu&#8217;il se passe après? Évidemment, <strong>ils ne vous désinscrivent pas</strong>, mais <strong>rajoutent votre adresse à leur liste d&#8217;emails valides</strong>. Vous venez de vous faire avoir.
  </p>
  
  <p style="text-align: justify;">
    L&#8217;autre technique fait l&#8217;objet de ce post est exposée ci-dessous.
  </p>
  
  <h2 style="text-align: justify;">
    Les images des mails de spam
  </h2>
  
  <p style="text-align: justify;">
    Vous avez sûrement reçu des emails contenant l&#8217;affichage d&#8217;une ou plusieurs images, censée égayer l&#8217;email. Je ne parle pas des <a title="Spam images" href="http://www.securiteinfo.com/attaques/divers/analyse_image_spam.shtml" target="_blank">spams  images</a> qui ne sont composés que d&#8217;une photo d&#8217;une pillule viagra et d&#8217;une adresse web, et qui sont un nouveau type de spam e****ant. Je parle des spams dont l&#8217;image est bloquée par votre lecteur de mail en général. Je vous montre ci-dessous pourquoi il ne faut pas les afficher (bien qu&#8217;en règle général ce ne soit pas la raison du blocage des images dans un email).
  </p>
  
  <p style="text-align: justify;">
    De manière classique on peut utiliser GD pour dessiner une image en php. Le spammeur peut alors inclure dans son email html l&#8217;appel vers une page qui va, en plus de vous afficher l&#8217;image&#8230; s&#8217;assurer que votre adresse email est bien fonctionnelle. Donc, à partir du moment où vous afficher une image dans un spam, vous pouvez être sur de recevoir des spams toute votre vie sur cette adresse.
  </p>
  
  <p style="text-align: justify;">
    Vous avez peut être lu mon article sur le <a title="Click frauding et cookie stuffing" href="http://localhost/oldblog/2009/06/cookie-stuffing-and-click-hidding/">click frauding et le cookie stuffing</a>. Celui-ci s&#8217;appuyait sur une utilisation de .htaccess pour que le serveur utilise le fichier image.gif comme un fichier php.
  </p>
  
  <p>
    <code>RewriteEngine On&lt;br />
RewriteBase /&lt;br />
RewriteRule fake_pixel.gif pixel.php [L]</code>
  </p>
  
  <p style="text-align: justify;">
    Il est bien sur amplement possible de rendre ce script dynamique, et avec un peu d&#8217;url rewriting, de créer un code unique pour chaque email envoyé, afin de l&#8217;associer à un nom d&#8217;image unique (idem que la technique GD ci-dessus).
  </p>
  
  <p style="text-align: justify;">
    En plus d&#8217;avoir votre email, il peut y associer des <a title="Informations a partir de votre ip" href="http://www.mon-ip.com/" target="_blank">informations supplémentaires</a>, comme votre zone géographique, afin de mieux vous cibler la prochaine fois.
  </p>
  
  <h3 style="text-align: justify;">
    Autres techniques
  </h3>
  
  <p style="text-align: justify;">
    En y incluant un CSS externe (même trick que l&#8217;image) ou bien appelant une image en background, qui va être comme ci-dessus. Cette technique marche sur <a title="CSS et logiciels de messagerie" href="http://www.campaignmonitor.com/css/" target="_blank">certains logiciels de messagerie</a> (notament les <a title="CSS et webmail" href="http://www.xavierfrenette.com/articles/css-support-in-webmail/" target="_blank">messageries online</a> comme gmail, yahoo ou hotmail).
  </p>
  
  <p style="text-align: justify;">
    Voilà, je n&#8217;ai pas cherché à écrire de code pour cette application, ni à le tester sous différentes messageries, je n&#8217;en ferai sans doute pas usage avant longtemps. Ce billet avait juste pour but de vous mettre en garde contre certaines de ces pratiques.
  </p>