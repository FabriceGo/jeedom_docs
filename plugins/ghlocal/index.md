# Google Home Local

## Présentation

Ce plugin a pour but de gérer vos Google Home et par extension vos Chromecast.

Le plugin permet d'envoyer des médias vers vos Google Home et Chromecast, qu'ils soient locaux, distant, ou des rapports jeedom ou bien encore consulter un site pour les écrans.

Pour les Google Home, il permet aussi de récupérer les alarmes et timers, l'activation du mode silencieux, le scan bluetooth

## Configuration

Le plugin dispose d'une page de configuration pour entrer un token d'authentification.

Pour trouver ce token : https://gist.github.com/rithvikvibhu/1a0f4937af957ef6a78453e3be482c1f

Pour chaque équipement créé manuellement, il faut indiquer si c'est un Google Home ou Chromecast, ainsi que son IP.

Les périphériques Bluetooth sont créés automatiquement.

Les commandes sont créées automatiquement dans tous les cas.

## Commandes

Les commandes suivantes sont communes aux Google Home et Chromecast (car elles utilisent la fonctionnalité Chromecast du Google Home) :

Stop lecture : arrête toute lecture en cours

Pause lecture : met en pause la lecture en cours

Reprise lecture : reprend la lecture en cours

Définir volume lecture : règle le volume des medias en %

Jouer un Fichier : permet de lancer un média supporté par le GH/Chromecast (audio sur tout, pour ce qui dispose d'un écran ca peut être une image ou vidéo).

Ouvrir une URL : permet d'afficher un site sur un GH/Chromecast avec écran (ou lire une vidéo youtube)

Commande Scénario : est prévue pour être utilisée en scénario sur les commandes report et notification de caméra

Radio : permet de lire une des radios, c'est une commande de type select avec une liste prédéfinie

Sons locaux : permet de lire un des sons présents dans le plugin (des sons de notification). Le plugin propose un modal permettant de gérer les fichiers.


Les Google Home ont des commandes spécifiques qui s'appuient sur leur API local non officielle :

Alarmes informations brutes : présente un json des informations sur les alarmes définies sur le GH

Alarme existante : info binaire indiquant si au moins une alarme existe

Alarme existante ce jour : info binaire indiquant si la prochaine alarme est ajourd'hui

Heure de la prochaine Alarme : heure au format Jeedom (pour l'utiliser avec un scénario et en condition "A ...." par exemple) de l'alarme

Timers informations brutes : présente un json des informations sur les timers définies sur le GH

Timer existant : info binaire indiquant si au moins un timer existe

Durée original du timer (en mn) : durée d'origine du compte à rebours

Heure du prochain Timer : heure au format Jeedom (pour l'utiliser avec un scénario et en condition "A ...." par exemple) du timer

Volume Alarmes (avec Définir Volume Alarme) : volume spécifique des alarmes

Etat Notification (avec Notification On, Notification Off) : commandes gérant et indiquant le mode DND (Do Not Disturb)

Rafraichir : standard Jeedom

Redémarrer : pour redémarrer votre GH


Et les périphériques Bluetooth scannés par au moins une GH se voient dotés d'une commande RSSI par Google Home à portée. On peut ainsi obtenir le RSSI relatif d'un objet bluetooth par rapport à plusieurs points correspondant aux GH. Une commande générale "Visible" est positive (1) si au moins un des Google Home trouve le périphérique dans les 5mn passées, elle est nulle si aucun Google Home ne le détecte dans les 5 dernière minutes.

## FAQ

> Est-ce que le plugin s'appuie sur des API tiers ?

Il s'appuie sur les API de votre Google Home. C'est donc sur le réseau local.

> Quels formats sont supportés ?

Pour les fichiers il s'agit de MP3, MP4, PNG. Plus les URL de site et Youtube.

> Quelle est la fréquence des informations sur les GH ?

Toutes les 5mn par défaut (voir le tableau des cron utilisés par le plugin sur la page de configuration générale plugin)

## Changelog

[Voir la page dédiée](changelog.md).
