# Plan d'architecture cible — à décider

- Statut : proposition de travail, pas une architecture approuvée.

## 1. Contraintes confirmées
- Zone de lancement : Côte d'Ivoire ; zones pilotes, langues et unités à préciser.
- Filières : plusieurs filières dès le départ (cacao, café, anacarde, hévéa, palmier à huile, autres) ; liste exacte à définir .
- Livraison : progressive, MVP puis extensions ; MVP non encore priorisé.
- Canaux : web + mobile Flutter.
- Hors ligne : saisir, consulter et modifier les données déjà téléchargées ; types de données, opérations autorisées et règles de conflit à spécifier.
- Multi-organisation : plusieurs clients/organisations avec cloisonnement confirmé ; hiérarchie exacte à trancher : Client → Organisation → Coopérative → Campagne → Zone.
- Échelle : ~800 000 producteurs ou davantage ; volumes opérationnels détaillés à mesurer — le nombre de producteurs ne suffit pas à définir la charge (principe 6).
- Profils de découverte : collecteurs, agents de terrain, administrateurs. Le producteur est une entité métier (données gérées par les profils), pas un profil utilisateur au lancement.
- Hébergement : aucune option choisie ; comparaison requise .
- Équipe : porteur principalement + assistance IA → simplicité opérationnelle et automatisation prioritaires.
- Données personnelles : à cadrer (identité, contacts, GPS, photos, pièces justificatives ; finalités et durées de conservation).

## 2. Principes de départ
1. Monolithe modulaire côté serveur tant que les contraintes n'imposent pas des services séparés (cohérent avec la soutenabilité par équipe réduite).
2. Séparer domaine métier, cas d'usage, accès aux données et transport HTTP.
3. Contrats API explicites et versionnés selon les besoins de compatibilité.
4. Offline-first comme capacité produit, pas comme cache d'écran.
5. Synchronisation idempotente, observable et résistante aux coupures.
6. Permissions et validation métier côté serveur (y compris pour les données synchronisées).
7. Mesurer avant de distribuer ou d'optimiser.
8. Automatiser tests et contrôles qualité dès le premier incrément.
9. Isolation multi-organisation par défaut : toute requête, tout stockage et toute synchronisation sont cloisonnés .
10. Documenter les décisions dans des ADR (principe 7 de la vision).

## 3. Vue logique proposée

```text
Web client ───────┐
                  ├── API / AuthN / AuthZ ── Application services ── Domain modules
Mobile client ────┘              │                    │                   │
   │                              │                    └── [outbox/events]? (option)
   ├─ Local store                 ├── Audit/logs                         ├─ Identity & access
   ├─ Sync queue                  ├── Observability                      ├─ Producer/farm
   └─ Conflict UX                 └── Rate limits                        ├─ Collection
                                                                          ├─ Traceability
[Stockage persistant]? + [Stockage fichiers]? + backup/restore            ├─ Sustainability
   (candidats, non décidés — cf. §6)                                      └─ Reporting/admin
```

Le diagramme est conceptuel. Les choix de stockage, de messages asynchrones et de découpage sont à confirmer après discovery et tranchés en ADR.

## 4. Architecture mobile hors ligne
Prévoir une couche locale et un moteur de synchronisation. La spécification devra définir :
- Données téléchargeables et périmètre autorisé par utilisateur et par organisation (cloisonnement).
- Opérations possibles hors ligne par type de donnée.
- Identifiants locaux uniques et idempotency keys.
- File d'attente durable des modifications.
- État de chaque élément : local, en attente, synchronisé, en conflit, rejeté.
- Règles de retry avec backoff, reprise après redémarrage et observabilité.
- Résolution des conflits par type de donnée ; aucune règle générique « last write wins » ne doit être adoptée sans validation.
- Fichiers/photos volumineux : quotas, reprise partielle, compression, stratégie d'éviction.
- Versionnement des schémas et compatibilité d'une application mobile ancienne.
- Authentification, expiration de session, appareil perdu, effacement local et à distance ; chiffrement des données locales → OPEN-028.
- Gestion de la suppression et des conflits avec les données supprimées côté serveur.
- Quota de stockage local par appareil et stratégie d'éviction (données les moins récentes / les moins prioritaires).
- Confidentialité des données locales : chiffrement au repos, effacement à distance, journal d'accès local.

## 5. Domaines métier candidats
- Identity & Access : identité, sessions, rôles, permissions, périmètres. Hiérarchie organisationnelle à trancher : Client → Organisation → Coopérative → Campagne → Zone ; Section à clarifier : lieu ou zone ?
- Producer & Farm : producteurs, ménages, exploitations, parcelles, référentiels (distinction Exploitation / Parcelle ). Identifiants et dédoublonnage.
- Collection : opérations et mesures de collecte ; workflow détaillé à définir , unités et conversions .
- Traceability : lots, événements, liens entre lots et historique, selon la cascade définie au glossaire (bord-champ → évacuation → réception coopérative → transfert exportateur) ; règles de regroupement et de scission à trancher ; infalsifiabilité à trancher (blockchain ou autre — décision non prise).
- Sustainability : questionnaires, pratiques, contrôles ou certifications selon les référentiels approuvés.
- Administration & Reporting : gestion des référentiels, qualité, exports, rapports et audit.
- Transverse : données personnelles et rétention , audit.

