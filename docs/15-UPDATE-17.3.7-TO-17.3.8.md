# 15 - Update NEFARAM 17.3.7 -> 17.3.8

> **TECHNICAL MIGRATION COMPLETE — translation/customization pass still in progress**  
> Prepared: 18 October 2026  
> Last updated: 21 October 2026  
> Installation: customized **NEFARAM-Rhiven**, manual upgrade only.

This document tracks the controlled migration of the customized **NEFARAM-Rhiven** installation from the validated **17.3.7** baseline to official **17.3.8**. It follows [the preceding migration procedure](14-UPDATE-17.3.6-TO-17.3.7.md).

The migration is being performed only in the dedicated MO2 test profile **`Eleanor 17.3.8 TEST`**. The validated profiles **`Eleanor Stable`** and **`Eleanor Stable - PRE 17.3.8`** remain the rollback references.

## Official 17.3.8 announcement

NEFARAM announces **save compatibility**. The update aims to make the list installable again and includes:

- Added **RaceMenu Portraits**.
- Added **Skyrim Performance Solution** as an optional mod **enabled by default**.
- Added **Serana Revamped — Valerica Has It Goin On**.
- Updated **Valerica Lust of a Mother**, **Acheron**, **Acheron Sacrosanct Patch**, **Advanced Nudity Detection**.
- Updated several **powerofthree** frameworks, including **SPID**, **Tweaks** and **AnimObject Swapper**.
- Updated **Perk Entry Point Extender**, **SKSE**, **Cinematic Conversation Camera**, **Skyrim Cosave Accelerator**, **JContainers SE**, **PPA Penetration Physics**, **Modex** and **SLSF Reloaded LL**.
- **UBE-specific**: OBody blacklist, Native EditorID Fix, and PPA reinstall with UBE selected.

**Source:** user-supplied official changelog, 18 October 2026. The announcement of save compatibility does **not** guarantee compatibility with the customized instance, local translations or additional mods.

## Non-negotiable migration rule

**NEVER run the Wabbajack installer against `C:\JEUX\NEFARAM`.** Do not replace its MO2 profile, `ModOrganizer.ini`, `Game Root`, translated plugins, INIs or generated output from the official installation automatically.

One module at a time:

1. identify **current Rhiven** version (MO2, not only the official 17.3.7 archive);
2. establish the official **17.3.8 target version** and download source;
3. check dependencies, supported Skyrim runtime and SKSE/API compatibility;
4. check MO2 left-pane overwrite order, right-pane plugins, FOMOD options and configs;
5. check whether an existing French translation/patch needs adaptation;
6. back up/retain the installed version, install manually, and test;
7. mark **VALIDATED** only after successful in-game verification.

Status: **TO REVIEW** → **COMPATIBLE** → **INSTALLED** → **VALIDATED**. Optional mods may be marked **SKIPPED / NOT REQUIRED** with justification. **BLOCKED** if a prerequisite fails.

## Source manifests and audit scope

| Reference | Date | Source |
| --- | --- | --- |
| NEFARAM 17.3.6 | 3 Oct 2026 | Historical reference |
| NEFARAM 17.3.7 | 6 Oct 2026 | `modlist_17.3.7` extracted from `.wabbajack` |
| NEFARAM 17.3.8 | 18 Oct 2026 | `modlist_17.3.8` extracted from `.wabbajack` |

The initial Wabbajack manifest audit reports **2,397 → 2,353 referenced archive names** and **456,220 → 456,535 directives**, with **38 archive names added and 82 removed**. **These are archive deltas, not counts of new/removed MO2 mods.** An archive disappearance may be a version replacement or removal; precise mod-level changes require confirmation. The audit also identifies changes inside official MO2 profiles and `Game Root`; these must **not** be applied wholesale to Rhiven.

The validated 17.3.7 Rhiven baseline was checked against the repository snapshots before migration. The active migration profile is **`Eleanor 17.3.8 TEST`**; the underlying MO2 `mods` directory remains shared between profiles, so updated versions are installed as **separate mods** rather than overwriting the old folders.

## Update matrix — known version replacements

