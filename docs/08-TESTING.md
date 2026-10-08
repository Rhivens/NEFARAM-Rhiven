# 08 - Testing & validation

This file records important validation steps before the real playthrough.

## Baseline validation

### Stock NEFARAM 17.3.6

- MO2 launch: **OK**
- Game launch: **OK**
- `NEFARAM_Start` save: **OK**
- Waiting room / configuration screen: **OK**
- Clean exit without creating a gameplay save: **OK**

### Current NEFARAM 17.3.7 baseline

- Manual 17.3.6 -> 17.3.7 migration: **COMPLETED**
- MO2 launch: **OK**
- Game launch: **OK**
- Current Rhiven instance: **active on 17.3.7**

## Current tests

### Dragonborn UI

Status: **VALIDATED**

- In-game test: **OK**
- Core menus and UI: **OK**
- Existing NEFARAM UI stack: **functional**
- Dragonborn UI visual overrides: **OK**
- No blocking compatibility issue observed
- Safe to keep enabled in `ELEANOR Stable`

### Dragonborn Reskin - Skyrim Character Sheet

Status: **VALIDATED**

- In-game test: **OK**
- Character Sheet opens normally: **OK**
- Dragonborn visual style applied correctly: **OK**
- No visible layout or text issue observed
- Safe to keep enabled in `ELEANOR Stable`

### Wheeler / Perfected Wheeler

Status: **VALIDATED**

Installed stack:

- `Wheeler - Quick Action Wheel Of Skyrim - Rhiven`
- `Perfected Wheeler - Apocrypha Menu Framework - Rhiven`
- `Dragonborn - Wheeler Reskin - Rhiven`
- `Dragonborn - Wheeler Reskin Edge UI Color Options - Rhiven`

Validation:

- In-game launch: **OK**
- Wheeler opens correctly: **OK**
- Perfected Wheeler detected in SKSE Menu Framework: **OK**
- Settings panel / Mod Control Panel: **OK**
- Resize / wheel layout controls: **OK**
- Dragonborn reskin: **OK**
- Edge UI color option: **OK**
- Test binding on `Caps Lock`: **OK**
- No ESP/plugin added by the four Wheeler mods
- Final hotkey layout intentionally deferred until the real playthrough setup
- Decision: keep enabled in `ELEANOR Stable`

### Compare Equipment NG 0.3.18

Status: **VALIDATED**

- Installed in `04 - User Interface` after the Dragonborn / Wheeler reskin block
- Pure SKSE implementation: **no ESP/plugin**
- Equipment comparison windows: **OK**
- Difference indicators: **OK**
- Armor-type mismatch color warning: **OK**
- Dragonborn UI compatibility during test: **OK**
- Decision: keep enabled in `ELEANOR Stable`

### FWMF + Skyrim Paper Map by Caro Tuts

Status: **VALIDATED**

- FWMF base: `Flat World Map Framework FOMOD Lite - Rhiven` v1.9.990
- Map: `Skyrim Paper Map by Caro Tuts for FWMF - Rhiven`
- MO2 section: `43 - FWMF Maps - Rhiven`
- In-game map test: **OK**
- Paper map rendering: **OK**
- No purple map / missing texture issue observed
- Map markers and map behavior: **OK**
- Caro Tuts map adds no ESP
- FWMF plugins remain at the bottom of the plugin order, after the late NEFARAM / LOD stack
- Safe to keep enabled in `ELEANOR Stable`

### Blood + Bathing in Skyrim Renewed stack

Status: **VALIDATED**

Core design:

- EBT = environment
- Just Blood = actors
- BiSR = hygiene
- SunHelm = needs
- Campfire = camping

Validation:

- Enhanced Blood Textures 4.0 SPID: **OK**
- EBT Settings Loader SPID: **OK**
- Just Blood retained: **OK**
- EBT / Just Blood body patch: **OK**
- Bathing in Skyrim Renewed 2.7.11 MCM detected: **OK**
- Blood-related MCM/options detected: **OK**
- BiSR addon stack detected: **OK**
- Widget Addon detected and patched by BiSR: **OK**
- Malignis animations: **OK**
- Wash Me - Renewed: **OK**
- No animation error observed
- No blocking file conflict observed in the final stack
- Plugin count after stack: **203 heavy plugins**

Pandora validation:

