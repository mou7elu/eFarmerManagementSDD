# Instructions pour assistants de développement

## Règles non négociables
1. Lire `README.md` et les documents applicables avant de proposer ou modifier du code.
2. Ne pas inventer de règles métier, statuts, rôles, champs obligatoires, seuils, volumes ou contraintes légales. Si une décision manque, l'enregistrer dans `docs/product/open-questions.md` et demander confirmation.
3. Chaque changement fonctionnel doit référencer un Requirement ID et une Specification ID.
4. Ne pas implémenter une fonctionnalité dont les critères d'acceptation sont ambigus ou non validés.
5. Mettre à jour spec/design/tasks et tests dans le même changement si le comportement ou la conception change.
6. Privilégier une tranche verticale testable et petite plutôt qu'un lot backend/frontend/mobile indépendant et massif.
7. Ne jamais ajouter de secrets, clés, données personnelles réelles ou identifiants dans le dépôt.
8. Toute opération hors ligne doit préciser ce qui est stocké localement, la durée, le chiffrement, la synchronisation et le comportement en conflit avant implémentation.
9. Les permissions sont appliquées côté serveur, pas uniquement masquées dans l'interface.
10. Ne pas déclarer un test passé sans l'avoir exécuté. Indiquer clairement les vérifications non exécutées.

## Définition de prêt (Ready)
- Besoin et utilisateur cible compris.
- Scénarios principaux et erreurs décrits.
- Critères d'acceptation testables et validés.
- Données sensibles et autorisations identifiées.
- Dépendances et décisions bloquantes résolues.

## Définition de terminé (Done)
- Implémentation conforme à la spec approuvée.
- Tests pertinents ajoutés et exécutés.
- Revue de code effectuée.
- Contrôles qualité/CI passés.
- Documentation et traçabilité mises à jour.
- Aucun secret ou donnée réelle ajoutée.