| Mod / component | 17.3.7 archive | 17.3.8 archive | Risk / checks | Status |
| --- | --- | --- | --- | --- |
| **Acheron** | 1.11.2 | **1.11.3** | Installed separately; ESP and existing French translation unchanged; menu/save/MCM checked; full defeat-path test still pending | **INSTALLED — STARTUP/MCM VALIDATED** |
| **Acheron — Sacrosanct Patch** | Not present in current Rhiven 17.3.7 | **1.1.0** | New Rhiven addition; ESPFE + targeted `AcheronHunterPride` script override; load order and masters verified; startup/save tested; vampire Feed/Drain functional test deferred | **TECHNICALLY VALIDATED** |
| **Advanced Nudity Detection** | 4.1.4c | **4.1.5** | Separate install; ESP unchanged; DLL/script update; MCM and game load tested | **VALIDATED** |
| **SLSF Reloaded LL** | 4.1.1 | **4.1.2** | Separate install; plugin position restored to exact baseline; menu/save/MCM tested. Official Friends/Lovers Ignore Sleep re-init caveat retained for the starter save | **VALIDATED — STARTER-SAVE CAVEAT** |
| **Modex / AddItemMenu** | 3.0.0 | **3.0.2** | Separate install + Rhiven patch; French localization preserved; one new string translated; settings adapted to 3.0.2 format; menu tested in game | **VALIDATED** |
| **PPA Penetration Physics** | 0.0.36 | **0.0.38** | Same FOMOD feature set reproduced; Rhiven hotkeys preserved; SKSE startup/load tested; full collision/scene test deferred to the definitive playthrough | **INSTALLED — STARTUP VALIDATED** |
| **SKSE64 (Steam)** | 2.2.6 | **2.2.8** | Runtime confirmed **Skyrim 1.6.1170**; scripts installed as separate MO2 mod; Game Root loader/DLL backed up then replaced; load/save tested | **VALIDATED** |
| **SPID** | 7.3.2 | **7.3.3** | Two-file DLL/PDB replacement; old version disabled; menu/save/console clean | **VALIDATED** |
| **powerofthree's Tweaks** | 1.16.0 | **1.17.1** | FOMOD branch `SSE/AE v1.6.1170`; DLL/PDB + script/source replacement; menu/save clean | **VALIDATED** |
| **AnimObject Swapper** | 1.1.0 | **2.0.0** | FOMOD branch `SSE/AE v1.6.1170`; DLL/PDB replacement only; menu/save clean | **VALIDATED** |
| **Cinematic Conversation Camera** | 1.4.8 | **1.5.0** | Existing 104 settings preserved semantically; 9 new options accepted from 1.5.0; startup/save clean; real dialogue/camera behavior deferred | **TECHNICALLY VALIDATED** |
| **Skyrim Cosave Accelerator / S.L.A.C.K** | 1.3.2 | **1.5.1** | 1.3.2 rejected SKSE 2.2.8; 1.5.1 AE 1.6.1170 / SKSE 2.2.8 branch installed; cosave load and save timings verified in game | **VALIDATED** |
| **Native EditorID Fix** | 1.2.2 | **1.2.3** | Old, new and First Person Inertia override INIs confirmed identical; DLL updated; startup/save clean | **VALIDATED** |
| **JContainers SE** | 4.2.13.2 + separate `JContainers Fix` | **4.3.3** | 4.3.3 installed for SKSE 2.2.8 / Skyrim 1.6.1170; old package disabled; legacy NDR Fix absent from official 17.3.8 and disabled; startup/save clean | **VALIDATED** |
| **Perk Entry Point Extender (PEPE)** | 2.2.4.6 | **2.3.7.0** | Adds `PerkEntryPointExtender.esl`, Lexicon data and AVG TOML; ESPFE left at MO2 automatic priority 176; inventory/perks/map/magic tested | **VALIDATED** |
| **Keyword Item Distributor** | 4.0.6 | **4.1.0** | FOMOD branch `SSE/AE v1.6.1170`; INI unchanged (`bVerboseLogging = false`); startup/save/inventory checks clean | **VALIDATED** |
| **Address Library** | All in One v11 | **All in One (1.7.104.0) v13** | v13 contains the required 1.6.1170 versionlib files; old v11 disabled; startup/save clean | **VALIDATED** |
| **XPMF** | 0.6.1 | **0.7.1** | New DLL/PDB installed; `Simplicity of Snow Sulfur Ash Moss` intentionally continues to win on four generic JSON profiles with `{}` while supplying its own `sos - ...` profiles; startup/save/visual check clean | **VALIDATED** |

