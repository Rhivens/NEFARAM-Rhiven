# NEFARAM-Rhiven — Animal Mansion Reborn Integration Plan

> **Status: CONFLICT AUDIT COMPLETE — RHIVEN PATCH DESIGN IN PROGRESS**
>
> This document defines the integration workflow for **Animal Mansion Reborn 1.8** in the NEFARAM-Rhiven build.
>
> The objective is not to force Animal Mansion into the load order at any cost. The goal is to determine the smallest, safest and most reproducible compatibility layer required for NEFARAM-Rhiven, while preserving the existing NEFARAM patch architecture.

---

## 1. Current known state

Previous preliminary review established the following:

- the main Animal Mansion Reborn plugin completed an xEdit Check for Errors with **0 errors**;
- the provided **Cities of the North - Falkreath** compatibility patch completed an xEdit Check for Errors with **0 errors**;
- the provided **The Great Town of Shor's Stone** compatibility patch contains an unresolved navmesh / NAVI problem and is therefore **not trusted as-is**;
- several conflicts appear to be ordinary record-winning conflicts that may be resolved by load-order placement rather than by creating unnecessary duplicate overrides;
- known areas requiring particular attention include:
  - **Shor's Stone**;
  - **Husky / MNC-related armor or race records**;
  - exterior and CELL conflicts with **Lux / NEFARAM patches / Synthesis**;
  - possible LOD implications if Animal Mansion adds or changes exterior structures.

The integration must therefore start with **load-order strategy first, patch creation second**.

---

## 2. Integration principle

Rhiven policy:

> **Prefer correct load-order placement over manual patching when the later NEFARAM patch already contains the desired final state.**

Do not immediately forward every conflict into a new Rhiven patch.

Animal Mansion should first be tested **higher in the load order**, before later environment / lighting / synthesis outputs when appropriate, so that existing NEFARAM patches can naturally win on records they already manage.

Only create a Rhiven compatibility override for conflicts that remain functionally incorrect after this placement.

---

## 3. Phase A — Baseline installation

Use a dedicated MO2 test profile or a clone of the current stable profile.

Before enabling Animal Mansion:

- back up the **MO2 left panel**;
- back up the **plugin order**;
- keep current generated outputs intact:
  - Synthesis Output;
  - xLODGen Output;
  - TexGen Output;
  - DynDOLOD Output;
  - Pandora Output;
- do **not** regenerate anything yet.

Install:

- Animal Mansion Reborn 1.8;
- its required dependencies;
- only compatibility patches that are individually validated.

Do not enable the Shor's Stone patch until its navmesh issue has been resolved or replaced.

---

## 4. Phase B — Initial xEdit audit

Load Animal Mansion and all active masters in xEdit.

### 4.1 Check for Errors

Run **Check for Errors** on:

- Animal Mansion Reborn main plugin;
- every AMR compatibility patch intended for use.

Record:

- total processed records;
- errors;
- unresolved references;
- malformed VMAD;
- broken aliases;
- NAVM / NAVI warnings;
- deleted references or navmeshes;
- unexpected FormID references to absent plugins.

Do not auto-clean based only on Check for Errors output.

### 4.2 Record categories to inspect

Review conflicts in at least these groups:

- `CELL`
- `WRLD`
- `LAND`
- `REFR`
- `ACHR`
- `NAVM`
- `NAVI`
- `STAT`
- `ARMA`
- `ARMO`
- `RACE`
- `FLST`
- `LVLI`
- `QUST`

Additional categories should be reviewed if the conflict filter shows AMR touching them.

---

## 4.3 Full conflict audit findings — 2026-10-24

A full xEdit conflict pass was completed against the current NEFARAM-Rhiven load order.

### Confirmed load-order strategy

Placing `Animal Mansion Reborn.esp` high enough for modern city, lighting and generated patches to win works as intended.

The following conflict families were repeatedly observed to resolve naturally without a Rhiven override:

- interior CELL lighting;
- image space / fog / ambient data;
- Lux / Lux COTN values;
- NEFARAM environment forwards;
- Synthesis final CELL winners;
- vanilla NPC placement where a later city overhaul already provides the correct modern position;
- AMR-added `XLRL - Location Reference` data where later plugins preserve it.

Representative examples verified during the audit include:

- Rorikstead Cowflop Farm;
- Battle-Born Farm;
- Darkwater Crossing — Verner and Annekke's House;
- Rorik's Manor;
- Salvius Farmhouse;
- Moorside Inn;
- Jorgen and Lami's House;
- Mor Khazgur — Larak's Longhouse;
- Battle-Born House;
- Hag's Cure.

