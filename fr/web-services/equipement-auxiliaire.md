---
title: Equipement auxiliaire
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-24T13:16:13.661Z
---

# Equipement auxiliaire

Cette API permet de récupérer :

- La durée totale d’utilisation des équipements auxiliaires par engin.

## Récupérer la durée totale d’utilisation des équipements auxiliaires par engin

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/dioutilisation/getDureeUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/dioUtilisation/duree
```

#### Paramètres de la requête

| Nom           | Type              | Description                                                                                                                   |
| ------------- | ----------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| customerId ** | integer ($int64)  | Identifiant du client. Obligatoire pour un utilisateur multi-client                                                           |
| vehIds        | array (of int)    | Liste des identifiants des véhicules                                                                                          |
| startDate     | string            | La date de début de la période. Elle doit être au format UTC : “dd/MM/yyyy”. Seul ce format est pris en compte par notre API. |
| endDate       | string            | La date de fin de la période. Elle doit être au format UTC : “dd/MM/yyyy”. Seul ce format est pris en compte par notre API.   |
| includeFields | array (of string) | Champs à inclure (cf. Facebook Graph API)                                                                                     |

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```JSON
[
  {
    "dailyDioUtilisation": [
      {
        "dailyDurationSecForAllDio": 0,
        "day": "string",
        "dayTotalUsePerEquipement": {
          "additionalProp1": 0,
          "additionalProp2": 0,
          "additionalProp3": 0
        },
        "usePerHalfHour": [
          {
            "end": "string",
            "libelleEquipement": "string",
            "start": "string",
            "useDuration": 0
          }
        ]
      }
    ],
    "durationSecForAllDio": 0,
    "totalUsePerEquipementForPeriod": {
      "additionalProp1": 0,
      "additionalProp2": 0,
      "additionalProp3": 0
    },
    "vehicle": {
      "categorie": "UNDEFINED",
      "description": "string",
      "detectionPorteEnabled": true,
      "dioEnabled": true,
      "dispositifIdentifiant": true,
      "geolocalise": true,
      "geosecuriteEnabled": true,
      "id": 0,
      "immobilisationCablee": true,
      "libelleTypeAsset": {
        "categorie": "UNDEFINED",
        "id": 0,
        "libelle": "string",
        "nomIcone": "string",
        "ordre": 0
      },
      "nomImage": "string",
      "odirectMode": "ODIRECT_UNIVERSEL",
      "privacyEnabled": true,
      "suppressionLogique": true,
      "typeMotorisation": "MONO"
    }
  }
]
```