Other technical archives in the manifest delta require review **only if the active Rhiven version differs**, including Base Object Swapper 3.5.0, AudioUtil 0.9.29, MfgFix NG 1.0.10, Actor Value Generator 2.3.6.0, Light Placer 5.0.0, Better Third Person Selection 0.9.0, Conditional Expressions Extended 2.3.0, Magic Fixes and Tweaks 2.4.5, Dynamic Dialogue Replacer 1.4.1, Andrealphus Papyrus Functions 1.10.1, Lexicon 0.6.3.0 and Rogue's Gallery 1.0.1.0. This is not confirmation that all of these need installation manually.

## Migration log — completed work

### Acheron 1.11.3

- Old **1.11.2** retained; new version installed separately as **`Acheron - Death Alternative 1.11.3 - Rhiven`**.
- File audit found the ESP unchanged, the existing French translation unchanged, seven `.psc` sources unchanged, while the native DLL/PDB and several compiled scripts changed.
- New OAR killmove files and `paired_huga.hkx` were added by 1.11.3.
- MO2 plugin position remained correct; no missing masters.
- Skyrim menu, save load and Acheron MCM/integration events tested successfully.
- **Pending:** a real defeat-path test before classifying the mod as fully validated.

### Advanced Nudity Detection 4.1.5

- Installed separately as **`Advanced Nudity Detection 4.1.5 - Rhiven`**.
- Old **4.1.4c** disabled only in the test profile.
- ESP unchanged; native DLL name/version and MCM compiled/source script changed.
- Game load, console and MCM checked with no error.
- **Status: VALIDATED.**

### SLSF Reloaded 4.1.2

- Installed separately as **`SLSF Reloaded 4.1.2 - Rhiven`**.
- File comparison: 32 identical, 5 modified, no additions/removals; ESP and translations remained unchanged.
- The official 4.1.1 → 4.1.2 re-init procedure was investigated. Removing SLSF temporarily caused a missing-master cascade through FameComments and NEFARAM/Synthesis patches, so the cascade was stopped and the normal save-compatible update path was used.
- Temporary MO2 plugin toggling changed priorities; `SLSF Reloaded.esp`, `FameCommentsReloaded.esp` and `_NEFERAM_SexDialogue.esp` were manually restored to their exact baseline positions.
- Final load order was verified line-for-line against the 17.3.7 baseline.
- Menu, save load, MCM and console tested successfully.
- Caveat: **Friends/Lovers Ignore Sleep** may still require a new game or official re-init; the definitive playthrough will be a new game.
- **Status: VALIDATED for the migration starter-save context.**

### Modex 3.0.2

- Installed separately as **`Modex - A Mod Explorer Menu (AddItemMenu) 3.0.2 - Rhiven`**.
- Separate local patch installed as **`Modex - 3.0.2 Patch - Rhiven`**.
- Existing `french.json` from 3.0 was preserved.
- New localization key translated: `NON_PLAYER_TARGET = "Ajout à une cible autre que le joueur"`.
- New 3.0.2 settings format retained while preserving applicable Rhiven options; language explicitly set to French.
- In-game Modex menu opened correctly in French and indexed game data.
- **Status: VALIDATED.**

### PPA / Procedural Penis Animations 0.0.38

- Existing MO2 mod identified as **`Penetration Physics`**, version **0.0.36**.
- New version installed separately as **`PPA Penetration Physics 0.0.38 - Rhiven`**.
- 0.0.36 contained 142 files. Reproducing the same FOMOD feature set in 0.0.38 yielded **140 identical files out of 142** before the local TOML hotkey edits.
- Preserved FOMOD choices:
  - Main Plugin Files / 3BA;
  - Procedural Sound Effects;
  - Creature Support requiring Baka ABC;
  - author's animation tags (`asdt123123_tags.json`);
  - XP32 Skeleton Fix.
- Not selected: UBE patch, BHUNP patch, assisted/Bigglsby tags, strict gangbang tags, MFEE UBE.
- The Rhiven setup is **3BA**, so the official UBE-specific reinstall instruction does not apply.
- Only four semantic TOML values differed between old and new defaults. The fresh 0.0.38 TOML was retained and the Rhiven hotkeys were restored:
  - `Reload = 73`
  - `SelectActor = 76`
  - `SpeedUpAnimKey = 201`
  - `SlowDownAnimKey = 209`
