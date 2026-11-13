---
title: Trajets et positions
description: 
published: true
date: 2025-01-15T14:31:29.466Z
tags: 
editor: markdown
dateCreated: 2024-12-05T13:02:16.432Z
---

# Trajets et positions

Cette API permet de récupérer :

- Les trajets journaliers effectués à titre professionnel pour les véhicules,
- Les positions de tous les véhicules autorisés pour l’utilisateur,
- Les dernières positions des véhicules / matériels,
- Les positions des véhicules / matériels entre 2 dates,
- La fiche journalière d’un véhicule pour une date donnée,
- La fiche journalière normalisée de plusieurs véhicules pour une période donnée (prochainement disponible).


## Récupérer les positions d'un ou plusieurs véhicules entre deux dates : 2

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/obtention-positions-vehicules/getTabPosVehUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
get /restapi/positions/search
```

#### Paramètres de la requête


| Nom                         | Type              | Description                                                                                                                                                                                                                                                                                                                     |
| --------------------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId                  | integer ($int64)  | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                                                                                                                                                                                                                                 |
| immatriculation             | array (of string) | Liste des immatriculations des véhicules                                                                                                                                                                                                                                                                                        |
| startDate                   | string            | La date de début au format DateHeure ISO le plus courant ‘yyyy-MM-dd’T’HH:mm:ss.SSSXXX’ (exemple : “2000-10-30T01:30:00.000Z”). Ne doit pas être plus ancienne que 2 mois.<br>                                                                                                                                                  |
| endDate                     | string            | La date de fin au format DateHeure ISO le plus courant ‘yyyy-MM-dd’T’HH:mm:ss.SSSXXX’ (exemple : “2000-10-30T01:30:00.000Z”). Ne doit pas être plus ancienne que 2 mois.                                                                                                                                                        |
| byStorageDate               | boolean           | Permet de rechercher les positions sur les horodates de stockage et non pas les horodates des positions                                                                                                                                                                                                                         |
| withPrivacy                 | boolean           | Indique si les positions doivent être renvoyées en VP. Valeur par défaut = true                                                                                                                                                                                                                                                 |
| addressEnrichmentDisable    | boolean           | Si true, désactive entièrement l'enrichissement d'adresses (reverse geocoding).                                                                                                                                                                                                                                                 |
| addressEnrichmentEtatMobile | boolean           | \|   \|   \|<br>\|---\|---\|<br>\|Filtre sur les états mobiles pour l'enrichissement d'adresses. Accepte les codes : STOPPED, STOP_ACTION, TRAVELING, WAITING, START_ACTION, ENGINE_UP, UNDEFINED, UNDEFINED_STATE, OUT_OF_ORDER, PRIVACY. Plusieurs valeurs possibles (paramètre répétable). Par défaut : aucun filtre.\|   \| |

\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
429 Too Many Requests
```

#### Résultat

