---
title: Usage Pro/Privee
description: 
published: true
date: 2025-11-25T11:45:29.845Z
tags: 
editor: markdown
dateCreated: 2025-11-25T11:16:09.120Z
---

# Gestion des Usages pro / privée 

Ces API permettent de gérer les horaires de vie privée et d'analyser l'usage privé/professionnel des véhicules et conducteurs.

- [Récupération la liste des individus](#récupération-list-des-individus)

> *Horaire vie privée récurrent*
> - [Récupération des horaires de vie privée récurrentes](#récupération-des-horaires-de-vie-privée-récurrentes)
> - [Création/Modification des horaires de vie privée](#créationmodification-des-horaires-de-vie-privée)
> - [Supprime des horaires de vie privée récurrentes d'un individu](#supprime-des-horaires-de-vie-privée-récurrentes-dun-individu)

> *Horaire vie privée exceptionnelle*
> - [Récupération des horaires de vie privée exceptionnelle](#récupération-des-horaires-de-vie-privée-exceptionnelle)
> - [Création/Modification des horaires de vie privée exceptionnelles](#créationmodification-des-horaires-de-vie-privée)
> - [Supprime des horaires de vie privée exceptionnelles d'un individu](#supprime-des-horaires-de-vie-privée-récurrentes-dun-individu)
{.is-info}

Pour utiliser les différents webservices, il est nécessaire d'utiliser des identifiants internes pour vos individus 
(par exemple, idChauffeur) ou pour les étapes (idEtape, correspondant à la fiche jour). 
Ces éléments sont facilement accessibles via les webservices suivants :

[Vehicles](/fr/web-services/flotte#récupérer_les_données_des_véhicules) GET /vehicule_engin/vehicles
[trajets-et-positions](/fr/web-services/trajets-et-positions#récupérer-la-fiche−journalière-d’un-véhicule-pour-une-date-donnée) GET /mobility/v1/ficheJour

## Récupération list des individus

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=post-/individus/list)
[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
POST /restapi/individus/list
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| criteria   | integer ($int64) | Critères de filtrage des individus dans le système|

liste des criteres possible :
WITHOUT_USER : individu sans utilisateur de créé
WITH_USER : avec utilisateur associé
WITH_ENTITE : avec entité organisationnelle rattachée
WITH_GSM : avec informations de téléphonie mobile
WITH_VEHICLE : avec véhicule(s) associé(s)
Allowed: WITHOUT_USER | WITH_USER | WITH_ENTITE | WITH_GSM | WITH_VEHICLE|                                                     |


\* paramètre obligatoire 

Réponse : Liste des individus du client 
À noter : idCivilite : MR = 1 ; MME = 2 ; MLLE = 3.

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

## Récupération des horaires de vie privée récurrentes

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=get-/vieprivee/v1/horairesViePriveeRecurrentesIndividu)
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
    "id": 1110000002,->horaireIndividuIds pour la suppression
    "individu": {
      "id": 1110000403,
      "nomInd": "Individu",
      "prenomInd": "Vie privée",
      "matriculeInd": null,
      "gsm": null,
      "email": null,
      "suppressionLogique": false,
      "idCivilite": 1,
      "initialesInd": null
    },
    "horaire": {
      "id": 1110000087,
      "idJourSemaine": "LUNDI",
      "typeHoraires": "VIE_PRIVEE",
      "debutHeure": 0,
      "finHeure": 8,
      "debutMinute": 0,
      "finMinute": 0
    },
    "debut": 1767222000000,
    "fin": null
  },
  {
    "id": 1110000004,
    "individu": {
      "id": 1110000403,
      "nomInd": "Individu",
      "prenomInd": "Vie privée",
      "matriculeInd": null,
      "gsm": null,
      "email": null,
      "suppressionLogique": false,
      "idCivilite": 1,
      "initialesInd": null
    },
    "horaire": {
      "id": 1110000089,
      "idJourSemaine": "MARDI",
      "typeHoraires": "VIE_PRIVEE",
      "debutHeure": 0,
      "finHeure": 8,
      "debutMinute": 0,
      "finMinute": 0
    },
    "debut": 1767222000000,
    "fin": null
  }  
]
```
#### Curl

```JSON
curl -X GET "https:/https://v3.oceansystem.com/ocean/restapi/vieprivee/v1/horairesViePriveeRecurrentesIndividu?customerId=1110000000&individuId=1110000004"
```

## Création/Modification des horaires de vie privée

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=post-/vieprivee/v1/horairesViePriveeRecurrentesIndividu)

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
Attention ! Dans le corps de l'appel, bien mettre les horaires définis comme données dans le résultat "innerMap".

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
    "map": {
      "LUNDI": {
        "VIE_PRIVEE": [
          {
            "idJourSemaine": "LUNDI",
            "typeHoraires": "VIE_PRIVEE",
            "debutHeure": 0,
            "finHeure": 8,
            "debutMinute": 0,
            "finMinute": 0
          },
          {
            "idJourSemaine": "LUNDI",
            "typeHoraires": "VIE_PRIVEE",
            "debutHeure": 12,
            "finHeure": 13,
            "debutMinute": 0,
            "finMinute": 30
          },
          {
            "idJourSemaine": "LUNDI",
            "typeHoraires": "VIE_PRIVEE",
            "debutHeure": 18,
            "finHeure": 23,
            "debutMinute": 0,
            "finMinute": 59
          }
        ]
      }
    }
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

## Supprime des horaires de vie privée récurrentes d'un individu

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=delete-/vieprivee/v1/horairesViePriveeRecurrentesIndividu)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
delete /restapi/vieprivee/v1/horairesViePriveeRecurrentesIndividu
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId  | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| individuId *  | integer ($int64) | Identifiant du conducteur.                                                      |
| horaireIndividuIds   | integer ($int64 | Identifiant de l'horaire individu correspond au champ Id dans le GET de horairesViePriveeRecurrentesIndividu     |


\* paramètre obligatoire 

Réponse : 204 OK ou none
#### Réponses

```application/json;charset=utf-8
204 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
500 INTERNAL SERVER ERROR
```

#### Résultat

```JSON
{
  
}
```
#### Curl

```JSON
curl -X DELETE "https://v3.oceansystem.com/ocean/restapi/vieprivee/v1/horairesViePriveeRecurrentesIndividu?customerId=1110000000&individuId=1110000403&horaireIndividuIds=90359" \
  -H "x-auth-token: 7fd67be08f1cca392dfd5d0cda4377eabae1cdacce54237538cd8aad3d6575396fe92cedc528389a37bbf1486cf56ee5eceee9f210b3c32f0a66d704bab8239b"
}'
```

## Récupération des horaires de vie privée exceptionnelles

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=get-/vieprivee/v1/horairesViePriveeExceptionnellesIndividu)
[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
GET /restapi/vieprivee/v1/horairesViePriveeExceptionnellesIndividu
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| individuId   | integer ($int64) | Identifiant du conducteur.                                                      |
| dateDebut   | date | La date de début au format "dd/MM/yyyy HH:mm:ss Z" (Format: dd/MM/yyyy HH:mm:ss Z)           |
| dateFin   | date | La date de fin au format "dd/MM/yyyy HH:mm:ss Z" (Format: dd/MM/yyyy HH:mm:ss Z)               |


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
                  "extension": {
                          "id": 18524,
                          "description": "NOEL"
                  },
                  "utilisateur": {
                          "id": 2000000015,
                          "nomUti": "Chef de ",
                          "prenomUti": "projet",
                          "loginUti": "ocean-cdp",
                          "emailUti": "prototype@oceansystem.com",
                          "suppressionLogique": false,
                          "individu": null,
                          "utilisateurType": "SUPERUSER",
                          "dateFinValidite": null
                  },
                  "individu": {
                          "id": 1110000004,
                          "nomInd": "Jean",
                          "prenomInd": "Edouardo",
                          "matriculeInd": null,
                          "gsm": null,
                          "email": "edouardo.jean@orange.com",
                          "suppressionLogique": false,
                          "idCivilite": 1,
                          "initialesInd": null
                  },
                  "debut": 1829692800000,
                  "fin": 1829779200000,
                  "horairesIndividu": [
                          {
                                  "id": 90377,
                                  "individu": {
                                          "id": 1110000004,
                                          "nomInd": "Jean",
                                          "prenomInd": "Edouardo",
                                          "matriculeInd": null,
                                          "gsm": null,
                                          "email": "edouardo.jean@orange.com",
                                          "suppressionLogique": false,
                                          "idCivilite": 1,
                                          "initialesInd": null
                                  },
                                  "horaire": {
                                          "id": 1642185,
                                          "idJourSemaine": "SAMEDI",
                                          "typeHoraires": "VIE_PRIVEE_EXCEPTIONNELLE",
                                          "debutHeure": 0,
                                          "finHeure": 24,
                                          "debutMinute": 0,
                                          "finMinute": 0
                                  },
                                  "debut": 1829692800000,
                                  "fin": 1829779200000
                          },
                           ],
                  "description": "BLABLA2",
                  "id": 18521
          }
]
```
#### Curl

```JSON
curl -X GET "https://v3.oceansystem.com/ocean/restapi/vieprivee/v1/horairesViePriveeExceptionnellesIndividu?customerId=1110000000&individuId=1110000004"
```

## Création/Modification des horaires de vie privée

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=get-/vieprivee/v1/horairesViePriveeExceptionnellesIndividu)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
POST /restapi/vieprivee/v1/horaireViePriveeExceptionnelleIndividu
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId  | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| individuId *  | integer ($int64) | Identifiant du conducteur.                                                      |
| dateDebut   | date | La date de début au format "dd/MM/yyyy HH:mm:ss Z" (Format: dd/MM/yyyy HH:mm:ss Z)           |
| dateFin   | date | La date de fin au format "dd/MM/yyyy HH:mm:ss Z" (Format: dd/MM/yyyy HH:mm:ss Z)               |
| extensionIdToUpdate   | integer ($int64) | id de l'horaire exceptionnnelle à mettre à jour   |


\* paramètre obligatoire 

Réponse : Boolean (succès/échec de l'opération)
Attention ne mettre un extensionIdToUpdate que dans le cas d'une modification 

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
 True/False
}
```
#### Curl

```JSON
curl -X POST "https://v3.oceansystem.com/ocean/restapi/vieprivee/v1/horaireViePriveeExceptionnelleIndividu?customerId=1110000000&individuId=1110000004&description=NOEL&dateDebut=25%2F12%2F2027+00%3A00%3A00+Z&dateFin=26%2F12%2F2027+00%3A00%3A00+Z"
```

## Supprime des horaires de vie privée exceptionnelles d'un individu

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=delete-/vieprivee/v1/horairesViePriveeExceptionnellesIndividu)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
delete /restapi/vieprivee/v1/horairesViePriveeExceptionnellesIndividu
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId  | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| horaireExtensionIds   | integer ($int64 | Identifiant de l'horaire exceptionnel correspond au champ Id dans le GET de horairesViePriveeExceptionnellesIndividu ->extension->id    |


\* paramètre obligatoire 

Réponse : 204 OK ou none
#### Réponses

```application/json;charset=utf-8
204 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
500 INTERNAL SERVER ERROR
```

#### Résultat

```JSON
{
  
}
```
#### Curl

```JSON
curl -X DELETE "https://v3.oceansystem.com/ocean/restapi/vieprivee/v1/horairesViePriveeExceptionnellesIndividu?customerId=1110000000&horaireExtensionIds=18524"\
  -H "x-auth-token: 7fd67be08f1cca392dfd5d0cda4377eabae1cdacce54237538cd8aad3d6575396fe92cedc528389a37bbf1486cf56ee5eceee9f210b3c32f0a66d704bab8239b"
}'
```


## Gestion des demandes de passage vie privée/pro à posteriori

Enregistre/Supprime une demande de passage en vie privée/vie pro à posteriori pour une étape

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=post-/vieprivee/v1/etapeViePriveePosteriori)

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
#### Résultat
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

## Analyses de vie privée/usage privé

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#lo?route=post-/analyse/preformattedPrivacy)

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

> **Modèle de données en entrée :**

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
