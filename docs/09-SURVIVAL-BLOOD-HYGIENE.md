# 09 - Survival, Blood & Hygiene Stack

This community guide documents a reproducible survival, blood and hygiene stack for **NEFARAM**. It distinguishes validated results from checks that each user should complete in their own game.

## Quick Setup / TL;DR

### Final responsibility split

| System | Selected component |
|---|---|
| Environmental blood | **Enhanced Blood Textures (EBT)** |
| Blood on actors | **Just Blood - Dirt and Blood Lite** |
| Hygiene, dirt and bathing | **Bathing in Skyrim - Renewed (BiSR) 2.7.11** |
| Needs and survival | **SunHelm** |
| Camping | **Campfire** |
| Hygiene/needs display | **Needs Widget AIO** — display only; validated in game with the supplied **Vel'Dun** preset |

### Essential BiSR stack

1. `Bathing in Skyrim - Renewed` **2.7.11**
2. `Bathing in Skyrim - BAIN (Multi-Language)`
3. `Zaki 8K-4K Textures for Bathing in Skyrim Renewed`
4. `Bathing in Skyrim - Renewed - Animal Fat and Linen`
5. `Bathing in Skyrim - Generic Soap Distribution`
6. `Bathing in Skyrim - Renewed - Seamless Soap`
7. `Bathing in Skyrim SE - SST MORE VISIBLE BUBBLES`
8. `Bathing in Skyrim - Wash Me` **1.3**
9. `Malignis Animations - Bathing in Skyrim Renewed` with the animation mods

### Critical points

- Place the BiSR mods together in your survival/gameplay area.
- Place Malignis with your animation mods, then rerun Pandora.
- **Needs Widget AIO** is the final retained display layer. Its supplied **Vel'Dun** preset is present, active and validated in game.
- Needs Widget AIO is **display only**: SunHelm remains the needs engine and BiSR remains the hygiene engine.
- The old **Widget Addon - Keep It Clean - Bathing in Skyrim** is retired, disabled and retained only for rollback.
- Run Pandora after the animation files are in place. The recorded successful generation detected all three BiSR lists and produced **38,349 animations**.
- On a new game, **enable BiSR in its MCM**; it is disabled by default.
- Before declaring the migration complete, confirm that `WA_BathWidget.esp` is inactive and refresh your exported MO2 mod and plugin lists.

---

## Status legend

- **Validated** — directly observed or successfully tested in the documented setup.
- **Installed / configured** — present or selected, but not fully validated in a normal playthrough.
- **Pending in-game validation** — must not be presented as confirmed yet.
- **Historical / rollback** — records an earlier working state, not the intended final active choice.

## Stack architecture

The stack deliberately assigns one main responsibility to each subsystem:

- **EBT = environment**
- **Just Blood = actors**
- **BiSR = hygiene**
- **SunHelm = needs**
- **Campfire = camping**
- **Needs Widget AIO = display only**

This avoids asking multiple mods to manage the same gameplay layer. **Needs Widget AIO is a display-only layer** and does not replace the SunHelm or BiSR gameplay systems.

## Blood layer

### Enhanced Blood Textures 4.0

Install **Enhanced Blood Textures 4.0** with the following options.

| FOMOD option | Selection |
|---|---|
| Install mode | **SPID Compatible** |
| Immersive Creatures patch | **No** |
| Blood size | **Default Splatter Size** |
| Wounds | **EBT - Default** |
| Drips | **Default** |
| Screen blood | **Default** |
| Blood color | User preference |

The MO2 conflict review found no direct file conflict with Just Blood.

### EBT Settings Loader

Install **Enhanced Blood Textures SE - Settings Loader (SPID Version)**.

- Version: **SPID 2.0.2**
- Selected to match the SPID installation of EBT 4.0.

### Just Blood - Dirt and Blood Lite

The stock NEFARAM mod is retained for actor blood visuals. It remains separate from EBT's environmental blood role.

### EBT / Just Blood body patch

Install the **EBT - Just Blood Body Patch**.

