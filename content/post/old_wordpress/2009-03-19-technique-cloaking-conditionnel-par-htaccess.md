---
title: '[Technique] Cloaking conditionnel par htaccess'
author: Jice

date: 2009-03-19
url: /2009/03/technique-cloaking-conditionnel-par-htaccess/
aktt_notify_twitter:
  - no
Image: images/posts/oldwordpress/uploads/2009/02/seo_white_hat.jpg
categories:
  - Informatique
tags:
  - SEO
---
<p style="text-align: justify;">
  Le cloaking&#8230; qu&#8217;est-ce donc? Il s&#8217;agit d&#8217;une technique plutôt mal vu des moteurs de rechreche, qui permet de sélectionner les informations à afficher en fonction du visiteur. Si le visiteur est un robot, on lui affiche une page dédiée (avec de jolis mots clés, ou une redirection qui va bien). Le cloaking sert à afficher un faux PR (technique mise au point par : <a title="Dark Seo Team" href="http://www.robots.darkseoteam.com/" target="_blank">http://www.robots.darkseoteam.com</a> remarque : leur page est ancienne, et la page n&#8217;est plus en PR10).
</p>

<p style="text-align: justify;">
  Pourquoi faire du cloaking? De nombreuses raisons sont possible, les plus évidentes sont liées au SEO. Néanmoins, je vous rappelle que cela vous blacklistera des grands moteurs de recherche lorsque cela sera découvert (si votre page est mise en cache, n&#8217;importe quel inernaute pourra voir la différence et vous <a title="Reporter un site spammy" href="http://www.google.fr/webmasters/spamreport.html" target="_blank">accuser de spam,</a> ou bien vous pourrez recevoir le visite d&#8217;un googleman qui effectuera tout seul le blacklistage).
</p>

<!--more-->

<h2 style="text-align: justify;">
  Utilisation du .htaccess :
</h2>

<p style="text-align: justify;">
  Pour effectuer un cloaking plus clean que du php, on va utiliser .htaccess. Dans le cas où vous désirez un cloaking plus élaboré est moins visible (seuls quelques parties de votre site changent, je vous conseille le précédent article sur les <a title="Pages parking" href="http://localhost/oldblog/2009/02/les-pages-parking/">pages parking</a>, afin que vous adaptiez le contenu à vos envies.
</p>

<p style="text-align: justify;">
  Notre htaccess va recevoir une instruction de redirection vers le site cible.com et testera seulement le nom du robot qui doit contenir &#8216;<em>google</em>&#8216; ; ceci afin de prendre en compte les robots feedfetcher, googlebot et google adsense. Pour en savoir plus sur apache-mod-rewrite, je vous conseille mon autre site pour débuter sur l&#8217;<a title="Débuter url rewriting avec apache mod-rewrite" href="http://www.apache-mod-rewrite.fr" target="_blank">url rewriting avec apache mod rewrite</a>.
</p>

<pre>[cc lang="htaccess]##Google Bot
RewriteCond %{HTTP_USER_AGENT} ^Google [NC]
RewriteRule ^(.*)$ /nouvellepage/$1 [L]
 [/cc]</pre>

## Vérifier le cloaking sur votre page :

<p style="text-align: justify;">
  Si le cloaking a été effectué en se basant sur des listes d&#8217;Ip, il va être difficile de le vérifier si vous n&#8217;avez pas l&#8217;ip en question. Par contre, dans notre cas, comme il se base uniquement sur le nom envoyé par le robot, il est possible de voir le résultat en envoyant de faux headers à votre site cible. Pour cela, vous pouvez utiliser le service : <a href="http://www.smart-it-consulting.com/internet/google/googlebot-spoofer/" target="_blank">http://www.smart-it-consulting.com/internet/google/googlebot-spoofer/</a>. Il y en a des mieux, mais je nn&#8217;ai pas eu le temps de les retrouver. Si vous en avez, envoyez un commentaire.
</p>

<p style="text-align: justify;">
  Vous trouverez dans les liens ci-dessous plus d&#8217;informations pour compléter cet article, et d&#8217;autres outils.
</p>

<br class="spacer_" />

## Liens associés :

Liste de robots : <a href="http://www.botsvsbrowsers.com" target="_blank">http://www.botsvsbrowsers.com</a>

Le cloaking expliqué pour les nuls : <a href="http://www.actulab.com/cloaking.php" target="_blank">http://www.actulab.com/cloaking.php</a>

Forum sur le cloaking : <a href="http://www.webmasterworld.com/forum24/" target="_blank">http://www.webmasterworld.com/forum24/</a>

Se déguiser en robot : <a href="http://www.ericgiguere.com/articles/masquerading-your-browser.html" target="_blank">http://www.ericgiguere.com/articles/masquerading-your-browser.html</a>

Une autre appli pour le cloaking : <a href="http://www.theblackmelvyn.com/2009/01/applications-cloaking-referer-ip-delivery/" target="_blank">http://www.theblackmelvyn.com/2009/01/applications-cloaking-referer-ip-delivery/</a>
