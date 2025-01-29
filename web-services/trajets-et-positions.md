---
title: trajets-et-positions
description: 
published: true
date: 2025-01-29T10:09:29.998Z
tags: 
editor: markdown
dateCreated: 2025-01-29T09:57:03.497Z
---

# Trajets et positions

\[ {

| materiel  { | object |
| --- | --- |
| boxLightDTO  { | object |
| id | integer ($int64)  Identifiant du boitier   |
| numeroSerieBoi | string (50)  Numéro de série du boitier   |
| } |  |
| entiteLightDTO  { | object |
| id | integer ($int64)  Identifiant de l’entité   |
| nom | string (150)  Nom de l’entité   |
| suppressionLogique | boolean  Suppression en base de données (oui/non)   |
| } |  |
| materiel  { | object |
| description | string (100)  Description du matériel   |
| id | integer  Identifiant du matériel   |
| marque | string (50)  Marque du matériel   |
| modele | string  Modèle du matériel   |
| reference | string (50)  Référence du matériel   |
| } |  |
| proprietesSpecifiquesDTO  { | object |
| id | integer ($int64)  Identifiant de la propriété   |
| idObjetRef | integer ($int64)  Identifiant de l’objet de référence   |
| typeObjet | string  Type d’objet de référence (Véhicules, matériel)   |
| } |  |
| trameDTO  { | object |
| id | integer ($int64)  Identifiant de la trame   |
| reason | string  Code interne type d’ événement   |
| scenarioDTO  { | object |
| code | string  Code du scénario   |
| i18nKey | string  Libellé du scénario   |
| id | integer ($int64)  Identifiant du scénario du boitier   |
| } |  |
| stateBoitier | boolean  Adresse de la position   |
| } |  |
| } |  |
| positions   \[  { | object |
| address | string (150)  Adresse de la position   |
| cap | integer ($int64)  Cap position GPS   |
| closestPoi  { | object |
| adressePoi | string (150)  Adresse de l’adresse de référence la plus proche   |
| codePostalPoi | string (20)  Code postal de l’adresse de référence la plus proche   |
| complementAdresse1Poi | string (150)  Complément d’adresse 1 de l’adresse de référence la plus proche   |
| complementAdresse2Poi | string (150)  Complément d’adresse 2 de l’adresse de référence la plus proche   |
| denominationPoi | string (50) |
| groupePoi  { | object |
| id | integer ($int32)  Identifiant du groupe de l’adresse de référence   |
| libelle | string  Libellé de l’adresse de référence   |
| } |  |
| id | integer ($int64)  Identifiant de l’adresse de référence   |
| idPays | integer ($int64)  Identifiant du pays   |
| latPoi | number ($double)  Latitude de l’adresse de référence   |
| libelleTypePoi  { | object |
| color | string  Couleur de l’adresse de référence   |
| i18nKey | string  La clé d’internalisation (français / english / español)   |
| id | integer ($int32)  Identifiant technique du libellé du type de l’adresse de référence   |
| libelle | string (100)  Libellé de l’adresse de référence   |
| ordre | integer ($int32)  Ordre d’affichage de l’adresse de référence   |
| type | string - Enum  Type de l’adresse de référence   Enum : UNDEFINED, OFFICE, HOME, PROVIDER, CLIENT, PROSPECT, GAS\_STATION, RESTAURANT, OTHER   |
| } |  |
| longPoi | number ($double)  Longueur de l’adresse de référence   |
| rayonPoi | integer ($int64)  Rayon de l’adresse de référence   |
| suppressionLogique | boolean  Suppression en base de données (oui/non)   |
| villePoi | string (100)  Ville de l’adresse de référence   |
| } |  |
| codeExploitant | string  Code Exploitant   |
| countryCode | integer ($int64)  Code de Pays   |
| gmtPosFormat | string  Date GMT de la position   |
| gpsCalle | boolean  GPS calé 0/1 (true / false)   |
| idEtatMobile | integer ($int64)  Identifiant de l’état Mobile   |
| idPositionGeo | integer ($int64)  Identifiant de la position Géosécurité   |
| latitude | number  Position latitude   |
| latitudeYPos | number  Position latitude Y   |
| longitude | number  Position longitude   |
| longitudeXPos | number  Position longitude X   |
| numeroEmbarquePos | integer ($int64)  Numéro embarqué   |
| postCode | string (20)   Code postal   |
| precision | number  Précision de la position GPS   |
| town | string (100)   Ville   |
| } \] |  |

} \]