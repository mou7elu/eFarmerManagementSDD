# Vision produit — eFarmerManagement

- Statut : vision de cadrage provisoire, qui sera evolutif au fur et à mesure
- Version : 0.2

## Vision
Construire une plateforme de gestion agricole déployée d’abord en Côte d’Ivoire, couvrant plusieurs filières agro-industriel(cacao,café,l'anarcarde,l'hevea ,le palmier à huile et bien d'autres cultures), accessible via le web et le mobile et conçue pour permettre le travail de terrain avec une connectivité intermittente. Le produit sera livré sous forme de SAAS avec la possibilité si un client le veut de l'installer sur son propre environnement, avec une ambition de capacité d’environ 800 000 producteurs ou davantage dans la base de données.

## Publics retenus pour la découverte
- Collecteurs (agents de saisie dans les différentes coopératives)
- Agents de terrain
- Administrateurs

Le fait de considérer ces profils au lancement ne définit pas encore leurs permissions ni ne signifie qu’ils réaliseront les mêmes tâches dans l’application.

## Périmètre à étudier avant de prioriser
- Gestion des producteurs, de son ménages et de ses parcelles
- Collecte des données sur le terrain
- Traçabilité sous forme de blockchain de la production dans les parcelles jusqu'à la livraison aux exportateurs
- Durabilité des questionnaires qui seront modulaires definis pas le client final (qui aura la main pour crée ses questions)
- Administration, gestion et reporting
- Gestion des flux financiers dans lapplication (avoir une une comptabilité,RH dans l'application)
- Identité, permissions et cloisonnement multi-organisation


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
