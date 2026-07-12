# ADR-003 — Inférence locale, entraînement déporté

**Statut :** Acté — Juillet 2026. Choix de l'option d'entraînement : **différé** (décision
nécessaire seulement à l'entrée en phase 3 du pipeline).

## Contexte

Le GPU du poste de travail est une AMD RX 7900 XT (20 Go VRAM).

- **Inférence** : le support officiel AMD ROCm sur Windows est disponible pour ComfyUI
  (ROCm 7.1.1+, driver AMD PyTorch preview requis, Python 3.12). La 7900 XT est dans la
  liste des GPU supportés. Contrainte : pas de FP8 sur RDNA3 → privilégier FP16/BF16/GGUF.
- **Entraînement** (LoRA) : les outils (kohya_ss, OneTrainer...) restent nettement moins
  fiables hors NVIDIA/Linux. L'entraînement est par ailleurs une opération **ponctuelle**
  (quelques heures, quelques fois par an), contrairement à l'inférence quotidienne.

## Décision

- **Inférence : 100 % locale**, sur la RX 7900 XT via ROCm natif Windows.
- **Entraînement : déporté hors de la machine principale.** Trois options, classées par
  coût, choix à faire au moment de la phase 3 :

| Option | Description | Coût estimé | Recommandation |
|--------|-------------|-------------|----------------|
| 1 | Location GPU à l'heure (RunPod, Vast.ai — RTX 4090+) | ~1-3 € par LoRA | ✅ Recommandée |
| 2 | Linux en dual-boot sur la machine actuelle (ROCm) | 0 € + temps de debug | Si envie d'apprendre Linux |
| 3 | Machine NVIDIA dédiée | Plusieurs centaines/milliers € | ❌ Non amortissable pour ce seul besoin |

### Précisions sur l'option 1 (juillet 2026)

Critères de l'utilisateur : puissance suffisante, délais cohérents, mise en place rapide,
simplicité d'utilisation. Application du principe **fiabilité avant économie** (ADR-000) :
on ne chasse pas le prix plancher.

- **Plateforme recommandée : RunPod, tier Secure Cloud** (~0,69 $/h pour une RTX 4090,
  facturation à la seconde, prix fixes publiés, transfert de données gratuit, templates
  pré-installés kohya_ss / OneTrainer). Vast.ai (~0,29-0,59 $/h) est moins cher mais exige
  de comparer les hébergeurs et leurs scores de fiabilité — incompatible avec le critère
  de simplicité.
- **Carte : RTX 4090 par défaut** (24 Go VRAM, point d'équilibre pour LoRA SDXL).
  Le choix de la carte se refait à chaque session : un futur LoRA sur modèle plus lourd
  pourra louer plus gros, sans engagement.
- **Coût réaliste : ~2 € par session** de 1-3 h en Secure Cloud.
- **Hygiène de fin de session : SUPPRIMER le pod** (pas seulement l'arrêter — un pod
  arrêté continue de facturer son stockage). Le dataset vit en local ; rien ne persiste
  chez le prestataire.
- **Prérequis au premier entraînement réel** : une procédure pas-à-pas rédigée dans
  `Documentation/guides/` (template, réglages, checklist avant/après, suppression du
  pod). La première session est l'exécution d'une recette, pas une exploration facturée
  à l'heure.

Tarifs relevés en juillet 2026 — à revérifier au moment de la phase 3.

## Conséquences

- Architecture hybride assumée, cohérente avec le principe "les outils sont remplaçables" :
  si ROCm devient fiable pour l'entraînement sous Windows, on rapatrie sans rien changer d'autre.
- La **préparation du dataset** (tri, cadrages variés, légendes propres) reste un travail
  local et gratuit, effectué au fil des phases 1-2. C'est elle qui détermine la qualité du
  LoRA — pas la machine d'entraînement.
- À l'installation (Sprint 3) : driver AMD PyTorch preview obligatoire (le driver Adrenalin
  standard ne suffit pas), environnement Python 3.12 dédié.
