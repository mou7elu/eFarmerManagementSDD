# eFarmerManagement — reconstruction SDD

> **Statut** : dossier de cadrage initial. Ce dépôt documentaire ne constitue pas encore une spécification métier validée.
>
> **Version** : 0.2 — réconciliée avec la vision v0.2, la roadmap v0.2, le Product Discovery v0.2, le glossaire v0.2, les questions ouvertes v0.2, le plan d'architecture v0.2 et le registre des décisions v0.2.
>
> **Date** : 2026-10-26

## Objectif

Reconstruire eFarmerManagement de zéro avec une démarche **Spec-Driven Development (SDD)**, en visant une plateforme agricole **multi-filières**, web et mobile, avec **fonctionnement hors ligne essentiel** et capacité à évoluer vers une grande échelle.

Le dépôt est **documentaire à ce stade** : il organise la découverte, les exigences, les spécifications et les décisions d'architecture. **Aucun code métier n'est produit avant validation des exigences et des ADR.**

## Choix confirmés à ce stade

- **Pays de lancement** : Côte d'Ivoire (zones pilotes, langues et unités à préciser — OPEN-002).
- **Filières** : plusieurs filières dès le départ (cacao, café, anacarde, hévéa, palmier à huile, autres) — liste exacte à définir (OPEN-001).
- **Stratégie de livraison** : MVP d'abord, puis extensions progressives (périmètre MVP non encore priorisé — OPEN-004).
- **Profils de découverte** : **collecteurs, agents de terrain, administrateurs**. Le **producteur est une entité métier** (données gérées par les profils), **pas un profil utilisateur au lancement** (cf. vision v0.2, Q-004, OPEN-010).
- **Plateformes** : application web et application mobile Flutter.
- **Fonctionnement hors ligne** : essentiel — saisir, consulter et modifier les données déjà téléchargées (périmètre → OPEN-006 ; conflits → OPEN-007).
- **Multi-organisation** : plusieurs clients/organisations avec **cloisonnement des données confirmé** (modèle → OPEN-005 / `adr/0004`).
- **Échelle** : ambition de volumétrie **~800 000 producteurs ou davantage**, à valider par un **modèle de charge** (OPEN-008).
- **Équipe** : porteur du projet principalement, avec assistance IA (Q-009).

## Ce qui n'est PAS encore décidé

- **Zones pilotes, langues et unités** du lancement (OPEN-002).
- **Liste exacte des filières** et particularités par filière (OPEN-001).
- **Workflow exact** des modules collecte, traçabilité, durabilité et gestion (OPEN-003, OPEN-014).
- **Rôles détaillés, permissions et hiérarchie organisationnelle** (Client → Organisation → Coopérative → Campagne → Zone) (OPEN-005, OPEN-031).
- **Modèle de synchronisation hors ligne** et règles de résolution des conflits (OPEN-007, `adr/0002`).
- **Stack technique définitive**, moteur de base de données, hébergement et budget (OPEN-022, OPEN-023, `adr/0001`, `adr/0003`, `adr/0005`).
- **Volumétrie détaillée, SLO/SLA, politique de conservation et obligations réglementaires** (OPEN-008, OPEN-009, OPEN-025, OPEN-026).
- **Traçabilité et infalsifiabilité** (blockchain ou autre) (`adr/0008`).

> **Règle** : les hypothèses ne doivent pas être converties en exigences avant validation par les parties prenantes. Les inconnues non bloquantes peuvent rester ouvertes, mais **doivent avoir un responsable et une date de réexamen** (cf. Gate de passage de la roadmap v0.2).

## Documents de référence

| Document | Rôle | Statut | Emplacement |
|---|---|---|---|
| **Vision** | Cadrage produit (où l'on va, pour qui, avec quels garde-fous) | Provisoire v0.2 | `docs/product/vision.md` |
| **Roadmap** | Phases de découverte et de livraison, ordonnées par dépendances | Provisoire v0.2 | `docs/product/roadmap.md` |
| **Product Discovery** | Décisions confirmées, hypothèses à tester, questions de recherche | v0.2 (validation métier requise) | `docs/product/product-discovery.md` |
| **Questions ouvertes** | Registre des inconnues P0/P1, avec responsable et statut | v0.2 | `docs/product/open-questions.md` |
| **Glossaire métier** | Définitions des termes métier (producteur, lot, cascade de traçabilité…) | v0.2 (à valider) | `docs/glossaire-metier.md` |
| **Plan d'architecture cible** | Proposition d'architecture, non décisionnelle | v0.2 (à décider) | `docs/architecture/plan-architecture-cible.md` |
| **Registre des décisions (ADR)** | Suivi des décisions d'architecture (0001 → 0008) | v0.2 | `docs/architecture/adr/README.md` |
| **Gabarit ADR** | Format standard des décisions d'architecture | — | `docs/architecture/adr/_template.md` |

## Arborescence du dépôt

```text
eFarmerManagementSDD/
├── README.md                          ← ce fichier
├── AGENTS.md                          ← règles pour l'assistance IA
├── CONTRIBUTING.md                    ← conventions de contribution
├── .gitignore
├── .gitattributes
├── docs/
│   ├── glossaire-metier.md            ← termes métier (v0.2)
│   ├── product/
│   │   ├── vision.md                  ← cadrage produit (v0.2)
│   │   ├── roadmap.md                 ← phases et dépendances (v0.2)
│   │   ├── product-discovery.md       ← décisions / hypothèses (v0.2)
│   │   └── open-questions.md          ← registre des inconnues (v0.2)
│   ├── architecture/
│   │   ├── plan-architecture-cible.md ← proposition d'architecture (v0.2)
│   │   └── adr/
│   │       ├── README.md              ← registre des décisions (v0.2)
│   │       ├── _template.md           ← gabarit ADR
│   │       ├── 0001-hebergement.md
│   │       ├── 0002-idempotence-sync.md
│   │       ├── 0003-base-de-donnees.md
│   │       ├── 0004-isolation-multi-org.md
│   │       ├── 0005-stack.md
│   │       ├── 0006-api-versionnement.md
│   │       ├── 0007-observabilite-livraison.md
│   │       └── 0008-tracabilite-infalsifiabilite.md
│   ├── requirements/                  ← exigences traçables (Phase 1)
│   └── specs/                         ← spécifications par domaine (Phase 1)
│       ├── 01-producteurs-parcelles.md
│       ├── 02-collecte-terrain.md
│       ├── 03-tracabilite.md
│       ├── 04-durabilite.md
│       ├── 05-administration-reporting.md
│       └── 06-identite-permissions-multi-org.md