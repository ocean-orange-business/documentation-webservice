---
title: Boitiers non communicants
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-24T13:16:04.247Z
---

# Boitiers non communicants


Cette API permet de récupérer :

- La liste des boitiers non communicants.

## Récupérer la liste des boitiers non communicants et leur qualification

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/non-communicant-controller)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

Par « qualification », on entend la raison renseignée par l’utilisateur sur la plateforme pour chaque boitier non communicant. Cette fonctionnalité n’est disponible que pour les clients ayant souscrit aux web services en complément d’une solution GéoPack, GéoPro, ParkConnect ou smart tracking.
### Définition {.tabset}

#### Endpoint
```
get /restapi/noncommunicant/list
```

#### Paramètres de la requête

| Nom          | Type             | Description                                                                     |
| ------------ | ---------------- | ------------------------------------------------------------------------------- |
| customerId * | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |

\* paramètre mandataire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```json
[
  {
    "boxInstallationInfo": {
      "hasCommunicatedAtLeastOnce": true,
      "hasNeverCommunicated": true,
      "installationDate": "2024-11-07T09:41:12.635Z",
      "lastCommunicatingDate": "2024-11-07T09:41:12.635Z"
    },
    "detailedBoxDTO": {
      "affectationVehiculeBoitierConfigSet": {
        "boitierConfigSetLightDTO": {
          "dateMaj": "2024-11-07T09:41:12.635Z",
          "id": 0,
          "libelleConfig": "string",
          "ordre": 0
        },
        "dateAck": "2024-11-07T09:41:12.635Z",
        "debut": "2024-11-07T09:41:12.635Z",
        "fin": "2024-11-07T09:41:12.635Z",
        "statutAffectation": "ON_STANDBY"
      },
      "box": {
        "adBoi": "string",
        "commentaireBoi": "string",
        "coreGsmBoi": "string",
        "debutGarantie": "2024-11-07T09:41:12.635Z",
        "finGarantie": "2024-11-07T09:41:12.635Z",
        "id": 0,
        "idEtatBoitier": 0,
        "imeiBoi": "string",
        "numeroSerieBoi": "string",
        "sn": "string"
      },
      "client": {
        "codeExploitant": "string",
        "dateContentieux": "2024-11-07T09:41:12.635Z",
        "fuseauHoraire": "string",
        "id": 0,
        "nom": "string",
        "suppressionLogique": true
      },
      "commande": {
        "commentaire": "string",
        "id": 0,
        "numero": "string",
        "quantite": 0
      },
      "currentEmplacementPhysique": {
        "codeEmp": "string",
        "descriptionEmp": "string",
        "id": 0
      },
      "currentVehicule": {
        "apcMode": "GPS",
        "boitierAvantCoupeCircuit": true,
        "buzzerSurvitesseEnabled": true,
        "categorie": "UNDEFINED",
        "categorieVehiculeEcoConduite": "UL",
        "couleur": "string",
        "coupeBatterie": true,
        "date1ereMec": "2024-11-07T09:41:12.635Z",
        "description": "string",
        "detectionPorteEnabled": true,
        "dioEnabled": true,
        "dispositifIdentifiant": true,
        "emissionCo2": 0,
        "etatEcoConduite": "ACTIF",
        "geolocalise": true,
        "geomissionEnabled": true,
        "geosecuriteEnabled": true,
        "id": 0,
        "idEnergie": 0,
        "idModeDeplacement": 0,
        "idUniteConsommation": 0,
        "immatriculation": "string",
        "immobilisationCablee": true,
        "libelleTypeAsset": {
          "categorie": "UNDEFINED",
          "id": 0,
          "libelle": "string",
          "nomIcone": "string",
          "ordre": 0
        },
        "marque": "string",
        "modele": "string",
        "nomImage": "string",
        "nombreCvFiscaux": 0,
        "numeroEmbarque": 0,
        "numeroParc": "string",
        "numeroSerie": "string",
        "odirectMode": "ODIRECT_UNIVERSEL",
        "privacyEnabled": true,
        "prk": 0,
        "signesDistinctifs": "string",
        "suppressionLogique": true,
        "typeMotorisation": "MONO",
        "valeurConsommation": 0,
        "vin": "string"
      },
      "distributeur": {
        "adresse": "string",
        "dateCreation": "2024-11-07T09:41:12.635Z",
        "designation": "string",
        "email": "string",
        "emailOperationnel": "string",
        "id": 0,
        "mapProvider": "GOOGLE_MAP",
        "telephone": "string"
      },
      "fournisseur": {
        "code": "string",
        "description": "string",
        "id": 0
      },
      "id": 0,
      "operateurSim": "string",
      "phoneSim": "string",
      "releaseHard": {
        "code": "string",
        "id": 0
      },
      "sim": {
        "dateImport": "2024-11-07T09:41:12.635Z",
        "iccid": "string",
        "idSim": 0,
        "nomFichierImport": "string",
        "simHs": true
      },
      "typeBoitier": {
        "code": "string",
        "description": "string",
        "id": 0
      },
      "typeStock": "UNDEFINED",
      "versionSoft": {
        "id": 0,
        "version": "string"
      }
    },
    "ongletPositionVehicleDTO": {
      "address": {
        "address": "string",
        "cap": 0,
        "closestPoi": {
          "adressePoi": "string",
          "codePostalPoi": "string",
          "complementAdresse1Poi": "string",
          "complementAdresse2Poi": "string",
          "denominationPoi": "string",
          "etatRegionPoi": "string",
          "geom": "string",
          "groupePoi": {
            "id": 0,
            "libelle": "string"
          },
          "id": 0,
          "idPays": 0,
          "latPoi": 0,
          "libelleTypePoi": {
            "color": "string",
            "i18nKey": "string",
            "id": 0,
            "libelle": "string",
            "nomImage": "string",
            "ordre": 0,
            "type": "UNDEFINED"
          },
          "longPoi": 0,
          "propSpecifiqueDTO": {
            "id": 0,
            "idClient": 0,
            "idObjetRef": 0,
            "proprietesSpecifiquesClient": {
              "psValues": {
                "additionalProp1": [
                  "string"
                ],
                "additionalProp2": [
                  "string"
                ],
                "additionalProp3": [
                  "string"
                ]
              }
            },
            "typeObjet": "CLIENT"
          },
          "rayonPoi": 0,
          "suppressionLogique": true,
          "villePoi": "string"
        },
        "countryCode": 0,
        "gpsCalle": true,
        "latitude": 0,
        "longitude": 0,
        "postCode": "string",
        "precision": 0,
        "town": "string"
      },
      "cataloguesDio": [
        {
          "code": "string",
          "id": 0,
          "inverse": true,
          "libelle": "string"
        }
      ],
      "chronotachygrapheCounter": {
        "cumulKilometrique": 0,
        "debut": "2024-11-07T09:41:12.635Z",
        "durationMap": {
          "additionalProp1": 0,
          "additionalProp2": 0,
          "additionalProp3": 0
        },
        "fin": "2024-11-07T09:41:12.635Z"
      },
      "compteur": 0,
      "currentChrono": {
        "activiteConducteur1": "REPOS",
        "activiteConducteur2": "REPOS",
        "carteConducteur1": "string",
        "carteConducteur2": "string",
        "debut": "2024-11-07T09:41:12.635Z",
        "fin": "2024-11-07T09:41:12.635Z",
        "indexKilometrique": 0,
        "individu": {
          "email": "string",
          "gsm": "string",
          "id": 0,
          "idCivilite": 0,
          "initialesInd": "string",
          "matriculeInd": "string",
          "nomInd": "string",
          "prenomInd": "string",
          "suppressionLogique": true
        },
        "numeroSerieBoitier": "string",
        "positionCurr": {
          "latitude": 0,
          "longitude": 0
        },
        "positionPrev": {
          "latitude": 0,
          "longitude": 0
        },
        "vehicule": {
          "categorie": "UNDEFINED",
          "couleur": "string",
          "description": "string",
          "detectionPorteEnabled": true,
          "dioEnabled": true,
          "dispositifIdentifiant": true,
          "geolocalise": true,
          "geosecuriteEnabled": true,
          "id": 0,
          "immatriculation": "string",
          "immobilisationCablee": true,
          "libelleTypeAsset": {
            "categorie": "UNDEFINED",
            "id": 0,
            "libelle": "string",
            "nomIcone": "string",
            "ordre": 0
          },
          "marque": "string",
          "modele": "string",
          "nomImage": "string",
          "numeroEmbarque": 0,
          "numeroParc": "string",
          "numeroSerie": "string",
          "odirectMode": "ODIRECT_UNIVERSEL",
          "privacyEnabled": true,
          "suppressionLogique": true,
          "typeMotorisation": "MONO"
        }
      },
      "distance": 0,
      "energyLevel": {
        "autonomie": 0,
        "capaciteReserve": 0,
        "chargeElectrique": {
          "capaciteBatterie": {
            "unit": "HOUR",
            "value": 0
          },
          "charge100Pct": true,
          "fastCharge": true,
          "periodeBranchement": {
            "daysDuration": 0,
            "debut": "2024-11-07T09:41:12.635Z",
            "fin": "2024-11-07T09:41:12.635Z",
            "timeDuration": 0
          },
          "periodeCharge": {
            "daysDuration": 0,
            "debut": "2024-11-07T09:41:12.635Z",
            "fin": "2024-11-07T09:41:12.635Z",
            "timeDuration": 0
          },
          "pourcentageBatterieDebut": 0,
          "pourcentageBatterieFin": 0,
          "tempsCharge100Pct": 0,
          "typeCharge": "UNKNOWN"
        },
        "energy": "UNDEFINED",
        "energyLevelDate": "2024-11-07T09:41:12.635Z",
        "gaugeLevel": 0,
        "lastEnergyLevelPeriod": {
          "daysDuration": 0,
          "debut": "2024-11-07T09:41:12.636Z",
          "fin": "2024-11-07T09:41:12.636Z",
          "timeDuration": 0
        },
        "unit": "HOUR"
      },
      "entiteChauffeur": {
        "id": 0,
        "nom": "string",
        "suppressionLogique": true
      },
      "entiteVehicle": {
        "id": 0,
        "nom": "string",
        "suppressionLogique": true
      },
      "etatMobile": "UNDEFINED",
      "gpsCale": true,
      "group": {
        "descriptionGrp": "string",
        "id": 0,
        "suppressionLogique": true
      },
      "heure": "2024-11-07T09:41:12.636Z",
      "id": 0,
      "idRattachementHoraire": 0,
      "immobilisationState": "LOCKED",
      "individu": {
        "affectedEtape": {
          "codeExploitant": "string",
          "creation": "2024-11-07T09:41:12.636Z",
          "debut": "2024-11-07T09:41:12.636Z",
          "idEtape": 0,
          "modeAffectationEtape": "AUTO",
          "ndid": "string",
          "numeroEmbarque": 0,
          "typeAffectationEtape": "CHAUFFEUR"
        },
        "dispositif": {
          "color": 0,
          "id": 0,
          "idClient": 0,
          "idTypeDispositifIdentifiant": 0,
          "numeroCleClient": 0,
          "numeroCompletDid": "string",
          "numeroDid": "string"
        },
        "id": 0,
        "identEnabled": true,
        "individu": {
          "email": "string",
          "gsm": "string",
          "id": 0,
          "idCivilite": 0,
          "initialesInd": "string",
          "matriculeInd": "string",
          "nomInd": "string",
          "prenomInd": "string",
          "suppressionLogique": true
        },
        "ndidLong": "string",
        "relevant": true
      },
      "lastEventWithinTheLast24h": {
        "date": "2024-11-07T09:41:12.636Z",
        "evenementLibelle": "string",
        "heure": "2024-11-07T09:41:12.636Z",
        "id": "string"
      },
      "lastTechnicalEventWithinTheLast24h": {
        "date": "2024-11-07T09:41:12.636Z",
        "evenementLibelle": "string",
        "heure": "2024-11-07T09:41:12.636Z",
        "id": "string"
      },
      "lastUnifiedEvent": {
        "address": {
          "address": "string",
          "cap": 0,
          "closestPoi": {
            "adressePoi": "string",
            "codePostalPoi": "string",
            "complementAdresse1Poi": "string",
            "complementAdresse2Poi": "string",
            "denominationPoi": "string",
            "etatRegionPoi": "string",
            "geom": "string",
            "groupePoi": {
              "id": 0,
              "libelle": "string"
            },
            "id": 0,
            "idPays": 0,
            "latPoi": 0,
            "libelleTypePoi": {
              "color": "string",
              "i18nKey": "string",
              "id": 0,
              "libelle": "string",
              "nomImage": "string",
              "ordre": 0,
              "type": "UNDEFINED"
            },
            "longPoi": 0,
            "propSpecifiqueDTO": {
              "id": 0,
              "idClient": 0,
              "idObjetRef": 0,
              "proprietesSpecifiquesClient": {
                "psValues": {
                  "additionalProp1": [
                    "string"
                  ],
                  "additionalProp2": [
                    "string"
                  ],
                  "additionalProp3": [
                    "string"
                  ]
                }
              },
              "typeObjet": "CLIENT"
            },
            "rayonPoi": 0,
            "suppressionLogique": true,
            "villePoi": "string"
          },
          "countryCode": 0,
          "gpsCalle": true,
          "latitude": 0,
          "longitude": 0,
          "postCode": "string",
          "precision": 0,
          "town": "string"
        },
        "advancedTechnicalEvent": true,
        "date": "2024-11-07T09:41:12.636Z",
        "dateDebut": "2024-11-07T09:41:12.636Z",
        "dateFin": "2024-11-07T09:41:12.636Z",
        "detailEvenementLightDTO": {
          "code": "string",
          "defaut": "string",
          "modele": "string",
          "statut": "string",
          "technicalLabel": "string",
          "type": "string"
        },
        "entite": {
          "id": 0,
          "nom": "string",
          "suppressionLogique": true
        },
        "evenementLibelle": "string",
        "eventState": "PUNCTUAL",
        "extendedDataMap": {
          "additionalProp1": {},
          "additionalProp2": {},
          "additionalProp3": {}
        },
        "groupingPeriod": "TODAY",
        "heure": "2024-11-07T09:41:12.636Z",
        "id": "string",
        "reliable": true,
        "typeEvenement": "UNDEFINED",
        "typeEvenementODirectDTO": {
          "classificationEvenementDTO": {
            "code": "string",
            "descriptioni18nKey": "string",
            "id": 0
          },
          "detailsEvenementLightDTO": [
            {
              "code": "string",
              "defaut": "string",
              "modele": "string",
              "statut": "string",
              "technicalLabel": "string",
              "type": "string"
            }
          ],
          "id": 0,
          "typeEvenementOdirectDTO": {
            "code": "string",
            "descriptionI18NKey": "string",
            "numeroEve": 0,
            "temporalType": "PUNCTUAL"
          }
        },
        "vehicleEngin": {
          "categorie": "UNDEFINED",
          "description": "string",
          "detectionPorteEnabled": true,
          "dioEnabled": true,
          "dispositifIdentifiant": true,
          "geolocalise": true,
          "geosecuriteEnabled": true,
          "id": 0,
          "immobilisationCablee": true,
          "libelleTypeAsset": {
            "categorie": "UNDEFINED",
            "id": 0,
            "libelle": "string",
            "nomIcone": "string",
            "ordre": 0
          },
          "nomImage": "string",
          "odirectMode": "ODIRECT_UNIVERSEL",
          "privacyEnabled": true,
          "suppressionLogique": true,
          "typeMotorisation": "MONO"
        }
      },
      "nbDaysInNC": 0,
      "onCharge": true,
      "tempsParcours": 0,
      "vehicle": {
        "categorie": "UNDEFINED",
        "couleur": "string",
        "description": "string",
        "detectionPorteEnabled": true,
        "dioEnabled": true,
        "dispositifIdentifiant": true,
        "geolocalise": true,
        "geosecuriteEnabled": true,
        "id": 0,
        "immatriculation": "string",
        "immobilisationCablee": true,
        "libelleTypeAsset": {
          "categorie": "UNDEFINED",
          "id": 0,
          "libelle": "string",
          "nomIcone": "string",
          "ordre": 0
        },
        "marque": "string",
        "modele": "string",
        "nomImage": "string",
        "numeroEmbarque": 0,
        "numeroParc": "string",
        "numeroSerie": "string",
        "odirectMode": "ODIRECT_UNIVERSEL",
        "privacyEnabled": true,
        "suppressionLogique": true,
        "typeMotorisation": "MONO"
      },
      "vin": "string",
      "vitesseInstantanee": 0
    },
    "qualificationNCVehiculeDTO": {
      "qualificationNCDTO": {
        "dateNcEnabled": true,
        "id": 0,
        "libelle": "string",
        "mailGroupNC": "NO_MAIL"
      },
      "qualificationNCVehiculeEnginLightDTO": {
        "commentaire": "string",
        "dateFin": "2024-11-07T09:41:12.636Z",
        "dateQualification": "2024-11-07T09:41:12.636Z",
        "id": 0
      },
      "utilisateurLightDTO": {
        "dateFinValidite": "2024-11-07T09:41:12.636Z",
        "emailUti": "string",
        "id": 0,
        "individu": {
          "email": "string",
          "gsm": "string",
          "id": 0,
          "idCivilite": 0,
          "initialesInd": "string",
          "matriculeInd": "string",
          "nomInd": "string",
          "prenomInd": "string",
          "suppressionLogique": true
        },
        "loginUti": "string",
        "nomUti": "string",
        "prenomUti": "string",
        "suppressionLogique": true,
        "utilisateurType": "CLASSIC"
      },
      "vehicle": {
        "categorie": "UNDEFINED",
        "description": "string",
        "detectionPorteEnabled": true,
        "dioEnabled": true,
        "dispositifIdentifiant": true,
        "geolocalise": true,
        "geosecuriteEnabled": true,
        "id": 0,
        "immobilisationCablee": true,
        "libelleTypeAsset": {
          "categorie": "UNDEFINED",
          "id": 0,
          "libelle": "string",
          "nomIcone": "string",
          "ordre": 0
        },
        "nomImage": "string",
        "odirectMode": "ODIRECT_UNIVERSEL",
        "privacyEnabled": true,
        "suppressionLogique": true,
        "typeMotorisation": "MONO"
      }
    }
  }
]
```
