---
title: equipement-auxiliaire
description: 
published: true
date: 2024-10-31T15:22:20.566Z
tags: 
editor: markdown
dateCreated: 2024-10-31T15:22:17.475Z
---

# Equipement auxiliaire

\[ {

| dailyDioUtilisation   \[  { | object |
| --- | --- |
| dailyDurationSecForAllDio | integer ($int64)  Durée d’utilisation cumulée journalière de tous les équipements (en seconde)   |
| day | string  Jour concerné, au format “dd/MM/yyyy”   |
| dayTotalUsePerEquipement  { | object |
| < Nom de l’équipement > | integer ($int64)  Durée d’utilisation cumulée journalière de cet équipement (en seconde)   |
| } |  |
| usePerHalfHour   \[  { | object |
| libelleEquipement | string  Nom de l’équipement   |
| useDuration | integer ($int32)  Durée d’utilisation (demi-heure)   |
| start | string  Heure de début (au format HH:mm)   |
| end | string  Heure de fin (au format HH:mm)   |
| } \] |  |
| } \] |  |
| totalUserPerEquipementForPeriod   \[  { | object |
| < Nom de l’équipement > | integer ($int64)  Durée d’utilisation cumulée journalière de cet équipement (en seconde)   |
| } \] |  |
| vehicle  { | object |
| categorie | string  Catégorie du véhicule   |
| description | string (100)  Description du véhicule   |
| dioEnabled | boolean  Donnée sur une entrée/sortie dans le boitier oui/non (moteur auxiliaire, ...)   |
| dispositifIdentifiant | boolean  Etat du dispositif identifiant (oui/non)   |
| geosecuriteEnabled | boolean  Activation de géosecurité (oui/non)   |
| id | integer ($int32)  Identifiant du véhicule   |
| nomImage | string  Nom de l’image du véhicule   |
| odirectMode | string  Mode O-Direct Renault/Peugeot/Kuantic, …   |
| privacyEnabled | boolean  Mode « Vie Privée » activé   |
| suppressionLogique | boolean  Suppression en base de données (oui/non)   |
| } |  |

} \]