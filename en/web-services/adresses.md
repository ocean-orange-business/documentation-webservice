---
title: adresses
description: 
published: true
date: 2024-10-31T15:22:05.508Z
tags: 
editor: markdown
dateCreated: 2024-10-31T15:22:01.422Z
---

# Gestion des adresses de référence

### Paramètres de la requête

| Nom | Description |
| --- | --- |
| poi | object  Objet JSON décrivant le point d’intérêt. Pour le format de l’objet se référer à sa description dans https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/createPoiUsingPOST     |

### Réponses

{

| adressePoi | string (150)  Adresse de référence   |
| --- | --- |
| codePostalPoi | string (20)  Code postal de l’adresse de référence   |
| complementAdresse1Poi | string (150)  Complément d’adresse I   |
| complementAdresse2Poi | string (150)  Complément d’adresse II   |
| denominationPoi | string (150)  Dénomination de l’adresse de référence   |
| etatRegionPoi | string (100)  Région de l’adresse de référence   |
| geom | string  Polygone contenant l’ensemble des points de l’adresse de référence   |
| groupePoi  { | object |
| id | integer ($int32)  Identifiant du groupe de l’adresse de référence   |
| libelle | string  Libellé de l’adresse de référence   |
| } |  |
| id | integer ($int32)  Identifiant technique de l’adresse de référence   |
| idPays | number ($float)  Identifiant technique du pays   |
| latPoi | number ($float)  Latitude de l’adresse de référence   |
| libelleTypePoi  { | object |
| color | string  Couleur de l’adresse de référence   |
| i18nKey | string  La clé d’internalisation (français / english / español)   |
| id | integer ($int32)  Identifiant technique du libellé du type de l’adresse de référence   |
| libelle | string (100)  Libellé de l’adresse de référence   |
| ordre | integer ($int32)  Ordre d’affichage de l’adresse de référence   |
| type | string - Enum  Type de l’adresse de référence   Enum : UNDEFINED, OFFICE, HOME, PROVIDER, CLIENT, PROSPECT, GAS\_STATION, RESTAURANT, OTHER   |
| } |  |
| longPoi | number ($float)  Longitude de l’adresse de référence   |
| rayonPoi | integer ($int32)  Rayon en mètre de l’adresse de référence   |
| suppressionLogique | boolean  L’adresse est complètement supprimée   |
| villePoi | string (100)  Ville   |

}

### Paramètres de la requête

| Nom | Description |
| --- | --- |
| poi obligatoire | object  Objet JSON décrivant le point d’intérêt. Pour le format de l’objet se référer à sa description dans https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/poi/createPoiUsingPOST     |
| externalId | string  Identifiant Externe (s’il provient d’un autre Système d’information)     |
| source | string  Source de l’identifiant externe (champs libre, ex. nom d’un logiciel pour le stockage des adresses de référence)     |

### Réponses

{

| adressePoi | string (150)  Adresse de référence   |
| --- | --- |
| codePostalPoi | string (20)  Code postal de l’adresse de référence   |
| complementAdresse1Poi | string (150)  Complément d’adresse I   |
| complementAdresse2Poi | string (150)  Complément d’adresse II   |
| denominationPoi | string (150)  Dénomination de l’adresse de référence   |
| etatRegionPoi | string (100)  Région de l’adresse de référence   |
| geom | string  Polygone contenant l’ensemble des points de l’adresse de référence   |
| groupePoi  { | object |
| id | integer ($int32)  Identifiant du groupe de l’adresse de référence   |
| libelle | string  Libellé de l’adresse de référence   |
| } |  |
| id | integer ($int32)  Identifiant technique de l’adresse de référence   |
| idPays | integer ($int32)  Identifiant technique du pays   |
| latPoi | number ($float)  Latitude de l’adresse de référence   |
| libelleTypePoi  { | object |
| color | string  Couleur de l’adresse de référence   |
| i18nKey | string  La clé d’internalisation (français / english / español)   |
| id | integer ($int32)  Identifiant technique du libellé du type de l’adresse de référence   |
| libelle | string (100)  Libellé de l’adresse de référence   |
| ordre | integer ($int32)  Ordre d’affichage de l’adresse de référence   |
| type | string - Enum  Type de l’adresse de référence   Enum : UNDEFINED, OFFICE, HOME, PROVIDER, CLIENT, PROSPECT, GAS\_STATION, RESTAURANT, OTHER   |
| } |  |
| longPoi | number ($float)  Longitude de l’adresse de référence   |
| rayonPoi | integer ($int32)  Rayon en mètre de l’adresse de référence   |
| suppressionLogique | boolean  Suppression en base de données oui/non   |
| villePoi | string (100)  Ville   |

}

### Paramètres de la requête

| Nom | Description |
| --- | --- |
| searchCenterLongitudeX | number ($double)  Longitude     |
| searchCenterLatitudeY | number ($double)  Latitude     |
| searchRadius | integer ($int32)  Rayon (en mètre)     |
| externalId | string  Identifiant Externe (s’il provient d’un autre Système d’information)     |
| source | string  Source de l’identifiant externe (ex. POI Fleet)     |

### Réponses

\[ {

| adressePoi | string (150)  Adresse de référence   |
| --- | --- |
| codePostalPoi | string (20)  Code postal de l’adresse de référence   |
| complementAdresse1Poi | string (150)  Complément d’adresse I   |
| complementAdresse2Poi | string (150)  Complément d’adresse II   |
| denominationPoi | string (150)  Dénomination de l’adresse de référence   |
| etatRegionPoi | string (100)  Région de l’adresse de référence   |
| geom | string  Polygone contenant l’ensemble des points de l’adresse de référence   |
| groupePoi  { | object |
| id | integer ($int32)  Identifiant du groupe de l’adresse de référence   |
| libelle | string  Libellé de l’adresse de référence   |
| } |  |
| id | integer ($int32)  Identifiant technique de l’adresse de référence   |
| idPays | number ($float)  Identifiant technique du pays   |
| latPoi | number ($float)  Latitude de l’adresse de référence   |
| libelleTypePoi  { | object |
| color | string  Couleur de l’adresse de référence   |
| i18nKey | string  La clé d’internalisation (français / english / español)   |
| id | integer ($int32)  Identifiant technique du libellé du type de l’adresse de référence   |
| libelle | string (100)  Libellé de l’adresse de référence   |
| ordre | integer ($int32)  Ordre d’affichage de l’adresse de référence   |
| type | string - Enum  Type de l’adresse de référence   Enum : UNDEFINED, OFFICE, HOME, PROVIDER, CLIENT, PROSPECT, GAS\_STATION, RESTAURANT, OTHER   |
| } |  |
| longPoi | number ($float)  Longitude de l’adresse de référence   |
| rayonPoi | integer ($int32)  Rayon en mètre de l’adresse de référence   |
| suppressionLogique | boolean  L’adresse est complètement supprimée   |
| villePoi | string (100)  Ville   |

} \]

### Paramètres de la requête

| Nom | Description |
| --- | --- |
| idPoi obligatoire | integer ($int64)  Identifiant technique de l’adresse de référence à supprimer     |

### Réponses