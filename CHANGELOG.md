# Changelog

## 2026-10-07

### NEFARAM 17.3.7 — active Rhiven baseline

- Current customized instance now runs on **NEFARAM 17.3.7**.
- The active setup includes the 17.3.7 migration components previously staged for review:
  - Inventory Refresh Fix
  - Standing Stealth
  - Core Impact Framework 2.0.7
  - Meshes Optimization Project
  - SLSF Reloaded 4.1.1
- Refreshed the MO2 left-pane and right-pane/plugin snapshots so the repository matches the current local instance.

### TNTR / trap ecosystem — initial integration

- Added modern runtime frameworks in `43 - Added Mods SFW`:
  - `SkyPatcher - AE - Rhiven`
  - `Object Impact Framework (OIF) - Rhiven`
- Added the TNTR trap stack in `44 - Added Mods NSFW`:
  - `Trap Needs to be Real Trap - Rhiven` — TNTR 0.74
  - `EET Extra Evil Traps - Rhiven` — EET 1.2.3
  - `O Skyrim Has Insane Traps - Rhiven`
  - `OMNOMS Not So Obvious Mimics - Rhiven` — OMNOMS 1.3.0
  - `Deadly Bear Trap - Rhiven`
  - `Watch Your Step - Rhiven` — v1.2
- TNTR FOMOD selections:
  - Replacer enabled
  - New Baka Traps enabled
  - OAR patch selected
  - Nemesis-style behavior patch selected for use with Pandora
- EET configured with patched Bear Trap and Snare Trap scripts for TNTR 0.73 / 0.74.
- OMNOMS configured with:
  - patched TNTR v0.7x Mimic script
  - Mimic activation-text replacement
  - experimental vanilla-chest shader replacement disabled
  - SkyPatcher distribution to Magic Vendors + Spell Tomes
  - General Vendors distribution disabled
  - O.S.H.I.T compatibility patch enabled
- Corrected MO2 conflict priority so OMNOMS loads after O.S.H.I.T and its `SKSE\\Plugins\\ObjectImpactFramework\\OSHIT-OIF.json` override wins as intended.
- Watch Your Step uses the current v1.2 main file for TNTR >0.46; the old O.S.H.I.T v0.4-only optional file was not installed.
- Initial New Game validation:
  - game launch: **OK**
  - no startup CTD observed
  - no obvious initialization anomaly observed
  - TNTR MCM registered
  - TNTR: Extra Evil Traps MCM registered
  - TNTR: Not So Obvious Mimics MCM registered
- Stack status: **technical initialization validated / real-game field testing still pending**.
- Planned early-playthrough checks include Mimics, Bear Trap, Snare/QTE, O.S.H.I.T / Watch Your Step placement, and interactions with Fill Her Up Baka, Devious Devices and Acheron / Practical Defeat.
- Load-order snapshot refresh intentionally deferred until the remaining planned mods are installed.

### Outfit Gallery - Visual Outfit Manager

- Installed `Outfit Gallery - Visual Outfit Manager - Rhiven` in `43 - Added Mods SFW`.
- Initial file-conflict review showed only documentation / license file overlaps with other CommonLibSSE-based mods; no functional conflict observed.
- In-game validation:
  - SKSE menu opens correctly: **OK**
  - default gallery hotkey `F8`: **OK**
  - no startup CTD observed
- Purpose: provide Eleanor with a scalable visual wardrobe manager for the large personal outfit / armor collection.
- Status: **Validated**.

### Regional Outfitters - Stalls of Skyrim

- Installed `Regional Outfitters - Stalls of Skyrim - Rhiven` in `43 - Added Mods SFW`.
- SkyPatcher framework reused from the current Rhiven setup.
- FOMOD compatibility patches selected for mods present in NEFARAM-Rhiven:
  - Capital Windhelm
  - Obscure's College of Winterhold
  - AI Overhaul
- Other city / college overhaul patches left disabled because the corresponding mods are not present in the current modlist.
- In-game validation performed with console `coc` tests across several cities.
- Results:
  - game stability: **OK**
  - no CTD observed
  - no obvious stall / vendor placement problem observed in the tested locations
- Status: **Validated** for initial integration; normal long-term inventory refresh behavior will be observed during the real playthrough.


### Private Needs - Orgasm 1.11.1

- Installed / updated `Private Needs - Orgasm 1.11.1 - Rhiven` in `44 - Added Mods NSFW`.
- Previous personal reference version was 1.8.3; 1.11.1 includes substantial SKSE-side runtime changes and fixes.
- Rhiven usage remains deliberately limited to **natural needs**:
  - bladder
  - bowel
  - urination / defecation animations and interactions
  - orgasm-related urination disabled in MCM
- Optional integrations intentionally skipped for now:
  - Dynamic Bloodpool Framework / puddles
  - Dooty
  - SkyrimNet
