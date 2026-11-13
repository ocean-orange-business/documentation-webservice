---
title: Trips and Positions
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
* Normalized daily log for several vehicles over a given period (coming soon).



## Retrieve the positions of one or more vehicles between two dates : 

[Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/obtention-positions-vehicules/getTabPosVehUsingGET)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint

```
get /restapi/positions/search
```

#### #### Request Parameters

| Name                        | Type              | Description                                                                                                                                                                                                                                                                                                                     |
| --------------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId                  | integer ($int64)  | Customer identifier. Required only for a multi-customer user                                                                                                                                                                                                                                                                    |
| immatriculation             | array (of string) | List of vehicle registration numbers                                                                                                                                                                                                                                                                                            |
| startDate                   | string            | The start date in the most common ISO DateTime format 'yyyy-MM-dd'T'HH:mm:ss.SSSXXX' (example: "2000-10-30T01:30:00.000Z"). Must not be older than 2 months.<br>                                                                                                                                                                |
| endDate                     | string            | The end date in the most common ISO DateTime format 'yyyy-MM-dd'T'HH:mm:ss.SSSXXX' (example: "2000-10-30T01:30:00.000Z"). Must not be older than 2 months.                                                                                                                                                                      |
| byStorageDate               | boolean           | Allows searching positions based on storage timestamps rather than position timestamps                                                                                                                                                                                                                                          |
| withPrivacy                 | boolean           | Indicates whether positions should be returned in Privacy Mode. Default value = true                                                                                                                                                                                                                                            |
| addressEnrichmentDisable    | boolean           | If true, completely disables address enrichment (reverse geocoding).                                                                                                                                                                                                                                                            |
| addressEnrichmentEtatMobile | boolean           | \|   \|   \|<br>\|---\|---\|<br>\|Filter on mobile states for address enrichment. Accepts the following codes: STOPPED, STOP_ACTION, TRAVELING, WAITING, START_ACTION, ENGINE_UP, UNDEFINED, UNDEFINED_STATE, OUT_OF_ORDER, PRIVACY. Multiple values allowed (repeatable parameter). Default: no filter.\|   \| |
|                             |                   |                                                                                                                                                                                                                                                                                                                                 |

\* rmandatory parameter 


#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
429 Too Many Requests
```

#### Résultat

```JSON

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
#### Curl

```application/json;charset=utf-8
curl -X GET "https://v3.oceansystem.com/ocean/restapi/positions/search?immatriculation=AA-123-ZZ&startDate=2026-01-10T01%3A30%3A00.000Z&endDate=2026-01-17T01%3A30%3A00.000Z&byStorageDate=false&withPrivacy=false&addressEnrichmentDisabled=true" \
  -H "x-auth-token: <VOTRE_TOKEN>"
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

#### Curl

```JSON
curl -X GET "https://v3.oceansystem.com/ocean/restapi/positionsVehicles/betweenDate?immatsVeh=AA-123-ZZ&immatsVeh=BB-456-ZZ&login=<LOGIN>&password=<MOT_DE_PASSE>&dateDebut=01%2F11%2F2026+00%3A00%3A00+Z&dateFin=02%2F11%2F2026+00%3A00%3A00+Z&parDateStockage=false" \
  -H "x-auth-token: <VOTRE_TOKEN>"
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

#### Curl

```JSON
curl -X GET "https://v3.oceansystem.com/ocean/restapi/positionsVehicles/lastPosition?immatsVeh=AA-123-ZZ&immatsVeh=BB-456-ZZ&login=<LOGIN>&password=<MOT_DE_PASSE>" \
  -H "x-auth-token: <VOTRE_TOKEN>"
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

#### Curl

```JSON
curl -X GET "https://v3.oceansystem.com/ocean/restapi/mobility/v1/vehiclePositions?customerId=1110000000" \
  -H "x-auth-token: <VOTRE_TOKEN>"
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

#### Curl

