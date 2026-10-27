# Lakeview Manor - As It Should Be

This document tracks the **Lakeview Manor - As It Should Be** installation and its surrounding home / world-addition block, initially integrated under **NEFARAM 17.3.7** and carried forward to the current **NEFARAM 17.3.8 / Eleanor Stable 17.3.8** baseline.

## MO2 organization

Dedicated separator:

`41 - Homes Eleanor`

This block is intentionally kept separate from NEFARAM's stock player-home mods and related fixes / patches.

## Current exact MO2 stack

Current order inside `41 - Homes Eleanor`:

1. `Road Signs Overhaul 2.0 - Rhiven`
2. `Road Sings 2.0 - Questionable Clutter Remover (BOS) - Rhiven`
3. `Road Signs Overhaul 2.0 - Blended Roads Patch(BOS) - Rhiven`
4. `Riverwood Riverhome - SE-AE Port - Rhiven`
5. `Lakeview. Manor - As It Should Be - Rhiven`
6. `Lakeview Manor - As It Should Be - (CC) Fishing Compatibility Patch - Rhiven`
7. `Lakeview Manor - As It Should Be - FR - Rhiven`

The separator name remains `Homes Eleanor` even though the current block also contains the Rhiven road-sign additions. This reflects the actual current MO2 organization and is kept as-is for consistency with the live instance. It is not a separator name that other users must reproduce.

## Road Signs Overhaul 2.0

Installed stack:

- `Road Signs Overhaul 2.0 - Rhiven`
- `Road Sings 2.0 - Questionable Clutter Remover (BOS) - Rhiven`
- `Road Signs Overhaul 2.0 - Blended Roads Patch(BOS) - Rhiven`

The existing `Skyrim Vanilla Remix Signs` texture stack is retained.

In-game validation:

- signs are present and readable;
- tested around Riverwood / Whiterun / Falkreath routes;
- no obvious placement issue observed;
- Blended Roads compatibility appears correct in tested areas.

Status: **Validated**.

A future Rhiven texture-only French translation of road-sign destinations is tracked separately in the pre-playthrough checklist.

## Riverwood Riverhome

Installed:

- `Riverwood Riverhome - SE-AE Port - Rhiven`

### xEdit cleanup

The original plugin contained an invalid deleted override of vanilla cell `0005EAC7` (`aaaMarkers`).

The bad Riverhome override was removed while preserving the actual Riverhome cell.

After cleanup:

- xEdit `Check for Errors`: **0 errors**.

### In-game validation

Validated successfully:

- exterior integration: **OK**
- bridge / river placement: **OK**
- interior: **OK**
- no obvious terrain break observed
- no major visual conflict observed

Status: **Validated**.

No DynDOLOD / xLODGen regeneration has been performed specifically for Riverhome. Exterior generated-output regeneration remains deferred to the final stable modpack pass.

## Lakeview Manor stack

Installed stack:

1. `Lakeview. Manor - As It Should Be - Rhiven`
2. `Lakeview Manor - As It Should Be - (CC) Fishing Compatibility Patch - Rhiven`
3. `Lakeview Manor - As It Should Be - FR - Rhiven`

Purpose:

- `Lakeview Manor - As It Should Be`: main player-home overhaul.
- `(CC) Fishing Compatibility Patch`: optional compatibility layer for Creation Club Fishing content; it is required only when CC Fishing is present and the patch applies to the setup.
- `FR`: French translation layer.

## Why the construction order matters

The overhaul expects the Hearthfire house to be built in a specific sequence before its intended layout takes over. Extra furniture or the wrong wing choices can leave the construction state out of step with that layout. Use a disposable or recoverable save and follow the sequence exactly.

## Mod author procedure

The following is the mod author's process, cleaned up for readability without materially changing it.

1. Make a save game. A named save is preferable, and backing it up is even better.
   - Optional: if you have never built a Hearthfire home before, build the vanilla house with all its wings to learn the building system. When finished, revert to the save made before that practice build.