Source: [Enhanced Blood Textures Just Blood Just Not Enhanced Body Blood](https://www.nexusmods.com/skyrimspecialedition/mods/93414)

It disables EBT body-blood decals, leaves actor body blood to Just Blood, and prevents the two systems from overlapping on actors. It adds no ESP/plugin.

## Bathing in Skyrim - Renewed core

Install **Bathing in Skyrim - Renewed 2.7.11**.

- Version: **2.7.11**
- Placement: keep it with the other survival/gameplay mods, near the existing wash-basin, SunHelm and Campfire files.

### Recorded main FOMOD choices

| Category | Selection |
|---|---|
| Male textures | **Zaki's SOS** |
| Female textures | **Zaki's CBBE** |
| Base Object Swapper | **Yes** |
| Description Framework | **Yes** |
| SkyPatcher | **Yes** |
| Widget Addon compatibility | **Yes — historical installation choice; review during final cleanup because the addon is no longer active** |
| Bathing Token | **No** |
| First Person Messages | **No** |
| Source Scripts | **Yes** |
| Mod Organizer support | **Yes** |

Patches not selected:

- Complete Alchemy and Cooking Overhaul
- Licenses - Player Oppression
- Barefoot Realism
- Barefoot Realism Tweaked

### Multi-language BAIN package

Install **Bathing in Skyrim - BAIN (Multi-Language)** directly after the BiSR core.

- Localized plugin support was enabled.
- Language was left at **None**.
- The package does **not** include French.
- It remains useful as a localization-ready base for future translation work.

## BiSR addon stack

Install the following below the BiSR core unless a later conflict audit establishes a more precise exception:

| Order | Mod | Role / recorded choice |
|---:|---|---|
| 1 | `Zaki 8K-4K Textures for Bathing in Skyrim Renewed` | Dirt overlays. Female **Level 4 (Recommended)**; male dirt level **None**. |
| 2 | `Bathing in Skyrim - Renewed - Animal Fat and Linen` | BiSR crafting and washing resources. |
| 3 | `Bathing in Skyrim - Generic Soap Distribution` | Soap and wash-rag distribution. |
| 4 | `Bathing in Skyrim - Renewed - Seamless Soap` | Renewed-specific seamless soap file, version **1.2**. |
| 5 | `Bathing in Skyrim SE - SST MORE VISIBLE BUBBLES` | Optional effect producing approximately 30% more visible bubbles. |
| 6 | `Bathing in Skyrim - Wash Me` | Follower washing interactions. |

The legacy Bathing in Skyrim SE conversion is not required for the selected Seamless Soap file.

### Artisan Soaps

**Not retained.** It overlapped with the soap visual layer, and Seamless Soap plus More Visible Bubbles was selected as the simpler final visual stack.

### Wash Me - Renewed

Install **Bathing in Skyrim - Wash Me 1.3**.

| FOMOD option | Selection |
|---|---|
| Dialog conditions | **Any follower** |
| Animation type | **NSFW** |
| Basin type | **Big** |

Requirement review:

- BiSR 2.7.5 or later: satisfied by **2.7.11**;
- Backported Extended ESL Support: not required on Skyrim **1.6.1170**;
- ConsoleUtilSSE NG: not installed;
- NEFARAM already uses **ConsoleUtil Extended**;
- the full Dirt and Blood mod is not required for the selected BiSR main file.

## Needs Widget AIO and the retired widget layer

### Current decision

**Needs Widget AIO is the final retained widget solution.** It has been tested in game with its supplied **Vel'Dun** preset and remains separate from the underlying needs and hygiene engines.

| Item | Status |
|---|---|
| Needs Widget AIO | **Validated / retained as the final display layer** |
| Vel'Dun preset | **Present, active and tested in game** |
| Needs Widget AIO role | **Display only; SunHelm owns needs and BiSR owns hygiene** |
| Widget Addon - Keep It Clean - Bathing in Skyrim | **Retired / disabled / rollback only** |

Do not copy the old Widget Addon order or options into a new setup unless deliberately performing a rollback.

### Retired plugin warning

Older exported MO2 lists may still contain:

- `Widget Addon - Keep It Clean - Bathing In Skyrim` in the left pane;
- `WA_BathWidget.esp` in the right pane.

These entries belong to the retired Widget Addon setup. Keep the mod and `WA_BathWidget.esp` inactive, and export fresh MO2 mod and plugin lists before playthrough sign-off.

### Historical Widget Addon configuration

For rollback reference only, the retired configuration used Widget Addon 1.7.2 with:

- iNeed: **No**
- Vitality Mode: **No**
- iWant RND: **No**
- None of the above: **Yes**
- Widget Addon above BiSR so the BiSR Renewed compatibility files won conflicts.

The tracked `Dirtiness Lvl5 Fix for Widget Addon` was never installed. It is irrelevant while Widget Addon remains inactive and should not be added pre-emptively.

## MO2 order, plugins and conflicts

### General left-pane order

Use this as the documented relationship, not as an absolute priority number:

1. Existing NEFARAM wash-basin, survival, SunHelm and Campfire base files
2. BiSR core
3. BiSR BAIN multi-language package
4. Zaki textures
5. Animal Fat and Linen
6. Generic Soap Distribution
7. Seamless Soap
8. More Visible Bubbles
9. Wash Me
10. Malignis with the animation mods, after the other files it is intended to overwrite

Place Needs Widget AIO with the other interface and HUD mods. The validated installation has no MO2 file conflicts; do not copy ordering rules from the retired Widget Addon configuration.

### Recorded BiSR-related plugins

Older exported plugin lists may contain:

- `Bathing in Skyrim.esp`
- `WA_BathWidget.esp` — obsolete entry from the retired Widget Addon; keep it inactive
- `Bathing in Skyrim - Renewed Animal Fat and Linen.esp`
- `Malignis Sound FX.esp`
- `Bathing in Skyrim - Wash Me.esp`

### Known conflict decisions

- The EBT body patch leaves actor blood to Just Blood.
- Seamless Soap plus More Visible Bubbles replaces the rejected Artisan Soaps option.
- ConsoleUtil Extended is retained; no duplicate ConsoleUtilSSE NG installation is added.
- Pandora writes to its dedicated output mod, never directly to the game Data folder.
- MO2 Overwrite should be inspected after generation and intentional output kept in dedicated output mods.

## Animations and Pandora

### Malignis Animations

Place Malignis with your animation mods, after the other files it is intended to overwrite, then rerun Pandora.

### Pandora paths

- Pandora output: the root of your dedicated `Pandora Output` MO2 mod
- Skyrim Data: the `Data` directory in your NEFARAM game root

Point Pandora to the root of the `Pandora Output` MO2 mod. Do not target a `meshes` subfolder and do not write generated behavior files directly into the game Data directory.

### Validated Pandora result

Pandora detected:

- `FNIS_BiS_WashMe_List`
- `FNIS_Bathing_in_Skyrim_List`
- `FNIS_Bathing_in_Skyrim_Malignis_List`

Recorded result:

- **38,349 total animations added**;
- generation completed successfully;
- no blocking error observed.

This validates the recorded generation, not every future regeneration. Run Pandora again after any later animation change and confirm the new result independently.

## Integration with the wider NEFARAM stack

### SunHelm

SunHelm remains the needs/survival engine and BiSR handles hygiene. Needs Widget AIO only displays their information; this separation was tested in game with the Vel'Dun preset.

### Campfire

Campfire remains the camping layer. The existing NEFARAM Campfire base is retained; the separately reviewed Campfire 2026 replacement was not adopted.

### Just Blood and EBT

Just Blood handles blood on actors, while EBT handles environmental blood. The dedicated body patch prevents EBT from duplicating the actor layer.

### Simple Inn Bath and Xtended Stay

These are part of the planned inn/economy validation rather than a completed validation claim. Confirm at least one normal inn flow with the final room-price configuration before starting a long-term playthrough.

## Validation register

### Validated

- EBT 4.0 installed in SPID mode.
- EBT Settings Loader SPID 2.0.2 selected.
- Just Blood retained for actor blood.
- EBT / Just Blood body patch installed with no added plugin.
- BiSR 2.7.11 MCM detected.
- Blood-related MCM/options detected.
- BiSR addon stack detected.
- BiSR options visible in game.
- Bathing animations worked without an observed animation error.
- Wash Me and Malignis were detected by Pandora.
- Pandora generation completed with **38,349 animations**.
- The blood/hygiene stack launched and functioned in the recorded test environment.
- Recorded heavy-plugin count immediately after this stack: **203**.

- Needs Widget AIO is retained as the final display-only layer.
- The supplied Vel'Dun preset is present, active and tested in game.

### Pending in-game validation

- Confirm no duplicate survival or hygiene display remains.
- Confirm `WA_BathWidget.esp` is inactive.
- Enable BiSR in its MCM on a new game and verify that the setting persists after restart.
- Validate BiSR plus Simple Inn Bath in at least one inn.
- Validate Simple Inn Bath plus Xtended Stay with the final inn-price configuration.
- Validate dirt progression, bathing, soap consumption/effects and follower washing during normal play.
- Confirm SunHelm continues to own needs while BiSR owns hygiene.
- Confirm HUD positioning, fading, opacity and hotkey coexistence during the final UI/MCM session.
- Save, exit Skyrim completely, reload and confirm that the configuration persists.

## Troubleshooting and rollback

### Duplicate or overlapping widgets

1. Confirm that the retired Widget Addon is not active alongside Needs Widget AIO.
2. Check the right pane for `WA_BathWidget.esp`.
3. Review Needs Widget AIO, SunHelm, STB and other HUD entries during the final UI/MCM session.
4. Change one layer at a time and retest on a disposable save.

### BiSR does not appear to run

- Confirm `Bathing in Skyrim.esp` is active.
- Allow MCM registration to finish.
- Open the BiSR MCM and enable the mod; it is disabled by default.
- Save, restart the game and verify persistence before changing other systems.

### Bathing animation failure or T-pose

- Confirm the BiSR, Wash Me and Malignis animation files are enabled.
- Re-run Pandora to the dedicated output mod.
- Check that all three recorded BiSR lists are detected.
- Inspect MO2 Overwrite and the Pandora output mod before testing again.

### Actor/environment blood overlap

- Confirm the EBT / Just Blood body patch is enabled after EBT.
- Keep EBT responsible for the environment and Just Blood responsible for actors.

### Soap or bubble visual conflict

- Keep the selected Seamless Soap and More Visible Bubbles combination.
- Do not add Artisan Soaps unless deliberately re-auditing the visual layer.

### Rollback strategy

- Keep a disposable test save and an MO2 backup before changing widget or survival layers.
- Needs Widget AIO is the intended final choice; Widget Addon may be kept temporarily only as a disabled rollback reference.
- If rollback becomes necessary, restore one known configuration at a time. Do not activate both display layers together.
- Re-export both MO2 panes after the final choice is confirmed.

## Before a long-term playthrough

- [x] Keep Needs Widget AIO active as the final display-only layer with the validated Vel'Dun preset.
- [ ] Confirm the retired Widget Addon is disabled or removed from the active mod list.
- [ ] Confirm `WA_BathWidget.esp` is inactive.
- [ ] Refresh the exported MO2 left-pane and right-pane lists.
- [ ] Run Pandora after the last animation-related change and verify a clean completion.
- [ ] Inspect MO2 Overwrite and generated output mods.
- [ ] Start from the supplied **NEFARAM_Start** save, as required by the project baseline.
- [ ] Let MCM registration settle, then enable BiSR.
- [ ] Complete the final SunHelm/BiSR/Needs Widget AIO HUD and MCM consistency pass.
- [ ] Test an inn with BiSR + Simple Inn Bath and the final economy settings.
- [ ] Perform a save / full exit / reload test.
- [ ] Mark remaining checks as validated only after they have been directly observed.

## Final decision

The retained architecture is:

- **EBT = environment**
- **Just Blood = actors**
- **BiSR = hygiene**
- **SunHelm = needs**
- **Campfire = camping**
- **Needs Widget AIO = display only**

The core blood, BiSR and Pandora integration has a documented successful validation. **Needs Widget AIO is the retained and validated display-only layer**, with its supplied **Vel'Dun** preset tested in game; SunHelm remains the needs engine and BiSR remains the hygiene engine.
