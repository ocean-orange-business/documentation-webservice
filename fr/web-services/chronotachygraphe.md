---
title: Chronotachygraphe
description: 
published: true
date: 2024-12-17T15:17:00.000Z
tags: 
editor: markdown
dateCreated: 2024-12-17T15:17:00.000Z
---

# Contrôleur de chronotachygraphe(s)

Cette API permet d'ajouter de nouvelles affectations pour l'étape individuelle du Chronotachygraphe.

## Ajouter de(s) nouvelle(s) affectation(s) étape individu Chronotachygraphe

### Définition {.tabset}

#### Endpoint
```
put /restapi/chronotachygraphe/affect
```

#### Paramètres de la requête

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| bdgSerial      | string           | Numéro de série du badge   |
| boxNumber      | string           | Numéro de série du boîtier (champ numero_serie_boi, ce n’est pas le SN)                |
| endDate        | string           | La date de fin au format “dd/MM/yyyy HH:mm:ss Z”             |
| startDate      | string           | La date de début au format “dd/MM/yyyy HH:mm:ss Z”              |

#### Réponses

```application/json;charset=utf-8
200 OK
201 CREATED
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```
