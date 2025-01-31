---
title: Faq
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-31T14:18:55.046Z
---

# Web Services FAQ

## 1. What is the status of the `/positionsVehicles/lastPosition` web service?
The `/positionsVehicles/lastPosition` web service is deprecated. Its use is not recommended.

## 2. How do I use the `/positionsVehicles/lastPosition` web service?
Although its use is discouraged, if necessary, this web service only works via a list of license plates. It is not designed to work by entity.

### Example Usage:
*(See attached screenshot)*

## 3. Which web service should I use instead?
It is recommended to use the following web service:
- **`/positions/search`**: This web service allows you to retrieve the positions of one or more vehicles between two dates.

## 4. How can I get all the license plates for my entity?
To get all the license plates for your entity, you can use the following web service:
- **`vehicule-engin-controllerWS`** for vehicle management.
  - **GET** `/vehicule_engin/vehicles`: This web service retrieves the vehicles and entities of a client. It will return all vehicles for the entity along with their information, including the license plate.

## Conclusion
For optimal use of web services, prioritize the recommended alternatives and avoid deprecated services.
