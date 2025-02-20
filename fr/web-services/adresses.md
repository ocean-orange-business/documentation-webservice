---
title: Gestion des adresses de référence
description: 
published: true
date: 2025-01-27T15:44:17.333Z
tags: 
editor: markdown
dateCreated: 2024-12-05T13:01:19.545Z
---

# Gestion des adresses de référence

Cette API permet de :

- Créer une adresse de référence.
- Modifier une adresse de référence.
- Supprimer une adresse de référence.
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
| externalId | string | Identifiant externe (s’il provient d’un autre système d’information)                                                                                                        |
| source     | string | Source de l’identifiant externe (champs libre, ex. nom d’un logiciel pour le stockage des adresses de référence)                                                            |

\* paramètre mandatory

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
  Adresse de référence(150)
  "codePostalPoi": "string",
  Code postal de l’adresse de référence(20)
  "complementAdresse1Poi": "string",
	Complément d’adresse I(150)
  "complementAdresse2Poi": "string",
  Complément d’adresse II(150)
  "denominationPoi": "string",
	Dénomination de l’adresse de référence(150)
  "etatRegionPoi": "string",
  Région de l’adresse de référence(150)
  "geom": "string",
  Polygone contenant l’ensemble des points de l’adresse de référence
  "groupePoi": {
    "id": 0,
    Identifiant du groupe de l’adresse de référence
    "libelle": "string"
    Libellé de l’adresse de référence
  },
  "id": 0,
  Identifiant technique de l’adresse de référence
  "idPays": 0,
  Identifiant technique du pays
  "latPoi": 0,
  Latitude de l’adresse de référence
  "libelleTypePoi": {
    "color": "string",
    Couleur de l’adresse de référence
    "i18nKey": "string",
    la clé d’internalisation (français / english / español)
    "id": 0,
    Identifiant technique du libellé du type de l’adresse de référence
    "libelle": "string",
    Libellé de l’adresse de référence
    "nomImage": "string",    
    "ordre": 0,
     Ordre d’affichage de l’adresse de référence
    "type": "string"
		Type de l’adresse de référence
		Enum : UNDEFINED, OFFICE, HOME, PROVIDER, CLIENT, PROSPECT, GAS_STATION, RESTAURANT, OTHER
  },
  "longPoi": 0,
  Longitude de l’adresse de référence
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
  Rayon en mètre de l’adresse de référence
  "suppressionLogique": true,
  L’adresse est complètement supprimée
  "villePoi": "string"
	Ville
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

\* paramètre mandatory

#### Réponses

```application/json;charset=utf-8
200 OK
201 CREATED
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```json
{
  "adressePoi": "string",
  Adresse de référence(150)
  "codePostalPoi": "string",
  Code postal de l’adresse de référence(20)
  "complementAdresse1Poi": "string",
	Complément d’adresse I(150)
  "complementAdresse2Poi": "string",
  Complément d’adresse II(150)
  "denominationPoi": "string",
	Dénomination de l’adresse de référence(150)
  "etatRegionPoi": "string",
  Région de l’adresse de référence(150)
  "geom": "string",
  Polygone contenant l’ensemble des points de l’adresse de référence
  "groupePoi": {
    "id": 0,
    Identifiant du groupe de l’adresse de référence
    "libelle": "string"
    Libellé de l’adresse de référence
  },
  "id": 0,
  Identifiant technique de l’adresse de référence
  "idPays": 0,
  Identifiant technique du pays
  "latPoi": 0,
  Latitude de l’adresse de référence
  "libelleTypePoi": {
    "color": "string",
    Couleur de l’adresse de référence
    "i18nKey": "string",
    La clé d’internalisation (français / english / español)
    "id": 0,
    Identifiant technique du libellé du type de l’adresse de référence
    "libelle": "string",
    Libellé de l’adresse de référence
    "nomImage": "string",
    "ordre": 0,
    Ordre d’affichage de l’adresse de référence
    "type": "string"
		Type de l’adresse de référence
		Enum : UNDEFINED, OFFICE, HOME, PROVIDER, CLIENT, PROSPECT, GAS_STATION, RESTAURANT, OTHER
  },
  "longPoi": 0,
   Longitude de l’adresse de référence
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
  Rayon en mètre de l’adresse de référence
  "suppressionLogique": true,
  Suppression en base de données oui/non
  "villePoi": "string"
  Ville
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

\* paramètre mandatory

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

\* paramètre mandatory

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
  Adresse de référence(150)
  "codePostalPoi": "string",
  Code postal de l’adresse de référence(20)
  "complementAdresse1Poi": "string",
	Complément d’adresse I(150)
  "complementAdresse2Poi": "string",
  Complément d’adresse II(150)
  "denominationPoi": "string",
	Dénomination de l’adresse de référence(150)
  "etatRegionPoi": "string",
  Région de l’adresse de référence(150)
  "geom": "string",
  Polygone contenant l’ensemble des points de l’adresse de référence
  "groupePoi": {
    "id": 0,
    Identifiant du groupe de l’adresse de référence
    "libelle": "string"
    Libellé de l’adresse de référence
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
       "type": "string"
		Type de l’adresse de référence
		Enum : UNDEFINED, OFFICE, HOME, PROVIDER, CLIENT, PROSPECT, GAS_STATION, RESTAURANT, OTHER
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
   Rayon en mètre de l’adresse de référence
   "suppressionLogique": true,
   L’adresse est complètement supprimée
   "villePoi": "string"
	 Ville
  }
]
```
