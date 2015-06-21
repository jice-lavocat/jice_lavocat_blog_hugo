---
title: Extraire les URLs des résultats Google en python
author: Jice

date: 2009-02-04
url: /2009/02/extraire-urls-des-resultats-google-en-python/
aktt_notify_twitter:
  - no
categories:
  - Informatique
tags:
  - python
  - SEO
---
<p style="text-align: justify;">
  J&#8217;ai passé une bonne partie de l&#8217;après-midi à me former à Python. Comme exercice je voulais adapter le script de Tiger sur l&#8217;<a title="Extraction de résultats google en php" href="http://www.seoblackout.com/2008/10/26/extraire-resultats-google/" target="_blank">extraction de résultats sur google</a>, en traduisant le php en python.
</p>

<p style="text-align: justify;">
  J&#8217;ai eu quelques soucis à cause d&#8217;erreurs d&#8217;innatention et de bêtises de codage, mais au final j&#8217;ai réussi. Le code suivant (Python 3.0) vous donne le même résultat (sans la mise en forme) que le script de Tiger.<!--more-->Le code obtenu est le suivant :
</p>

<p style="text-align: justify;">
   
</p>

<pre><code lang="python">
import urllib.request
import re

user_agent = 'Mozilla/4.0 (compatible; MSIE 5.5; Windows NT)'
headers = { 'User-Agent' : user_agent }

ext="fr"
lang="fr" #sur quelle datacenter chercher?"

nb_page=5 #Nombre de pages de résultat
keyword='"Dynamic+Friends"+ring+google.com' #Mot clé cherché

pagenum = 0	#on commence à la page 1
googlefrurl = "http://www.google."+ext+"/custom?hl="+lang+"&#038;q=" + keyword + "&#038;start="+str(pagenum)

f = open("liste_url_collectees.txt", "w")
while pagenum &lt;= nb_page:
	rep = urllib.request.Request(googlefrurl,None,headers)
	response = urllib.request.urlopen(rep)
	result = str(response.read())
	sep='
&lt;h2 class=r>&lt;a href=.*?>'
	matches=re.findall(sep,result)
	res_tab=[]
	for elt in matches:
		sep='http.*?"'
		match=re.findall(sep,elt)
		res_tab.append(match[0][:-1])

	for elt in res_tab:
		print(elt)
		f.write(elt+"n")

	pagenum = int(pagenum)+1 #on passe à la page suivante
	pagenum2 = str(pagenum)+'0'#on met en forme pour google qui va de 10 en 10
	googlefrurl = "http://www.google."+ext+"/custom?hl="+lang+"&#038;q=" + keyword + "&#038;start="+pagenum2+"&#038;safe=off&#038;pwst=1&#038;filter=0"

f.close()
</code>
</pre>

<p align="justify">
  Au final on obtient un fichier <em>liste_url_collectees.txt</em> qui va nous servir à plein de chose&#8230;
</p>