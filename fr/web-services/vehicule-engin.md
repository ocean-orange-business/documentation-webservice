---
title: Vehicule Engin
description: 
published: true
date: 2025-02-20T17:02:29.845Z
tags: 
editor: markdown
dateCreated: 2025-02-20T17:02:29.845Z
---

# Gestion des véhicules

Cette API permet de récupérer :
* L'identifiant de plusieurs véhicules depuis leur immatriculation

## Récupérer l'identifiant d'un véhicule depuis son immatriculation

Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/vehicule_engin/ids-from-immats
```

#### Paramètres de la requête

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId *   | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| immatriculations* | Array(String) | Immatriculations des véhicules dont on veut récupérer l'identifiant             |

\* paramètre obligatoire 

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
  "immatriculation": 0,
  "immatriculation": 0,
  "immatriculation": 0
}
```
