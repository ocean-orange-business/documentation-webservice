---
title: Fleet Management
description: 
published: true
date: 2025-01-27T16:27:40.067Z
tags: 
editor: markdown
dateCreated: 2024-12-05T13:02:01.324Z
---

# Fleet Management

This API allows retrieval of:

* Vehicle details (name, registration, make, model, category, device serial number, odometer (once a day), driver identity, etc.).
* Equipment details (name, reference, make, model, operating scenario, configured button press message, tag serial number, etc.).
* Latest events (for vehicles and equipment).
* Client entities.


# Retrieve a Client's Entities

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/mobility/getEntitiesUsingGET)

[Prior authentication required](./acces.md#authentification-par-requête-post) and passing the token in the **X-AUTH-TOKEN** header.

### Definition {.tabset}

#### Endpoint
```
get /restapi/mobility/v1/entities
```

#### Request Parameters

| Name          | Type             | Description                                                              |
|---------------|-----------------|--------------------------------------------------------------------------|
| customerId * | integer ($int64) | Client identifier. Required only for multi-client users.                |

\* mandatory parameter

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

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

## Retrieve Vehicle Data

[Prior authentication required](./acces.md#authentification-par-requête-post) and passing the token in the **X-AUTH-TOKEN** header.
[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/vehiculeengin/getVehiclesUsingGET)

### Definition {.tabset}

#### Endpoint
```
get /restapi/vehicule_engin/vehicles
```

#### Request Parameters

| Name            | Type            | Description                                                                                                 |
|-----------------|-----------------|-------------------------------------------------------------------------------------------------------------|
| customerId *    | integer ($int64)| Client identifier. Required only for multi-client users.                                                    |
| immatriculation | string          | Vehicle registration/license plate.                                                                         |

\* mandatory parameter

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
      "adBoi": "string", // Device AD (APC for obsolete BBOXv1) (50)
      "commentaireBoi": "string", // Device comment
      "coreGsmBoi": "string", // Device GSM number
      "debutGarantie": "2024-12-17T16:14:51.577Z", // Device warranty start date
      "finGarantie": "2024-12-17T16:14:51.577Z", // Device warranty end date
      "id": 0, // Device identifier
      "idEtatBoitier": 0, // Device status identifier
      "imeiBoi": "string", // Device IMEI (15)
      "numeroSerieBoi": "string", // Device serial number (50)
      "sn": "string" // Device SN (Serial Number) (30)
    },
    "chauffeur": {
      "email": "string", // Driver email
      "gsm": "string", // Driver phone number
      "id": 0, // Driver identifier
      "idCivilite": 0, // Driver civility identifier
      "initialesInd": "string", // Driver initials
      "matriculeInd": "string", // Driver ID number
      "nomInd": "string", // Driver last name
      "prenomInd": "string", // Driver first name
      "suppressionLogique": true // Driver logically deleted
    },
    "emissionCo2": 0, // CO2 emission rate
    "entite": {
      "id": 0, // Entity identifier
      "nom": "string", // Entity name (150)
      "suppressionLogique": true // Entity logically deleted
    },
    "releve": {
      "dateReleve": "2024-12-17T16:14:51.577Z", // Odometer reading date
      "id": 0, // Odometer reading identifier
      "value": 0 // Odometer reading value at the end of the previous day (value calculated at midnight)
    },
    "releveAjuste": {
      "dateReleve": "2024-12-17T16:14:51.577Z", // Adjusted odometer reading date
      "id": 0, // Adjusted odometer reading identifier
      "value": 0 // Adjusted odometer value based on the distance or time traveled by the vehicle since the last automatic reading
    },
    "vehicle": {
      "apcMode": "GPS", // APC mode
      "boitierAvantCoupeCircuit": true, // Device before circuit breaker
      "buzzerSurvitesseEnabled": true, // Overspeed buzzer enabled
      "categorie": "UNDEFINED", // Vehicle category
      "categorieVehiculeEcoConduite": "UL", // Eco-driving vehicle category
      "couleur": "string", // Vehicle color (50)
      "coupeBatterie": true, // Battery cut-off
      "date1ereMec": "2024-12-17T16:14:51.577Z", // First mechanical date
      "description": "string", // Vehicle description
      "detectionPorteEnabled": true, // Door detection enabled
      "dioEnabled": true, // Data on an input/output in the device yes/no (auxiliary motor, ...)
      "dispositifIdentifiant": true, // Status of the identifying device (yes/no)
      "emissionCo2": 0, // CO2 emission
      "etatEcoConduite": "ACTIF", // Eco-driving status
      "geolocalise": true, // Geolocated
      "geomissionEnabled": true, // Geomission enabled
      "geosecuriteEnabled": true, // Geosecurity enabled
      "id": 0, // Vehicle identifier
      "idEnergie": 0, // Energy type identifier
      "idModeDeplacement": 0, // Mode of travel identifier
      "idUniteConsommation": 0, // Consumption unit identifier
      "immatriculation": "string", // Vehicle registration/license plate
      "immobilisationCablee": true, // Wired immobilization
      "libelleTypeAsset": {
        "categorie": "UNDEFINED", // Asset type category
        "id": 0, // Asset type identifier
        "libelle": "string", // Asset type label
        "nomIcone": "string", // Asset type icon name
        "ordre": 0 // Asset type order
      },
      "marque": "string", // Vehicle make
      "modele": "string", // Vehicle model
      "nomImage": "string", // Image name
      "nombreCvFiscaux": 0, // Fiscal horsepower
      "numeroEmbarque": 0, // On-board number
      "numeroParc": "string", // Fleet number
      "numeroSerie": "string", // Vehicle serial number
      "odirectMode": "ODIRECT_UNIVERSEL", // O-Direct mode Renault/Peugeot/Kuantic, ...
      "privacyEnabled": true, // "Privacy" mode enabled
      "prk": 0, // PRK
      "signesDistinctifs": "string", // Distinguishing marks
      "suppressionLogique": true, // Logically deleted
      "typeMotorisation": "MONO", // Motorization type
      "valeurConsommation": 0, // Consumption value
      "vin": "string" // VIN
    },
    "visites": [
      {
        "compteurPrevu": 0, // Expected odometer reading
        "datePrevue": "2024-12-17T16:14:51.577Z", // Expected date
        "description": "string", // Description
        "idVisiteEntretien": 0 // Maintenance visit identifier
      }
    ]
  }
]
```

## Retrieve Nearest Vehicle Data

[Prior authentication required](./acces.md#authentification-par-requête-post) and passing the token in the **X-AUTH-TOKEN** header.

### Definition {.tabset}

#### Endpoint
```
post /restapi/vehicule_engin/nearestVehicles
```

#### Request Parameters

| Name           | Type            | Description                                                             |
|----------------|-----------------|-------------------------------------------------------------------------|
| customerId     | integer ($int64)| Client identifier. Required only for multi-client users.                |
| radius         | integer ($int32)| Search radius.                                                          |
| latitude       | double          | Latitude of the search starting point.                                  |
| longitude      | double          | Longitude of the search starting point.                                 |
| resultsLimit   | integer ($int32)| Specifies the number of results to return for the computeMode PAR_ROUTE (value between 1 and 10). |

#### Request Body

```JSON
{
  "computeMode":"VOL_OISEAU ou PAR_ROUTE",
  "radiusUnit":"string"
}
```

#### Responses

```application/json;charset=utf-8
200 OK
201 Created
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Result

