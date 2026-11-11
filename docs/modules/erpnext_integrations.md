# Intégrations ERPNext (`erpnext_integrations`)

Les réglages des connecteurs vers des services bancaires externes — seule trace des intégrations d'ERPNext conservée dans le jeu.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 1 | 0 | 0 | 1 | 0 | 0 | 5 |

## Espace de travail

Ce module n'a pas d'espace de travail ni de contribution.

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Plaid Settings`](../reference/erpnext_integrations.md#plaid-settings) | Plaid Settings | unique |  |  |  |

## Points clés

- `Plaid Settings` : document unique (`single: true`) — identifiants du service Plaid d'agrégation bancaire.
- Le connecteur lui-même n'existe pas dans ce jeu : seul le réglage est décrit.

## Dépendances

- **Dépend de** : personne. **Requis par** : personne.

Détail complet : [matrice](../dependances.md#integrations-erpnext-erpnext_integrations).

## Implémentation en plugin xcore

- Peut être fusionné dans le plugin `accounts` (réglage bancaire) ou supprimé si le service n'est pas retenu.

## Référence complète

[Référence — Intégrations ERPNext](../reference/erpnext_integrations.md).
