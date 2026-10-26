# ADR-0008 : Traçabilité et infalsifiabilité (blockchain ou autre)

- Statut : Proposé
- Date : 2026-10-26
- Remplace : —
- Remplacé par : —
- Décideur(s) : Porteur du projet (à confirmer)
- Consultés : (à définir)
- Informés : (à définir)
- Exigences liées : OPEN-013, OPEN-031
- Phase de la roadmap : Phase 2
- Date / condition de réexamen : à définir

## Contexte
La vision mentionne une « traçabilité sous forme de blockchain ». La cascade de
lots est définie au glossaire v0.2 (bord-champ → évacuation → réception
coopérative → transfert exportateur). Restent à trancher : les règles de
regroupement/scission (OPEN-013), la définition de « Section » (OPEN-031), et le
**mécanisme d'infalsifiabilité** (blockchain ou autre). La décision doit tenir
compte du coût, de la complexité d'exploitation et de la soutenabilité par une
équipe réduite.

## Options considérées
1. Blockchain (publique ou permissionnée) — avantages/inconvénients.
2. Journal d'audit append-only signé (hash chain) sans blockchain.
3. Journalisation classique + contrôles d'intégrité.
4. (Autre option pertinente)

### Matrice de comparaison
| Critère | Poids | Option 1 | Option 2 | Option 3 |
|---|---|---|---|---|
| Infalsifiabilité | | | | |
| Coût / complexité | | | | |
| Exploitation (équipe réduite) | | | | |
| Interopérabilité exportateurs | | | | |
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
- Critères : cascade de lots validée (OPEN-013) ; Section clarifiée (OPEN-031) ;
  POC d'infalsifiabilité testé.
- Preuve / POC / mesure : —
- Validé par : —
- Date de validation : —

## Suivi
- Tâches de mise en œuvre : —
- Risques résiduels : décision différenciante du produit.
- Date / condition de réexamen : —