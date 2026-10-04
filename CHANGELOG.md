# Changelog

## 2026-10-04

### User Interface / QoL

- Installed `Compare Equipment NG` v0.3.18 in `04 - User Interface`.
- Kept QuickLoot IE optional / not required for this setup.
- Confirmed the mod is pure SKSE and adds no ESP/plugin.
- In-game validation:
  - comparison cards: **OK**
  - item differences: **OK**
  - armor-type mismatch color warning: **OK**
  - Dragonborn UI compatibility: **OK**
- Compare Equipment NG marked **Validated**.

### Blood architecture

- Kept stock `Just Blood - Dirt and Blood Lite` for actor blood.
- Installed `Enhanced Blood Textures - Rhiven` v4.0 in **SPID Compatible** mode.
- Installed `Enhanced Blood Textures SE - Settings Loader (SPID Version) - Rhiven` v2.0.2.
- Installed `EBT - Just Blood Body Patch - Rhiven` to prevent EBT body-blood overlap with Just Blood.
- Validated the split:
  - **EBT = environment**
  - **Just Blood = actors**

### Bathing in Skyrim Renewed

- Installed `Bathing in Skyrim - Renewed - Rhiven` v2.7.11.
- Installed source scripts and MO2 support files.
- Enabled Base Object Swapper, Description Framework, SkyPatcher and Widget Addon compatibility.
- Selected Zaki SOS / CBBE texture families in the BiSR FOMOD.
- Installed `Bathing in Skyrim - BAIN (Multi-Language) - Rhiven`.
- Confirmed the BAIN package currently provides no French language pack; localized plugin support retained for future translation work.

### BiSR addon stack

- Installed `Zaki 8K-4K Textures for Bathing in Skyrim Renewed - Rhiven`.
- Installed `Bathing in Skyrim - Renewed - Animal Fat and Linen - Rhiven`.
- Installed `Bathing in Skyrim - Generic Soap Distribution - Rhiven`.
- Installed `Bathing in Skyrim - Renewed - Seamless Soap - Rhiven`.
- Installed `Bathing in Skyrim SE - SST MORE VISIBLE BUBBLES - Rhiven`.
- Installed `Bathing in Skyrim - Wash Me - Rhiven` v1.3.
- Wash Me FOMOD:
  - Any follower
  - NSFW
  - Big basin
- Installed original `Widget Addon - Keep It Clean - Bathing in Skyrim - Rhiven` v1.7.2.
- Widget FOMOD set to `None of the above` because NEFARAM uses SunHelm.
- BiSR is loaded after the Widget Addon so its Renewed compatibility patch wins.
- Reviewed Artisan Soaps but did not retain it because Seamless Soap was preferred for the final visual stack.
- Added `Dirtiness Lvl5 Fix for Widget Addon` to Nexus tracking only; not installed unless needed.

### Animations / Pandora

- Moved Malignis Animations to the bottom of `24 - Animations`.
- Corrected Pandora output path from the game Data directory to:
  - `C:\JEUX\NEFARAM\mods\Pandora Output`
- Pandora detected:
  - `FNIS_BiS_WashMe_List`
  - `FNIS_Bathing_in_Skyrim_List`
  - `FNIS_Bathing_in_Skyrim_Malignis_List`
- Pandora generation completed successfully with **38,349 total animations added**.

### Eleanor outfits / BodySlide

- Created dedicated separator `15.1 - Outfits Eleanor`.
- Added the first personal Eleanor outfit batch:
  - Invicta Couture Black Rose
  - Silver Witch
  - DX Fetish Fashion Volume II
  - Invicta Couture Lingerie
  - Chain Bikini Armor
  - Dark Rebel
  - Aradia Bikini
  - Aether
  - Lady Ritual
  - Bisquits Priestess of Mara
  - Forgotten Princess
  - COCO 2B Wedding Outfit
  - MME Milk Harness v3
- Kept required BHUNP source packages for the Invicta conversions while using their CBBE 3BA conversions for Eleanor.
- Created dedicated generated-output mod `Bodyslide Output - Eleanor`.
- Corrected BodySlide output path to:
  - `C:\JEUX\NEFARAM\mods\Bodyslide Output - Eleanor`
