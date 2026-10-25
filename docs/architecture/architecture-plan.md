# Plan d'architecture cible — à décider

- Statut : proposition de travail, pas une architecture approuvée.

## 1. Contraintes confirmées
- Zone de lancement : Côte d’Ivoire.
- Plusieurs filières doivent être couvertes dès le départ ; la liste reste à définir.
- Livraison progressive : MVP puis extensions ; le MVP n’est pas encore priorisé.
- Canaux : web et mobile Flutter.
- Hors ligne : l’utilisateur doit pouvoir saisir, consulter et modifier les données déjà téléchargées. Les types de données et les règles de conflit restent à spécifier.
- Multi-organisation : plusieurs clients/organisations avec cloisonnement des données ; la hiérarchie exacte reste à définir.
- Échelle visée : environ 800 000 producteurs ou davantage ; les volumes opérationnels détaillés restent à mesurer.
- Profils de départ : producteurs, collecteurs, administrateurs et agents de terrain.
- Hébergement : aucune option choisie ; une comparaison est requise.
- Réalisation principalement par le porteur du projet avec assistance IA : la simplicité opérationnelle et l’automatisation sont importantes.

## 2. Principes de départ
1. Commencer par un **monolithe modulaire** côté serveur tant que les contraintes n'imposent pas des services séparés.
2. Séparer domaine métier, cas d'usage, accès aux données et transport HTTP.
3. Définir des contrats API explicites et versionnés selon les besoins de compatibilité.
4. Concevoir l'offline-first comme une capacité produit, pas comme un simple cache d'écran.
5. Rendre la synchronisation idempotente, observable et résistante aux coupures.
6. Appliquer les permissions et la validation métier côté serveur.
7. Mesurer avant de distribuer ou d'optimiser.
8. Automatiser les tests et les contrôles qualité dès le premier incrément.

## 3. Vue logique proposée

```text
Web client ───────┐
                  ├── API / AuthN / AuthZ ── Application services ── Domain modules
Mobile client ────┘              │                    │                   │
   │                              │                    └── Events/outbox?  │
   ├─ Local store                 ├── Audit/logs                         ├─ Identity & access
   ├─ Sync queue                  ├── Observability                      ├─ Producer/farm
   └─ Conflict UX                 └── Rate limits                        ├─ Collection
                                                                          ├─ Traceability
Database + object storage + backup/restore                               ├─ Sustainability
                                                                          └─ Reporting/admin
```

Le diagramme est conceptuel. Les choix de stockage, de messages asynchrones et de découpage sont à confirmer après discovery.

## 4. Architecture mobile hors ligne
Prévoir une couche locale et un moteur de synchronisation. La spécification devra définir :
- données téléchargeables et périmètre autorisé par utilisateur ;
- opérations possibles hors ligne ;
- identifiants locaux uniques et idempotency keys ;
- file d'attente durable des modifications ;
- état de chaque élément : local, en attente, synchronisé, en conflit, rejeté ;
- règles de retry avec backoff, reprise après redémarrage et observabilité ;
- résolution des conflits par type de donnée ; aucune règle générique « last write wins » ne doit être adoptée sans validation ;
- traitement des fichiers/photos volumineux, quotas et reprise partielle ;
- versionnement des schémas et compatibilité d'une application mobile ancienne ;
- authentification, expiration de session, appareil perdu et effacement local ;
- gestion de la suppression et des conflits avec les données supprimées côté serveur.

## 5. Domaines métier candidats
- Identity & Access : identité, sessions, rôles, permissions, périmètres.
- Producer & Farm : producteurs, organisations, exploitations, parcelles, référentiels.
- Collection : opérations et mesures de collecte, si confirmées par le métier.
- Traceability : lots, événements, liens entre lots et historique, après définition métier.
- Sustainability : questionnaires, pratiques, contrôles ou certifications seulement selon les référentiels approuvés.
- Administration & Reporting : gestion des référentiels, qualité, exports, rapports et audit.

## 6. Données et stockage
Ne pas choisir le moteur de base de données avant d'avoir défini les relations, les requêtes, l'intégrité, les besoins géospatiaux, les transactions, les volumes et les contraintes d'exploitation. Évaluer au minimum :
- base relationnelle pour les relations et contraintes transactionnelles ;
- base documentaire si la flexibilité de schéma répond à des cas démontrés ;
- stockage objet pour photos et pièces jointes ;
- index géospatiaux si les parcours géographiques les nécessitent ;
- chiffrement, sauvegarde, restauration et politique de rétention.

Ne pas adopter plusieurs bases simplement pour suivre une mode. La cohérence opérationnelle prime.

## 7. API et contrats
- OpenAPI comme contrat documenté si l'API REST est retenue.
- Validation d'entrée centralisée et erreurs stables/documentées.
- Pagination, filtres et tri explicites pour les collections.
- Idempotence pour les commandes pouvant être rejouées, particulièrement la synchronisation.
- Corrélation de requête et audit sans exposer de données sensibles.
- Politique de compatibilité pour les versions web/mobile déployées séparément.

## 8. Architecture frontend
Web : structure par domaine fonctionnel, composants réutilisables, séparation UI / cas d'usage / accès API, états chargement-erreur-vide, permissions côté serveur toujours autoritatives.

Mobile : séparation présentation / domaine / données, persistance locale durable, couche réseau remplaçable, gestion explicite des états de synchronisation et télémétrie respectueuse de la confidentialité.

Le choix exact des frameworks, bibliothèques et gestionnaires d'état reste à documenter dans un ADR après validation des compétences et contraintes.

## 9. Sécurité et exploitation
- Authentification et autorisation fondées sur un modèle de menace.
- Isolation des données entre organisations/périmètres si le besoin est confirmé.
- Gestion des secrets, chiffrement en transit et au repos selon les risques.
- Audit des actions sensibles.
- CI avec tests, lint, analyse de dépendances et scan de secrets.
- Environnements séparés, migrations contrôlées, sauvegardes et exercices de restauration.
- Logs, métriques, traces et alertes sans données sensibles.
- SLO, RPO, RTO et stratégie de déploiement à fixer avec l'exploitation.

## 10. Stratégie de tests
- Unitaires : règles métier et transitions.
- Intégration : base de données, transactions, stockage, synchronisation.
- Contrats : compatibilité API et clients.
- E2E : parcours critiques web et mobile.
- Offline : coupure réseau, redémarrage, retries, doublons, conflits, appareils à espace faible.
- Sécurité : autorisations, isolation, validation, upload de fichiers, sessions.
- Performance : scénarios et volumes issus des objectifs validés.
- Reprise : restauration de sauvegarde et réconciliation des données.

## 11. Décisions à prendre dans des ADR
1. Stack backend et organisation du monolithe modulaire.
2. Base de données et stratégie géospatiale.
3. Modèle d'identité, rôles, permissions et périmètres d'organisation.
4. Stockage local mobile et stratégie de synchronisation.
5. Hébergement, régions, stockage objet et sauvegardes.
6. API, versionnement et compatibilité mobile.
7. Observabilité et stratégie de livraison.

## 12. Critères de validation de l'architecture
L'architecture ne sera considérée comme prête que lorsque les scénarios offline prioritaires, les modèles de données, les volumes cibles, les frontières de confiance, les exigences de confidentialité et le plan de reprise sont suffisamment documentés pour être testés.
