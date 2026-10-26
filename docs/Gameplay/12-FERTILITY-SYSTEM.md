# 12 - Fertility system

This document records the Rhiven fertility / pregnancy architecture for **NEFARAM 17.3.6**.

## Goal

Use **Beeing Female NG** as the primary fertility framework because its cycle system and HUD are preferred over the stock optional Fertility Mode, while keeping the integration conservative and compatible with the existing NEFARAM SexLab / animation / BodyMorph stack.

## Installed stack

- `Fertility Adventures Redux - Rhiven`
- `Beeing Female NG 3.6.0 - Rhiven`
- `Beeing Female NG - HUD Re-Alignment Patch - Rhiven`

Stock optional `Fertility Mode` remains disabled.

## BFNG FOMOD choices

Selected:

- Open Animation Replacer
- Fertility Adventures Redux patch
- SPID item distribution
- P.A.I.A base patch
- P.A.I.A Expansion patch
- SlaveTats womb / birth-count tattoo packs

Not selected:

- FMR-Immersive Effects
- RS Children child actors
- Creature child actors

## Child system policy

NEFARAM currently uses **Simple Children**, not RS Children.

No migration to SkyChild / RS Children is part of this project. Previous experience with fertility mods showed that child-actor systems can add unwanted complexity and instability.

Planned player birth output:

- **Gem**

This avoids persistent child actors and population growth while preserving the pregnancy / birth loop.

The BFNG creature-child addon is therefore not required. Creature conception, if later enabled, is controlled separately by BFNG MCM settings such as creature sperm / lore-friendly rules.

## NPC pregnancy policy

Planned configuration:

- Player pregnancy: **enabled**
- NPC pregnancy: **disabled**

This is an intentional performance / complexity choice carried over from previous large modpack playthroughs.

## BodyMorph strategy

Primary plan:

- BFNG visual scaling type: **BodyMorph**
- BFNG profile: **CBBE 3BA**

NEFARAM also includes systems such as:

- SexLab Fill Her Up Baka Edition
- Milk Mod Economy

These systems may apply morphs at the same time. The first approach is **not** to add another framework layer, but to tune each mod's MCM amplitudes conservatively.

`Inflation Framework NG` is tracked on Nexus as a reserve option only. It will be reconsidered if the native BFNG / FHU / MME configuration produces a reproducible morph-coexistence issue that cannot be solved through MCM tuning.

## HUD

The HUD Re-Alignment addon was inspected before installation.

BFNG 3.6.0 provides:

- `BeeingFemale/HUD/default.ini`
- `BeeingFemale/HUD/LeftOver.ini`

The addon adds:

- `BeeingFemale/HUD/Align1.ini`
- `Align2.ini`
- `Align3.ini`
- `Align4.ini`
- `Align5.ini`
- `Align6.ini`

The preset structure was compared against the current BFNG 3.6.0 HUD files and found compatible.

The original addon archive was repacked without its root `README.txt` so MO2 accepts the intended directory structure cleanly.

Final preset choice remains an in-game configuration task.

## Existing integrations

The current NEFARAM-Rhiven stack already provides the main BFNG ecosystem requirements / companions used here, including:

- SexLab Framework
- SkyUI
- PapyrusUtil
- Address Library
- powerofthree's Papyrus Extender
- SPID
- P.A.I.A
- P.A.I.A Expansion
- SlaveTats / SlaveTatsNG
- Bathing in Skyrim Renewed

The P.A.I.A patches shipped by BFNG are allowed to win the relevant OAR configuration conflicts.

## Pandora

Immediately after BFNG installation, the BFNG System page showed its animation component as incompatible.

Pandora was regenerated and detected:

- `FNIS_BeeingFemale_List`

Result:

- **38,367 total animations added**
- generation completed successfully
- after relaunch: **BeeingFemale Animations = COMPATIBLE**

## Validation status

Technical validation completed:

- BFNG initialized correctly
- MCM registered
- SexLab compatibility detected
- Bathing in Skyrim compatibility detected
- BF item distribution operational
- Pandora integration operational
- no blocking BFNG console error observed

Still pending:

- French translation work
- definitive HUD preset
- pregnancy probabilities / cycle duration
- creature-fertility policy
- final BodyMorph amplitudes
- FHU / MME coexistence tuning
- full pregnancy / birth gameplay test

These settings will be done only after the complete NEFARAM-Rhiven build is finished, translations are complete, the definitive playthrough is created and the NEFARAM difficulty preset is selected.

## Current decision

**Keep the BFNG / FAR stack.**

Technical integration is validated; gameplay configuration is intentionally deferred.
