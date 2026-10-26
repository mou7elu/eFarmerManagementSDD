# ADR-0006 : Contrats API, versionnement et compatibilité mobile

- Statut : Proposé
- Date : 2026-10-26
- Remplace : —
- Remplacé par : —
- Décideur(s) : Porteur du projet (à confirmer)
- Consultés : (à définir)
- Informés : (à définir)
- Exigences liées : OPEN-020, OPEN-027
- Phase de la roadmap : Phase 2
- Date / condition de réexamen : à définir

## Contexte
Définir des contrats API explicites (OpenAPI si REST), validation centralisée,
erreurs stables, pagination/filtres/tri, idempotence (synchronisation),
corrélation et audit, politique de compatibilité pour les versions web/mobile
déployées séparément.

## Options considérées
1. REST + OpenAPI versionné (ex. `/v1`).
2. GraphQL + schéma versionné.
3. gRPC (si pertinent pour le mobile).
4. (Autre option pertinente)

### Matrice de comparaison
| Critère | Poids | Option 1 | Option 2 | Option 3 |
|---|---|---|---|---|
| Compatibilité mobile | | | | |
| Outillage (porteur + IA) | | | | |
| Idempotence / sync | | | | |
| Observabilité | | | | |
| Soutenabilité | | | | |

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
- Critères : —
- Preuve / POC / mesure : —
- Validé par : —
- Date de validation : —

## Suivi
- Tâches de mise en œuvre : —
- Risques résiduels : —
- Date / condition de réexamen : —