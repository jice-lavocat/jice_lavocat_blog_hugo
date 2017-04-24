+++
date = "2017-04-20"
title = "Développer avec Amazon Alexa - Tutoriel"
url= "developper_avec_amazon_alexa"
image = "/images/posts/2017/tutoriel_amazon_alexa/amazon-echo-featured.jpg"
tags = ["amazon alexa", "voice programmation"]
+++

La vague d'intérêt pour Amazon Alexa arrive seulement en Europe depuis 2017 alors qu'elle a débuté en 2016 aux États-Unis. Dans cet article en Français, j'ai voulu vous donner quelques pistes pour commencer à coder et développer sur cette plateforme vocale. Ceci est donc la première partie d'une série sur comment coder une **application voice**.

L'avènement du **Voice** est à prévoir pour d'ici quelques mois/années et se base principalement sur des avancées en Traitement Automatique des Langues (TAL, ou Natural Language Processing - NLP en Anglais) et sur la démocratisation du cloud computing.

Si vous avez quelques connaissances en programmation (Python, NodeJs ou Java) et quelques connaissances du système [Amazon Lambda](../../2015/image-conversion-using-amazon-lambda-and-s3-in-node.js/), vous pouvez sauter les premiers paragraphes d'introduction et aller directement à la partie [Hello World avec Alexa]({{< ref "#hello-world-avec-alexa" >}}).

Si vous n'avez pas les compétences mais souhaitez faire *créer une application voice par un freelance*, [faites moi signe](https://twitter.com/Jice_Lavocat).



## L'écosystème Voice

### Amazon Alexa - Amazon Echo

Commençons par le commencement : quel est la différence entre Alexa et Echo ? Très simple, **Amazon Alexa** c'est l'algorithme de reconnaissance et d'interaction vocale développé par la firme de *Jeff Bezos*, tandis que l'Amazon Echo est un des appareils qui permettent d'accéder à Alexa.

Amazon a ainsi construit plusieurs "terminaux" qui tirent parti de la puissance d'Alexa. Echo fut le premier mis sur le marché, et il est aussi le plus puissant car son architecture enregistre mieux les voix, même si elles sont émises d'une autre pièces. L'Amazon Dot et l'Amazon Tap sont deux autres produits de la gamme. Le premier est une version minimaliste de l'Echo, tandis que le Tap se positionne d'abord comme une enceinte bluetooth.

<img src="/images/posts/2017/tutoriel_amazon_alexa/Amazon-Echo.jpg">
<br><center><i>L'Amazon Echo - Vu interne et externe</i></center>

Si vous ne souhaitez pas acheter un device physique, vous pouvez utilisez l'application [iOS](https://itunes.apple.com/app/id944011620) ou [Android](https://play.google.com/store/apps/details?id=com.amazon.dee.app). Cependant, pour les besoins de l'article nous n'utiliserons aucune de ces plateformes, mais plutôt [Echosim.io](https://echosim.io), un outil pour tester pour Alexa (et vos futurs *skills*) via votre compte Amazon. Si vous êtes curieux, vous pouvez déjà aller y faire un tour, et tester quelques commandes :

- loggez vous avec votre compte Amazon
- autorisez l'utilisation du microphone
- pressez espace pendant que vous parlez
- vous pouvez tester "What's the news in France today?" ou "What's the weather in Marseille?"

### Amazon Skills

L'application Alexa, de base, fournit un ensemble de fonctionnalités avancées qui vous permettent de lui parler et de lui demander des informations telles que la météo ou les news du jour. Il y a une petite liste non exhaustive [en anglais sur Cnet](https://www.cnet.com/how-to/amazon-echo-the-complete-list-of-alexa-commands/).

<img src="/images/posts/2017/tutoriel_amazon_alexa/alexa-logo.png">

Ces fonctionnalités de base ne seraient rien sans les applications tierces que l'on peut créer et ajouter à la marketplace. Amazon les appelle **Skills** (compétences en Français) et la place de marché a dépassé le chiffre symbolique de 10 000 skills il y a quelques semaines. Cette place de marché, un peu à la manière de l'appstore Google ou iOS, permet aux développeurs de proposer leur création à tous les propriétaire d'un appareil compatible avec Alexa. On y trouve donc deux types d'applications : les indépendantes (les jeux, les utilitaires, ...) et les applications de marque (ecommerce, culture, Radio, ...).

Cet article va vous permettre de coder votre première skill et de la mettre sur la marketplace. Vous verrez à quel point c'est facile et jouissif.

### Google Home et autres alternatives

