# Veille tarifaire des spiritueux — Whiskies du Monde

> Projet final Data Analyst · DataSuits 

## 1\. Contexte

Whiskies du Monde (WDM) distribue des spiritueux, notamment des whiskies et des rhums. L’entreprise communique des prix marketing conseillés (PMC), tandis que les revendeurs fixent leurs propres prix publics. WDM souhaite mesurer les écarts avec les PMC et situer le prix de ses produits face à la concurrence.

## 2\. Problématique

**Question centrale** — Comment exploiter les prix publics relevés chez les revendeurs pour situer les spiritueux de Whiskies du Monde face à des produits concurrents comparables, mesurer les écarts avec les prix marketing conseillés (PMC) et identifier les références à examiner en priorité ?

**Utilisateur** — Le Category Manager de WDM utilisera le tableau de bord Power BI pour décider quelles références nécessitent une analyse tarifaire plus approfondie.

## 3\. Indicateurs clés (KPI)

|KPI|Calcul prévu|Décision éclairée|
|-|-|-|
|Écart au PMC (€ et %) des références WDM|Prix revendeur – PMC<br />(Prix revendeur – PMC) /PMC x100<br />|Repérer les écarts à examiner par référence et par revendeur.|
|Écart au prix des concurrents sur refs équivalentes|Comparer le prix public observé de la référence WDM au prix médian des produits concurrents comparables.|Identifier les références dont le positionnement tarifaire mérite d’être réexaminé.|
|Nombre de références à examiner|Compter chaque référence signalée une seule fois, selon des seuils et une règle de sélection à définir.|Prioriser la revue tarifaire.|

## 4\. Sources de données

|Source|Type|Contenu|Collecte|Fréquence|
|-|-|-|-|-|
|Base produits Off Trade 2026 de WDM|Excel interne|Famille, marque, code article, EAN, désignation, contenance, degré d’alcool et PMC TTC.|Fichier reçu.|Version 2026.|
|Leclerc|Site marchand|Prix publics et caractéristiques produits.|Collecte Python prévue.|Relevés datés sur une période à définir.|
|Carrefour|Site marchand|Prix publics et caractéristiques produits.|Collecte Python prévue.|Relevés datés sur une période à définir.|
|Intermarché|Site marchand|Prix publics et caractéristiques produits.|Collecte Python prévue.|Relevés datés sur une période à définir.|
|Coopérative U|Site marchand|Prix publics et caractéristiques produits.|Collecte Python prévue.|Relevés datés sur une période à définir.|

## 5\. Architecture du pipeline

|Étape|Rôle dans le projet|Où dans le dépôt|Statut|
|-|-|-|-|
|1. Sources|Identifier le catalogue WDM et les sites marchands.|README|Catalogue reçu, sites retenus.|
|2. Collecte|Relever les prix publics et dater chaque observation.|`scripts/`|À faire.|
|3. Nettoyage et transformation|Harmoniser les libellés, contenances, prix et formats d’EAN.|`scripts/`, `data/processed/`|À faire.|
|4. Rapprochement et agrégation|Relier les relevés WDM à leur référence exacte, constituer les panels concurrents et calculer les écarts.|`scripts/`, `sql/`|À faire.|
|5. Stockage|Structurer les références et les relevés dans MySQL.|`sql/`|À faire.|
|6. API|Mettre les données préparées à disposition via une API REST.|`api/`|À faire.|
|7. Exploitation|Interroger les données en SQL et visualiser les écarts dans Power BI.|`sql/`, `dashboard/`|À faire.|

## 6\. Structure du projet

* `data/raw/` et `data/processed/` — Données brutes et préparées utilisées localement.
* `notebooks/` et `scripts/` — Exploration et scripts Python.
* `sql/` et `api/` — Schéma MySQL, requêtes et API REST.
* `dashboard/` — Rapport Power BI.
* `docs/` — Fiche projet et documentation.

## 7\. Technologies

Python pour la collecte et la préparation avec Pandas, MySQL et SQL pour le stockage et l’analyse, API REST pour la mise à disposition, Power BI pour la visualisation et GitHub Desktop pour le suivi des versions.

## 8\. Lancer le projet

Le projet est au stade du cadrage. Les instructions de lancement seront ajoutées à mesure que les scripts, la base MySQL et l’API seront mis en place.

## 9\. Avancement

* \[x] Cadrage du sujet, fiche projet et arborescence.
* \[x] Réception du catalogue interne WDM.
* \[ ] Collecte des prix publics.
* \[ ] Nettoyage et rapprochement des données.
* \[ ] Stockage MySQL et analyse SQL.
* \[ ] API REST et tableau de bord Power BI.

## 10\. Limites et points de vigilance

* La première version photographiera les prix affichés sur une période définie. Le magasin sélectionné et les promotions peuvent influer sur les prix relevés.
* L’écart au PMC se calcule sur une référence identique. L’EAN permet de confirmer la correspondance lorsqu’il est disponible. Le panel concurrent repose sur des critères de comparabilité comme le type, l’origine, le vieillissement et la contenance.
* Le classeur interne WDM est conservé hors du dépôt public.

## 11\. Utilisation de l'IA

L’IA a aidé à formuler la problématique, à préciser les calculs des indicateurs et à adapter le README au projet WDM.

## Auteur

Carine

