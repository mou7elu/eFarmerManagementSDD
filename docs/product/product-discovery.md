# Product Discovery — eFarmerManagement

- Statut : **cadrage initial mis à jour ; validation métier encore nécessaire**
- Version : 0.2
- Date : 2026-10-25
- Décideur produit / sponsor : moi

## 1. Vision provisoire
Construire une plateforme de gestion agricole pour la Côte d’Ivoire, accessible via le web et le mobile, couvrant plusieurs filières dès le départ et permettant aux acteurs autorisés de saisir, consulter et modifier hors ligne les données déjà téléchargées. Le produit vise une architecture capable d’évoluer vers environ 800 000 producteurs dans la base ou davantage. Le lancement doit se faire par un MVP, puis des extensions progressives.

Cette vision résume les choix de cadrage fournis par le porteur du projet. Elle ne remplace pas les ateliers métier : les problèmes prioritaires, les workflows, les responsabilités, les mesures de succès et les critères d’acceptation restent à valider.

## 2. Décisions confirmées par le porteur du projet

| ID | Sujet | Décision confirmée | Limites / précisions manquantes |
|---|---|---|---|
| D-001 | Zone de lancement | Côte d’Ivoire uniquement | Zones pilotes, langues et contraintes réglementaires à préciser |
| D-002 | Filières | Plusieurs filières dès le départ | Liste des filières et particularités par filière à définir |
| D-003 | Stratégie de livraison | MVP d’abord, puis extensions | Périmètre du MVP non encore priorisé |
| D-004 | Utilisateurs de départ |  collecteurs, administrateurs et agents de terrain ; tous les profils doivent être considérés dès le lancement | Sous-rôles, permissions et disponibilité réelle de chaque profil à préciser |
| D-005 | Canaux | Web React et mobile Flutter visés | Répartition précise des fonctions entre web et mobile à définir |
| D-006 | Mode hors ligne | Saisir, consulter et modifier les données déjà téléchargées sans connexion | Types de données, limites temporelles, conflits et règles de sécurité à définir |
| D-007 | Organisations | Plusieurs clients/organisations avec cloisonnement des données | Hiérarchie entre client, organisation, coopérative, campagne et zone à définir |
| D-008 | Hébergement | Décision reportée à une comparaison | Budget, résidence des données, exigences d’exploitation et options à comparer |
| D-009 | Échelle | Environ 800 000 producteurs ou davantage | Volumes de parcelles, événements, fichiers, utilisateurs simultanés et pics inconnus |
| D-010 | Équipe | Porteur du projet principalement, avec assistance IA | Disponibilité, expertise, budget, calendrier et recours éventuel à des prestataires à préciser |
| D-011 | Modules du MVP,Priorisation MVP = livrable de sortie de Discovery | Tous les modules doivent être étudiés avant de prioriser | La présence de tous les domaines dans l’étude ne signifie pas qu’ils seront tous livrés dans le MVP |
| D-012 | Données personnelles | Les données personnelles des producteurs (identité, contacts, localisation) seront traitées selon un régime de minimisation et de durées de conservation à définir | base légale, durées, droits des personnes à préciser. |
## 3. Portée métier candidate à étudier
Les domaines suivants sont à examiner avant de décider du MVP :
- gestion des producteurs,  parcelles ;
- collecte ;
- traçabilité ;
- durabilité ;
- administration, gestion et reporting ;
- identité, accès et gestion multi-organisation, nécessaires à l’ensemble.

Les noms de modules sont des catégories de travail, pas encore des spécifications approuvées. Il faut déterminer leurs frontières, les processus réels et les éventuelles intégrations.

## 4. Contraintes et principes confirmés ou proposés

### Confirmés
- Pays de lancement : Côte d’Ivoire.
- Plusieurs filières à couvrir dès le départ.
- Livraison progressive : MVP puis extensions.
- Web et mobile.
- Saisie, consultation et modification de données déjà téléchargées hors ligne.
- Cloisonnement entre plusieurs clients/organisations.
- Capacité cible : environ 800 000 producteurs ou davantage.
- Réalisation principalement par le porteur du projet avec assistance IA.