- Old 0.0.36 disabled, new 0.0.38 enabled; no unexpected MO2 conflicts.
- Skyrim/save load tested with no PPA/SKSE error.
- **Pending:** functional collision/scene test during the definitive Eleanor playthrough.
- **Status: INSTALLED — STARTUP VALIDATED.**

### SKSE64 2.2.8

- Runtime confirmed: **Skyrim AE 1.6.1170**.
- Existing 2.2.6 layout was split:
  - MO2 `SKSE` mod: scripts/sources;
  - `Game Root`: `skse64_loader.exe` and `skse64_1_6_1170.dll`.
- New scripts installed separately as **`SKSE 2.2.8 - Rhiven`**, using only the official archive's `Data` directory.
- Old 2.2.6 scripts mod disabled in the test profile.
- Old Game Root binaries backed up to **`C:\JEUX\NEFARAM\SKSE_BACKUP_2.2.6`** before replacement.
- `skse64_loader.exe` and `skse64_1_6_1170.dll` then replaced with 2.2.8 files.
- Initial launch exposed the expected incompatibility with old S.L.A.C.K 1.3.2; Skyrim itself still reached the main menu.
- After the S.L.A.C.K update, the game reached menu, loaded the Unbound test save and created a new manual save successfully.
- Console identified **SKSE64 2.2.8 rel 73**.
- **Status: VALIDATED.**

### S.L.A.C.K 1.5.1

- Existing **1.3.2** used the legacy `DLLPlugins` layout and raised an incompatibility popup with SKSE 2.2.8.
- Installed separately as **`Save and Load Accelerator for SKSE Cosaves - S.L.A.C.K 1.5.1 - Rhiven`**.
- FOMOD automatically selected the correct branch: **Skyrim AE 1.6.1170 / SKSE64 2.2.8**.
- 1.5.1 uses the modern `SKSE\Plugins` layout, explaining why MO2 showed no direct file conflicts with the old 1.3.2 package.
- Old 1.3.2 disabled; new 1.5.1 enabled.
- Main menu reached with no incompatibility popup.
- Existing Unbound test save loaded successfully.
- Console confirmed **S.L.A.C.K Cosave load timing**.
- A new manual save completed successfully and console confirmed **S.L.A.C.K Cosave save timing** with no error.
- **Status: VALIDATED.**

### Address Library v13

- Existing **All in One v11** replaced in the test profile by **`Address Library for SKSE Plugins v13 - Rhiven`**.
- The v13 package includes both `versionlib-1-6-1170-0.bin` and `versionlib-1-6-1170-0-1.bin`, so the active **Skyrim 1.6.1170** runtime is covered.
- v13 also contains newer runtime libraries (1.7.99 / 1.7.104), which do not interfere with 1.6.1170.
- Old v11 disabled; main menu and Unbound save loaded with no popup, CTD or console error.
- **Status: VALIDATED.**

### SPID 7.3.3

- Existing **7.3.2** replaced by separate **`Spell Perk Item Distributor (SPID) 7.3.3 - Rhiven`**.
- Archive contains only `po3_SpellPerkItemDistributor.dll` and its PDB; conflicts were exactly the expected two files.
- Old 7.3.2 disabled.
- Main menu and Unbound save loaded cleanly.
- **Status: VALIDATED.**

### powerofthree's Tweaks 1.17.1

- Existing **1.16.0** replaced by separate **`powerofthree's Tweaks 1.17.1 - Rhiven`**.
- FOMOD selected **SSE/AE v1.6.1170**.
- Expected replacements: `po3_Tweaks.dll`, PDB, compiled Papyrus script and source.
- No Rhiven-specific INI was present to migrate.
- Main menu and Unbound save loaded cleanly.
- **Status: VALIDATED.**

### AnimObject Swapper 2.0.0

- Existing **1.1.0** replaced by separate **`AnimObject Swapper 2.0.0 - Rhiven`**.
- FOMOD selected **SSE/AE v1.6.1170**.
- Only the native DLL/PDB conflict with the old version.
- Old 1.1.0 disabled; main menu and Unbound save loaded cleanly.
- **Status: VALIDATED.**

### Cinematic Conversation Camera 1.5.0

