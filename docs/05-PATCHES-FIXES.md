# 05 - Patches & fixes

This file documents every Rhiven-specific compatibility patch, manual fix, generated config or targeted override.

## Current

### Terrain Helper generated configuration

- Mod: `Terrain Helper - Generated INI - Rhiven`
- File: `Shaders\Features\TerrainHelper.ini`
- Origin: generated into MO2 Overwrite
- Action: moved into its own dedicated mod
- Reason: keep MO2 Overwrite clean and preserve stock files

### EBT / Just Blood body blood separation

- **Target mods:** Enhanced Blood Textures 4.0 + Just Blood - Dirt and Blood Lite
- **Patch:** `EBT - Just Blood Body Patch - Rhiven`
- **Problem:** EBT and Just Blood can both provide actor body blood visuals
- **Fix:** neutralize EBT body blood decals and leave actor blood to Just Blood
- **Load-order requirement:** patch must load after EBT in the MO2 left pane
- **Test status:** **VALIDATED**
- **Notes:** no ESP/plugin added

### Widget Addon compatibility with Bathing in Skyrim Renewed

- **Target mods:** Widget Addon 1.7.2 + Bathing in Skyrim Renewed 2.7.11
- **Problem:** original widget targets the legacy Bathing in Skyrim implementation
- **Fix:** enable the Widget Addon compatibility option in the BiSR FOMOD
- **Load-order requirement:** Widget Addon above BiSR so the BiSR compatibility files win conflicts
- **Test status:** **VALIDATED**
- **Notes:** `Dirtiness Lvl5 Fix` remains tracked but intentionally not installed unless level-5 dirtiness breaks the widget

### ConsoleUtil compatibility for Wash Me

- **Target mod:** Bathing in Skyrim - Wash Me - Renewed
- **Problem:** Nexus lists ConsoleUtilSSE NG as a recommended optional dependency
- **Decision:** do **not** install ConsoleUtilSSE NG because NEFARAM already uses `ConsoleUtil Extended`
- **Reason:** ConsoleUtil Extended is intended as the replacement implementation and duplicate ConsoleUtil installs should be avoided
- **Test status:** **VALIDATED**

### Pandora output path correction

- **Tool:** Pandora Behaviour Engine
- **Problem:** Output Folder was pointing directly to `Game Root\Data`
- **Fix:** changed Pandora Output Folder to:
  - `C:\JEUX\NEFARAM\mods\Pandora Output`
- **Skyrim Data remains:**
  - `C:\JEUX\NEFARAM\Game Root\Data`
- **Rule:** output points to the root of the MO2 `Pandora Output` mod, not to `meshes` or another subfolder
- **Test status:** **VALIDATED**
- **Result:** Pandora generation completed successfully

### On-demand bikini armor enchanting fix

- **Target mods:** bikini / skimpy armor pieces used by Eleanor
- **Trigger:** only when a specific armor piece cannot be enchanted in-game
- **Decision:** do not install a broad third-party enchanting fix pre-emptively; patch only the affected pieces actually encountered during play
- **Procedure:**
  1. Open the affected armor plugin in xEdit with only its required masters.
  2. Locate the relevant `ARMO` record.
  3. Copy it as an override into the dedicated Rhiven personal patch plugin.
  4. Add the missing enchanting-related keyword used by the equivalent enchantable armor records.
  5. Save the patch and keep it loading after the source armor plugin.
  6. Re-test enchanting in-game.
- **Rule:** never edit the original armor mod directly.
- **Reason:** keeps the build minimal, avoids unnecessary overrides, and preserves update safety.
- **Test status:** **ON DEMAND**
- **Notes:** if multiple pieces from the same armor pack prove affected, batch them into the same Rhiven patch instead of creating separate plugins.

### OMNOMS / O.S.H.I.T Object Impact Framework override

- **Target mods:** OMNOMS 1.3.0 + O.S.H.I.T + Object Impact Framework
- **File:** `SKSE\\Plugins\\ObjectImpactFramework\\OSHIT-OIF.json`
- **Problem:** the O.S.H.I.T OIF config can make Mimics destructible on impact, which can destroy the Mimic/container state and make its loot inaccessible.
- **Fix:** enable the OMNOMS `OSHIT Patch` and ensure the OMNOMS version of `OSHIT-OIF.json` wins the MO2 file conflict.
- **Current left-pane priority:** TNTR -> EET -> O.S.H.I.T -> OMNOMS -> Deadly Bear Trap -> Watch Your Step.
- **Important:** OMNOMS must remain below O.S.H.I.T in the MO2 left pane for this specific file override.
- **Structural test status:** **VALIDATED**
- **Gameplay test status:** **PENDING EARLY REAL-PLAYTHROUGH TESTING**

### OMNOMS SkyPatcher distribution

- **Framework:** `SkyPatcher - AE - Rhiven`
- **Enabled distribution:** Magic Vendors + Spell Tomes
- **Disabled distribution:** General Vendors
- **Purpose:** distribute the OMNOMS `Banish Mimic` scroll without adding a broad generic-vendor distribution.
- **Test status:** **INITIALIZATION VALIDATED / IN-GAME ACQUISITION PENDING**

### PAMA / NEFARAM ZaZ ankle chains override

- **Target mods:** Bad Ends Revived: Windhelm + `NEFARAM Patches`
- **Patch mod:** `PAMA - NEFARAM ZaZ Ankle Chains Patch - Rhiven`
- **File:** `meshes\\ZaZ-UltimateDataPack\\ZaZ - HDT\\ZaZAnkleChainsRagdolls_1.nif`
- **Problem:** Bad Ends Windhelm ships its own older copy of the ZaZ ankle-chain ragdoll mesh and wins by MO2 priority when kept in the dedicated late PAMA block.
- **Fix:** copy the NEFARAM-patched version into a dedicated Rhiven compatibility mod placed after Bad Ends Windhelm.
- **Reason:** preserve the NEFARAM-specific ZaZ mesh while keeping the whole PAMA stack below the NEFARAM late-loader architecture.
- **Test status:** **STRUCTURAL FIX APPLIED / IN-GAME VISUAL CHECK PENDING**

### PAMA / Windhelm navmesh compatibility patch

- **Target mods:** Bad Ends Revived: Windhelm + WindhelmSSE + Capital Windhelm Expansion / Skyrim Sewers integration
- **Patch:** `PAMA - Windhelm Navmesh Patch - Rhiven.esp`
- **Plugin type:** ESP with ESL flag
- **Problem:** `PrisonAlternative_Executions_WindHelm.esp` reintroduced old / vanilla-like navmesh geometry over newer Windhelm fixes.
- **Fixes preserved:**
  - `000FC117` / `WindhelmBridge04` copied from `WindhelmSSE - Exterior NavMesh Fixes.esp`
  - `0004B66C` / `WindhelmCandlehearthHallExterior` copied from `CapitalWindhelmExpansion - SkyrimSewers.esp`
- **Explicit master added:** `PrisonAlternative_Executions_WindHelm.esp`
- **Load-order requirement:** patch must load after Bad Ends Windhelm and the Windhelm source/fix plugins it reconciles.
- **xEdit validation:** `Check for Errors` — **0 errors, 7 records processed**
- **Test status:** **XEDIT VALIDATED / IN-GAME PATHING CHECK PENDING**

## Future patch template

### Patch name

- **Target mods:**
- **Problem:**
- **Fix:**
- **Files / records affected:**
- **Load-order requirement:**
- **Test status:**
- **Notes:**
