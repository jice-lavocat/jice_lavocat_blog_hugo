+++
date = "2018-03-14"
title = "Calculer la LTV d'une app B2B"
url = "2018/calcul-ltv-app-b2c/"
image = "/images/posts/2018/ga_play_sound/google_analytics_live_play_sound_alert.png"
description = " In this post you'll find a bookmarklet that allows you to hear a sound notification whenever you have a new visitor showing up in your Real-Time Google Analytics view."
tags = ["mobile", "growth", "data", "analytics"]
+++

Calculer la LTV d'une app est devenu l'une des premières étapes à effectuer quand on aborde les problématiques de croissance (_Growth_). Si la littérature à ce sujet abonde pour les app SaaS B2B, c'est moins souvent le cas pour les app B2C qui cumulent plusieurs petits détails qui ralentissent ce calcul.

Nous allons ici tenter de calculer le revenu d'un utilisateur d'une application B2C gratuite, durant sa durée de vie (_LTV_). Nous prendrons l'exemple d'un jeu mobile en ligne, dans lequel deux sources de revenu coexistente : les achats in-app ainsi que la publicité display.

Vous trouverez dans la dernière partie une feuille de calcul Google Drive avec les formules, que vous pourrez utilisez pour calculer le LTV de votre propre application.

## Qu'es-ce que la LTV ?

LTV signifie **Lifetime Value** , ce qui de l'anglais se traduit par "Revenu sur le cycle de vie". En pratique il s'agit du revenu moyen qu'un utilisateur va générer en utilisant vos services au cours du temps.

Dans la suite de l'article nous parlerons de **LTV à 6 mois** et de **LTV à 1 an** pour parler du revenu que génère un utilisateur en 6 mois ou un an.

## Pourquoi calculer la LTV ?

En connaissant la LTV de vos utilisateurs, vous saurez combien ils sont succeptibles de générer dans le temps. Ce paramètre va servir de base à votre stratégie d'acquisition.

En effet, pour acquérir vos utilisateurs, vous dépensez sur différents canaux d'acquisition (la pub en ligne, le SEO, les évènements physiques, ...). On parle de **Coût d'Acquisition Client** (_CAC_) pour caractériser le coût moyen dépensé pour acquérir un nouvel utilisateur. Le _CAC_ se calcul canal par canal, voir campagne par campagne.

Si votre _CAC_ dépasse votre _LTV_, autrement dit si vous dépensez plus pour obtenir un utilisateur que celui-ci ne vous rapporte, vous êtes dans le rouge. Vous perdez de l'argent sur ce canal ou cette campagne d'acquisition. A l'inverse, si votre _LTV_ est bien plus élevée que votre _CAC_, votre Retour sur Investissement (_ROI_) sera plus important.

Dans la pratique, en B2B, la communauté s'accorde à dire qu'une campagne est un succès quand le _CAC_ < (_LTV_ / 3). Cette marge permet de couvrir les frais de fonctionnement, et de générer du revenu.



## Calcul de LTV - B2B vs B2C

Quand on effectue l'exercice pour une application à destination du B2B, les données sur lesquelles il est possible de s'appuyer sont souvent bien consistantes. Le revenu de chaque client est connu (donc le revenu moyen mensuel est facilement calculable), le taux de retention (et par conséquent celui d'attrition, _Churn_) l'est aussi.

Dans le cas d'une application B2C, ces deux informations sont très souvent beaucoup plus difficiles à définir :

-  L'utilisation n'étant pas liée à un abonnement (ou très rarement), le taux de retention doit se calculer sur des échelles de temps différentes (journalière, hebdomadaire, mensuel) en fonction des cas.
- Les revenus peuvent provenir de différentes sources, très souvent inhomogènes. Par exemple, sur de l'achat in-app, 10% des utilisateurs payant peuvent générer 90% de vos revenus. Ou sur des revenus de type _Ads_, en fonction des annonceurs, votre CPC peut varier du jour au lendemain.

La simulation de votre LTV doit prendre en compte vos spécificités.

[**A vérifier**] En B2B, comme les revenus sont soumis à un abonnement, on peut se fier plus précisément à la rétention, et on connait donc précisément la durée de vie. On peut rapidement calculer la durée de vie moyenne : si l'attrition (churn) mensuelle en pourcentage est _Ch_, la durée de vie _LT_ = 1/Ch.

## Calcul en pratique

En pratique, nous allons procéder de façon assez basique. Après avoir calculer le revenu journalier moyen par utilisateur, nous allons en faire la somme sur une année, en pondérant par le taux de retention :



## Exemple : calcul de la LTV d'un jeu vidéo mobile

Nous allons prendre l'exemple d'un jeu mobile qui génère des revenus via les achats in-app et via des annonces publicitaire dans le jeu. Son taux de retention est assez élevé, mais la plupart des joueurs se connectent le week-end pour jouer.

### Récupérer les informations

La première étape est de récupérer les chiffres liés à l'utilisation de l'application. Pour celà, il est recommandé d'utiliser des outils d'analytics comme Google Firebase, Mixpanel, AppsFlyer, ... Pour éviter un biais trop important, essayer de récupérer au moins 60 à 90 jours de données.

Voici les informations dont vous aurez besoin :

- Nombre d'utilisateurs journaliers (_DAU_ pour Daily Active Users) moyen sur le mois
- Rétention journalière moyenne sur les 30 premiers jours
- Revenu généré sur le mois pour les deux canaux

###
