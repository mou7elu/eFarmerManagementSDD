# Spec 01 — Gestion des producteurs, ménages, exploitations et parcelles

- Statut : Brouillon (à valider en Phase 1)
- Version : 0.1
- Domaine : Producer & Farm
- Phase roadmap : Phase 1 (Requirements) → Phase 4 (MVP vertical, si priorisé)
- Dépendances : glossaire v0.2 (Producteur, Ménage, Exploitation, Parcelle), OPEN-011, OPEN-012
- ADR liés : adr/0004 (isolation multi-org), adr/0002 (sync)

## 1. Objectif
Permettre aux profils autorisés d'enregistrer, consulter et modifier les
producteurs, leurs ménages, leurs exploitations et leurs parcelles, y compris
hors ligne, avec un cloisonnement multi-organisation.

## 2. Périmètre
**Inclus** : création/consultation/modification de producteur, ménage,
exploitation, parcelle ; liens entre ces entités ; identifiants et dédoublonnage.
**Exclus** : collecte (spec 02), traçabilité (spec 03), durabilité (spec 04),
reporting (spec 05), permissions détaillées (spec 06).

## 3. Profils concernés
- Collecteurs (saisie)
- Agents de terrain (saisie, consultation)
- Administrateurs (gestion, consultation, exports)
- *Producteur = entité métier, pas profil utilisateur au lancement* (cf. OPEN-010).

## 4. Récits utilisateurs (à valider)
- En tant que **collecteur**, je veux créer un producteur avec ses informations
  d'identité, afin de le rattacher à une coopérative.
  - Critères d'acceptation : champs obligatoires définis (OPEN-011) ; doublons
    détectés ; identifiant local unique généré hors ligne.
- En tant qu'**agent de terrain**, je veux enregistrer le ménage et les parcelles
  d'un producteur, afin de préparer la collecte.
  - Critères : parcelle rattachée à une exploitation (pas directement au producteur) ;
    géométrie saisie ou importée (à préciser).
- En tant qu'**administrateur**, je veux consulter et corriger les données d'un
  producteur, afin d'assurer la qualité des données.
  - Critères : audit des modifications ; permissions vérifiées côté serveur.

## 5. Règles métier (à valider)
- Un producteur appartient à **une ou plusieurs** organisations/coopératives ?
  → OPEN-012.
- Un producteur peut avoir **plusieurs exploitations** ? → OPEN-012.
- Une **exploitation** regroupe **une ou plusieurs parcelles** (glossaire v0.2).
- Une **parcelle** est rattachée à **une exploitation** (glossaire v0.2).
- Un **ménage** est l'ensemble des personnes vivant sous le même toit (glossaire v0.2).

## 6. Données manipulées
Voir `docs/glossaire-metier.md` v0.2 et `docs/modele-donnees.md` (à créer).
Entités candidates : Producteur, Ménage, Exploitation, Parcelle, Organisation
(réf. OPEN-005), Coopérative, Campagne, Zone.
Identifiants : à définir (OPEN-011) ; idempotency keys pour la sync.

## 7. Parcours hors ligne et synchronisation
- Données téléchargeables : producteurs, ménages, exploitations, parcelles du
  périmètre de l'utilisateur (organisation/zone).
- Opérations autorisées hors ligne : création, consultation, modification
  (OPEN-006).
- Conflits : résolution **par type de donnée**, pas de last-write-wins générique
  (OPEN-007, adr/0002).
- États : local, en attente, synchronisé, en conflit, rejeté.
- Suppression : soft-delete + conflits avec suppressions serveur (adr/0002).

## 8. Permissions et cloisonnement
- Toute requête et toute donnée synchronisée sont **cloisonnées par organisation**
  (adr/0004, OPEN-005).
- Permissions vérifiées **côté serveur**, y compris pour les données offline.
- Tests d'accès croisés obligatoires.

## 9. Traçabilité et audit
- Journaliser les créations, modifications et suppressions sensibles (principe 4).
- Corréler les événements offline et serveur (idempotency keys).
- Ne pas exposer de données personnelles dans les logs (OPEN-009).

## 10. Cas limites et erreurs
- Doublon de producteur (même nom, même zone) → détection, proposition de fusion.
- Parcelle sans exploitation → rejet.
- Ménage vide → autorisé ? (à préciser).
- Conflit de modification concurrente → état « en conflit », résolution manuelle.
- Suppression côté serveur pendant une modification offline → à trancher (OPEN-007).

## 11. Exigences non fonctionnelles (renvois)
- Volumes : OPEN-008.
- Performance : mesurée, pas supposée (principe 6).
- Disponibilité, RPO/RTO : OPEN-025.
- Conservation des données personnelles : OPEN-009 / D-012.

## 12. Non-objectifs
- Pas de gestion des collectes (spec 02).
- Pas de traçabilité de lots (spec 03).
- Pas de certification de durabilité (spec 04).
- Pas de reporting avancé (spec 05).

## 13. Questions ouvertes
- OPEN-011 (identifiants fiables), OPEN-012 (multi-coopératives, multi-exploitations),
  OPEN-005 (hiérarchie), OPEN-009 (données personnelles), OPEN-010 (fonctions
  producteur direct).

## 14. Dépendances ADR
- adr/0002 (sync), adr/0004 (isolation). À trancher avant implémentation.