- Existing **1.4.8** replaced by separate **`Cinematic Conversation Camera 1.5.0 - Rhiven`**.
- Existing install used `SceneDirector.dll` + `SD.ini`; no `SD_user.ini` was present.
- Semantic comparison found all **104 existing settings retained with the same values** in 1.5.0.
- 1.5.0 adds nine settings: `iSceneWait`, `iSceneRange`, `bFollowFace`, `bPersuasionBeat`, `bFilmScenesAuto`, `iKeyFilmScene`, `bSubtitlesInBar`, `bStopWorkToTalk`, `bPlayerGestureCue`.
- The fresh 1.5.0 `SD.ini` was kept as-is.
- Main menu and Unbound save loaded cleanly.
- **Pending:** real dialogue/camera behavior during the definitive playthrough.
- **Status: TECHNICALLY VALIDATED.**

### Native EditorID Fix 1.2.3

- Existing **1.2.2** replaced by separate **`Native EditorID Fix 1.2.3 - Rhiven`**.
- `First Person (FP) Inertia - SKSE` already overwrites `NativeEditorIDFix.ini`.
- Old 1.2.2 INI, the FP Inertia winning override and the new 1.2.3 INI were compared and are semantically identical:
  - `EnableLookupTable = true`
  - `EnableNativeEditorIDLookup = false`
  - `MaxEditorIDLength = 128`
  - all three patch toggles remain `true`.
- FP Inertia therefore continues to win the INI with no behavioral change.
- Main menu and Unbound save loaded cleanly.
- **Status: VALIDATED.**

### JContainers SE 4.3.3

- Previous state: **JContainers 4.2.13.2** plus separate **`JContainers Fix`** (`4.2.13.2-NDRFix-1.6.1170`) overriding only `JContainers64.dll`.
- The official 17.3.8 manifest was searched for `JContainers Fix`, `JContainersFix` and `NDRFix`: no legacy fix package is present.
- Installed separate **`JContainers SE 4.3.3 - Rhiven`** for **SKSE 2.2.8 / Skyrim 1.6.1170**.
- Old JContainers 4.2.13.2 disabled.
- Legacy `JContainers Fix` disabled to match the official 17.3.8 architecture.
- Main menu, Unbound save and console checks clean.
- **Status: VALIDATED.**

### Perk Entry Point Extender (PEPE) 2.3.7.0

- Existing **2.2.4.6** replaced by separate **`Perk Entry Point Extender 2.3.7.0 - Rhiven`**.
- 2.3.7.0 adds, in addition to the updated DLL/script files:
  - `PerkEntryPointExtender.esl`;
  - `SKSE\Lexicon\scripts\Shared\PEPE.lsi`;
  - `SKSE\Plugins\ActorValueData\PerkEntryPointExtender_AVG.toml`.
- These additions are present in the official 17.3.8 manifest and are intentional.
- MO2 automatically inserted `PerkEntryPointExtender.esl` at **priority 176**, ESL index **FE:06F**. It was deliberately **not moved without evidence of the official 17.3.8 plugin position**.
- Old 2.2.4.6 disabled.
- Main menu and Unbound save loaded successfully; inventory, perks, map and magic menus were exercised with no issue.
- **Status: VALIDATED.**

### Keyword Item Distributor (KID) 4.1.0

- Existing **4.0.6** replaced by separate **`Keyword Item Distributor (KID) 4.1.0 - Rhiven`**.
- FOMOD selected **SSE/AE v1.6.1170**.
- Expected conflicts: DLL, INI and PDB.
- Old and new INIs are identical:
  ```ini
  [Settings]
  bVerboseLogging = false
  ```
- Old 4.0.6 disabled.
- Main menu, Unbound save, multiple inventories, console and notifications checked with no anomaly.
- **Status: VALIDATED.**

### XPMF 0.7.1

- Existing **0.6.1** replaced by separate **`XPMF - Extended Projected Materials Framework 0.7.1 - Rhiven`**.
- XPMF supplies `XPMF.dll`, PDB and four generic material profiles: `ash.json`, `ash_pbr.json`, `snow.json`, `snow_pbr.json`.
- Existing **`Simplicity of Snow Sulfur Ash Moss`** intentionally overwrites those four generic JSON files.
- Inspection confirmed its generic overrides contain only **`{}`**, deliberately neutralizing XPMF's generic ash/snow profiles while the mod supplies its own more specific `sos - ...` XPMF profiles.
- That overwrite relationship was preserved; XPMF 0.7.1 wins only the DLL/PDB while Simplicity of Snow Sulfur Ash Moss continues to win the four generic JSON files.
- Old 0.6.1 disabled.
- Main menu, Unbound save and visual sanity check completed cleanly.
- **Status: VALIDATED.**

