# Questions ouvertes — eFarmerManagement

- Statut : réponses de cadrage intégrées le 2026-10-25.
- Règle : une réponse de cadrage ne vaut pas validation détaillée d'une règle métier ou d'une architecture.

## 1. Décisions déjà confirmées

| ID | Sujet | Réponse | Conséquence |
|---|---|---|---|
| Q-001 | Pays de lancement | Côte d’Ivoire uniquement | |
| Q-002 | Filières | Plusieurs filières dès le départ | Obtenir la liste exacte et distinguer les données communes des données propres à chaque filière |
| Q-003 | Livraison | MVP puis extensions | Définir le MVP après étude comparative de tous les modules |
| Q-004 | Profils de départ | collecteurs, administrateurs, agents de terrain ; tous considérés simultanément | Définir les responsabilités et permissions exactes |
| Q-005 | Hors ligne | Saisir, consulter et modifier les données déjà téléchargées | Définir le périmètre des données locales et les règles de conflit |
| Q-006 | Organisations | Plusieurs clients/organisations avec cloisonnement | Définir le modèle hiérarchique et les tests d’isolation |
| Q-007 | Hébergement | À comparer | Ne pas choisir de fournisseur avant les critères de comparaison |
| Q-008 | Échelle | Environ 800 000 producteurs ou davantage | Établir un modèle de charge chiffré au-delà du seul nombre de producteurs |
| Q-009 | Équipe | Porteur du projet principalement, avec assistance IA | Adapter le plan à la capacité disponible et automatiser les contrôles |
| Q-010 | Priorisation des modules | Tous les modules doivent être étudiés avant de prioriser | Ne signifie pas que tous seront inclus dans le MVP |

## 2. Priorité P0 — décisions bloquantes pour le MVP et les fondations

| ID | Question | Pourquoi c’est important | Responsable suggéré | Statut |
|---|---|---|---|---|
| OPEN-001 | Quelles filières exactes sont concernées au lancement ? | Modèle de données, formulaires et règles spécifiques | Sponsor métier | Ouverte |
| OPEN-002 | Quelles zones pilotes, langues et unités doivent être prises en charge ? | Parcours terrain et référentiels | Métier / opérations | Ouverte |
| OPEN-003 | Quels processus précis couvrent collecte, traçabilité, durabilité et gestion ? | Empêcher un périmètre flou ou infini | Responsables de domaines | Ouverte |
| OPEN-004 | Quels critères permettent de sélectionner le MVP et quelles fonctionnalités sont explicitement exclues ? | Réaliser une première livraison utile | Sponsor produit | Ouverte |
| OPEN-005 | Qui est propriétaire des données et comment s'organisent client, organisation, coopérative, campagne et zone ? | Cloisonnement, autorisations et modèle de données | Métier + sécurité | Ouverte |
| OPEN-006 | Quelles opérations exactes sont autorisées hors ligne pour chaque type de donnée ? | Stockage local, sécurité et expérience utilisateur | Opérations + métier | Ouverte |
| OPEN-007 | Comment résoudre les modifications concurrentes, suppressions, doublons et validations hors ligne ? | Éviter les pertes silencieuses et incohérences | Métier + architecture | Ouverte |
| OPEN-008 | Quels volumes sont attendus pour les utilisateurs actifs/simultanés, parcelles, événements, fichiers et synchronisations ? | Dimensionnement et tests de charge | Produit + opérations | Ouverte |
| OPEN-009 | Quelles données personnelles, GPS, photos et pièces justificatives seront collectées, pour quelles finalités et combien de temps ? | Confidentialité, sécurité et conservation | Responsable métier / juridique | Ouverte |
| OPEN-010 | Quelles fonctions doivent être accessibles aux producteurs directement, et lesquelles seront gérées par les agents en leur nom ? | Parcours et responsabilités | Métier | Ouverte |

## 3. Priorité P1 — exigences métier détaillées

| ID | Question | Pourquoi c’est important | Statut |
|---|---|---|---|
| OPEN-011 | Quelles données identifient de façon fiable un producteur, une exploitation et une parcelle ? | Identifiants et dédoublonnage | Ouverte |
| OPEN-012 | Un producteur peut-il appartenir à plusieurs coopératives ou être lié à plusieurs exploitations ? | Relations métier | Ouverte |
| OPEN-013 | Quelle est la définition d’un lot et comment peut-il être créé, divisé, fusionné ou transféré ? | Intégrité de la traçabilité | Ouverte |
| OPEN-014 | Quelles étapes, mesures, unités, justificatifs et statuts composent une collecte pour chaque filière ? | Workflow et validations | Ouverte |
| OPEN-015 | Quelles conversions, tolérances et règles de correction sont autorisées ? | Cohérence des mesures | Ouverte |
| OPEN-016 | Quelles données et règles définissent la durabilité ou une certification ? Quels référentiels sont officiellement requis ? | Éviter d’inventer des critères | Ouverte |
| OPEN-017 | Quelles actions exigent validation, double contrôle ou signature ? | Contrôle métier et audit | Ouverte |
| OPEN-018 | Quels tableaux de bord, rapports, exports et notifications sont requis au MVP ? | Priorisation des interfaces | Ouverte |
| OPEN-019 | Quelles langues, devises, formats de date et unités sont nécessaires ? | Internationalisation et cohérence | Ouverte |
| OPEN-020 | Quelle répartition des fonctionnalités entre web et mobile est attendue ? | Spécifications par canal | Ouverte |
| OPEN-021 | Que devient l’accès aux données lorsqu’un compte ou un agent est désactivé ? | Continuité opérationnelle et audit | Ouverte |

## 4. Priorité P1 — architecture et exploitation

| ID | Question | Pourquoi c’est important | Statut |
|---|---|---|---|
| OPEN-022 | Quel budget, calendrier et niveau de service l’équipe peut-elle soutenir ? | Réalisme du projet | Ouverte |
| OPEN-023 | Hébergement cloud, local ou hybride ? Existe-t-il des contraintes de région ou de résidence des données ? | Comparaison des options | Ouverte |
| OPEN-024 | Quelles intégrations externes sont nécessaires (SMS, cartographie, paiements, outils existants, systèmes clients) ? | Dépendances et coûts | Ouverte |
| OPEN-025 | Quels objectifs de disponibilité, latence, RPO et RTO sont attendus ? | Exploitation et reprise | Ouverte |
| OPEN-026 | Quelles règles de conservation, export et suppression des données s’appliquent ? | Cycle de vie et conformité | Ouverte |
| OPEN-027 | Quels appareils, versions Android/iOS et capacités de stockage faut-il supporter ? | Tests offline et compatibilité | Ouverte |
| OPEN-028 | Comment s’authentifier et autoriser les actions hors ligne, et que faire en cas d’appareil perdu ou de session expirée ? | Sécurité des données locales | Ouverte |
| OPEN-029 | Quels outils et compétences sont disponibles pour l’exploitation, la surveillance, les sauvegardes et le support ? | Choix soutenables pour une équipe réduite | Ouverte |

## 5. Sources à examiner
L’ancien dépôt contient des éléments qui peuvent aider à découvrir les champs et processus. Ils doivent être examinés comme des sources de discussion, jamais importés automatiquement comme vérité métier. Valider l’utilité, l’obligation, la sensibilité, la finalité et la durée de conservation de chaque champ.
