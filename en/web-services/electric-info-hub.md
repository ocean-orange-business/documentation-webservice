---
title: ElectricInfoHub
description: 
published: true
date: 2024-10-31T14:19:32.927Z
tags: 
editor: markdown
dateCreated: 2024-10-31T14:19:29.689Z
---

# Page de Remontée d'Informations Électriques

## Introduction
Cette page est dédiée à la remontée et à la gestion des informations électriques des véhicules.

## Objectifs
- Suivre l'état de charge des batteries
- Collecter des données sur la consommation d'énergie
- Analyser les performances électriques des véhicules

## Informations à Remonter
### État de Charge
- **On Charge** : Indique si le véhicule est en charge.
- **Full Charge Time** : Temps restant pour une recharge complète.

### Données Électriques
- **Tension de la batterie**
- **Courant de charge**
- **Capacité restante (kWh)**

### Types de Charge
- **UNKNOWN** (-1)
- **CHARGE_10A** (1)
- **CHARGE_16A** (2)
- **FAST_CHARGE** (3)

## Conditions de Remontée
- Remonter les informations lorsque le véhicule est en charge.
- Remonter les données lors de la réception d'`extended_data`.

## Exemple de Fréquence de Remontée pour les Véhicules Électriques
- **Valeur des informations remontées par Renault** : 
  - Fréquence de 5 minutes pour la première ligne.

### Tableau des Informations Remontées
| Information                | Fréquence (minutes) |
|----------------------------|----------------------|
| État de charge             | 5                    |
| Tension de la batterie     | 5                    |
| Courant de charge          | 5                    |
| Capacité restante (kWh)    | 5                    |
| Autres données             | 10                   |

## API et Intégrations
- **Endpoints API** :
  - `/positions/search` : Pour récupérer l'état de charge.
  - `/ecoAttitude/v1/get_datas` : Pour les données de consommation.

## Conclusion
Cette page sert de référence pour la remontée des informations électriques, facilitant ainsi le suivi et l'analyse des performances des véhicules électriques.
