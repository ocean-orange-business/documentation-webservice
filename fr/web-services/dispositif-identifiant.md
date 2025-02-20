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

Cette API permet d'affecter un dispositif identifiant / badge à un constructeur

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
