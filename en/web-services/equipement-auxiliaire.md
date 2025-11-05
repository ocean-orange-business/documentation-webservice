---
title: Auxiliary Equipment
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-24T13:16:13.661Z
---

# Auxiliary Equipment

This API allows you to retrieve:

- The total usage duration of auxiliary equipment by vehicle.

## Retrieve Total Usage Duration of Auxiliary Equipment by Vehicle

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/dioutilisation/getDureeUsingGET)

[Prior authentication required](./acces.md#authentication-via-post-request) and passing the token in the header **X-AUTH-TOKEN**

### Definition {.tabset}

#### Endpoint
```
get /restapi/dioUtilisation/duree
```

#### Request Parameters

| Name           | Type              | Description                                                                                                                   |
| -------------- | ----------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| customerId **  | integer ($int64)  | Customer identifier. Required for multi-client users                                                                         |
| vehIds         | array (of int)    | List of vehicle identifiers                                                                                                   |
| startDate      | string            | Start date of the period. Must be in UTC format: "dd/MM/yyyy". Only this format is accepted by our API.                    |
| endDate        | string            | End date of the period. Must be in UTC format: "dd/MM/yyyy". Only this format is accepted by our API.                      |

#### Responses

```application/json;charset=utf-8
200 OK
401 Unauthorized
403 Forbidden
404 Not Found
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
