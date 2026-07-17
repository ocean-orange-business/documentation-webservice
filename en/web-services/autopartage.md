---
title: Car Sharing (Autopartage)
description: 
published: true
date: 2026-07-16T15:00:00.000Z
tags: 
editor: markdown
dateCreated: 2026-07-16T15:00:00.000Z
---

# Car Sharing (Autopartage)

This API allows you to check the reservation availability of the vehicles in the car sharing fleet:

- Reservable vehicles with their unavailability periods over a given time slot,
- Vehicles available for a reservation over a given time slot.

> These web services require the **Autopartage** (car sharing) module to be active on the customer account. Without this module, calls are rejected.
{.is-warning}

> The `dateDebut` and `dateFin` parameters must be in UTC format: "dd/MM/yyyy HH:mm:ss Z" (URL-encoded). Only this format is accepted by our API; the ISO format is rejected (422 UNPROCESSABLE ENTITY).
{.is-info}

## Retrieve reservable vehicles with their unavailability periods

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint

```
get /restapi/autopartage/v1/vehicules-reservables-with-indispo
```

#### Request parameters

| Name        | Type             | Description                                                                                      |
| ----------- | ---------------- | ------------------------------------------------------------------------------------------------ |
| customerId  | integer ($int64) | Customer identifier. Mandatory only for a multi-customer user                                    |
| dateDebut * | string           | The start date must be in UTC format: "dd/MM/yyyy HH:mm:ss Z". Only this format is accepted by our API. |
| dateFin *   | string           | The end date must be in UTC format: "dd/MM/yyyy HH:mm:ss Z". Only this format is accepted by our API.   |

\* mandatory parameter 

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
422 UNPROCESSABLE ENTITY (invalid date format)
429 Too Many Requests
```

#### Result

```JSON
[
  {
    "vehicule": {
      "immatriculation": "string",
      "marque": "string",
      "modele": "string",
      "couleur": "string",
      "numeroEmbarque": 0,
      "numeroSerie": "string",
      "numeroParc": "string"
    },
    "parking": {
      "id": 0,
      "denominationPoi": "string"
    },
    "indisponibilite": {
      "id": 0,
      "debut": "date",
      "fin": "date",
      "detail": "string"
    },
    "entite": {
      "id": 0,
      "nom": "string"
    },
    "activeAffectationPeriod": {
      "debut": "date",
      "fin": "date"
    },
    "activeIndisponibilitePeriod": {
      "debut": "date",
      "fin": "date"
    }
  }
]
```

#### Curl

```application/json;charset=utf-8
curl -X GET "https://v3.oceansystem.com/ocean/restapi/autopartage/v1/vehicules-reservables-with-indispo?dateDebut=01%2F07%2F2026%2008%3A00%3A00%20%2B0000&dateFin=01%2F07%2F2026%2018%3A00%3A00%20%2B0000" -H "X-AUTH-TOKEN: <token>"
```

## Retrieve vehicles available for a reservation

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header

### Definition {.tabset}

#### Endpoint

```
get /restapi/autopartage/v1/vehiclesAvailableForReservation
```

#### Request parameters

| Name            | Type             | Description                                                                                      |
| --------------- | ---------------- | ------------------------------------------------------------------------------------------------ |
| customerId      | integer ($int64) | Customer identifier. Mandatory only for a multi-customer user                                    |
| entiteId        | integer ($int64) | Identifier of a car sharing fleet                                                                |
| dateDebut *     | string           | The start date must be in UTC format: "dd/MM/yyyy HH:mm:ss Z". Only this format is accepted by our API. |
| dateFin *       | string           | The end date must be in UTC format: "dd/MM/yyyy HH:mm:ss Z". Only this format is accepted by our API.   |
| categorie *     | string           | The vehicle category code                                                                        |
| nombrePassagers | integer ($int32) | The number of people the vehicle must accommodate                                                |
| parkingId       | integer ($int64) | Parking identifier                                                                               |

\* mandatory parameter 

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
422 UNPROCESSABLE ENTITY (invalid date format)
429 Too Many Requests
```

#### Result

```JSON
[
  {
    "immatriculation": "string",
    "marque": "string",
    "modele": "string",
    "couleur": "string",
    "capacity": 0,
    "parking": {
      "id": 0,
      "denominationPoi": "string"
    },
    "eligibleCleDematerialisee": true,
    "physicalKey": true,
    "identifiantRFID": true,
    "identifiantSmartphone": true
  }
]
```

#### Curl

```application/json;charset=utf-8
curl -X GET "https://v3.oceansystem.com/ocean/restapi/autopartage/v1/vehiclesAvailableForReservation?dateDebut=01%2F07%2F2026%2008%3A00%3A00%20%2B0000&dateFin=01%2F07%2F2026%2018%3A00%3A00%20%2B0000&categorie=VL" -H "X-AUTH-TOKEN: <token>"
```
