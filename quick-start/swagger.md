---
title: swagger
description: 
published: true
date: 2025-01-29T10:02:32.988Z
tags: 
editor: markdown
dateCreated: 2025-01-29T10:01:55.990Z
---

# Swagger

### Quick Start

## 1\. S'authentifier

Avant d’accéder à tout service, une phase d’authentification est nécessaire sur le lien suivant :

```
/restapi/auth/authenticate2
```

![](authenticate2.jpg)

Pour s’authentifier, il suffit de :

1.  Dérouler le lien,
2.  Cliquer sur le bouton « Try it out » en haut à droite 
3.  Entrer votre login/password dans le champs "body" de la manière suivante:

![](authenticate2_2.jpg)

Ensuite pour valider l’authentification, il suffit de cliquer sur le bouton « Execute », en bas de l’écran.

Une fois l’authentification réussie, l’écran suivant apparait :

Les parties à considérer sont :

-   « **Curl** » : permet d’exécuter le service en utilisant directement la console sans passer par l’interface web
-   « **Response body** » : contient le token généré lors de l’invocation de ce service et qui peut aussi être généré en utilisant la commande ci-dessus.

## 2\. Ajouter l’extension "Modify header"

*Pour tester depuis votre navigateur*

Cette section explique comment exploiter le token généré pour continuer à utiliser nos web services depuis un navigateur.  
Tout d’abord, il est nécessaire de télécharger pour votre navigateur une extension du type « Modify header ».  
(Pour notre exemple, nous utiliserons le navigateur Firefox, dont le lien pour le téléchargement est : https://addons.mozilla.org/fr/firefox/addon/modify-headers/)  
Pour vérifier que le plugin a bien été ajouté au navigateur, cet icone doit apparaitre en haut à droite du navigateur.

![](quickStart-swagger-2-icon.png)

Une fois l’extension ajoutée, il faut cliquer sur « Open Modify Headers » et entrer les informations suivantes :

1.  « X-Auth-Token »
2.  le token récupéré précédemment.

![](quickStart-swagger-3-headers-notes.jpg)

*NB : après avoir entré une première fois ces paramètres, à chaque authentification ou après l’expiration du token, il est nécessaire de générer un nouveau token en se reconnectant et modifiant le header et cliquant sur « Edit ».*

## 3\. Construire une requête

Une requête à l‘API REST inclut l’élément basic figurant sur la table ci-dessous, et peut aussi contenir des paramètres spécifiques :

| Elément | Exemple/Valeur | Description |
| --- | --- | --- |
| **Url de base** | https://v3.oceansystem.com/ocean-3.0.0/apidocs | Environnement de production |
| **Url spécifique (extension de l’url de base)** | /restapi/materiel |  |
| **Resource** | /list/positionBetween | Spécifiez les détails de la demande via des paramètres de requête |
| **Format** | Formats supportés : • JSON |  |
| **Token** | &token={token} | Replacez votre propre unique token |
