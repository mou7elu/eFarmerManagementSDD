# Exigences sécurité et confidentialité — base de travail

Statut : propositions à valider par les responsables métier, sécurité et protection des données.

- Les secrets et clés doivent être fournis par un mécanisme de gestion de secrets et ne doivent jamais être committés.
- Les contrôles d'autorisation sont appliqués côté serveur à chaque opération et à chaque périmètre de données.
- Les accès administratifs et les changements métier sensibles doivent être journalisés selon une politique approuvée.
- Les données locales hors ligne doivent être classifiées ; chiffrement, verrouillage, expiration de session et effacement à distance éventuel sont à décider selon le risque et les capacités des appareils.
- Les fichiers joints doivent être validés, limités en taille/type, stockés de façon sécurisée et soumis à des règles d'accès.
- Les erreurs retournées au client ne doivent pas révéler secrets, jetons, données personnelles ou détails internes inutiles.
- Les dépendances doivent être suivies et mises à jour ; l'intégration continue doit exécuter des contrôles automatisés adaptés.
- Les sauvegardes doivent être protégées et les restaurations testées.
- Les journaux ne doivent pas contenir de mots de passe, jetons ou données personnelles non nécessaires.
- Les finalités, bases légales, droits des personnes, durées de conservation et éventuelles obligations locales doivent être confirmés par une personne compétente avant mise en production.

## Décisions ouvertes
Voir Q-010, Q-026 et Q-028 dans `docs/product/open-questions.md`.
