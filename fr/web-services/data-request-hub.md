---
title: DataSourceGuide
description: 
published: true
date: 2024-10-31T14:19:28.349Z
tags: 
editor: markdown
dateCreated: 2024-10-31T14:19:25.227Z
---

# Informations Webservices

## Concernant la valeur *OnCharge* et *full ChargeTime* dans les *extended data* détectées sur des boîtiers natifs *Stellantis* et *Renault*.

### Types de Charge
- **UNKNOWN** (-1, `#959595`)
- **CHARGE_10A** (1, `#3958ab`)
- **CHARGE_16A** (2, `#0c964b`)
- **FAST_CHARGE** (3, `#cd2e08`)

### Conditions de Remontée des Informations
- **Si l'état est en charge :**
  - Remonter les informations de chargement :
    - Durée
    - Durée restante pour une recharge à 100%
  
- **Ou si on a une remontée `extended_data` :**
  - Remonter les informations de chargement :
    - Durée
    - Durée restante pour une recharge à 100%

## Information des data API REST

### Kpi's données API REST
| Source                        | Validé |
|-------------------------------|--------|
| LIGIER-ACTIA                  | Validé |
| STELLANTIS-première monte     | Validé |
| RENAULT-première monte        | Validé |

### Commentaires
- **Geolocalisation**
  - `/positions/search`
  
- **Odomètre**
  - `/positions/search`
  
- **Consommation instantanée du carburant (L ou kWh) à la fin du trajet**
  - `/positions/search`
  
- **État de charge de la batterie (SOC)**
  - `/positions/search`
  
### Extended_data
- **Vitesse de déplacement**
  - `/positions/search`
  
- **Vitesse KmH**
  
- **Accélération/Décélération brutale**
  - Non
  - `/ecoAttitude/v1/get_datas`
  
- **Déclenchement ABS**
  - Non
  - NC
  - NC
  - NC
  
- **Déclenchement ESP**
  - NC
  - NC
  - NC
  
- **Pression pneumatique**
  - NC
  - NC
  - NC
  
- **Alertes**
  - **ID Conducteur**
  - **Émission CO2 à la fin du trajet**
    - `/ecoAttitude/v1/get_datas`
  
- **Niveau du carburant à la fin du trajet pour VL thermique (ratio ou litre)**
  - `/positions/search`
  
- **Autonomie restante en kWh**
  - `/positions/search`
  
- **État de santé batterie (SOH)**
  - `/positions/search`
  
- **Batterie des VL électriques en charge ("on charge")**
  - `/positions/search`
  
- **Alerte ouverture des portes, type de porte (arrière, hayon…)**
  - NC
  - NC
  - NC
  
- **Appui pédale de frein**
  - NC
  - NC
  - NC
  
- **Alerte pression pneumatique (sous-gonflage et sur-gonflage)**
  - NC
  - NC
  - NC
  
- **État du moteur (allumé / éteint)**
  - `/positions/search` → ?
  
- **Positions du véhicule (État surtout à l'arrêt et arrêté)**
  - `/positions/search` → positions : `"etat": "start/traveling/stop"`
