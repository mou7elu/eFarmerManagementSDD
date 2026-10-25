# Vision produit — eFarmerManagement

- Statut : vision de cadrage provisoire, fondée sur les réponses du porteur de projet
- Version : 0.2

## Vision
Construire une plateforme de gestion agricole déployée d’abord en Côte d’Ivoire, couvrant plusieurs filières, accessible via le web et le mobile et conçue pour permettre le travail de terrain avec une connectivité intermittente. Le produit sera livré sous forme de MVP puis étendu, avec une ambition de capacité d’environ 800 000 producteurs ou davantage.

## Publics retenus pour la découverte
- Producteurs
- Collecteurs
- Agents de terrain
- Administrateurs

Le fait de considérer ces profils au lancement ne définit pas encore leurs permissions ni ne signifie qu’ils réaliseront les mêmes tâches dans l’application.

## Périmètre à étudier avant de prioriser
- Gestion des producteurs, exploitations et parcelles
- Collecte
- Traçabilité
- Durabilité
- Administration, gestion et reporting
- Identité, permissions et cloisonnement multi-organisation

Tous ces domaines doivent être étudiés ; le contenu du MVP reste à décider.

## Principes de conception proposés
1. Définir explicitement les parcours hors ligne et les données disponibles localement.
2. Éviter les pertes de données avec synchronisation durable, idempotence et résolution des conflits par type de donnée.
3. Appliquer les autorisations côté serveur et tester l’isolation entre organisations.
4. Garder une trace des modifications métier sensibles.
5. Concevoir une solution soutenable par une équipe principalement composée du porteur du projet et d’une assistance IA.
6. Mesurer les charges et performances avec des scénarios réalistes plutôt que supposer qu’un nombre de producteurs suffit à définir l’échelle.
7. Documenter les décisions techniques et leur justification.

## Décisions non prises
La stack finale, la base de données, le fournisseur d’hébergement, la hiérarchie exacte des organisations, les règles de certification, les workflows détaillés, les seuils de performance et le périmètre MVP ne sont pas encore approuvés.
