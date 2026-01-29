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

- [Retrieval of individu list](#retrieval-individu-list)
- [Retrieval of recurring private life schedules](#retrieval-of-recurring-private-life-schedules)
- [Creation/Modification of private life schedules](#creationmodification-of-private-life-schedules)
- [Management of requests for private/professional passage retroactively](#management-of-requests-for-private/professional-passage-retroactively)
- [Private life/private usage analyses](#private-life/private-usage-analyses)

To use the various web services, it is necessary to use internal identifiers for your individuals 
(for example, idChauffeur) or for the steps (idEtape, corresponding to the daily record).
These elements are easily accessible via the following web services:

[Vehicles](/en/web-services/flotte#récupérer_les_données_des_véhicules) GET /vehicule_engin/vehicles
[trajets-et-positions](/en/web-services/trajets-et-positions#récupérer-la-fiche−journalière-d’un-véhicule-pour-une-date-donnée) GET /mobility/v1/ficheJour

## Retrival individus list

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=post-/individus/list)
[Pre-authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
POST /restapi/individus/list
```

#### Request parameters

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Customer ID. Required only for a multi-client user. |
| criteria   | integer ($int64) | Filtering criteria for individuals in the system |

List of possible criteria:
- WITHOUT_USER: individual without a created user
- WITH_USER: with an associated user
- WITH_ENTITE: with an attached organizational entity
- WITH_GSM: with mobile phone information
- WITH_VEHICLE: with associated vehicle(s)

Allowed: WITHOUT_USER | WITH_USER | WITH_ENTITE | WITH_GSM | WITH_VEHICLE                                                |


\* parameter is mandatory

Response: List of the client's individuals


#### Respond

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
    "entite": {
      "id": 0,
      "nom": "nom",
      "suppressionLogique": false
    },
    "utilisateur": {
      "emailUti": "emailUti",
      "prenomUti": "prenomUti",
      "loginUti": "loginUti",
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
      "nomUti": "nomUti",
      "id": 0,
      "dateFinValidite": "2026-01-21T15:35:19.720Z",
      "suppressionLogique": false,
      "utilisateurType": "CLASSIC"
    },
    "groupe": {
      "descriptionGrp": "descriptionGrp",
      "id": 0,
      "suppressionLogique": false
    },
    "fonctionnalites": [
      {
        "idFonctionnalite": 0
      }
    ],
    "propSpecifiqueDTO": {
      "proprietesSpecifiquesClient": {
        "psValues": {}
      },
      "ville": "ville",
      "dateFCO": "2026-01-21T15:35:19.721Z",
      "objectifMensuel": 0,
      "dateNaissanceConducteur": "2026-01-21T15:35:19.721Z",
      "nationalitePermis": 0,
      "idClient": 0,
      "lieuNaissanceConducteur": "lieuNaissanceConducteur",
      "numeroVoieAdresse": "numeroVoieAdresse",
      "typeObjet": "CLIENT",
      "idObjetRef": 0,
      "objectifHebdo": 0,
      "codePostal": "codePostal",
      "keyUser": "keyUser",
      "lieuDelivrancePermis": "lieuDelivrancePermis",
      "complementAdresse": "complementAdresse",
      "dateVisiteMedicale": "2026-01-21T15:35:19.721Z",
      "categoriePermis": [
        "A"
      ],
      "dateValiditePermis": "2026-01-21T15:35:19.721Z",
      "numeroPermis": "numeroPermis",
      "adresse": "adresse",
      "dateDelivrancePermis": "2026-01-21T15:35:19.721Z",
      "id": 0,
      "pays": 0
    },
    "vehicleFieldsDTO": {
      "numeroSerie": "numeroSerie",
      "typeMotorisation": "MONO",
      "categorie": "UNDEFINED",
      "nomImage": "nomImage",
      "odirectMode": "ODIRECT_UNIVERSEL",
      "couleur": "couleur",
      "description": "description",
      "numeroParc": "numeroParc",
      "marque": "marque",
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
      "modele": "modele",
      "dispositifIdentifiant": false,
      "immobilisationCablee": false,
      "id": 0,
      "dioEnabled": false,
      "immatriculation": "immatriculation",
      "numeroEmbarque": 0,
      "geosecuriteEnabled": false,
      "detectionPorteEnabled": false
    }
  }
]
```
#### Curl

```JSON
curl -X POST "https:/https://v3.oceansystem.com/ocean/restapi/individus/list?customerId=21"
```

## Retrieval of recurring private life schedules

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=get-/vieprivee/v1/horairesViePriveeRecurrentesIndividu)

[Pre-authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**

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
#### Curl

```JSON
curl -X GET "https:/https://v3.oceansystem.com/ocean/restapi/vieprivee/v1/horairesViePriveeRecurrentesIndividu?customerId=1110000000&individuId=1110000004"
```
## Creation/Modification of private life schedules

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=post-/vieprivee/v1/horairesViePriveeRecurrentesIndividu)

[Pre-authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**

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
#### Curl

```JSON
curl -X POST "https://v3.oceansystem.com/ocean/restapi/vieprivee/v1/horairesViePriveeRecurrentesIndividu?customerId=1110000000&individuId=1110000004&dateDebut=24%2F11%2F2025+00%3A00%3A00+Z&dateFin=30%2F11%2F2025+00%3A00%3A00+Z" \
  -H "content-type: application/json" \
  -d '{
    "innerMap": {   "map": {}
    }
}'
```
## Management of requests for private/professional passage retroactively

Records/Deletes a request for private/professional life passage retroactively for a step

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=post-/vieprivee/v1/etapeViePriveePosteriori)

[Pre-authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**

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
#### Result
```JSON
[
  {
  boolean:true/false
  }
]
```
#### Curl

```JSON
curl -X POST "https://v3.oceansystem.com/ocean/restapi/vieprivee/v1/etapeViePriveePosteriori?idEtape=1110000401&numeroEmbarque=2&codeExploitant=1110000001&privacy=false"
```



## Private life/private usage analyses

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#lo?route=post-/analyse/preformattedPrivacy)

[Pre-authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
GET /restapi/analyse/preformattedPrivacy
```

#### Request Parameters

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId   | integer ($int64) | Customer ID. Required only for a multi-client user.                          |

> **Input data model :**

```JSON
{
filter: {
persons: [integer]
An array of driver/person IDs (e.g., [7001, 7002, 7003]) for filtering specific drivers. Can be empty if not needed.

entities: [integer]
An array of entity IDs (e.g., [123, 456, 789]) for filtering entities. Can be empty if not needed.

groups: [integer]
An array of group IDs (e.g., [1001, 1002, 1003]) for filtering organizational groups. Can be empty if not needed.

vehicleIds: [integer]
An array of vehicle IDs (e.g., [5001, 5002, 5003]) for filtering specific vehicles. Can be empty if not needed.

}
renderMode: string enum
Allowed: BY_DRIVER_WITHOUT_HORAIRE_SYNTHESIS ┃ BY_DRIVER_WITH_HORAIRE_SYNTHESIS ┃ BY_VEHICLE_WITHOUT_HORAIRE_SYNTHESIS ┃ BY_VEHICLE_WITH_HORAIRE_SYNTHESIS ┃ BY_DRIVER_WITHOUT_HORAIRE_DETAIL ┃ BY_DRIVER_WITH_HORAIRE_DETAIL ┃ BY_VEHICLE_WITHOUT_HORAIRE_DETAIL ┃ BY_VEHICLE_WITH_HORAIRE_DETAIL ┃ BY_DRIVER_VEHICLE_FUNCTION_WITH_HORAIRE_SYNTHESIS ┃ BY_DRIVER_VEHICLE_FUNCTION_WITH_HORAIRE_DETAIL
criteria: string enum
Allowed: GEOLOCATION ┃ WIHOUT_GEOLOCATION ┃ ALL
periode: {
debut: date-time
A start date. Can be an epoch timestamp in milliseconds (e.g., 1747063827938) or an ISO-8601 date string (e.g., "2025-05-12T15:30:27.938+00:00")

fin: date-time
An end date. Can be an epoch timestamp in milliseconds (e.g., 1747063827938) or an ISO-8601 date string (e.g., "2025-05-12T15:30:27.938+00:00")
}
}
```

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
#### Curl

```JSON
curl -X POST "https://v3.oceansystem.com/ocean/restapi/analyse/preformattedPrivacy?customerId=1110000000" \
  -H "content-type: application/json" \
  -d '{
    "filter": {   "persons": [       0   ],   "entities": [       0   ],   "groups": [       0   ],   "vehicleIds": [       0   ]
    },
    "renderMode": "BY_DRIVER_WITHOUT_HORAIRE_SYNTHESIS",
    "criteria": "GEOLOCATION",
    "periode": {   "debut": "2025-11-28T14:51:37.798Z",   "fin": "2025-11-28T14:51:37.799Z"
    }
}'
```