### Principes proposés, à valider
- Favoriser une architecture modulaire et éviter les microservices sans justification mesurée.
- Traiter la synchronisation hors ligne comme une capacité de premier ordre, avec file d’attente durable, idempotence, reprise et résolution explicite des conflits.
- Vérifier les permissions côté serveur, y compris pour les données synchronisées.
- Tester la charge avec des profils réalistes avant de conclure que l’architecture supporte l’échelle cible.
- Ne choisir la base de données, l’hébergement ou les services externes qu’après comparaison documentée.

## 5. Hypothèses à tester — ne pas traiter comme des décisions

| ID | Hypothèse | Validation proposée | Statut |
|---|---|---|---|
| HYP-001 | Les agents de terrain réaliseront une part importante des saisies hors ligne | Observation de terrain et entretiens par profil | À tester |
| HYP-002 | Les données téléchargées hors ligne peuvent être mises à jour par plusieurs utilisateurs ou appareils | Cartographie des workflows et atelier sur les conflits | À tester |
| HYP-003 | Une organisation cliente peut contenir plusieurs coopératives ou zones | Atelier de gouvernance métier | À tester |
| HYP-004 | Les domaines collecte, traçabilité, durabilité et gestion sont tous nécessaires au produit cible | Inventaire des processus, fréquence et valeur métier | À confirmer |
| HYP-005 | Le volume de 800 000 producteurs implique aussi de fortes volumétries de parcelles, événements et pièces jointes | Construire des scénarios de charge séparés par type de donnée | À mesurer |
| HYP-006 | Le questionnaire existant sur les exploitants peut être réutilisé comme source de découverte | Revue champ par champ avec le métier et contrôle de minimisation des données | À confirmer |
| HYP-007 | React est adapté au web pour ce produit | à valider en Phase 2 | À confirmer |

## 6. Questions de recherche et entretiens

Interroger ou observer les 3 catégories de profils :
- **Collecteurs** : déroulé réel de la collecte, mesures, unités, corrections, validations et justificatifs.
- **Agents de terrain** : préparation des visites, formulaires, GPS, pièces jointes, partage d’appareil et synchronisation différée.
- **Administrateurs** : création des organisations, gestion des accès, référentiels, audit, qualité des données, exports et support.

Ne pas supposer que chaque profil aura les mêmes écrans ou droits sur web et mobile. Documenter les parcours AS-IS puis TO-BE.

## 7. Échelle et critères de réussite à définir
La cible « environ 800 000 producteurs ou davantage » est confirmée comme ambition de volumétrie, mais elle ne constitue pas encore un objectif de performance testable. Il faut préciser séparément : producteurs enregistrés, utilisateurs actifs, utilisateurs simultanés, parcelles, événements de collecte/traçabilité, photos/documents, synchronisations quotidiennes et pics de trafic.

Les seuils de performance, disponibilité, synchronisation, récupération et adoption doivent être fixés après analyse des usages et du budget. Mesures candidates : taux de synchronisation réussie, durée des tâches terrain, doublons, conflits, complétude des données, adoption par profil, latence des parcours critiques et capacité de restauration.

## 8. Livrables de sortie de Discovery
- Parties prenantes, décideur produit et responsabilités identifiés.
- Parcours métier observés pour les trois profils.
- Liste des filières et processus cibles validée.
- Cartographie des organisations et règles de cloisonnement validées.
- Matrice des fonctions disponibles en ligne/hors ligne et sur chaque canal.
- Périmètre MVP priorisé avec inclusions, exclusions et justification.
- Volumes et objectifs non fonctionnels mesurables.
- Risques, hypothèses et questions ouvertes affectés à un responsable.
- Comparaison d’hébergement et premières décisions d’architecture documentées.

## 9. Critère de sortie de Discovery
La phase ne sera pas considérée comme terminée avant validation du MVP, des parcours prioritaires, des règles de cloisonnement multi-organisation, des besoins hors ligne, des données personnelles à traiter, des scénarios de charge et des indicateurs de réussite. Les décisions inconnues restent explicitement ouvertes.
