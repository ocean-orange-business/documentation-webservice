---
title: trajets-et-positions
description: 
published: true
date: 2025-01-15T14:31:29.466Z
tags: 
editor: markdown
dateCreated: 2024-12-05T13:02:16.432Z
---

# Trips and Positions

This API allows retrieval of:

* Daily trips made for professional purposes for vehicles.
* Positions of all vehicles authorized for the user.
* Last positions of vehicles/equipment.
* Positions of vehicles/equipment between two dates.
* Daily log for a vehicle for a given date.



## Retrieve the positions of one or more vehicles between two dates : 

[Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/obtention-positions-vehicules/getTabPosVehUsingGET)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint

```
get /restapi/positions/search
```

#### Request Parameters


|| Name            | Type              | Description                                                                                                                      |
|------------------|-------------------|----------------------------------------------------------------------------------------------------------------------------------|
| byStorageDate    | boolean           | Allows searching positions based on storage timestamps instead of position timestamps.                                           |
| customerId       | integer ($int64)  | Client ID. Mandatory only for multi-client users.                                                                                |
| endDate          | string            | End date in UTC format: "dd/MM/yyyy HH:mm:ss Z". Only this format is accepted by the API.                                        |
| immatriculation  | array (of string) | List of vehicle registrations.                                                                                                   |
| startDate        | string            | Start date in ISO DateTime format: 'yyyy-MM-dd'T'HH:mm:ss.SSSXXX' (e.g., "2000-10-30T01:30:00.000Z"). Must not be older than 2 months. |
| withPrivacy      | boolean           | Indicates if positions should be returned in VP (privacy mode). Default value = true.                                                                                             |

* mandatory parameter


