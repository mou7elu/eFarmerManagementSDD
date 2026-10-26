# Spec 03 — Traçabilité des lots

- Statut : Brouillon (à valider en Phase 1)
- Version : 0.1
- Domaine : Traceability
- Phase roadmap : Phase 1 → Phase 5 (extension)
- Dépendances : glossaire v0.2 (cascade de lots), OPEN-013, OPEN-031
- ADR liés : adr/0008 (infalsifiabilité), adr/0004 (isolation)

## 1. Objectif
Permettre de suivre les lots de la parcelle à l'exportateur, via la cascade
bord-champ → évacuation → réception coopérative → transfert exportateur, avec
événements de traçabilité et conservation de la traçabilité amont.

## 2. Périmètre
**Inclus** : création de lots, regroupements, événements de traçabilité,
historique, liens amont/aval.
**Exclus** : collecte (spec 02) ; durabilité (spec 04) ; reporting avancé (spec 05).

## 3. Profils concernés
- Agents de terrain (pré-collecte → lot de bord-champ)
- Collecteurs (évacuation, réception)
- Administrateurs (transfert, audit)

## 4. Récits utilisateurs (à valider)
- En tant qu'**agent de terrain**, je veux créer un lot de bord-champ, afin
  d'initier la traçabilité.
- En tant que **collecteur**, je veux regrouper des lots de bord-champ en lot
  d'évacuation, afin de les transporter vers la section.
- En tant qu'**administrateur**, je veux regrouper des lots de réception en lot
  de transfert exportateur, afin de préparer l'export.
- En tant qu'**auditeur**, je veux remonter d'un lot exportateur jusqu'aux parcelles,
  afin de vérifier l'origine.

## 5. Règles métier (à valider)
- Cascade : lot de bord-champ → lot d'évacuation → lot de réception coopérative
  → lot de transfert exportateur (glossaire v0.2).
- Un **regroupement** crée un nouveau lot et référence les lots d'origine.
- Un lot est **immuable dans son identité** ; ses regroupements créent de nouveaux lots.
- **Section** : lieu ou zone ? → OPEN-031.
- **Scission** de lot autorisée ? → OPEN-013.
- **Transfert direct** sans regroupement autorisé ? → OPEN-013.
- Cardinalités (N lots par regroupement) → OPEN-013.

## 6. Données manipulées
Entités candidates : Lot (4 types), Événement de traçabilité, Regroupement,
Section, Parcelle/Producteur (réf. spec 01), Collecte (réf. spec 02).
Voir glossaire v0.2 et `modele-donnees.md` (à créer).

## 7. Parcours hors ligne et synchronisation
- Création de lot et événements hors ligne possibles (OPEN-006).
- Idempotence des regroupements (adr/0002).
- Conflits : un lot modifié offline et côté serveur → résolution manuelle.
- Conservation de la traçabilité amont même en cas de conflit.

## 8. Permissions et cloisonnement
- Un lot appartient à une organisation/coopérative (adr/0004).
- Les regroupements inter-organisations sont-ils autorisés ? → OPEN-005.
- Tests d'accès croisés obligatoires.

## 9. Traçabilité et audit
- Chaque événement de traçabilité est daté, tracé, et **infalsifiable** (mécanisme
  à trancher — adr/0008).
- Journalisation des regroupements, scissions, transferts.

## 10. Cas limites et erreurs
- Regroupement de lots de sections différentes → autorisé ? (OPEN-013).
- Scission non prévue → à trancher (OPEN-013).
- Lot orphelin (sans événement) → rejet.
- Conflit de regroupement → état « en conflit ».

## 11. Exigences non fonctionnelles (renvois)
- Volumes de lots et d'événements : OPEN-008.
- Performance de remontée de chaîne : mesurée.
- Infalsifiabilité : adr/0008.

## 12. Non-objectifs
- Pas de collecte (spec 02).
- Pas de durabilité (spec 04).
- Pas de reporting (spec 05).

## 13. Questions ouvertes
- OPEN-013 (règles de lot), OPEN-031 (Section), OPEN-005 (hiérarchie),
  OPEN-006/007 (offline/conflits), décision blockchain (adr/0008).

## 14. Dépendances ADR
- adr/0008 (infalsifiabilité), adr/0004 (isolation), adr/0002 (sync).