```JSON
curl -X GET "https://v3.oceansystem.com/ocean/restapi/mobility/v1/trajet?customerId=1110000000&travelId=123456" \
  -H "x-auth-token: <VOTRE_TOKEN>"
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

#### Curl

```JSON
curl -X GET "https://v3.oceansystem.com/ocean/restapi/mobility/v1/ficheJour?customerId=1110000000&vehId=12345&date=03%2F11%2F2026" \
  -H "x-auth-token: <VOTRE_TOKEN>"
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

#### Curl

```JSON
curl -X GET "https://v3.oceansystem.com/ocean/restapi/materiel/positionBetween?customerId=1110000000&materielIds=2001&materielIds=2002&dateDebut=03%2F11%2F2026+00%3A00%3A00+Z&dateFin=03%2F11%2F2026+23%3A59%3A59+Z" \
  -H "x-auth-token: <VOTRE_TOKEN>"
```

## Retrieve the normalized daily report of vehicles for the given period

> ⚠️ **This web service is not yet available in production.** It will be available soon: until then, calls return `404 NOT FOUND`.

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

Unlike [the daily report of a vehicle](#retrieve-the-daily-report-of-a-vehicle-for-a-given-date), this version returns **one row per step** (`rows`). Repeated entities (entities, vehicles, drivers, POIs) are not duplicated in each row: they are moved to indexes (`entitiesById`, `vehiclesById`, `individusById`, `poisById`), and each row refers to them by identifier. Totals are not provided: they can be recomputed from the rows.

> The request is limited to **50 vehicles × days** (calendar days, bounds included). Example: 1 vehicle over 50 days, or 10 vehicles over 5 days. Beyond that, the API answers `400 BAD REQUEST`.
{.is-warning}

### Definition {.tabset}

#### Endpoint

```
post /restapi/vehicule_engin/v2/fichesJoursVehicules
```

#### Request Parameters

| Name         | Type             | Description                                       |
| ------------ | ---------------- | ------------------------------------------------- |
| customerId * | integer ($int64) | Client ID. Mandatory only for multi-client users. |

\* mandatory parameter

#### Request Body

```JSON
{
  "periode": {
    "debut": "2026-11-01T00:00:00.000Z",
    "fin": "2026-11-03T23:59:59.999Z"
  },
  "vehicleIds": [12345, 12346],
  "criteria": {
    "withDriver": true,
    "withPoi": true,
    "withAddress": true
  }
}
```

| Name          | Type            | Description                                                                                                                                                  |
| ------------- | --------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| periode *     | object          | Requested period. `debut` and `fin` are mandatory, in ISO-8601 format (e.g. `"2026-11-01T00:00:00.000Z"`) or as an epoch timestamp in milliseconds.         |
| vehicleIds *  | array (of int)  | Vehicle / equipment IDs. At least one ID, none null. The user must have rights on each of them.                                                              |
| criteria      | object          | Daily report criteria (optional). Optional row fields are only filled when the matching criterion is requested.                                              |

\* mandatory parameter

**Most useful criteria (`criteria`)**: all are booleans, `false` by default.

* `withDriver`: fills in the driver of each step (`individuId` and `individusById`).
* `withPoi`: fills in the closest POI to the start and end of the step (`startPoiId`, `endPoiId` and `poisById`).
* `withAddress`: fills in the start and end addresses (`startAddress`, `endAddress`).
* `withAffectationManuelle`: fills in manual and badge assignments (`affectation`).
* `withBadg`: fills in badge information (`ndidLong`).
* `withUnifiedEvent`: fills in the events of the step (`evenement`).
* `withRealConsumption`: fills in the real consumption (`consommation`).
* `withCapacity`: fills in the battery capacity (`capaciteBatterie`).
* `withChargeElectrique`: fills in the charging data of an electric vehicle (`chargeElectrique`).
* `withNoteEcoConduite`: computes an eco-driving score per trip (`ecoConduite`).
* `minDurationInSec` / `maxDurationInSec`: only keeps the steps whose duration is greater / lower than the given value (in seconds).

#### Responses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Result

```JSON
{
  "rows": [
    {
      "id": 0,
      "date": "string",
      "entityId": 0,
      "vehicleId": 0,
      "type": "T",
      "startTime": "string",
      "endTime": "string",
      "durationInSec": 0,
      "distanceInMeters": 0,
      "inProgress": false,
      "anomalyType": "NONE",
      "etatMobile": "string",
      "etapeSource": "string",
      "individuId": 0,
      "ndidLong": "string",
      "affectation": {},
      "startAddress": {
        "address": "string",
        "town": "string",
        "postCode": "string",
        "countryCode": 0,
        "precision": 0,
        "gpsCalle": true,
        "latitude": 0,
        "longitude": 0,
        "cap": 0
      },
      "endAddress": {
        "address": "string",
        "town": "string",
        "postCode": "string",
        "countryCode": 0,
        "precision": 0,
        "gpsCalle": true,
        "latitude": 0,
        "longitude": 0,
        "cap": 0
      },
      "startPoiId": 0,
      "endPoiId": 0,
      "evenement": {},
      "consommation": 0,
      "capaciteBatterie": {},
      "chargeElectrique": {},
      "startLevelValue": 0,
      "stopLevelValue": 0,
      "ecoConduite": {}
    }
  ],
  "entitiesById": {
    "0": {
      "id": 0,
      "nom": "string",
      "suppressionLogique": false
    }
  },
  "vehiclesById": {
    "0": {
      "id": 0,
      "categorie": "string",
      "description": "string",
      "geolocalise": true,
      "typeMotorisation": "string"
    }
  },
  "individusById": {
    "0": {
      "id": 0,
      "nomInd": "string",
      "prenomInd": "string",
      "matriculeInd": "string",
      "gsm": "string",
      "email": "string"
    }
  },
  "poisById": {
    "0": {
      "id": 0,
      "denominationPoi": "string",
      "adressePoi": "string",
      "codePostalPoi": "string",
      "villePoi": "string",
      "latPoi": 0,
      "longPoi": 0,
      "rayonPoi": 0
    }
  }
}
```

#### Curl

```JSON
curl -X POST "https://v3.oceansystem.com/ocean/restapi/vehicule_engin/v2/fichesJoursVehicules?customerId=1110000000" \
  -H "content-type: application/json" \
  -H "x-auth-token: <VOTRE_TOKEN>" \
  -d '{
    "periode": {
      "debut": "2026-11-01T00:00:00.000Z",
      "fin": "2026-11-03T23:59:59.999Z"
    },
    "vehicleIds": [12345, 12346],
    "criteria": {
      "withDriver": true,
      "withPoi": true,
      "withAddress": true
    }
  }'
```

**Description of the fields of a row (`rows`)**:

* `date`: day the step is attached to, in "dd/MM/yyyy" format.
* `entityId`, `vehicleId`, `individuId`, `startPoiId`, `endPoiId`: identifiers to resolve in `entitiesById`, `vehiclesById`, `individusById` and `poisById`.
* `type`: step type (trip, stop, …).
* `durationInSec` / `distanceInMeters`: duration of the step in seconds and distance travelled in meters.
* `inProgress`: `true` if the step is still in progress.
* `anomalyType`: time inconsistency of the step. It only concerns dates, never consumption or distance.
* The fields `individuId`, `ndidLong`, `affectation`, `startAddress`, `endAddress`, `startPoiId`, `endPoiId`, `evenement`, `consommation`, `capaciteBatterie`, `chargeElectrique`, `startLevelValue`, `stopLevelValue` and `ecoConduite` are absent from the response until the matching criterion has been requested.

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

#### Curl

```JSON
curl -X GET "https://v3.oceansystem.com/ocean/restapi/materiel/lastPosition?customerId=1110000000&materielIds=2001&materielIds=2002" \
  -H "x-auth-token: <VOTRE_TOKEN>"
```
