---
title: flotte
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

\* paramètre mandataire 

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
| includeFields   | Array of string | Champs à inclure (cf. Facebook Graph API) |

\* paramètre mandataire

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

## Récupérer les données des véhicules les plus proches

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
post /restapi/vehicule_engin/nearestVehicles
```

#### Paramètres de la requête

| Nom             | Type            | Description                               |
| --------------- | --------------- | ----------------------------------------- |
| customerId      | integer ($int64)| Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                     |
| radius          | integer ($int32)| Rayon de recherche                        |
| latitude        | double          | Latitude du point de départ de recherche  |
| longitude       | double          | Longitude du point de départ de recherche |
| resultsLimit    | integer ($int32)| Permet de spécifier le nombre de résultats à renvoyer pour le computeMode PAR_ROUTE (valeur comprise entre 1 et 10)    |

#### Corps de la requête

```JSON
{
  "computeMode":"VOL_OISEAU ou PAR_ROUTE",
  "radiusUnit":"string"
}
```

#### Réponses

```application/json;charset=utf-8
200 OK
201 Created
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Résultat

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