2. Download and install the mod with a mod manager. The FOMOD guides the setup. It contains two independent main files plus optional files.
3. Buy the Lakeview plot if it is not already owned. Complete the prerequisite quests given by the Jarl of Falkreath first.
4. Travel to Lakeview.
5. Choose the branch that matches the installed main file:
   - With `LKVM Main House`, follow steps 6–11.
   - With only `LKVM Cellar and Exterior`, skip directly to steps 12–14.
6. At the Drafting Table, build `Small House Layout`. Then use the Carpenter's Workbench to build all of its components: walls, floor and the other required structural parts.
7. Repeat the building process for:
   - `Main Hall`
   - `East Wing – Kitchen`
   - `North Wing – Alchemy Laboratory`
   - `West Wing – Bedroom`
8. Return to the Drafting Table and select `remodel house into entryway`.
9. Enter the house.
10. At the bedroom workbench, build only:
    - `Child's Bed & Chest x 2`
    - `Double Bed`

    > **AUTHOR-CRITICAL RESTRICTION: DO NOT BUILD ANYTHING ELSE AT THE BEDROOM WORKBENCH.**

11. Return to the Drafting Table outside and disable all workbenches.
12. Build the cellar, enter it and build only:
    - `Child Practice Dummy`

    > **AUTHOR-CRITICAL RESTRICTION: DO NOT BUILD ANYTHING ELSE IN THE CELLAR.**

13. Exit the cellar and disable its workbench.
14. Build the `Animal Pen`, `Garden`, `Apiary` and `Stable` if they have not already been built.

## Validation and status

### Author procedure

The sequence above is the procedure supplied by the mod author. The two restrictions on bedroom and cellar construction are part of that procedure, not optional Rhiven preferences.

### Maintainer validation

Fabien/Rhiven personally followed and validated this exact construction process in two separate Skyrim setups/playthroughs:

- **Nolvus**
- **NEFARAM 16**

This real-world validation supports confidence in the sequence. It does **not** automatically prove that every later customization or interaction in **NEFARAM 17.x** is identical.

## Lakeview validation constraint

Lakeview cannot yet be fully validated because normal Hearthfire gameplay progression is required before a meaningful test.

Required progression:

- complete the relevant Falkreath Jarl quest progression;
- obtain permission to purchase the Hearthfire plot;
- purchase the Lakeview Manor land;
- build the manor far enough for the modded interior / exterior setup to be tested properly.

For that reason the Lakeview stack is currently **Installed / Pending gameplay validation**, not **Validated**.

This current-baseline status is separate from the successful earlier validation of the author procedure in Nolvus and NEFARAM 16.

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

Player-home mods can modify cells, placed references and navmesh. Their right-pane plugin placement should therefore remain driven by actual records and compatibility requirements rather than by a generic personal-mod parking rule.

The MO2 left-pane separator is organizational only. Any final right-pane plugin placement should be checked against NEFARAM patches and related records if conflicts appear.

## Current status

- Dedicated separator: **YES**
- Road Signs Overhaul stack: **INSTALLED / VALIDATED**
- Riverwood Riverhome: **INSTALLED / CLEANED / VALIDATED**
- Lakeview Manor main mod: **INSTALLED**
- Lakeview CC Fishing patch: **INSTALLED** (optional / conditional for setups using Creation Club Fishing)
- Lakeview French translation: **INSTALLED**
- Lakeview author procedure: **VALIDATED IN NOLVUS AND NEFARAM 16**
- Lakeview full in-game validation: **PENDING GAMEPLAY PROGRESSION**

## Community-facing guide

For the simplified English procedure intended for NEFARAM users, see:

[Lakeview Manor - As It Should Be community guide](../12%20-%20COMMUNITY%20GUIDES/LAKEVIEW-MANOR-AS-IT-SHOULD-BE/README.md)
