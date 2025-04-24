---
title: Gestion des techniciens
description: 
published: true
date: 2025-03-03T09:54:20.256Z
tags: 
editor: markdown
dateCreated: 2025-03-03T09:54:20.256Z
---

# Gestion des techniciens

Cette API permet de :

- Attribuer les droits d'accès client à plusieurs techniciens
- Met à jour les informations d'un technicien

## Attribuer les droits d'accès client à plusieurs techniciens

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
post /restapi/technicien/grant-client-access
```

#### Paramètres de la requête

| Nom             | Type               | Description                                                                                                          |
| --------------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| emails          | string             | Email(s) du/des technicien(s) qu’on veut récupérer. Si vous voulez mettre plusieurs emails, séparez les par des ;    |
| codeExploitant  | string             | Code exploitant du client                                                                                            |
| dateFin         | string             | Date de fin de validité yyyy-MM-dd                                                                                   |

#### Réponses

```application/json;charset=utf-8
200 OK
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Met à jour les informations d'un technicien

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint

```
get /restapi/technicien/update
```

#### Paramètres de la requête

| Nom             | Type               | Description                                                                                                          |
| --------------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| customerId   *  | integer ($int64)   | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients                                      |

\* paramètre obligatoire

#### Corps de la requête

```JSON
{
  "distributeur": {
    "adresse": "string",
    "dateCreation": "2025-04-23T07:34:29.509Z",
    "designation": "string",
    "email": "string",
    "emailOperationnel": "string",
    "id": 0,
    "mapProvider": "GOOGLE_MAP",
    "telephone": "string"
  },
  "id": 0,
  "idUtilisateur": 0,
  "passwordValidityDurationNbDays": 0,
  "techos": {
    "description": "string",
    "id": 0,
    "suppressionLogique": true,
    "techType": "CLIENT"
  },
  "userclients": [
    {
      "client": {
        "codeExploitant": "string",
        "dateContentieux": "2025-04-23T07:34:29.509Z",
        "fuseauHoraire": "string",
        "id": 0,
        "nom": "string",
        "suppressionLogique": true
      },
      "utilisateur": {
        "dateFinValidite": "2025-04-23T07:34:29.509Z",
        "emailUti": "string",
        "id": 0,
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
        "loginUti": "string",
        "nomUti": "string",
        "prenomUti": "string",
        "suppressionLogique": true,
        "utilisateurType": "CLASSIC"
      },
      "utilisateurClientLightDTO": {
        "expirationDate": "string",
        "id": 0
      }
    }
  ],
  "utilisateur": {
    "dateFinValidite": "2025-04-23T07:34:29.509Z",
    "emailUti": "string",
    "id": 0,
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
    "loginUti": "string",
    "nomUti": "string",
    "numeroFaxUti": "string",
    "numeroGsmUti": "string",
    "numeroTelephoneUti": "string",
    "prenomUti": "string",
    "suppressionLogique": true,
    "utilisateurType": "CLASSIC"
  }
}
```

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat de la requête

Le résultat de la requête sera formaté de la même façon que le corps de cette requête.
