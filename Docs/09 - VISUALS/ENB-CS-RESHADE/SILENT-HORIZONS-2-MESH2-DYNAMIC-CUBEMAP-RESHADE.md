# Configuration graphique retenue — SH2, MESH2, Dynamic Cubemap et ReShade

## Statut

**Sélectionnée, installée et fonctionnelle sur NEFARAM-Rhiven 17.3.8.** La chaîne graphique retenue est :

> **Silent Horizons 2 → MESH2 ENB → ENB Dynamic Cubemaps → ReShade**

Les éventuelles anomalies découvertes pendant la partie définitive seront traitées au cas par cas ; elles ne constituent plus une phase de sélection graphique dans la roadmap.

## Architecture retenue

- **Silent Horizons 2 Universal Core 1.13** reste la base ENB.
- **MESH2 ENB - Max's Edited Silent Horizons 2 1.2.1** est intégré sélectivement : les helpers et réglages utiles ont été repris sans écraser en bloc la structure moderne de SH2 1.13.
- **ENB Dynamic Cubemaps 1.01** est installé après `Quality CubeMaps - HD Cube Maps` afin de gagner les conflits globaux de cubemaps.
- **ReShade 6.8.0 Full Add-on Support** fonctionne à côté d'ENB via `dxgi.dll`, tandis qu'ENB conserve `d3d11.dll`.
- Le preset ReShade retenu est **Sswaye LUT13** avec `DPX.fx`, `Clarity.fx` et `LUT13.fx`.

## Réglages et choix conservés

- MESH2 reprend de façon ciblée les réglages utiles pour les yeux, le SSS de la peau, AO/SSIL, IBL, Complex Grass, Complex Material, Dynamic Cubemap et une partie du réglage de l'eau.
- Valeurs structurelles conservées depuis SH2 1.13 :
  - `EnableDepthOfField=false` ;
  - `EnableLens=false` ;
  - `EnablePrepass=false` ;
  - `EnableLODShadow=true` ;
  - `EnableMultipleWeathers=true`.
- Le fichier généré `Shaders/Features/TerrainHelper.ini` est isolé dans le mod MO2 `MESH2 - TerrainHelper Config`, actif uniquement avec la variante MESH2.
- `NEFARAM Patches` reste gagnant sur `chrome_e.dds`, `glacierice_e.dds` et `ore_obsidian_e.dds`.
- Le réglage SH2 documenté **Interior – Exposure (in EVs) = +0.50** est conservé.

## Sauvegarde et retour arrière

- **ENB and ReShade Manager Set 3** : `SH2 + ReShade Sswaye LUT13`, référence de retour arrière.
- **Set 4** : variante active `SH2 + ReShade LUT13 + MESH2`.

La configuration Community Shaders testée séparément n'a pas été retenue. Ne pas reprendre cette migration sans nouveau besoin explicite.

## Validation observée

- Les comparaisons visuelles ont retenu MESH2 malgré un coût GPU modéré accepté ; le relevé ponctuel documenté était d'environ **63,1 FPS avec MESH2** contre **70,7 FPS avec SH2** sur la scène utilisée.
- ENB Dynamic Cubemaps a été testé en jeu sans yeux anormaux, matériaux aberrants ni reflets visiblement cassés.
- La persistance des réglages et le retour arrière par le Set 3 ont été vérifiés.

Ces mesures sont des observations de la configuration testée, pas un benchmark général.

## Références

- [Silent Horizons 2](https://www.nexusmods.com/skyrimspecialedition/mods/99398)
- [Étude historique ENB vers Community Shaders / NAT Effect 11](NEFARAM_Guide_ENB_vers_Community_Shaders_NAT_Effect_11.md)
