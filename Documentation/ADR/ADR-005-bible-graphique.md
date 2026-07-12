# ADR-005 — La bible graphique comme contrat de validation

**Statut :** Acté — Juillet 2026

## Contexte

Le principe fondateur "la cohérence avant la qualité" n'est pas opérationnel tel quel :
face à une image générée, "est-elle cohérente ?" appelle un ressenti, et les ressentis
dérivent (surtout après cinquante générations). Par ailleurs, la cohérence de **lore**
(les aéronefs de Vargath existent, les sous-marins non) ne peut pas venir du modèle,
qui ne "connaîtra" jamais l'univers.

## Décision

Chaque univers possède une **bible graphique** : document Markdown d'une à deux pages,
versionné dans Git, rédigé **avant** le premier asset officiel de l'univers, contenant
cinq sections (voir `templates/bible_graphique.md`) :

1. **Identité** — l'ambiance visuelle en trois phrases ;
2. **Rendu** — style pictural, niveau de détail, éclairage, saturation ;
3. **Palette** — 5 à 8 couleurs dominantes avec codes hexadécimaux ;
4. **Lore visuel** — éléments signatures obligatoires (avec renvoi vers leurs planches
   de référence) et liste des interdits ;
5. **Kit de prompt** — préfixe standardisé + exclusions types, copiables-collables.

La bible est le **contrat de validation** entre le WIP et les Assets officiels : une image
ne quitte le WIP que si elle passe la checklist (palette respectée ? rendu conforme ?
signatures présentes ? aucun interdit visible ?).

## Conséquences

- La frontière WIP / Assets officiels du cadrage initial acquiert un critère objectif.
- La bible v1 sera imparfaite et s'affinera pendant la production : c'est un document
  versionné (Vargath aura une bible v1.2 comme Maggie une planche v1.1).
- La rédaction de la bible Vargath v1 devient une étape explicite de la feuille de route,
  **avant** la planche de Maggie.
- Le modèle de production retenu pour l'univers (ADR-004) est consigné dans sa bible.