- `FNIS_BiS_WashMe_List`: detected
- `FNIS_Bathing_in_Skyrim_List`: detected
- `FNIS_Bathing_in_Skyrim_Malignis_List`: detected
- Total animations added: **38,349**
- Generation completed successfully
- Final Pandora output isolated in the MO2 `Pandora Output` mod

Decision:

- keep the complete stack enabled in `ELEANOR Stable`
- `Dirtiness Lvl5 Fix` remains tracked only and will be installed only if the widget fails at dirtiness level 5

### Eleanor outfit block / BodySlide

Status: **PREPARED — IN-GAME VISUAL VALIDATION PENDING**

- Created separator `15.1 - Outfits Eleanor`
- Installed the current personal outfit batch
- Created dedicated `Bodyslide Output - Eleanor`
- Output path: `C:\JEUX\NEFARAM\mods\Bodyslide Output - Eleanor`
- BodySlide preset: `- Zeroed Sliders -`
- BodySlide generation: **COMPLETED**
- MME Milk Harness v3: CBBE 3BA **CM** variants selected
- Added outfit plugins are already ESL-flagged / ESP-FE
- Personal outfit plugins kept together before FWMF, preserving the late-loader / generated-plugin architecture
- Next step: in-game visual / physics validation

### Lakeview Manor - As It Should Be

Status: **INSTALLED — GAMEPLAY VALIDATION PENDING**

Installed stack:

- `Lakeview. Manor - As It Should Be - Rhiven`
- `Lakeview Manor - As It Should Be - (CC) Fishing Compatibility Patch - Rhiven`
- `Lakeview Manor - As It Should Be - FR - Rhiven`

MO2 section:

- `41 - Homes Eleanor`

Validation cannot be completed immediately because normal Hearthfire progression is required first:

- complete the required Falkreath Jarl progression;
- obtain and purchase the Lakeview Manor plot;
- build the manor far enough to access the affected areas.

When available in the real playthrough, test exterior placement, interior, cellar, lighting, activators, storage, Fishing compatibility and NPC navigation.

Decision:

- keep installed;
- do **not** mark Validated until Lakeview Manor can be tested in normal gameplay.

### Beeing Female NG 3.6.0 + Fertility Adventures Redux

Status: **TECHNICAL INTEGRATION VALIDATED — GAMEPLAY / MCM TUNING PENDING**

Installed stack:

- `Fertility Adventures Redux - Rhiven`
- `Beeing Female NG 3.6.0 - Rhiven`
- `Beeing Female NG - HUD Re-Alignment Patch - Rhiven`

BFNG FOMOD integration:

- Open Animation Replacer: **selected**
- Fertility Adventures Redux patch: **selected**
- SPID item distribution: **selected**
- P.A.I.A base patch: **selected**
- P.A.I.A Expansion patch: **selected**
- SlaveTats womb / birth-count tattoo packs: **selected**
- FMR-Immersive Effects patch: **not selected**
- RS Children child actors: **not selected**
- Creature child actors: **not selected**

Initial launch:

- BFNG 3.6.0 initialization: **OK**
- BFNG MCM registration: **OK**
- Skyrim / SKSE / PapyrusUtil checks: **OK**
- SexLab compatibility: **OK**
- Bathing in Skyrim compatibility: **OK**
- BF item distribution: **OK**
- Console: **no blocking BFNG error observed**
- Initial animation status before regeneration: `BeeingFemale Animations = NO COMPATIBILITY`

Pandora regeneration:

- `FNIS_BeeingFemale_List`: **detected**
- Total animations added: **38,367**
- Generation completed successfully
- Post-Pandora BFNG status: `BeeingFemale Animations = COMPATIBLE`

HUD Re-Alignment Patch:

- original archive inspected before installation
- preset structure compared with BFNG 3.6.0 `default.ini` / `LeftOver.ini`
- same current widget sections / key structure confirmed
- archive cleaned and repacked without the root README that confused MO2
- final path: `BeeingFemale/HUD/Align1.ini` through `Align6.ini`
- final visual preset selection: **deferred**

Design decisions for the definitive playthrough:

- stock optional `Fertility Mode`: **OFF**
- pregnancy scope: **player only**
- NPC pregnancy: **OFF**
- child output: **Gem**
- BFNG visual scaling: **BodyMorph / CBBE 3BA profile**
- SkyChild migration: **rejected for this integration**
- existing `Simple Children` stack: **kept unchanged**
- `Inflation Framework NG`: **tracked only / not installed**
- FHU / MME / BFNG morph amplitudes: tune natively in MCM first
- full MCM configuration intentionally deferred until the definitive character start and NEFARAM difficulty preset selection

