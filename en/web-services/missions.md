---
title: Missions Management
description: 
published: true
date: 2025-01-24T15:05:20.256Z
tags: 
editor: markdown
dateCreated: 2024-12-05T13:02:09.334Z
---

# Mission Management

This API allows you to:

-   Create a new mission
-   Modify an ongoing mission
-   Retrieve the status of a mission
-   Delete a mission

Note: This feature is only available to clients who have subscribed to web services in addition to a GéoPack or GéoPro solution..

## Create a New Mission

 [Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/geomission/ajouterMissionUsingPOST)

[Prior authentication is required.](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header.

### Definition {.tabset}

#### Endpoint

```
post /restapi/geomission/ajoutMission
```

#### Request Parameters

| Name            | Type               | Description                                                                                                          |
| --------------- | ------------------ | -------------------------------------------------------------------------------------------------------------------- |
| customerId   *  | integer ($int64)   | Client ID. Required only for multi-client users.                                                                     |
| idMission       | string             | Client-specific mission ID.                                                                                          |
| jourHeureInter  | string ($dateTime) | Intervention date, must be in UTC format: "dd/MM/yyyy HH:mm". Only this format is supported by our API.              |
| jourHeurePeremp | string ($dateTime) | Automatic deletion date on the screen, must be in UTC format: "dd/MM/yyyy HH:mm". Only this format is supported.     |
| typeMission     | string             | Mission type.                                                                                                        |
| nomVeh          | string             | Vehicle name.                                                                                                        |
| nomIndi         | string             | Individual's last name (if no vehicle is selected, the target recipient is an individual with first and last name).  |
| prenomIndi      | string             | Individual's first name (if no vehicle is selected, the target recipient is an individual with first and last name). |
| nomPrenom       | string             | Full name of the individual.                                                                                         |
| commentaire     | string             | Mission comment.                                                                                                     |
| adrRefCli       | string             | Client reference address name (truncated to 20 characters on site and screen display).                               |
| rue             | string             | Destination street.                                                                                                  |
| codPost         | string             | Destination postal code.                                                                                             |
| ville           | string             | Destination city.                                                                                                    |
| aEnvoyer        | boolean            | **TRUE** if the mission is to be sent, **FALSE** if the mission is only prepared.                                    |
| longitude       | number ($double)   | Destination longitude.                                                                                               |
| latitude        | number ($double)   | Destination latitude.                                                                                                |


#### Responses

```application/json;charset=utf-8
200 OK
201 Created
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Result

```JSON
{
  "message": "string"
  Return message from the WS (success/failure)
}
```

## Modify an ongoing mission

 [Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/geomission/modifierMissionUsingPOST)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header.

### Definition {.tabset}

#### Endpoint

```
post /restapi/geomission/modifierMission
```

#### Request Parameters

| Name            | Type               | Description                                                                                                          |
| --------------- | ------------------ | -------------------------------------------------------------------------------------------------------------------- |
| customerId *    | integer ($int64)   | Client ID. Required only for multi-client users.                                                                     |
| idMission       | string             | Client-specific mission ID.                                                                                          |
| jourHeureInter  | string ($dateTime) | Intervention date, must be in UTC format: "dd/MM/yyyy HH:mm". Only this format is supported by our API.              |
| jourHeurePeremp | string ($dateTime) | Automatic deletion date on the screen, must be in UTC format: "dd/MM/yyyy HH:mm". Only this format is supported.     |
| typeMission     | string             | Mission type.                                                                                                        |
| nomVeh          | string             | Vehicle name.                                                                                                        |
| nomIndi         | string             | Individual's last name (if no vehicle is selected, the target recipient is an individual with first and last name).  |
| prenomIndi      | string             | Individual's first name (if no vehicle is selected, the target recipient is an individual with first and last name). |
| nomPrenom       | string             | Full name of the individual.                                                                                         |
| commentaire     | string             | Mission comment.                                                                                                     |
| adrRefCli       | string             | Client reference address name (truncated to 20 characters on site and screen display).                               |
| rue             | string             | Destination street.                                                                                                  |
| codPost         | string             | Destination postal code.                                                                                             |
| ville           | string             | Destination city.                                                                                                    |
| aEnvoyer        | boolean            | **TRUE** if the mission is to be sent, **FALSE** if the mission is only prepared.                                    |
| longitude       | number ($double)   | Destination longitude.                                                                                               |
| latitude        | number ($double)   | Destination latitude.                                                                                                |

#### Responses

```application/json;charset=utf-8
200 OK
201 Created
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Result

```JSON
{
  "message": "string"
  Return message from the WS (success/failure)
}
```

## Retrieve the status of a mission

 [Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/geomission/getStatutMissionUsingGET)
 
[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header.

### Definition {.tabset}

#### Endpoint

```
get /restapi/geomission/statutMission
```

#### Request Parameters

| Name         | Type               | Description                                                                 |
| -------------| ------------------ | --------------------------------------------------------------------------- |
| customerId * | integer ($int64)   | Client ID. Required only for multi-client users.                            |
| idMission *  | string             | Client-specific mission ID.                                                 |
\* mandatory parameter

#### Responses

```application/json;charset=utf-8
200 OK
401 Unauthorized
403 Forbidden
404 Not Found
```

#### Result

```JSON
{
  "commentRefuseReason": "string", 
   Reason for refusal
  "complement": "string",          
   Additional information
  "externalMissionId": "string",   
   Technical mission ID
  "status": "string",              
   Mission status
  "statusCode": "string",          
   Mission status code
  "time": "string"                 
   Mission date
}
```

## Delete a mission

 [Additional SWAGGER Documentation](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/geomission/supprimerMissionUsingPOST)

[Prior authentication is required](./acces.md#authentification-par-requête-post) and the token must be included in the **X-AUTH-TOKEN** header.
 
### Definition {.tabset}

#### Endpoint

```
post /restapi/geomission/supprimerMission
```

#### Request Parameters

| Name         | Type               | Description                                                                 |
| -------------| ------------------ | --------------------------------------------------------------------------- |
| customerId * | integer ($int64)   | Client ID. Required only for multi-client users.                            |
| idMission *  | string             | Client-specific mission ID.                                                 |
\* mandatory parameter

#### Responses

```application/json;charset=utf-8
200 OK
201 CREATED
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Result
```
{
 "message": "string"
  Return message from the WS (success/failure)
}
```
