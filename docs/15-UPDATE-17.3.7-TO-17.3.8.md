# 15 - Update NEFARAM 17.3.7 -> 17.3.8

> **IN PROGRESS — controlled manual migration underway**  
> Prepared: 18 October 2026  
> Last updated: 20 October 2026  
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
| **Acheron — Sacrosanct Patch** | Previous archive to confirm | **1.1.0** | Check matching Acheron/Sacrosanct versions and plugin load order | TO REVIEW |
| **Advanced Nudity Detection** | 4.1.4c | **4.1.5** | Separate install; ESP unchanged; DLL/script update; MCM and game load tested | **VALIDATED** |
| **SLSF Reloaded LL** | 4.1.1 | **4.1.2** | Separate install; plugin position restored to exact baseline; menu/save/MCM tested. Official Friends/Lovers Ignore Sleep re-init caveat retained for the starter save | **VALIDATED — STARTER-SAVE CAVEAT** |
| **Modex / AddItemMenu** | 3.0.0 | **3.0.2** | Separate install + Rhiven patch; French localization preserved; one new string translated; settings adapted to 3.0.2 format; menu tested in game | **VALIDATED** |
| **PPA Penetration Physics** | 0.0.36 | **0.0.38** | Same FOMOD feature set reproduced; Rhiven hotkeys preserved; SKSE startup/load tested; full collision/scene test deferred to the definitive playthrough | **INSTALLED — STARTUP VALIDATED** |
| **SKSE64 (Steam)** | 2.2.6 | **2.2.8** | Runtime confirmed **Skyrim 1.6.1170**; scripts installed as separate MO2 mod; Game Root loader/DLL backed up then replaced; load/save tested | **VALIDATED** |
| **SPID** | 7.3.2 | **7.3.3** | Distribution configuration and version compatibility | TO REVIEW |
| **powerofthree's Tweaks** | 1.16.0 | **1.17.1** | SKSE DLL/INI; technical dependencies | TO REVIEW |
| **AnimObject Swapper** | 1.1.0 (archive name) | **2.0.0** | Major version; INI/data compatibility and downstream mods | TO REVIEW |
| **Cinematic Conversation Camera** | 1.4.8 | **1.5.0** | Camera controls, custom presets/INI, conflicts | TO REVIEW |
| **Skyrim Cosave Accelerator / S.L.A.C.K** | 1.3.2 | **1.5.1** | 1.3.2 rejected SKSE 2.2.8; 1.5.1 AE 1.6.1170 / SKSE 2.2.8 branch installed; cosave load and save timings verified in game | **VALIDATED** |
| **Native EditorID Fix** | 1.2.2 | **1.2.3** | Plugin/DLL compatibility; especially UBE setup | TO REVIEW |
| **JContainers SE** | old package 4.2.13.2 (for 1.6.1170) | **4.3.3** | Runtime, plugins/scripts depending on JContainers | TO REVIEW |
| **Perk Entry Point Extender (PEPE)** | 2.2.4.6 | **2.3.7.0** | Native DLL, dependent perks/mods | TO REVIEW |
| **Keyword Item Distributor** | 4.0.6 | **4.1.0** | KID distributions, INI compatibility | TO REVIEW |
| **Address Library** | All in One v11 (archive name) | **All in One (1.7.104.0) v13** | Verify exact edition/runtime match before installing | TO REVIEW |
| **XPMF** | 0.6.1 | **0.7.1** | Framework compatibility with configured materials | TO REVIEW |

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

## Added / content-sensitive modules

### 1. RaceMenu Portraits

- Official archive identified: **1.1.2**.
- Check prerequisites, output/overwrites, and whether the customized Rhiven setup benefits from this feature.
- **Status: TO REVIEW (new, optionality not yet verified).**

### 2. Skyrim Performance Solution (SPS)

- Official archive identified: **1.0.63**.
- **Officially optional, enabled by default.** For Rhiven, do not enable it automatically.
- Check overlaps with existing performance and SKSE tweaks; benchmark/stability check before and after.
- **Status: TO REVIEW — decision required.**

### 3. Serana Revamped — Valerica Has It Goin On

- Official archive identified: **1.25**.
- Check appearance and facegen collisions with the customized NPC overhaul, Serana/Valerica patches, and left-pane priorities.
- **Status: TO REVIEW.**

### 4. Valerica Lust of a Mother

- Target archive: **1.25 Slab Edition**; previous archive name indicates **1.24 Slab Edition**.
- Compare plugins, meshes/scripts and translation files; verify dependency changes.
- **Status: TO REVIEW.**

### 5. Acheron and Sacrosanct Patch

- **Acheron 1.11.3 is installed and startup/MCM validated.**
- The **Sacrosanct Patch 1.1.0 remains TO REVIEW**.
- Preserve any Rhiven-specific patches, French files, configs and save state.
- **Status: PARTIAL.**

### 6. OBody / UBE-specific updates

- Author announces an **UBE blacklist** addition, **Native EditorID Fix**, and a **PPA reinstall selecting UBE**.
- Rhiven currently uses **CBBE/3BA**, not UBE.
- The PPA 0.0.38 migration therefore deliberately retained the existing 3BA configuration and did **not** select UBE-specific files.
- **Status: UBE-SPECIFIC PPA STEP NOT REQUIRED.** Other Native EditorID/OBody changes still require independent review where applicable.

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
3. **Technical prerequisites — IN PROGRESS.** Skyrim runtime and SKSE 2.2.8 are validated; S.L.A.C.K 1.5.1 is validated. Address Library and remaining native frameworks still need review.
4. **Core SKSE frameworks — IN PROGRESS.** Continue independently and test startup/load/save after each native component.
5. **Gameplay frameworks — IN PROGRESS.** Acheron, AND, SLSF, Modex and PPA migrated; Acheron full defeat test and PPA full scene/collision test remain deferred; Acheron Sacrosanct Patch still pending.
6. **NPC/content — PENDING.** Valerica / Serana changes and visual-load-order compatibility not yet reviewed.
7. **Opt-in decision — PENDING.** RaceMenu Portraits and especially Skyrim Performance Solution.
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
| Acheron Sacrosanct Patch 1.1.0 | PENDING |
| Remaining technical/native replacements | PENDING / TO REVIEW |
| NPC/content additions and optional modules | PENDING / TO REVIEW |
| xEdit, translations, plugins and final game validation | IN PROGRESS |
| Migration status | **IN PROGRESS** |

## Next action (one step at a time)

Resume from the **remaining 17.3.8 target replacements** after SKSE64 2.2.8 / S.L.A.C.K 1.5.1. For each module, first confirm the currently installed Rhiven version, inspect archive/FOMOD/config differences, preserve translations and local settings, then install as a separate mod and test before continuing.

Do **not** run LOOT or Wabbajack, do not batch-enable/disable mods, and do not alter the stable rollback profiles.