### Acheron — Sacrosanct Patch 1.1.0

- This patch was **not present in the current Rhiven 17.3.7 installation**; it is a new addition for the 17.3.8 migration.
- Installed as **`Acheron - Sacrosanct Patch - Rhiven`**, using the main **1.1.0** file intended for **Acheron 1.11.3 + Sacrosanct 6.0.0**.
- The mod contains:
  - `Acheron - Sacrosanct Patch.esp` (ESPFE);
  - `Scripts\AcheronHunterPride.pex`;
  - matching Papyrus source.
- Its script and source intentionally overwrite the files from **Acheron 1.11.3**.
- xEdit confirms only three masters: `Skyrim.esm`, `Acheron.esm`, `Sacrosanct - Vampires of Skyrim.esp`.
- The ESPFE was moved from MO2's automatic bottom position to immediately after `Sacrosanct - Vampires of Skyrim.esp`:
  - Sacrosanct priority **484**;
  - Acheron Sacrosanct Patch priority **485**, ESL index **FE:183**;
  - followed by `Shoo_TestCRVampFix.esp` and `CoverYourHead - Sacrosanct.esp`.
- Main menu and Unbound save loaded cleanly.
- **Pending:** real vampire **Feed/Drain** behavior test during the definitive playthrough.
- **Status: TECHNICALLY VALIDATED.**

## Added / content-sensitive modules

### 1. RaceMenu Portraits

- Official NEFARAM 17.3.8 archive reference: **1.1.2**.
- Rhiven deliberately installed **1.2.0** instead, because its documented fixes are directly relevant to this setup: reduced preset-generation freezing, RaceMenu closing/input fixes, safer handling of crashing portraits, and a fix for portrait creation with **XPMSE in-game options** installed.
- Version 1.3.0 was reviewed but not selected; its headline change is **NPA 3.0 compatibility** plus unspecified minor fixes, which is not required for the current Rhiven setup.
- Installed as **`RaceMenu Portraits - Rhiven`** directly below RaceMenu in the left pane.
- Pure SKSE plugin: `SKSE\Plugins\RaceMenuPortraits.dll`; **no ESP/ESL, Papyrus script or load-order entry**.
- No MO2 file conflicts.
- Main menu and Unbound save loaded cleanly.
- RaceMenu **Réglages / Presets** opened the Portraits interface correctly and detected **65 presets**.
- One portrait was generated successfully without freeze/CTD; the counter dropped to 64 missing portraits.
- The same preset was loaded onto the player successfully. Missing preset dependencies were reported and skipped cleanly instead of causing a failure.
- **Status: VALIDATED.**

### 2. Skyrim Performance Solution (SPS)

- Official NEFARAM 17.3.8 reference: **1.0.63**, optional and enabled by default.
- Rhiven deliberately installed **1.0.64** instead as a stability-only deviation for a very large list.
- Installed as **`Skyrim Performance Solution (SPS) - Rhiven`** with a separate **`Skyrim Performance Solution (SPS) INI - Rhiven`** override.
- Quality-first settings disable actor-shadow, general shadow, point-light shadow and decal culling; cache/throttle/subtree-pruning and VRAM-budget texture streaming remain enabled.
- Menu, Unbound save, forest and city tests were clean. Under high VRAM pressure SPS downscaled textures and later restored them; observed savings reached about **876 MB** with no visible degradation or load errors.
- A global keyboard/hotkey audit is deferred to the final Eleanor setup.
- **Status: VALIDATED.**

### 3. Serana Revamped — Valerica Has It Goin On

- Exact official 17.3.8 manifest entry verified: **`Serana Revamped - Valerica has it Goin On - 1.25`** (Nexus mod 185642, file 806187).
- Installed as **`Serana Revamped - Lust of a Mother - Serana Voice Over - KerstynVoices Edition - Rhiven`**.
- This package is a voice override plus a tiny ESL-flagged **`KVSeranaLustOfAMother.esp`**. xEdit confirms that plugin contains **0 records** and only Skyrim/Update/Dawnguard masters.
- Existing **Serana Re-Imagined** remains the visual appearance layer; the new package contains no meshes, textures or FaceGen.
- The separate Nexus **Dawnguard Revoice - KerstynVoices Edition** was searched in the exact Wabbajack 17.3.8 manifest and is **absent**, so it was deliberately not added.
- Main menu and Unbound save loaded cleanly.
- **Pending:** natural in-game verification of the new voiced lines during the definitive playthrough.
- **Status: TECHNICALLY VALIDATED.**

