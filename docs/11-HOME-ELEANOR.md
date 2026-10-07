# 11 - Home Eleanor

This document tracks Eleanor's dedicated home / nearby world-addition block on top of **NEFARAM 17.3.7**.

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

The separator name remains `Homes Eleanor` even though the current block also contains the Rhiven road-sign additions. This reflects the actual current MO2 organization and is kept as-is for consistency with the live instance.

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

- `Lakeview Manor - As It Should Be`: Eleanor's intended main player home.
- `(CC) Fishing Compatibility Patch`: compatibility layer for Creation Club Fishing content.
- `FR`: French translation layer.

## Lakeview validation constraint

Lakeview cannot yet be fully validated because normal Hearthfire gameplay progression is required before a meaningful test.

Required progression:

- complete the relevant Falkreath Jarl quest progression;
- obtain permission to purchase the Hearthfire plot;
- purchase the Lakeview Manor land;
- build the manor far enough for the modded interior / exterior setup to be tested properly.

For that reason the Lakeview stack is currently **Installed / Pending gameplay validation**, not **Validated**.

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
- Lakeview CC Fishing patch: **INSTALLED**
- Lakeview French translation: **INSTALLED**
- Lakeview full in-game validation: **PENDING GAMEPLAY PROGRESSION**