Le succès récent d'Alexa a poussé de nombreux constructeurs à sortir leur propre appareil. Le plus connu est sans aucun doute Google Home, une alternative provenant de chez Google et qui intègre plus ou moins les mêmes fonctionnalités et principes. Sans m'être trop penché sur l'écosystème de celui-ci, je pense qu'il y a évidemment une app android. Avec Google Home, les *skills* s'appellent des *actions*.

<img src="/images/posts/2017/tutoriel_amazon_alexa/google-home-lead.jpg">


De nombreux constructeurs peuvent aussi intégrer directement l'algorithme Alexa dans leur objet connecté. C'est d'ailleurs une des forces d'Amazon qui tente de prendre de vitesse l'écosystème IoT (un peu à la manière d'Android qui a phagocyté les OS mobiles). Google a cependant pris les devants en rachetant en Septembre 2016 [Api.ai](https://api.ai/), un service tiers qui permettait d'implémenter facilement des compétences conversationnelles dans votre application/objet connecté.

Bref, ça bouge beaucoup dans ce secteur. Il ne serait pas surprenant de voir arriver Apple ou Facebook dans la course un de ces jours. Facebook possède d'ailleurs le système [Wit.ai](https://wit.ai) pour la conception d'interfaces de type chatbots par texte.


## Voice Apps - Interfaces Conversationnelles - SSML

### Interaction avec le système conversationnel

Avant d'aborder concrètement le code (promis ça vient vite), je voulais présenter rapidement les concepts qui dirigent les applications vocales (Alexa ou Google Home). L'interaction se fait en plusieurs étapes :

1. L'utilisateur parle dans sa langue
- L'appareil enregistre et transfert l'audio sur le cloud vers Alexa
- L'audio est traité et amélioré (on sépare la voix des bruits ambiants)
- L'audio est transcrit (d'une piste audio, on passe à une suite de mots)
- Le texte est interprété (du texte on essaye de saisir une commande avec des arguments)
- La commande est transmise en JSON et réalisée soit via Amazon Lambda soit sur votre propre serveur
- Le résultat est retourné sous format SSML vers Alexa
- L'appareil décrypte le SSML et génère l'audio
- l'audio est renvoyé vers l'appareil de l'utilisateur

<center><img src="/images/posts/2017/tutoriel_amazon_alexa/alexa_skill_interaction_flow.png"><br><i>Le process d'interaction sur Amazon Alexa - Credits: Rick Wargo</i></center>


Je n'ai pas retrouvé la page officielle qui montrait le processus d'interaction complet. L'image était de meilleure qualité. Mais j'espère que vous comprendrez avec celle-ci. Si jamais vous tombez sur une meilleure image de l'interaction, je suis preneur.

### Qu'est-ce que le SSML ?