These records should **not** be duplicated in the Rhiven patch.

### COTN Falkreath

`COTN -Falkreath AMR.esp` is confirmed to be functionally important.

It does more than forward CELL data: it repositions AMR-specific markers and quest triggers into the COTN Falkreath geometry, including locations such as:

- Jarl's Longhouse;
- Dead Man's Drink.

The patch also adds appropriate `XLRL` location references to several AMR markers / triggers.

Because the patch previously passed xEdit Check for Errors with **0 errors**, the current plan is:

> **retain `COTN -Falkreath AMR.esp` as a separate active compatibility patch.**

One record remains worth observing in-game:

- `DelacourtREF [00072667]` — the COTN AMR patch removes its previous `XLCN - Persistent Location` while retaining the Dead Man's Drink `XLRL`. No correction should be made without a demonstrated gameplay issue.

### MNC / Husky

Confirmed conflict:

- `HuskyBareAA [02018B35]`

AMR restores the vanilla male Husky mesh and drops the MNC female mesh assignment, while the rest of the record remains compatible.

Rhiven decision:

> preserve the MNC male and female biped model paths in a minimal override.

No wider MNC merge is currently indicated.

### Shor's Stone

The supplied `AMR The Great Town of Shor's Stone Patch.esp` remains **disabled** for the final setup because of its unresolved NAVI / navmesh issue.

However, the patch is useful as a reference because it contains valid-looking repositioning work for AMR-specific content in Sylgja's redesigned house.

The following records were identified as useful compatibility data candidates:

- `CommonBedDouble01 [0009F417]`
- `SylgjaRef [000C3A46]`
- `AMR_SylgjaTalkSpot [AE5D2E10]`
- `AMR_SylgjaSexSpot [AE5D2E11]`
- `AMR_SylgjaFSpot [AE5D2E12]`
- `AMR_SylgjasDog "Bandit" [AE5DD196]`
- `defaultSetStageTRIGSpecificActor [AE5D2E20]`
- `DogLayingDownIdleMarker [AE5DD197]`

These should be reconstructed into the Rhiven patch from the final Shor's Stone geometry rather than copied blindly together with the broken navmesh data.

A persistent exterior door reference also exposes a navmesh door link:

- `REFR [000177DE]`
- `XNDP - Navmesh Door Link`
- target `NAVM [00106C48]`
- teleport marker triangle `464`

This record is **navmesh-sensitive** and must not be copied mechanically.

### Dialogue topics

AMR modifies several vanilla dialogue topics by extending their INFO order.

Three DIAL records require a dedicated merge review because later NEFARAM / dialogue plugins appear to drop AMR-added INFO entries:

- `DGCrimeForcegreetTopic [000267DE]`
- `DGCrimeWantedTopic [0002A37F]`
- `OfferServicesTopic [00076FBB]`

The correct solution is **not** to force the whole AMR DIAL record to win.

The final Rhiven patch should preserve the final winner's dialogue structure while restoring only the AMR INFO entries that are actually missing.

By contrast, INFO records that differ only because AMR or another mod restores English text over French Skyrim strings are a **translation issue, not a compatibility issue**, and belong in the later French translation phase.

### Worldspace / LOD

AMR contains exterior worldspace content and at least one visible `LAND` record under:

`WhiterunWorld -> WhiterunWindDistrict02`

The existence of the `LAND` override alone is not sufficient to mandate xLODGen. The record still needs a direct comparison to determine whether it contains meaningful terrain changes or is effectively identical / negligible.

Current LOD decision therefore remains:

- if the LAND record is meaningful -> `xLODGen -> TexGen -> DynDOLOD`;
- if the LAND record is not meaningful but exterior statics need LOD -> `TexGen -> DynDOLOD`;
- do not regenerate until the final patch and Synthesis output are complete.


---

## 5. Phase C — Load-order placement test

### Goal

Determine how many apparent conflicts disappear simply by placing Animal Mansion before the existing NEFARAM finalization layers.

### Procedure

1. place Animal Mansion before late NEFARAM environment / patch outputs where possible;
2. keep required direct AMR compatibility patches after Animal Mansion;
3. keep generated patches in their existing positions for this first comparison;
4. reload the full load order in xEdit;
5. apply conflict filters;
6. compare the final winning records.

### Expected outcome

Some conflicts in:

- CELL lighting;
- image space;
- acoustic space;
- water;
- weather-linked cell values;
- object bounds or environment forwarding;

may already be correctly resolved because later NEFARAM / Lux / Synthesis patches win.

These records should **not** be copied again into a Rhiven patch unless the final winning state is actually incorrect.

---

## 6. Phase D — Shor's Stone investigation

Shor's Stone is currently the most important compatibility area.

### Known concern

The supplied AMR patch for **The Great Town of Shor's Stone** previously showed an unresolved **NAVI / navmesh-related reference**.

### Required checks

Inspect:

- every AMR-modified `NAVM` in Shor's Stone;
- corresponding `NAVI` entries;
- deleted navmeshes;
- replaced navmeshes;
- triangle / edge connections if required;
- door links;
- teleport markers;
- persistent references connected to the edited navmesh;
- NPC placement and sandbox packages;
- beds / furniture moved by The Great Town of Shor's Stone;
- Sylgja;
- Odfel;
- any vanilla references restored or repositioned by AMR.

### Rule

Do not copy the broken supplied patch blindly.

If a navmesh conflict must be resolved:

> build a new dedicated Rhiven compatibility patch from the actual final NEFARAM world state.

### In-game validation

Test Shor's Stone with:

- NPC pathing;
- door entry / exit;
- followers;
- combat;
- wait / sleep cycles;
- AMR quest actors if present;
- travel to and from the settlement.

Watch for:

- NPCs stuck in place;
- actors walking into walls;
- followers unable to enter / leave;
- broken door transitions;
- sudden actor teleport;
- CTD on cell transition.

---

## 7. Phase E — COTN Falkreath

The existing **Cities of the North - Falkreath** AMR patch previously passed xEdit Check for Errors.

This does not automatically prove functional compatibility.

Verify:

- CELL ownership / lighting;
- doors and teleport links;
- persistent references;
- furniture;
- navmesh adjacency;
- AMR quest markers;
- exterior placement;
- conflicts with COTN Falkreath Lite / patch collection;
- Lux / Lux Orbis / Lux Via winners.

If all final winners are correct, retain the supplied patch without unnecessary Rhiven overrides.

---

## 8. Phase F — MNC / Husky conflict

A previous review identified a conflict involving the AMR Husky-related record and the More Nasty Critters / NEFARAM creature stack.

Inspect:

- AMR Husky ARMA / ARMO / race-related records;
- MNC winning records;
- skeleton / mesh paths;
- slot masks;
- additional races;
- sex / creature framework expectations;
- any later NEFARAM merge or patch.

Decision rule:

- preserve the record required by the current MNC / creature framework unless AMR genuinely depends on its own version;
- avoid replacing modern MNC mesh / skeleton assignments with older AMR data.

If AMR requires only a subset of its original Husky changes, forward only that subset into a Rhiven override.

---

## 9. Phase G — CELL and worldspace conflict audit

For every AMR exterior or interior CELL touched by late NEFARAM patches, compare:

- ownership;
- encounter zone;
- lighting template;
- image space;
- acoustic space;
- water;
- sky / weather settings;
- music type;
- location;
- persistent references;
- placed objects;
- enable parents;
- XESP;
- XOWN;
- linked references.

The goal is to distinguish:

1. **AMR intentional placement changes**
2. **old vanilla values carried forward by AMR**
3. **later NEFARAM / Lux corrections that should win**

Only category 1 normally needs preservation from AMR.

---

## 10. Phase H — Synthesis

Do **not** regenerate Synthesis during the early audit.

First determine the intended final Animal Mansion load-order position and any required Rhiven patches.

Once Animal Mansion is accepted into the build:

1. enable the final AMR plugin set;
2. place AMR and compatibility patches in their final positions;
3. rebuild any manual Rhiven compatibility patch;
4. **rerun Synthesis**;
5. compare the newly generated Synthesis output against the previous one;
6. re-open xEdit and confirm the final winners.

Reason:

> the existing Synthesis output was generated without Animal Mansion in its final load-order position and should not be treated as authoritative after AMR integration.

---

## 11. Phase I — LOD decision tree

Do not regenerate the complete LOD chain automatically.

First inspect whether Animal Mansion modifies:

- `LAND` records;
- terrain height;
- landscape textures;
- large exterior statics;
- buildings visible at distance;
- trees;
- worldspace object placement.

### If AMR changes only interiors

No xLODGen / TexGen / DynDOLOD regeneration is required.

### If AMR adds exterior buildings or large statics but does not alter terrain

Expected final regeneration:

