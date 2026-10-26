# ADR-0002 : Stockage mobile hors ligne et synchronisation

- Statut : Proposé
- Date : 2026-10-26
- Remplace : —
- Remplacé par : —
- Décideur(s) : Porteur du projet (à confirmer)
- Consultés : (à définir)
- Informés : (à définir)
- Exigences liées : OPEN-006, OPEN-007
- Phase de la roadmap : Phase 2
- Date / condition de réexamen : à définir

## Contexte
Le mode hors ligne est une capacité de premier ordre. Il faut définir : données
téléchargeables par utilisateur/organisation, opérations autorisées hors ligne,
identifiants locaux et idempotency keys, file d'attente durable, états des
éléments (local, en attente, synchronisé, en conflit, rejeté), retry/backoff,
résolution des conflits **par type de donnée**, gestion des fichiers volumineux,
versionnement de schéma, auth/expiration/appareil perdu, suppression et conflits
avec les données supprimées côté serveur.

## Options considérées
1. File d'attente durable + résolution manuelle des conflits par type.
2. CRDT (résolution automatique) — avantages/inconvénients.
3. Last-write-wins (rejeté par principe, sauf validation explicite).
4. (Autre option pertinente)

### Matrice de comparaison
| Critère | Poids | Option 1 | Option 2 | Option 3 |
|---|---|---|---|---|
| Risque de perte de données | | | | |
| Complexité d'implémentation | | | | |
| Complexité UX (conflits) | | | | |
| Observabilité | | | | |
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
- Critères : scénarios offline (coupure, redémarrage, doublons, conflits, espace faible).
- Preuve / POC / mesure : —
- Validé par : —
- Date de validation : —

## Suivi
- Tâches de mise en œuvre : —
- Risques résiduels : risque majeur n°1 (cf. registre des risques).
- Date / condition de réexamen : —