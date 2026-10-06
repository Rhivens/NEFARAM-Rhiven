# 14 - Update NEFARAM 17.3.6 -> 17.3.7

This document tracks the controlled manual migration of the customized **NEFARAM-Rhiven** installation from **NEFARAM 17.3.6** to **17.3.7**.

The goal is to reproduce the 17.3.7 delta manually without running Wabbajack over the customized setup.

## Official 17.3.7 delta

NEFARAM 17.3.7 is announced as **save compatible** and includes:

- Added `Inventory Refresh Fix`
- Added `Standing Stealth`
- Added `Meshes Optimization Project`
- Updated `SLSF Reloaded LL`

## Migration rule

Do **not** run a blind Wabbajack update on the customized installation.

Each change is handled independently:

1. identify exact mod / version
2. verify prerequisites
3. inspect MO2 conflicts
4. inspect plugin impact in xEdit where relevant
5. install in a controlled position
6. launch and validate
7. only then mark the item as integrated

Status convention:

- **TO REVIEW**
- **COMPATIBLE**
- **INSTALLED**
- **VALIDATED**

---

## 1. Inventory Refresh Fix

Source:

https://www.nexusmods.com/skyrimspecialedition/mods/192814

Current Nexus version observed: **0.7.1**

Type:

- SKSE plugin / UI-performance fix
- no gameplay-content dependency identified in the 17.3.7 delta
- supports Skyrim 1.5.97, 1.6+ and 1.7+

Planned checks:

- verify files and requirements against current NEFARAM stack
- confirm no conflicting SKSE plugin already provides the same fix
- inspect MO2 file conflicts
- in-game inventory open / refresh / equip test

Status: **TO REVIEW**

---

## 2. Standing Stealth

Source:

https://www.nexusmods.com/skyrimspecialedition/mods/193088

Current Nexus version observed: **1.0.0**

Purpose:

- removes the crouch requirement for sneak attacks
- keeps Skyrim detection logic and normal sneak-attack multipliers
- can apply independently to player, followers and NPCs
- weapon categories are configurable through `SKSE\Plugins\StandingStealth.ini`

Requirements:

- SKSE64
- Address Library
- **Core Impact Framework 2.0.3+**

Important consequence for NEFARAM-Rhiven:

The current setup uses **Core Impact Framework 1.2.8**, so Standing Stealth cannot be added safely without first updating CIF.

Status: **TO REVIEW**

---

## 3. Core Impact Framework

Source:

https://www.nexusmods.com/skyrimspecialedition/mods/146873

Current NEFARAM-Rhiven version: **1.2.8**

Target version required / observed: **2.0.7**

### Relevant changes from 1.2.8 to 2.0.7

- CIF 2.0 is a near-complete internal refactor.
- redesigned filter system
- improved runtime mapping selection
- new hook system for multiple mods interacting with impact data
- expanded API and contextual hit data
- multiple crash fixes and null-safety improvements
- improved perk / magnitude / projectile / deferred-hit handling
- updated CommonLibSSE-NG
- 2.0.6 adds support for game versions 1.7.99+ while remaining backward compatible with 1.6.1170 and earlier supported versions
- 2.0.7 fixes a potential CTD caused by reading the magnitude of an invalid base effect

Compatibility statement from the author:

- mods built for previous CIF versions are intended to remain compatible with CIF 2.0
- Nexus states that CIF can be safely installed / updated / uninstalled mid-playthrough

Planned checks:

- identify every current NEFARAM mod depending on CIF
- confirm no obsolete CIF configuration file requires preservation
- replace 1.2.8 with 2.0.7
- inspect MO2 conflicts
- test CIF-dependent effects in game
- only then install / enable Standing Stealth

Status: **TO REVIEW**

---

## 4. Meshes Optimization Project

Source:

https://www.nexusmods.com/skyrimspecialedition/mods/160495

Current Nexus version observed: **1.5.6**

Purpose:

- optimized meshes intended to reduce draw calls
- performance improvement with minimal visual loss
- distributed through a FOMOD
- contains compatibility / optimized mesh options for several world and city mods

Known relevant supported mods include, among others:

- Capital Whiterun Expansion
- Northern Roads
- Cities of the North variants
- JK's outskirts modules
- other architecture / city additions

This is the **highest-risk item of the 17.3.7 delta for the current customized visual stack** because it can intentionally overwrite meshes already supplied by NEFARAM.

Planned checks before installation:

- retrieve NEFARAM Discord guidance for the exact FOMOD selections
- identify which MOP options correspond to mods actually present in NEFARAM
- inspect all MO2 conflicts before deciding overwrite priority
- verify interaction with SMIM and current architecture / landscape mesh stack
- test representative locations in game after installation

Do not install this mod blindly from default FOMOD choices.

Status: **TO REVIEW - WAITING FOR NEFARAM DISCORD DETAILS**

---

## 5. SLSF Reloaded LL

NEFARAM 17.3.7 states that SLSF Reloaded LL was updated.

Current NEFARAM 17.3.6 version: **4.1.0**

Target NEFARAM 17.3.7 version: **4.1.1**

Reason for the NEFARAM update:

- the author removed the previously distributed **4.1.0** package
- **4.1.1** was published as its replacement / update
- this is therefore a maintenance-version refresh rather than a deliberate NEFARAM feature change

Planned checks:

- retrieve LoversLab changelog / release notes for 4.1.1 if available
- compare package structure with 4.1.0
- preserve existing configuration if appropriate
- inspect plugin / script conflicts
- test SLSF initialization and MCM after update

Status: **TO REVIEW - VERSION TARGET CONFIRMED (4.1.0 -> 4.1.1)**

---

## Recommended migration order

1. **Inventory Refresh Fix**
2. **Core Impact Framework 1.2.8 -> 2.0.7**
3. validate CIF-dependent mods
4. **Standing Stealth**
5. **SLSF Reloaded LL -> 4.1.1** after changelog review
6. **Meshes Optimization Project** only after NEFARAM FOMOD / overwrite guidance is known
7. final MO2 conflict pass
8. xEdit checks where applicable
9. game launch and functional tests
10. update Rhiven load-order snapshots
11. change repository baseline to **NEFARAM 17.3.7** only after validation

## Current migration status

- Wabbajack update: **NOT USED**
- Current validated base: **NEFARAM 17.3.6**
- Target base: **NEFARAM 17.3.7**
- Save compatibility announced by NEFARAM: **YES**
- Manual migration: **IN PREPARATION**
