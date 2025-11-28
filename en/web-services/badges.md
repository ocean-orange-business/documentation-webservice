---
title: Badge Management
description: 
published: true
date: 2025-11-27T11:45:29.845Z
tags: 
editor: markdown
dateCreated: 2025-11-27T11:16:09.120Z
---

# Badge Management

These APIs allow managing individual badges.

- [create an individual](#create-an-individual)
- [assign an entity to anindividual](#assign-an-entity-to-an-individual)
- [delete individual](#delete-individual)
- [modify individual](#modify-individualu)

Data formats 
Dates in ISO 8601 format 
JSON responses 
Support for enumerations for specific types

## Create an individual
Creates a new individual with all their information.

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=get-/individus/create)
[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post)  and token passing in the  **X-AUTH-TOKEN** header

### Endpoint {.tabset}

#### Endpoint
```
POST /restapi/individus/create
```

#### Request parameters

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Customer identifier. Required only for multi-client users |
| individuId   | integer ($int64) | Driver identifier.                                                      |
| entityStart   | date | Start date in the most common ISO DateTime format "yyyy-MM-dd'T'HH:mm:ss.SSSXXX" (ISO Format: yyyy-MM-dd'T'HH:mm:ss.SSSXXX)         |
| entityEnd   | date | End date in the most common ISO DateTime format "yyyy-MM-dd'T'HH:mm:ss.SSSXXX" (ISO Format: yyyy-MM-dd'T'HH:mm:ss.SSSXXX)               |


\* required parameter 


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
"oceanStatus": "oceanStatus",
"message": "message"
}
]
```

#### Curl

```JSON
curl -X POST "https://v3.oceansystem.com/ocean/restapi/individus/create" \
  -H "content-type: application/json" \
  -H "x-auth-token: 838432519fd251884b43c0b83e82bd7b7913ee43d2c9bba7ad8d6d33a4168826075a134986cdc4611a3b97925890b0a837515523d3d683f941e6c1bac5233ae1" \
  -d '{
    "individu": {   "nomInd": "nomInd",   "gsm": "gsm",   "matriculeInd": "matriculeInd",   "initialesInd": "initialesInd",   "prenomInd": "prenomInd",   "id": "",   "email": "email",   "suppressionLogique": false,   "idCivilite": 0
    },
    "entite": {   "id": "",   "nom": "nom",   "suppressionLogique": false
    },
    "utilisateur": {   "emailUti": "emailUti",   "prenomUti": "prenomUti",   "loginUti": "loginUti",   "individu": {       "nomInd": "nomInd",       "gsm": "gsm",       "matriculeInd": "matriculeInd",       "initialesInd": "initialesInd",       "prenomInd": "prenomInd",       "id": "",       "email": "email",       "suppressionLogique": false,       "idCivilite": 0   },   "nomUti": "nomUti",   "id": "",   "dateFinValidite": "2025-11-27T15:30:15.353Z",   "suppressionLogique": false,   "utilisateurType": "CLASSIC"
    },
    "groupe": {   "descriptionGrp": "descriptionGrp",   "id": "",   "suppressionLogique": false
    },
    "fonctionnalites": [   {       "idFonctionnalite": 0   }
    ],
    "propSpecifiqueDTO": {   "proprietesSpecifiquesClient": {       "psValues": {}   },   "ville": "ville",   "dateFCO": "2025-11-27T15:30:15.353Z",   "objectifMensuel": 0,   "dateNaissanceConducteur": "2025-11-27T15:30:15.353Z",   "nationalitePermis": 0,   "idClient": 0,   "lieuNaissanceConducteur": "lieuNaissanceConducteur",   "numeroVoieAdresse": "numeroVoieAdresse",   "typeObjet": "CLIENT",   "idObjetRef": 0,   "objectifHebdo": 0,   "codePostal": "codePostal",   "keyUser": "keyUser",   "lieuDelivrancePermis": "lieuDelivrancePermis",   "complementAdresse": "complementAdresse",   "dateVisiteMedicale": "2025-11-27T15:30:15.353Z",   "categoriePermis": [       "A"   ],   "dateValiditePermis": "2025-11-27T15:30:15.354Z",   "numeroPermis": "numeroPermis",   "adresse": "adresse",   "dateDelivrancePermis": "2025-11-27T15:30:15.354Z",   "id": "",   "pays": 0
    },
    "vehicleFieldsDTO": {   "numeroSerie": "numeroSerie",   "typeMotorisation": "MONO",   "categorie": "UNDEFINED",   "nomImage": "nomImage",   "odirectMode": "ODIRECT_UNIVERSEL",   "couleur": "couleur",   "description": "description",   "numeroParc": "numeroParc",   "marque": "marque",   "suppressionLogique": false,   "privacyEnabled": false,   "geolocalise": false,   "libelleTypeAsset": {       "categorie": "UNDEFINED",       "ordre": 0,       "libelle": "libelle",       "nomIcone": "nomIcone",       "id": ""   },   "modele": "modele",   "dispositifIdentifiant": false,   "immobilisationCablee": false,   "id": "",   "dioEnabled": false,   "immatriculation": "immatriculation",   "numeroEmbarque": 0,   "geosecuriteEnabled": false,   "detectionPorteEnabled": false
    }
}'
```


## Assign an entity to an individual
Assigns an individual to an entity for a given period

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=post-/individus/affectation-entite/add)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
POST /restapi/individus/affectation-entite/add
```

