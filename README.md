# Hackaviz2020
> Le tourisme dans la région Occitanie en 2018

Tout au long de l’année chaque nuit, des milliers de touristes dorment dans notre belle région. Nous avons réussi à assembler un jeu de données unique qui les localise et les compte par nuitée. Nous connaissons les capacités d’hébergement (hôtel, camping,..) de chaque département. Nous savons aussi d’où ils viennent que ce soit d’un département Français ou de l’étranger. Nous savons enfin le temps qu’il faisait et les principaux événements culturels du jour.

| Synthétique et facile d'accès | Le plus détaillé mais pas le plus simple à exploiter | Croisement capacités x nuités, sert de complément optionnel aux autres| 
| :--: | :--: | :--: |
|  *nuitees.xlsx et .csv* | *par_origines.xlsx et .csv* | *capacites.xlsx, .csv et .geojson* |
| par jour en synthèse par dpt | par jour avec tous les détails | par semaine en catégories de nuitées par dpt |

Il est possible de faire de belles visualisations à partir d'un seul de ces trois fichiers de données, le plus simple étant *nuitees* qui est un aggrégat de *par_origines*. Les plus experts arriveront à combiner les trois, mais il n'est pas certain que la plus belle histoire ait besoin de toutes ces données. 

## par_origines

| Variable | Format | Définition | Exemple | 
| :-- | :--: | :-- | --: |
| date | année-mois-jour | Date du comptage | 2018-01-01 |
| org | caractères | Département ou pays d’origine des touristes. **Attention** : certains pays peuvent être regroupés. | 01 ou DK+SE+NO |
| dest | caractères | Département de destination en Occitanie. **Attention** : doit être importé en caractères sinon le département 09 est importé comme 9 | 09 |
| volume | entier | Nuitées dans le département de destination | 459 |
| vacances_org | entier | Statut des vacances du département d’origine. 0: pas en vacances, 1: en vacances, 2: non renseigné | 1 |
| T_midi | entier |  Température °C à midi (solaire) dans la préfecture du département | 25 |
| meteo | entier | Statut qualificatif de la météo du département de destination : 0: météo très défavorable, 1: météo défavorable, 2: météo correcte, 3: météo favorable, 4: météo idéale | 0 |
| nb_evt | entier| Nombre d’événements majeurs dans le département de destination | 2 |


## nuitées

| Variable | Format | Définition | Exemple |
| :-- | :--: | :-- | --: |
| date | année-mois-jour | Date du comptage | 2018-01-01 |
| dpt_09 | entier | Nuitées dans le 09 | 36427 |
| dpt_11 | entier | Nuitées dans le 11 | 120186 |
| dpt_xx | entier | Nuitées dans le xx | 567 |

**Attention** : pour les 2018-12-03 et le 2018-08-29, le nombre de nuitées est égal à zéro à cause d’un problème de récupération de données pour ces jours-là.

Le fichier compléments.xlsx contient des informations supplémentaires : codage des départements, codage des pays et liste des évenements.


## capacites

| Variable | Format | Définition | Exemple |
| :-- | :--: | :-- | --: |
| dpt | caractère| Département de destination en Occitanie. **Attention** : doit être importé en caractères sinon le département 09 est importé comme 9 | 09 |
| nom_dpt | caractère | Nom du département| Ariège|
| pop_dpt | entier| Population du département| 1376737 |
| Hbgt_collectif | entier | Places (personnes) en hébergement collectif (par jour) | 16248|
| Hbgt_locatif | entier| Places (personnes) en hébergement locatif (par jour) | 10569 |
| Hbgt_plein_air |entier| Places (personnes) en hébergement de plein air (par jour) | 11284 |
| Hbgt_hotel | entier | Places (personnes) en hébergement hôtelier (par jour) | 10231 |
| Hbgt_total | entier | Places (personnes) total (par jour) | 48332 |

**Attention**:  le nombre de places en hébergement collectif est nul pour le Tarn et Garonne par absence de données.

# Information sur les sources des données 

* Les données volume de nuitées proviennent d'un opérateur de téléphonie mobile déduites des bornages téléphoniques. Elles doivent être considérées comme des estimateurs statistiques. Ces données ont été fournies par le Comité Régional du Tourisme (CRT) 
* Les données concernant les capacités d’hébergement ont été construites par TDV à partir de données fournies par le Comité Régional du Tourisme (CRT).
* Les données concernant les événements ont été construites par TDV à partir de données fournis par le Comité Régional du Tourisme (CRT)
* Les données méteo proviennent d'un site internet fournissant l'historique des données météo pour un grand nombre de villes en France et dans le monde
* Les données de géométrie des départements sont incluses uniquement dans le fichier geojson. Ce format est adapté pour ceux qui souhaitent utiliser des outils de cartographie tels que le logiciel libre QGIS ou des librairies javascript telles que d3.js.

**Ces jeux de données sont à l’usage exclusif de l’Hackaviz 2020. Pour toute autre utilisation veuillez contacter l’association [Toulouse DataViz](mailto:contact@toulouse-dataviz.fr)**

