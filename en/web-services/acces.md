---
title: acces
description: 
published: true
date: 2024-10-31T15:22:00.083Z
tags: 
editor: markdown
dateCreated: 2024-10-31T15:21:56.959Z
---

# Access Management

This API allows for:

- Password modification => authentication,
- Password reset => authentication,
- Management of feature permissions by user => authorization.

## Modify User Password

```
post /restapi/auth/changePassword
```

Prior authentication is required, and the token must be passed in the header **X-AUTH-TOKEN**.

> Note: The token is only valid for 12 hours. After this period, a new one must be generated.

### Request Parameters

| Name                  | Required    | Type   | Description                      |
| --------------------- | ----------- | ------ | -------------------------------- |
| actualPassword        | Yes         | string | Current password                 |
| newPassword           | Yes         | string | New password                     |
| newPasswordConfirmed  | Yes         | string | New password confirmation         |

### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

## Reset Password via Email

```
post /restapi/auth/requestPasswordReset
```
Prior authentication is required, and the token must be passed in the header **X-AUTH-TOKEN**.

> Note: The token is only valid for 12 hours. After this period, a new one must be generated.

### Request Parameters

| Name | Description |
| --- | --- |
| login | Required boolean - User's login for which the password reset request is made |

### Responses

## Find User Rights/Functionalities in the Application

get /restapi/authorization/functionalities\_detailed

Prior authentication is required, and the token must be passed in the header **X-AUTH-TOKEN**.

> Note: The token is only valid for 12 hours. After this period, a new one must be generated.

This web service allows you to find all rights/functionalities (with detailed content) in the application for a user.

### Request Parameters

| Name | Description |
| --- | --- |
| elementType | Required string - Enum Type of application element (Link, Tab, Web service, Action) |

### Responses
[](https://api-docs.oceansystem.com/fr/web-services/acces)

#### [**200** OK](https://grav.new-media.ovh/web-services/acces#detail-fonctionnalites-utilisateur-res-object-200)

```application/json;charset=utf-8
{
  "enumCode": "string",  // Code to describe the functionality
  "fonctionnaliteDto": {
    "description": "string",  // Description of the functionality
    "idFonctionnalite": "integer ($int32)",  // Unique identifier of the functionality in the Ocean information system
    "typeElement": "string"  // Action/Tabs/Link/Menu/WsAction/Tabs/Link/Menu/Ws
  }
}
