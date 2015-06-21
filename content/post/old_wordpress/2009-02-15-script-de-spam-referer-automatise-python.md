---
title: Script de spam referer automatisé python
author: Jice

date: 2009-02-15
url: /2009/02/script-de-spam-referer-automatise-python/
aktt_notify_twitter:
  - no
categories:
  - Informatique
tags:
  - python
  - SEO
  - web
---
<p style="text-align: justify;">
  Script de Spam Referer automatisé en Python
</p>

<p style="text-align: justify;">
  <img class="alignleft size-full wp-image-119" style="margin: 5px;" title="Spammeur SEO" src="/images/posts/oldwordpress/uploads/2009/02/seo_black_hat.jpg" alt="Spammeur SEO" width="140" height="112" />Suite à mon article sur les aléas du spam referer, je poste un script python que j&#8217;ai utilisé pour faire mes tests. Le script se déroule en deux parties. La première va <a title="Récupération résultats google par python" href="http://localhost/oldblog/2009/02/extraire-urls-des-resultats-google-en-python/#more-127">récupérer les résultats google et les enregistrer dans un fichier</a>.
</p>

<p style="text-align: justify;">
  Je vous laisse consulter l&#8217;<a title="Enregistrer résultats google par script python" href="http://localhost/oldblog/2009/02/extraire-urls-des-resultats-google-en-python/#more-127">article</a> et revenir ici pour la deuxième partie. La deuxième partie va :<!--more-->
</p>

<ul style="text-align: justify;">
  <li>
    consulter les url archivées
  </li>
  <li>
    les visiter avec un fake referer
  </li>
  <li>
    vérifier que l&#8217;injection s&#8217;est bien passée
  </li>
  <li>
    si oui elle enregistre les résultats dans un fichier pour pouvoir les donner à manger rapidement à google
  </li>
</ul>

<p style="text-align: justify;">
  Le script est donc le suivant :
</p>

<pre><code lang="python">
import urllib.request
import re

user_agent = 'Mozilla/5.0 (Windows; U; Windows NT 5.1; fr; rv:1.9.0.5) Gecko/2008120122 Firefox/3.0.5'
headers = { 'User-Agent' : user_agent }
fake_referer='http://www.le-refpowa.fr'

f = open("liste_liens_enregistres_avant.txt", "r")
save=open("vient_manger_cher_google.html","w")
save.write("
&lt;h1>Mes Favoris&lt;/h1>

")
nb_ok=0
while True:
	txt=f.readline()
	if txt=="":
		break
	url_target=txt
	req = urllib.request.Request(url_target, None, headers)
	req.add_header('Referer', fake_referer)
	response = urllib.request.urlopen(req)
	resultat_html=str(response.read())
	match=re.findall(fake_referer,resultat_html)
	if match==[]:
		print("Injection ratee sur "+url_target)
	else:
		print("Injection reussie de "+fake_referer+" sur "+url_target)
		save.write('&lt;a href="'+url_target+'">'+url_target+'&lt;/a>')
		nb_ok=nb_ok+1
f.close()
save.close()

print("Nombre d'injections réussies : "+str(nb_ok))
</code></pre>

<p style="text-align: justify;">
  Au final j&#8217;ai un fichier comme le lien suivant où je regroupe mes <a title="Favoris Refpowa" href="http://localhost/oldblog/favoris1.html">favoris sur le refpowa</a>, et j&#8217;espère que google le parcourra rapidement !!!!
</p>