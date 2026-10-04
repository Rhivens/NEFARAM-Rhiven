# 11 - Home Eleanor

This document tracks Eleanor's dedicated player-home setup on top of **NEFARAM 17.3.6**.

## MO2 organization

Dedicated separator:

`41 - Homes Eleanor`

This block is intentionally kept separate from NEFARAM's existing player-home mods and related fixes / patches.

Current end-of-left-pane organization:

- `39 - OPTIONAL MODS`
- `40 - Female Skin Options (Enable all mods with the same [prefix] and disable the others)`
- `41 - Homes Eleanor`
- `42 - Added Mods (En attente)`
- `43 - FWMF Maps - Rhiven`
- `Overwrite`

The temporary `42 - Added Mods (En attente)` separator can be renamed later when its contents form a clear category.

## Installed Lakeview Manor stack

Current MO2 order inside `41 - Homes Eleanor`:

1. `Lakeview. Manor - As It Should Be - Rhiven`
2. `Lakeview Manor - As It Should Be - (CC) Fishing Compatibility Patch - Rhiven`
3. `Lakeview Manor - As It Should Be - FR - Rhiven`

Purpose:

- `Lakeview Manor - As It Should Be`: Eleanor's future main player home.
- `(CC) Fishing Compatibility Patch`: compatibility layer for Creation Club Fishing content.
- `FR`: French translation layer.

## Validation constraint

The home cannot be fully validated immediately.

Normal gameplay progression is required before a meaningful in-game test:

- complete the relevant Falkreath Jarl quest progression;
- obtain permission to purchase the Hearthfire plot;
- purchase the Lakeview Manor land;
- build the manor far enough for the modded interior / exterior setup to be tested properly.

For that reason the stack is currently **Installed / Pending gameplay validation**, not **Validated**.

When Lakeview becomes accessible during the real playthrough, validation should include:

- exterior placement and terrain;
- entry / exit;
- main-house interior;
- cellar;
- lighting;
- furniture / activators;
- storage;
- bathing / utility features if present;
- Creation Club Fishing compatibility;
- follower / NPC navigation if used;
- visible conflicts or misplaced objects.

## Load-order principle

Unlike self-contained outfits or SKSE-only QoL additions, a player-home overhaul can modify cells, placed references and navmesh. Its plugin position should therefore remain driven by its actual records and compatibility requirements rather than by a generic personal-mod parking rule.

The MO2 left-pane separator is organizational; any final right-pane plugin placement should be checked against NEFARAM patches and other Lakeview-related records if conflicts appear.

## Current status

- Dedicated separator: **YES**
- Main mod installed: **YES**
- CC Fishing patch installed: **YES**
- French translation installed: **YES**
- Full in-game validation: **PENDING GAMEPLAY PROGRESSION**
