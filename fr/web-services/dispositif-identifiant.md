---
title: Gestion des dispositifs identifiants
description: 
published: true
date: 2024-12-18T16:09:00.000Z
tags: 
editor: markdown
dateCreated: 2024-12-13T13:40:00.000Z
---

# Gestion des dispositifs identifiants

Cette API permet de :
- Affecter un dispositif identifiant / badge à un constructeur
- Récupérer la liste des dispositifs identifiants avec les affectations

## Affecter un dispositif identifiant/badge à un conducteur

Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
post /restapi/dispositifIdentifiant/affectation/create-affectation
```
#### Paramètres de la requête
| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId*    | integer ($int64) | Obligatoire seulement pour un utilisateur multi clients.       |
| personId*      | integer ($int64) | Identifiant de l'individu                                      |
| identifierId*  | integer ($int64) | Identifiant du dispositif                                      |
| date_debut *   | date             | La date de début au format “yyyy-MM-ddTHH:mm:ss.SSSZ”          |
| date_fin      | date             | La date de fin au format “yyyy-MM-ddTHH:mm:ss.SSSZ”            |

\* paramètre mandataire

#### Corps de la requête
```JSON
{
    "identifierId": 0,
    "personId": 0,
    "period": {
        "debut": "yyyy-MM-ddTHH:mm:ss.SSSZ",
        "fin": "yyyy-MM-ddTHH:mm:ss.SSSZ",
    }
}
```
#### Réponses
```application/json;charset=utf-8
200 OK
201 CREATED
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Récupérer la liste des dispositifs identifiants avec les affectations

Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/dispositifIdentifiant/list-identifiants
```
#### Paramètres de la requête
| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId*    | integer ($int64) | Obligatoire seulement pour un utilisateur multi clients.       |
| individuIds    | Array of integer | Liste d’ids d’individus dont on veut les dispositifs identifiants |

\* paramètre mandataire

#### Corps de la requête
```JSON
[
  {
    "autoPartageBadgeRFID": {
      "admin": true,
      "id": 0
    },
    "dispositifIdentifiant": {
      "color": 0,
      "id": 0,
      "idClient": 0,
      "idTypeDispositifIdentifiant": 0,
      "numeroCleClient": 0,
      "numeroCompletDid": "string",
      "numeroDid": "string"
    },
    "entity": {
      "id": 0,
      "nom": "string",
      "suppressionLogique": true
    },
    "groupe": {
      "descriptionGrp": "string",
      "id": 0,
      "suppressionLogique": true
    },
    "individu": {
      "email": "string",
      "gsm": "string",
      "id": 0,
      "idCivilite": 0,
      "initialesInd": "string",
      "matriculeInd": "string",
      "nomInd": "string",
      "prenomInd": "string",
      "suppressionLogique": true
    }
  }
]
```
#### Réponses
```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```
