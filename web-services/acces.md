---
title: acces
description: 
published: true
date: 2025-01-29T10:04:23.498Z
tags: 
editor: markdown
dateCreated: 2025-01-29T09:52:13.396Z
---

# Gestion des accès

Cette API permet de :

-   Modification du mot de passe => authentification,
-   Réinitialisation du mode de passe => authentification,
-   Gestion des autorisations aux fonctionnalités par utilisateur => autorisation.

## Modifier le mot de passe de l'utilisateur

```
post /restapi/auth/changePassword
```

Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

> Attention : le token n’est valable que 12 heures. Au-delà de ce délai, il faudra en générer un nouveau.

### Paramètres de la requête

| Nom                  |             | type   | Description                      |
| -------------------- | ----------- | ------ | -------------------------------- |
| actualPassword       | obligatoire | string | Mot de passe actuel              |
| newPassword          | obligatoire | string | Nouveau mot de passe             |
| newPasswordConfirmed | obligatoire | string | Nouveau mot de passe à confirmer |

### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Réinitialiser le mot de passe par l’envoi d’un email

```
post /restapi/auth/requestPasswordReset
```
Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

>Attention : le token n’est valable que 12 heures. Au-delà de ce délai, il faudra en générer un nouveau.

### Paramètres de la requête

| Nom | Description |
| --- | --- |
| login obligatoire | boolean  Login de l’utilisateur pour lequel il y a une demande de réinitialisation du mot de passe     |

### Réponses

## Trouve les droits/fonctionnalités à l'application pour un utilisateur

get /restapi/authorization/functionalities\_detailed

Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

Attention : le token n’est valable que 12 heures. Au-delà de ce délai, il faudra en générer un nouveau.

Ce web services permet de trouver tous les droits/fonctionnalités (avec un contenu détaillé) à l'application pour un utilisateur.

### Paramètres de la requête

| Nom | Description |
| --- | --- |
| elementType obligatoire | string - Enum  Type d’élément de l’application (Lien, Onglet, Web service, Action)     |

### Réponses

[](https://grav.new-media.ovh/web-services/acces#detail-fonctionnalites-utilisateur-res-object-200)

#### [**200** OK](https://grav.new-media.ovh/web-services/acces#detail-fonctionnalites-utilisateur-res-object-200)

[application/json;charset=utf-8](https://grav.new-media.ovh/web-services/acces#detail-fonctionnalites-utilisateur-res-object-200)

{

| enumCode | string  Code pour décrire la fonctionnalité   |
| --- | --- |
| fonctionnaliteDto  { | object |
| description | string  Description de la fonctionnalité   |
| idFonctionnalite | integer ($int32)  Identifiant unique de la fonctionnalité dans le système d’information Océan   |
| typeElement | string  Action/Onglets/Lien/Menu/WsAction/Onglets/Lien/Menu/Ws   |
| } |  |

}