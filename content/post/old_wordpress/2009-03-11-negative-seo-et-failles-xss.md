---
title: Negative SEO (et failles XSS)
author: Jice

date: 2009-03-11
url: /2009/03/negative-seo-et-failles-xss/
aktt_notify_twitter:
  - no
categories:
  - Informatique
tags:
  - SEO
---
<p style="text-align: justify;">
  <img class="alignleft size-full wp-image-119" style="margin: 5px;" title="Spammeur SEO" src="/images/posts/oldwordpress/uploads/2009/02/seo_black_hat.jpg" alt="Spammeur SEO" width="140" height="112" >Ca buzz beaucoup en ce moment sur les sites SEO français autour de la boite de Pandore nommée &#8220;Negative seo&#8221;. En français on pourrait simplement dire &#8220;déréférencement&#8221;. Il s&#8217;agit d&#8217;employer des méthodes qui sont toujours (car ce n&#8217;est pas bien) hors la loi pour déclasser un concurrent sur ses requêtes Google.
</p>

Dans ce post je vous propose une méthode à tester (ceux qui ont du temps peuvent le faire, et leur commentaires seront les bienvenues) concernant ce fameux negative seo.<!--more-->

## Les différentes techniques connues

<p style="text-align: justify;">
  Rappelons ce qui peut nuire à un référencement :
</p>

> Find out if a site buys links and then report them.
   
> File a complaint with G/Y!/MSN saying a site is stealing copyrighted material. Name the page and the engine has to remove the page for 10 days. 
   
> Send a ton of spam links with questionable anchor (buy viagra, etc) to your competitors site.
   
> Black social bookmarking.
   
> Hijack the content of your competitors site and publish it as your own on a shady site (which you would presumably buy/already own).
   
> Create a blog about how shady/shitty the site is, promote the hell out of it, outrank them for their main keyword phrase. 
   
> 301 a bad site (porn, gambling etc) to your competitors site. 
   
> Pose as a disgruntled employee and talk shit.
> 
> (source : <a title="Google bowling" href="http://www.blackhatworld.com/blackhat-seo/black-hat-seo/57800-google-bowling-2009-a.html#post558546" target="_blank">http://www.blackhatworld.com/blackhat-seo</a>)

<p style="text-align: justify;">
  Pour les non français, je vous recommande les site d&#8217;OSEOX, Pagasa, Discodog et Dievotchka qui en ont récemment parlé. Si j&#8217;ai l&#8217;envie ou des commentaires qui me le demande je compléterai ce post plus tard.
</p>

<br class="spacer_" />

## Les failles XSS :

<p style="text-align: justify;">
  La plupart des référenceurs plus ou moins Black Hat connaissent les failles XSS. Celles-ci permettent d&#8217;injecter du code malicieux dans un script cgi mal corrigé par exemple. Le site refpowa n&#8217;en a pas bénéficier, à part pour ce court exemple (une <a title="Une page sérieuse qui parle de refpowa... étrange" rel="nofollow" href="http://www.crisco.unicaen.fr/cgi-bin/trouvebis2?requete=Perdre%20du%20poids,%20gagner%20du%20%3Ca+href%3D%22http%3A%2F%2Fwww.le-refpowa.fr%22%3ERefpowa%3C%2Fa%3E%3C%2Fp%3E&refer=%23&proc=1739_30610b" target="_blank">démo de XSS sur le refpowa</a> : corrigé après alerte au webmaster concerné). Pour en savoir plus, je vous conseille l&#8217;article de <a title="Black Hat et Failles XSS pour le spam" href="http://www.seoblackout.com/2007/07/22/obtenir-liens-sites-edu-gov/" target="_blank">SBH sur les failles XSS</a>.
</p>

<p style="text-align: justify;">
  Une autre page sur le <a title="Search for refpowa" href="http://feedmelinks.com/search?q=&quot;</td></tr></table><h1>Perdez du poids, gagner du <a href=http://www.le-refpowa.fr>Refpowa<%2Fa></h1><table><tr><td>&x=0&y=0&search_only=links" target="_blank">refpowa</a> (n&#8217;oubliez pas de toujours bien sécuriser les scripts que vous mettez en ligne).
</p>

<br class="spacer_" />

## L&#8217;idée : utiliser les failles XSS pour la negtive seo :

<p style="text-align: justify;">
  Plus c&#8217;est crade plus ça passe. Alors pourquoi, au lien de mettre un pauvre lien vers votre site web, ne pas mettre des tonnes de liens avec des ancres porno/viagra/poker, vers le site de votre concurrent? Pourquoi ne pas injecter des redirections JS (plus c&#8217;est crade plus ça marche) vers le site de votre concurrent? Bref, tout ce que vous trouvez en techniques que vous ne pratiquiez qu&#8217;au début avant de voir que ça ne vous permettait que d&#8217;obtenir des pénalités est utilisable.
</p>

<p style="text-align: justify;">
  Une fois que vous avec collecté une bonne liste de sales failles et liens associés, ne la laissez pas sur un serveur à vous, au risque de vous faire reconnaitre. Utilisez des <a title="Refpowa" href="http://jump.to/www.le-refpowa.fr" target="_blank">jump.to</a>, des <a title="Refpowa" href="http://miniurl.org/1Ok" target="_blank">miniurl</a> et autres choses pour les cacher et faites les manger à google par une technique à venir (si vous avez des propoosition pour faire manger google d&#8217;un fichier de liens sales, sans vous impliquer, je suis preneur).
</p>

<br class="spacer_" />