---
title: usage pro privee
description: 
published: true
date: 2025-11-25T11:45:29.845Z
tags: 
editor: markdown
dateCreated: 2025-11-25T11:16:09.120Z
---

# Gestion des Usages pro / privée 

Ces API permettent de gérer les horaires de vie privée et d'analyser l'usage privé/professionnel des véhicules et conducteurs.
-Récupération des horaires de vie privée récurrentes
-Création/Modification des horaires de vie privée
-Gestion des demandes de passage vie privée/pro à posteriori
-Analyses de vie privée/usage privé

## Récupération des horaires de vie privée récurrentes

[Documentation supplémentaire sur SWAGGER](ocean/restapi/common/openapi/explorer#?route=get-/vieprivee/v1/horairesViePriveeRecurrentesIndividu)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
GET /restapi/vieprivee/v1/horairesViePriveeRecurrentesIndividu
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| individuId   | integer ($int64) | Identifiant du conducteur.                                                      |


\* paramètre obligatoire 

Réponse : Liste des horaires récurrents contenant :

Horaire : Heures de début/fin, jour de la semaine, type d'horaire
Individu : Informations personnelles (nom, prénom, email, GSM, etc.)
Dates : Début et fin de validité

#### Réponses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
404 NOT FOUND
500 INTERNAL SERVER ERROR
```

#### Résultat

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

[Documentation supplémentaire sur SWAGGER](ocean/restapi/common/openapi/explorer#?route=post-/vieprivee/v1/horairesViePriveeRecurrentesIndividu)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
POST /restapi/vieprivee/v1/horairesViePriveeRecurrentesIndividu
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId  | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| individuId *  | integer ($int64) | Identifiant du conducteur.                                                      |
| dateDebut   | date | La date de début au format "dd/MM/yyyy HH:mm:ss Z" (Format: dd/MM/yyyy HH:mm:ss Z)           |
| dateFin   | date | La date de fin au format "dd/MM/yyyy HH:mm:ss Z" (Format: dd/MM/yyyy HH:mm:ss Z)               |


\* paramètre obligatoire 

Réponse : Boolean (succès/échec de l'opération)


#### Réponses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
500 INTERNAL SERVER ERROR
```

#### Résultat

```JSON
{
        "innerMap": {
                "map": {}
        }
}
```

## Gestion des demandes de passage vie privée/pro à posteriori

Enregistre/Supprime une demande de passage en vie privée/vie pro à posteriori pour une étape

[Documentation supplémentaire sur SWAGGER](ocean/restapi/common/openapi/explorer#?route=post-/vieprivee/v1/etapeViePriveePosteriori)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
POST /restapi/vieprivee/v1/etapeViePriveePosteriori
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| idEtape  | integer ($int64) | Identifiant de l'étape |
| numeroEmbarque *  | integer ($int64) | Numéro d'embarquement                                                     |
| codeExploitant   | Code exploitant    |
| privacy   | boolean |  true / false |


\* paramètre obligatoire 

Réponse : Boolean (succès/échec de l'opération)


#### Réponses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
500 INTERNAL SERVER ERROR
```
## Analyses de vie privée/usage privé

[Documentation supplémentaire sur SWAGGER](ocean/restapi/common/openapi/explorer#?route=post-/analyse/preformattedPrivacy)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
POST /restapi/analyse/preformattedPrivacy
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId  | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |


\* paramètre obligatoire 

Réponse : Analyses détaillées incluant :

Synthèses par conducteur/véhicule
Consommations (carburant, électricité)
Distances et durées
Coûts
Informations véhicules (motorisation, équipements)

#### Réponses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
500 INTERNAL SERVER ERROR
```

#### Résultat

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
