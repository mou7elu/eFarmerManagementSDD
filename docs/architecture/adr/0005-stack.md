# ADR-0005 : Stack backend et organisation du monolithe modulaire

- Statut : Proposé
- Date : 2026-10-26
- Remplace : —
- Remplacé par : —
- Décideur(s) : Porteur du projet (à confirmer)
- Consultés : (à définir)
- Informés : (à définir)
- Exigences liées : HYP-007 (frontend React = hypothèse)
- Phase de la roadmap : Phase 2
- Date / condition de réexamen : à définir

## Contexte
Commencer par un monolithe modulaire tant que les contraintes n'imposent pas des
services séparés. Séparer domaine, cas d'usage, accès aux données et transport
HTTP. Le choix exact (langage, framework, gestionnaire d'état frontend) reste à
documenter après validation des compétences et contraintes. « React » est une
hypothèse (HYP-007), pas une décision.

## Options considérées
1. Stack A (ex. TypeScript/NestJS + React) — avantages/inconvénients.
2. Stack B (ex. Python/Django + Vue) — idem.
3. Stack C (ex. Dart/Flutter + backend Dart) — idem.
4. (Autre option pertinente)

### Matrice de comparaison
| Critère | Poids | Option 1 | Option 2 | Option 3 |
|---|---|---|---|---|
| Compétences disponibles (porteur + IA) | | | | |
| Écosystème / support | | | | |
| Soutenabilité (équipe réduite) | | | | |
| Performance | | | | |
| Outillage offline | | | | |

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