#### Request parameters

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId  | integer ($int64) | Customer identifier. Required only for multi-client users |
| individuId   | integer ($int64) | Individual identifier.                                                      |
| entiteId   | integer ($int64) | Entity identifier.                                                      |
| startDate   | date | La date de début au format "dd/MM/yyyy HH:mm:ss Z" (Format: dd/MM/yyyy HH:mm:ss Z)           |
| endDate   | date | La date de fin au format "dd/MM/yyyy HH:mm:ss Z" (Format: dd/MM/yyyy HH:mm:ss Z)               |


\* required parameter 

Response: Boolean (success/failure of the operation)


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
headers: {
<any-key>: {
}
}
body: {
}
status: {
}
}
```

#### Curl

```JSON
curl -X POST "https://v3.oceansystem.com/ocean/restapi/individus/affectation-entite/add" \
  -H "x-auth-token: 838432519fd251884b43c0b83e82bd7b7913ee43d2c9bba7ad8d6d33a4168826075a134986cdc4611a3b97925890b0a837515523d3d683f941e6c1bac5233ae1"
```


## Delete individual

Deletes an individual from the system

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean/restapi/common/openapi/explorer#?route=post-/individus/delete)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Definition {.tabset}

#### Endpoint
```
POST /restapi/individus/delete
```

#### Request parameters

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| idEtape  | integer ($int64) | Identifiant de l'étape |
| numeroEmbarque *  | integer ($int64) | Numéro d'embarquement                                                     |
| codeExploitant   | Code exploitant    |
| privacy   | boolean |  true / false |


\* required parameter 

Response: Boolean (success/failure of the operation)


#### Responses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST - Invalid input parameters
401 UNAUTHORIZED
403 FORBIDDEN
429 TOO MANY REQUEST 
500 INTERNAL SERVER ERROR
```

#### Curl

```JSON
curl -X POST "https://v3.oceansystem.com/ocean/restapi/individus/delete" \
  -H "x-auth-token: 838432519fd251884b43c0b83e82bd7b7913ee43d2c9bba7ad8d6d33a4168826075a134986cdc4611a3b97925890b0a837515523d3d683f941e6c1bac5233ae1"
```


## Modify individual
Updates information of an existing individual

