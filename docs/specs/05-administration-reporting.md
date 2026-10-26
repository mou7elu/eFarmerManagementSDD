# Spec 05 — Administration, gestion et reporting

- Statut : Brouillon (à valider en Phase 1)
- Version : 0.1
- Domaine : Administration & Reporting
- Phase roadmap : Phase 1 → Phase 5
- Dépendances : OPEN-018, OPEN-004, OPEN-005
- ADR liés : adr/0004 (isolation), adr/0007 (observabilité)

## 1. Objectif
Permettre aux administrateurs de gérer les référentiels, les accès, la qualité
des données, les exports et les rapports, avec audit et cloisonnement.

## 2. Périmètre
**Inclus** : gestion des référentiels, gestion des accès, qualité des données,
exports, rapports, audit, notifications (à préciser).
**Exclus** : collecte (spec 02), traçabilité (spec 03), durabilité (spec 04),
identité/permissions détaillées (spec 06).

## 3. Profils concernés
- Administrateurs (gestion, reporting)
- Super-administrateurs (à préciser)

## 4. Récits utilisateurs (à valider)
- En tant qu'**administrateur**, je veux gérer les référentiels (filières, zones,
  unités), afin de maintenir la cohérence.
- En tant qu'**administrateur**, je veux consulter des tableaux de bord et exports,
  afin de piloter l'activité.
- En tant qu'**administrateur**, je veux auditer les actions sensibles, afin de
  garantir la conformité.

## 5. Règles métier (à valider)
- Référentiels gérés : filières, zones, unités, langues → OPEN-001, OPEN-002, OPEN-019.
- Tableaux de bord, rapports, exports requis au MVP → OPEN-018.
- Qualité des données : doublons, complétude, cohérence → OPEN-011, OPEN-018.
- Notifications : à préciser (OPEN-018).

## 6. Données manipulées
Entités candidates : Référentiel (Filière, Zone, Unité, Langue), Rapport, Export,
AuditLog, Notification.
Voir glossaire v0.2 et `modele-donnees.md` (à créer).

## 7. Parcours hors ligne et synchronisation
- La plupart des fonctions d'administration sont **en ligne** (à préciser).
- Certains exports peuvent être préparés hors ligne (à trancher).
- Conflits : résolution par type de donnée.

## 8. Permissions et cloisonnement
- Un administrateur ne voit que son organisation (adr/0004).
- Les exports respectent le cloisonnement.
- Tests d'accès croisés obligatoires.

## 9. Traçabilité et audit
- Journalisation de toutes les actions sensibles (principe 4).
- Audit consultable par les administrateurs autorisés.
- Ne pas exposer de données personnelles dans les logs (OPEN-009).

## 10. Cas limites et erreurs
- Export volumineux → pagination / asynchrone (à préciser).
- Référentiel modifié pendant une saisie → gestion de version (à trancher).
- Accès non autorisé → refus côté serveur.

## 11. Exigences non fonctionnelles (renvois)
- Volumes de rapports/exports : OPEN-008.
- Performance des exports : mesurée.
- Observabilité : adr/0007.

## 12. Non-objectifs
- Pas de collecte (spec 02).
- Pas de traçabilité (spec 03).
- Pas de durabilité (spec 04).

## 13. Questions ouvertes
- OPEN-018 (rapports, exports, notifications), OPEN-001/002/019 (référentiels),
  OPEN-005 (hiérarchie), OPEN-009 (données personnelles).

## 14. Dépendances ADR
- adr/0004 (isolation), adr/0007 (observabilité).