Heavy-plugin count at this stage: **211**.

Decision:

- keep the BFNG / FAR stack enabled;
- translations still pending;
- do not perform final gameplay tuning on the temporary test character.


### TNTR / EET / OMNOMS trap ecosystem

Status: **TECHNICAL INITIALIZATION VALIDATED — FIELD GAMEPLAY PENDING**

Installed / integrated stack:

- `SkyPatcher - AE - Rhiven`
- `Object Impact Framework (OIF) - Rhiven`
- `Trap Needs to be Real Trap - Rhiven` — TNTR 0.74
- `EET Extra Evil Traps - Rhiven` — EET 1.2.3
- `O Skyrim Has Insane Traps - Rhiven`
- `OMNOMS Not So Obvious Mimics - Rhiven` — OMNOMS 1.3.0
- `Deadly Bear Trap - Rhiven`
- `Watch Your Step - Rhiven` — v1.2

Installation / conflict validation:

- TNTR 0.74 selected as the supported base for EET / OMNOMS: **OK**
- TNTR OAR patch: **selected**
- TNTR Nemesis-style behavior patch for Pandora: **selected**
- EET Bear Trap patch for TNTR 0.73/0.74: **selected**
- EET Snare Trap patch for TNTR 0.73/0.74: **selected**
- OMNOMS patched Mimic script: **selected**
- OMNOMS activation-text replacement: **selected**
- OMNOMS experimental vanilla-chest shader replacement: **not selected**
- OMNOMS O.S.H.I.T patch: **selected**
- OMNOMS OIF config verified to win over O.S.H.I.T after MO2 priority correction: **OK**
- SkyPatcher distribution: Magic Vendors + Spell Tomes enabled; General Vendors disabled

Initial launch / MCM validation:

- New Game test launch: **OK**
- CTD during startup / initialization: **none observed**
- obvious abnormal behavior during initialization: **none observed**
- TNTR MCM: **registered**
- TNTR: Extra Evil Traps MCM: **registered**
- TNTR: Not So Obvious Mimics MCM: **registered**

Known points to verify early in the definitive playthrough:

- trigger and escape at least one TNTR Bear Trap and Snare Trap / QTE;
- verify one OMNOMS Mimic encounter and post-encounter container / loot behavior;
- verify O.S.H.I.T and Watch Your Step trap placement without animation deadlocks;
- specifically watch Fill Her Up Baka deflation during TNTR trap animations;
- verify Devious Devices and Acheron / Practical Defeat interactions;
- perform these checks early enough that the entire TNTR stack can still be removed if a reproducible save-impacting problem appears.

Decision:

- keep enabled for now;
- do **not** mark the gameplay stack fully Validated until early real-playthrough field tests pass.

### Private Needs - Orgasm 1.11.1

Status: **VALIDATED FOR RHIVEN NATURAL-NEEDS USE**

Configuration intent:

- used for bladder / bowel simulation only;
- orgasm-related urination features intentionally disabled in MCM;
- Dynamic Bloodpool Framework not installed because puddles are not required;
- optional Dooty integration not installed;
- optional SkyrimNet integration deferred until / unless SkyrimNet is actually added later.

Initial in-game validation:

- game launch: **OK**
- mod initialization: **OK**
- bladder fullness percentage visible: **OK**
- bowel fullness percentage visible: **OK**
- chair / furniture toilet interaction: **OK**
- no CTD observed during the initial test
- functionality worked before an additional Pandora regeneration, indicating the tested functions did not depend on a missing behavior-generation pass in this setup

Notes:

- v1.11.1 represents a substantial architecture update from the previously used 1.8.3 branch, with more runtime work moved into SKSE.
- long-term checks remain sensible for equipment re-equip behavior, Devious Devices interaction and normal needs progression during the real playthrough.

Decision:

- keep enabled in the Rhiven build.

### NakedStart 1.1.0

Status: **REJECTED — NEFARAM START WORKFLOW INCOMPATIBLE**

