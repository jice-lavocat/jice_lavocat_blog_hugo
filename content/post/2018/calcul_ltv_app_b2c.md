+++
date = "2018-03-14"
title = "Calculer la LTV d'une app B2C"
url = "2018/calcul-ltv-app-b2c/"
image = "/images/posts/2018/ltv/ltv_mobile_phone.png"
description = " In this post you'll find a bookmarklet that allows you to hear a sound notification whenever you have a new visitor showing up in your Real-Time Google Analytics view."
tags = ["mobile", "growth", "data", "analytics"]
+++

Calculer la LTV d'une app est devenu l'une des premières étapes à effectuer quand on aborde les problématiques de croissance (_Growth_). Si la littérature à ce sujet abonde pour les app SaaS B2B, c'est moins souvent le cas pour les app B2C qui cumulent plusieurs petits détails qui compliquent ce calcul.

Nous allons ici tenter de calculer le revenu pour un utilisateur d'une application B2C gratuite, durant sa durée de vie (_LTV_). Nous prendrons l'exemple d'un jeu mobile en ligne, dans lequel deux sources de revenu coexistent : les achats in-app ainsi que la publicité display.

Vous trouverez dans la dernière partie une feuille de calcul Google Drive avec les formules, que vous pourrez utilisez pour calculer le LTV de votre propre application.

## Qu'es-ce que la LTV ?

LTV signifie **Lifetime Value** , ce qui de l'anglais se traduit par "Revenu sur le cycle de vie". En pratique il s'agit du revenu moyen qu'un utilisateur va générer en utilisant vos services au cours du temps.

Dans la suite de l'article nous parlerons de **LTV à 6 mois** et de **LTV à 1 an** pour parler du revenu que génère un utilisateur en 6 mois ou un an.

## Pourquoi calculer la LTV ?

En connaissant la LTV de vos utilisateurs, vous saurez combien ils sont succeptibles de générer dans le temps. Ce paramètre va servir de base à votre stratégie d'**user acquisition**.

En effet, pour acquérir vos utilisateurs, vous dépensez sur différents canaux d'acquisition (la pub en ligne, le SEO, les évènements physiques, ...). On parle de **Coût d'Acquisition Client** (_CAC_) pour caractériser le coût moyen dépensé pour acquérir un nouvel utilisateur. Le _CAC_ se calcul canal par canal, voir campagne par campagne.

Si votre _CAC_ dépasse votre _LTV_, autrement dit si vous dépensez plus pour obtenir un utilisateur que celui-ci ne vous rapporte, vous êtes dans le rouge. Vous perdez de l'argent sur ce canal ou cette campagne d'acquisition. A l'inverse, si votre _LTV_ est bien plus élevée que votre _CAC_, votre Retour sur Investissement (_ROI_) sera plus important.

Dans la pratique, en B2B, la communauté s'accorde à dire qu'une campagne est un succès quand le _CAC_ < (_LTV_ / 3). Cette marge permet de couvrir les frais de fonctionnement, et de générer du revenu. Je n'ai pas assez de recul en B2C pour connaitre les recommandations, donc jusqu'à avis contraire, j'utilise aussi LTV/3.



## Calcul de LTV - B2B vs B2C

