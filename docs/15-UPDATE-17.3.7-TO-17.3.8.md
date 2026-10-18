# 15 - Update NEFARAM 17.3.7 -> 17.3.8

> **DRAFT — migration not started / awaiting validation**  
> Prepared: 18 October 2026  
> Installation: customized **NEFARAM-Rhiven**, manual upgrade only.

This document tracks the controlled migration of the customized **NEFARAM-Rhiven** installation from the validated **17.3.7** baseline to official **17.3.8**. It follows [the preceding migration procedure](14-UPDATE-17.3.6-TO-17.3.7.md).

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

## Update matrix — known version replacements

All rows are **TO REVIEW**, even where target versions are identified by the manifests.

| Mod / component | 17.3.7 archive | 17.3.8 archive | Risk / checks | Status |
| --- | --- | --- | --- | --- |
| **Acheron** | 1.11.2 | **1.11.3** | Death-alternative integrations; inspect French ESP/scripts and dependencies | TO REVIEW |
| **Acheron — Sacrosanct Patch** | Previous archive to confirm | **1.1.0** | Check matching Acheron/Sacrosanct versions and plugin load order | TO REVIEW |
| **Advanced Nudity Detection** | 4.1.4c | **4.1.5** | MCM, scripts, French files | TO REVIEW |
| **SLSF Reloaded LL** | 4.1.1 | **4.1.2** | Existing settings/MCM; LL package; translation impact | TO REVIEW |
| **Modex / AddItemMenu** | 3.0.0 | **3.0.2** | SKSE/UI dependencies, menu operation | TO REVIEW |
| **PPA Penetration Physics** | 0.0.36 | **0.0.38** | FOMOD, body framework, UBE-specific selection if applicable | TO REVIEW |
| **SKSE64 (Steam)** | 2.2.6 | **2.2.8** | Critical: actual runtime, loader, Game Root files, DLL compatibility, rollback | TO REVIEW |
| **SPID** | 7.3.2 | **7.3.3** | Distribution configuration and version compatibility | TO REVIEW |
| **powerofthree's Tweaks** | 1.16.0 | **1.17.1** | SKSE DLL/INI; technical dependencies | TO REVIEW |
| **AnimObject Swapper** | 1.1.0 (archive name) | **2.0.0** | Major version; INI/data compatibility and downstream mods | TO REVIEW |
| **Cinematic Conversation Camera** | 1.4.8 | **1.5.0** | Camera controls, custom presets/INI, conflicts | TO REVIEW |
| **Skyrim Cosave Accelerator** | 1.3.2 | **1.5.1** | SKSE cosaves, save/load test, DLL versions | TO REVIEW |
| **Native EditorID Fix** | 1.2.2 | **1.2.3** | Plugin/DLL compatibility; especially UBE setup | TO REVIEW |
| **JContainers SE** | old package 4.2.13.2 (for 1.6.1170) | **4.3.3** | Runtime, plugins/scripts depending on JContainers | TO REVIEW |
| **Perk Entry Point Extender (PEPE)** | 2.2.4.6 | **2.3.7.0** | Native DLL, dependent perks/mods | TO REVIEW |
| **Keyword Item Distributor** | 4.0.6 | **4.1.0** | KID distributions, INI compatibility | TO REVIEW |
| **Address Library** | All in One v11 (archive name) | **All in One (1.7.104.0) v13** | Verify exact edition/runtime match before installing | TO REVIEW |
| **XPMF** | 0.6.1 | **0.7.1** | Framework compatibility with configured materials | TO REVIEW |

Other technical archives in the manifest delta require review **only if the active Rhiven version differs**, including Base Object Swapper 3.5.0, AudioUtil 0.9.29, MfgFix NG 1.0.10, Actor Value Generator 2.3.6.0, Light Placer 5.0.0, Better Third Person Selection 0.9.0, Conditional Expressions Extended 2.3.0, Magic Fixes and Tweaks 2.4.5, Dynamic Dialogue Replacer 1.4.1, Andrealphus Papyrus Functions 1.10.1, Lexicon 0.6.3.0 and Rogue's Gallery 1.0.1.0. This is not confirmation that all of these need installation manually.

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

- Apply dependency compatibility checks **together**, but install/test in a controlled order.
- Preserve any Rhiven-specific patches, French files, configs and save state.
- **Status: TO REVIEW.**

### 6. OBody / UBE-specific updates

- Author announces an **UBE blacklist** addition, **Native EditorID Fix**, and a **PPA reinstall selecting UBE**.
- Confirm whether Rhiven actually uses **UBE** before applying any UBE-specific step. Never assume the official list's body preset is identical to Rhiven's choices.
- **Status: CONDITIONAL / TO REVIEW.**

## Files and profiles requiring explicit protection

- `C:\JEUX\NEFARAM` — customized working installation.
- `profiles/NEFARAM/modlist.txt`, `plugins.txt`, `loadorder.txt` and any other profile settings.
- `ModOrganizer.ini`, generated outputs and personal MO2 separators/priorities.
- `Game Root/skse64_1_6_1170.dll` and `skse64_loader.exe` — replace only after runtime and SKSE compatibility checks.
- All **Rhiven FR translations**, custom patches, xEdit changes, NPC appearances, FOMOD choices and local INI files.

**Important:** the initial archive audit mentions many apparent removals unrelated to the published changelog. Do not delete any Rhiven mods based on the “archive removed” list alone. They could reflect repackaging, optimization or source-archive cleanup.

## Recommended phased execution (not yet authorized)

1. **Freeze baseline:** copy/confirm MO2 left/right snapshots and relevant configuration backups.
2. **Build active-version table:** compare installed Rhiven versions to the target manifest; avoid redundant updates.
3. **Technical prerequisites:** verify Skyrim runtime, SKSE and Address Library compatibility **before** upgrading any DLL.
4. **Core SKSE frameworks:** update independently, test startup after small batches.
5. **Gameplay frameworks:** Acheron + patch, AND, SLSF, PPA, Modex; inspect French translations.
6. **NPC/content:** Valerica / Serana change, compatibility with visual load order.
7. **Opt-in decision:** RaceMenu Portraits and especially Skyrim Performance Solution.
8. **UBE special-case checks** only if UBE is actually active.
9. **Final checks:** MO2 conflicts, plugin masters/xEdit as applicable, launch, load save, core gameplay test, MCM tests.
10. **Documentation:** refresh Rhiven MO2 left/right snapshots; only then declare **17.3.8 VALIDATED**.

## Validation register

| Milestone | State |
| --- | --- |
| Wabbajack 17.3.7 and 17.3.8 manifest files acquired | DONE |
| Initial archive/manifests comparison | DONE — preliminary |
| Active Rhiven MO2 version inventory | PENDING |
| Backup of customized MO2 settings | PENDING |
| SKSE/runtime compatibility decision | PENDING |
| Manual installs and per-mod tests | NOT STARTED |
| xEdit, translations, plugins and game validation | NOT STARTED |
| Migration status | **DRAFT — NOT STARTED** |

## Next action (one step at a time)

**First confirm the current customized MO2 snapshots (left and right panels), including any changes since the last uploaded baseline, before proposing any install.** Do not change or reinstall anything yet.
