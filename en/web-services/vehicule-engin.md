---
title: Vehicule Engin
description: 
published: true
date: 2025-02-20T17:02:29.845Z
tags: 
editor: markdown
dateCreated: 2025-02-20T17:02:29.845Z
---

# Vehicle Management

This API allows you to retrieve:
* The identifier of multiple vehicles based on their registration numbers.

## Retrieve Vehicle Identifier from Registration Number

Prior authentication is required, and the token must be passed in the header **X-AUTH-TOKEN**.

### Definition {.tabset}

#### Endpoint
```
get /restapi/vehicule_engin/ids-from-immats
```

#### Paramètres de la requête

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId *   | integer ($int64) |  Client identifier. Required only for multi-client users |
| immatriculations* | Array(String) | Registration numbers of the vehicles for which you want to retrieve the identifier             |

\* required parameter 

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Result
```JSON
{
  "immatriculation": 0,
  "immatriculation": 0,
  "immatriculation": 0
}
```