#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```JSON
{
  "positionsVehicles": [
    {
      "positions": [
        {
          "address": {
            "address": "string",
            "country": "string",
            "postalCode": "string",
            "town": "string"
          },
          "adresseDeReference": "string",
          "approximationMeter": 0,
          "cap": 0,
          "chauffeur": "string",
          "consommationThermiqueL": 0,
          "date": "string",
          "distanceDepuisPosPrecMeter": 0,
          "etat": "string",
          "initialesChauffeur": "string",
          "latitudeY": 0,
          "longitudeX": 0,
          "matriculeChauffeur": "string",
          "typePoi": "string",
          "vitesseKmh": 0
        }
      ],
      "vehicle": {
        "descriptionVehicule": "string",
        "idVehicule": 0,
        "immatriculation": "string",
        "typeMotorisationEnergie": "MONO_ELECTRIQUE"
      }
    }
  ]
}
```

## Retrieve the positions of one or more vehicles between two dates

[Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/obtention-positions-vehicules/getTabPosVehUsingGET)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

> Outdated version
{.is-warning}

### Definition {.tabset}

#### Endpoint

```
get /restapi/positionsVehicles/betweenDate
```

#### Request Parameters

| Name             | Type              | Description                                                                                                                  |
| ---------------- | ----------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| immatsVeh        | array (of string) | List of vehicle registrations.                                                                                               |
| login *          | string            | User identifier.                                                                                                             |
| password *       | string            | Password.                                                                                                                    |
| dateDebut        | string            | Start date in UTC format: "dd/MM/yyyy HH:mm:ss Z". Must not be older than 2 months.                                          |
| dateFin          | string            | End date in UTC format: "dd/MM/yyyy HH:mm:ss Z".                                                                             |
| parDateStockage  | boolean           | If **true**, the method retrieves positions based on the timestamps of the positions.                                        |

\* mandatory parameter 

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```JSON
{
  "positionsVehicles": [
    {
      "positions": [
        {
          "address": {
            "address": "string",
            "country": "string",
            "postalCode": "string",
            "town": "string"
          },
          "adresseDeReference": "string",
          "approximationMeter": 0,
          "cap": 0,
          "chauffeur": "string",
          "consommationThermiqueL": 0,
          "date": "string",
          "distanceDepuisPosPrecMeter": 0,
          "etat": "string",
          "initialesChauffeur": "string",
          "latitudeY": 0,
          "longitudeX": 0,
          "matriculeChauffeur": "string",
          "typePoi": "string",
          "vitesseKmh": 0
        }
      ],
      "vehicle": {
        "descriptionVehicule": "string",
        "idVehicule": 0,
        "immatriculation": "string",
        "typeMotorisationEnergie": "MONO_ELECTRIQUE"
      }
    }
  ]
}
```

## Retrieve the last position of one or more vehicles

[Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/obtention-positions-vehicules/getPosAndStatusVehUsingGET)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

> Outdated version
{.is-warning}

### Definition {.tabset}

#### Endpoint
```
get /restapi/positionsVehicles/lastPosition
```

#### Request Parameters


| Name        | Type              | Description                                                                                   |
| ----------- | ----------------- | --------------------------------------------------------------------------------------------- |
| immatsVeh   | array (of string) | List of vehicle registrations (maximum 50).                                                   |
| login *     | string            | User identifier.                                                                              |
| password *  | string            | Password.                                                                                     |

\* mandatory parameter 

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Retrieve all vehicles authorized for the user along with their positions

[Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/mobility/getPositionsVehiclesUsingGET)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint
```
get /restapi/mobility/v1/vehiclePositions
```

#### Request Parameters

| Name          | Type             | Description                                                                     |
| ------------- | ---------------- | ------------------------------------------------------------------------------- |
| customerId *  | integer ($int64) | Client ID. Mandatory only for multi-client users.                               |

\* mandatory parameter 

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat
```JSON
{
  "vehicles": [
    {
      "description": "string",
      "entityName": "string",
      "etatImmobilisation": "LOCKED",
      "genre": "string",
      "geolocalise": true,
      "id": "string",
      "immat": "string",
      "marque": "string",
      "modele": "string",
      "nomImage": "string",
      "position": {
        "cap": 0,
        "date": "string",
        "driver": {
          "matricule": "string",
          "nom": "string",
          "prenom": "string",
          "tel": "string"
        },
        "etat": "string",
        "fullAddress": {
          "address": "string",
          "country": "string",
          "postalCode": "string",
          "town": "string"
        },
        "gpsCale": true,
        "heure": "string",
        "latitudeY": 0,
        "longitudeX": 0,
        "poi": {
          "couleurHTML": "string",
          "nom": "string",
          "nomType": "string"
        }
      }
    }
  ]
}
```

## Retrieve the route of a vehicle.

[Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/mobility/getTrajetUsingGET)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint
```
get /restapi/mobility/v1/trajet
```

#### Request Parameters


| Name         | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Client ID. Mandatory only for multi-client users.                               |
| travelId *   | integer ($int64) | Vehicle travel ID.                                                              |

\* mandatory parameter 

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat
```JSON
{
  "positions": [
    {
      "idPos": 0,
      "latitude": 0,
      "longitude": 0
    }
  ]
}
```

## Retrieve the daily report of a vehicle for a given date.

[Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/mobility/getFicheJourUsingGET)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint

```
get /restapi/mobility/v1/ficheJour
```

#### Request Parameters

| Name         | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Client ID. Mandatory only for multi-client users.                               |
| vehId        | integer ($int64) | Vehicle ID for which the daily report is retrieved.                             |
| date         | string           | Date in UTC format: "dd/MM/yyyy". Only this format is accepted by the API.      |

\* mandatory parameter 

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat
```JSON
{
  "fjRows": [
    {
      "anomalyType": "NONE",
      "distanceMeter": 0,
      "dureeMs": 0,
      "id": 0,
      "posDeb": {
        "cap": 0,
        "date": "string",
        "driver": {
          "matricule": "string",
          "nom": "string",
          "prenom": "string",
          "tel": "string"
        },
        "etat": "string",
        "fullAddress": {
          "address": "string",
          "country": "string",
          "postalCode": "string",
          "town": "string"
        },
        "gpsCale": true,
        "heure": "string",
        "latitudeY": 0,
        "longitudeX": 0,
        "poi": {
          "couleurHTML": "string",
          "nom": "string",
          "nomType": "string"
        }
      },
      "posFin": {
        "cap": 0,
        "date": "string",
        "driver": {
          "matricule": "string",
          "nom": "string",
          "prenom": "string",
          "tel": "string"
        },
        "etat": "string",       
        "fullAddress": {
          "address": "string",
          "country": "string",
          "postalCode": "string",
          "town": "string"
        },
        "gpsCale": true,
        "heure": "string",
        "latitudeY": 0,
        "longitudeX": 0,
        "poi": {
          "couleurHTML": "string",
          "nom": "string",
          "nomType": "string"
        }
      },
      "type": "T"
    }
  ]
}
*Possible values for the field `etat` :  « start D » / « waiting T » / « traveling R » / « stop A»

