# EDI (`edi`)

L'échange de données informatisées avec les partenaires : les transactions reçues et envoyées.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 2 | 0 | 0 | 0 | 0 | 0 | 15 |

## Espace de travail

**Contribution à l'espace `setup`** (aucun espace propre au module).

- **Codes** : [`Code List`](../reference/edi.md#code-list) — création, [`Common Code`](../reference/edi.md#common-code) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Code List`](../reference/edi.md#code-list) | Code List | données de base |  |  |  |
| [`Common Code`](../reference/edi.md#common-code) | Common Code | données de base |  |  |  |

## Points clés

- `EDIFACT Settings` : paramètres de connexion du partenaire ; `EDI Transaction Record` : journal de chaque échange (statut, message).
- Module **feuille**, autonome ; les cibles sont désignées par nom dans les champs `DynamicLink`.

## Dépendances

- **Dépend de** : personne.
- **Requis par** : personne pour l'instant — à brancher sur les modules commerce (`selling`, `buying`) lors de l'implémentation.

Détail complet : [matrice](../dependances.md#edi-edi).

## Implémentation en plugin xcore

- Simple à charger à tout moment ; la traduction des messages EDI vers des pièces (`Sales Order`…) est un hook d'intégration à écrire dans le plugin consommateur.

## Référence complète

[Référence — EDI](../reference/edi.md).