## 6. Données et stockage
Ne pas choisir le moteur de base de données avant d'avoir défini les relations, les requêtes, l'intégrité, les besoins géospatiaux, les transactions, les volumes et les contraintes d'exploitation. Évaluer au minimum :
- base relationnelle pour les relations et contraintes transactionnelles (candidat principal) ;
- base documentaire si la flexibilité de schéma répond à des cas démontrés ;
- stockage de fichiers pour photos et pièces jointes (candidat : stockage objet) ;
- index géospatiaux si les parcours géographiques les nécessitent (parcelles, sections, zones,regions,pays) ;
- chiffrement au repos et en transit, sauvegarde, restauration et politique de rétention ;
- versionnement du schéma serveur : migrations, compatibilité descendante, stratégie de déploiement ;
- stratégie d'infalsifiabilité de la traçabilité : blockchain ou autre — décision non prise, à trancher .

Ne pas adopter plusieurs bases simplement pour suivre une mode. La cohérence opérationnelle prime.

## 7. API et contrats
- OpenAPI comme contrat documenté si l'API REST est retenue.
- Validation d'entrée centralisée et erreurs stables/documentées.
- Pagination, filtres et tri explicites pour les collections.
- Idempotence pour les commandes pouvant être rejouées, particulièrement la synchronisation.
- Corrélation de requête et audit sans exposer de données sensibles.
- Politique de compatibilité pour les versions web/mobile déployées séparément.
- Versionnement d'API et contrats de compatibilité testés (section 10).

## 8. Architecture frontend
Web : structure par domaine fonctionnel, composants réutilisables, séparation UI / cas d'usage / accès API, états chargement-erreur-vide, permissions côté serveur toujours autoritatives.

Mobile : séparation présentation / domaine / données, persistance locale durable, couche réseau remplaçable, gestion explicite des états de synchronisation et télémétrie respectueuse de la confidentialité.

Le choix exact des frameworks, bibliothèques et gestionnaires d'état reste à documenter dans un ADR après validation des compétences et contraintes.

## 9. Sécurité et exploitation
- Authentification et autorisation fondées sur un modèle de menace.

- Isolation des données entre organisations/périmètres : principe confirmé ; modèle à trancher (schéma par tenant, base par tenant, colonne tenant_id) . Tests d'accès croisés obligatoires.
- Données personnelles : minimisation, finalités, durées de conservation, droits des personnes.
- Gestion des secrets, chiffrement en transit et au repos, chiffrement local mobile selon les risques .
- Audit des actions sensibles .
- CI avec tests, lint, analyse de dépendances et scan de secrets.
- Environnements séparés, migrations contrôlées, sauvegardes et exercices de restauration (testés, pas seulement documentés).
- Logs, métriques, traces et alertes sans données sensibles.
- SLO, RPO, RTO et stratégie de déploiement à fixer avec l'exploitation .
- Gestion des incidents : qui est alerté, procédure, post-mortem, communication — critique pour une équipe réduite.
- Soutenabilité budgétaire et calendaire : le plan doit rester réalisable par le porteur + IA .

## 10. Stratégie de tests
- Unitaires : règles métier et transitions.
- Intégration : base de données, transactions, stockage, synchronisation.
- Contrats : compatibilité API et clients.
- E2E : parcours critiques web et mobile.
- Offline : coupure réseau, redémarrage, retries, doublons, conflits, appareils à espace faible.
- Sécurité : autorisations,  isolation inter-organisations (accès croisés), validation, upload de fichiers, sessions.
- Performance : scénarios et volumes issus des objectifs validés, pas seulement le nombre de producteurs.
- Reprise : restauration de sauvegarde et réconciliation des données.
- Données personnelles : vérification de la minimisation et de la rétention.

## 11. Décisions à prendre dans des ADR
1. Stack backend et organisation du monolithe modulaire.
2. Base de données et stratégie géospatiale.
3. Modèle d'identité, rôles, permissions et périmètres d'organisation.
4. Stockage local mobile et stratégie de synchronisation (idempotence, conflits).
5. Hébergement, régions, stockage de fichiers et sauvegardes.
6. API, versionnement et compatibilité mobile.
7. Observabilité et stratégie de livraison.
8. Traçabilité et infalsifiabilité (blockchain ou autre) 

Chaque ADR suit le gabarit ADR (statut, décideurs, exigences liées, options, matrice de comparaison, décision, conséquences, validation, réexamen).

## 12. Critères de validation de l'architecture
L'architecture ne sera considérée comme prête que lorsque tous les critères suivants sont satisfaits :

1. Scénarios offline prioritaires documentés et testables .
2. Modèles de données (entités, relations, contraintes) documentés .
3. Volumes cibles mesurés et scénarisés (producteurs, parcelles, événements, fichiers, utilisateurs simultanés).
4. Frontières de confiance explicites (client, API, serveur, stockage, mobile) .
5. Exigences de confidentialité (données personnelles, rétention, chiffrement) documentées.
6. Plan de reprise testé (sauvegarde, restauration, réconciliation) .
7. Isolation multi-organisation prouvée par des tests d'accès croisés.
8. ADR de la Phase 2 approuvés : sans cela, les critères 1 à 7 pourraient être « satisfaits » sans que les décisions techniques soient prises.
9. Hiérarchie organisationnelle tranchée  et Section clarifiée .
10. Soutenabilité confirmée : le plan reste réalisable par le porteur + IA dans le budget/calendrier.

## 13. Gate de passage (rappel)
Ne pas figer les choix techniques ni commencer l'implémentation métier à grande échelle avant d'avoir validé les exigences qui conditionnent ces choix (Phase 1) et approuvé les ADR de la Phase 2. Les inconnues non bloquantes peuvent rester ouvertes, mais doivent avoir un responsable et une date de réexamen.