---
title: Modéliser la blogosphère
author: Jice

date: 2009-07-26
url: /2009/07/modeliser-la-blogosphere/
categories:
  - Informatique
tags:
  - blog
  - web
---
Je suis actuellement en train de lire le livre :  &#8220;<a href="http://www.morganclaypool.com/doi/abs/10.2200/S00213ED1V01Y200907DMK001" target="_blank">Modelling and Data Mining the Blogosphere</a>&#8221; de <a href="http://www.public.asu.edu/~nagarwa6/" target="_blank">N.Agarwal</a> et <a href="http://www.public.asu.edu/%7Ehuanliu/" target="_blank">H.Liu</a>.

Le livre est un condensé de maths appliquées au web, et spécialement au monde des blogs. Pour vous donner envie de lire le livre, voilà un petit extrait :

<p style="text-align: justify;">
  <cite>Past few years have observed a phenomenal growth in the blogosphere. Technorati<br /> (<a href="http://technorati.com/blogging/state-of-the-blogosphere/" target="_blank">http://technorati.com/blogging/state-of-the-blogosphere/</a>) published a report on<br /> the growth of the blogosphere. The report mentioned that the blogosphere is consistently doubling<br /> every 5 months for the last 4 years and the size was estimated to be approximately 133 million blogs<br /> by December 2008. Furthermore, 2 new blogs or roughly 18.6 new blog posts are added to the blogosphere<br /> every second. Given the prominent and continued growth of the blogosphere, it is natural<br /> to ask whether it is possible to model the growth of the blogosphere and derive some macro-level<br /> statistics that characterizes the blog network. To study the complex network such as blogosphere,<br /> researchers can develop blog models and generate data through these models while continuously<br /> collecting blog data.</cite>
</p>

<p style="text-align: justify;">
  Je posterai peut être des mises à jour à ce billet qui est quasiment aussi rempli qu&#8217;un tweet.
</p>

<p style="text-align: justify;">
  Note :
</p>

<p style="text-align: justify;">
  En premier lieu, les auteurs distinguent deux graphes orientés : graphe des blogs, graphe des posts. Le premier constitue la forme basse résolution du deuxième graphe. En effet, dans le deuxième on considère chaque post unique comme un sommet du graphe, et les liens pointant vers d&#8217;autres posts sont les arêtes du graphe. Le premier graphe quand à lui rassemble tous les posts sous le blog initial.
</p>

<p style="text-align: justify;">