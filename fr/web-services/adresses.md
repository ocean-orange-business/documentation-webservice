---
title: adresses
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-24T13:15:58.912Z
---

# Gestion des adresses de référence

Cette API permet de :

- Créer une adresse de référence.
- Modifier une adresse de référence.
- Supprimer une adresses de référence.
- Récupérer toute la liste des adresses de référence.

## Créer une adresse de référence

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
post /restapi/pois/createPoi
```

#### Paramètres de la requête

| Nom        | Type   | Description                                                                                                                                                                 |
| :--------- | :----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                                                                 |
| poi *      | object | Objet JSON décrivant le point d’intérêt. Pour le format de l’objet se référer à sa description dans https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/createPoiUsingPOST |
| externalId | string | Identifiant Externe (s’il provient d’un autre Système d’information)                                                                                                        |
| source     | string | Source de l’identifiant externe (champs libre, ex. nom d’un logiciel pour le stockage des adresses de référence)                                                            |

\* paramètre mandataire

#### Réponses

```application/json;charset=utf-8
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```json
{
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
}
```

## Modifier une adresse de référence

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

 [Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/updatePoiUsingPOST)

### Définition {.tabset}

#### Endpoint

```
post /restapi/pois/updatePoi
```

#### Paramètres de la requête

| Nom | Type   | Description                                                                                                                                                                  |
| --- | ------ | :--------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                                                           |
| poi * | object | Objet JSON décrivant le point d’intérêt. Pour le format de l’objet se référer à sa description dans https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/createPoiUsingPOST  |

\* paramètre mandataire

#### Réponses

```application/json;charset=utf-8
200 OK
201 CREATED
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```application/json;charset=utf-8
{
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
}
```

## Supprimer une adresse de référence

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/deletePoiUsingPOST)

### Définition {.tabset}

#### Endpoint

```
post /restapi/pois/deletePoi
```

#### Paramètres de la requête

| Nom     | Type             | Description                                                 |
| ------- | ---------------- | ----------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| idPoi * | integer ($int64) | Identifiant technique de l’adresse de référence à supprimer |

\* paramètre mandataire

#### Réponses

```application/json;charset=utf-8
201 Created
204 No Content
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Récupérer toute la liste des adresses de référence

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/pois)
### Définition {.tabset}

#### Endpoint

```
get /restapi/pois/pois
```

#### Paramètres de la requête

| Nom                    | Type             | Description                                                          |
| ---------------------- | ---------------- | -------------------------------------------------------------------- |
| customerId *           | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| searchCenterLongitudeX | number ($double) | Longitude                                                            |
| searchCenterLatitudeY  | number ($double) | Latitude                                                             |
| searchRadius           | integer ($int32) | iRayon (en mètre)                                                    |
| externalId             | string           | Identifiant Externe (s’il provient d’un autre Système d’information) |
| libelleTypePoiId       | integer ($int64) | Identifiant d'un libellé type                                        |
| source                 | string           | Source de l’identifiant externe (ex. POI Fleet)                      |
| withZone               | boolean          | Ajout des POIs zones ou non. Valeur par défaut : false               |

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
[
  {
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
  }
]
```
