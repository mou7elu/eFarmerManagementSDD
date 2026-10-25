# Contribuer

1. Choisir un Requirement et une spec approuvés.
2. Vérifier les dépendances et critères d'acceptation.
3. Créer une branche courte avec un nom explicite, par exemple `feat/REQ-TRA-001-lot-history`.
4. Implémenter une petite tranche verticale.
5. Ajouter tests unitaires, d'intégration ou de parcours selon le risque.
6. Exécuter formatage, lint, tests et contrôles de sécurité disponibles.
7. Ouvrir une PR décrivant les IDs SDD couverts, les décisions prises, les tests exécutés et les limites connues.
8. Mettre à jour les documents dans la même PR si le comportement change.

Ne pas intégrer une règle métier supposée sans validation. Les migrations de données et changements de contrat API doivent avoir une stratégie de compatibilité et de retour arrière documentée.
