# ADR-000 — Principes d'arbitrage du projet

**Statut :** Acté — Juillet 2026

## Contexte

Le projet impliquera des dizaines de décisions techniques (prestataires, modèles,
workflows, réglages). Sans principes d'arbitrage explicites, chaque décision risque de
dériver vers l'optimisation maximale — coûteuse en temps, en argent et en complexité —
alors que le besoin est **amateur** : ambitieux et durable, mais amateur.

## Décision

Deux principes tranchent tous les arbitrages du projet, dans cet ordre :

### 1. Fiabilité avant économie

À budget raisonnable, on paie volontiers le surcoût qui garantit que ça marche du
premier coup. L'objectif n'est pas de minimiser la facture, mais de minimiser les
mauvaises surprises. Chasser le prix plancher (prestataire le moins cher, hébergeur au
rabais, bricolage pour éviter 2 €) est contraire à ce principe.

### 2. Efficacité avant perfection

Le but n'est pas la qualité maximale théorique, mais un résultat **suffisant et
constant** obtenu avec un effort raisonnable. Le "suffisant" est défini par les critères
du projet (bibles graphiques, planches de référence) — pas par l'état de l'art.

Définition de l'efficacité, dans les mots du propriétaire du projet :

> « Une illustration, aussi jolie soit-elle, dans une session de JDR perd de son intérêt
> si elle ne respecte pas les autres illustrations. Je ne cherche pas les graphismes les
> plus beaux possibles, mais que d'une image à une autre, on sache qu'il s'agit du ou des
> personnages et qu'on est toujours dans le même univers. »

Corollaire : dans ce projet, la cohérence n'est pas une contrainte posée sur la qualité —
elle **est** la qualité. L'échelle de valeur d'une image n'est pas « belle → très belle »
mais « reconnaissable et à sa place → pas à sa place ». Une image dissonante retire de la
valeur à la collection, quelle que soit sa beauté intrinsèque.

Concrètement, sont contraires à ce principe : le workflow à 47 nœuds qui gagne 3 % de
qualité, le dernier modèle expérimental à la mode, le fine-tuning d'un détail invisible
en miniature YouTube.

## Conséquences

- Face à un arbitrage, l'option par défaut est **robuste et simple**, jamais maximale.
- Ces principes complètent le principe fondateur "la cohérence avant la qualité" :
  la cohérence est l'exigence non négociable ; la qualité vise le suffisant ; le coût
  est secondaire tant qu'il reste raisonnable.
- Application immédiate : choix RunPod Secure Cloud plutôt que le marché au rabais
  (ADR-003) ; SDXL plutôt que le modèle le plus puissant du moment (ADR-004).
