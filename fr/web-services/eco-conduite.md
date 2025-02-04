---
title: Eco-Conduite
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-24T13:16:09.120Z
---

Cette API permet de récupérer :

- Les données liées à l’éco conduite des chauffeurs pour une période donnée,
- Les notes de « Sécurité » et « Consommation » par mois ou semaine.

## Récupérer les notes de sécurité et consommation par mois ou semaine

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getEchoattitudeGraphUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/ecoAttitude/v1/get_ecoattitude_graph
```

#### Paramètres de la requête

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId *   | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| individuId     | integer ($int64) | Identifiant du conducteur. |
| EC_MONTH_START | integer ($int32) | Mois de début              |
| EC_MONTH_END   | integer ($int32) | Mois de fin                |
| EC_YEAR_START  | integer ($int32) | Année de début             |
| EC_YEAR_END    | integer ($int32) | Année de fin               |
| EC_MODE        | string           | Au choix : semaine ou mois |

\* paramètre mandataire 

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

## Récupérer les données liées à l’éco conduite des chauffeurs pour une période donnée

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getDatasUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/ecoAttitude/v1/get_datas
```

#### Paramètres de la requête

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId *   | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| EC_MONTH_START | integer ($int32) | Mois de début              |
| EC_MONTH_END   | integer ($int32) | Mois de fin                |
| EC_YEAR_START  | integer ($int32) | Année de début             |
| EC_YEAR_END    | integer ($int32) | Année de fin               |
| EC_MODE        | string           | Au choix : semaine ou mois |

\* paramètre mandataire 

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
