# Exigences fonctionnelles — registre initial

- Statut : registre initial non validé
- Les lignes ci-dessous sont des domaines à instruire, pas des engagements fonctionnels complets.

| ID | Domaine | Besoin candidat | Statut | Critère d'acceptation |
|---|---|---|---|---|
| FR-IDENT-001 | Identité et accès | Les utilisateurs autorisés accèdent aux fonctions selon leurs permissions | À spécifier | À définir après matrice rôles/actions |
| FR-PROD-001 | Producteurs | Les acteurs autorisés peuvent consulter les informations producteur nécessaires à leur travail | À confirmer | À définir avec les champs et permissions validés |
| FR-FARM-001 | Exploitations/parcelles | Les acteurs autorisés peuvent gérer les informations validées sur exploitations et parcelles | À confirmer | À définir après modèle métier |
| FR-COLL-001 | Collecte | Les acteurs autorisés peuvent réaliser les opérations de collecte retenues | À spécifier | Workflow et unités à valider |
| FR-TRACE-001 | Traçabilité | Les acteurs autorisés peuvent consulter l'historique validé d'un lot | À spécifier | Définir lot, événements et droits |
| FR-SUST-001 | Durabilité | Les données et contrôles de durabilité retenus peuvent être enregistrés et consultés | À confirmer | Référentiels et critères à valider |
| FR-OFF-001 | Hors ligne | Les parcours explicitement retenus restent utilisables sans réseau | Confirmé comme contrainte, périmètre à définir | Scénarios offline et sync à valider |
| FR-SYNC-001 | Synchronisation | Les modifications locales sont synchronisées sans perte silencieuse | Exigence de qualité proposée | Règles de conflit et reprise à spécifier |
| FR-AUD-001 | Audit | Les changements métier sensibles sont traçables selon une politique validée | À confirmer | Événements et durée de conservation à définir |
| FR-REP-001 | Reporting | Les utilisateurs autorisés accèdent aux rapports validés | À confirmer | Rapports, filtres et exports à définir |

## Règles
- Une exigence approuvée doit avoir un propriétaire, une justification, une priorité, une source et des critères testables.
- Les champs et workflows ne doivent pas être dérivés automatiquement du code existant.
- Les exigences hors ligne doivent distinguer création, lecture, modification, suppression, pièces jointes et synchronisation.
