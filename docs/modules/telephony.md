# Téléphonie (`telephony`)

La téléphonie intégrée au CRM : journaux d'appels, types d'appels et réglages de la voix. Le module contribue à l'espace CRM.

## Chiffres

| DocTypes | dont pièces | dont enfants | dont uniques | workflows | séries | champs |
|---|---|---|---|---|---|---|
| 5 | 1 | 1 | 2 | 0 | 1 | 30 |

## Espace de travail

**Contribution à l'espace `crm`** (aucun espace propre au module).

- **Téléphonie** : [`Call Log`](../reference/telephony.md#call-log) — création, [`Telephony Call Type`](../reference/telephony.md#telephony-call-type) — création

## DocTypes du module

| DocType | Libellé | Nature | Soumis | Numérotation | Workflow |
|---|---|---|---|---|---|
| [`Call Log`](../reference/telephony.md#call-log) | Call Log | données de base |  |  |  |
| [`Incoming Call Handling Schedule`](../reference/telephony.md#incoming-call-handling-schedule) | Incoming Call Handling Schedule | enfant |  |  |  |
| [`Telephony Call Type`](../reference/telephony.md#telephony-call-type) | Telephony Call Type | pièce | oui | `TCT-{YYYY}-{#####}` |  |
| [`Incoming Call Settings`](../reference/telephony.md#incoming-call-settings) | Incoming Call Settings | unique |  |  |  |
| [`Voice Call Settings`](../reference/telephony.md#voice-call-settings) | Voice Call Settings | unique |  |  |  |

## Points clés

- **`Call Log`** : le journal des appels entrants/sortants, relié au contact ou à la piste ; **`Telephony Call Type`** (TCT-) est la seule pièce soumise.
- **Réglages uniques** : `Voice Call Settings` (passerelle) et `Incoming Call Settings` (routage des appels entrants vers les agents, avec plages horaires `Incoming Call Handling Schedule`).
- Le connecteur lui-même n'est pas fourni — ce module décrit la trace, pas l'intégration opérateur.

## Dépendances

- **Dépend de** : `setup` (2 liens), `selling` (1).
- **Requis par** : personne.

Détail complet : [matrice](../dependances.md#telephonie-telephony).

## Implémentation en plugin xcore

- À porter avec `crm` (sa contribution va à son espace) ou à laisser de côté si aucune intégration téléphonique n'est retenue.

## Référence complète

[Référence — Téléphonie](../reference/telephony.md).
