---
title: eco-conduite
description: 
published: true
date: 2024-12-19T09:24:13.106Z
tags: 
editor: markdown
dateCreated: 2024-12-05T13:01:41.131Z
---

Cette API permet de récupérer :

- Les données liées à l’éco conduite des chauffeurs pour une période donnée,
- Les notes de « Sécurité » et « Consommation » par mois ou semaine.

## Récupérer les notes de sécurité et consommation par mois ou semaine



[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getEchoattitudeGraphUsingGET)

Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/ecoAttitude/v1/get_ecoattitude_graph
```

#### Paramètres de la requête

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| EC_MONTH_START | integer ($int32) | Mois de début              |
| EC_MONTH_END   | integer ($int32) | Mois de fin                |
| EC_YEAR_START  | integer ($int32) | Année de début             |
| EC_YEAR_END    | integer ($int32) | Année de fin               |
| EC_MODE        | string           | Au choix : semaine ou mois |
#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```
!Attention l'utilisateur du webservice doit être un utilisateur individuel pour avoir des data 
![roleindividu.png](/roleindividu.png)
Sinon vous aurez l'erreur 400 Bad request 
![erreurindividu_400.png](/erreurindividu_400.png)


## Récupérer les données liées à l’éco conduite des chauffeurs pour une période donnée



[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getDatasUsingGET)

Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/ecoAttitude/v1/get_datas
```

#### Paramètres de la requête


| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| EC_MONTH_START | integer ($int32) | Mois de début              |
| EC_MONTH_END   | integer ($int32) | Mois de fin                |
| EC_YEAR_START  | integer ($int32) | Année de début             |
| EC_YEAR_END    | integer ($int32) | Année de fin               |
| EC_MODE        | string           | Au choix : semaine ou mois |

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```
