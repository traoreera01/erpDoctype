# ERP DocTypes — accueil

Ce dépôt contient le **jeu de définitions ERP** du projet [xcore-doctype](https://github.com/traoreera/doctype) :
**704 définitions de DocTypes en YAML**, réparties en **22 modules**, migrées depuis ERPNext puis adaptées au schéma et aux capacités du moteur xcore-doctype.

> Ces fichiers décrivent la **structure** des documents (champs, types, liens, conditions, numérotation, workflows d'état). Toute **logique métier** — écritures comptables, mouvements de stock, droits propres à un client — vit dans les *plugins* qui chargent ces définitions, jamais dans le YAML. Voir [Implémenter un module](integration.md).

## Chiffres clés

| Mesure | Valeur |
|---|---|
| Définitions (DocTypes) | 704 |
| Modules | 22 |
| Espaces de travail nommés | 14 (+ 7 contributions) |
| Champs au total | 8 926 |
| Tables enfants (`istable`) | 293 |
| Pièces soumises (`submittable`) | 136 |
| Documents uniques (`single`) | 23 |
| Numérotation par série | 137 |
| Numérotation par champ | 8 |
| Workflows déclarés | 4 |
| Champs `currency_from` | 860 |
| Champs `fetch_from` | 123 |
| Champs `compute` | 44 |
| Champs sous condition (`depends_on`) | 100 |

## Organisation du dépôt

```
doctypes/
├── accounts/        Comptabilité (192 DT) — pièces comptables, plan SYSCOHADA
├── assets/          Immobilisations (25)
├── bulk_transaction/ Traitement en masse (2)
├── buying/          Achats (19)
├── communication/   Communication (4)
├── crm/             CRM (32)
├── edi/             EDI (2)
├── erpnext_integrations/ Intégrations ERPNext (1)
├── hr/              Ressources humaines (114)
├── maintenance/     Maintenance (5)
├── manufacturing/  Fabrication (49)
├── payroll/         Paie (42)
├── projects/        Projets (14)
├── quality_management/ Qualité (16)
├── regional/        Régionalisation (5)
├── selling/         Ventes (20)
├── setup/           Configuration (53)
├── stock/           Stock (76)
├── subcontracting/  Sous-traitance (13)
├── support/         Support (11)
├── telephony/       Téléphonie (5)
├── utilities/       Utilitaires (4)
├── workspaces/      Espaces de travail (21 fichiers YAML)
└── docs/            Cette documentation
```

Chaque dossier de module se charge indépendamment (`load_dir`) ; les liens entre modules forment un graphe **cyclique** qui impose le chargement en mode *pairs* — voir [Dépendances](dependances.md).

## Comment lire cette documentation

| Page | Contenu |
|---|---|
| [Le jeu de définitions](erp-doctypes.md) | Historique de la migration depuis ERPNext, organisation, chargement |
| [Architecture des définitions](architecture.md) | Le contrat de schéma : clés d'une définition, types de champs, numérotation, workflows, vues, permissions |
| [Dépendances entre modules](dependances.md) | Matrice complète « dépend de / requis par », cycles, ordre de déploiement |
| [Implémenter un module](integration.md) | Transformer un dossier de module en plugin xcore-doctype : gabarit, grants, hooks, traductions, validation |
| [Modules](modules/accounts.md) | 22 pages, une par module : rôle, chiffres, espace de travail, DocTypes, dépendances, implémentation |
| [Référence des champs](reference/accounts.md) | 22 pages **générées** : chaque DocType, chaque champ, avec attributs — [`docs/scripts/gen_reference.py`](scripts/gen_reference.py) |

## Provenance et licence

Les définitions sont dérivées d'ERPNext (licence GPL-3.0) et adaptées : voir `NOTICE` et `LICENSE` à la racine du dépôt, ainsi que [Le jeu de définitions](erp-doctypes.md). Elles ne doivent pas être présentées comme une copie inchangée d'ERPNext ni comme un ERP complet.
