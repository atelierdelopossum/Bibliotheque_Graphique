# ADR-006 — Sauvegarde hors machine du patrimoine

**Statut :** Acté — Juillet 2026

## Contexte

Le projet se définit comme un **patrimoine** ("une bibliothèque qui prend de la valeur au
fil du temps"), mais le cadrage initial prévoyait un dossier `Sauvegardes` sur la même
machine. Un SSD défaillant suffirait à détruire la Bibliothèque.

Constat clé : les données n'ont pas toutes la même valeur.

| Donnée | Volume | Reconstructible ? |
|--------|--------|-------------------|
| Documentation, workflows, bibles, ADR | Quelques Mo | Non → à protéger |
| Assets officiels (planches, illustrations validées) | Quelques Go | Non → à protéger |
| WIP | Potentiellement énorme | Oui (regénérable) |
| Modèles IA | Dizaines de Go | Oui (retéléchargeables) |

## Décision

- **Documentation, workflows, bibles, ADR** : dépôt **Git distant** (GitHub ou équivalent).
- **Assets officiels** : synchronisation **hors machine** — cloud, NAS, ou le VPS existant
  de l'Atelier (qui a l'espace nécessaire). Mécanisme exact à choisir au Sprint 3.
- **WIP et modèles** : sacrifiables. Aucune sauvegarde distante requise ; le dossier
  `Sauvegardes` local peut servir de copie de confort, rien de plus.

## Conséquences

- La perte totale du poste de travail coûte du temps de réinstallation, jamais le patrimoine.
- Le volume à sauvegarder à distance reste faible (quelques Go), donc peu coûteux.
- Conformité avec la décision initiale : les modèles IA et les assets ne vont pas dans Git.
