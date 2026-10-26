# Registre des décisions — eFarmerManagement

- Version : 0.2
- Date : 2026-10-26
- Règle : un ADR ne passe à « Accepté » qu'après comparaison documentée des options,
  prise en compte des exigences liées, et validation par les décideurs concernés
  (porteur + validateurs métier nommés en Phase 0).
- Numérotation alignée sur le Plan d'architecture cible v0.2 (adr/0001 → adr/0008).

## 1. Registre des ADR

| ID | Sujet | Statut | Phase | Responsable | Dépend de | Exigences liées | Document de décision | Réexamen |
|---|---|---|---|---|---|---|---|---|
| ADR-0001 | Hébergement, régions, stockage de fichiers et sauvegardes | Non décidé | Phase 2 | Porteur (à confirmer) | OPEN-023, OPEN-025 | OPEN-023, OPEN-025 | `adr/0001-hebergement.md` | À définir |
| ADR-0002 | Stockage mobile hors ligne et synchronisation (idempotence, conflits) | Non décidé | Phase 2 | Porteur (à confirmer) | OPEN-006, OPEN-007 | OPEN-006, OPEN-007 | `adr/0002-idempotence-sync.md` | À définir |
| ADR-0003 | Base de données et stratégie géospatiale | Non décidé | Phase 2 | Porteur (à confirmer) | OPEN-008 | OPEN-008 | `adr/0003-base-de-donnees.md` | À définir |
| ADR-0004 | Identité, rôles, permissions et isolation multi-organisation | Non décidé | Phase 2 | Porteur (à confirmer) | **OPEN-005**, OPEN-031 | OPEN-005, OPEN-031 | `adr/0004-isolation-multi-org.md` | À définir |
| ADR-0005 | Stack backend et organisation du monolithe modulaire | Non décidé | Phase 2 | Porteur (à confirmer) | — | HYP-007 (frontend) | `adr/0005-stack.md` | À définir |
| ADR-0006 | Contrats API, versionnement et compatibilité mobile | Non décidé | Phase 2 | Porteur (à confirmer) | OPEN-020, OPEN-027 | OPEN-020, OPEN-027 | `adr/0006-api-versionnement.md` | À définir |
| ADR-0007 | Observabilité, livraison et gestion des incidents | Non décidé | Phase 2 | Porteur (à confirmer) | OPEN-025, OPEN-029 | OPEN-025, OPEN-029 | `adr/0007-observabilite-livraison.md` | À définir |
| ADR-0008 | Traçabilité et infalsifiabilité (blockchain ou autre) | Non décidé | Phase 2 | Porteur (à confirmer) | OPEN-013, OPEN-031 | OPEN-013, OPEN-031 | `adr/0008-tracabilite-infalsifiabilite.md` | À définir |

## 2. Décisions de cadrage confirmées — 2026-10-25

- Pays de lancement : Côte d'Ivoire uniquement.
- Plusieurs filières à étudier dès le départ (liste exacte → OPEN-001).
- Livraison : MVP puis extensions (périmètre MVP → OPEN-004 / `scope.md`).
- **Profils de découverte : collecteurs, agents de terrain, administrateurs. Le producteur est une entité métier, pas un profil utilisateur au lancement** (cf. vision v0.2, Q-004, OPEN-010).
- Plateformes : web + mobile Flutter (React = HYP-007, non décidé).
- Mode hors ligne : saisir, consulter et modifier les données déjà téléchargées (périmètre → OPEN-006 ; conflits → OPEN-007).
- Multi-organisation avec cloisonnement des données (modèle → OPEN-005 / `adr/0004`).
- Ambition de volumétrie : ~800 000 producteurs ou davantage (volumes détaillés → OPEN-008).
- Hébergement à comparer ; aucun fournisseur ni stack n'est approuvé par cette décision.
- Le MVP doit être priorisé après étude de l'ensemble des modules ; tous les modules ne sont pas automatiquement dans le MVP.

## 3. Dépendances entre décisions

- `adr/0004` (identité/isolation) **dépend de** OPEN-005 (hiérarchie) et OPEN-031 (Section) — à trancher en Phase 0.
- `adr/0002` (sync) **dépend de** OPEN-007 (règles de conflit) — à trancher en Phase 0/1.
- `adr/0003` (BDD) **dépend de** OPEN-008 (volumes) — à chiffrer en Phase 0.
- `adr/0008` (traçabilité) **dépend de** OPEN-013 (règles de lot) et OPEN-031 (Section) — Phase 1.

## 4. Règle de passage à « Accepté »

Un ADR ne passe à « Accepté » qu'après :
1. comparaison documentée des options (matrice de comparaison du gabarit ADR) ;
2. prise en compte des exigences liées (`REQ-...` ou `OPEN-...`) ;
3. validation par les décideurs concernés (porteur + validateurs métier nommés en Phase 0) ;
4. date de validation renseignée et condition de réexamen définie.