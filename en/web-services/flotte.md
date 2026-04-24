---
title: Fleet Management
description:
published: true
date: 2024-10-31T15:22:25.027Z
tags:
editor: markdown
dateCreated: 2024-10-31T15:22:21.849Z
---
# Fleet Management

This API allows you to retrieve:

- Vehicle record information (name, registration, make, model, category, device serial number, odometer reading (once per day), driver identity, …),
- Equipment record information (name, reference, make, model, operating scenario, configured message for button press, beacon serial number, …),
- Latest events (for vehicles and equipment),
- Customer entities.
- Driver assignments and their history

## Retrieve customer entities

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/mobility/getEntitiesUsingGET)

[Prior authentication required](./acces.md#authentification-par-requête-post) and token must be passed in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint
```
get /restapi/mobility/v1/entities
```

#### Request Parameters

| Name         | Type             | Description                                                                  |
| ------------ | ---------------- | ---------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Customer identifier. Required only for a multi-customer user                 |

\* required parameter 

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Result

```json
{
  "entities": [
    {
      "id": 0,
      Entity identifier
      "nom": "string"
      Entity name
    }
  ]
}
```

## Retrieve vehicle data

[Prior authentication required](./acces.md#authentification-par-requête-post) and token must be passed in the **X-AUTH-TOKEN** header
 [Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/vehiculeengin/getVehiclesUsingGET)
### Definition {.tabset}

#### Endpoint
```
get /restapi/vehicule_engin/vehicles
```

#### Request Parameters

| Name            | Type             | Description                               |
| --------------- | ---------------- | ----------------------------------------- |
| customerId *    | integer ($int64) | Customer identifier. Required only for a multi-customer user                                                                           |
| immatriculation | string           | Vehicle registration number               |
| includeFields   | Array of string  | Fields to include (see Facebook Graph API) |

\* required parameter

#### Responses

```application/json;charset=utf-8
200 OK
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Result

```JSON
[
  {
    "boitier": {
      "adBoi": "string",
      Device ad (APC for BBOXv1 obsolete) (50)
      "commentaireBoi": "string",
  		Device comment
      "coreGsmBoi": "string",
  		Device GSM number
      "debutGarantie": "2024-12-17T16:14:51.577Z",
  		Device warranty start date
      "finGarantie": "2024-12-17T16:14:51.577Z",
  		Device warranty end date
      "id": 0,
      Device identifier
      "idEtatBoitier": 0,
      Device status identifier
      "imeiBoi": "string",
      Device IMEI (15)
      "numeroSerieBoi": "string",
      Device serial number (50)
      "sn": "string"
      Device SN (Serial Number) (30)
    },
    "chauffeur": {
      "email": "string",
      Driver email
      "gsm": "string",
      Driver phone number
      "id": 0,
      Driver identifier
      "idCivilite": 0,
      Title identifier
      "initialesInd": "string",
      "matriculeInd": "string",
      Driver employee number
      "nomInd": "string",
      Driver last name
      "prenomInd": "string",
      Driver first name
      "suppressionLogique": true
    },
    "emissionCo2": 0,
    CO2 emission rate
    "entite": {
      "id": 0,
      Entity identifier
      "nom": "string",
      Entity name (150)
      "suppressionLogique": true
    },
    "releve": {
      "dateReleve": "2024-12-17T16:14:51.577Z",
      Odometer reading date
      "id": 0,      
      Reading identifier
      "value": 0
      Odometer reading value 
      at the end of the previous day (value calculated at midnight)
    },
    "releveAjuste": {
      "dateReleve": "2024-12-17T16:14:51.577Z",
      Adjusted odometer reading date 
      "id": 0,
      Reading identifier
      "value": 0
      Odometer value adjusted based on the distance 
      or time traveled by the vehicle since the last automatic reading
    },
    "vehicle": {
      "apcMode": "GPS",
      "boitierAvantCoupeCircuit": true,
      "buzzerSurvitesseEnabled": true,
      "categorie": "UNDEFINED",
      Vehicle category
      "categorieVehiculeEcoConduite": "UL",
      "couleur": "string",
      Vehicle color (50)
      "coupeBatterie": true,
      "date1ereMec": "2024-12-17T16:14:51.577Z",
      "description": "string",
			Vehicle description
      "detectionPorteEnabled": true,
      "dioEnabled": true,
			Data on a device input/output yes/no (auxiliary engine, ...)
      "dispositifIdentifiant": true,	
			Identifying device status (yes/no)
      "emissionCo2": 0,
      "etatEcoConduite": "ACTIF",
      "geolocalise": true,
      "geomissionEnabled": true,
			Geomission activation (yes/no)
      "geosecuriteEnabled": true,
			Geosecurity activation (yes/no)
      "id": 0,
      "idEnergie": 0,
      "idModeDeplacement": 0,
      "idUniteConsommation": 0,
      "immatriculation": "string",
      "immobilisationCablee": true,
      "libelleTypeAsset": {
        "categorie": "UNDEFINED",
        "id": 0,
        "libelle": "string",
        "nomIcone": "string",
        "ordre": 0
      },
      "marque": "string",
			Vehicle make
      "modele": "string",
			Vehicle model
      "nomImage": "string",
      "nombreCvFiscaux": 0,
      "numeroEmbarque": 0,
      "numeroParc": "string",
      "numeroSerie": "string",
			Vehicle serial number
      "odirectMode": "ODIRECT_UNIVERSEL",
			O-Direct mode Renault/Peugeot/Kuantic, …
      "privacyEnabled": true,
      "Privacy Mode" enabled
      "prk": 0,
      "signesDistinctifs": "string",
      "suppressionLogique": true,
      "typeMotorisation": "MONO",
      "valeurConsommation": 0,
      "vin": "string"
    },
    "visites": [
      {
        "compteurPrevu": 0,
        "datePrevue": "2024-12-17T16:14:51.577Z",
        "description": "string",
        "idVisiteEntretien": 0
      }
    ]
  }
]
```

## Retrieve an assignment (by its id)

[Prior authentication required](./acces.md#authentification-par-requête-post) and token must be passed in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint
```
get /affectations_chauffeurs/get
```

#### Request Parameters

| Name          | Type             | Description                                                                  |
| ------------- | ---------------- | ---------------------------------------------------------------------------- |
| customerId    | integer ($int64) | Customer identifier. Required only for a multi-customer user                 |
| idAffectation | integer ($int64) | Vehicle-driver assignment identifier                                         |
#### Responses

```application/json;charset=utf-8
200 OK
201 Created
401 Unauthorized
403 Forbidden
429 Too Many Requests
500 Internal Server Error
```

#### Result

```JSON
{
  "vehicule": {
    "typeMotorisation": "MONO",
    "categorie": "UNDEFINED",
    "nomImage": "nomImage",
    "odirectMode": "ODIRECT_UNIVERSEL",
    "description": "description",
    "suppressionLogique": false,
    "privacyEnabled": false,
    "geolocalise": false,
    "boutonEvenementEnabled": false,
    "libelleTypeAsset": {
      "categorie": "UNDEFINED",
      "ordre": 0,
      "libelle": "libelle",
      "nomIcone": "nomIcone",
      "id": 0
    },
    "dispositifIdentifiant": false,
    "immobilisationCablee": false,
    "id": 0,
    "dioEnabled": false,
    "geosecuriteEnabled": false,
    "detectionPorteEnabled": false
  },
  "chauffeur": {
    "nomInd": "nomInd",
    "gsm": "gsm",
    "matriculeInd": "matriculeInd",
    "initialesInd": "initialesInd",
    "prenomInd": "prenomInd",
    "id": 0,
    "email": "email",
    "suppressionLogique": false,
    "idCivilite": 0
  },
  "chauffeurVehicule": {
    "isVehiculeFonction": false,
    "idVehicule": 0,
    "dateDebut": "2026-04-22T15:39:15.262Z",
    "idIndividu": 0,
    "id": 0,
    "dateFin": "2026-04-22T15:39:15.262Z"
  }
}
```

#### Curl

```application/json;charset=utf-8
curl -X GET "https:/https://v3.oceansystem.com/ocean/restapi/affectations_chauffeurs/get?idAffectation=100001"
```

## Retrieve assignment history

[Prior authentication required](./acces.md#authentification-par-requête-post) and token must be passed in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint
```
get /affectations_chauffeurs/historique
```

#### Request Parameters

| Name       | Type             | Description                                                                  |
| ---------- | ---------------- | ---------------------------------------------------------------------------- |
| customerId | integer ($int64) | Customer identifier. Required only for a multi-customer user                 |
| idVehicule | integer ($int64) | Vehicle identifier                                                           |
| idIndividu | integer ($int64) | Vehicle-driver assignment identifier                                         |
|            |                  |                                                                              |

#### Responses

```application/json;charset=utf-8
200 OK
201 Created
401 Unauthorized
403 Forbidden
429 Too Many Requests
500 Internal Server Error
```

#### Result

```JSON
[
  {
    "vehicule": {
      "typeMotorisation": "MONO",
      "categorie": "UNDEFINED",
      "nomImage": "nomImage",
      "odirectMode": "ODIRECT_UNIVERSEL",
      "description": "description",
      "suppressionLogique": false,
      "privacyEnabled": false,
      "geolocalise": false,
      "boutonEvenementEnabled": false,
      "libelleTypeAsset": {
        "categorie": "UNDEFINED",
        "ordre": 0,
        "libelle": "libelle",
        "nomIcone": "nomIcone",
        "id": 0
      },
      "dispositifIdentifiant": false,
      "immobilisationCablee": false,
      "id": 0,
      "dioEnabled": false,
      "geosecuriteEnabled": false,
      "detectionPorteEnabled": false
    },
    "chauffeur": {
      "nomInd": "nomInd",
      "gsm": "gsm",
      "matriculeInd": "matriculeInd",
      "initialesInd": "initialesInd",
      "prenomInd": "prenomInd",
      "id": 0,
      "email": "email",
      "suppressionLogique": false,
      "idCivilite": 0
    },
    "chauffeurVehicule": {
      "isVehiculeFonction": false,
      "idVehicule": 0,
      "dateDebut": "2026-04-22T16:01:00.201Z",
      "idIndividu": 0,
      "id": 0,
      "dateFin": "2026-04-22T16:01:00.201Z"
    }
  }
]
```

#### Curl

```application/json;charset=utf-8
curl -X GET "https:/https://v3.oceansystem.com/ocean/restapi/affectations_chauffeurs/historique?customerId=1110000000&idVehicule=10&idIndividu=1110"
```