Le Speech Synthesis Markup Language ([SSML](https://www.w3.org/TR/speech-synthesis11/)) permet aux développeurs de rendre du texte sous format audio en précisant certaines nuances. Il s'agit d'un simple format de markup basé sur l'XML qui permet de rajouter des "effets" sur le texte qui sera "lu" par l'appareil. Un peu comme le ```<strong>``` (gras) ou le ```<em>``` (italique) qui permettent de mettre en avant les mots en html, des balises vont servir à lire correctement votre texte.

Vous pourrez par exemple changer la prononciation des mots avec l'utilisation de phonèmes, ou bien lire des chiffres sous forme ordinal ("Premier, Deuxième") ou cardinal ("Un, Deux") ou insérer une pause entre deux phrases. Le format SSML existe depuis les années 2000 est c'est une recommandation du W3C.

Si vous souhaitez tester quelques phrases en SSML, IBM a mis à disposition une [instance démo de text-to-speach](https://text-to-speech-demo.mybluemix.net/). Vous pouvez tester les différents exemples disponibles dans la [documentation SSML d'Alexa](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/speech-synthesis-markup-language-ssml-reference).

## Hello World avec Alexa

Ok, let's go !!! Je vais suivre plus ou moins le tutoriel officiel d'Amazon pour vous faire découvrir rapidement les possibilités d'Alexa.

Une **application vocale** (voice app) se compose de deux parties. La première regroupe l'ensemble des commandes audio et des arguments qui pourront être prononcés par les utilisateurs. On parle alors des **intentions** (*intents* en Anglais) que l'utilisateur va émettre. On pourrait comparer ça à une interface graphique : les différents boutons ou menus déroulants accessibles. La deuxième partie est plus conventionnelle : c'est le coeur de la fonction, avec la logique, l'accès aux données etc.

La première partie est gérée par Alexa (Amazon a mis en place une interface visuelle dédiée pour rentrer vos paramètres). La seconde partie peut vivre, soit sur Amazon Lambda (on parle alors d'une structure *serverless*) soit sur votre serveur (et dans ce cas elle doit être accessible via une API sécurisée en https).

Avant de commencer à coder, voici quelques liens utiles à bookmarker pour le futur :

Le [tutoriel officiel](https://developer.amazon.com/alexa-skills-kit/alexa-skill-quick-start-tutorial) sur lequel je me suis basé pour écrire cette partie.

[Echosim.io](https://echosim.io), déjà cité plus haut, qui vous permettra de tester votre skill depuis votre navigateur.

La [documentation officielle d'Alexa](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/getting-started-guide) qui vous permettra à l'issue de ce tuto d'aller plus loin.

Le [blog officiel d'Alexa](https://developer.amazon.com/blogs/alexa/tag/alexa) où sortent très fréquemment de nouvelles annonces.

Le [framework Serverless](https://serverless.com/) qui vous permettra, plus tard, d'accélérer le développement de vos skills.


### Etape 1 - L'interface vocale - Intentions d'Utilisateurs

Pour commencer, créez votre compte sur le [portail de développement d'Amazon](https://developer.amazon.com/login.html). Ce portail est différent d'AWS ... pourquoi ? Aucune idée, peut être car les apps sont affichées sur le store Amazon comme un livre classique. Ou bien c'est le système d'[achat in-app](https://developer.amazon.com/in-app-purchasing) qui permettra à vos utilisateurs d'acheter depuis leur Echo qui doit être relier à un compte Amazon classique (pas certain que l'achat in-app soit disponible sur Alexa, à confirmer).

Une fois loggé, cliquez sur l'onglet Alexa, puis sur "Alexa Skill Kit".

<img src="/images/posts/2017/tutoriel_amazon_alexa/alexa_skill_dev_console.png">


Cliquez sur "Add a new skill". Amazon propose une sorte d'assistant pour la conception de votre skill. Beaucoup d'étapes sont assez transparentes et reliées à l'apparence dans le store.


#### Informations sur le skill

Le premier onglet va permettre de gérer les réglages de base de votre skill : son type, son nom, sa langue d'utilisation et la commande pour l'invoquer.

<img src="/images/posts/2017/tutoriel_amazon_alexa/new_skill_wizard.png">


Un skill peut être de trois **types** différents : custom, smart home et flash briefing. Le plus général et le plus flexible est **Custom Interaction Model**. C'est ce type qui permettra à vos utilisateurs de poser des questions à Alexa. Le type Smart Home permet de contrôler des objets connectés ("allume la lumière", "change de chanson", "lance la cuisson du four"). Enfin, le dernier type sert aux sites de news pour retourner aux utilisateurs un bulletin flash (pas totalement certain, je n'ai pas approfondi).

Pour le **langage**, c'est évident. Sachez que seuls l'Anglais US et UK ainsi que l’Allemand sont actuellement disponibles. Pour le **nom**, pareil, c'est transparent.

Le **nom d'invocation** par contre est plus important. C'est l'expression que vos utilisateurs vont utiliser pour "lancer votre application". Ce nom doit obéir à un [ensemble de règles](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/choosing-the-invocation-name-for-an-alexa-skill) mises en place pour éviter le brand squatting et autres problèmes de copyright ou de conflit de commande avec le système core d'Alexa. Première règle, cette commande doit être en deux mots minimum (sauf marque clairement unique), les stop-word et prépositions ne comptent pas. La commande ne doit pas contenir de nom de personne ou de ville. etc. etc.

Plusieurs langues peuvent être inclues dans une même application. Mais vous le verrez seulement lorsque votre première application sera complète.

#### Modèle d'interaction

La partie la plus intéressante, pour les non techniques se situe ici. Vous pouvez faire intervenir ici vos enfants, votre designer, vos parents... Je n'ajoute pas de screenshots ici car l'interface est en train de changer à l'heure où j'écris ces lignes.

L'idée ici est de convenir tout d'abord d'un **schéma d'intentions** qui liste l'ensemble des fonctions qui sont accessibles dans votre application. Si vous suivez le [tutoriel de démarrage rapide d'Amazon](https://developer.amazon.com/alexa-skills-kit/alexa-skill-quick-start-tutorial) vous allez créer deux fonctions (un *getter* - WhatsMyColorIntent - et un *setter* - MyColorIsIntent -); ces deux fonctions sont donc données dans un dictionnaire JSON.

```
{
  "intents": [
    {
      "intent": "MyColorIsIntent",
      "slots": [
        {
          "name": "Color",
          "type": "LIST_OF_COLORS"
        }
      ]
    },
    {
      "intent": "WhatsMyColorIntent"
    },
    {
      "intent": "AMAZON.HelpIntent"
    }
  ]
}
```

La fonction qui permet d'enregistrer la couleur favorite de l'utilisateur ```MyColorIsIntent``` prend en entrée un argument (*SLOT*). Amazon accepte de nombreux [types de **slots**](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/built-in-intent-ref/slot-type-reference) prédéfinis (date, durée, pays, ingrédients, ...). Dans le tutoriel, on définit un type custom *LIST_OF_COLORS* qui correspond à une liste prédéfinie. Dans cette liste vous allez expliquer quelles valeurs sont attendues par Alexa lorsque l'utilisateur va parler :

```
green
red
blue
orange
gold
silver
yellow
black
white
```

Enfin, la dernière étape consiste à lister les **énonciations** possibles (*utterances* en anglais) pour appeler chacune des fonctions. Rappelez-vous, nous avons deux fonctions, `MyColorIsIntent` et `WhatsMyColorIntent` :

* pour la première fonction le guide propose une seule variation :

    `MyColorIsIntent my favorite color is {Color}`

* pour la deuxième, le guide propose de rentrer une longue liste de variations possibles :

    ```
    WhatsMyColorIntent what's my favorite color
    WhatsMyColorIntent what is my favorite color
    WhatsMyColorIntent what's my color
    WhatsMyColorIntent what is my color
    WhatsMyColorIntent my color
    WhatsMyColorIntent my favorite color
    WhatsMyColorIntent get my color
    WhatsMyColorIntent get my favorite color
    WhatsMyColorIntent give me my favorite color
    WhatsMyColorIntent give me my color
    WhatsMyColorIntent what my color is
    WhatsMyColorIntent what my favorite color is
    ```

Vous noterez qu'il n'y a pas de ponctuation dans ces questions. Ces **énonciations** répondent elles aussi à des [règles](https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/alexa-skills-kit-interaction-model-reference#sample-utterances-syntax) et peuvent inclure les variables que nous avons définis un peu plus haut (comme `{COLOR}`).

Vous pouvez sauver et passer à la suite.


#### Configuration du endpoint

Maintenant que votre modèle d'interaction est prêt, il faut relier votre application au code principal qui servira la logique. Le guide vous propose d'utiliser Amazon Lambda pour commencer, ce qui permet de relier plus facilement la fonction à Alexa. On peut revenir plus tard à cette partie, donc concentrons nous à présent sur le code vivant sur AWS Lambda.


### Etape 2 - Création de la logique de votre application

Pour ceux d'entre-vous qui ne connaissent pas Lambda, il s'agit d'un outil de l'écosystème AWS qui permet de lancer des tâches à la demande, sur les serveurs d'Amazon. On peut ainsi définir des triggers qui vont lancer l’exécution d'un bout de code ("upload d'une image sur AWS S3 -> redimensionnement d'une vignette"). Amazon Lambda n'était initialement disponible qu'avec Node.JS mais à présent vous pouvez utiliser Python, Java ou C#.

Le [guide rapide](https://developer.amazon.com/alexa-skills-kit/alexa-skill-quick-start-tutorial) est très bien détaillé pour cet étape, et je vous propose de le suivre (step 1) pour la création du code de base.

Une fois votre fonction lambda créé, vous pouvez passer un peu de temps pour comprendre le code. Je prendrai un peu plus de temps dans un prochain article pour le détailler. Cette introduction est déjà beaucoup plus longue que ce que je souhaitais.

Ce code vie sur Lambda et est accessible via une adresse unique, l'**ARN** (voilà à quoi elle ressemble chez moi: `ARN - arn:aws:lambda:eu-west-1:309702694645:function:myColorSkill`).


Il vous faut finalement revenir sur votre compte Amazon Developer et renseigner la dernière section de votre skill en donnant l'adresse ARN pour qu'Alexa appelle cette fonction Lambda au bon moment.

## Test et conclusion

Si tout à bien marché jusqu'au bout, vous pourrez normalement tester votre fonction avec Echosim (rappelez-vous cet outil est relié à votre compte Amazon et donc votre skill, même en mode en test, vous est accessible).
Vous devez d'abord lancer votre application dans Alexa, pour cela, dites : `Alexa, open Color Picker`. Votre application sera lancée et vous donnera l'indication pour l'utiliser.

A vous de tester de modifier à l'envie.

Dans une deuxième partie, je traiterai plus en détail la logique de l'application, celle qui route vos commandes vocales et renvoie un résultat. N'hésitez pas à vous [inscrire à ma newsletter](http://eepurl.com/Argdf) pour recevoir l'annonce de l'article.



---

Credit : Teaser photo by Amazon
