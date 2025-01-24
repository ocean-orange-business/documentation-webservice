---
title: trajets-et-positions
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-24T13:16:27.247Z
---

# Trajets et positions

Cette API permet de récupérer :

- Les trajets journaliers effectués à titre professionnel pour les véhicules,
- Les positions de tous les véhicules autorisés pour l’utilisateur,
- Les dernières positions des véhicules / matériels,
- Les positions des véhicules / matériels entre 2 dates,
- La fiche journalière d’un véhicule pour une date donnée.


## Récupérer les positions d'un ou plusieurs véhicules entre deux dates : 2

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/obtention-positions-vehicules/getTabPosVehUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
get /restapi/positions/search
```

#### Paramètres de la requête


| Nom             | Type              | Description                                                                                                                                                                |
| --------------- | ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| byStorageDate   | boolean           | Permet de rechercher les positions sur les horodates de stockage et non pas les horodates des positions                            |
| customerId      | integer ($int64)  | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                                    |
| endDate         | string            | La date de fin doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API.                 |
| immatriculation | array (of string) | Liste des immatriculations des véhicules                                                                                           |
| startDate       | string            | La date de début au format DateHeure ISO le plus courant ‘yyyy-MM-dd’T’HH:mm:ss.SSSXXX’ (exemple : “2000-10-30T01:30:00.000Z”). Ne doit pas être plus ancienne que 2 mois. |
| withPrivacy     | boolean           | Indique si les positions doivent être renvoyées en VP. Valeur par défaut = true                                                    |

\* paramètre mandataire 

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

\* paramètre mandataire 

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

\* paramètre mandataire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
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

\* paramètre mandataire 

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

\* paramètre mandataire 

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

\* paramètre mandataire 

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

\* paramètre mandataire 

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

\* paramètre mandataire 

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