- Plugin files were correctly installed under `SKSE\\Plugins`.
- Repeated NEFARAM start tests retained the full randomly assigned starting outfit / weapon set.
- Increasing the settle window and disabling item-menu shutdown did not change the result.
- NEFARAM starts from the supplied `NEFARAM_Start` save and then runs its Skyrim Unbound / RaceMenu / teleport workflow instead of beginning from Skyrim's normal `New Game` event.
- NakedStart is designed to arm only on a true new game, so the NEFARAM supplied-save workflow is the likely incompatibility point.

Decision:

- remove / do not retain NakedStart in the final build.

### PAMA / Prison Alternative integration

Status: **CORE BLOCK VALIDATED FOR INTEGRATION**

Current installed block:

- Next-Gen Decapitations + dedicated Sovngarde INI override
- Pama's Deadly Furniture 3.4.5 Revision 2
- Prison Alternative 2.0.3
- Pama Sovngarde Aftermath 1.0.0
- Punishment Pack 1.3.0
- Outdoor Event Pack 1.3
- Bad Ends Revived: Windhelm 1.3.0
- Rhiven Windhelm navmesh patch
- Rhiven NEFARAM ZaZ ankle-chain mesh patch
- Bad Ends Revived: Riften 1.3.2
- Bad Ends Revived: Solitude 1.8.0 Revision 2
- Rhiven Solitude Location patch
- Orkish Bounty Hunters 0.4

Validation completed:

- Deadly Furniture MCM / requirements: **OK**
- Deadly Furniture controlled test in `pamaTestZone`: **OK**
- Prison Alternative MCM / base Event Registry: **OK**
- vanilla arrest → Whiterun jail handoff: **OK**
- Whiterun vanilla cot `CivilWarCot01L` / BaseID `000E2826`: **OK**
- prison sleep / sentence progression: **OK**
- Sovngarde Aftermath handoff from PAMA: **OK**
- full Sovngarde return intentionally deferred to avoid scenario spoilers
- Bad Ends Windhelm targeted xEdit audit: **OK with dedicated Rhiven patches**
- Bad Ends Riften targeted xEdit audit: **OK, no navmesh patch required**
- Bad Ends Solitude targeted xEdit / in-game pathing audit: **OK with dedicated Location patch**
- Falkreath prison bed checked as vanilla `Bedroll01` / BaseID `00036ED3` / RefID `000EF426`
- Orkish Bounty Hunters manual ambush start: **OK**
- OBH scripted poison / KO flow: **OK**
- OBH jail outcome: **OK**
- OBH camp outcome: **OK**
- OBH escape and recapture: **OK**
- one isolated OBH recapture CTD was observed once and could not be reproduced during repeated retests

Pandora checkpoints:

- Deadly Furniture: **39,142**
- Prison Alternative: **39,184** (+42)
- Sovngarde Aftermath: **39,184** (+0)
- Punishment Pack: **39,200** (+16)
- Outdoor Event Pack: **39,200** (+0)
- Bad Ends Windhelm: **39,222** (+22)
- Bad Ends Riften: **39,252** (+30)
- Bad Ends Solitude: **39,298** (+46)
- all listed runs completed without reported Pandora errors

Windhelm xEdit validation:

- navmesh `000FC117` restored from `WindhelmSSE - Exterior NavMesh Fixes.esp`
- navmesh `0004B66C` restored from `CapitalWindhelmExpansion - SkyrimSewers.esp`
- dedicated patch ESL-flagged
- xEdit `Check for Errors`: **0 errors / 7 records**

Riften validation:

- PAMA navmesh `000429CE` intentionally kept
- Riften of Reverie does not override this navmesh
- no dedicated navmesh patch required
- minor visual overlap from a vanilla well will be handled in the definitive playthrough after positive console identification

Solitude validation:

- PAMA and Animal Research touch the same broad navmesh, but tested gameplay zones are spatially distinct
- Saffron exterior pathing / wall-lean behavior observed in game: **OK**
- no navmesh merge retained
- `PAMA - Solitude Location Patch - Rhiven.esp` restores `SolitudeLocation` on `SolitudeOrigin [00037EE9]`
- xEdit `Check for Errors`: **0 errors / 17 records**

Decision:

- keep the complete PAMA core enabled;
- treat the block as validated for integration;
- continue only with normal real-playthrough observation and the intentionally deferred full Sovngarde return test.

## Test entry template

### YYYY-MM-DD — Change tested

- **Change:**
- **Launch:** OK / KO
- **Save load:** OK / KO
- **UI / gameplay:** OK / KO
- **Conflicts observed:**
- **Result:**
- **Decision:**
