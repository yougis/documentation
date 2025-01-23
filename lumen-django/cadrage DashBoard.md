# Cadrage projet "WashBoard" plugin


Objectif :



- Permettre l’agrégation des données sur des référentiels spatiaux

- Permettre le filtrage dynamique

- Proposer des modes de représentation cartographique conçu pour être compris (cartographie thématique - sémiologie graphique)

- Proposer de fonctionnalité d'analyse spatiale simple ?


- Implémentation par le développeur la plus simple et rapide possible "à la manière du geoCommon ou du solrCommon"
Comment :

- Identifier les données coté domaine

  - Identifier les attributs agrégateurs (localisants : attributs permettant de géoréferencer l'entité comme la commune, une route, une adresse ...). La géométrie si existante servira pour agréger l'entité à des objets géographiques de référence (surfacique, ponctuelles et linéaire).

  - Identifier les attributs valeurs sur lesquels porterons les méthodes différentes méthodes d'agrégations,



Les méthodes d’agrégations :
- les différentes méthodes d'agrégations
Cas des valeurs quantitatives
  - taux
  - stock
Cas des valeurs qualitatives
  - ordonnées
  - distinctes
