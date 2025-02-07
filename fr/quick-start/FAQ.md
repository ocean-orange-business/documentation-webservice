---
title: Faq
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-31T14:18:55.046Z
---

# FAQ d'utilisation des Webservices

### Quick Start

## 1. Quel est le statut du webservice `/positionsVehicles/lastPosition` ?
Le webservice `/positionsVehicles/lastPosition` est déprécié. Il n'est pas recommandé de l'utiliser.

## 2. Comment utiliser le webservice `/positionsVehicles/lastPosition` ?
Bien que son utilisation ne soit pas encouragée, si nécessaire, ce webservice fonctionne uniquement via une liste d'immatriculations. Il n'est pas prévu par entité.

### Exemple d'utilisation :
![last_position.png](/last_position.png)

## 3. Quel webservice devrais-je utiliser à la place ?
Il est recommandé d'utiliser le webservice suivant :
- **`/positions/search`** : Ce webservice permet de récupérer les positions d'un ou plusieurs véhicules entre deux dates.

## 4. Comment obtenir toutes les immatriculations de mon entité ?
Pour obtenir toutes les immatriculations de votre entité, vous pouvez utiliser le webservice suivant :
- **`vehicule-engin-controllerWS`** pour la gestion des véhicules.
  - **GET** `/vehicule_engin/vehicles` : Ce webservice récupère les véhicules et entités d'un client. Il renverra tous les véhicules de l'entité ainsi que leurs informations, y compris l'immatriculation.

## Conclusion
Pour une utilisation optimale des webservices, privilégiez les alternatives recommandées et évitez les services dépréciés.
