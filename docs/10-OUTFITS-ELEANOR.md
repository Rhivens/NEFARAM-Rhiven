# 10 - Eleanor outfits

This document tracks the personal outfit collection added for Eleanor on top of **NEFARAM 17.3.6**.

## MO2 organization

Dedicated separator:

`15.1 - Outfits Eleanor`

The stock `15 - Outfits` section is left intact. Personal additions are isolated in their own block for easier maintenance, testing and removal.

Dedicated generated-output mod:

`Bodyslide Output - Eleanor`

This output is placed at the bottom of the `15.1 - Outfits Eleanor` block so generated meshes can overwrite the source meshes when required.

BodySlide output path:

`C:\JEUX\NEFARAM\mods\Bodyslide Output - Eleanor`

BodySlide game data path:

`C:\JEUX\NEFARAM\Game Root\data\`

## BodySlide convention

Because NEFARAM uses OBody NG, the added outfits are built with:

- **Preset:** `- Zeroed Sliders -`
- **Body:** CBBE 3BA where available
- Generated meshes go only to `Bodyslide Output - Eleanor`

This keeps the outfit meshes neutral while OBody handles body morphs in game.

For the MME Milk Harness v3, the selected BodySlide variants are the **CBBE 3BA (CM)** variants rather than PBR.

## Installed outfit stack

Current MO2 order inside `15.1 - Outfits Eleanor`:

1. `Invicta Couture Black Rose BHUNPv4 Extra 2K - Rhiven`
2. `Invicta Couture Black Rose CBBE 3BA - Rhiven`
3. `[qdaro] Silver Witch 3BA SMP - Rhiven`
4. `DX Fetish Fashion Volume 2 SE - CBBE Physics 3BA - Rhiven`
5. `Invicta Couture Lingerie BHUNP SMP - Rhiven`
6. `Invicta Couture Lingerie CBBE 3BA - Rhiven`
7. `Chain Bikini Armor - CBBE 3BA - Rhiven`
8. `ELLE - Dark Rebel 3BA - Rhiven`
9. `Minou Aradia Bikini SE 3BAv2 - Rhiven`
10. `Aether CBBE 3BA - Rhiven`
11. `Lady Ritual CBBE 3BA - Rhiven`
12. `Bisquits Priestess of Mara - Rhiven`
13. `Forgotten Princess - CBBE 3BA - Rhiven`
14. `COCO 2B Wedding Outfit - CBBE 3BA - Rhiven`
15. `[Predator] MME Milk Harness v3 - Rhiven`
16. `Bodyslide Output - Eleanor`

## Source / conversion handling

### Invicta Couture Black Rose

The CBBE 3BA conversion uses the original BHUNPv4 package for the source assets.

Selected original package:

- **Invicta Couture Black Rose EXTRA 2K**
- one original main file only
- used as the texture / asset source
- 3BA conversion installed after it

### Invicta Couture Lingerie

The CBBE 3BA conversion likewise keeps the original BHUNP package as the source asset / texture package.

The outfit lists `Heel sound footstep sound replacement` as a requirement, but the current NEFARAM setup already uses the modern **Heels Sound - 2025 Edition** stack, so the older sound replacer was not added.

## Plugin handling

The newly added outfit plugins are already **ESL-flagged / ESP-FE**, so no additional ESL conversion pass is required.

Current Rhiven plugin-order convention:

- personal additions without a specific late-load requirement are kept together near the bottom of the normal plugin order
- they are placed **before FWMF**
- technical late-loader / generated-plugin ordering is preserved
- FWMF remains the final dedicated map block

This avoids scattering personal outfit plugins throughout the stock NEFARAM load order while keeping the late-load architecture intact.

## Current status

- Mods installed: **YES**
- Dedicated MO2 separator: **YES**
- Dedicated BodySlide output: **YES**
- BodySlide generation completed: **YES**
- Zeroed Sliders used: **YES**
- Plugins already ESL-flagged / ESP-FE: **YES**
- In-game visual validation: **PENDING**

The outfit block is ready for the next in-game validation pass.