- Initial in-game validation:
  - launch: **OK**
  - bladder fullness percentage displayed correctly
  - bowel fullness percentage displayed correctly
  - vanilla chair / furniture toilet interaction works correctly
  - no CTD observed
- The tested functionality worked before a new Pandora generation, so no missing behavior dependency was observed for the current use case.
- Status: **Validated for the Rhiven natural-needs configuration**.

### NakedStart 1.1.0 — rejected

- Tested `NAKED START - NO ESP NO CRASH 1.1.0` as a possible no-record naked-start solution.
- Correct SKSE plugin structure confirmed.
- Multiple NEFARAM start tests retained the complete randomly assigned outfit / weapon set.
- Config tests with a longer settle window and item-menu shutdown disabled did not change the behavior.
- Likely incompatibility: NEFARAM begins from the supplied `NEFARAM_Start` save and then runs its custom Skyrim Unbound / RaceMenu / teleport sequence, while NakedStart expects a true Skyrim `New Game` event to arm itself.
- Decision: **Rejected / removed from final build**.


### Riverhome

- Installed Riverwood Riverhome SE/AE Port as an additional Eleanor home.
- xEdit review found an invalid deleted override of vanilla cell `0005EAC7` (`aaaMarkers`) in `Riverhome v1.4.esp`.
- Removed only the bad Riverhome override while preserving the actual Riverhome cell.
- Re-ran xEdit `Check for Errors`: **0 errors**.
- In-game validation:
  - exterior integration: **OK**
  - bridge / river placement: **OK**
  - interior: **OK**
  - no obvious terrain break or major visual conflict observed
- No DynDOLOD / xLODGen regeneration performed yet; exterior LOD will be handled during the final generated-output pass.

### Road Signs Overhaul 2.0

- Installed:
  - `Road Signs Overhaul 2.0 - Rhiven`
  - `Road Signs 2.0 - Questionable Clutter Remover (BOS) - Rhiven`
  - `Road Signs Overhaul 2.0 - Blended Roads Patch(BOS) - Rhiven`
- Kept the existing `Skyrim Vanilla Remix Signs` texture stack.
- In-game validation showed readable, correctly placed signs around Riverwood / Whiterun / Falkreath routes.
- No LOD regeneration required at this stage.
- Added a future checklist task for a **Rhiven French texture-only road-sign translation** while preserving the original visual style.

### TK Dodge

- Created dedicated MO2 separator `37.1 - TK Dodge` inside Late Loaders.
- Installed the final TK Dodge stack:
  - `IFrame Generator RE AE Support - Rhiven`
  - `TK Dodge For RE - Rhiven`
  - `TK Dodge RE - Script Free - Rhiven`
  - `TK dodge firstperson 8 ways dodge - Rhiven`
  - `TK Dodge Animation Pandora Fix Patch - Rhiven`
  - `TK Dodge NG - Rhiven`
  - `Dynamic Dodge Animation - Rhiven`
- TK Dodge RE FOMOD:
  - standalone
  - sheathed dodge enabled
  - concentration-spell cancel enabled
  - forward dodge scurry fix enabled
- Dynamic Dodge Animation configured for:
  - `TK Dodge RE-0.55-rc3`
  - `Sway` attack-cancel behavior
- TK Dodge NG initial configuration keeps `StepDodge = false` for rolling dodges.
- Pandora correctly detected:
  - `TK Dodge RE / Ultimate Combat`
  - `TK Dodge Standalone`
- Pandora generation completed successfully with **38,375 total animations added**.
- In-game validation completed successfully:
  - out-of-combat dodge: **OK**
  - combat dodge: **OK**
  - no T-pose / behavior failure observed
- TK Dodge stack marked **Validated**.

### Documentation / repository maintenance

- Added Markdown technical counterparts for easier repository-side consultation:
  - `docs/guides/NEFARAM_Guide_Installation_Creation_Kit_MO2_FR.md`
  - `docs/guides/NEFARAM_Guide_TK_Dodge_FR.md`
  - `docs/guides/NEFARAM_Modding_Guide_1.4_FR.md`
- Kept the original DOCX guides as the richer visual references.
- Updated `docs/13-PRE-PLAYTHROUGH-CHECKLIST.md` with the future French Road Signs texture task.
- Synchronized the current MO2 left/right load-order reference files with the local NEFARAM-Rhiven instance.

## 2026-10-06

### NEFARAM 17.3.7 migration preparation

- NEFARAM 17.3.7 detected as a save-compatible update.
- Chosen strategy: controlled manual migration instead of running Wabbajack over the customized installation.
- Identified the 17.3.7 delta:
  - Inventory Refresh Fix
  - Standing Stealth
  - Meshes Optimization Project
  - SLSF Reloaded LL update
