# Roadmap de découverte et de livraison — eFarmerManagement

Statut : provisoire, fondé sur le cadrage du 2026-10-25. Les phases sont ordonnées par dépendances et non par durée.

## Phase 0 — Product Discovery (en cours)
- [x] Confirmer la zone initiale : Côte d’Ivoire.
- [x] Confirmer la couverture de plusieurs filières dès le départ.
- [x] Confirmer une stratégie MVP puis extensions.
- [x] Identifier les quatre profils de départ : producteurs, collecteurs, agents de terrain, administrateurs.
- [x] Confirmer web + Flutter mobile.
- [x] Confirmer saisie, consultation et modification de données déjà téléchargées hors ligne.
- [x] Confirmer plusieurs organisations avec cloisonnement des données.
- [x] Enregistrer l’ambition de volumétrie : environ 800 000 producteurs ou davantage.
- [ ] Identifier le sponsor, les décideurs métier et les utilisateurs à interviewer.
- [ ] Lister les filières, zones, langues et unités du lancement.
- [ ] Cartographier les processus réels de chaque domaine.
- [ ] Définir la hiérarchie client/organisation/coopérative/campagne/zone.
- [ ] Définir les opérations autorisées hors ligne et les règles de conflit.
- [ ] Définir les données personnelles, finalités et durées de conservation.
- [ ] Prioriser le MVP après comparaison de tous les domaines.
- [ ] Définir les volumes détaillés, indicateurs de succès et critères de charge.

## Phase 1 — Requirements
- [ ] Transformer les besoins validés en exigences identifiées et traçables.
- [ ] Définir la matrice de rôles et autorisations, y compris les périmètres organisationnels.
- [ ] Définir les scénarios hors ligne et les critères de synchronisation.
- [ ] Définir les exigences non fonctionnelles mesurables.
- [ ] Faire valider les requirements par les responsables métier.

## Phase 2 — Architecture et preuves de faisabilité
- [ ] Comparer les options d’hébergement sans présumer du fournisseur.
- [ ] Comparer les options de base de données selon relations, transactions, géospatial, charge et exploitation.
- [ ] Prototyper stockage local, synchronisation, idempotence et conflits.
- [ ] Prototyper le cloisonnement multi-organisation et tester les accès croisés.
- [ ] Construire un modèle de charge pour producteurs, parcelles, événements, fichiers et utilisateurs simultanés.
- [ ] Documenter les décisions approuvées dans des ADR.

## Phase 3 — Fondations produit
- [ ] Dépôt, conventions, CI et contrôle de qualité.
- [ ] Gestion des secrets, environnements et dépendances.
- [ ] Authentification, autorisation et isolation multi-organisation selon les règles validées.
- [ ] Contrats API, stratégie de versionnement et migrations.
- [ ] Observabilité, sauvegardes et procédure de restauration.
- [ ] Squelette web/mobile et persistance locale.

## Phase 4 — MVP vertical
- [ ] Choisir le parcours MVP sur la base des résultats de Discovery.
- [ ] Écrire requirement/spec/design/tasks pour ce parcours.
- [ ] Livrer le parcours de bout en bout avec tests automatisés.
- [ ] Tester les scénarios en ligne, hors ligne, de reprise et de conflits.
- [ ] Faire valider le parcours par des utilisateurs représentatifs.
- [ ] Mesurer les résultats par rapport aux critères d’acceptation.

## Phase 5 — Extension progressive
- [ ] Ajouter les domaines et filières priorisés.
- [ ] Tester la charge, la sécurité, la restauration et la qualité des données.
- [ ] Préparer formation, support et exploitation.

## Gate de passage
Ne pas figer les choix techniques ni commencer l’implémentation métier à grande échelle avant d’avoir validé les exigences qui conditionnent ces choix. Les inconnues non bloquantes peuvent rester ouvertes, mais doivent avoir un responsable et une date de réexamen.