```JSON
[
  {
    "address": {
      "address": "string",
      "cap": 0,
      "closestPoi": {
        "adressePoi": "string",
        "codePostalPoi": "string",
        "complementAdresse1Poi": "string",
        "complementAdresse2Poi": "string",
        "denominationPoi": "string",
        "etatRegionPoi": "string",
        "geom": "string",
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
        "propSpecifiqueDTO": {
          "id": 0,
          "idClient": 0,
          "idObjetRef": 0,
          "proprietesSpecifiquesClient": {
            "psValues": {
              "additionalProp1": [
                "string"
              ],
              "additionalProp2": [
                "string"
              ],
              "additionalProp3": [
                "string"
              ]
            }
          },
          "typeObjet": "CLIENT"
        },
        "rayonPoi": 0,
        "suppressionLogique": true,
        "villePoi": "string"
      },
      "countryCode": 0,
      "gpsCalle": true,
      "latitude": 0,
      "longitude": 0,
      "postCode": "string",
      "precision": 0,
      "town": "string"
    },
    "distance": 0,
    "driver": {
      "affectedEtape": {
        "codeExploitant": "string",
        "creation": "2024-12-18T11:05:38.972Z",
        "debut": "2024-12-18T11:05:38.972Z",
        "idEtape": 0,
        "modeAffectationEtape": "AUTO",
        "ndid": "string",
        "numeroEmbarque": 0,
        "typeAffectationEtape": "CHAUFFEUR"
      },
      "dispositif": {
        "color": 0,
        "id": 0,
        "idClient": 0,
        "idTypeDispositifIdentifiant": 0,
        "numeroCleClient": 0,
        "numeroCompletDid": "string",
        "numeroDid": "string"
      },
      "id": 0,
      "identEnabled": true,
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
      },
      "ndidLong": "string",
      "relevant": true
    },
    "duration": 0,
    "eta": "2024-12-18T11:05:38.972Z",
    "etatMobile": "UNDEFINED",
    "gmtPos": "2024-12-18T11:05:38.972Z",
    "gpsCale": true,
    "group": {
      "descriptionGrp": "string",
      "id": 0,
      "suppressionLogique": true
    },
    "immobilisationState": "LOCKED",
    "time": 0,
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
