---
layout: post
title: "LessPass comment ça marche ?"
author: "Guillaume Vincent"
redirect_from:
  - /lesspass-comment-ça-marche-9f1201fffda5
---

Gérer ses mots de passe sur Internet ça n’a jamais été facile.
Vous utilisez certainement un gestionnaire de mots de passe pour vous aider.
Le système est simple, l’outil génère des mots de passe aléatoires à chaque fois que vous en avez besoin et les sauvegarde dans un fichier protégé par un mot de passe fort.

Ce système est très robuste, vous n’avez plus qu’à mémoriser un mot de passe pour les gouverner tous !
À vous des mots de passe uniques pour chaque site !

J’ai utilisé ce système pendant longtemps. Mais à chaque fois j’ai rencontré les problèmes suivant :

* comment synchroniser et partager ce fichier sur tous mes appareils.

* comment j’accède à un mot de passe sur l’ordinateur de mes parents sans installer mon gestionnaire de mot de passe.

* comment j’accède à un mot de passe sur mon téléphone.

Je suis donc parti en quête d’un système plus simple et j’ai créé LessPass.
> # L’objectif de LessPass est de supprimer des problèmes qui se posent avec d’autres solutions de gestion de mots de passe comme la synchronisation ou l’accès au code source.

L’astuce de LessPass réside dans le calcul de mots de passe plutôt que dans la génération aléatoire et le stockage.

**LessPass génère des mots de passe uniques pour les sites web, comptes de messagerie, ou toute autre chose à partir d’un mot de passe fort et d’informations connues de vous.**

LessPass est différent d’autres gestionnaire de mot de passe que vous pouvez trouver sur internet parce :

* il ne sauvegarde pas vos mots de passe dans une base de données

* il n’a pas besoin de synchroniser vos appareils entre eux

* il est open source (son code source peut être audité)

Le système utilise une [fonction pure](https://fr.wikipedia.org/wiki/Fonction_pure) c’est à dire qui retourne toujours la même valeur pour les mêmes arguments.

Vous lui fournissez 4 arguments (login, mot de passe fort, site et des options) et elle vous retourne votre mot de passe unique pour votre site.

![comment ça marche demo](../images/2016-10-19-how-does-it-works/HowItWorks.png)

Plus besoin de sauvegarder vos mots de passe dans un fichier chiffré. Vous avez juste besoin d’accéder à l’outil pour **recalculer** un mot de passe à partir d’informations que vous connaissez.

La génération du mot de passe doit rajouter du temps de calcul pour compliquer le cassage du mot de passe fort, notamment par brute force.
LessPass utilise PBKDF2 (abréviation de Password-Based Key Derivation Function 2) avec 100 000 itérations et une fonction de hashage sha-256.

Le hash généré par la première fonction est ensuite dérivé puis transformé pour que le mot de passe final corresponde aux options demandées (longueur, minuscules, majuscules, nombres, caractères spéciaux, etc ).

Le code source est disponible [ici](https://github.com/lesspass/lesspass), je vous invite à y jeter un oeil.

## Comment ça s’utilise :

Une image vaut mille mots :

![lesspass demo](../images/2016-10-19-how-does-it-works/demo.gif)

Si vous êtes sur votre téléphone ou sur l’ordinateur de vos parents, vous pouvez vous connecter à [https://lesspass.com/](https://lesspass.com/) rentrer votre login, mot de passe fort et le site et copier votre mot de passe en cliquant sur le bouton. Pas besoin de synchronisation.

## Et c’est disponible sur quel appareil ?

* Disponible sur [Android](https://play.google.com/store/apps/details?id=com.lesspass.android&hl=en)

* C’est disponible sur tous les navigateurs avec l’extension [Chrome](https://chrome.google.com/webstore/detail/lesspass/lcmbpoclaodbgkbjafnkbbinogcbnjih) ou l’extension [Firefox](https://addons.mozilla.org/en-US/firefox/addon/lesspass/).

* Directement sur le site [https://lesspass.com](https://lesspass.com)

## Comment je gère mes mots de passe complexe ?

Il arrive que certains sites aient des règles de mot de passe particulières. Certaines banques par exemple n’acceptent que des mots de passe avec des chiffres. Il faut donc à la fois mémoriser un mot de passe fort et mémoriser, les caractéristiques du mot de passe. Nous avons construit une version connecté qui enregistre les profils de mot de passe (seulement les profils).

Un profil ressemble à ça

    {
        "login": "38491092",
        "site": "www.ingdirect.fr",
        "lowercase": false,
        "uppercase": false,
        "symbols": false,
        "numbers": true,
        "counter": 1,
        "length": 6
    }

Cela permet en se connectant de charger le profil simplement :

![LessPass connecté pour les profils complexes à mémoriser](../images/2016-10-19-how-does-it-works/demo-lesspass-connected.gif)*LessPass connecté pour les profils complexes à mémoriser*

## Auto hébergement

Vous pouvez héberger votre propre base de données LessPass si vous ne voulez pas utiliser celle fournie par LessPass. Il vous faut docker et docker-compose d’installé sur votre machine.

Si vous êtes intéressé, allez voir la documentation sur [github](https://github.com/lesspass/lesspass).

## Comment je change un mot de passe sans changer mon mot de passe fort ?

Vous pouvez changer de mot de passe fort en incrémentant le compteur dans les options du mot de passe.


## L’idée est géniale, comment je peux contribuer ?

* Vous êtes scientifique, aidez-nous à réaliser un livre blanc.

* Participer à l’amélioration du [code source](https://github.com/lesspass/lesspass).

* Mettez une note sur les extensions navigateurs

* Mettez une étoile sur [github](https://github.com/lesspass/lesspass)

## Road Map

* Chiffrement des profils coté client

* Livre blanc

## Culture

LessPass est open source (licence GPLv3), nous nous refusons d’installer des mouchards, outils d’analyses sur nos applications (il n’y a aucun Google Analytics, ou liens vers des services externes sur nos outils).
Nous hébergeons notre code sur des serveurs [Vultr](http://www.vultr.com/?ref=6830452) et nos DNS sont gérés par [Gandi](https://www.gandi.net/).

Notre aimons beaucoup l’idée d’une culture ouverte. Tous les bugs que nous trouvons sont visibles de tous le monde. Nous documentons nos algorithmes et notre façon de faire. Pas de magie ou de boite noire.
Nous sommes très friand de vos retours, vos idées pour améliorer l’outil. Nous sommes conscient de certaines limitations (changement du mot de passe fort par exemple) mais nous travaillons à améliorer le produit.

Nous ne sommes sponsorisé par aucune entreprise, le développement de LessPass se fait pendant notre temps libre. Si vous avez des remarques ou des questions, n’hésitez pas à nous envoyez un email à **contact@lesspass.com**

J’en profite pour remercier Édouard pour tout le travail sur l’expérience utilisateur et les nombreux retours sur le produit !
