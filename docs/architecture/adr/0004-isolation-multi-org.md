# ADR-0004 : Identité, rôles, permissions et isolation multi-organisation

- Statut : Proposé
- Date : 2026-10-26
- Remplace : —
- Remplacé par : —
- Décideur(s) : Porteur du projet (à confirmer)
- Consultés : (à définir)
- Informés : (à définir)
- Exigences liées : OPEN-005, OPEN-031, OPEN-004
- Phase de la roadmap : Phase 2
- Date / condition de réexamen : à définir

## Contexte
Le cloisonnement multi-organisation est **confirmé**. Ce qui reste à trancher :
le **modèle** (schéma par tenant, base par tenant, colonne `tenant_id`), la
**hiérarchie** (Client → Organisation → Coopérative → Campagne → Zone) et la
définition de « Section » (lieu ou zone). Les permissions doivent être vérifiées
côté serveur, y compris pour les données synchronisées.

## Options considérées
1. Colonne `tenant_id` + Row-Level Security.
2. Schéma par tenant.
3. Base par tenant.
4. (Autre option pertinente)

### Matrice de comparaison
| Critère | Poids | Option 1 | Option 2 | Option 3 |
|---|---|---|---|---|
| Isolation (sécurité) | | | | |
| Complexité d'exploitation | | | | |
| Coût par tenant | | | | |
| Tests d'accès croisés | | | | |
| Soutenabilité (équipe réduite) | | | | |

## Décision
À compléter après revue. Ne pas confondre une option étudiée avec une décision prise.
**Option retenue :** —
**Options rejetées et pourquoi :** —

## Conséquences
- Positives :
- Négatives / compromis :
- Sécurité et confidentialité :
- Exploitation et coûts :
- Migration / retour arrière :

## Validation
- Critères : tests d'accès croisés obligatoires ; hiérarchie OPEN-005 tranchée ;
  Section OPEN-031 clarifiée.
- Preuve / POC / mesure : —
- Validé par : —
- Date de validation : —

## Suivi
- Tâches de mise en œuvre : —
- Risques résiduels : risque majeur n°2 (cf. registre des risques).
- Date / condition de réexamen : —