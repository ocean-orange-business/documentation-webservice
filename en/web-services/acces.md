---
title: Access Management
description: 
published: true
date: 2024-10-31T15:22:00.083Z
tags: 
editor: markdown
dateCreated: 2024-10-31T15:21:56.959Z
---

# Access Management

This API allows for:

-   [Authentication via GET request](#authentication-via-post-request)
-   [Authentication via POST request](#authentication-via-post-request)
-   [Password modification](#modify-user-password) => authentication,
-   [Password reset](#reset-password-by-sending-an-email) => authentication,
-   [Management of feature permissions by user](#find-feature-rights-for-an-application-for-a-user) => authorization.

> The token is only valid for 12 hours. After this period, a new one must be generated.
{.is-warning}

## Authentication via GET request

### Definition {.tabset}

#### Endpoint

```
post /restapi/auth/authenticate * Deprecated
```

#### Request Parameters

| Name                | Type   | Description                      |
| ------------------- | ------ | -------------------------------- |
| login *             | string | Identifier                       |
| password *          | string | Password                         |
\* mandatory parameter

#### Responses
```application/json;charset=utf-8
200 OK
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Result

```JSON
{
  "additionalAccountData": {},
  "passwordExpirationRemainingDays": 0,
  "token": "string"
  // Token duration: 12 hours
}
```

## Authentication via POST request

### Definition {.tabset}

#### Endpoint

```
post /restapi/auth/authenticate2
```

#### Request Body

```JSON
{
    "login": "Any identifier",
    "password": "Strong and secure password"
}
```
#### Responses
```application/json;charset=utf-8
200 OK
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Result

```JSON
{
  "additionalAccountData": {},
  "passwordExpirationRemainingDays": 0,
  "token": "string"
  // Token duration: 12 hours
}
```

## Modify User Password

[Prior authentication required](#authentication-via-post-request) and passing the token in the header **X-AUTH-TOKEN**

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/authentication/changePasswordUsingPOST)

### Definition {.tabset}

#### Endpoint

```
post /restapi/auth/changePassword
```
#### Request Parameters

| Name                    | Type   | Description                      |
| ----------------------- | ------ | -------------------------------- |
| actualPassword *        | string | Current password                 |
| newPassword *           | string | New password                     |
| newPasswordConfirmed *  | string | New password confirmation        |
\* mandatory parameter

#### Responses

```application/json;charset=utf-8
200 OK
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Reset Password by Sending an Email

[Prior authentication required](#authentication-via-post-request) and passing the token in the header **X-AUTH-TOKEN**

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/authentication/requestPasswordResetUsingPOST)

### Definition {.tabset}

#### Endpoint
```
post /restapi/auth/requestPasswordReset
```

#### Request Parameters

| Name    | Type    | Description                                                                               |
| ------- | ------- | ----------------------------------------------------------------------------------------- |
| login * | string  | User login for which the password reset request is made                                   |
| url     | string  | Application URL                                                                           |
\* mandatory parameter

#### Responses
```application/json;charset=utf-8
200 OK
204 No Content
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Find Application Rights/Features for a User

[Prior authentication required](#authentication-via-post-request) and passing the token in the header **X-AUTH-TOKEN**

This web service allows you to find all rights/features (with detailed content) for an application for a user.

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/authorization/findFunctionalitiesDetailedUsingGET)

### Definition {.tabset}

#### Endpoint

#### Request Parameters

| Name          | Type            | Description                                                                 |
|---------------|-----------------|-----------------------------------------------------------------------------|
| customerId    | integer ($int64)| Customer identifier. Required only for multi-client users                  |
| elementType * | string - Enum   | Type of application element (Link, Tab, Web service, Action)               |
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
    "enumCode": "string",
    // Code to describe the feature
    "fonctionnaliteDto": {
      "description": "string",
      // Description of the feature
      "idFonctionnalite": 0,
      // Unique identifier of the feature in the Ocean information system
      "ordre": 0,
      // Display order of the feature
      "typeElement": "string"
      // Action/Tabs/Link/Menu/WsAction/Tabs/Link/Menu/Ws
    }
  }
]
```

## Retrieve Vehicle Rental Contracts

[Prior authentication required](#authentication-via-post-request) and passing the token in the header **X-AUTH-TOKEN**

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/)

### Definition {.tabset}

#### Endpoint

```
get /restapi/contrat_location/contrats
```

#### Request Parameters

| Name           | Type             | Description                                                                                                                                            |
| -------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------|
| customerId **  | integer ($int64) | Customer identifier. Required for multi-client users                                                                                                   |
| date           | string           | Filter for active contracts on this date. The date must be in UTC format: "dd/MM/yyyy HH:mm:ss Z". Only this format is accepted by our API             |
| vehicleIds     | array (of int)   | Filter for identified vehicles (unlimited number)                                                                                                      |
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
    "id": 0,
    "loueur": "string",
    "nbKmPrevus": 0,
    "nbMoisPrevus": 0,
    "nbMoisUtilisation": 0,
    "typeLocation": "INCONNU",
    "vehicleId": 0
  }
]
```

## Retrieve Latest Events

[Prior authentication required](#authentication-via-post-request) and passing the token in the header **X-AUTH-TOKEN**

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/)

### Definition {.tabset}

#### Endpoint

```
get /restapi/evenement/lastEvent
```

#### Request Parameters

| Name            | Type             | Description                                                                                                          |
| --------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------- |
| customerId *    | integer ($int64) | Customer identifier                                                                                                |
| vehiculesIds    | array (of int)   | Vehicle identifier                                                                                              |
| entitiesIds     | array (of int)   | Entity identifier                                                                                              |
| dateDebut       | string           | Start date must be in UTC format: "dd/MM/yyyy HH:mm:ss Z". Only this format is accepted by our API. |
| dateFin         | string           | End date must be in UTC format: "dd/MM/yyyy HH:mm:ss Z". Only this format is accepted by our API.   |
| codeEvenements *| array (of int)   | Event identifier                                                                                         |
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
{
  "additionalProp1": {
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
    "advancedTechnicalEvent": true,
    "date": "2024-12-18T10:36:39.869Z",
    "dateDebut": "2024-12-18T10:36:39.869Z",
    "dateFin": "2024-12-18T10:36:39.869Z",
    "detailEvenementLightDTO": {
      "code": "string",
      "defaut": "string",
      "modele": "string",
      "statut": "string",
      "technicalLabel": "string",
      "type": "string"
    },
    "entite": {
      "id": 0,
      "nom": "string",
      "suppressionLogique": true
    },
    "evenementLibelle": "string",
    "eventState": "PUNCTUAL",
    "extendedDataMap": {
      "additionalProp1": {},
      "additionalProp2": {},
      "additionalProp3": {}
    },
    "groupingPeriod": "TODAY",
    "heure": "2024-12-18T10:36:39.869Z",
    "id": "string",
    "reliable": true,
    "typeEvenement": "UNDEFINED",
    "typeEvenementODirectDTO": {
      "classificationEvenementDTO": {
        "code": "string",
        "descriptioni18nKey": "string",
        "id": 0
      },
      "detailsEvenementLightDTO": [
        {
          "code": "string",
          "defaut": "string",
          "modele": "string",
          "statut": "string",
          "technicalLabel": "string",
          "type": "string"
        }
      ],
      "id": 0,
      "typeEvenementOdirectDTO": {
        "code": "string",
        "descriptionI18NKey": "string",
        "numeroEve": 0,
        "temporalType": "PUNCTUAL"
      }
    },
    "vehicleEngin": {
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
  },
  "additionalProp2": {
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
    "advancedTechnicalEvent": true,
    "date": "2024-12-18T10:36:39.869Z",
    "dateDebut": "2024-12-18T10:36:39.869Z",
    "dateFin": "2024-12-18T10:36:39.869Z",
    "detailEvenementLightDTO": {
      "code": "string",
      "defaut": "string",
      "modele": "string",
      "statut": "string",
      "technicalLabel": "string",
      "type": "string"
    },
    "entite": {
      "id": 0,
      "nom": "string",
      "suppressionLogique": true
    },
    "evenementLibelle": "string",
    "eventState": "PUNCTUAL",
    "extendedDataMap": {
      "additionalProp1": {},
      "additionalProp2": {},
      "additionalProp3": {}
    },
    "groupingPeriod": "TODAY",
    "heure": "2024-12-18T10:36:39.869Z",
    "id": "string",
    "reliable": true,
    "typeEvenement": "UNDEFINED",
    "typeEvenementODirectDTO": {
      "classificationEvenementDTO": {
        "code": "string",
        "descriptioni18nKey": "string",
        "id": 0
      },
      "detailsEvenementLightDTO": [
        {
          "code": "string",
          "defaut": "string",
          "modele": "string",
          "statut": "string",
          "technicalLabel": "string",
          "type": "string"
        }
      ],
      "id": 0,
      "typeEvenementOdirectDTO": {
        "code": "string",
        "descriptionI18NKey": "string",
        "numeroEve": 0,
        "temporalType": "PUNCTUAL"
      }
    },
    "vehicleEngin": {
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
}
```

## Retrieve Equipment Data

[Prior authentication required](#authentication-via-post-request) and passing the token in the header **X-AUTH-TOKEN**

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/materiel/getMaterielsUsingGET)

### Definition {.tabset}

#### Endpoint

```
get /restapi/materiel/list
```

#### Request Parameters

| Name          | Type             | Description                                            |
| --------------|------------------|-------------------------------------------------------|
| customerId *  | integer ($int64) | Customer identifier. Required only for multi-client users |
| materielIds    | array (of int)   | List of equipment identifiers (unlimited number)      |

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
  }
]
```