[Documentation supplémentaire sur SWAGGER](ocean/restapi/common/openapi/explorer#?route=post-/individus/update)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
POST /restapi/individus/update
```

#### Request parameters

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId  | integer ($int64) | Customer identifier. Required only for multi-client users |


\* required parameter 

Structure: Identical to creation, allows complete modification

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
     "oceanStatus": "",
     "message": ""
}
]
```

#### Curl

```JSON
curl -X POST "https://v3.oceansystem.com/ocean/restapi/individus/update" \
  -H "content-type: application/json" \
  -H "x-auth-token: 838432519fd251884b43c0b83e82bd7b7913ee43d2c9bba7ad8d6d33a4168826075a134986cdc4611a3b97925890b0a837515523d3d683f941e6c1bac5233ae1" \
  -d '{
    "individu": {   "nomInd": "nomInd",   "gsm": "gsm",   "matriculeInd": "matriculeInd",   "initialesInd": "initialesInd",   "prenomInd": "prenomInd",   "id": "",   "email": "email",   "suppressionLogique": false,   "idCivilite": 0
    },
    "entite": {   "id": "",   "nom": "nom",   "suppressionLogique": false
    },
    "utilisateur": {   "emailUti": "emailUti",   "prenomUti": "prenomUti",   "loginUti": "loginUti",   "individu": {       "nomInd": "nomInd",       "gsm": "gsm",       "matriculeInd": "matriculeInd",       "initialesInd": "initialesInd",       "prenomInd": "prenomInd",       "id": "",       "email": "email",       "suppressionLogique": false,       "idCivilite": 0   },   "nomUti": "nomUti",   "id": "",   "dateFinValidite": "2025-11-27T15:51:04.019Z",   "suppressionLogique": false,   "utilisateurType": "CLASSIC"
    },
    "groupe": {   "descriptionGrp": "descriptionGrp",   "id": "",   "suppressionLogique": false
    },
    "fonctionnalites": [   {       "idFonctionnalite": 0   }
    ],
    "propSpecifiqueDTO": {   "proprietesSpecifiquesClient": {       "psValues": {}   },   "ville": "ville",   "dateFCO": "2025-11-27T15:51:04.020Z",   "objectifMensuel": 0,   "dateNaissanceConducteur": "2025-11-27T15:51:04.020Z",   "nationalitePermis": 0,   "idClient": 0,   "lieuNaissanceConducteur": "lieuNaissanceConducteur",   "numeroVoieAdresse": "numeroVoieAdresse",   "typeObjet": "CLIENT",   "idObjetRef": 0,   "objectifHebdo": 0,   "codePostal": "codePostal",   "keyUser": "keyUser",   "lieuDelivrancePermis": "lieuDelivrancePermis",   "complementAdresse": "complementAdresse",   "dateVisiteMedicale": "2025-11-27T15:51:04.020Z",   "categoriePermis": [       "A"   ],   "dateValiditePermis": "2025-11-27T15:51:04.020Z",   "numeroPermis": "numeroPermis",   "adresse": "adresse",   "dateDelivrancePermis": "2025-11-27T15:51:04.020Z",   "id": "",   "pays": 0
    },
    "vehicleFieldsDTO": {   "numeroSerie": "numeroSerie",   "typeMotorisation": "MONO",   "categorie": "UNDEFINED",   "nomImage": "nomImage",   "odirectMode": "ODIRECT_UNIVERSEL",   "couleur": "couleur",   "description": "description",   "numeroParc": "numeroParc",   "marque": "marque",   "suppressionLogique": false,   "privacyEnabled": false,   "geolocalise": false,   "libelleTypeAsset": {       "categorie": "UNDEFINED",       "ordre": 0,       "libelle": "libelle",       "nomIcone": "nomIcone",       "id": ""   },   "modele": "modele",   "dispositifIdentifiant": false,   "immobilisationCablee": false,   "id": "",   "dioEnabled": false,   "immatriculation": "immatriculation",   "numeroEmbarque": 0,   "geosecuriteEnabled": false,   "detectionPorteEnabled": false
    }
}'
```
