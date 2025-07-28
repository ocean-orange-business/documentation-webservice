---
title: Éco-conduite
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-24T13:16:09.120Z
---

# Gestion de l'Éco-conduite

Cette API permet de récupérer :

- Les données liées à l’éco-conduite des chauffeurs pour une période donnée.
- Les notes de « Sécurité » et « Consommation » par mois ou par semaine.
- Les notes affichées sur l'écran "Synthèse de flotte" de la webApp

## Récupérer les notes de sécurité et consommation par mois ou semaine

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getEchoattitudeGraphUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/ecoAttitude/v1/get_ecoattitude_graph
```

#### Paramètres de la requête

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId *   | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| individuId     | integer ($int64) | Identifiant du conducteur. |
| EC_MONTH_START | integer ($int32) | Mois de début              |
| EC_MONTH_END   | integer ($int32) | Mois de fin                |
| EC_YEAR_START  | integer ($int32) | Année de début             |
| EC_YEAR_END    | integer ($int32) | Année de fin               |
| EC_MODE        | string           | Au choix : semaine ou mois |

\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```JSON
{
  "conso": [
    0
  ],
  "date": [
    "string"
  ],
  "noteSimplifie": [
    0
  ],
  "secu": [
    0
  ]
}
```

## Récupérer les données liées à l’éco-conduite des chauffeurs pour une période donnée

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getDatasUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
get /restapi/ecoAttitude/v1/get_datas
```

#### Paramètres de la requête

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId *   | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| EC_MONTH_START | integer ($int32) | Mois de début              |
| EC_MONTH_END   | integer ($int32) | Mois de fin                |
| EC_YEAR_START  | integer ($int32) | Année de début             |
| EC_YEAR_END    | integer ($int32) | Année de fin               |
| EC_MODE        | string           | Au choix : semaine ou mois |

