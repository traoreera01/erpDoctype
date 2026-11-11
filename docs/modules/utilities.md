# Utilitaires (`utilities`)

Quatre DocTypes transverses : l'utilisateur du portail client/fournisseur, l'outil de renommage, et la vidéo de présentation. Le module contribue à l'espace Configuration.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 4 | 0 | 1 | 1 | 0 | 0 | 18 |

## Espace de travail

**Contribution à l'espace `setup`** (aucun espace propre au module).

- **Outils** : [`Rename Tool`](../reference/utilities.md#rename-tool) — création, [`Video`](../reference/utilities.md#video) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Rename Tool`](../reference/utilities.md#rename-tool) | Rename Tool | données de base |  |  |  |
| [`Video`](../reference/utilities.md#video) | Video | données de base |  |  |  |
| [`Portal User`](../reference/utilities.md#portal-user) | Portal User | enfant |  |  |  |
| [`Video Settings`](../reference/utilities.md#video-settings) | Video Settings | unique |  |  |  |

## Points clés

- **`Portal User`** (table enfant) : un utilisateur du portail — email et rôle, attaché aux fiches `Customer`/`Supplier` ; c'est le lien par lequel `selling` et `buying` ouvrent le portail.
- **`Rename Tool`** : l'outil de renommage en masse ; le moteur fournit déjà `rename` unitaire.
- **`Video`/`Video Settings`** : les vidéos d'aide intégrées.

## Dépendances

- **Dépend de** : personne (module feuille).
- **Requis par** : `buying` (1), `selling` (1) — les deux consomment `Portal User`.

Détail complet : [matrice](../dependances.md#utilitaires-utilities).

## Implémentation en plugin xcore

- Peut être fusionné dans `setup` ; l'accès portail d'un `Portal User` exige l'authentification (le compte doit exister côté xauth).

## Référence complète

[Référence — Utilitaires](../reference/utilities.md).
