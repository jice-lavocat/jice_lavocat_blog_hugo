---
title: Regarder Arte ou Roland Garros de l’etranger
author: Jice

date: 2009-05-09
url: /2009/05/regarder-arte-rolland-garros-de-letranger/
aktt_notify_twitter:
  - no
categories:
  - Informatique
tags:
  - Arte
  - Expatriation
  - firefox
  - international
  - proxy
---
## Mise a jour importante

<p style="text-align: justify;">
  Une nouvelle solution est décrite ici : <a href="http://www.graphemeride.com/blog/geolocalisation-des-contenus-mise-en-place-et-contournement" title="Geolocalisation : Utilisation et Contournement">Geolocalisation : Utilisation et Contournement</a>. Veuillez la lire pour une solution plus efficace.
</p>

## Ancien article

<p style="text-align: justify;">
  {{<img style="float: left; margin-left: 5px; margin-right: 5px;" src="https://addons.mozilla.org/en-US/firefox/images/t/5857/943948800" alt="Foxy Proxy" width="200" height="150" >}}Vous êtes en stage <strong>a l&#8217;étranger</strong>, vous avez envie de <strong>regarder Arte </strong>(ou <strong>regarder Roland Garros</strong>)&#8230; pas de chance les sites qui vous permettraient de regarder les émissions en Live ou différés bloquent les connexions qui proviennent d&#8217;<strong>IP non françaises</strong>. La solution consiste a passer par un proxy francais.
</p>

<p style="text-align: justify;">
  Facile a dire, pas si facile a faire quand on a pas trop l&#8217;habitude de chercher des <strong>proxys ouverts</strong>, ou si on ne possède pas son propre serveur sur<strong> IP française qui héberge un proxy</strong>.<!--more-->
</p>

<p style="text-align: justify;">
  Grâceau magnifique tuto de <a title="Tutorial regarder TV a l'etranger" href="http://astuces.jeanviet.info/videos/regarder-les-videos-reservees-aux-americains-grace-a-foxyproxy.htm" target="_blank">Jean Viet</a> j&#8217;ai réussi, et je vous livre en résumé (il explique mieux et plus en détail la technique pour les sites US) la technique pour regarder Arte ou Rolland Garros de l&#8217;étranger avec le navigateur <strong>Firefox</strong>.
</p>

<p style="text-align: justify;">
  <span style="text-decoration: underline;">Avant-propos pour les débutants :</span>
</p>

<p style="text-align: justify;">
  Une <a title="Adresse IP" href="http://fr.wikipedia.org/wiki/Adresse_IP" target="_blank">adresse IP</a> est un identifiant unique qui permet de reconnaître votre ordinateur sur internet.
</p>

<p style="text-align: justify;">
  Un <a title="Proxy" href="http://fr.wikipedia.org/wiki/Proxy" target="_blank">proxy</a> est un serveur sur lequel peuvent transiter des informations et qui sert de passerelle entre vous et internet. Vous demandez au proxy l&#8217;information que vous voulez, il va la chercher avec SON adresse IP, et vous la renvoie.
</p>

<h2 style="text-align: justify;">
  Trouver une liste de proxy ouverts francais qui fonctionnent :
</h2>

Ca se passe la : <a title="Liste de proxys gratuits" href="http://www.freeproxylists.com/fr.html" target="_blank">http://www.freeproxylists.com/fr.html</a>

<p style="text-align: justify;">
  Sur la gauche vous pourrez trouver la liste de proxys pour d&#8217;autres pays courants. La seule chose a faire est de consulter les listes de &#8220;raw proxys&#8221;. Vous devez normalement en avoir plusieurs a disposition. Comme chaque liste contient une dizaines de proxys, vous avez le choix.
</p>

<p style="text-align: justify;">
  Ensuite il faut les tester. Pour se faire, copier tout une des listes de raw proxy que vous avez, et tester la sur ce site : <a title="Verifier liste de proxys" href="http://www.checker.freeproxy.ru/checker/index.php" target="_blank">http://www.checker.freeproxy.ru/checker/index.php</a> (copier/coller, puis &#8220;check proxys&#8221;).
</p>