\* paramètre obligatoire 

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```

#### Résultat

```JSON
{
  "BILAN_CONSO_J": 0,
  "BILAN_CONSO_P": 0,
  "BILAN_DISTANCE_J": 0,
  "BILAN_DISTANCE_P": 0,
  "BILAN_EMISSION_CO2_J": 0,
  "BILAN_EMISSION_CO2_P": 0,
  "BILAN_TEMPS_CONDUITE_J": 0,
  "BILAN_TEMPS_CONDUITE_P": "string",
  "CFF_NOM": "string",
  "CFF_PRENOM": "string",
  "CONDUITE_MOY_PERIODE_ACCEL": 0,
  "CONDUITE_MOY_PERIODE_FREIN": 0,
  "CONDUITE_MOY_PERIODE_VIRAGES": 0,
  "CONDUITE_MOY_PERIODE_VITESSE": 0,
  "CONDUITE_USAGE_M_ARRET": "string",
  "CONDUITE_USAGE_M_DUREE_CHARGES": 0,
  "CONDUITE_USAGE_M_DUREE_REGIMES": 0,
  "CONDUITE_USAGE_M_ZONES_ROUGES": 0,
  "CONDUITE_Z_EXTRA_ACCEL": 0,
  "CONDUITE_Z_EXTRA_FREIN": 0,
  "CONDUITE_Z_EXTRA_VIRAGES": 0,
  "CONDUITE_Z_EXTRA_VITESSE": 0,
  "CONDUITE_Z_MIXTE_ACCEL": 0,
  "CONDUITE_Z_MIXTE_FREIN": 0,
  "CONDUITE_Z_MIXTE_VIRAGES": 0,
  "CONDUITE_Z_MIXTE_VITESSE": 0,
  "CONDUITE_Z_URBAINE_ACCEL": 0,
  "CONDUITE_Z_URBAINE_FREIN": 0,
  "CONDUITE_Z_URBAINE_VIRAGES": 0,
  "CONDUITE_Z_URBAINE_VITESSE": 0,
  "ECOATTITUDE_CONSO": 0,
  "ECOATTITUDE_SECU": 0,
  "MOY_ACC_PARC": 0,
  "MOY_FREIN_PARC": 0,
  "MOY_TYPO_ACC_PARC": {
    "additionalProp1": 0,
    "additionalProp2": 0,
    "additionalProp3": 0
  },
  "MOY_TYPO_FREIN_PARC": {
    "additionalProp1": 0,
    "additionalProp2": 0,
    "additionalProp3": 0
  },
  "MOY_TYPO_VIRAGES_PARC": {
    "additionalProp1": 0,
    "additionalProp2": 0,
    "additionalProp3": 0
  },
  "MOY_VIRAGES_PARC": 0,
  "RATIO_CMH_PARC": 0,
  "RATIO_RMH_PARC": 0,
  "TRAJETS_DISTANCE_MOYENNE": 0,
  "TRAJETS_NB": 0,
  "TRAJETS_TEMPS_MOYEN": "string",
  "VERSION_ECO": "string",
  "bilanJournalier": {
    "additionalProp1": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    },
    "additionalProp2": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    },
    "additionalProp3": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    }
  },
  "bilanPeriode": {
    "additionalProp1": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    },
    "additionalProp2": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    },
    "additionalProp3": {
      "co2": 0,
      "conso": 0,
      "distance": 0,
      "tempsConduite": 0
    }
  }
}
```

## Récupérer les notes affichées sur l'écran "Synthèse de flotte" de la webApp

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) et passage du token dans le header **X-AUTH-TOKEN**

### Définition {.tabset}

#### Endpoint
```
post /restapi/ecoAtecoconduitetitude/syntheseFlotte
```

#### Paramètres de la requête

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId *   | integer ($int64) | Identifiant du client. Obligatoire uniquement pour un utilisateur multi-clients |
| mode *         | AnalysisMode     | Mode d'analyse de la flotte (DETAIL ou SYNTHESIS) |

\* paramètre obligatoire 

#### Corps de la requête
```JSON
{
	"filter": {
		"categorieVehicle": [
			"ALL"
		],
		"displayMode": "string",
		"ecoConduiteVehicleCategory": "string",
		"filterBean": {
			"entities": [0],
			"persons": [0],
			"vehicleIds": [0]
		},
		"periodeBean": {
			"debut": "date",
			"fin": "date"
		},
		"timeUnit": "string",
		"version": "string"
	}
}
```
**Voici les différentes valeurs que peuvent avoir les paramètres du corps de cette requête** :
* displayMode : ENTITY, DRIVER, VEHICLE. Sélectionne les données d'entités, de conducteurs **ou** de véhicules.
* ecoConduiteVehicleCategory: UL (Utilitaire Léger), U (Utilitaire (- de 3,5T)), CITADINE, ALL (tout type de véhicule), NONE (pour n'avoir aucune donnée). Pour choisir le profil de véhicules dont vous voulez les données. *Ce qui est écrit entre parenthèse est ce à quoi ça correspond sur le site.*
* filterBean: En fonction du displayMode choisi, vous pourrez remplir un des trois tableaux d'identifiants d'entité, conducteur ou véhicule dont vous voulez les données. Laissez vide le tableau adéquat si vous voulez toutes les données (en dehors des critères sélectionnés ci-dessous).
* periodeBean: Les dates doivent être notées selon le format YYYY-MM-ddTHH:mm:ss.SSSZ
* timeUnit: DAY, WEEK, MONTH. Permet l'affichage par jour, semaine **ou** mois respectivement.
* version: ALL, ERCO, RENAULT_FAM, PSABTA, BUC, FLEET, CKUA (Cloud Kuantic), F2M (Stellantis). Afin de déterminer la version Écoconduite des véhicules que vous allez recevoir. *Ce qui est écrit entre parenthèse est ce à quoi ça correspond sur le site*.


#### Résultat de la requête **en mode DETAIL**
```JSON
{
	"challenges": {
		"map": [
			{
				"key": {
					"id": 0,
					"categorie": "string",
					"description": "string",
					"geosecuriteEnabled": boolean,
					"suppressionLogique": boolean,
					"dispositifIdentifiant": boolean,
					"privacyEnabled": boolean,
					"dioEnabled": boolean,
					"immobilisationCablee": boolean,
					"geolocalise": boolean,
					"nomImage": "string",
					"odirectMode": "string",
					"libelleTypeAsset": {
						"id": 0,
						"libelle": "string",
						"categorie": "string",
						"nomIcone": "string",
						"ordre": 0
					},
					"typeMotorisation": "string",
					"detectionPorteEnabled": boolean,
					"immatriculation": "string",
					"marque": "string",
					"modele": "string",
					"couleur": null,
					"numeroEmbarque": 0,
					"numeroSerie": null,
					"numeroParc": "string"
				},
				"value": [
					{
						"key": {
							"debut": 1709247600000,
							"fin": 1712008799999,
							"timeDuration": 0,
							"daysDuration": 0
						},
						"value": {
							"id": 0,
							"dateDebut": 1709251200000,
							"versionEcoConduite": "string",
							"uniteTemps": "string",
							"categorieVehiculeEco": "string",
							"moyenneNoteEcoConduiteRefOcean": 0,
							"moyenneNoteEcoConduiteRefClient": 0,
							"moyenneNoteSecuriteRefOcean": 0,
							"moyenneNoteSecuriteRefClient": 0,
							"distanceParcourueThermiqueM": 0,
							"distanceParcourueElectriqueM": 0,
							"dureeEffectiveCumuleeThermiqueS": 0,
							"dureeEffectiveCumuleeElectriqueS": 0,
							"consommationCumuleeL": 0,
							"consommationCumuleeKWh": 0,
							"emissionCo2Total": 0,
							"emissionCo2EviteTotal": 0
						}
					}
				]
			}
		]
	},
	"challengeAverageByDto": [
		{
			"key": {
				"id": 0,
				"categorie": "string",
				"description": "string",
				"geosecuriteEnabled": boolean,
				"suppressionLogique": boolean,
				"dispositifIdentifiant": boolean,
				"privacyEnabled": boolean,
				"dioEnabled": boolean,
				"immobilisationCablee": boolean,
				"geolocalise": boolean,
				"nomImage": "string",
				"odirectMode": "string",
				"libelleTypeAsset": {
					"id": 0,
					"libelle": "string",
					"categorie": "string",
					"nomIcone": "string",
					"ordre": 0
				},
				"typeMotorisation": "string",
				"detectionPorteEnabled": boolean,
				"immatriculation": "string",
				"marque": "string",
				"modele": "string",
				"couleur": null,
				"numeroEmbarque": 0,
				"numeroSerie": null,
				"numeroParc": ""
			},
			"value": {
				"id": null,
				"dateDebut": null,
				"versionEcoConduite": "string",
				"uniteTemps": null,
				"categorieVehiculeEco": null,
				"moyenneNoteEcoConduiteRefOcean": 0,
				"moyenneNoteEcoConduiteRefClient": 0,
				"moyenneNoteSecuriteRefOcean": 0,
				"moyenneNoteSecuriteRefClient": 0,
				"distanceParcourueThermiqueM": 0,
				"distanceParcourueElectriqueM": 0,
				"dureeEffectiveCumuleeThermiqueS": 0,
				"dureeEffectiveCumuleeElectriqueS": 0,
				"consommationCumuleeL": 0,
				"consommationCumuleeKWh": 0,
				"emissionCo2Total": 0,
				"emissionCo2EviteTotal": 0
			}
		}
	],
	"challengeAverageByPeriod": [
		{
			"key": {
				"debut": 1709247600000,
				"fin": 1712008799999,
				"timeDuration": 0,
				"daysDuration": 0
			},
			"value": {
				"id": null,
				"dateDebut": null,
				"versionEcoConduite": "string",
				"uniteTemps": null,
				"categorieVehiculeEco": null,
				"moyenneNoteEcoConduiteRefOcean": 0,
				"moyenneNoteEcoConduiteRefClient": 0,
				"moyenneNoteSecuriteRefOcean": 0,
				"moyenneNoteSecuriteRefClient": 0,
				"distanceParcourueThermiqueM": 0,
				"distanceParcourueElectriqueM": 0,
				"dureeEffectiveCumuleeThermiqueS": 0,
				"dureeEffectiveCumuleeElectriqueS": 0,
				"consommationCumuleeL": null,
				"consommationCumuleeKWh": null,
				"emissionCo2Total": null,
				"emissionCo2EviteTotal": null
			}
		}
	]
}
```
**Voici les différentes valeurs que peuvent avoir les paramètres du résultat de cette requête** :
* challenges: Tableau d'objet qui représente des lignes, chaque ligne correspondant à un(e) entité, conducteur ou véhicule. Cet objet en contient deux autres, un qui possède les informations du type de données choisi, le second qui contient un tableau qui possède la note de la donnée pour chaque mois.
* challengeAverageByDto: Tableau d'objet qui représente la moyenne de chaque ligne (donc la moyenne sur toute la sélection temporelle pour chaque donnée). Structuré de façon similaire à challenges, le paramètre value ne contient qu'un objet puiqu'il n'y a qu'une moyenne par donnée sur la sélection temporelle.
* challengeAverageByPeriod: Structuré de façon similaire à challengeAverageByDto, au lieu de contenir la moyenne de chaque entité/conducteur/véhicule, il contient la moyenne de toutes les notes sur chaque période de la sélection temporelle (ex: vous avez sélectionné les notes de véhicules par mois sur Mars et Avril 2024, alors le tableau contiendra deux cases, une pour chaque mois, qui fera la moyenne des notes de tous les véhicules).

#### Réponses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```