### 4. Valerica Lust of a Mother

- Previous Rhiven version: **1.24 Slab Edition**.
- Installed separately as **`Valerica Lust of a Mother 1.25 Slab Edition - Rhiven`**; old 1.24 retained but disabled.
- Normalized file comparison: **932** old functional files; **931 SHA-256 identical**; only **`abcd_valerica.esp`** changed.
- Version 1.25 adds **91 functional files**: **89 Serana `.fuz` files** plus `aabcd_SeranaTransition.pex` and matching source.
- Existing animations, scripts, sequence file and old voice assets are otherwise unchanged.
- xEdit: ESL-flagged `abcd_valerica.esp`, expected masters, **Check for Errors: 0**.
- Main menu and Unbound save loaded cleanly.
- **Pending:** new dialogue/scene verification during the definitive playthrough.
- **Status: TECHNICALLY VALIDATED.**

### 5. Acheron and Sacrosanct Patch

- **Acheron 1.11.3 is installed and startup/MCM validated.**
- **Acheron — Sacrosanct Patch 1.1.0** is now installed and technically validated.
- The patch was a new Rhiven addition, not a replacement of an existing 17.3.7 mod.
- Its targeted Acheron script override, masters and ESPFE load-order position were verified in MO2/xEdit.
- **Pending:** functional Feed/Drain test with a vampire character.
- **Status: TECHNICALLY VALIDATED; gameplay interaction deferred.**

### 6. OBody / UBE-specific updates

- Author announces an **UBE blacklist** addition, **Native EditorID Fix**, and a **PPA reinstall selecting UBE**.
- Rhiven currently uses **CBBE/3BA**, not UBE.
- The PPA 0.0.38 migration therefore deliberately retained the existing 3BA configuration and did **not** select UBE-specific files.
- **Native EditorID Fix 1.2.3 is independently migrated and VALIDATED**; its winning INI behavior remains unchanged.
- **Status: UBE-SPECIFIC PPA STEP NOT REQUIRED; Native EditorID migration complete.**

## Files and profiles requiring explicit protection

- `C:\JEUX\NEFARAM` — customized working installation.
- **`Eleanor Stable`** — original validated stable profile.
- **`Eleanor Stable - PRE 17.3.8`** — rollback profile created before this migration.
- **`Eleanor 17.3.8 TEST`** — only profile authorized for migration testing.
- Profile `modlist.txt`, `plugins.txt`, `loadorder.txt` and any other profile settings.
- `ModOrganizer.ini`, generated outputs and personal MO2 separators/priorities.
- `Game Root/skse64_1_6_1170.dll` and `skse64_loader.exe` — current 2.2.8; previous 2.2.6 binaries backed up in `C:\JEUX\NEFARAM\SKSE_BACKUP_2.2.6`.
- All **Rhiven FR translations**, custom patches, xEdit changes, NPC appearances, FOMOD choices and local INI files.

**Important:** MO2 profiles share the underlying `mods` directory. A profile protects activation/load order but **not the physical mod folders**. For migration work, install new versions as separate mods and retain the old folders until final validation.

**Important:** the initial archive audit mentions many apparent removals unrelated to the published changelog. Do not delete any Rhiven mods based on the “archive removed” list alone. They could reflect repackaging, optimization or source-archive cleanup.

## Recommended phased execution — live status

