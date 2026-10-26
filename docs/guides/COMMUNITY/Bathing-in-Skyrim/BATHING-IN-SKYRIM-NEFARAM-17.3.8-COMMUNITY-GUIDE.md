# Bathing in Skyrim - Renewed 2.7.11 — NEFARAM 17.3.8 Community Guide

> **Community modification warning:** This guide changes the official NEFARAM setup. Back up your profile or work from a cloned NEFARAM instance before installing anything.

> **Baseline:** official NEFARAM 17.3.8
>
> **Validated status:** Bathing in Skyrim - Renewed (BiSR) 2.7.11 was tested in game and is functional for the core integration and bathing animations documented here.

## Responsibilities at a glance

Keep one clear owner for each gameplay or visual layer:

| Role | Component |
|---|---|
| Environmental blood | **Enhanced Blood Textures** |
| Blood on actors | **Just Blood** |
| Hygiene | **Bathing in Skyrim - Renewed (BiSR)** |
| Survival and needs | **SunHelm** |
| Camping | **Campfire** |
| Display only | **Needs Widget AIO** |

Needs Widget AIO does not replace SunHelm or BiSR. It only displays their information.

## Supported BiSR installation stack

Install and enable the following stack:

1. **Bathing in Skyrim - Renewed 2.7.11**
2. **Bathing in Skyrim - BAIN (Multi-Language)**
3. **Zaki 8K-4K Textures for Bathing in Skyrim Renewed**
4. **Bathing in Skyrim - Renewed - Animal Fat and Linen**
5. **Bathing in Skyrim - Generic Soap Distribution**
6. **Bathing in Skyrim - Renewed - Seamless Soap 1.2**
7. **Bathing in Skyrim SE - SST MORE VISIBLE BUBBLES**
8. **Bathing in Skyrim - Wash Me 1.3**
9. **Malignis Animations - Bathing in Skyrim Renewed**, placed with the animation mods

### BiSR 2.7.11 FOMOD choices

| Option | Selection |
|---|---|
| Male textures | **Zaki's SOS** |
| Female textures | **Zaki's CBBE** |
| Base Object Swapper | **Yes** |
| Description Framework | **Yes** |
| SkyPatcher | **Yes** |
| Bathing Token | **No** |
| First Person Messages | **No** |
| Source Scripts | **Yes** |
| Mod Organizer support | **Yes** |

Do not select the patches for:

- CACO;
- Licenses - Player Oppression;
- Barefoot Realism;
- Barefoot Realism Tweaked.

### Multi-language BAIN package

Install the BAIN package directly after the BiSR core. It does **not** include French, so leave the language at **None**. It is still useful as a localization-ready base for future translation work.

### Addon choices

- **Zaki textures:** female dirt **Level 4 (Recommended)**; male dirt level **None**.
- **Wash Me 1.3:** **Any follower**, **NSFW**, **Big basin**.
- **Artisan Soaps:** not retained. The selected visual combination is Seamless Soap plus More Visible Bubbles.

## MO2 relative order

Use relative relationships rather than copying absolute priority numbers from another installation:

1. Existing NEFARAM wash-basin, survival, SunHelm and Campfire files
2. BiSR core
3. BiSR BAIN multi-language package
4. Zaki textures
5. Animal Fat and Linen
6. Generic Soap Distribution
7. Seamless Soap
8. More Visible Bubbles
9. Wash Me

Place **Malignis** with the animation mods, after the files it is intended to overwrite. Place **Needs Widget AIO** with the interface and HUD mods.

## Malignis and Pandora

After installing Malignis with the animation mods, rerun Pandora.

- Send generated files to a dedicated **Pandora Output** MO2 mod.
- Point Pandora to the root of that output mod, not to a `meshes` subfolder.
- Never generate directly into the game's `Data` folder.

The recorded successful run detected:

- `FNIS_BiS_WashMe_List`
- `FNIS_Bathing_in_Skyrim_List`
- `FNIS_Bathing_in_Skyrim_Malignis_List`

Pandora completed successfully with **38,349 animations generated**.

## Critical BiSR MCM setup

BiSR is **disabled by default on a new game**. After MCM registration finishes:

1. Open the BiSR MCM and enable the mod.
2. Enable custom animations.
3. Give Malignis a **non-zero percentage weight** relative to other installed sets, such as Baka.
4. Test several bathing events to confirm that the intended sets play.

Pandora registration alone does not enable BiSR or assign Malignis a playback weight.

## Needs Widget AIO

Needs Widget AIO is an optional, recommended display layer. Its supplied **Vel'Dun preset** was present, active and validated in game.

It remains display-only:

- **SunHelm** continues to manage survival and needs;
- **BiSR** continues to manage hygiene;
- **Needs Widget AIO** only displays their information.

## What was validated

Direct in-game findings for the documented setup:

- BiSR 2.7.11 registered and exposed its MCM options.
- The core BiSR integration launched and functioned in game.
- Bathing animations worked without an observed animation error.
- Pandora detected the BiSR, Wash Me and Malignis lists and completed generation.
- Needs Widget AIO and its supplied Vel'Dun preset were active and working as the display layer.

This guide does **not** claim validation for Simple Inn Bath with Xtended Stay; those checks remain pending.

## Troubleshooting

### BiSR does not run

- Confirm `Bathing in Skyrim.esp` is active.
- Wait for MCM registration to finish.
- Enable BiSR in its MCM; it is disabled by default on a new game.
- Save, fully restart the game and check that the setting persists before changing other systems.

### T-pose or bathing animation failure

- Confirm the BiSR, Wash Me and Malignis animation files are enabled.
- Rerun Pandora into the dedicated Pandora Output mod.
- Confirm that all three recorded BiSR lists are detected.
- In the BiSR MCM, enable BiSR and custom animations, then give Malignis a non-zero weight.
- Inspect MO2 Overwrite and the Pandora output before testing again.

### Duplicate widgets

- Review Needs Widget AIO, SunHelm and other HUD entries.
- Keep only one visible widget for each value.
- Change one display layer at a time and retest on a disposable save.

### Actor and environmental blood overlap

- Keep Enhanced Blood Textures responsible for the environment and Just Blood responsible for actors.
- Confirm the EBT / Just Blood body patch is enabled after EBT.

### Soap or bubble conflicts

- Keep the selected Seamless Soap and More Visible Bubbles combination.
- Do not add Artisan Soaps unless you deliberately re-audit the visual layer.

## Final setup summary

Starting from official **NEFARAM 17.3.8**, this setup adds a validated BiSR 2.7.11 hygiene layer while preserving the existing division of responsibilities: EBT for environmental blood, Just Blood for actor blood, SunHelm for needs, Campfire for camping and Needs Widget AIO for display only.
