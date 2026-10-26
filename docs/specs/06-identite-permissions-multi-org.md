# Spec 06 — Identité, permissions et cloisonnement multi-organisation

- Statut : Brouillon (à valider en Phase 1)
- Version : 0.1
- Domaine : Identity & Access
- Phase roadmap : Phase 1 → Phase 2 (ADR) → Phase 3 (fondations)
- Dépendances : OPEN-004, OPEN-005, OPEN-031, OPEN-028
- ADR liés : adr/0004 (isolation), adr/0002 (auth offline)

## 1. Objectif
Définir l'identité, les rôles, les permissions et le cloisonnement
multi-organisation, y compris pour les données synchronisées et hors ligne.

## 2. Périmètre
**Inclus** : authentification, sessions, rôles, permissions, périmètres
organisationnels, hiérarchie (Client → Organisation → Coopérative → Campagne → Zone),
isolation, auth offline, appareil perdu.
**Exclus** : gestion des producteurs (spec 01), collecte (spec 02), etc.

## 3. Profils concernés
- Tous les profils (collecteurs, agents de terrain, administrateurs).
- Le producteur n'est pas un profil utilisateur au lancement (OPEN-010).

## 4. Récits utilisateurs (à valider)
- En tant qu'**utilisateur**, je veux m'authentifier et accéder à mon périmètre,
  afin de travailler en sécurité.
- En tant qu'**administrateur**, je veux créer des organisations et gérer les accès,
  afin d'administrer les utilisateurs.
- En tant qu'**utilisateur offline**, je veux continuer à travailler avec une session
  valide, afin de ne pas être bloqué par le réseau (OPEN-028).
- En tant qu'**administrateur**, je veux révoquer un appareil perdu, afin de
  protéger les données locales (OPEN-028).

## 5. Règles métier (à valider)
- **Hiérarchie** : Client → Organisation → Coopérative → Campagne → Zone → OPEN-005.
- **Section** : lieu ou zone ? → OPEN-031.
- **Rôles et permissions** : matrice à définir → OPEN-004.
- **Auth offline** : durée de validité, révocation, chiffrement local → OPEN-028.
- **Appareil perdu** : effacement local et à distance → OPEN-028.
- **Sessions expirées** : comportement offline → OPEN-028.

## 6. Données manipulées
Entités candidates : Utilisateur, Session, Rôle, Permission, Organisation,
Coopérative, Campagne, Zone, Section, Appareil.
Voir glossaire v0.2 et `modele-donnees.md` (à créer).

## 7. Parcours hors ligne et synchronisation
- Auth offline : token local chiffré, durée de validité (OPEN-028).
- Révocation : à la prochaine connexion ou par effacement à distance.
- Permissions vérifiées côté serveur à la synchronisation (principe 3).
- Conflits de permissions : résolution côté serveur.

## 8. Permissions et cloisonnement
- **Isolation confirmée** : chaque requête et chaque donnée est cloisonnée par
  organisation (adr/0004).
- Modèle à trancher : colonne `tenant_id`, schéma par tenant, base par tenant.
- Tests d'accès croisés obligatoires (section 10).
- Les permissions sont **toujours vérifiées côté serveur**, y compris pour les
  données synchronisées.

## 9. Traçabilité et audit
- Journalisation des connexions, révocations, changements de permissions.
- Audit des accès croisés refusés.

## 10. Cas limites et erreurs
- Session expirée hors ligne → comportement à définir (OPEN-028).
- Appareil perdu → révocation + effacement (OPEN-028).
- Accès croisé tenté → refus + audit.
- Conflit de permission (accordée offline, révoquée serveur) → serveur prime.

## 11. Exigences non fonctionnelles (renvois)
- Performance auth : mesurée.
- Disponibilité : OPEN-025.
- Chiffrement local : OPEN-028.

## 12. Non-objectifs
- Pas de gestion des producteurs (spec 01).
- Pas de reporting (spec 05).

## 13. Questions ouvertes
- OPEN-004 (rôles, permissions), OPEN-005 (hiérarchie), OPEN-031 (Section),
  OPEN-028 (auth offline, appareil perdu), OPEN-010 (producteur direct).

## 14. Dépendances ADR
- adr/0004 (isolation), adr/0002 (auth offline / sync).
  **Bloquant** : OPEN-005 et OPEN-031 à trancher avant implémentation.