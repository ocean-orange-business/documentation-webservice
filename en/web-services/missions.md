---
title: missions
description: 
published: true
date: 2024-10-31T15:22:29.673Z
tags: 
editor: markdown
dateCreated: 2024-10-31T15:22:26.326Z
---

# Gestion des missions

Cette API permet de :

-   Créer une nouvelle mission,
-   Modifier une mission en cours,
-   Retrouver le statut d’une mission,
-   Supprimer une mission.

Cette fonctionnalité n’est disponible que pour les clients ayant souscrit aux web services en complément d’une solution GéoPack ou GéoPro.

### Paramètres de la requête

| Nom | Description |
| --- | --- |
| idMission | string  Identifiant client de la mission     |
| jourHeureInter | string ($dateTime)  Date d'intervention, elle doit être au format UTC : "dd/MM/yyyy HH:mm". Seul ce format est pris en compte par notre API.     |
| jourHeurePeremp | string ($dateTime)  Date de suppression automatique de la mission sur l’écran, elle doit être au format UTC : "dd/MM/yyyyHH:mm". Seul ce format est pris en compte par notre API.     |
| typeMission | string  Type de la mission     |
| nomVeh | string  Nom du véhicule     |
| nomIndi | string  Nom de l'individu (si aucun véhicule sélectionné, le destinataire cible est un individu avec nom prénom)     |
| prenomIndi | string  Prénom de l'individu (si aucun véhicule sélectionné, le destinataire cible est un individu avec nom prénom)     |
| nomPrenom | string  Nom et prénom de l'individu     |
| commentaire | string  Commentaire de la mission     |
| adrRefCli | string  Nom de l’adresse de référence client (tronquée à 20 caractères sur l’affichage site et écran)     |
| rue | string  Rue de destination     |
| codPost | string  Code postal de destination     |
| ville | string  Ville de destination     |
| aEnvoyer | boolean  TRUE si la mission est à envoyer   FALSE si la mission est seulement préparée     |
| longitude | number ($double)  Longitude de la destination     |
| latitude | number ($double)  Latitude de la destination     |

### Réponses

{

| message | string  Message de retour du WS (succès/échec)   |
| --- | --- |

}

### Paramètres de la requête

| Nom | Description |
| --- | --- |
| idMission | string  Identifiant client de la mission     |
| jourHeureInter | string ($dateTime)  Date d'intervention, elle doit être au format UTC : "dd/MM/yyyy HH:mm". Seul ce format est pris en compte par notre API.     |
| jourHeurePeremp | string ($dateTime)  Date de suppression automatique de la mission sur l’écran, elle doit être au format UTC : "dd/MM/yyyyHH:mm". Seul ce format est pris en compte par notre API.     |
| typeMission | string  Type de la mission     |
| nomVeh | string  Nom du véhicule     |
| nomIndi | string  Nom de l'individu (si aucun véhicule sélectionné, le destinataire cible est un individu avec nom prénom)     |
| prenomIndi | string  Prénom de l'individu (si aucun véhicule sélectionné, le destinataire cible est un individu avec nom prénom)     |
| nomPrenom | string  Nom et prénom de l'individu     |
| commentaire | string  Commentaire de la mission     |
| adrRefCli | string  Nom de l’adresse de référence client (tronquée à 20 caractères sur l’affichage site et écran)     |
| rue | string  Rue de destination     |
| codPost | string  Code postal de destination     |
| ville | string  Ville de destination     |
| aEnvoyer | boolean  TRUE si la mission est à envoyer   FALSE si la mission est seulement préparée     |
| longitude | number ($double)  Longitude de la destination     |
| latitude | number ($double)  Latitude de la destination     |

### Réponses

{

| message | string  Message de retour du WS (succès/échec)   |
| --- | --- |

}

### Paramètres de la requête

| Nom | Description |
| --- | --- |
| idMission obligatoire | string  Identifiant client de la mission     |

### Réponses

{

| commentRefuseReason | string  Raison de refus   |
| --- | --- |
| complement | string  Complément d’information   |
| externalMissionId | string  Identifiant technique de la mission   |
| status | string  Statut de la mission   |
| statusCode | string  Code statut de la mission   |
| timestring | string  Date de la mission   |

}

### Paramètres de la requête

| Nom | Description |
| --- | --- |
| idMission obligatoire | string  Identifiant client de la mission     |

### Réponses

{

| message | string  Message de retour du WS (succès/échec)   |
| --- | --- |

}