<p style="text-align: justify;">
  A la fin, vous allez en avoir beaucoup qui ne marchent pas, et seuls quelques uns qui fonctionnent : &#8221;    HTTP: Proxy is working!&#8221;
</p>

<p style="text-align: justify;">
  Voila, vous avez a présent l&#8217;<strong>adresse IP et le port du proxy</strong> que vous allez utiliser ensuite.
</p>

<p style="text-align: justify;">
  Rappel pour ceux qui ne savent pas :<br /> XXX.XXX.XXX.XXX:YYYY<br /> Le XXX.XXX.XXX.XXX correspond a l&#8217;<strong>adresse IP</strong><br /> Et le YYYY correspond au <strong>port</strong>.
</p>

## Installer  et configurer Foyxy Proxy :

<p style="text-align: justify;">
  Ce plugin va vous faciliter la vie par ses options. Il remplace facilement le gestionnaire de connexion de Firefox de base.
</p>

Allez l&#8217;installer sur  : <a title="Foxy Proxy" href="https://addons.mozilla.org/en-US/firefox/addon/2464" target="_blank">https://addons.mozilla.org/en-US/firefox/addon/2464</a>

<p style="text-align: justify;">
  Ensuite, vous aurez son icone en bas a gauche. Un clic dessus vous amène dans sa configuration.<br /> Cliquez sur : &#8220;add new proxy&#8221;. Dans l&#8217;onglet &#8220;General&#8221; vous lui donnez un petit nom, et dans l&#8217;onglet &#8220;Proxy details&#8221; vous rentrez les informations obtenues a l&#8217;étape précédente (IP et port).
</p>

<p style="text-align: justify;">
  Vous pouvez ensuite précisez dans quelles conditions utiliser ce proxy, pour eviter de ralentir votre connexion le reste du temps. Pour se faire, j&#8217;ai configurer de base le comportement suivant : le proxy francais est appele lorsque je visite une URL qui contient &#8220;arte&#8221;. Pour se faire :<br /> -Cliquez sur &#8220;new pattern&#8221;. Donnez un nom au pattern (regle) que vous aller créer. Vérifier qu&#8217;il soit &#8220;enabled&#8221; (active) et dans URL pattern, remplissez &#8221;   *arte*   &#8220;. Cochez en-dessous : whitelist (autorise) et &#8220;wildcard&#8221; (pour utiliser les *).
</p>

<p style="text-align: justify;">
  Cliquez sur ok partout. Normalement vous devez préciser a foxyproxy son comportement. Après l&#8217;installation il doit être sur &#8220;désactivé&#8221; (en bas, a cote de l&#8217;icône le texte doit être rouge). Faites un clic droit, et sélectionnez &#8220;use proxys &#8230; patterns&#8221; comme ça il ne marchera que sur les sites qui possèdent &#8220;arte&#8221; dans leur url.
</p>

<p style="text-align: justify;">
  Voila&#8230; ai-je ete clair ou il y a des points sombres a eclaircir en commentaires?
</p>

<h2 style="text-align: justify;">
  Signer la pétition :
</h2>

<p style="text-align: justify;">
  Tres recemment a ete mis en ligne la petition suivante que je vous encourage a remplir :
</p>

<p style="text-align: justify;">
  <a title="Petitions pour regarder arte de l' etranger" href="http://www.mesopinions.com/Diffusion-libres-des-programmes-de-http---plus7-arte-tv-pour-les-Francais-et-Europeens-residant-a-l-etranger--petition-petitions-76af6d7cd2247a5f244d90b98628e356.html" target="_blank">http://www.mesopinions.com/&#8230;</a>
</p>

<p style="text-align: justify;">
  Elle demande la <span>diffusion libres des programmes de <a href="http://plus7.arte.tv" target="_blank">http://plus7.arte.tv</a> pour les Français et Européens résidant a l&#8217;étranger.</span>
</p>

<h2 style="text-align: justify;">
  <span>Mise à jour : </span>
</h2>

<p style="text-align: justify;">
  <span>Lire l&#8217;article concernant la création d&#8217;un<a href="http://localhost/oldblog/2010/11/expat-la-tv-francaise-a-letranger/"> service pour diffuser la TV à l&#8217;étranger</a><br /></span>
</p>