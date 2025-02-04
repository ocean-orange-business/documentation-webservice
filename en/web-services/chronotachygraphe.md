---
title: Tachograph
description: 
published: true
date: 2024-12-17T15:17:00.000Z
tags: 
editor: markdown
dateCreated: 2024-12-17T15:17:00.000Z
---

# Tachograph Controller

This API allows you to add new assignments for an individual tachograph.

## Add New Assignments for Individual Tachograph

### Definition {.tabset}

#### Endpoint
```
put /restapi/chronotachygraphe/affect
```

#### Request Parameters

| Name         | Type   | Description                                                                 |
|--------------|--------|-----------------------------------------------------------------------------|
| bdgSerial    | string | Badge serial number.                                                        |
| boxNumber    | string | Box serial number (field numero_serie_boi, this is not the SN).           |
| endDate      | string | End date in the format “dd/MM/yyyy HH:mm:ss Z”.                           |
| startDate    | string | Start date in the format “dd/MM/yyyy HH:mm:ss Z”.                         |

#### Responses

```application/json;charset=utf-8
200 OK
400 BAD REQUEST
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```
