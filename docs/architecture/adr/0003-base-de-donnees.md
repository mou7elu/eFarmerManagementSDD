# ADR-0003 : Base de données et stratégie géospatiale

- Statut : Proposé
- Date : 2026-10-26
- Remplace : —
- Remplacé par : —
- Décideur(s) : Porteur du projet (à confirmer)
- Consultés : (à définir)
- Informés : (à définir)
- Exigences liées : OPEN-008
- Phase de la roadmap : Phase 2
- Date / condition de réexamen : à définir

## Contexte
Ne pas choisir le moteur avant d'avoir défini les relations, requêtes, intégrité,
besoins géospatiaux, transactions, volumes et contraintes d'exploitation. Évaluer :
relationnel, documentaire (si cas démontrés), stockage de fichiers, index
géospatiaux, chiffrement, sauvegarde, rétention. Éviter la multiplication des
bases sans justification mesurée.

## Options considérées
1. Relationnel + extension géospatiale (ex. PostgreSQL/PostGIS — candidat).
2. Documentaire (ex. MongoDB — candidat).
3. Relationnel + base géospatiale séparée.
4. (Autre option pertinente)

### Matrice de comparaison
| Critère | Poids | Option 1 | Option 2 | Option 3 |
|---|---|---|---|---|
| Transactions / intégrité | | | | |
| Géospatial | | | | |
| Charge (volumes OPEN-008) | | | | |
| Exploitation (équipe réduite) | | | | |
| Migration / évolution de schéma | | | | |

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
- Critères : volumes OPEN-008, requêtes types, tests de charge.
- Preuve / POC / mesure : —
- Validé par : —
- Date de validation : —

## Suivi
- Tâches de mise en œuvre : —
- Risques résiduels : décision structurante.
- Date / condition de réexamen : —