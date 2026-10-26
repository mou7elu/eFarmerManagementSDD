# AGENTS.md — Règles pour l'assistance IA

- Version : 0.2
- Date : 2026-10-26
- Portée : tout agent IA (assistant de code, générateur de specs, relecteur, etc.)
  intervenant sur le dépôt eFarmerManagementSDD.
- Document de référence : `README.md` (v0.2). En cas de conflit, le README et les
  documents de `docs/` priment sur ce fichier.

## 1. Posture générale

1. **Ce dépôt est documentaire à ce stade.** Ne produis pas de code métier avant
   validation des exigences (Phase 1) et approbation des ADR (Phase 2).
2. **Ne convertis jamais une hypothèse en exigence.** Les hypothèses sont dans
   `docs/product/product-discovery.md` (HYP-XXX) et `docs/product/open-questions.md`
   (OPEN-XXX). Tant qu'elles ne sont pas validées, elles restent des hypothèses.
3. **Ne fige jamais un choix technique.** La stack, la BDD, l'hébergement et la
   traçabilité/infalsifiabilité sont des ADR non décidés (`adr/0001` à `adr/0008`).
   Tu peux **proposer** des options, jamais **trancher**.
4. **Respecte le Gate de passage** : « Ne pas figer les choix techniques ni commencer
   l'implémentation métier à grande échelle avant d'avoir validé les exigences qui
   conditionnent ces choix. » (roadmap v0.2)
5. **Trace tes contributions** : toute modification doit être rattachable à un
   document existant (`vision`, `roadmap`, `Product Discovery`, `open-questions`,
   `glossaire`, `plan-architecture-cible`, `adr/`).

## 2. Règles de cohérence (à vérifier avant toute production)

1. **Profils** : il y a **3 profils de découverte** — collecteurs, agents de terrain,
   administrateurs. **Le producteur est une entité métier**, pas un profil utilisateur
   au lancement. (cf. vision v0.2, roadmap v0.2, Q-004, OPEN-010.)
2. **Pays de lancement** : Côte d'Ivoire (confirmé). Zones pilotes, langues et unités
   restent à préciser (OPEN-002).
3. **Offline-first** : toute spec ou ADR qui touche à la synchronisation doit
   respecter les principes : idempotence, file d'attente durable, résolution des
   conflits **par type de donnée**, pas de « last write wins » générique sans
   validation (OPEN-007, `adr/0002`).
4. **Multi-organisation** : le cloisonnement est **confirmé** ; le **modèle** (schéma
   par tenant, base par tenant, colonne `tenant_id`) reste à trancher (`adr/0004`).
   Toute spec doit prévoir des tests d'accès croisés.
5. **Traçabilité** : la cascade de lots est définie au glossaire v0.2
   (bord-champ → évacuation → réception coopérative → transfert exportateur). Les
   règles de regroupement/scission restent à trancher (OPEN-013). L'infalsifiabilité
   (blockchain ou autre) est une décision non prise (`adr/0008`).
6. **Données personnelles** : minimisation, finalités et durées de conservation à
   cadrer (OPEN-009 / D-012 à créer). Ne jamais exposer de données sensibles dans les
   logs, les exemples ou les specs.
7. **Terminologie** : utiliser les termes du `docs/glossaire-metier.md` v0.2. Si un
   terme manque, le signaler — ne pas en inventer un nouveau sans mise à jour du
   glossaire.

## 3. Ce que tu peux faire

- Rédiger des **squelettes** de specs, d'ADR, de docs, en respectant les gabarits.
- **Comparer des options** dans un ADR (matrice de comparaison), sans trancher.
- **Détecter les incohérences** entre documents et les signaler explicitement.
- **Proposer des questions ouvertes** (OPEN-XXX) quand une inconnue apparaît.
- **Proposer des tests** (unitaires, intégration, offline, sécurité) dans les specs.
- **Mettre à jour la traçabilité** (tableaux de renvoi entre documents).

## 4. Ce que tu ne dois pas faire

- ❌ Choisir la stack, la BDD, l'hébergement ou la blockchain.
- ❌ Transformer une hypothèse (HYP-XXX) en exigence (REQ-XXX) sans validation.
- ❌ Ajouter un terme au glossaire sans définition et sans statut de validation.
- ❌ Écrire du code métier avant la Phase 4 (MVP vertical).
- ❌ Modifier un ADR « Accepté » sans créer un nouvel ADR qui le remplace.
- ❌ Supprimer une question ouverte sans réponse documentée.
- ❌ Inventer des volumes, des SLO ou des règles métier non validés.

## 5. Format de sortie attendu

- **Specs** : suivre le gabarit de `docs/specs/` (à créer), avec les sections
  Objectif, Récits utilisateurs, Règles métier, Données, Offline/sync, Permissions,
  Audit, Cas limites, Non-objectifs, Questions ouvertes.
- **ADR** : suivre `docs/architecture/adr/_template.md` (statut, décideurs,
  exigences liées, options + matrice, décision, conséquences, validation, réexamen).
- **Documents de cadrage** : suivre le style des documents v0.2 (statut explicite,
  séparation décidé / hypothèse / question ouverte, renvois OPEN-XXX / HYP-XXX).

## 6. En cas de doute

1. Signaler l'ambiguïté au porteur du projet.
2. Proposer une question ouverte (OPEN-XXX) plutôt que de trancher.
3. Vérifier la cohérence avec `README.md` v0.2 et `docs/product/vision.md` v0.2.
4. Ne jamais « compléter » une décision manquante par une supposition silencieuse.

---

*Ce fichier est un garde-fou, pas une contrainte créative. Son but est d'éviter les
décisions prématurées et les incohérences entre documents.*