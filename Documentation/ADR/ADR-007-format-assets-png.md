# ADR-007 — Assets officiels conservés en PNG d'origine

**Statut :** Acté — Juillet 2026

## Contexte

ComfyUI embarque nativement le **workflow complet** (graphe de nœuds, prompt, seed,
modèle, paramètres) dans les métadonnées des PNG qu'il génère. Un PNG d'origine est donc
auto-documenté : le glisser dans ComfyUI recharge le workflow exact qui l'a produit.

Toute réexportation (conversion JPG, retouche enregistrée par-dessus, compression)
détruit ces métadonnées.

## Décision

- Tout asset officiel est conservé dans son **PNG d'origine, jamais réexporté**.
- Les besoins de diffusion (miniatures YouTube, overlays, Foundry, web) passent par le
  dossier `Exports` : on y produit des copies converties/redimensionnées, l'original
  reste intact dans `Assets_officiels`.
- Toute retouche manuelle d'un asset produit une **nouvelle version** (v1.1), l'original
  étant conservé ; la retouche est notée dans le nom ou un fichier d'accompagnement.

## Conséquences

- Chaque asset du patrimoine est reproductible et traçable gratuitement, sans discipline
  documentaire supplémentaire.
- La distinction `Assets_officiels` (originaux intouchables) / `Exports` (copies jetables,
  regénérables) devient une règle stricte de l'arborescence.
