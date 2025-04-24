---
title: Eco-Driving
description: 
published: true
date: 2024-10-31T14:45:29.845Z
tags: 
editor: markdown
dateCreated: 2024-10-24T13:16:09.120Z
---

# Eco-Driving Management

This API allows you to retrieve:

- Data related to drivers' eco-driving for a given period.
- "Safety" and "Consumption" scores by month or week.
- Scores displayed on the "Fleet Summary" screen of the webApp.

## Retrieve Safety and Consumption Scores by Month or Week

[Additional documentation on SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getEchoattitudeGraphUsingGET)

[Prior authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**.

### Definition {.tabset}

#### Endpoint
```
get /restapi/ecoAttitude/v1/get_ecoattitude_graph
```

#### Request Parameters

| Name            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId *   | integer ($int64) | Client identifier. Required only for multi-client users |
| individuId     | integer ($int64) | Driver identifier. |
| EC_MONTH_START | integer ($int32) | Start month              |
| EC_MONTH_END   | integer ($int32) | End month                |
| EC_YEAR_START  | integer ($int32) | Start year             |
| EC_YEAR_END    | integer ($int32) | End year               |
| EC_MODE        | string           | Choose: week or month |

\* required parameter 

#### Responses

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

## Retrieve Data Related to Drivers' Eco-Driving for a Given Period

[Documentation supplémentaire sur SWAGGER](https://v3.oceansystem.com/ocean-3.0.0/apidocs/#/monecoattitude/getDatasUsingGET)

[Authentification préalable nécessaire](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**

### Definition {.tabset}

#### Endpoint
```
get /restapi/ecoAttitude/v1/get_datas
```

#### Request Parameters

| Name            | Type             | Description                                                                                  |
| --------------- | ---------------- | -------------------------------------------------------------------------------------------- |
| customerId *    | integer ($int64) | Customer identifier. Required only for multi-client users                                   |
| EC_MONTH_START  | integer ($int32) | Start month                                                                                |
| EC_MONTH_END    | integer ($int32) | End month                                                                                  |
| EC_YEAR_START   | integer ($int32) | Start year                                                                                 |
| EC_YEAR_END     | integer ($int32) | End year                                                                                   |
| EC_MODE         | string           | Choose: week or month                                                                      |

\* mandatory parameter

#### Responses

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

## Retrieve Scores Displayed on the "Fleet Summary" Screen of the WebApp

[Prior authentication required](./acces.md#authentification-par-requête-post) and passing the token in the header **X-AUTH-TOKEN**.

### Definition {.tabset}

#### Endpoint
```
post /restapi/ecoAtecoconduitetitude/syntheseFlotte
```

#### Request Parameters

| Nom            | Type             | Description                |
| -------------- | ---------------- | -------------------------- |
| customerId *   | integer ($int64) | Client identifier. Required only for multi-client users |
| mode *         | AnalysisMode     | Fleet analysis mode (DETAIL or SYNTHESIS) |

\* required parameter 

#### Request Body
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
**Here are the different values that the parameters in the body of this request can have**:
* **displayMode**: ENTITY, DRIVER, VEHICLE. Selects data for entities, drivers **or** vehicles.
* **ecoConduiteVehicleCategory**: UL (Light Utility), U (Utility (- under 3.5T)), CITADINE, ALL (any type of vehicle), NONE (to have no data). To choose the vehicle profile for which you want data. *What is written in parentheses corresponds to what it means on the site.*
* **filterBean**: Depending on the chosen displayMode, you can fill one of the three arrays of entity, driver, or vehicle identifiers for which you want data. Leave the appropriate array empty if you want all data (outside the selected criteria below).
* **periodeBean**: Dates must be noted in the format YYYY-MM-ddTHH:mm:ss.SSSZ.
* **timeUnit**: DAY, WEEK, MONTH. Allows display by day, week **or** month respectively.
* **version**: ALL, ERCO, RENAULT_FAM, PSABTA, BUC, FLEET, CKUA (Cloud Kuantic), F2M (Stellantis). To determine the eco-driving version of the vehicles you will receive. *What is written in parentheses corresponds to what it means on the site*.


#### Result of the Request **in DETAIL mode**
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
**Here are the different values that the parameters in the result of this request can have**:
* **challenges**: An array of objects representing rows, each row corresponding to an entity, driver, or vehicle. This object contains two others: one with the information of the chosen data type, and the second containing an array with the score of the data for each month.
* **challengeAverageByDto**: An array of objects representing the average of each row (thus the average over the entire time selection for each data). Structured similarly to challenges, the value parameter contains only one object since there is only one average per data over the time selection.
* **challengeAverageByPeriod**: Structured similarly to challengeAverageByDto, instead of containing the average of each entity/driver/vehicle, it contains the average of all scores over each period of the time selection (e.g., if you selected vehicle scores by month for March and April 2024, then the array will contain two entries, one for each month, averaging the scores of all vehicles).

#### Responses

```application/json;charset=utf-8
200 OK
401 UNAUTHORIZED
403 FORBIDDEN
404 NOT FOUND
```
