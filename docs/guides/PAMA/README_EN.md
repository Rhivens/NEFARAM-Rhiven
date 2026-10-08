# PAMA Integration — Prison Alternative / NEFARAM-Rhiven (EN)

> 🇬🇧 **English version** — French version: [README.md](README.md)
>
> **Status: PAMA core block installed and validated for integration into NEFARAM-Rhiven**
>
> The full PAMA core is now installed and the main targeted xEdit audits and in-game tests have been completed. The few remaining items are long-term / real-playthrough observations and do not currently block integration.

## Position relative to stock NEFARAM

Stock NEFARAM uses generic **Added Mods** separators near the lower part of the MO2 left pane.

The Rhiven setup keeps that principle, but the personal section has been reorganized and **numbered** so that the structure stays readable and reproducible.

The PAMA ecosystem is grouped in its own dedicated separator:

`44 - PRISON PAMA SYSTEM`

This separator does **not** exist in stock NEFARAM. It is part of the Rhiven organization layered on top of **NEFARAM 17.3.7**.

### Logical order used for the PAMA block

1. Next-Gen Decapitations - Sovngarde INI - Rhiven
2. Pama's Deadly Furniture 3.4.5 Revision 2
3. Prison Alternative 2.0.3
4. Pama Sovngarde Aftermath 1.0.0
5. Punishment Pack 1.3.0
6. Outdoor Event Pack 1.3
7. Bad Ends Windhelm 1.3.0
8. Rhiven Windhelm patches
9. Bad Ends Riften 1.3.2
10. Bad Ends Solitude 1.8.0 Revision 2
11. PAMA - Solitude Location Patch - Rhiven
12. Orkish Bounty Hunters 0.4

This mainly describes the **MO2 left-pane / functional architecture**. Do not blindly copy it into the right-pane plugin order without checking masters and winning overrides.

## Goal

The purpose of this work is to add a coherent PAMA / Prison Alternative ecosystem to NEFARAM-Rhiven while preserving the existing NEFARAM architecture whenever possible.

Core components retained:

1. **Pama's Deadly Furniture 3.4.5 Revision 2**
2. **Prison Alternative - A modular Prison System 2.0.3**
3. **Pama Sovngarde Aftermath 1.0.0**
4. **Prison Alternative - Punishment Pack 1.3.0**
5. **Prison Alternative - Outdoor Event Pack 1.3**
6. **Bad Ends Revived: Windhelm 1.3.0**
7. **Bad Ends Revived: Riften 1.3.2**
8. **Bad Ends Revived: Solitude 1.8.0 Revision 2**
9. **Orkish Bounty Hunters 0.4**

## Functional architecture

```text
Pama's Deadly Furniture
        ↓
Prison Alternative
        ↓
Pama Sovngarde Aftermath
        ↓
Punishment Pack / Outdoor Event Pack / Bad Ends
        ↓
Orkish Bounty Hunters
```

- **Deadly Furniture** provides the technical layer for lethal and non-lethal devices.
- **Prison Alternative** is the central prison framework and event registry.
- **Sovngarde Aftermath** provides continuity after some PAMA executions.
- **Punishment / Outdoor / Bad Ends** add prison and regional events.
- **Orkish Bounty Hunters** provides a dynamic route into arrest / imprisonment.

## Important dependencies already present in NEFARAM-Rhiven

The build already includes the important foundations used by this stack:

- SKSE
- SkyUI
- SexLab Framework
- ZaZ Animation Pack
- powerofthree's Papyrus Extender
- Pandora
- ConsoleUtil Extended
- Acheron - Death Alternative
- Practical Defeat Reanimated
- Devious Devices
- Troubles of Heroine
- Simple Slavery / Simple Slavery Rebuild

## Next-Gen Decapitations

Next-Gen Decapitations is strongly recommended by Deadly Furniture and required by Sovngarde Aftermath.

In the Rhiven setup, the original mod remains in the SFW additions block and a dedicated MO2 override is used for the Sovngarde-specific configuration:

`Next-Gen Decapitations - Sovngarde INI - Rhiven`

Settings:

```ini
[Misc]
iCanBeResurrected = 2
bAdvancedNPCMaintenance = 0
```

This keeps the original mod untouched and isolates the PAMA-specific configuration.

## Compatibility notes

### Devious Devices

PAMA treats Devious Devices as a **soft incompatibility** in several places.

Having DD installed can be fine, but problems become much more likely if the player is actively wearing DD restraints while a PAMA arrest / prison / event tries to equip and control its own restraints.

Practical rule for testing:

- keep DD installed;
- avoid active DD restraints during first PAMA tests;
- if a real-playthrough problem occurs, reproduce it with the exact restraint state before changing anything.

### Devious Cursed Loot

DCL is not part of this build and is intentionally not added to the PAMA stack.

### Acheron / defeat frameworks

Prison Alternative can coexist with defeat systems.

Orkish Bounty Hunters is especially interesting because it uses its own scripted poison / knockout mechanism instead of reducing player health to zero. In testing, this avoided Acheron / Practical Defeat interception and allowed OBH to keep control of its own defeat sequence.

### Random scene mods

PAMA documentation warns that mods which start random scenes at the wrong time can interrupt PAMA events.

This remains something to watch during the real playthrough rather than a confirmed incompatibility in the current build.

### Fill Her Up Baka

Outdoor Event Pack documentation mentions that badly timed deflation can produce visual issues during animations.

No blocking issue has been observed so far, but this remains a real-playthrough observation point.

## Windhelm audit

Bad Ends Windhelm was installed and audited against the current NEFARAM-Rhiven Windhelm stack.

### Navmesh conflicts found

Two PAMA navmeshes were found to be older / effectively vanilla-like compared with the current winning NEFARAM setup:

- `000FC117` — WindhelmBridge04
- `0004B66C` — WindhelmCandlehearthHallExterior

The intended winners are:

- `WindhelmSSE - Exterior NavMesh Fixes.esp` for `000FC117`
- `CapitalWindhelmExpansion - SkyrimSewers.esp` for `0004B66C`

A dedicated ESL-flagged patch was created:

`PAMA - Windhelm Navmesh Patch - Rhiven.esp`

Bad Ends Windhelm was added as an explicit master.

xEdit Check for Errors:

- **0 errors**
- **7 records**

### ZaZ ankle-chain mesh conflict

Bad Ends Windhelm also shipped an older copy of:

`meshes\ZaZ-UltimateDataPack\ZaZ - HDT\ZaZAnkleChainsRagdolls_1.nif`

The current NEFARAM-patched version is intentionally restored after PAMA with:

`PAMA - NEFARAM ZaZ Ankle Chains Patch - Rhiven`

## Riften audit

Bad Ends Riften 1.3.2 was installed and checked against the current build, including Riften of Reverie.

Results:

- Pandora total: **39,252** animations (**+30**)
- no notable MO2 file conflict
- the main PAMA navmesh involved is `000429CE` in `RiftenCityNorth`
- Riften of Reverie does not override this navmesh
- PAMA's navmesh extension is consistent with its scaffold / execution layout
- **no navmesh compatibility patch is required**

### Minor visual issue

A vanilla well clips through the PAMA scaffold platform.

Current decision:

- do not create a one-object patch for this;
- during the definitive playthrough, positively identify the well reference in console and use `disable`.

This is treated as a minor visual cleanup, not a structural incompatibility.

## Solitude audit

Bad Ends Solitude 1.8.0 Revision 2 was installed and audited in `SolitudeWorld`.

Results:

- Pandora total: **39,298** animations (**+46**)
- the vanilla execution area is reused cleanly
- PAMA and `Animal_Research.esp` both touch navmesh `000CAD79`
- their actual gameplay areas are spatially distinct
- Saffron was observed in-game leaving the inn, walking outside, using her wall-lean marker and returning normally
- decision: **do not merge the navmeshes**

A navmesh merge would add unnecessary risk when no functional pathing problem is currently observed.

### Solitude Location fix

PAMA's winning `SolitudeOrigin [00037EE9]` cell record dropped:

`XLCN - Location = SolitudeLocation [00018A5A]`

A minimal ESL-flagged patch was created:

`PAMA - Solitude Location Patch - Rhiven.esp`

Its purpose is only to restore the missing location assignment while preserving the PAMA-winning cell data.

xEdit Check for Errors:

- **0 errors**
- **17 records**

## Orkish Bounty Hunters 0.4

OBH was tested directly through its MCM debug controls.

### Validated paths

- manual ambush start: **OK**
- immediate hunter spawn: **OK**
- combat: **OK**
- scripted poison accumulation: **OK**
- unconsciousness / KO: **OK**
- jail outcome: **OK**
- camp outcome: **OK**
- camp escape: **OK**
- recapture: **OK**
- severe / execution aftermath after recapture: **observed and working**

The important compatibility point is that OBH's poison caused the defeat without driving player health to zero, so the normal Acheron / Practical Defeat path did not take over.

### Isolated CTD

One CTD occurred during a recapture sequence after an escape.

The crash log pointed to a `TESObjectREFR` / Papyrus `EnableFunctor` operation on an invalid reference.

However:

- the same sequence was repeated several times;
- the CTD did **not** reproduce;
- recapture subsequently worked;
- the execution aftermath also triggered correctly.

Current classification:

**isolated non-reproducible CTD — monitor during the real Eleanor playthrough, but do not patch pre-emptively.**

## Pandora checkpoints

Observed animation totals during installation:

- Deadly Furniture: **39,142**
- Prison Alternative: **39,184** (+42)
- Sovngarde Aftermath: **39,184** (+0)
- Punishment Pack: **39,200** (+16)
- Outdoor Event Pack: **39,200** (+0)
- Bad Ends Windhelm: **39,222** (+22)
- Bad Ends Riften: **39,252** (+30)
- Bad Ends Solitude: **39,298** (+46)

All listed Pandora generations completed without a reported blocking error.

## Core validation summary

### Deadly Furniture

- MCM / requirements detected: **OK**
- `coc pamaTestZone`: **OK**
- non-lethal furniture flow: **OK**
- controlled lethal guillotine test: **OK**
- no CTD during the tested execution

### Prison Alternative

- MCM: **OK**
- Event Registry: **OK**
- vanilla arrest → Whiterun jail: **OK**
- prison sleep / sentence progression: **OK**
- Whiterun vanilla cot works:
  - EditorID `CivilWarCot01L`
  - Base FormID `000E2826`
  - RefID `0009DC89`

Falkreath prison bed was also checked and appears to be the vanilla:

- EditorID `Bedroll01`
- Base FormID `00036ED3`
- RefID `000EF426`

This supports a **per-prison validation** approach rather than blindly replacing vanilla prison beds.

### Sovngarde Aftermath

- MCM: **OK**
- lethal PAMA execution → Sovngarde transfer: **OK**
- no CTD during the tested decapitation / transition
- full return to Tamriel intentionally deferred to avoid spoiling the scenario

Still to validate later:

- completion of the Sovngarde scenario
- return to Tamriel
- correct head restoration with `iCanBeResurrected = 2`

## Optional PAMA modules reviewed but not part of the core block

### Pama's Permanent Crucifixes 2.0

Optional standalone content with strong persistence. Not required for the Prison Alternative architecture.

### Pama's Interactive Beatup Module 2.9

Optional punishment / whipping framework. Interesting, but not required for the current prison stack.

### Pama's Interactive Gallows 3.0

Optional standalone gallows system. Functionally overlaps with Deadly Furniture for the current use case.

### Furniture Alignment Correction for NPCs 4.0.0

Technical no-ESP resource. Kept as a possible troubleshooting tool if a specific furniture alignment issue appears.

## Current conclusion

The **complete planned PAMA core is installed and accepted for integration** in NEFARAM-Rhiven.

The main remaining items are deliberately deferred rather than blocked:

- full Sovngarde → Tamriel completion / head restoration;
- long-term observation during Eleanor's real playthrough;
- DD interaction only if active restraints are actually involved;
- investigate the OBH recapture CTD only if it becomes reproducible.

The current philosophy is conservative:

**do not rebuild working NEFARAM systems unnecessarily, and do not create speculative patches for issues that cannot be reproduced.**
