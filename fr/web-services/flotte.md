---
title: Gestion de la flotte
description: 
published: true
date: 2025-01-27T16:27:40.067Z
tags: 
editor: markdown
dateCreated: 2024-12-05T13:02:01.324Z
---

# Gestion de la flotte

Cette API permet de récupérer :

- Les informations de la fiche du véhicule (nom, immatriculation, marque, modèle, catégorie, numéro de série du boîtier, compteur kilométrique (1 fois par jour) identité du conducteur, …),
- Les informations de la fiche matériel (nom, référence, marque, modèle, scénario de fonctionnement, message paramétré pour l’appui bouton, numéro de série de la balise, …),
- Les derniers évènements (pour les véhicules et les matériels),
- Les entités du client.
- Les affectations du chauffeur, son historique

## Récupérer les entités d’un client

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/mobility/getEntitiesUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/mobility/v1/entities
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

```json
{
  "entities": [
    {
      "id": 0,
      Identifiant de l’entité
      "nom": "string"
      Nom de l’entité
    }
  ]
}
```

## Récupérer les données des véhicules

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**
 [Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/vehiculeengin/getVehiclesUsingGET)
### Définition {.tabset}

#### Endpoint
```
get /restapi/vehicule_engin/vehicles
```

#### Paramètres de la requête

| Nom             | Type            | Description                               |
| --------------- | --------------- | ----------------------------------------- |
| customerId *    | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                                                           |
| immatriculation | string          | Immatriculation du véhicule               |

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
    "boitier": {
      "adBoi": "string",
      Ad du boitier (APC pour BBOXv1 obsolète) (50)
      "commentaireBoi": "string",
  		Le commentaire du boitier
      "coreGsmBoi": "string",
  		Numéro GSM du boitier
      "debutGarantie": "2024-12-17T16:14:51.577Z",
  		Début de la garantie du boitier
      "finGarantie": "2024-12-17T16:14:51.577Z",
  		Fin de la garantie du boitier
      "id": 0,
      Identifiant du boitier
      "idEtatBoitier": 0,
      Identifiant de l’état du boitier
      "imeiBoi": "string",
      Imei du boitier (15)
      "numeroSerieBoi": "string",
      Numéro de série du boitier (50)
      "sn": "string"
      SN (Serial Number) du boitier (30)
    },
    "chauffeur": {
      "email": "string",
      Email du chauffeur
      "gsm": "string",
      Téléphone du chauffeur
      "id": 0,
      Identifiant du boitier
      "idCivilite": 0,
      Identifiant du boitier
      "initialesInd": "string",
      "matriculeInd": "string",
      Matricule du chauffeur
      "nomInd": "string",
      Nom du chauffeur
      "prenomInd": "string",
      Prénom du chauffeur
      "suppressionLogique": true
    },
    "emissionCo2": 0,
    Taux émission de CO2
    "entite": {
      "id": 0,
      Identifiant de l’entité
      "nom": "string",
      Nom de l’entité (150)
      "suppressionLogique": true
    },
    "releve": {
      "dateReleve": "2024-12-17T16:14:51.577Z",
      Date du relevé de compteur kilométrique
      "id": 0,      
      Identifiant du relevé
      "value": 0
      Valeur du relevé de compteur kilométrique 
      à la fin de la journée précédente (valeur calculée à minuit)
    },
    "releveAjuste": {
      "dateReleve": "2024-12-17T16:14:51.577Z",
      Date du relevé de compteur kilométrique ajusté 
      "id": 0,
      Identifiant du relevé
      "value": 0
      valeur du compteur ajustée en fonction de la distance 
      ou du temps parcouru par le véhicule depuis le dernier relevé automatique
    },
    "vehicle": {
      "apcMode": "GPS",
      "boitierAvantCoupeCircuit": true,
      "buzzerSurvitesseEnabled": true,
      "categorie": "UNDEFINED",
      Catégorie du véhicule
      "categorieVehiculeEcoConduite": "UL",
      "couleur": "string",
      Couleur du véhicule (50)
      "coupeBatterie": true,
      "date1ereMec": "2024-12-17T16:14:51.577Z",
      "description": "string",
			Description du véhicule
      "detectionPorteEnabled": true,
      "dioEnabled": true,
			Donnée sur une entrée/sortie dans le boitier oui/non (moteur auxiliaire, ...)
      "dispositifIdentifiant": true,	
			Etat du dispositif identifiant (oui/non)
      "emissionCo2": 0,
      "etatEcoConduite": "ACTIF",
      "geolocalise": true,
      "geomissionEnabled": true,
			Activation de géomission (oui/non)
      "geosecuriteEnabled": true,
			Activation de géosecurité (oui/non)
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
			Marque du véhicule
      "modele": "string",
			Modèle du véhicule
      "nomImage": "string",
      "nombreCvFiscaux": 0,
      "numeroEmbarque": 0,
      "numeroParc": "string",
      "numeroSerie": "string",
			Numéro de série du véhicule
      "odirectMode": "ODIRECT_UNIVERSEL",
			Mode O-Direct Renault/Peugeot/Kuantic, …
      "privacyEnabled": true,
      Mode « Vie Privée » activé
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

## Récupérer une affectation (par son id)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /affectations_chauffeurs/get
```

#### Paramètres de la requête

| Nom           | Type             | Description                                                                     |
| ------------- | ---------------- | ------------------------------------------------------------------------------- |
| customerId    | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| idAffectation | integer ($int64) | Identifiant de l'affectation vehicule chauffeur                                 |
#### Réponses

```application/json;charset=utf-8
200 OK
201 Created
401 Unauthorized
403 Forbidden
429 Too Many Requests
500 Internal Server Error
```

#### Résultat

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


## Récupérer l'historique des affectations

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /affectations_chauffeurs/historique
```

#### Paramètres de la requête

| Nom        | Type             | Description                                                                     |
| ---------- | ---------------- | ------------------------------------------------------------------------------- |
| customerId | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| idVehicule | integer ($int64) | Identifiant du véhicule                                                         |
| idIndividu | integer ($int64) | Identifiant de l'affectation vehicule chauffeur                                 |
|            |                  |                                                                                 |

#### Réponses

```application/json;charset=utf-8
200 OK
201 Created
401 Unauthorized
403 Forbidden
429 Too Many Requests
500 Internal Server Error
```

#### Résultat

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