```JSON
{
  "positionsVehicles": [
    {
      "positions": [
        {
          "date": "date",
          "matriculeChauffeur": "matriculeChauffeur",
          "address": {
            "country": "country",
            "address": "address",
            "town": "town",
            "postalCode": "postalCode"
          },
          "latitudeY": 0,
          "approximationMeter": 0,
          "consommationThermiqueL": {},
          "chauffeur": "chauffeur",
          "etat": "etat",
          "vitesseKmh": 0,
          "distanceDepuisPosPrecMeter": 0,
          "cap": 0,
          "typePoi": "typePoi",
          "longitudeX": 0,
          "initialesChauffeur": "initialesChauffeur",
          "adresseDeReference": "adresseDeReference",
          "timestamp": 0
        }
      ],
      "vehicle": {
        "typeMotorisationEnergie": "MONO_ELECTRIQUE",
        "idVehicule": 0,
        "immatriculation": "immatriculation",
        "descriptionVehicule": "descriptionVehicule"
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

## Récupérer les positions d'un ou plusieurs véhicules entre deux dates 

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/obtention-positions-vehicules/getTabPosVehUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

> Version obsolète
{.is-warning}

### Définition {.tabset}

#### Endpoint

```
get /restapi/positionsVehicles/betweenDate
```

#### Paramètres de la requête

| Nom             | Type              | Description                                                                                                                  |
| --------------- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| immatsVeh       | array (of string) | Liste des immatriculations des véhicules                                                                                     |
| login *         | string            | Identifiant                                                                                                                  |
| password *      | string            | Mot de passe                                                                                                                 |
| dateDebut       | string            | La date de début doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API. Elle ne doit pas être plus ancienne que 2 mois. |
| dateFin         | string            | La date de fin doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API.           |
| parDateStockage | boolean           | Si « vrai », la méthode va chercher les positions sur les horodates des positions.                                           |

\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
429 Too Many Requests
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

## Récupérer la dernière position d'un ou plusieurs véhicules

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/obtention-positions-vehicules/getPosAndStatusVehUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

> Version obsolète
{.is-warning}

### Définition {.tabset}

#### Endpoint
```
get /restapi/positionsVehicles/lastPosition
```

#### Paramètres de la requête


| Nom        | Type              | Description                                                                                   |
| ---------- | ----------------- | --------------------------------------------------------------------------------------------- |
| immatsVeh  | array (of string) | Liste des immatriculations des véhiculesListe des immatriculations des véhicules (50 maximum) |
| login *    | string            | Identifiant                                                                                   |
| password * | string            | Mot de passe                                                                                  |

\* paramètre obligatoire 

#### Réponses

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

## Récupérer tous les véhicules autorisés pour l'utilisateur avec leurs positions

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/mobility/getPositionsVehiclesUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/mobility/v1/vehiclePositions
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |

\* paramètre obligatoire 

#### Réponses

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

## Récupérer le trajet d’un véhicule

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/mobility/getTrajetUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/mobility/v1/trajet
```

#### Paramètres de la requête


| Nom        | Type             | Description                       |
| ---------- | ---------------- | --------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| travelId * | integer ($int64) | Identifiant du trajet du véhicule |

\* paramètre obligatoire 

#### Réponses

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

## Récupérer la fiche journalière d’un véhicule pour une date donnée

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/mobility/getFicheJourUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
get /restapi/mobility/v1/ficheJour
```

#### Paramètres de la requête

| Nom   | Type             | Description                                                                         |
| ----- | ---------------- | ----------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| vehId | integer ($int64) | Identifiant du véhicule pour lequel la fiche journalière est récupérée              |
| date  | string           | Date au format UTC : "dd/MM/yyyy". Seul ce format est pris en compte par notre API. |

\* paramètre obligatoire 

#### Réponses

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
*Valeur possibe du champ etat :  « start D » / « waiting T » / « traveling R » / « stop A»
```

#### Curl

```JSON
curl -X GET "https://v3.oceansystem.com/ocean/restapi/mobility/v1/ficheJour?customerId=1110000000&vehId=12345&date=03%2F11%2F2026" \
  -H "x-auth-token: <VOTRE_TOKEN>"
```

## Récupérer les positions d'un ou plusieurs matériels entre deux dates

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/materiel/getMaterielPosBetweenDateUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
get /restapi/materiel/positionBetween
```

#### Paramètres de la requête

| Nom         | Type           | Description                                                                                                                                                |
| ----------- | -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                                                         |
| materielIds | array (of int) | Liste des identifiants des matériels (nombre illimité)                                                                                                     |
| dateDebut   | string         | La date de début doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API.                                       |
| dateFin     | string         | La date de fin doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API. La période ne doit pas dépasser 1 jour. |

\* paramètre obligatoire 

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

## Récupérer la fiche journalière normalisée des véhicules pour la période donnée

> ⚠️ **Ce web service n'est pas encore disponible en production.** Il le sera prochainement : d'ici là, un appel renvoie `404 NOT FOUND`.

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

Contrairement à [la fiche journalière d'un véhicule](#récupérer-la-fiche-journalière-d’un-véhicule-pour-une-date-donnée), cette version renvoie **une ligne par étape** (`rows`). Les entités qui se répètent (entités, véhicules, conducteurs, POI) ne sont pas dupliquées dans chaque ligne : elles sont sorties dans des index (`entitiesById`, `vehiclesById`, `individusById`, `poisById`), et chaque ligne y renvoie par son identifiant. Les totaux ne sont pas fournis : ils se recalculent à partir des lignes.

> La demande est limitée à **50 véhicules × jours** (jours calendaires, bornes incluses). Exemple : 1 véhicule sur 50 jours, ou 10 véhicules sur 5 jours. Au-delà, l'API répond `400 BAD REQUEST`.
{.is-warning}

### Définition {.tabset}

#### Endpoint

```
post /restapi/vehicule_engin/v2/fichesJoursVehicules
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |

\* paramètre obligatoire

#### Corps de la requête

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

| Nom           | Type                   | Description                                                                                                                                                         |
| ------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| periode *     | object                 | Période demandée. `debut` et `fin` sont obligatoires, au format ISO-8601 (ex. `"2026-11-01T00:00:00.000Z"`) ou en timestamp epoch en millisecondes.               |
| vehicleIds *  | array (of int)         | Identifiants des véhicules / engins. Au moins un identifiant, aucun nul. L'utilisateur doit avoir les droits sur chacun d'eux.                                      |
| criteria      | object                 | Critères de la fiche journalière (facultatif). Les champs optionnels des lignes ne sont renseignés que si le critère correspondant est demandé.                     |

\* paramètre obligatoire

**Critères les plus utiles (`criteria`)** : tous sont des booléens, `false` par défaut.

* `withDriver` : renseigne le conducteur de chaque étape (`individuId` et `individusById`).
* `withPoi` : renseigne le POI le plus proche du début et de la fin de l'étape (`startPoiId`, `endPoiId` et `poisById`).
* `withAddress` : renseigne les adresses de début et de fin (`startAddress`, `endAddress`).
* `withAffectationManuelle` : renseigne les affectations manuelles et par badge (`affectation`).
* `withBadg` : renseigne les informations de badgeage (`ndidLong`).
* `withUnifiedEvent` : renseigne les évènements de l'étape (`evenement`).
* `withRealConsumption` : renseigne la consommation réelle (`consommation`).
* `withCapacity` : renseigne la capacité de batterie (`capaciteBatterie`).
* `withChargeElectrique` : renseigne les données de charge d'un véhicule électrique (`chargeElectrique`).
* `withNoteEcoConduite` : calcule une note d'écoconduite par trajet (`ecoConduite`).
* `minDurationInSec` / `maxDurationInSec` : ne garde que les étapes dont la durée est supérieure / inférieure à la valeur donnée (en secondes).

#### Réponses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

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

**Description des champs d'une ligne (`rows`)** :

* `date` : jour de rattachement de l'étape, au format "dd/MM/yyyy".
* `entityId`, `vehicleId`, `individuId`, `startPoiId`, `endPoiId` : identifiants à résoudre dans `entitiesById`, `vehiclesById`, `individusById` et `poisById`.
* `type` : type d'étape (trajet, arrêt, …).
* `durationInSec` / `distanceInMeters` : durée de l'étape en secondes et distance parcourue en mètres.
* `inProgress` : `true` si l'étape est encore en cours.
* `anomalyType` : incohérence temporelle de l'étape. Elle ne concerne que les dates, jamais la consommation ni la distance.
* Les champs `individuId`, `ndidLong`, `affectation`, `startAddress`, `endAddress`, `startPoiId`, `endPoiId`, `evenement`, `consommation`, `capaciteBatterie`, `chargeElectrique`, `startLevelValue`, `stopLevelValue` et `ecoConduite` sont absents de la réponse tant que le critère correspondant n'a pas été demandé.

## Récupérer la dernière position d'un ou plusieurs matériels

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/materiel/getMaterialLastPositionUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

> Version obsolète
{.is-warning}

### Définition {.tabset}

#### Endpoint

```
get /restapi/materiel/lastPosition
```

#### Paramètres de la requête

| Nom         | Type           | Description                                            |
| ----------- | -------------- | ------------------------------------------------------ |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| materielIds | array (of int) | Liste des identifiants des matériels (nombre illimité) |

\* paramètre obligatoire 

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
