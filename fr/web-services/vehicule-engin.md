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
* L'identifiant d'un véhicule depuis son immatriculation

## Récupérer l'identifiant d'un véhicule depuis son immatriculation

Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/vehicule_engin/get-vehicle-id-from-immat
```

#### Paramètres de la requête

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId *   | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| immatriculation* | String         | Immatriculation            |

\* paramètre mandataire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat
```text
ID du véhicule
```
