---
title: Les pages parking
author: Jice

date: 2009-02-25
url: /2009/02/les-pages-parking/
aktt_notify_twitter:
  - no
categories:
  - Informatique
tags:
  - SEO
---
## Définition d&#8217;une page parking :

Les pages parking&#8230;? Kesako?

<p style="text-align: justify;">
  Vous avez tous déjà rencontré ces pages en tapant au hasard une adresse web dans votre navigateur. Qu&#8217;il s&#8217;agisse de &#8230;.com ou de &#8230;.fr, il peut s&#8217;agir de <strong>typosquatting </strong>ou simplement d&#8217;un <strong>domainer </strong>qui attend avec son joli nom de domaine sans rien en faire. Dans ce cas, les noms de domaines sont souvent en vente sur <a title="Domainers en vadrouille" href="http://sedo.fr/" target="_blank">sedo.fr</a>. Pour ceux qui se sentent intéressés par le domaining (on réserve un <strong>nom de domaine</strong> et on le revend au plus offrant) je vous recommande le forum français de référence : <a title="Forum pour Domainers sur les noms de domaine" href="http://www.forumndd.com/" target="_blank">http://www.forumndd.com</a>
</p>

Pour continuer cet article, je demande à google de bien vouloir indexer la page suivante : <a title="Page parking sur les chiens et les fleurs" href="http://www.le-refpowa.fr/parking/" target="_blank">http://www.le-refpowa.fr/parking/</a>

<!--more-->

## Principe d&#8217;une page parking :

<p style="text-align: justify;">
  Une <strong>page parking</strong>, comment ça fonctionne? Et bien c&#8217;est très simple, ça regarde comment vous êtes arrivés dessus, et ça vous affiche ce que vous auriez voulu voir (en principe). Par exemple, admettons que j&#8217;ai un nom de domaine qui peux abritter des informations sur la nature (c&#8217;est vaste). Vous pourriez très bien venir chez moi en cherchant des infos sur les chiens ou sur les fleurs&#8230;
</p>

<p style="text-align: justify;">
  Comment choisir ce que j&#8217;affiche? Et bien c&#8217;est simple, je vais voir comment vous êtes venu sur cette page. En pratique, le php permet de connaitre le <strong>referer</strong>, lien à partir duquel vous êtes attérit sur ma page! Si vous êtes venu d&#8217;un site qui vante les informations sur les <a title="Chiens sur Refpowa" href="http://www.le-refpowa.fr/parking/">chiens et le refpowa</a> de ma page, alors je saurais que vous cherchiez des info sur les chiens&#8230; vous suivez toujours?
</p>

<p style="text-align: justify;">
  Une autre manière consiste à voir quelle requête vous aviez tapé sur google pour venir sur ma page&#8230; dans ce cas de figure, j&#8217;attends l&#8217;indexation de google pour vous montrer la puissance du concept.
</p>

<p style="text-align: justify;">
   
</p>

<h2 style="text-align: justify;">
  Mise en pratique en php :
</h2>

<p style="text-align: justify;">
  On a donc deux solutions plus ou moins faciles à mettre en œuvre. La première consiste à regarder simplement lurl du referer et à y chercher les mots clés qui nous intéresse. La deuxième consiste à aller voir quel était l&#8217;ancre du lien qui pointe vers nous&#8230; pour ça, il suffit d&#8217;un peu d&#8217;huile de coude, et de quelques lignes de code. A vos claviers!
</p>

<p style="text-align: justify;">
  Une troisième solution, plus complexe consisterai à parcourir la page référente, extraire la thématique, et afficher notre contenu en rapport avec cette thématique. Cependant cette solution a ses limites. D&#8217;une part car une page parking n&#8217;est pas souvent pointer ;-), d&#8217;autre part car il se peut que le contenu soit fastidieux à extraire, et être totalement sans rapport avec l&#8217;article que lis le visiteur (par exemple dans un blog avec contenu en silot).
</p>

<p style="text-align: justify;">
  Pour la suite de l&#8217;article je me créé donc deux articles (un sur les chiens et un sur les fleurs)dans des fichiers séparés. Lors de l&#8217;appel je vais appeler soit l&#8217;un soit l&#8217;autre en fonction du referer, et les deux si il n&#8217;y a pas de referer transmis (eh oui, il faut bien que ma page soit indexée un jour par google, avec du contenu).
</p>

<p style="text-align: justify;">
   
</p>

<h3 style="text-align: justify;">
  Solution simple :
</h3>

<p style="text-align: justify;">
  On cherche dans l&#8217;adresse référente, le mot clé (demande uniquement l&#8217;utilisation de $_SERVER[&#8216;HTTP_REFERER&#8217;]) et on affiche le résultat voulu. On va ici aussi traiter le cas de google, afin de rester dans l&#8217;esprit SEO de cet article!
</p>

<p style="text-align: justify;">
   
</p>

<pre><code lang="php">
$flag=1; // Affichage à la fin si rien n'a été affiché
if(isset($_SERVER['HTTP_REFERER'])){
	$referer=$_SERVER['HTTP_REFERER'];
	echo "Votre referer est : ".$referer;
	if (preg_match("/chien/i", $referer)) {// Le "i" après le délimiteur du pattern indique que la recherche ne sera pas sensible à la casse
		include("chien.php");
		$flag=0;
	}
	if (preg_match("/fleur/i", $referer)) {// Le "i" après le délimiteur du pattern indique que la recherche ne sera pas sensible à la casse
		include("fleur.php");
		$flag=0;
	}
	}
if ($flag){
	include("chien.php");
	include("fleur.php");
}

</code></pre>

<p style="text-align: justify;">
  On a donc à présent rediriger les gens en fonction de l&#8217;<strong>adresse </strong>de leur referer! Ceci nous est utile pour traiter le cas de google (ou tout autre moteur de recherche qui se basae sur le même principe). Lors d&#8217;une recherche, les mots clé cherchés sont inclus dans l&#8217;url de google&#8230; il va donc être facile de les extraire pour les afficher à l&#8217;utilisateur ou orienter le contenu présenté!
</p>

<p style="text-align: justify;">
  Par exemple si je cherche sur Google l&#8217;expression : <cite title="Chien et Refpowa" lang="French">Chien et Refpowa</cite>, l&#8217;adresse utilisée pour afficher les résultats est : <a href="http://www.google.fr/search?hl=fr&q=chien+et+refpowa&btnG=Recherche+Google&meta=&aq=f&oq=" target="_blank">http://www.google.fr/search?hl=fr&q=chien+et+refpowa&btnG=Recherche+Google&meta=&aq=f&oq=</a> . Nous allons donc extraire le mot clé, et l&#8217;afficher, disons, comme titre de notre page! .. Mais tout cela sera pour un article prochain!
</p>