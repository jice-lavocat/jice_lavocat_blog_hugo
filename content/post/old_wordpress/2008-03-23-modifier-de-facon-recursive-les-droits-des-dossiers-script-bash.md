---
title: 'Modifier de façon récursive les droits des dossiers [Script Bash]'
author: Jice

date: 2008-03-23
url: /2008/03/modifier-de-facon-recursive-les-droits-des-dossiers-script-bash/
btc_comment_counts:
  - 'a:0:{}'
btc_comment_summary:
  - 'a:0:{}'
categories:
  - Linux
tags:
  - Bash
  - Linux
  - Sécurité
---
Vous êtes étudiants à l&#8217;Ecole Centrale Marseille ? Vous êtes sur un réseau où les administrateurs se font du soucis pour la sécurité ? Il y a fort à parier que la publication d&#8217;un site web présente quelques difficultés pour le néophyte.

En effet, le serveur qui affichera vos pages web (apache?) se basera sur les droits que vous accordez à vos fichiers. Si ceux-ci sont mal réglés, vous n&#8217;aurez pas le droit d&#8217;y accéder par le web.

Voilà le code source d&#8217;un script bash pour faire les changements automatiquement sur votre fichier web :

<script src="https://gist.github.com/tanzaho/d8866efa4b0913e8b8eeeed2d052c3b2.js"></script>

### Utilisation :

Créer un fichier vierge : &#8216;touch nom_script.sh&#8217;, dans lequel vous allez copier le texte ci-dessus. Pour l&#8217;exécuter, donner lui les droits nécessaire (&#8216;chmod 700&#8242; devrait suffire).

Lancez le ensuite grâce à &#8216; ./nom_script.sh&#8217;.