Quand on effectue l'exercice pour une application à destination du B2B, les données sur lesquelles il est possible de s'appuyer sont souvent bien consistantes. Le revenu de chaque client est connu (donc le revenu moyen mensuel est facilement calculable), le taux de retention (et par conséquent celui d'attrition, _Churn_) l'est aussi.

Dans le cas d'une application B2C, ces deux informations sont très souvent beaucoup plus difficiles à définir :

-  L'utilisation n'étant pas liée à un abonnement (ou très rarement), le taux de retention doit se calculer sur des échelles de temps différentes (journalière, hebdomadaire, mensuel) en fonction des cas.
- Les revenus peuvent provenir de différentes sources, très souvent inhomogènes. Par exemple, sur de l'achat in-app, 10% des utilisateurs payant peuvent générer 90% de vos revenus. Ou sur des revenus de type _Ads_, en fonction des annonceurs, votre CPC peut varier du jour au lendemain.

La simulation de votre LTV doit prendre en compte vos spécificités.

### Le cas de la LTV en B2B

En B2B, comme les revenus sont soumis à un abonnement, on peut se fier plus précisément à la rétention, et on connait donc précisément la durée de vie. On peut rapidement calculer la durée de vie moyenne : si l'attrition (churn) mensuelle est donné en pourcentage, et qu'on note _LT_ la durée de vie alors :

<img src="/images/posts/2018/ltv/ltv_equation_1.png" alt="Calcul de la durée de vie en fonction du churn" title="Calcul de la durée de vie en fonction du churn"/>

Partant de là, en utilisant le revenu moyen par utilisateur (ARPA), on obtient la revenu de l'utilisateur pendant sa durée de vie, la LTV :


<img src="/images/posts/2018/ltv/ltv_equation_2.png" alt="Calcul du revenu moyen par utilisateur" title="Calcul du revenu moyen par utilisateur"/>

<img src="/images/posts/2018/ltv/ltv_equation_3.png" alt="Calcul du revenu généré par un utilisateur sur sa lifetime" title="Calcul du revenu généré par un utilisateur sur sa lifetime"/>

Pour aller plus loin, il y a de nombreuses ressources pour les SaaS autour du [calcul de LTV](https://www.forentrepreneurs.com/ltv/).


## Comment calculer la LTV en B2C en pratique

En pratique, nous allons procéder de façon assez basique. Après avoir calculer le revenu journalier moyen par utilisateur, nous allons en faire la somme sur une année, en pondérant par le taux de retention :

<!-- LTV = \sum_{i \in days}(ARPDAU * Retention_i) -->

<img src="/images/posts/2018/ltv/ltv_equation_4.png" alt="Calcul du revenu généré par un utilisateur sur sa lifetime" title="Calcul du revenu généré par un utilisateur sur sa lifetime"/>

Dans cette formule, _ARPDAU_ (*Average Revenu Per Daily Active User*) se calcule en fonction du revenu moyen généré chaque jour, divisé par le nombre d'utilisateurs :

<!-- ARPDAU = Avg_Revenu_Day / DAU -->
<img src="/images/posts/2018/ltv/ltv_equation_5.png" alt="Calcul de l'ARPDAU (revenu moyen par utilisateur actif journalier)" title="Calcul de l'ARPDAU (revenu moyen par utilisateur actif journalier)"/>

Enfin, la Retention est approximée grâce à une loi de puissance de type y=a*x^b. Pour le détail de ce calcul on pourra se reporter à la présentation de [Eric Seufert](https://www.slideshare.net/EricSeufert/ltv-spreadsheet-models-eric-seufert) sur Slideshare, slide 29.

## Exemple : calcul de la LTV d'un jeu vidéo mobile

Nous allons prendre l'exemple d'un jeu mobile qui génère des revenus via les achats in-app et via des annonces publicitaires dans le jeu.

### Récupérer les informations

La première étape est de récupérer les chiffres liés à l'utilisation de l'application. Pour celà, il est recommandé d'utiliser des outils d'analytics comme Google Firebase, Mixpanel, AppsFlyer, ... Pour éviter un biais trop important, essayer de récupérer au moins 60 à 90 jours de données.

Voici les informations dont vous aurez besoin :

- Nombre d'utilisateurs journaliers (_DAU_ pour Daily Active Users) moyen sur le mois
- Rétention journalière moyenne sur les 30 premiers jours
- Revenu généré sur le mois pour les deux canaux

### Calculer le revenu moyen journalier par utilisateur actif

Pour commencer, il est nécessaire d'obtenir :

- le DAU, cela se passe dans votre outil d'analytics qui comptera le nombre de sessions uniques moyennes par jour
- le revenu généré pendant les 30 derniers jours

Sur cette base, on calculera la valeur de **revenu moyen journalier d'un utilisateur actif** pour les deux canaux (in-app purchase/display ads).

<img src="/images/posts/2018/ltv/ltv_equation_6.png" alt="Calcul de l'ARPDAU (revenu moyen par utilisateur actif journalier)" title="Calcul de l'ARPDAU (revenu moyen par utilisateur actif journalier)"/>

Cette information devrait déjà vous donner un repère purement pratique pour estimer votre revenu au cours du mois. En multipliant cette valeur par le nombre d'utilisateurs du jour, vous pourrez connaitre approximativement le revenu au jour le jour. L'utilité se ressent si vous avez un volume qui varie avec la saison. En comparant avec l'année précédente, vous pourrez prévoir comment se passera le mois à venir et investir en conséquence.

### Calculer la rétention au cours de la vie d'un utilisateur

Ici, nous allons projeter les taux de retention à partir des premiers jours d'utilisation. Si à _t=0_ nous avons 100 nouveaux inscrits, cela nous permettra de savoir, après _n_ jours combien d'utilisateurs sont encore actifs en moyenne.

L'approximation sera assez limitée, et l'équation que vous utilisez devra être affinée avec le temps en fonction de votre activité et de la retention de votre app. Ici, nous partons d'une loi de puissance qui se prête généralement bien au courbes de retention.

y=a*x^b

Pour le calcul dans une spreadsheet, les fonctions varies d'un outil à l'autre. Dans Google Sheet, la formule pour calculer les paramètres _a_ et _b_ est la suivante :

- = EXP(INDEX(LINEST(intervalle_data;intervalle_abcisse);2))
- = INDEX(LINEST(intervalle_data;intervalle_abcisse);1)

Dans l'intervalle des abscisses on listera le jour depuis l'installation de l'app. Dans les data, on renseignera le taux de retention de la base utilisateur.

Ces deux coefficients vous permettent de reconstruire et de projeter les valeurs de retention pour les jours à venir :

- = coef_a*POWER(jour_depuis_install;coef_b)

### Lifetime Value

Via la formule de retention estimée, vous pourrez alors calculer le revenu estimé d'un utilisateur pour chaque jour suivant son inscription. Il vous suffit de multiplier la retention du jour par l'ARPDAU :

- = retention_jour * arpdau

Une petite somme sur l'intervale qui vous intéresse (6 mois, 1 an, ...) et vous avez à disposition le revenu estimé d'un utilisateur.

En fonction de votre stratégie d'investissement, vous pouvez être aggressif et tenter d'acquérir un utilisateur avec un ROI positif en 3 mois, 6 mois, 12 mois, ...

## Modèle de Lifetime Value (Google Sheet)

Pour vous faciliter le travail, je vous propose d'utiliser le modèle de calcul que j'ai mis en ligne pour un projet sur lequel je travaille.


<a href="https://docs.google.com/spreadsheets/d/1GQHxZie-5t0XOQoFzcJn5iti06SzUieJO5e-iFgfVgA/edit?usp=sharing" target="_blank" ><img src="/images/posts/2018/ltv/calcul_ltv_google_spreadsheet.png" alt="Calculateur de LTV B2C spreadsheet" title="Calculateur de LTV B2C spreadsheet"/></a>

Le modèle vous propose de renseigner la retention journalière à J+1, J+7, J+14 et J+30. Il calcule ensuite la LTV à 180 et 360 jours.

A vous de le copier dans votre Drive et de le modifier à l'envie pour qu'il s'adapte à vos besoins.

<center><div ><a class="menu-button"  href="https://docs.google.com/spreadsheets/d/1GQHxZie-5t0XOQoFzcJn5iti06SzUieJO5e-iFgfVgA/edit?usp=sharing" target="_blank" style="text-decoration: none; display:inline-block; float:none; background-color: #4A90E2; color: #fff">Calculateur de LTV (Google spreadsheet)</a></div></center>


Des questions ? N'hésitez pas à les poser en commentaires.

## Ressources supplémentaires

- [Two Methods for Modeling LTV with a Spreadsheet](https://www.slideshare.net/EricSeufert/ltv-spreadsheet-models-eric-seufert)
- [Un plugin pour faire des régressions de puissance rapidement sur Google Sheets](https://magnus-karlsson.nu/powerregression/#h.tgycqt34hyl0)
- [Modelling lifetime](http://blog.soomla.com/2016/04/clv-calculation-modeling-lifetime.html)
<!-- - [Spreadsheet pour Excel chez Tilting Point](https://tiltingpoint.com/how-to-calculate-ltv-for-mobile-game/) -->
