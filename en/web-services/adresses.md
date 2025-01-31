---
title: adresses
description: 
published: true
date: 2024-10-31T15:22:05.508Z
tags: 
editor: markdown
dateCreated: 2024-10-31T15:22:01.422Z
---

# Management of Reference Addresses

This API allows for:

- Creating a reference address.
- Modifying a reference address.
- Deleting a reference address.
- Retrieving the entire list of reference addresses.

## Create a Reference Address

[Prior authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**.

### Définition {.tabset}

#### Endpoint

```
post /restapi/pois/createPoi
```

#### Request Parameters

| Name        | Type             | Description                                                                                                                                                                 |
| :--------- | :--------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Client Identifier. Required only for multi-client users.                                                                                                                   |
| poi *      | object           | JSON object describing the point of interest. For the object's format, refer to its description in https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/createPoiUsingPOST |
| externalId | string           | External Identifier (if it comes from another Information System).                                                                                                         |
| source     | string           | Source of the external identifier (free field, e.g., name of software for storing reference addresses).                                                                     |

\* mandatory parameter

#### Responses

```application/json;charset=utf-8
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```json
{
  "adressePoi": "string",      // Reference address (150)
  "codePostalPoi": "string",  // Postal code of the reference address (20)
  "complementAdresse1Poi": "string", // Address complement I (150)
  "complementAdresse2Poi": "string", // Address complement II (150)
  "denominationPoi": "string", // Name of the reference address (150)
  "etatRegionPoi": "string",  // Region of the reference address (150)
  "geom": "string",          // Polygon containing all points of the reference address
  "groupePoi": {
    "id": 0,                // Identifier of the reference address group
    "libelle": "string"     // Label of the reference address
  },
  "id": 0,                  // Technical identifier of the reference address
  "idPays": 0,              // Technical identifier of the country
  "latPoi": 0,              // Latitude of the reference address
  "libelleTypePoi": {
    "color": "string",       // Color of the reference address
    "i18nKey": "string",    // Internationalization key (French / English / Spanish)
    "id": 0,                // Technical identifier of the reference address type label
    "libelle": "string",     // Label of the reference address
    "nomImage": "string",   // Image name
    "ordre": 0,             // Display order of the reference address
    "type": "string"        // Type of the reference address
                             // Enum: UNDEFINED, OFFICE, HOME, PROVIDER, CLIENT, PROSPECT, GAS_STATION, RESTAURANT, OTHER
  },
  "longPoi": 0,             // Longitude of the reference address
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
  "rayonPoi": 0,            // Radius in meters of the reference address
  "suppressionLogique": true, // The address is completely deleted
  "villePoi": "string"      // City
}
```

## Modify a Reference Address

[Prior authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**.

 [Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/updatePoiUsingPOST)

### Definition {.tabset}

#### Endpoint

```
post /restapi/pois/updatePoi
```
#### Request Parameters

| Name        | Type             | Description                                                                                                                                                                  |
| :--------- | :--------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Client identifier. Required only for multi-client users.                                                                                                                   |
| poi *      | object           | JSON object describing the point of interest. For the object's format, refer to its description in https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/createPoiUsingPOST |

\* mandatory parameter

#### Responses


```application/json;charset=utf-8
200 OK
201 CREATED
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Result

```json
{
  "adressePoi": "string",      // Reference address (150)
  "codePostalPoi": "string",  // Postal code of the reference address (20)
  "complementAdresse1Poi": "string", // Address complement I (150)
  "complementAdresse2Poi": "string", // Address complement II (150)
  "denominationPoi": "string", // Name of the reference address (150)
  "etatRegionPoi": "string",  // Region of the reference address (150)
  "geom": "string",          // Polygon containing all points of the reference address
  "groupePoi": {
    "id": 0,                // Identifier of the reference address group
    "libelle": "string"     // Label of the reference address
  },
  "id": 0,                  // Technical identifier of the reference address
  "idPays": 0,              // Technical identifier of the country
  "latPoi": 0,              // Latitude of the reference address
  "libelleTypePoi": {
    "color": "string",       // Color of the reference address
    "i18nKey": "string",    // Internationalization key (French / English / Spanish)
    "id": 0,                // Technical identifier of the reference address type label
    "libelle": "string",     // Label of the reference address
    "nomImage": "string",   // Image name
    "ordre": 0,             // Display order of the reference address
    "type": "string"        // Type of the reference address
                             // Enum: UNDEFINED, OFFICE, HOME, PROVIDER, CLIENT, PROSPECT, GAS_STATION, RESTAURANT, OTHER
  },
  "longPoi": 0,             // Longitude of the reference address
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
  "rayonPoi": 0,            // Radius in meters of the reference address
  "suppressionLogique": true, // Database deletion (true/false)
  "villePoi": "string"      // City
}
```
## Delete a Reference Address

[Prior authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**.

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/deletePoiUsingPOST)

### Definition {.tabset}

#### Endpoint

```
post /restapi/pois/deletePoi
```

#### Request Parameters

| Name     | Type             | Description                                                              |
| ------- | ---------------- | ------------------------------------------------------------------------ |
| customerId * | integer ($int64) | Client identifier. Required only for multi-client users.                |
| idPoi * | integer ($int64) | Technical identifier of the reference address to be deleted.           |

\* mandatory parameter

#### Responses

```application/json;charset=utf-8
201 Created
204 No Content
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Retrieve the Entire List of Reference Addresses

[Prior authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**.

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/pois)
### Definition {.tabset}

#### Endpoint

```
get /restapi/pois/pois
```

#### Request Parameters

| Name                    | Type             | Description                                                              |
| ---------------------- | ---------------- | ------------------------------------------------------------------------ |
| customerId *           | integer ($int64) | Client identifier. Required only for multi-client users.                |
| searchCenterLongitudeX | number ($double) | Longitude                                                                |
| searchCenterLatitudeY  | number ($double) | Latitude                                                                 |
| searchRadius           | integer ($int32) | Radius (in meters)                                                       |
| externalId             | string           | External identifier (if it comes from another Information System).        |
| libelleTypePoiId       | integer ($int64) | Type label identifier                                                    |
| source                 | string           | Source of the external identifier (e.g., POI Fleet).                    |
| withZone               | boolean          | Whether or not to include zone POIs. Default value: false.              |

\* mandatory parameter

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Result

```json
 {
    "adressePoi": "string",      // Reference address (150)
    "codePostalPoi": "string",  // Postal code of the reference address (20)
    "complementAdresse1Poi": "string", // Address complement I (150)
    "complementAdresse2Poi": "string", // Address complement II (150)
    "denominationPoi": "string", // Name of the reference address (150)
    "etatRegionPoi": "string",  // Region of the reference address (150)
    "geom": "string",          // Polygon containing all points of the reference address
    "groupePoi": {
      "id": 0,                // Identifier of the reference address group
      "libelle": "string"     // Label of the reference address
    },
    "id": 0,                  // Technical identifier of the reference address
    "idPays": 0,              // Technical identifier of the country
    "latPoi": 0,              // Latitude of the reference address
    "libelleTypePoi": {
      "color": "string",       // Color of the reference address
      "i18nKey": "string",    // Internationalization key (French / English / Spanish)
      "id": 0,                // Technical identifier of the reference address type label
      "libelle": "string",     // Label of the reference address
      "nomImage": "string",   // Image name
      "ordre": 0,             // Display order of the reference address
      "type": "string"        // Type of the reference address
                               // Enum: UNDEFINED, OFFICE, HOME, PROVIDER, CLIENT, PROSPECT, GAS_STATION, RESTAURANT, OTHER
    },
    "longPoi": 0,             // Longitude of the reference address
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
    "rayonPoi": 0,            // Radius in meters of the reference address
    "suppressionLogique": true, // The address is completely deleted
    "villePoi": "string"      // City
  }
```

