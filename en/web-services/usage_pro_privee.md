---
title: Pro/Private Usage
description: 
published: true
date: 2025-11-25T11:45:29.845Z
tags: 
editor: markdown
dateCreated: 2025-11-25T11:16:09.120Z
---

# Management of Professional/Private Usage

These APIs allow managing private life schedules and analyzing private/professional vehicle and driver usage.

-Retrieval of recurring private life schedules
-Creation/Modification of private life schedules
-Management of requests for private/professional passage retroactively
-Private life/private usage analyses

## Retrieval of recurring private life schedules

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=get-/vieprivee/v1/horairesViePriveeRecurrentesIndividu)

[Pre-authentication required](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
GET /restapi/vieprivee/v1/horairesViePriveeRecurrentesIndividu
```

#### Request parameters

| Name          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| individuId   | integer ($int64) | Identifiant du conducteur.                                                      |


\* mandatory parameter

Response: List of recurring schedules containing:

Schedule: Start/end hours, day of the week, schedule type
Individual: Personal information (name, first name, email, mobile, etc.)
Dates: Start and end validity

#### Responses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
404 NOT FOUND
500 INTERNAL SERVER ERROR
```

#### Result

```JSON
[
  {
    "horaire": {
      "finHeure": 0,
      "idJourSemaine": "LUNDI",
      "finMinute": 0,
      "typeHoraires": "IMMOBILISATION",
      "debutMinute": 0,
      "id": 0,
      "debutHeure": 0
    },
    "debut": "2025-11-25T13:49:33.102Z",
    "individu": {
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
    "fin": "2025-11-25T13:49:33.102Z",
    "id": 0
  }
]
```

## Création/Modification des horaires de vie privée

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=post-/vieprivee/v1/horairesViePriveeRecurrentesIndividu)

[Pre-authentication required](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
POST /restapi/vieprivee/v1/horairesViePriveeRecurrentesIndividu
```

#### Request parameters

| Name          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId  | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| individuId *  | integer ($int64) | Identifiant du conducteur.                                                      |
| dateDebut   | date | La date de début au format "dd/MM/yyyy HH:mm:ss Z" (Format: dd/MM/yyyy HH:mm:ss Z)           |
| dateFin   | date | La date de fin au format "dd/MM/yyyy HH:mm:ss Z" (Format: dd/MM/yyyy HH:mm:ss Z)               |


\* mandatory parameter

Response : Boolean (success/failure of the operation)


#### Responses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
500 INTERNAL SERVER ERROR
```

#### Result

```JSON
{
        "innerMap": {
                "map": {}
        }
}
```

## Management of requests for private/professional passage retroactively

Records/Deletes a request for private/professional life passage retroactively for a step

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=post-/vieprivee/v1/etapeViePriveePosteriori)

