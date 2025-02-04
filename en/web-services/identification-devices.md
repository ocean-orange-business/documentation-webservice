---
title: Management of Identification Devices
description: 
published: true
date: 2024-12-18T16:09:00.000Z
tags: 
editor: markdown
dateCreated: 2024-12-13T13:40:00.000Z
---

# Management of Identification Devices

This allows for the assignment of an identification device/badge to a manufacturer.

## Assign an Identification Device/Badge to a Driver

Prior authentication is required, and the token must be passed in the header **X-AUTH-TOKEN**.

### Definition {.tabset}

#### Endpoint
```
post /restapi/dispositifIdentifiant/affectation/create-affectation
```
#### Request Parameters
| Name            | Type             | Description                                                                                  |
| --------------- | ---------------- | -------------------------------------------------------------------------------------------- |
| customerId*     | integer ($int64) | Required only for multi-client users.                                                       |
| personId*       | integer ($int64) | Identifier of the individual.                                                                |
| identifierId*   | integer ($int64) | Identifier of the device.                                                                    |
| date_debut      | date             | Start date in the format “yyyy-MM-ddTHH:mm:ss.SSSZ”.                                       |
| date_fin*       | date             | End date in the format “yyyy-MM-ddTHH:mm:ss.SSSZ”.                                         |

\* mandatory parameter 

#### Request Body
```JSON
{
    "identifierId": 0,
    "personId": 0,
    "period": {
        "debut": "yyyy-MM-ddTHH:mm:ss.SSSZ",
        "fin": "yyyy-MM-ddTHH:mm:ss.SSSZ",
    }
}
```
#### Responses
```application/json;charset=utf-8
200 OK
201 CREATED
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```
