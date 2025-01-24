---
title: boitiers-non-communicants
description: 
published: true
date: 2024-10-31T15:22:10.566Z
tags: 
editor: markdown
dateCreated: 2024-10-31T15:22:07.127Z
---

# Boitiers non communicants

\[ {

| qualificationNCVehiculeDTO  { | object |
| --- | --- |
| qualificationNCDTO  { | object |
| dateNcEnabled | boolean  « True » / « False » si le boitier est non communicant   |
| id | integer  Identification de la qualification « non communicant »   |
| libelle | string (250)  Libellé de la qualification « non communicant »   |
| mailGroupNC | string - Enum  Type d’envoi de mail   Enum : NO\_MAIL, MAIL\_TO\_NC, MAIL\_TO\_NC2    |
| } |  |
| qualificationNCVehiculeEnginLightDTO  { | object |
| commentaire | string  Commentaire sur la qualification « non communicant »   |
| dateFin | string  Date de fin de la qualification « non communicant »   |
| dateQualification | string  Date de qualification « non communicant »   |
| id | integer  Identification de la qualification « non communicant » du véhicule   |
| } |  |
| utilisateurLightDTO  { | object |
| emailUti | string  Email de l’utilisateur   |
| id | string  Identifiant de l’utilisateur   |
| individu  { | object |
| email | string (50)  Email de l’individu   |
| gsm | string (20)  Numéro de téléphone portable de l’individu   |
| id | integer  Identifiant de l’individu   |
| nomInd | string (100)  Nom de l’individu   |
| prenomInd | string (100)  Prénom de l’individu   |
| suppressionLogique | boolean  Suppression en base de données (oui/non)   |
| } |  |
| loginUti | string (100)  Login de l’utilisateur   |
| nomUti | string (100)  Nom de l’utilisateur   |
| prenomUti | string  Prénom de l’utilisateur   |
| suppressionLogique | boolean  Suppression en base de données (oui/non)   |
| utilisateurOceanUti | boolean  Utilisateur Ocean   |
| utilisateurType | string - Enum  Type d’utilisateur   Enum : CLASSIC, SUPERUSER, PRESTA, INDIVIDUEL, EBTP, DISTRI, SUPER\_ADMIN, ADMIN\_MULTI\_CLI, DT\_DEV, DT\_SUPPORT, ADV, ADV\_MANAGER, SC\_CDC, SC\_INS, SC\_INS\_MANAGER, SC\_PLAN, SC\_LOG   |
| } |  |
| vehicle  { | object |
| categorie | string  Catégorie du véhicule   |
| couleur | string (50)  Couleur du véhicule   |
| description | string (100)  Description du véhicule   |
| dioEnabled | boolean  Donnée sur une entrée/sortie dans le boitier oui/non (moteur auxiliaire, ...)   |
| dispositifIdentifiant | boolean  Etat du dispositif identifiant (oui/non)   |
| geosecuriteEnabled | boolean  Activation de géosecurité (oui/non)   |
| id | integer ($int32)  Identifiant du véhicule   |
| immatriculation | string (50)  Immatriculation du véhicule   |
| marque | string (50)  Marque du véhicule   |
| modele | string (50)  Modèle du véhicule   |
| nomImage | string  Nom de l’image du véhicule   |
| numeroEmbarque | integer ($int32)  Numéro embarqué du véhicule   |
| numeroSerie | string  Numéro de série du véhicule   |
| odirectMode | string  Mode O-Direct Renault/Peugeot/Kuantic, …   |
| privacyEnabled | boolean  Mode « Vie Privée » activé   |
| suppressionLogique | boolean  Suppression en base de données (oui/non)   |
| } |  |
| } |  |

} \]