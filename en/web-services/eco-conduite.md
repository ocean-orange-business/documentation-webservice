---
title: Eco-Driving
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-24T13:16:09.120Z
---

This API allows you to retrieve:

- Data related to the eco-driving of drivers for a given period,
- "Safety" and "Consumption" scores by month or week.

## Retrieve Safety and Consumption Scores by Month or Week

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getEchoattitudeGraphUsingGET)

[Prior authentication required](./acces.md#authentication-via-post-request) and passing the token in the header **X-AUTH-TOKEN**

### Definition {.tabset}

#### Endpoint
```
get /restapi/ecoAttitude/v1/get_ecoattitude_graph
```

#### Request Parameters

| Name            | Type             | Description                                                                                  |
| --------------- | ---------------- | -------------------------------------------------------------------------------------------- |
| customerId *    | integer ($int64) | Customer identifier. Required only for multi-client users                                   |
| individuId      | integer ($int64) | Driver identifier.                                                                          |
| EC_MONTH_START  | integer ($int32) | Start month                                                                                |
| EC_MONTH_END    | integer ($int32) | End month                                                                                  |
| EC_YEAR_START   | integer ($int32) | Start year                                                                                 |
| EC_YEAR_END     | integer ($int32) | End year                                                                                   |
| EC_MODE         | string           | Choose: week or month                                                                      |

\* mandatory parameter 

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Result

```JSON
{
  "conso": [
    0
  ],
  "date": [
    "string"
  ],
  "noteSimplifie": [
    0
  ],
  "secu": [
    0
  ]
}
```

## Retrieve Data Related to Eco-Driving of Drivers for a Given Period

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getDatasUsingGET)

[Prior authentication required](./acces.md#authentication-via-post-request) and passing the token in the header **X-AUTH-TOKEN**

### Definition {.tabset}

#### Endpoint
```
get /restapi/ecoAttitude/v1/get_datas
```

#### Request Parameters

| Name            | Type             | Description                                                                                  |
| --------------- | ---------------- | -------------------------------------------------------------------------------------------- |
| customerId *    | integer ($int64) | Customer identifier. Required only for multi-client users                                   |
| EC_MONTH_START  | integer ($int32) | Start month                                                                                |
| EC_MONTH_END    | integer ($int32) | End month                                                                                  |
| EC_YEAR_START   | integer ($int32) | Start year                                                                                 |
| EC_YEAR_END     | integer ($int32) | End year                                                                                   |
| EC_MODE         | string           | Choose: week or month                                                                      |

\* mandatory parameter

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
  "BILAN_CONSO_J": 0,
  "BILAN_CONSO_P": 0,
  "BILAN_DISTANCE_J": 0,
  "BILAN_DISTANCE_P": 0,
  "BILAN_EMISSION_CO2_J": 0,
  "BILAN_EMISSION_CO2_P": 0,
  "BILAN_TEMPS_CONDUITE_J": 0,
  "BILAN_TEMPS_CONDUITE_P": "string",
  "CFF_NOM": "string",
  "CFF_PRENOM": "string",
  "CONDUITE_MOY_PERIODE_ACCEL": 0,
  "CONDUITE_MOY_PERIODE_FREIN": 0,
  "CONDUITE_MOY_PERIODE_VIRAGES": 0,
  "CONDUITE_MOY_PERIODE_VITESSE": 0,
  "CONDUITE_USAGE_M_ARRET": "string",
  "CONDUITE_USAGE_M_DUREE_CHARGES": 0,
  "CONDUITE_USAGE_M_DUREE_REGIMES": 0,
  "CONDUITE_USAGE_M_ZONES_ROUGES": 0,
  "CONDUITE_Z_EXTRA_ACCEL": 0,
  "CONDUITE_Z_EXTRA_FREIN": 0,
  "CONDUITE_Z_EXTRA_VIRAGES": 0,
  "CONDUITE_Z_EXTRA_VITESSE": 0,
  "CONDUITE_Z_MIXTE_ACCEL": 0,
  "CONDUITE_Z_MIXTE_FREIN": 0,
  "CONDUITE_Z_MIXTE_VIRAGES": 0,
  "CONDUITE_Z_MIXTE_VITESSE": 0,
  "CONDUITE_Z_URBAINE_ACCEL": 0,
  "CONDUITE_Z_URBAINE_FREIN": 0,
  "CONDUITE_Z_URBAINE_VIRAGES": 0,
  "CONDUITE_Z_URBAINE_VITESSE": 0,
  "ECOATTITUDE_CONSO": 0,
  "ECOATTITUDE_SECU": 0,
  "MOY_ACC_PARC": 0,
  "MOY_FREIN_PARC": 0,
  "MOY_TYPO_ACC_PARC": {
    "additionalProp1": 0,
    "additionalProp2": 0,
    "additionalProp3": 0
  },
  "MOY_TYPO_FREIN_PARC": {
    "additionalProp1": 0,
    "additionalProp2": 0,
    "additionalProp3": 0
  },
  "MOY_TYPO_VIRAGES_PARC": {
    "additionalProp1": 0,
    "additionalProp2": 0,
    "additionalProp3": 0
  },
  "MOY_VIRAGES_PARC": 0,
  "RATIO_CMH_PARC": 0,
  "RATIO_RMH_PARC": 0,
  "TRAJETS_DISTANCE_MOYENNE": 0,
  "TRAJETS_NB": 0,
  "TRAJETS_TEMPS_MOYEN": "string",
  "VERSION_ECO": "string",
  "bilanJournalier": {
    "additionalProp1": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    },
    "additionalProp2": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    },
    "additionalProp3": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    }
  },
  "bilanPeriode": {
    "additionalProp1": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    },
    "additionalProp2": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    },
    "additionalProp3": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    }
  }
}
```
