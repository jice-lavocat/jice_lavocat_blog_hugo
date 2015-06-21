---
title: Corriger le comportement du composant SEF sur Joomla 1.5 (OVH)
author: Jice

date: 2008-08-24
url: /2008/08/corriger-le-comportement-du-composant-sef-sur-joomla-1-5-cas-ovh/
btc_comment_counts:
  - 'a:0:{}'
btc_comment_summary:
  - 'a:0:{}'
categories:
  - Informatique
tags:
  - Htaccess
  - Joomla
  - web
---
Cet article fait suite à un problème rencontré de manière récurrente par les utilisateurs de Joomla 1.5  et hébérgés sur OVH (mais aussi probablement sur d&#8217;autres hébergeurs). Deux problèmes sont traités dans ce billet.

### Problème d&#8217;affichage :

<p align="justify">
  Vous possédez un site hébergé sur un serveur mutualisé avec certaines règles dans Apache qui vous empêche d&#8217;utiliser correctement l&#8217;<strong>URL Rewriting de Joomla 1.5</strong>? Chez moi ce fut le cas. Le texte et le contenu était présent, mais les images de mon template ainsi que mes css n&#8217;étaient pas trouvés (erreur 404) et je me retrouvais avec une mise en page horrible. Pour régler le problème, il faut fixer un petit bug inhérent à Joomla.
</p>

Editez le fichier _/include/application.php_ à la ligne 108 et remplacez :

<pre lang="bash">$document-&gt;setBase(JURI::current());</pre>

par

<pre>$document-&gt;setBase(JURI::base());</pre>

<p align="justify">
  A la suite de cela, il faut aussi vérifier le fichier <em>configuration.php</em>, à la racine de votre site, pour qu&#8217;il contienne  la bonne information sur votre adresse de base. Renseignez la variable $live_site à la ligne 19 avec l&#8217;adresse de base de votre site (pour ma part <a href="http://jice.lavocat.name" target="_blank">http://jice.lavocat.name</a>). Normalement tout redevient dans l&#8217;ordre. Sinon, postez un commentaire.
</p>

<p align="justify">
  <h3>
    Problème de duplicate content et d&#8217;urls non maitrisées:
  </h3>
  
  <p align="justify">
    Un autre problème peut survenir si vous êtes hébergés par exemple sur un serveur mutualisé OVH. Comme Joomla ne sais pas sur quelle version de php il tourne, il rajoute dans la première page appelé de votre site, des bouts d&#8217;URL très moches. Par exemple, mon site possédait des URL rewrités sous la forme : mapage?d6002d3c23a7b32546bd03e1985537da=584db87785da0f3151aff0a3b3a&#8230;
  </p>
  
  <p align="justify">
    Le gros problème vient du fait que google va donc indexer cette URL. Un plus gros problème encore, est que ces URL sont différentes à chaque accès. En utilisant <a href="http://www.crawltrack.fr/" target="_blank">Crawltrack</a> je me suis rendu compte que <a href="http://www.google.com/support/webmasters/bin/answer.py?answer=70897&cbid=-8z25jad68u5g&src=cb&lev=topic" target="_blank">googlebot</a> accédait à ma page plus de 25 000 dans la même journée. Outre une saturation de mon serveur, cela induit forcément du <a href="http://www.google.com/support/webmasters/bin/answer.py?hl=en&answer=66359" target="_blank">duplicate content</a> de mon site web. Ainsi, il serait désindexé très rapidement.
  </p>
  
  <p align="justify">
    La solution? Essayer de régler ce problème. Suite à une longue recherche infructueuse, je vous livre la solution trouvée au hasard sur un forum de Joomla. Il faut que vous rajoutiez une petite ligne à votre .htaccess à la base de votre site web.
  </p>
  
  <pre>SetEnv PHP_VER 5</pre>
  
  <p>
    Normalement le problème est réglé. Vérifier que vos URL sont jolies sur ce site web : <a href="http://www.rankquest.com/tools/Link-Explorer.php" target="_blank">RankQuest</a>
  </p>