# 09 - Survival, Blood & Hygiene Stack

This guide documents the Rhiven survival, blood and hygiene stack built on **NEFARAM 17.3.8**. It is intended as a reproducible setup reference for experienced NEFARAM users while keeping a clear distinction between confirmed results and checks that still require the definitive playthrough.

## Quick Setup / TL;DR

### Final responsibility split

| System | Selected component |
|---|---|
| Environmental blood | **Enhanced Blood Textures (EBT)** |
| Blood on actors | **Just Blood - Dirt and Blood Lite** |
| Hygiene, dirt and bathing | **Bathing in Skyrim - Renewed (BiSR) 2.7.11** |
| Needs and survival | **SunHelm** |
| Camping | **Campfire** |
| Hygiene/needs display | **iNeeds** — current replacement; exact setup still to be documented and validated |

### Essential BiSR stack

1. `Bathing in Skyrim - Renewed - Rhiven` **2.7.11**
2. `Bathing in Skyrim - BAIN (Multi-Language) - Rhiven`
3. `Zaki 8K-4K Textures for Bathing in Skyrim Renewed - Rhiven`
4. `Bathing in Skyrim - Renewed - Animal Fat and Linen - Rhiven`
5. `Bathing in Skyrim - Generic Soap Distribution - Rhiven`
6. `Bathing in Skyrim - Renewed - Seamless Soap - Rhiven`
7. `Bathing in Skyrim SE - SST MORE VISIBLE BUBBLES - Rhiven`
8. `Bathing in Skyrim - Wash Me - Rhiven` **1.3**
9. `Malignis Animations - Bathing in Skyrim Renewed - Rhiven` in the animation block

### Critical points

- Keep the BiSR block in MO2 section **`21 - Survival`** and Malignis in **`24 - Animations`**.
- The old **Widget Addon - Keep It Clean - Bathing in Skyrim** is not part of the intended final active stack. It has been replaced by **iNeeds**.
- **Needs Widget AIO is also no longer the final display choice.** It may be retained only as rollback material until cleanup is complete.
- Do not infer undocumented iNeeds options. Its version, exact MO2 entry, integration settings and final HUD configuration are **to be confirmed**.
- Run Pandora after the animation files are in place. The recorded successful generation detected all three BiSR lists and produced **38,349 animations**.
- On the definitive New Game, **enable BiSR in its MCM**; it is disabled by default.
- Before declaring the migration complete, confirm that `WA_BathWidget.esp` is inactive and refresh both MO2 snapshots.

---

## Status legend

- **Validated** — directly observed or successfully tested in the documented setup.
- **Installed / configured** — present or selected, but not fully validated for the definitive playthrough.
- **Pending in-game validation** — must not be presented as confirmed yet.
- **Historical / rollback** — records an earlier working state, not the intended final active choice.

## Stack architecture

The stack deliberately assigns one main responsibility to each subsystem:

- **EBT = environment**
- **Just Blood = actors**
- **BiSR = hygiene**
- **SunHelm = needs**
- **Campfire = camping**

This avoids asking multiple mods to manage the same gameplay layer. iNeeds is documented here only as the current display/widget replacement; the repository does not yet contain enough information to claim a broader gameplay role or prescribe detailed settings for it.

## Blood layer

### Enhanced Blood Textures 4.0

Installed as `Enhanced Blood Textures - Rhiven`.

| FOMOD option | Selection |
|---|---|
| Install mode | **SPID Compatible** |
| Immersive Creatures patch | **No** |
| Blood size | **Default Splatter Size** |
| Wounds | **EBT - Default** |
| Drips | **Default** |
| Screen blood | **Default** |
| Blood color | Personal visual choice |

The MO2 conflict review found no direct file conflict with Just Blood.

### EBT Settings Loader

Installed as `Enhanced Blood Textures SE - Settings Loader (SPID Version) - Rhiven`.

- Version: **SPID 2.0.2**
- Selected to match the SPID installation of EBT 4.0.

### Just Blood - Dirt and Blood Lite

The stock NEFARAM mod is retained for actor blood visuals. It remains separate from EBT's environmental blood role.

### EBT / Just Blood body patch

