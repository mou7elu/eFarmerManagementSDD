# eFarmerManagement — reconstruction SDD

> Statut : dossier de cadrage initial. Ce dépôt documentaire ne constitue pas encore une spécification métier validée.

## Objectif
Reconstruire eFarmerManagement de zéro avec une démarche Spec-Driven Development (SDD), en visant une plateforme agricole complète, web et mobile, avec fonctionnement hors ligne essentiel et capacité à évoluer vers une grande échelle.

## Choix confirmés à ce stade
- Périmètre cible : plateforme complète.
- Utilisateurs prioritaires mentionnés : producteurs, collecteurs, administrateurs, agents de terrain.
- Plateformes : application web et application mobile.
- Fonctionnement hors ligne : essentiel.
- Échelle : grande échelle visée, sans objectif chiffré validé.

## Ce qui n'est PAS encore décidé
- Pays et périmètre géographique du lancement, cultures et filières prioritaires.
- Workflow exact des modules collecte, traçabilité, durabilité et gestion.
- Rôles détaillés, permissions et organisation multi-tenant.
- Stack technique définitive, moteur de base de données, hébergement et budget.
- Volumétrie, SLO/SLA, politique de conservation et obligations réglementaires.
- Modèle de synchronisation hors ligne et règles de résolution des conflits.

Les hypothèses ne doivent pas être converties en exigences avant validation par les parties prenantes.

## Démarrage
1. Lire `docs/product/product-discovery.md`.
2. Répondre aux questions de `docs/product/open-questions.md`.
3. Valider le périmètre MVP et les métriques de succès.
4. Établir les exigences traçables dans `docs/requirements/`.
5. Décider l'architecture à partir des exigences validées.
6. Créer une spec complète dans `docs/specs/` pour une première fonctionnalité verticale.
7. Développer et tester seulement après validation des critères d'acceptation.

## Principe SDD
Requirement → Specification → Design → Tasks → Implement → Test → Review/update docs.
Le cycle est itératif. Les tests et les retours terrain peuvent conduire à modifier une spec ou un design.

## Source existante
L'ancienne archive eFarmerManagement est une source de découverte, pas une vérité normative. Les questionnaires et le code existants peuvent informer les ateliers, mais chaque règle métier doit être confirmée. Ne copiez pas automatiquement les choix d'architecture, les endpoints ou les modèles legacy.
