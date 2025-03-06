---
title: Gestion des missions
description: 
published: true
date: 2025-01-24T15:05:20.256Z
tags: 
editor: markdown
dateCreated: 2024-12-05T13:02:09.334Z
---

# Gestion des missions

Cette API permet de :

-   Créer une nouvelle mission,
-   Modifier une mission en cours,
-   Retrouver le statut d’une mission,
-   Supprimer une mission.

Cette fonctionnalité n’est disponible que pour les clients ayant souscrit aux web services en complément d’une solution GéoPack ou GéoPro.

## Créer une nouvelle mission

 [Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/geomission/ajouterMissionUsingPOST)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
post /restapi/geomission/ajoutMission
```

#### Paramètres de la requête

| Nom             | Type               | Description                                                                                                          |
| --------------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId   *  | integer ($int64)   | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                      |
| idMission       | string             | Identifiant client de la mission                                                                                     |
| jourHeureInter  | string ($dateTime) | Date d'intervention, elle doit être au format UTC : "dd/MM/yyyy HH:mm". Seul ce format est pris en compte par notre API.                                   |
| jourHeurePeremp | string ($dateTime) | Date de suppression automatique de la mission sur l’écran, elle doit être au format UTC : "dd/MM/yyyyHH:mm". Seul ce format est pris en compte par notre API. |
| typeMission     | string             | Type de la mission                                                                                                   |
| nomVeh          | string             | Nom du véhicule                                                                                                      |
| nomIndi         | string             | Nom de l'individu (si aucun véhicule sélectionné, le destinataire cible est un individu avec nom prénom)             |
| prenomIndi      | string             | Prénom de l'individu (si aucun véhicule sélectionné, le destinataire cible est un individu avec nom prénom)          |
| nomPrenom       | string             | Nom et prénom de l'individu                                                                                          |
| commentaire     | string             | Commentaire de la mission                                                                                            |
| adrRefCli       | string             | Nom de l’adresse de référence client (tronquée à 20 caractères sur l’affichage site et écran)                        |
| rue             | string             | Rue de destination                                                                                                   |
| codPost         | string             | Code postal de destination                                                                                           |
| ville           | string             | Ville de destination                                                                                                 |
| aEnvoyer        | boolean            | TRUE si la mission est à envoyer   FALSE si la mission est seulement préparée                                        |
| longitude       | number ($double)   | Longitude de la destination                                                                                          |
| latitude        | number ($double)   | Latitude de la destination                                                                                           |

#### Réponses

```application/json;charset=utf-8
200 OK
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```JSON
{
  "message": "string"
  Message de retour du WS (succès/échec)
}
```

## Modifier une mission en cours

 [Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/geomission/modifierMissionUsingPOST)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
post /restapi/geomission/modifierMission
```

#### Paramètres de la requête

| Nom             | Type               | Description                                                                                                          |
| --------------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId *    | integer ($int64)   | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                      |
| idMission       | string             | Identifiant client de la mission                                                                                     |
| jourHeureInter  | string ($dateTime) | Date d'intervention, elle doit être au format UTC : "dd/MM/yyyy HH:mm". Seul ce format est pris en compte par notre API.                                |
| jourHeurePeremp | string ($dateTime) | Date de suppression automatique de la mission sur l’écran, elle doit être au format UTC : "dd/MM/yyyyHH:mm". Seul ce format est pris en compte par notre API. |
| typeMission     | string             | Type de la mission                                                                                                   |
| nomVeh          | string             | Nom du véhicule                                                                                                      |
| nomIndi         | string             | Nom de l'individu (si aucun véhicule sélectionné, le destinataire cible est un individu avec nom prénom)             |
| prenomIndi      | string             | Prénom de l'individu (si aucun véhicule sélectionné, le destinataire cible est un individu avec nom prénom)          |
| nomPrenom       | string             | Nom et prénom de l'individu                                                                                          |
| commentaire     | string             | Commentaire de la mission                                                                                            |
| adrRefCli       | string             | Nom de l’adresse de référence client (tronquée à 20 caractères sur l’affichage site et écran)                        |
| rue             | string             | Rue de destination                                                                                                   |
| codPost         | string             | Code postal de destination                                                                                           |
| ville           | string             | Ville de destination                                                                                                 |
| aEnvoyer        | boolean            | TRUE si la mission est à envoyer   FALSE si la mission est seulement préparée                                        |
| longitude       | number ($double)   | Longitude de la destination                                                                                          |
| latitude        | number ($double)   | Latitude de la destination                                                                                           |

#### Réponses

```application/json;charset=utf-8
200 OK
201 Created
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Résultat

```JSON
{
  "message": "string"
  Message de retour du WS (succès/échec)
}
```

## Retrouver le statut d’une mission

 [Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/geomission/getStatutMissionUsingGET)
 
[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
get /restapi/geomission/statutMission
```

#### Paramètres de la requête

| Nom         | Type   | Description                      |
| ----------- | ------ | -------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| idMission * | string | Identifiant client de la mission |
\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Résultat

```JSON
{
  "commentRefuseReason": "string",
  Raison de refus
  "complement": "string",
  Complément d’information
  "externalMissionId": "string",
  Identifiant technique de la mission
  "status": "string",
  Statut de la mission
  "statusCode": "string",
  Code statut de la mission
  "time": "string"
  Date de la mission
}
```


## Supprimer une mission

 [Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/geomission/supprimerMissionUsingPOST)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**
 
### Définition {.tabset}

#### Endpoint

```
post /restapi/geomission/supprimerMission
```

#### Paramètres de la requête

| Nom         | Type   | Description                      |
| ----------- | ------ | -------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| idMission * | string | Identifiant client de la mission |
\* paramètre obligatoire

#### Réponses

```application/json;charset=utf-8
200 OK
201 CREATED
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat
```
{
 "message": "string"
  Message de retour du WS (succès/échec)
}
```