Installed as `EBT - Just Blood Body Patch - Rhiven`.

Source: [Enhanced Blood Textures Just Blood Just Not Enhanced Body Blood](https://www.nexusmods.com/skyrimspecialedition/mods/93414)

It disables EBT body-blood decals, leaves actor body blood to Just Blood, and prevents the two systems from overlapping on actors. It adds no ESP/plugin.

## Bathing in Skyrim - Renewed core

Installed as `Bathing in Skyrim - Renewed - Rhiven`.

- Version: **2.7.11**
- MO2 section: **`21 - Survival`**
- Recorded position: near the existing wash-basin and survival mods.

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

Installed as `Bathing in Skyrim - BAIN (Multi-Language) - Rhiven`.

- Localized plugin support was enabled.
- Language was left at **None**.
- The package does **not** include French.
- It remains useful as a localization-ready base for future translation work.

## BiSR addon stack

Install the following below the BiSR core unless a later conflict audit establishes a more precise exception:

| Order | Mod | Role / recorded choice |
|---:|---|---|
| 1 | `Zaki 8K-4K Textures for Bathing in Skyrim Renewed - Rhiven` | Dirt overlays. Female **Level 4 (Recommended)**; male dirt level **None**. |
| 2 | `Bathing in Skyrim - Renewed - Animal Fat and Linen - Rhiven` | BiSR crafting and washing resources. |
| 3 | `Bathing in Skyrim - Generic Soap Distribution - Rhiven` | Soap and wash-rag distribution. |
| 4 | `Bathing in Skyrim - Renewed - Seamless Soap - Rhiven` | Renewed-specific seamless soap file, version **1.2**. |
| 5 | `Bathing in Skyrim SE - SST MORE VISIBLE BUBBLES - Rhiven` | Optional effect producing approximately 30% more visible bubbles. |
| 6 | `Bathing in Skyrim - Wash Me - Rhiven` | Follower washing interactions. |

The legacy Bathing in Skyrim SE conversion is not required for the selected Seamless Soap file.

### Artisan Soaps

**Not retained.** It overlapped with the soap visual layer, and Seamless Soap plus More Visible Bubbles was selected as the simpler final visual stack.

### Wash Me - Renewed

Installed as `Bathing in Skyrim - Wash Me - Rhiven`, version **1.3**.

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

## iNeeds and the retired widget layers

### Current decision

**iNeeds replaces both the old Widget Addon solution and the later Needs Widget AIO choice in the intended final setup.** This replacement is user-confirmed, but its technical details are not yet recorded in the repository.

| Item | Status |
|---|---|
| iNeeds selected as the current replacement | **Installed / configured — user-confirmed** |
| Exact iNeeds version and MO2 display name | **To be confirmed** |
| iNeeds FOMOD/options and HUD settings | **To be confirmed** |
| iNeeds interaction with SunHelm and BiSR | **Pending in-game validation** |
| Needs Widget AIO | **Superseded / rollback only** |
| Widget Addon - Keep It Clean - Bathing in Skyrim | **Retired from the intended active stack / rollback history only** |

Do not copy the old Widget Addon order or options into a new setup unless deliberately performing a rollback.

### Repository snapshot warning

The current exported MO2 snapshots still list:

- `Widget Addon - Keep It Clean - Bathing In Skyrim - Rhiven` in the left pane;
- `WA_BathWidget.esp` in the right pane.

Those snapshots predate the final iNeeds replacement. Confirm the actual MO2 checkbox/plugin state and export fresh snapshots before publication or final playthrough sign-off.

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
10. Malignis in the bottom area of **`24 - Animations`**

iNeeds placement is **to be confirmed from the actual active MO2 profile**. Do not invent an order from the obsolete Widget Addon or Needs Widget AIO configuration.

### Recorded BiSR-related plugins

The last repository snapshot contains:

- `Bathing in Skyrim.esp`
- `WA_BathWidget.esp` — obsolete snapshot entry; must be confirmed inactive after the iNeeds replacement
- `Bathing in Skyrim - Renewed Animal Fat and Linen.esp`
- `Malignis Sound FX.esp`
- `Bathing in Skyrim - Wash Me.esp`

The snapshot does not yet document the definitive iNeeds plugin state.

### Known conflict decisions

- The EBT body patch leaves actor blood to Just Blood.
- Seamless Soap plus More Visible Bubbles replaces the rejected Artisan Soaps option.
- ConsoleUtil Extended is retained; no duplicate ConsoleUtilSSE NG installation is added.
- Pandora writes to its dedicated output mod, never directly to the game Data folder.
- MO2 Overwrite should be inspected after generation and intentional output kept in dedicated output mods.

## Animations and Pandora

### Malignis Animations

Install in **`24 - Animations`**, at the bottom of the animation block.

### Pandora paths

- Pandora output: `C:\JEUX\NEFARAM\mods\Pandora Output`
- Skyrim Data: `C:\JEUX\NEFARAM\Game Root\Data`

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

SunHelm remains the needs/survival engine. BiSR handles hygiene. The exact way iNeeds displays or reads these systems is not yet documented and must be confirmed in game.

### Campfire

Campfire remains the camping layer. The existing NEFARAM Campfire base is retained; the separately reviewed Campfire 2026 replacement was not adopted.

### Just Blood and EBT

Just Blood handles blood on actors, while EBT handles environmental blood. The dedicated body patch prevents EBT from duplicating the actor layer.

### Simple Inn Bath and Xtended Stay

These are part of the planned inn/economy validation rather than a completed validation claim. Confirm at least one normal inn flow with the final room-price configuration before the definitive playthrough.

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

### Installed / configured, but not final-playthrough validated

- iNeeds is the selected replacement for the previous widget layers.
- The final iNeeds/SunHelm/BiSR display relationship has not been documented in detail.
- The current MO2 snapshot has not yet been refreshed after the iNeeds replacement.

### Pending in-game validation

- Confirm the exact active iNeeds version, entry name, plugins and configuration.
- Confirm no duplicate survival or hygiene display remains.
- Confirm `WA_BathWidget.esp` is inactive.
- Enable BiSR in its MCM on the definitive New Game and verify that the setting persists after restart.
- Validate BiSR plus Simple Inn Bath in at least one inn.
- Validate Simple Inn Bath plus Xtended Stay with the final inn-price configuration.
- Validate dirt progression, bathing, soap consumption/effects and follower washing during normal play.
- Confirm SunHelm continues to own needs while BiSR owns hygiene.
- Confirm HUD positioning, fading, opacity and hotkey coexistence during the final UI/MCM session.
- Save, exit Skyrim completely, reload and confirm that the configuration persists.

## Troubleshooting and rollback

### Duplicate or overlapping widgets

1. Confirm that Widget Addon and Needs Widget AIO are not active alongside iNeeds.
2. Check the right pane for `WA_BathWidget.esp`.
3. Review iNeeds, SunHelm, STB and other HUD entries during the final UI/MCM session.
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

- Keep a disposable test save and MO2 profile backup before changing widget or survival layers.
- iNeeds is the intended final choice; Needs Widget AIO and Widget Addon may be kept temporarily only as disabled rollback references.
- If rollback becomes necessary, restore one known configuration at a time. Do not activate all three display layers together.
- Re-export both MO2 panes after the final choice is confirmed.

## Before the definitive playthrough

- [ ] Confirm the active iNeeds entry, version, plugin state and settings.
- [ ] Confirm Widget Addon and Needs Widget AIO are disabled or removed from the active profile.
- [ ] Confirm `WA_BathWidget.esp` is inactive.
- [ ] Refresh the MO2 left-pane and right-pane snapshots.
- [ ] Run Pandora after the last animation-related change and verify a clean completion.
- [ ] Inspect MO2 Overwrite and generated output mods.
- [ ] Start from the supplied **NEFARAM_Start** save, as required by the project baseline.
- [ ] Let MCM registration settle, then enable BiSR.
- [ ] Complete the final SunHelm/BiSR/iNeeds HUD and MCM consistency pass.
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

The core blood, BiSR and Pandora integration has a documented successful validation. The current iNeeds replacement is **installed/configured but still pending repository-detail and in-game validation**; it must not be presented as fully validated until the open checks above are completed.