```

## Récupérer les positions d'un ou plusieurs matériels entre deux dates

[Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/materiel/getMaterielPosBetweenDateUsingGET)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint

```
get /restapi/materiel/positionBetween
```

#### Request Parameters

| Name          | Type           | Description                                                                                                                                                |
| ------------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId *  | integer ($int64) | Client ID. Mandatory only for multi-client users.                                                                                                        |
| materielIds   | array (of int)  | List of equipment IDs (unlimited number).                                                                                                                 |
| dateDebut     | string         | Start date in UTC format: "dd/MM/yyyy HH:mm:ss Z". Only this format is accepted by the API.                                                                |
| dateFin       | string         | End date in UTC format: "dd/MM/yyyy HH:mm:ss Z". Only this format is accepted by the API. The period must not exceed 1 day.                                |

\* mandatory parameter


#### Responses

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
    "materiel": {
      "boxCapabilities": [
        "SEND_BATTERIE_FAIBLE"
      ],
      "boxLightDTO": {
        "id": 0,
        "numeroSerieBoi": "string"
      },
      "commandeDTO": {
        "commentaire": "string",
        "id": 0,
        "numero": "string",
        "quantite": 0
      },
      "entiteLightDTO": {
        "id": 0,
        "nom": "string",
        "suppressionLogique": true
      },
      "materiel": {
        "description": "string",
        "id": 0,
        "marque": "string",
        "modele": "string",
        "reference": "string"
      },
      "proprietesSpecifiquesDTO": {
        "id": 0,
        "idClient": 0,
        "idObjetRef": 0,
        "typeObjet": "CLIENT"
      },
      "trameDTO": {
        "id": 0,
        "reason": "string",
        "scenarioDTO": {
          "code": "string",
          "i18nKey": "string",
          "id": 0
        },
        "stateBoitier": true
      }
    },
    "positions": [
      {
        "address": "string",
        "cap": 0,
        "closestPoi": {
          "adressePoi": "string",
          "codePostalPoi": "string",
          "complementAdresse1Poi": "string",
          "complementAdresse2Poi": "string",
          "denominationPoi": "string",
          "groupePoi": {
            "id": 0,
            "libelle": "string"
          },
          "id": 0,
          "idPays": 0,
          "latPoi": 0,
          "libelleTypePoi": {
            "color": "string",
            "i18nKey": "string",
            "id": 0,
            "libelle": "string",
            "nomImage": "string",
            "ordre": 0,
            "type": "UNDEFINED"
          },
          "longPoi": 0,
          "rayonPoi": 0,
          "suppressionLogique": true,
          "villePoi": "string"
        },
        "codeExploitant": "string",
        "countryCode": 0,
        "gmtPosFormat": "string",
        "gpsCalle": true,
        "idEtatMobile": 0,
        "idPositionGeo": 0,
        "latitude": 0,
        "latitudeYPos": 0,
        "longitude": 0,
        "longitudeXPos": 0,
        "numeroEmbarquePos": 0,
        "postCode": "string",
        "precision": 0,
        "town": "string"
      }
    ]
  }
]
```

## Retrieve the last position of one or more pieces of equipment.

[Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/materiel/getMaterialLastPositionUsingGET)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

> Outdated version
{.is-warning}

### Definition {.tabset}

#### Endpoint

```
get /restapi/materiel/lastPosition
```

#### Request Parameters

| Name          | Type           | Description                                                                 |
| ------------- | -------------- | --------------------------------------------------------------------------- |
| customerId *  | integer ($int64) | Client ID. Mandatory only for multi-client users.                          |
| materielIds   | array (of int)  | List of equipment IDs (unlimited number).                                  |

\* mandatory parameter

#### Responses

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
    "materiel": {
      "boxCapabilities": [
        "SEND_BATTERIE_FAIBLE"
      ],
      "boxLightDTO": {
        "id": 0,
        "numeroSerieBoi": "string"
      },
      "commandeDTO": {
        "commentaire": "string",
        "id": 0,
        "numero": "string",
        "quantite": 0
      },
      "entiteLightDTO": {
        "id": 0,
        "nom": "string",
        "suppressionLogique": true
      },
      "materiel": {
        "description": "string",
        "id": 0,
        "marque": "string",
        "modele": "string",
        "reference": "string"
      },
      "proprietesSpecifiquesDTO": {
        "id": 0,
        "idClient": 0,
        "idObjetRef": 0,
        "typeObjet": "CLIENT"
      },
      "trameDTO": {
        "id": 0,
        "reason": "string",
        "scenarioDTO": {
          "code": "string",
          "i18nKey": "string",
          "id": 0
        },
        "stateBoitier": true
      }
    },
    "positions": [
      {
        "address": "string",
        "cap": 0,
        "closestPoi": {
          "adressePoi": "string",
          "codePostalPoi": "string",
          "complementAdresse1Poi": "string",
          "complementAdresse2Poi": "string",
          "denominationPoi": "string",
          "groupePoi": {
            "id": 0,
            "libelle": "string"
          },
          "id": 0,
          "idPays": 0,
          "latPoi": 0,
          "libelleTypePoi": {
            "color": "string",
            "i18nKey": "string",
            "id": 0,
            "libelle": "string",
            "nomImage": "string",
            "ordre": 0,
            "type": "UNDEFINED"
          },
          "longPoi": 0,
          "rayonPoi": 0,
          "suppressionLogique": true,
          "villePoi": "string"
        },
        "codeExploitant": "string",
        "countryCode": 0,
        "gmtPosFormat": "string",
        "gpsCalle": true,
        "idEtatMobile": 0,
        "idPositionGeo": 0,
        "latitude": 0,
        "latitudeYPos": 0,
        "longitude": 0,
        "longitudeXPos": 0,
        "numeroEmbarquePos": 0,
        "postCode": "string",
        "precision": 0,
        "town": "string"
      }
    ]
  }
]
```
