---
title: Référencement google
author: Jice

date: 2008-07-23
url: /2008/07/referencement-google/
btc_comment_counts:
  - 'a:0:{}'
btc_comment_summary:
  - 'a:0:{}'
categories:
  - Informatique
tags:
  - proxy
  - SEO
  - web
---
&#8212; Article brouillon&#8212;

Seul intérêt = présentation des proxys

Les vrais articles seront publiés dès la mi-aout. En attendant, voilà un lien vers une pages qui recence de nombreux outils du web pour le référencement. Assez indispensables :

 <a href="http://www.7-dragons.com/archives/google-outils.php" target="_blank">http://www.7-dragons.com/archives/google-outils.php</a>

Quelques bons articles ici : <a href="http://www.actulab.com/identification-des-robots.php" target="_blank">http://www.actulab.com/identification-des-robots.php</a>

Il est aussi possible d&#8217;utiliser des proxys pour se donner des BL pointants d&#8217;adresses avec IP différentes. Néanmoins cette technique ne marche pas très bien car les proxys ne conservent pas en cache les liens dynamiques qu&#8217;ils génèrent. Vous pouvez toutefois essayer avec les exemples suivant :

<a rel="nofollow" href="http://www.phproxy.fr/index.php?q=aHR0cDovL3BlcnNvLmVjLW1hcnNlaWxsZS5mci9%2BamNnb21lei1sYXZvL3BhZ2VfcHJveHkucGhw&hl=ed" target="_blank">Exemple 1</a>

<a rel="nofollow" href="http://www.zelune.fr/?__new_url=aHR0cDovL2pjZ29tZXotbGF2by5wZXJzby5lYy1tYXJzZWlsbGUuZnIvcGFnZV9wcm94eS5waHA=#" target="_blank">Exemple 2</a>

<a rel="nofollow" href="http://www.webproxy.ws/index.php?q=aHR0cDovL2pjZ29tZXotbGF2by5wZXJzby5lYy1tYXJzZWlsbGUuZnIvcGFnZV9wcm94eS5waHA%3D&hl=ed">Exemple 3</a>

Le principe est le suivant. Je demande à ses proxys de m&#8217;envoyer le classement des [meilleurs ingénieurs généralistes][1] de france, et ils empruntent cette adresse avec leur adresse ip. Ils établissent donc un lien en dur entre leur ip et ma page placée sur le concours du GInfo (voir rubrique &#8220;l&#8217;auteur&#8221; ci-dessus).

Encore quelques exemples et après j&#8217;arrête : <a rel="nofollow" href="http://www.zend2.com/browse.php?u=aHR0cDovL2pjZ29tZXotbGF2by5wZXJzby5lYy1tYXJzZWlsbGUuZnIvcGFnZV9wcm94eS5waHA%3D&b=31#" target="_blank">exemple 4</a> ..<a href="http://www.proxy4myspace.org/index.php?q=aHR0cDovL2pjZ29tZXotbGF2by5wZXJzby5lYy1tYXJzZWlsbGUuZnIvcGFnZV9wcm94eS5waHA%3D&hl=2e9" target="_blank">exemple5</a>.

Et une bonne liste de proxys ici : <a href="http://www.prospector.cz/Free-Internet-services/Web-proxy/" target="_blank">http://www.prospector.cz/Free-Internet-services/Web-proxy/</a>

Après il existe d&#8217;autres système, comme les générateurs d&#8217;URL courte : <a href="http://bit.ly/info.php?id=1aJ9wl" target="_blank">http://bit.ly/info.php?id=1aJ9wl</a>

### Détournement de proxys :

On peut se débrouiller pour trouver exactement ce que l&#8217;on veut. Beaucoup de proxys convertissent leur adresse en base 64. On peut utiliser un <a href="http://www.paulschou.com/tools/xlate/" target="_blank">convertisseur 64</a> pour voir ce que donne l&#8217;adresse : http://jcgomez-lavo.ec-marseille.fr/redirect.php . J&#8217;ai placé sur cette page une redirection 301 (car sinon ça pointait pas comme je le voulais vers la page de [présentation d&#8217;une ingénieur généraliste][2]).

Ca nous donne la suite : aHR0cDovL2pjZ29tZXotbGF2by5wZXJzby5lYy1tYXJzZWlsbGUuZnIvcmVkaXJlY3Q

On peut ensuite vérifier que certains proxys acceptent ce genre d&#8217;adresse : <a href="http://en.netlog.com/go/out/url=-aHR0cDovL2pjZ29tZXotbGF2by5wZXJzby5lYy1tYXJzZWlsbGUuZnIvcmVkaXJlY3Q" target="_blank">Netlog</a> (et hop un nouveau lien en dur).

<a href="http://www.carpfishinguk.co.uk/fisheries.htm?redirect:aHR0cDovL2pjZ29tZXotbGF2by5wZXJzby5lYy1tYXJzZWlsbGUuZnIvcmVkaXJlY3Q" target="_blank">Exemple 12</a>

<a href="http://www.tarad.com/_tarad/_templates/b/_modules/gotolink.php?aHR0cDovL2pjZ29tZXotbGF2by5wZXJzby5lYy1tYXJzZWlsbGUuZnIvcmVkaXJlY3Q" target="_blank">Exemple 15</a>

 [1]: http://jcgomez-lavo.perso.ec-marseille.fr/page_proxy.php
 [2]: ../../ingenieur-generaliste.html