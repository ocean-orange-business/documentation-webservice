---
title: flotte
description: 
published: true
date: 2024-10-31T15:22:25.027Z
tags: 
editor: markdown
dateCreated: 2024-10-31T15:22:21.849Z
---

# Gestion de la flotte

{

| additionalProp1  { | object |
| --- | --- |
| Id | integer ($int64)  Identifiant du matériel   |
| evenementLibelle | string  Libellé de l’événement   |
| groupingPeriod | string  Période  : TODAY, YESTERDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY, LASTWEEK, TWOWEEKS\_AGO, THREEWEEKS\_AGO, FOURWEEKS\_AGO, FIVEWEEKS\_AGO, LAST\_MONTH, BEFORE\_LAST\_MONTH   |
| vehicleEngin  { | object |
| id | integer ($int64)  Identifiant du véhicule   |
| categorie | string - Enum  Catégorie du véhicule / engin : UNDEFINED, VL, ALL, VUL, VU, PL, PELLE, TRCTP, COMPR, GROUP, MINIPE, CHELEVT, CHELEVE, FINISS, CHARGE, FOREUSE, CONT, BENNE, REMORQUE, AUTRE\_MATERIEL, AUTRE\_ENGIN, AUTRE\_VEHICULE   |
| description | string (100)  Description du véhicule   |
| geosecuriteEnabled | boolean  Activation de géosecurité (oui/non)   |
| suppressionLogique | boolean  Suppression en base de données (oui/non)   |
| dispositifIdentifiant | boolean  Etat du dispositif identifiant (oui/non)   |
| privacyEnabled | boolean  Mode « Vie Privée » activé   |
| dioEnabled | boolean  Donnée sur une entrée/sortie dans le boitier oui/non (moteur auxiliaire, ...)   |
| nomImage | string  Nom de l’image du véhicule   |
| odirectMode | string  Mode O-Direct Renault/Peugeot/Kuantic …   |
| } |  |
| entite  { | object |
| id | integer ($int64)  Identifiant de l’entité   |
| nom | string (150)  Nom de l’entité   |
| suppressionLogique | boolean  Suppression en base de données (oui/non)   |
| } |  |
| adress  { | object |
| address | string (150)  Adresse de la position   |
| town | string (100)  Ville de la position   |
| country | string (100)  Pays de la position   |
| postCode | string (20)  Code postal de la position   |
| countryCode | string  Code postal de la position   |
| closestPoi | string (150)  Adresse de référence la plus proche   |
| Precision | integer ($int64)  Valeur de la précision de l’adresse de référence la plus proche   GPS calé : true/false   |
| latitudeY | number  Position latitude X   |
| longitudeX | string  Position longitude X   |
| cap | number  Cap position GPS   |
| } |  |
| TypeEVenement  | string - Enum  ENUM : DEMARRAGE, ARRET, BADGEAGE\_CHAUFFEUR…   |
| typeEvenementODirectDTO  { | objectRef |
| eventState | string  PUNCTUAL, OPEN, CLOSED   |
| dateDebut | string  Date de début   |
| dateFin | string  Date de fin   |
| extendedDataMap  { | object |
| ndid | string  Numéro du badge   |
| unit | string  Unité de l’extended Data (donnée supplémentaire à l’événement)   |
| anomalieId | integer ($int64)  Identifiant de l’anomalie   |
| zone | string  Zone   |
| forced | integer ($int64)  Forcer 0/1   |
| tank\_level\_before | integer ($int64)  Niveau du réservoir avant prise de carburant   |
| poiId | integer ($int64)  Identifiant de l’adresse de référence   |
| speed | integer ($int64)  Vitesse   |
| tank\_level\_after | integer ($int64)  Niveau du réservoir après prise de carburant   |
| } |  |
| heure | timestamp  Heure   |
| date | timestamp  Date   |
| } |  |

}