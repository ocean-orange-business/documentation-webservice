---
title: eco-conduite
description: 
published: true
date: 2025-01-29T10:06:36.798Z
tags: 
editor: markdown
dateCreated: 2025-01-29T09:54:14.498Z
---

Cette API permet de récupérer :

- Les données liées à l’éco conduite des chauffeurs pour une période donnée,
- Les notes de « Sécurité » et « Consommation » par mois ou semaine.

## Récupérer les notes de sécurité et consommation par mois ou semaine

GET/restapi/ecoAttitude/v1/get_ecoattitude_graph

 [Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getEchoattitudeGraphUsingGET)

Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

Attention : le token n’est valable que 12 heures. Au-delà de ce délai, il faudra en générer un nouveau.

### Paramètres de la requête

|Nom|Description|
|---|---|
|EC_MONTH_START|integer ($int32)<br><br>Mois de début|
|EC_MONTH_END|integer ($int32)<br><br>Mois de fin|
|EC_YEAR_START|integer ($int32)<br><br>Année de début|
|EC_YEAR_END|integer ($int32)<br><br>Année de fin|
|EC_MODE|string<br><br>Au choix : semaine ou mois|

### Réponses

 [####  **200** OK

application/json;charset=utf-8](https://grav.new-media.ovh/web-services/eco-conduite#notes-securite-consommation-res-object-200)

|   |   |
|---|---|
|||
|||
|||

 [####  **401** UNAUTHORIZED

application/json;charset=utf-8](https://grav.new-media.ovh/web-services/eco-conduite#notes-securite-consommation-res-object-401)

 [####  **403** FORBIDDEN

application/json;charset=utf-8](https://grav.new-media.ovh/web-services/eco-conduite#notes-securite-consommation-res-object-403)

 [####  **404** NOT FOUND

application/json;charset=utf-8](https://grav.new-media.ovh/web-services/eco-conduite#notes-securite-consommation-res-object-404)

## Récupérer les données liées à l’éco conduite des chauffeurs pour une période donnée

GET/restapi/ecoAttitude/v1/get_datas

 [Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getDatasUsingGET)

Authentification préalable nécessaire et passage du token dans le header **X-AUTH-TOKEN**

Attention : le token n’est valable que 12 heures. Au-delà de ce délai, il faudra en générer un nouveau.

### Paramètres de la requête

|Nom|Description|
|---|---|
|EC_MONTH_START|integer ($int32)<br><br>Mois de début|
|EC_MONTH_END|integer ($int32)<br><br>Mois de fin|
|EC_YEAR_START|integer ($int32)<br><br>Année de début|
|EC_YEAR_END|integer ($int32)<br><br>Année de fin|
|EC_MODE|string<br><br>Au choix : semaine ou mois|

### Réponses

 [####  **200** OK

application/json;charset=utf-8](https://grav.new-media.ovh/web-services/eco-conduite#donnees-eco-conduite-res-object-200)

|   |   |
|---|---|
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||
|||

 [####  **401** UNAUTHORIZED

application/json;charset=utf-8](https://grav.new-media.ovh/web-services/eco-conduite#donnees-eco-conduite-res-object-401)

 [####  **403** FORBIDDEN

application/json;charset=utf-8](https://grav.new-media.ovh/web-services/eco-conduite#donnees-eco-conduite-res-object-403)

 [####  **404** NOT FOUND

application/json;charset=utf-8](https://grav.new-media.ovh/web-services/eco-conduite#donnees-eco-conduite-res-object-404)