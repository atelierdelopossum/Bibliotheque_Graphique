# Bible graphique — [Nom de l'univers]

> Version : 1.0 — [date]
> Modèle de production : *à déterminer (ADR-004)*
> Statut : ébauche / active

Cette bible est le **contrat de validation** entre le WIP et les Assets officiels
(ADR-005). Une image ne devient un asset officiel que si elle passe la checklist finale.

---

## 1. Identité

*L'ambiance visuelle en trois phrases maximum. Que doit-on ressentir en voyant une image
de cet univers, avant même d'en regarder le sujet ?*

- ...
- ...
- ...

## 2. Rendu

| Aspect | Choix |
|--------|-------|
| Style pictural | *(peinture numérique / semi-réaliste / ligne claire / ...)* |
| Niveau de détail | *(épuré / moyen / très détaillé)* |
| Éclairage type | *(dramatique / doux / naturel / ...)* |
| Saturation | *(désaturé / naturel / vif)* |
| Références d'inspiration | *(liens vers `References\`)* |

## 3. Palette

*5 à 8 couleurs dominantes. Les codes hex servent de référence objective lors de la validation.*

| Rôle | Couleur | Hex |
|------|---------|-----|
| Dominante 1 | ... | `#......` |
| Dominante 2 | ... | `#......` |
| Accent | ... | `#......` |

## 4. Lore visuel

### Éléments signatures (doivent apparaître de façon récurrente et identique)

| Élément | Planche de référence | Notes |
|---------|---------------------|-------|
| *(ex. aéronefs)* | `Assets_officiels\...\Signatures\...` | *(planche à créer si absente)* |

### Interdits (ne doivent jamais apparaître)

- *(ex. sous-marins)*
- *(ex. armes à feu modernes)*
- ...

## 5. Kit de prompt

### Préfixe standardisé

*Bloc copié tel quel en tête de chaque génération de cet univers.*

```text
...
```

### Exclusions types (negative prompt)

```text
...
```

---

## Checklist de validation (WIP → Assets officiels)

- [ ] Palette respectée (section 3)
- [ ] Style de rendu conforme (section 2)
- [ ] Éléments signatures conformes à leurs planches (section 4)
- [ ] Aucun interdit visible (section 4)
- [ ] Personnage reconnaissable vs sa planche de référence (si applicable)
- [ ] PNG d'origine, métadonnées workflow intactes (ADR-007)

## Historique des versions

| Version | Date | Changements |
|---------|------|-------------|
| 1.0 | ... | Création |
