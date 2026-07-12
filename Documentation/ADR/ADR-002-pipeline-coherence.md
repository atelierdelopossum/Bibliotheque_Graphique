# ADR-002 — Pipeline de cohérence en trois phases

**Statut :** Acté — Juillet 2026

## Contexte

La cohérence d'un personnage (ou d'un univers) sur des dizaines de générations est LE
problème technique central du projet. Trois familles de techniques existent :

- **A. Édition par référence** (modèles type FLUX Kontext, Qwen-Image-Edit) : on fournit
  une image + une consigne de variation. Simple, cohérence forte, contrôle artistique moyen.
- **B. Adaptateurs de référence** (IPAdapter, PuLID sur SDXL) : injection du visage/style
  pendant la génération. Rapide, combinable avec ControlNet, ressemblance ~80-90 % (tri
  nécessaire), optimisé pour les visages humains.
- **C. LoRA par personnage/univers** : cohérence maximale, seule option robuste pour les
  personnages non humains, mais exige un dataset d'images déjà cohérentes.

Ces techniques ne sont **pas concurrentes** : elles s'enchaînent.

## Décision

Tout personnage, mascotte ou élément signature suit le même pipeline en trois phases :

1. **Planche de référence** — génération classique + tri strict jusqu'à LA bonne version
   (voir ADR-001). Aucune technique de cohérence nécessaire à ce stade.
2. **Variations** — production des assets dérivés via A ou B, avec la planche comme
   référence. Chaque image validée (contrat : la bible graphique, ADR-005) rejoint les
   Assets officiels.
3. **LoRA** — quand le stock d'assets validés est suffisant (~20-50 images), il *devient*
   le dataset d'entraînement. Le LoRA remplace alors A/B comme mécanisme principal.

## Conséquences

- La décision initiale "ne pas toucher au Dataset avant longtemps" est confirmée et
  expliquée : le Dataset est un **produit dérivé des phases 1-2**, pas un préalable.
- Le pipeline est générique : Maggie est le premier passage sur la chaîne, pas un cas
  particulier. Luc, Illya, l'opossum, l'aéronef de Vargath suivront le même chemin.
- La cohérence d'**univers** se traite pareil : préfixe de prompt standardisé (phase 1),
  transfert de style par référence (phase 2), LoRA de style (phase 3).
- Le lore visuel (ce qui existe / n'existe pas dans l'univers) ne peut pas venir du
  modèle : il vient de la bible graphique et des planches d'éléments signatures. Le
  risque réel n'est pas l'intrusion d'éléments interdits, mais la **fuite du générique**
  (obtenir la fantasy standard au lieu des signatures de l'univers).