- Confirmed current Core Impact Framework is 1.2.8 while Standing Stealth requires CIF 2.0.3+.
- Target CIF version identified as 2.0.7.
- Target SLSF package currently identified as `SLSF Reloaded 4.1.1.zip`; detailed release-note comparison still pending.
- Meshes Optimization Project held for review pending NEFARAM Discord guidance on FOMOD / overwrite choices.
- Added dedicated migration document: `docs/14-UPDATE-17.3.6-TO-17.3.7.md`.

## 2026-10-05

### Eleanor outfits — final stack

- Finalized the `15.1 - Outfits Eleanor` block with the definitive personal outfit list.
- Added the second outfit batch:
  - ELLE - Delicate Zhuque 3BA
  - COCO Luscious Lady
  - COCO Caress of Venus
  - Nocturne Armor 3BA - SMP
  - Spartan Hoplite Female Version
  - Daggerfall Archmage Outfit Remake 3BA stack, including 1.2 update, NON CS PBR override and hood/cape physics fix
  - Sexy Tsun Armor 3BA ESL
  - Leolic Armor
  - Elf Stalhrim Bikini Armor
  - Dark Dreams + 3BA BodySlide conversion
  - Misc High Heels Stilettos Eins
- Kept Daggerfall's NON CS PBR files below the PBR base/update so they win the intended mesh/material overrides for the ENB setup.
- xEdit `Check for Errors` returned **0 errors** for the newly checked outfit plugins.
- Confirmed `Dark Dreams.esp` requires FormID compacting before ESL flagging; it is intentionally kept as a heavy ESP.
- `Bodyslide Output - Eleanor` remains last in the personal outfit block.

### Pre-playthrough checklist

- Added `docs/13-PRE-PLAYTHROUGH-CHECKLIST.md` as the definitive launch checklist for NEFARAM-Rhiven.
- Split the checklist into **Pre-install / Before New Game**, **Post-install / New Game**, and **Future / Optional backlog**.
- Added the planned outfit keyword / KID audit, translation pass, final MCM session, Lakeview validation, Pandora / generated-output checks and final go/no-go criteria.

## 2026-10-04

### Fertility system / Beeing Female NG

- Kept stock optional `Fertility Mode` disabled.
- Installed `Fertility Adventures Redux - Rhiven`.
- Installed `Beeing Female NG 3.6.0 - Rhiven`.
- Installed a cleaned / repacked `Beeing Female NG - HUD Re-Alignment Patch - Rhiven` containing only:
  - `BeeingFemale/HUD/Align1.ini` through `Align6.ini`
- BFNG FOMOD selections:
  - Open Animation Replacer
  - Fertility Adventures Redux patch
  - SPID item distribution
  - P.A.I.A base patch
  - P.A.I.A Expansion patch
  - SlaveTats womb / birth-count tattoo packs
- Deliberately skipped:
  - FMR-Immersive Effects patch
  - RS Children child actors
  - Creature child actors
  - SkyChild integration
- Confirmed NEFARAM uses `Simple Children`; no child-replacer migration was introduced.
- `Inflation Framework NG` reviewed and placed on Nexus tracking only; not installed unless native BodyMorph coexistence proves insufficient.
- Initial game launch:
  - BFNG 3.6.0 initialized correctly
  - MCM detected
  - SexLab compatibility: OK
  - Bathing in Skyrim compatibility: OK
  - BF items distributed correctly through the selected integration
  - console showed no BFNG blocking error
- Pandora regenerated after BFNG installation:
  - `FNIS_BeeingFemale_List` detected
  - generation completed successfully
  - **38,367 total animations added**
- Re-test after Pandora:
  - `BeeingFemale Animations = COMPATIBLE`
- Intended real-playthrough configuration is documented but **not applied yet**:
  - player pregnancy only
  - NPC pregnancy disabled
  - birth output = Gem
  - BodyMorph profile = CBBE 3BA
  - final HUD / morph amplitudes / fertility probabilities deferred to the global MCM setup after the definitive character start
- Heavy-plugin count at this stage: **211**.
- Added dedicated documentation: `docs/12-FERTILITY-SYSTEM.md`.

### Eleanor home / Lakeview Manor

- Created dedicated MO2 separator `41 - Homes Eleanor`.
- Created temporary holding separator `42 - Added Mods (En attente)`.
- Renumbered the dedicated map block to `43 - FWMF Maps - Rhiven`.
- Installed:
  - `Lakeview. Manor - As It Should Be - Rhiven`
  - `Lakeview Manor - As It Should Be - (CC) Fishing Compatibility Patch - Rhiven`
  - `Lakeview Manor - As It Should Be - FR - Rhiven`
- Lakeview is intentionally isolated from NEFARAM's existing player-home block and related fixes / patches.
- Full in-game validation is **pending** because normal Hearthfire progression is required: Falkreath Jarl progression, plot purchase and manor construction.
- Added dedicated documentation: `docs/11-HOME-ELEANOR.md`.


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

- Created MO2 separator `43 - FWMF Maps - Rhiven` (renumbered from the original personal `42` separator after adding Eleanor's home block).
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
