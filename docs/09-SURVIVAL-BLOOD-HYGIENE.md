# 09 - Survival, blood & hygiene stack

This document records the Rhiven survival/hygiene stack added on top of **NEFARAM 17.3.6**.

The design goal is simple: keep each subsystem responsible for one job, minimize overlap, and validate the whole stack **before** starting the real playthrough.

## Architecture

- **Enhanced Blood Textures (EBT)** — environmental blood visuals
- **Just Blood - Dirt and Blood Lite** — blood on actors
- **Bathing in Skyrim - Renewed (BiSR)** — dirt, bathing and hygiene logic
- **SunHelm** — needs / survival
- **Campfire** — camping
- **Malignis Animations** — bathing animations
- **Wash Me - Renewed** — follower washing interactions

## Blood stack

### Enhanced Blood Textures 4.0

Installed as:

`Enhanced Blood Textures - Rhiven`

FOMOD choices:

- Install mode: **SPID Compatible**
- Immersive Creatures patch: **No**
- Blood Size: **Default Splatter Size**
- Wounds: **EBT - Default**
- Drips: **Default**
- Screen Blood: **Default**
- Blood color: personal visual choice

MO2 file-conflict review showed no direct conflict with Just Blood.

### Enhanced Blood Textures SE - Settings Loader

Installed as:

`Enhanced Blood Textures SE - Settings Loader (SPID Version) - Rhiven`

- Version used: **SPID 2.0.2**
- Chosen because EBT 4.0 was installed in SPID mode

### Just Blood - Dirt and Blood Lite

Stock NEFARAM mod retained.

Role:

- actor blood visuals
- kept separate from EBT environmental blood

### EBT - Just Blood Body Patch - Rhiven

Original mod:
[Enhanced Blood Textures Just Blood Just Not Enhanced Body Blood](https://www.nexusmods.com/skyrimspecialedition/mods/93414)

Purpose:

- disables EBT body blood decals
- leaves actor body blood to Just Blood
- avoids visual overlap between EBT and Just Blood

No ESP/plugin is added by this patch.

## Bathing in Skyrim - Renewed

Installed as:

`Bathing in Skyrim - Renewed - Rhiven`

Version validated: **2.7.11**

Installed in MO2 section:

`21 - Survival`

Recommended position used: near the existing wash-basin / survival mods.

### Main FOMOD choices

Texture sets:

- Male: **Zaki's SOS**
- Female: **Zaki's CBBE**

Addons:

- Base Object Swapper: **Yes**
- Description Framework: **Yes**
- SkyPatcher: **Yes**
- Widget Addon: **Yes**
- Bathing Token: **No**
- First Person Messages: **No**

Patches not used:

- Complete Alchemy and Cooking Overhaul
- Licenses - Player Oppression
- Barefoot Realism
- Barefoot Realism Tweaked

Support files:

- Source Scripts: **Yes**
- Mod Organizer support: **Yes**

### Multi-language package

Installed as:

`Bathing in Skyrim - BAIN (Multi-Language) - Rhiven`

Important note:

- the current BAIN package does **not** provide French
- localized plugin support was enabled
- language support was left at **None**
- useful as a localization-friendly base for future French translation work

## BiSR addon stack

Installed below BiSR unless noted otherwise:

1. `Zaki 8K-4K Textures for Bathing in Skyrim Renewed - Rhiven`
2. `Bathing in Skyrim - Renewed - Animal Fat and Linen - Rhiven`
3. `Bathing in Skyrim - Generic Soap Distribution - Rhiven`
4. `Bathing in Skyrim - Renewed - Seamless Soap - Rhiven`
5. `Bathing in Skyrim SE - SST MORE VISIBLE BUBBLES - Rhiven`
6. `Bathing in Skyrim - Wash Me - Rhiven`

### Zaki 8K-4K Textures

Player character is female, so the selected install was:

- Male Dirt Level: **None**
- Female Dirt Level: **Level 4 (Recommended)**

### Animal Fat and Linen

Retained as part of the BiSR crafting / washing ecosystem.

### Generic Soap Distribution

Retained for soap / wash-rag distribution.

### Seamless Soap

Renewed-specific file used:

- **Bathing in Skyrim - Renewed - Seamless Soap v1.2**

Optional effect:

- **SST MORE VISIBLE BUBBLES**
- approximately 30% more visible bubbles

The old Bathing in Skyrim SE conversion is **not** required.

### Artisan Soaps

Reviewed but **not retained** in the final stack.

Reason:

- overlaps with the soap visual layer
- Seamless Soap + More Visible Bubbles was preferred for a simpler and cleaner setup

### Wash Me - Renewed

Installed as:

`Bathing in Skyrim - Wash Me - Rhiven`

Version validated: **1.3**

FOMOD choices:

- Dialog conditions: **Any follower**
- Animation type: **NSFW**
- Basin type: **Big**

Requirements review:

- BiSR 2.7.5+: satisfied by BiSR 2.7.11
- Backported Extended ESL Support: not required on Skyrim 1.6.1170
- ConsoleUtilSSE NG: **not installed**
- NEFARAM already uses **ConsoleUtil Extended**
- Dirt and Blood full version: not required for the selected BiSR main file

## Widget Addon

Original widget used:

[Widget Addon - Keep It Clean - Bathing in Skyrim - Dirt and Blood](https://www.nexusmods.com/skyrimspecialedition/mods/34502)

Installed as:

`Widget Addon - Keep It Clean - Bathing in Skyrim - Rhiven`

FOMOD needs integration:

- iNeed: No
- Vitality Mode: No
- iWant RND: No
- **None of the above: Yes**

Reason: NEFARAM uses **SunHelm**.

### Load-order relationship

Widget Addon is placed **above** BiSR so the BiSR compatibility patch can overwrite / redirect the widget references to Bathing in Skyrim Renewed.

### Dirtiness level 5 fix

Candidate:
[Dirtiness Lvl5 Fix for Widget Addon - Bathing In Skyrim Renewed](https://www.nexusmods.com/skyrimspecialedition/mods/178194)

Current status:

- **Tracked on Nexus**
- **Not installed**
- only install if the widget disappears at dirtiness level 5 / Filthy

## Malignis Animations

Installed in:

`24 - Animations`

Position:

- bottom of the animation block

This keeps animation-related files grouped with the rest of the NEFARAM animation stack.

## Pandora

Pandora output path corrected to:

`C:\JEUX\NEFARAM\mods\Pandora Output`

Skyrim Data remains:

`C:\JEUX\NEFARAM\Game Root\Data`

Important:

- output must point to the **root of the Pandora Output mod**
- do not point to `meshes` or another subfolder
- do not write Pandora output directly into the game Data directory

### Validation

Pandora successfully detected:

- `FNIS_BiS_WashMe_List`
- `FNIS_Bathing_in_Skyrim_List`
- `FNIS_Bathing_in_Skyrim_Malignis_List`

Generation result:

- **38,349 total animations added**
- completed successfully
- no blocking error observed

## Final validation

Status: **VALIDATED**

Validated in game:

- BiSR MCM detected
- blood-related MCM/options detected
- new BiSR options visible
- animations working
- no animation error observed
- Wash Me detected by Pandora
- Malignis detected by Pandora
- stack functional in game

Plugin count after the blood + hygiene stack:

- **203 heavy plugins**

## Final decision

The stack is accepted for the future Eleanor playthrough.

The intended responsibility split is:

- **EBT = environment**
- **Just Blood = actors**
- **BiSR = hygiene**
- **SunHelm = needs**
- **Campfire = camping**

This layout is considered stable, coherent and reproducible.
