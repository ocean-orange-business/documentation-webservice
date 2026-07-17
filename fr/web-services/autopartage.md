---
title: Autopartage
description: 
published: true
date: 2026-07-16T15:00:00.000Z
tags: 
editor: markdown
dateCreated: 2026-07-16T15:00:00.000Z
---

# Autopartage

Cette API permet de consulter la disponibilité à la réservation des véhicules du parc autopartage :

- Les véhicules réservables avec leurs périodes d'indisponibilité sur un créneau donné,
- Les véhicules disponibles pour une réservation sur un créneau donné.

> Ces web services nécessitent que le module **Autopartage** soit actif sur le compte client. Sans ce module, les appels sont refusés.
{.is-warning}

> Les paramètres `dateDebut` et `dateFin` doivent être au format UTC : "dd/MM/yyyy HH:mm:ss Z" (URL-encodé). Seul ce format est pris en compte par notre API ; le format ISO est rejeté (422 UNPROCESSABLE ENTITY).
{.is-info}

## Récupérer les véhicules réservables avec leurs périodes d'indisponibilité

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
get /restapi/autopartage/v1/vehicules-reservables-with-indispo
```

#### Paramètres de la requête

| Nom         | Type             | Description                                                                                                          |
| ----------- | ---------------- | -------------------------------------------------------------------------------------------------------------------- |
| customerId  | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                      |
| dateDebut * | string           | La date de début doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API. |
| dateFin *   | string           | La date de fin doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API.   |

\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
422 UNPROCESSABLE ENTITY (format de date invalide)
429 Too Many Requests
```

#### Résultat

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

## Récupérer les véhicules disponibles pour une réservation

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
get /restapi/autopartage/v1/vehiclesAvailableForReservation
```

#### Paramètres de la requête

| Nom             | Type             | Description                                                                                                          |
| --------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------- |
| customerId      | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                      |
| entiteId        | integer ($int64) | Identifiant d'un parc autopartage                                                                                    |
| dateDebut *     | string           | La date de début doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API. |
| dateFin *       | string           | La date de fin doit être au format UTC : "dd/MM/yyyy HH:mm:ss Z". Seul ce format est pris en compte par notre API.   |
| categorie *     | string           | Le code de la catégorie de véhicule                                                                                  |
| nombrePassagers | integer ($int32) | Le nombre de personnes que doit contenir le véhicule                                                                 |
| parkingId       | integer ($int64) | Identifiant du parking                                                                                               |

\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
422 UNPROCESSABLE ENTITY (format de date invalide)
429 Too Many Requests
```

#### Résultat

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