[Pre-authentication required](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Definition {.tabset}

#### Endpoint
```
POST /restapi/vieprivee/v1/etapeViePriveePosteriori
```

#### Request parameters

| Name          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| idEtape  | integer ($int64) | Identifiant de l'étape |
| numeroEmbarque *  | integer ($int64) | Numéro d'embarquement                                                     |
| codeExploitant   | Code exploitant    |
| privacy   | boolean |  true / false |


\* mandatory parameter 

Response : Boolean (success/failure of the operation)


#### Responses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
500 INTERNAL SERVER ERROR
```
## Analyses de vie privée/usage privé

[Additional documentation on SWAGGER](ocean/restapi/common/openapi/explorer#?route=post-/analyse/preformattedPrivacy)

[Pre-authentication required](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
POST /restapi/analyse/preformattedPrivacy
```

#### Request parameters

| Name          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId  | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |


\* mandatory parameter 

Response: Detailed analyses including:

Summaries by driver/vehicle
Consumptions (fuel, electricity)
Distances and durations
Costs
Vehicle information (engine type, equipment)

#### Responses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
500 INTERNAL SERVER ERROR
```

#### Result

```JSON
[
  {
    "mode": "BY_DRIVER_WITHOUT_HORAIRE_SYNTHESIS",
    "synthesisTreeByDriver": {
      "nodes": {},
      "entityTotalCumul": {
        "consoL": 0,
        "total": {
          "durationInSecByPeriodMap": {},
          "utilisationBatterieByPeriodMap": {},
          "distanceInMeterByPeriodMap": {},
          "distanceElectriqueInMeterByPeriodMap": {}
        },
        "cost": 0,
        "driver": {
          "affectedEtape": {
            "debut": "2025-11-25T14:02:52.955Z",
            "ndid": "ndid",
            "modeAffectationEtape": "AUTO",
            "codeExploitant": "codeExploitant",
            "idEtape": 0,
            "typeAffectationEtape": "CHAUFFEUR",
            "numeroEmbarque": 0,
            "creation": "2025-11-25T14:02:52.955Z"
          },
          "individu": {
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
          "isRelevant": false,
          "isIdentEnabled": false,
          "dispositif": {
            "numeroCleClient": 0,
            "color": 0,
            "idClient": 0,
            "numeroOcean": "numeroOcean",
            "numeroCompletDid": "numeroCompletDid",
            "numeroDid": "numeroDid",
            "id": 0,
            "idTypeDispositifIdentifiant": 0
          },
          "ndidLong": "ndidLong"
        },
        "dayDate": "dayDate",
        "consoKWh": 0,
        "entity": {
          "id": 0,
          "nom": "nom",
          "suppressionLogique": false
        },
        "vehicle": {
          "typeMotorisation": "MONO",
          "categorie": "UNDEFINED",
          "nomImage": "nomImage",
          "odirectMode": "ODIRECT_UNIVERSEL",
          "description": "description",
          "suppressionLogique": false,
          "privacyEnabled": false,
          "geolocalise": false,
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
        }
      },
      "entityTotalByFlagCumul": {},
      "entity": {
        "id": 0,
        "nom": "nom",
        "suppressionLogique": false
      },
      "content": {
        "typeMotorisationEnergyeMap": {},
        "chauffeursByIdDriverAndPeriodeBean": {
          "map": {}
        },
        "entityTotal": {
          "consoL": 0,
          "total": {
            "durationInSecByPeriodMap": {},
            "utilisationBatterieByPeriodMap": {},
            "distanceInMeterByPeriodMap": {},
            "distanceElectriqueInMeterByPeriodMap": {}
          },
          "cost": 0,
          "driver": {
            "affectedEtape": {
              "debut": "2025-11-25T14:02:52.956Z",
              "ndid": "ndid",
              "modeAffectationEtape": "AUTO",
              "codeExploitant": "codeExploitant",
              "idEtape": 0,
              "typeAffectationEtape": "CHAUFFEUR",
              "numeroEmbarque": 0,
              "creation": "2025-11-25T14:02:52.956Z"
            },
            "individu": {
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
            "isRelevant": false,
            "isIdentEnabled": false,
            "dispositif": {
              "numeroCleClient": 0,
              "color": 0,
              "idClient": 0,
              "numeroOcean": "numeroOcean",
              "numeroCompletDid": "numeroCompletDid",
              "numeroDid": "numeroDid",
              "id": 0,
              "idTypeDispositifIdentifiant": 0
            },
            "ndidLong": "ndidLong"
          },
          "dayDate": "dayDate",
          "consoKWh": 0,
          "entity": {
            "id": 0,
            "nom": "nom",
            "suppressionLogique": false
          },
          "vehicle": {
            "typeMotorisation": "MONO",
            "categorie": "UNDEFINED",
            "nomImage": "nomImage",
            "odirectMode": "ODIRECT_UNIVERSEL",
            "description": "description",
            "suppressionLogique": false,
            "privacyEnabled": false,
            "geolocalise": false,
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
          }
        },
        "refItems": {},
        "entityTotalByFlag": {},
        "entity": {
          "id": 0,
          "nom": "nom",
          "suppressionLogique": false
        }
      }
    },
    "htmlTable": "htmlTable",
    "synthesisTreeByVehicle": {
      "nodes": {},
      "entityTotalCumul": {
        "consoL": 0,
        "total": {
          "durationInSecByPeriodMap": {},
          "utilisationBatterieByPeriodMap": {},
          "distanceInMeterByPeriodMap": {},
          "distanceElectriqueInMeterByPeriodMap": {}
        },
        "cost": 0,
        "driver": {
          "affectedEtape": {
            "debut": "2025-11-25T14:02:52.957Z",
            "ndid": "ndid",
            "modeAffectationEtape": "AUTO",
            "codeExploitant": "codeExploitant",
            "idEtape": 0,
            "typeAffectationEtape": "CHAUFFEUR",
            "numeroEmbarque": 0,
            "creation": "2025-11-25T14:02:52.957Z"
          },
          "individu": {
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
          "isRelevant": false,
          "isIdentEnabled": false,
          "dispositif": {
            "numeroCleClient": 0,
            "color": 0,
            "idClient": 0,
            "numeroOcean": "numeroOcean",
            "numeroCompletDid": "numeroCompletDid",
            "numeroDid": "numeroDid",
            "id": 0,
            "idTypeDispositifIdentifiant": 0
          },
          "ndidLong": "ndidLong"
        },
        "dayDate": "dayDate",
        "consoKWh": 0,
        "entity": {
          "id": 0,
          "nom": "nom",
          "suppressionLogique": false
        },
        "vehicle": {
          "typeMotorisation": "MONO",
          "categorie": "UNDEFINED",
          "nomImage": "nomImage",
          "odirectMode": "ODIRECT_UNIVERSEL",
          "description": "description",
          "suppressionLogique": false,
          "privacyEnabled": false,
          "geolocalise": false,
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
        }
      },
      "entityTotalByFlagCumul": {},
      "entity": {
        "id": 0,
        "nom": "nom",
        "suppressionLogique": false
      },
      "content": {
        "typeMotorisationEnergyeMap": {},
        "chauffeursByIdDriverAndPeriodeBean": {
          "map": {}
        },
        "entityTotal": {
          "consoL": 0,
          "total": {
            "durationInSecByPeriodMap": {},
            "utilisationBatterieByPeriodMap": {},
            "distanceInMeterByPeriodMap": {},
            "distanceElectriqueInMeterByPeriodMap": {}
          },
          "cost": 0,
          "driver": {
            "affectedEtape": {
              "debut": "2025-11-25T14:02:52.958Z",
              "ndid": "ndid",
              "modeAffectationEtape": "AUTO",
              "codeExploitant": "codeExploitant",
              "idEtape": 0,
              "typeAffectationEtape": "CHAUFFEUR",
              "numeroEmbarque": 0,
              "creation": "2025-11-25T14:02:52.958Z"
            },
            "individu": {
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
            "isRelevant": false,
            "isIdentEnabled": false,
            "dispositif": {
              "numeroCleClient": 0,
              "color": 0,
              "idClient": 0,
              "numeroOcean": "numeroOcean",
              "numeroCompletDid": "numeroCompletDid",
              "numeroDid": "numeroDid",
              "id": 0,
              "idTypeDispositifIdentifiant": 0
            },
            "ndidLong": "ndidLong"
          },
          "dayDate": "dayDate",
          "consoKWh": 0,
          "entity": {
            "id": 0,
            "nom": "nom",
            "suppressionLogique": false
          },
          "vehicle": {
            "typeMotorisation": "MONO",
            "categorie": "UNDEFINED",
            "nomImage": "nomImage",
            "odirectMode": "ODIRECT_UNIVERSEL",
            "description": "description",
            "suppressionLogique": false,
            "privacyEnabled": false,
            "geolocalise": false,
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
          }
        },
        "refItems": {},
        "entityTotalByFlag": {},
        "entity": {
          "id": 0,
          "nom": "nom",
          "suppressionLogique": false
        }
      }
    },
    "bean": {}
  }
]
```
