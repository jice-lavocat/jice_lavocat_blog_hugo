---
title: Personnaliser ses pages d’erreurs sous Joomla
author: Jice

date: 2008-08-31
url: /2008/08/personnaliser-ses-pages-derreurs-sous-joomla/
btc_comment_counts:
  - 'a:0:{}'
btc_comment_summary:
  - 'a:0:{}'
categories:
  - Informatique
tags:
  - 404
  - Joomla
---
<p align="justify">
  Vous possédez un site sous <strong>Joomla</strong>, vous vouliez faire des <strong>pages d&#8217;erreur 404 personnalisées</strong>? Malheureusement, la mise en place des <strong>URLs SEF</strong> sous Joomla vous empêche de le faire.
</p>

<p align="justify">
  En effet, toutes les URLs sont redirigées vers le module de SEF de Joomla qui traite lui même les adresses URL demandées. Du coup, impossible de traiter cette fameuse page 404. Il existe pourtant une solution.
</p>

### Customiser le fichier error.php

<p align="justify">
  Dans Joomla 1.5 l&#8217;affichage des messages d&#8217;erreurs se fait grâce au fichier <strong>error.php</strong> présent dans <em>racine/templates/system</em>. Pour le customiser, copier ce fichier dans le répertoire de votre template actuel. Faites-y les modifications que vous voulez, et le tour est joué.
</p>

<p align="justify">
  &#8230;
</p>

<p align="justify">
  Ce fut bref comme tuto non? Bon, ok, je vais jusqu&#8217;au bout.
</p>

<p align="justify">
  <h3>
    Adapter Joomla, l&#8217;Erreur 404 et le script Google :
  </h3>
  
  <p align="justify">
    Dans son site d&#8217;aide aux webmasters, google fournit un script pour renvoyer si possible au visiteur une page la plus proche de celle recherchée. Pour l&#8217;utiliser, rien de plus simple, il suffit de créer une page, et d&#8217;y insérer le code html. Le script récupérera l&#8217;adresse URL demandé, et fera (je suppose) une recherche dans la base de donnée Google pour voir quelle URL est la plus proche.
  </p>
  
  <p align="justify">
    On aurait pu créer un article Joomla dans lequel serait indiqué à l&#8217;utilisateur qu&#8217;il tombe sur une erreur 404, et mettre à la suite le script. Dans le fichier error.php personnalisé nous aurions mis dans les premières lignes :
  </p>
  
  <p>
    <?php<br /> if ($this->error->code = &#8216;404&#8217;) {<br /> header(&#8220;HTTP/1.0 404 Not Found&#8221;);<br /> header(&#8216;Location: http://www.mon_site.fr/index.php?option=com_content&view=article&id=16&Itemid=14&#8242;); //adresse de l&#8217;article 404 sous joomla<br /> exit;<br /> }<br /> ?>
  </p>
  
  <p>
    Mais le problème vient du fonctionnement du script. Celui-ci regarde l&#8217;URL donnée en entrée. Et là, il y voit l&#8217;adresse de la page d&#8217;erreur {{<img title="Undecided" src="plugins/editors/tinymce/jscripts/tiny_mce/plugins/emotions/images/smiley-undecided.gif" border="0" alt="Undecided" >}}.
  </p>
  
  <p>
    Voilà la solution : juste après
  </p>
  
  <p>
    defined( &#8216;_JEXEC&#8217; ) or die( &#8216;Restricted access&#8217; );
  </p>
  
  <p>
    J&#8217;ai mis les lignes suivantes (et j&#8217;ai laissé le reste du fichier error.php inchangé par rapport à celui d&#8217;origine) :
  </p>
  
  <p>
    if ($this->error->code = &#8216;404&#8217;) {<br /> header(&#8220;HTTP/1.0 404 Not Found&#8221;);<br /> $url=&#8221;http://www.mon-site.fr/index.php?option=com_content&view=article&id=16&Itemid=14&#8243;; //adresse article 404<br /> $result= file_get_contents($url);<br /> echo $result;
  </p>
  
  <p>
    exit;<br /> }
  </p>
  
  <p>
    Le script prend alors bien en compte l&#8217;URL demandée par le visiteur.
  </p>
  
  <p>
    Par contre, <strong>j&#8217;aurais besoin de vos commentaires</strong> : je n&#8217;ai pas l&#8217;impression que ce script google marche très bien. Est-ce le cas pour vous? Sur joomla ou non?
  </p>