1. **Freeze baseline — DONE.** Stable/reference profiles and repository left/right snapshots checked before migration.
2. **Build active-version table — IN PROGRESS.** Target replacements identified; each installed Rhiven version is still confirmed immediately before touching that module.
3. **Technical prerequisites — DONE for the identified 17.3.8 replacements.** Skyrim 1.6.1170, SKSE 2.2.8, S.L.A.C.K 1.5.1, Address Library v13 and the listed native dependencies are validated.
4. **Core SKSE frameworks — DONE for the known replacement matrix.** SPID, powerofthree's Tweaks, AnimObject Swapper, Native EditorID Fix, JContainers, PEPE, KID and XPMF are migrated and validated; Cinematic Conversation Camera is technically validated with real dialogue behavior deferred.
5. **Gameplay frameworks — IN PROGRESS.** Acheron, AND, SLSF, Modex and PPA are migrated; Acheron Sacrosanct Patch is technically validated. Acheron defeat, vampire Feed/Drain and PPA collision/scene tests remain deferred to the definitive playthrough.
6. **NPC/content — PENDING.** Valerica / Serana changes and visual-load-order compatibility not yet reviewed.
7. **Opt-in decision — PARTIAL.** RaceMenu Portraits 1.2.0 is installed and validated; Skyrim Performance Solution still requires a deliberate compatibility/benchmark decision.
8. **UBE special-case checks — PARTIALLY RESOLVED.** Rhiven is 3BA, so PPA UBE instructions are not applicable.
9. **Final checks — PENDING.** Full MO2 conflict review, plugin masters/xEdit as applicable, definitive new-game gameplay tests and MCM tests after all components are migrated.
10. **Documentation — IN PROGRESS.** This migration sheet is maintained during the work; final Rhiven MO2 left/right snapshots will be refreshed only after the complete 17.3.8 state is validated.

## Validation register

| Milestone | State |
| --- | --- |
| Wabbajack 17.3.7 and 17.3.8 manifest files acquired | DONE |
| Initial archive/manifests comparison | DONE — preliminary |
| Active Rhiven MO2 baseline / left-right snapshots | DONE — validated before migration |
| Rollback profile / customized setup protection | DONE — `Eleanor Stable - PRE 17.3.8` + separate version installs |
| Skyrim runtime / SKSE compatibility decision | DONE — Skyrim 1.6.1170 + SKSE64 2.2.8 |
| SKSE64 2.2.8 | **VALIDATED** |
| S.L.A.C.K 1.5.1 | **VALIDATED** |
| Advanced Nudity Detection 4.1.5 | **VALIDATED** |
| SLSF Reloaded 4.1.2 | **VALIDATED — starter-save caveat documented** |
| Modex 3.0.2 + Rhiven patch | **VALIDATED** |
| Acheron 1.11.3 | **INSTALLED — startup/MCM validated; defeat-path test pending** |
| PPA 0.0.38 | **INSTALLED — startup validated; functional scene test pending** |
| Acheron Sacrosanct Patch 1.1.0 | **TECHNICALLY VALIDATED — Feed/Drain test deferred** |
| Address Library v13 | **VALIDATED** |
| SPID 7.3.3 | **VALIDATED** |
| powerofthree's Tweaks 1.17.1 | **VALIDATED** |
| AnimObject Swapper 2.0.0 | **VALIDATED** |
| Cinematic Conversation Camera 1.5.0 | **TECHNICALLY VALIDATED — dialogue behavior deferred** |
| Native EditorID Fix 1.2.3 | **VALIDATED** |
| JContainers SE 4.3.3 / legacy Fix removal | **VALIDATED** |
| PEPE 2.3.7.0 | **VALIDATED** |
| KID 4.1.0 | **VALIDATED** |
| XPMF 0.7.1 | **VALIDATED** |
| RaceMenu Portraits 1.2.0 | **VALIDATED** |
| Remaining technical/native replacements | **KNOWN MATRIX COMPLETE; review only additional manifest deltas if relevant** |
| NPC/content additions and optional modules | PENDING / TO REVIEW |
| xEdit, translations, plugins and final game validation | IN PROGRESS |
| Migration status | **IN PROGRESS** |

## Next action (one step at a time)

The known **technical replacement matrix is now complete**. Continue with the remaining **content/optional 17.3.8 additions**, one module at a time:

1. **Skyrim Performance Solution 1.0.63** — review overlap with existing performance/SKSE tweaks before deciding whether to enable it.
2. **Serana Revamped — Valerica Has It Goin On 1.25** — inspect facegen/NPC overhaul conflicts before installation.
3. **Valerica Lust of a Mother 1.25 Slab Edition** — compare against the existing 1.24 Slab Edition, including plugins, assets and translation implications.
4. Review any additional manifest-only deltas only where the active Rhiven version actually differs.

Deferred functional tests remain: Acheron defeat path, Acheron/Sacrosanct vampire Feed/Drain, PPA collision/scene behavior, and Cinematic Conversation Camera during real dialogue.

Do **not** run LOOT or Wabbajack, do not batch-enable/disable mods, and do not alter the stable rollback profiles.
