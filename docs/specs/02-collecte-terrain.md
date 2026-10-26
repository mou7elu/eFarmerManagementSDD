# Spec 02 — Collecte des données sur le terrain

- Statut : Brouillon (à valider en Phase 1)
- Version : 0.1
- Domaine : Collection
- Phase roadmap : Phase 1 → Phase 4 (candidat MVP vertical)
- Dépendances : glossaire v0.2 (Collecte, Pré-collecte, Lot de bord-champ), OPEN-014, OPEN-015
- ADR liés : adr/0002 (sync), adr/0004 (isolation)

## 1. Objectif
Permettre aux agents de terrain et collecteurs d'enregistrer les opérations de
collecte (mesures, unités, justificatifs, statuts) sur le terrain, y compris
hors ligne, avec idempotence et résolution de conflits.

## 2. Périmètre
**Inclus** : pré-collecte au bord-champ, mesures, unités, conversions, justificatifs,
photos, statuts de collecte.
**Exclus** : évacuation, réception, transfert (spec 03) ; durabilité (spec 04).

## 3. Profils concernés
- Agents de terrain (saisie bord-champ)
- Collecteurs (saisie en coopérative)
- Administrateurs (consultation, correction)

## 4. Récits utilisateurs (à valider)
- En tant qu'**agent de terrain**, je veux enregistrer une pré-collecte au bord
  du champ (poids, unité, photo, GPS), afin de créer un lot de bord-champ.
  - Critères : lot de bord-champ créé ; idempotency key ; état offline géré.
- En tant que **collecteur**, je veux corriger une mesure erronée avec justification,
  afin de maintenir la cohérence.
  - Critères : correction tracée (audit) ; tolérances définies (OPEN-015).
- En tant qu'**administrateur**, je veux consulter les collectes et leurs statuts,
  afin de contrôler la qualité.

## 5. Règles métier (à valider)
- Une **collecte** produit un **lot de bord-champ** (glossaire v0.2).
- Unités et conversions autorisées → OPEN-015.
- Tolérances et règles de correction → OPEN-015.
- Statuts de collecte (brouillon, validée, rejetée…) → OPEN-014.
- Justificatifs obligatoires selon la filière → OPEN-014.

## 6. Données manipulées
Entités candidates : Collecte, Lot de bord-champ, Mesure, Unité, Justificatif
(photo/document), Parcelle (réf. spec 01), Producteur (réf. spec 01).
Voir glossaire v0.2 et `modele-donnees.md` (à créer).

## 7. Parcours hors ligne et synchronisation
- Saisie complète hors ligne (OPEN-006).
- File d'attente durable ; retry/backoff ; reprise après redémarrage (adr/0002).
- Idempotency keys pour éviter les doublons de collecte.
- Photos volumineuses : quota, compression, reprise partielle (adr/0002).
- Conflits : résolution par type de donnée (mesure vs justificatif).

## 8. Permissions et cloisonnement
- Un agent ne voit que les producteurs/parcelles de son périmètre (adr/0004).
- Un collecteur ne voit que sa coopérative.
- Validation côté serveur des permissions, même pour les données offline.

## 9. Traçabilité et audit
- Chaque collecte et correction est journalisée (principe 4).
- Les événements offline sont corrélés aux événements serveur.

## 10. Cas limites et erreurs
- Double saisie de la même collecte → détection par idempotency key.
- Photo non synchronisée → état « en attente ».
- Conflit mesure vs correction → résolution manuelle.
- Appareil plein → éviction / alerte (adr/0002).

## 11. Exigences non fonctionnelles (renvois)
- Volumes d'événements de collecte : OPEN-008.
- Performance offline : mesurée.
- RPO/RTO : OPEN-025.

## 12. Non-objectifs
- Pas d'évacuation/réception/transfert (spec 03).
- Pas de durabilité (spec 04).

## 13. Questions ouvertes
- OPEN-014 (workflow, mesures, unités, statuts), OPEN-015 (conversions, tolérances),
  OPEN-006 (opérations offline), OPEN-007 (conflits), OPEN-009 (photos/GPS).

## 14. Dépendances ADR
- adr/0002 (sync), adr/0004 (isolation). Candidat MVP vertical (Phase 4).