- Used `- Zeroed Sliders -` to preserve OBody NG morph handling.
- Generated the full added-outfit BodySlide batch.
- Selected CBBE 3BA **Complex Material (CM)** variants for MME Milk Harness v3 instead of PBR.
- Confirmed the newly added outfit plugins are already ESL-flagged / ESP-FE.
- Adopted a plugin-order convention that keeps personal additions together before FWMF while preserving the technical late-loader / generated-plugin structure.
- Added dedicated documentation: `docs/10-OUTFITS-ELEANOR.md`.
- In-game visual / physics validation of the outfit batch remains pending.

### Validation

- Game launch: **OK**
- New BiSR MCM/options: **OK**
- Blood options / MCM: **OK**
- Animations: **OK**
- No blocking animation or compatibility issue observed.
- Blood + hygiene stack marked **Validated**.
- Heavy-plugin count after the stack: **203**.
- Added dedicated documentation: `docs/09-SURVIVAL-BLOOD-HYGIENE.md`.

## 2026-10-03

### Baseline

- Installed and validated NEFARAM 17.3.6.
- Created MO2 profile `ELEANOR Stable`.
- Numbered MO2 separators.
- Adopted `- Rhiven` suffix for personal additions.

### Terrain Helper

- Isolated generated `TerrainHelper.ini` from MO2 Overwrite.
- Created `Terrain Helper - Generated INI - Rhiven`.

### Dragonborn UI

- Installed `Dragonborn UI - SkyUI Reskin - Rhiven`.
- Kept the existing NEFARAM UI stack active.
- Selected Knotwork-compatible system menu.
- Enabled Sovngarde Font.
- Enabled More Informative Console patch.
- Initial conflict review showed primarily expected UI/visual overwrites.
- In-game validation completed successfully.
- Dragonborn UI marked **Validated**.
- Identified the remaining unskinned window as Skyrim Character Sheet.
- Installed `Dragonborn Reskin - Skyrim Character Sheet - Rhiven`.
- Character Sheet reskin validated successfully in-game.

### Wheeler / Perfected Wheeler

- Restored Wheeler functionality using the modern Perfected Wheeler branch.
- Installed `Wheeler - Quick Action Wheel Of Skyrim - Rhiven`.
- Installed `Perfected Wheeler - Apocrypha Menu Framework - Rhiven`.
- Reused NEFARAM's existing `SKSE Menu Framework` as the supported configuration framework.
- Did **not** reinstall the legacy `dMenu` / `dMenu NG` chain.
- Installed `Dragonborn - Wheeler Reskin - Rhiven`.
- Installed `Dragonborn - Wheeler Reskin Edge UI Color Options - Rhiven`.
- Confirmed Perfected Wheeler appears in the SKSE Mod Control Panel.
- Confirmed Wheeler opens correctly in-game.
- Confirmed resize / layout settings work correctly.
- Initial test used the default `Caps Lock` binding; final Rhiven keymap will be rebuilt before the real playthrough.
- Confirmed the four Wheeler mods add no ESP/plugin.
- Wheeler stack marked **Validated**.

### FWMF / Paper Map

- Created MO2 separator `42 - FWMF Maps - Rhiven`.
- Installed `Flat World Map Framework FOMOD Lite - Rhiven` v1.9.990.
- Selected Flat Map Markers AE Updated for Skyrim 1.6.629–1.7.99.
- Selected Skyrim-only map whitelist for the initial setup.
- Enabled Water for ENB support.
- Enabled EVLaS patch.
- Enabled Lux patch.
- Enabled Seasons of Skyrim support for Skyrim.
- Installed the integrated FWMF MCM.
- Installed `Skyrim Paper Map by Caro Tuts for FWMF - Rhiven`.
- Confirmed that the Caro Tuts map itself adds no ESP.
- FWMF plugins installed at the bottom of the plugin order.
- In-game validation completed successfully with no purple map or missing-texture issue.
- FWMF + Caro Tuts marked **Validated**.

### Repository

- Created initial NEFARAM-Rhiven documentation structure.
