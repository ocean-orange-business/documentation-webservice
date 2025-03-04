---
title: Gestion des accès
description: 
published: true
date: 2025-01-23T16:26:10.725Z
tags: 
editor: markdown
dateCreated: 2024-12-05T13:01:11.758Z
---

# Gestion des accès

Cette API permet de :

-   [Authentification par requête GET](#authentification-par-requête-post)
-   [Authentification par requête POST](#authentification-par-requête-post)
-   [Modification du mot de passe](#modifier-le-mot-de-passe-de-lutilisateur) => authentification,
-   [Réinitialisation du mode de passe](#r%C3%A9initialiser-le-mot-de-passe-par-lenvoi-dun-email) => authentification,
-   [Gestion des autorisations aux fonctionnalités par utilisateur](#trouve-les-droitsfonctionnalit%C3%A9s-%C3%A0-lapplication-pour-un-utilisateur) => autorisation.

> Le token n’est valable que 12 heures. Au-delà de ce délai, il faudra en générer un nouveau.
{.is-warning}

## Authentification par requête GET

### Définition {.tabset}

#### Endpoint

```
post /restapi/auth/authenticate * Deprecated
```

#### Paramètres de la requête

| Nom                 | Type   | Description                      |
| ------------------- | ------ | -------------------------------- |
| login *             | string | Identifiant                      |
| password *          | string | Mot de passe                     |
\* paramètre obligatoire

#### Réponses
```application/json;charset=utf-8
200 OK
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```JSON
{
  "additionalAccountData": {},
  "passwordExpirationRemainingDays": 0,
  "token": "string"
  Durée du token 12 heures
}
```

## Authentification par requête POST

### Définition {.tabset}

#### Endpoint

```
post /restapi/auth/authenticate2
```

#### Corps de la requête

```JSON
{
    "login": "Identifiant quelconque",
    "password": "Mot de passe fort et protégé"
}
```

#### Réponses
```application/json;charset=utf-8
200 OK
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```JSON
{
  "additionalAccountData": {},
  "passwordExpirationRemainingDays": 0,
  "token": "string"
  Durée du token 12 heures
}
```

## Modifier le mot de passe de l'utilisateur

[Authentification préalable nécessaire](#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/authentification/changePasswordUsingPOST)

### Définition {.tabset}

#### Endpoint

```
post /restapi/auth/changePassword
```

#### Paramètres de la requête

| Nom                    | Type   | Description                      |
| ---------------------- | ------ | -------------------------------- |
| actualPassword *       | string | Mot de passe actuel              |
| newPassword *          | string | Nouveau mot de passe             |
| newPasswordConfirmed * | string | Nouveau mot de passe à confirmer |
\* paramètre obligatoire

#### Réponses

```application/json;charset=utf-8
200 OK
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Réinitialiser le mot de passe par l’envoi d’un email

[Authentification préalable nécessaire](#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/authentification/requestPasswordResetUsingPOST)

### Définition {.tabset}

#### Endpoint
```
post /restapi/auth/requestPasswordReset
```

#### Paramètres de la requête

| Nom    | Type    | Description                                                                               |
| ------ | ------- | ----------------------------------------------------------------------------------------- |
| login * | boolean | Login de l’utilisateur pour lequel il y a une demande de réinitialisation du mot de passe |
| url    | string  | Url de l’application                                                                      |
\* paramètre obligatoire 

#### Réponses
```application/json;charset=utf-8
200 OK
204 No Content
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Trouver les droits/fonctionnalités à l'application pour un utilisateur

[Authentification préalable nécessaire](#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

Ce web services permet de trouver tous les droits/fonctionnalités (avec un contenu détaillé) à l'application pour un utilisateur.

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/authorization/findFunctionalitiesDetailedUsingGET)

### Définition {.tabset}

#### Endpoint

```
get /restapi/authorization/functionalities_detailed
```

#### Paramètres de la requête

| Nom    | Type    | Description                        |
| ------ | ------- | ---------------------------------- |
| customerId    | integer ($int64)| Identifiant du client. Obligatoire uniquement pour un utilisateur multi-client |
| elementType * | string - Enum | Type d’élément de l’application (Lien, Onglet, Web service, Action)  |
\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Résultat

```JSON
[
  {
    "enumCode": "string",
    Code pour décrire la fonctionnalité
    "fonctionnaliteDto": {
      "description": "string",
    Description de la fonctionnalité
      "idFonctionnalite": 0,
    Identifiant unique de la fonctionnalité dans le système d’information Océan
      "ordre": 0,
    Ordre d'affichage de la fonctionnalité
      "typeElement": "string"
    Action/Onglets/Lien/Menu/WsAction/Onglets/Lien/Menu/Ws
    }
  }
]
```

## Récupérer les contrats de location des véhicules

[Authentification préalable nécessaire](#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/)

### Définition {.tabset}

#### Endpoint

```
get /restapi/contrat_location/contrats
```

#### Paramètres de la requête

| Nom           | Type             | Description                                                                                                                                             |
| ------------- | ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId ** | integer ($int64) | Identifiant du client. Obligatoire pour un utilisateur multi-client                                                                                     |
| date          | string           | Filtre sur les contrats actifs à cette date. La date doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API |
| vehicleIds    | array (of int)   | Filtre sur les véhicules identifiés (nombre illimité)                                                                                                   |
\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Résultat

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

## Récupérer les derniers événements

[Authentification préalable nécessaire](#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/)

### Définition {.tabset}

#### Endpoint

```
get /restapi/evenement/lastEvent
```

#### Paramètres de la requête

| Nom            | Type             | Description                                                                                                          |
| -------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------- |
| customerId *   | integer ($int64) | Identifiant du client                                                                                                |
| vehiculesIds   | array (of int)   | Identifiant du véhicule                                                                                              |
| entitiesIds    | array (of int)   | Identifiant de l’entité                                                                                              |
| dateDebut      | string           | La date de début doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API. |
| dateFin        | string           | La date de fin doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API.   |
| codeEvenements * | array (of int)   | Identifiant de l’événement                                                                                         |
\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Résultat

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
  },
  "additionalProp3": {
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

## Récupérer les données des matériels

[Authentification préalable nécessaire](#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/materiel/getMaterielsUsingGET)

### Définition {.tabset}

#### Endpoint

```
get /restapi/materiel/list
```

#### Paramètres de la requête

| Nom         | Type           | Description                                            |
| ----------- | -------------- | ------------------------------------------------------ |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-client |
| materielIds | array (of int) | Liste des identifiants des matériels (nombre illimité) |

\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Résultat

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
