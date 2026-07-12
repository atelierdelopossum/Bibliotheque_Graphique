# ADR-004 — SDXL pour apprendre, modèle de production différé

**Statut :** Acté — Juillet 2026. Choix du (des) modèle(s) de production : **différé**.

## Contexte

Le cadrage initial citait FLUX comme modèle implicite. Or :

- sur RDNA3, pas de FP8 → FLUX tourne en FP16/GGUF, plus lourd et plus lent ;
- la licence de FLUX.1-dev est non commerciale (à vérifier précisément vs l'usage chaîne
  YouTube au moment du choix) ;
- la phase d'apprentissage (étape 3 de la roadmap) a besoin d'un modèle qui **itère vite** :
  plus on génère, plus on apprend.

SDXL : génération en quelques secondes sur la 7900 XT, écosystème le plus riche
(ControlNet matures, IPAdapter, PuLID, milliers de LoRA d'exemples), bonne gestion des
negative prompts (utile pour les kits d'exclusion d'univers), rodé sur AMD, licence
permissive. Ses faiblesses (texte dans l'image, photoréalisme extrême) sont indifférentes
pour de l'illustration JDR.

## Décision

- **Modèle d'apprentissage : SDXL.** Toute l'étape 3 (maîtrise de ComfyUI, workflow de
  planche, personnage anonyme) se fait sur SDXL.
- **Le choix du modèle de production est une décision explicite**, prise en fin
  d'apprentissage sur tests comparatifs, selon quatre critères :
  1. qualité du rendu dans le style cible de l'univers (pas dans l'absolu) ;
  2. compatibilité avec le pipeline de cohérence (ADR-002) : édition par référence
     disponible ? entraînement LoRA aisé ?
  3. performances sur la RX 7900 XT (formats supportés, VRAM, vitesse) ;
  4. **licence** compatible avec un usage commercial (chaîne monétisable).
- Le modèle est un **attribut de la bible graphique de chaque univers**, pas une décision
  globale : Vargath et les miniatures YouTube peuvent utiliser des modèles différents.

## Conséquences

- Aucun engagement sur FLUX ni sur aucun modèle : le paysage évolue vite, un état des
  lieux sera refait au moment du choix.
- Apprendre sur SDXL n'est pas du travail perdu : les concepts ComfyUI (samplers,
  conditionnement, ControlNet, workflows) sont transférables.
