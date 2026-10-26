# Spec 04 — Durabilité

- Statut : Brouillon (à valider en Phase 1)
- Version : 0.1
- Domaine : Sustainability
- Phase roadmap : Phase 1 → Phase 5 (extension)
- Dépendances : OPEN-016, glossaire v0.2 (Durabilité)
- ADR liés : adr/0004 (isolation)

## 1. Objectif
Permettre d'enregistrer et de suivre les pratiques et critères de durabilité
selon les référentiels approuvés, sans inventer de critères non validés.

## 2. Périmètre
**Inclus** : questionnaires, pratiques, contrôles, certifications (selon référentiels).
**Exclus** : collecte (spec 02), traçabilité (spec 03), reporting (spec 05).

## 3. Profils concernés
- Agents de terrain (saisie des pratiques)
- Administrateurs (contrôle, certification)
- Auditeurs externes (consultation, à préciser)

## 4. Récits utilisateurs (à valider)
- En tant qu'**agent de terrain**, je veux enregistrer les pratiques durables
  d'une parcelle, afin d'alimenter la certification.
- En tant qu'**administrateur**, je veux vérifier les critères et valider une
  certification, afin de garantir la conformité.
- En tant qu'**auditeur**, je veux consulter les preuves, afin de vérifier.

## 5. Règles métier (à valider)
- **Référentiels officiels requis** → OPEN-016 (ne pas inventer de critères).
- Critères de durabilité par filière → OPEN-016.
- Processus de certification (étapes, preuves, validations) → OPEN-016.
- Double contrôle / signature → OPEN-017.

## 6. Données manipulées
Entités candidates : Questionnaire, Pratique, Contrôle, Certification, Preuve
(photo/document), Parcelle (réf. spec 01).
Voir glossaire v0.2 et `modele-donnees.md` (à créer).

## 7. Parcours hors ligne et synchronisation
- Saisie des pratiques hors ligne possible (OPEN-006).
- Photos/preuves : quota, compression (adr/0002).
- Conflits : résolution par type de donnée.

## 8. Permissions et cloisonnement
- Un agent ne voit que ses parcelles (adr/0004).
- Un auditeur externe a un accès en lecture limité (à préciser).
- Tests d'accès croisés.

## 9. Traçabilité et audit
- Journalisation des validations et certifications (principe 4).
- Preuves conservées et liées aux parcelles.

## 10. Cas limites et erreurs
- Référentiel non approuvé → rejet.
- Preuve manquante → certification bloquée.
- Conflit de validation → état « en conflit ».

## 11. Exigences non fonctionnelles (renvois)
- Volumes de preuves : OPEN-008.
- Conservation des preuves : OPEN-026.
- Performance : mesurée.

## 12. Non-objectifs
- Pas de collecte (spec 02).
- Pas de traçabilité (spec 03).

## 13. Questions ouvertes
- OPEN-016 (référentiels, critères), OPEN-017 (validations, signatures),
  OPEN-009 (données personnelles), OPEN-026 (conservation).

## 14. Dépendances ADR
- adr/0004 (isolation). Référentiels à valider avant implémentation.