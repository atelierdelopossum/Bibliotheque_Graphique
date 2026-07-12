# ADR-001 — L'asset fondateur d'un personnage est une planche de référence

**Statut :** Acté — Juillet 2026

## Contexte

Le cadrage initial définissait "Maggie v1.0" comme le premier asset officiel, implicitement
sous forme d'illustration. Or les modèles de génération n'ont aucune mémoire : garder un
personnage reconnaissable exige une image de référence exploitable par les outils de
cohérence (édition par référence, IPAdapter/PuLID, futur LoRA).

Une illustration unique (un seul angle, un seul éclairage, une seule expression) est une
mauvaise référence.

## Décision

L'asset fondateur de tout personnage est une **planche de référence** (character sheet),
pas une illustration. Contenu minimal :

- visage de face, de trois-quarts et de profil ;
- corps entier (tenue de base) ;
- 2 à 4 expressions clés ;
- fond neutre, éclairage neutre.

La planche est versionnée (Maggie v1.0, v1.1...). Les illustrations "spectaculaires"
(scènes, poses, tenues alternatives) sont des assets **dérivés**, produits en phase 2 du
pipeline (voir ADR-002) à partir de la planche.

## Conséquences

- Le premier livrable graphique du projet n'est pas Maggie : c'est le **workflow ComfyUI
  capable de produire une planche**, validé sur un personnage anonyme.
- Ce principe s'applique aussi aux éléments signatures d'un univers (ex. l'aéronef type
  de Vargath) : un design récurrent = une planche de référence.
- La mascotte opossum (personnage anthropomorphe) suivra le même principe, avec une
  contrainte supplémentaire : les adaptateurs de visages humains ne l'aideront pas ;
  sa cohérence reposera sur l'édition par référence puis le LoRA.