> **TexGen → DynDOLOD**

### If AMR modifies LAND / terrain

Expected final regeneration:

> **xLODGen → TexGen → DynDOLOD**

Before generating LOD, Synthesis and manual compatibility patches must already be in their intended final state.

---

## 12. Phase J — Navmesh validation rules

Any AMR compatibility patch touching navmesh must be treated as high-risk.

Check for:

- deleted navmeshes;
- NAVM FormID changes;
- NAVI entries pointing to missing navmeshes;
- overlapping replacement navmeshes;
- cell-border edge connections;
- doors whose teleport destinations no longer align with reachable navmesh;
- old navmesh records from vanilla carried into redesigned settlements.

Do not solve navmesh issues by simply changing load order if two mods physically redesign the same navigable space.

Where required, rebuild compatibility in Creation Kit / appropriate navmesh workflow and verify again in xEdit.

---

## 13. Phase K — Minimal Rhiven patch policy

### Current patch candidate set

At the end of the conflict audit, the Rhiven patch is expected to stay deliberately small.

Confirmed / likely candidates:

- 1 MNC/Husky armor-addon override;
- 8 Shor's Stone placement/location records reconstructed from the safe parts of the supplied patch;
- 3 dialogue-topic merges if the AMR INFO entries are confirmed missing from the final winners;
- any strictly necessary Shor's Stone door/navmesh compatibility record only after navmesh validation.

This candidate list is provisional until the dialogue INFO chains and the Shor's Stone navmesh dependency are fully verified.



Create an `Animal Mansion Reborn - Rhiven Patch.esp` only if necessary.

The patch should contain **only** records that cannot be resolved safely by:

- load-order placement;
- existing official / community AMR patches;
- later NEFARAM patches;
- Synthesis regeneration.

Preferred patch contents:

- specific Shor's Stone compatibility records;
- required MNC / Husky forwarding;
- isolated CELL / REFR fixes;
- corrected door / teleport / ownership records;
- any proven navmesh compatibility work.

Avoid broad forwarding of whole CELL records unless required.

---

## 14. Phase L — In-game smoke tests

Use a disposable test save first.

### Core AMR

- [ ] Animal Mansion starts correctly
- [ ] quest progression begins normally
- [ ] quest NPCs exist
- [ ] dialogue works
- [ ] scenes start
- [ ] transitions between AMR locations work
- [ ] no obvious missing assets
- [ ] no repeatable CTD

### World compatibility

- [ ] Falkreath exterior
- [ ] Falkreath interiors used by AMR
- [ ] Shor's Stone exterior
- [ ] Shor's Stone interiors
- [ ] NPC pathing
- [ ] follower pathing
- [ ] doors / teleport markers
- [ ] combat near modified areas
- [ ] fast travel into modified areas

### Framework compatibility

- [ ] SexLab scenes
- [ ] creature scenes where relevant
- [ ] MNC creature behavior
- [ ] defeat stack remains functional
- [ ] followers recover normally
- [ ] no stuck animation state

---

## 15. Final integration order

Only after all preceding checks pass:

1. finalize AMR plugin placement;
2. finalize AMR compatibility patches;
3. create / finalize Rhiven AMR patch if required;
4. rerun Synthesis;
5. re-check xEdit winners;
6. determine whether xLODGen is required;
7. run TexGen if required;
8. run DynDOLOD if required;
9. final xEdit verification;
10. final in-game smoke test;
11. update NEFARAM-Rhiven documentation;
12. publish compatibility notes / patch if appropriate.

---

## 16. Stop conditions

Pause the integration if any of the following are reproducible:

- unresolved NAVI / NAVM references;
- broken Shor's Stone pathing;
- persistent CTD entering an AMR-modified cell;
- AMR requires overwriting critical modern MNC creature records without a safe compatibility solution;
- major worldspace redesign conflict requiring extensive navmesh reconstruction;
- Synthesis produces incompatible final winners that cannot be cleanly isolated;
- AMR quest progression breaks under the NEFARAM environment stack.

The project should remain a compatibility effort, not a reconstruction of Animal Mansion itself.

---

## 17. Intended outcome

Best-case result:

> **Animal Mansion Reborn positioned early enough that NEFARAM / Lux / Synthesis naturally retain their intended environment data, with only a very small Rhiven compatibility patch for the genuinely incompatible records.**

This is preferable to forwarding dozens of records into a large monolithic patch.

The final decision will be based on reproducible xEdit and in-game evidence, not on conflict count alone.
