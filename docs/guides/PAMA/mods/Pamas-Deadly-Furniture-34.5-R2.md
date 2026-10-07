# Pama´s Deadly Furniture (scripts) 34.5 - Revision 2

Source: https://www.loverslab.com/files/file/12508-pama%C2%B4s-deadly-furniture-scripts/

## About This File

This is an ongoing work to bring actual functionality to Execution/torture devices added by ZAP or any other compatible source.

## Already implemented

- The Garotte
- The Wayrest Guillotine
- The MK2 Guillotine
- The chopping Block
- Gallows
- Impaling Machine
- Gravity Impaler
- Deadly tree stump
- Spitroast (and accessories)
- Two point Gallow
- Dwemer Oven
- Dwemer Electrocution/Amputation Device
- Generic painful script for static racks, crosses, spikes, and similar devices

## General Features

- Works on player and NPCs.
- Fully interactive devices.
- Nonlethal mode available: player/NPC can be knocked out for an adjustable duration instead of being killed.
- Fully reusable.
- MCM with many options:
  - death camera duration;
  - knock-out duration;
  - choking damage to PC/NPC;
  - related device parameters.
- Sound options.
- Spells for spawning devices and commanding NPCs into them.

## Hard Requirements

### Powerofthree´s Papyrus Extender

- LE: https://www.nexusmods.com/skyrim/mods/95017
- SE/AE: https://www.nexusmods.com/skyrimspecialedition/mods/22854

### Zap8

Only needed for versions lower than 3.0.0.

- LE: https://www.loverslab.com/files/file/5211-zaz-animation-pack-v80-plus/
- SE/AE: https://www.loverslab.com/files/file/5957-zaz-animation-packs-for-se/

### Behavior engine

One of:

- FNIS
- Nemesis
- Pandora

### mfgConsole

Optional. Required for facial expressions to work properly.

- LE: https://www.nexusmods.com/skyrim/mods/44596
- SE/AE: https://www.nexusmods.com/skyrimspecialedition/mods/11669

### Next-Gen Decapitations

Not a true hard requirement, but **strongly recommended** to avoid issues with face overlays and CTDs.

https://www.nexusmods.com/skyrimspecialedition/mods/135254

### SexlabFramework.pex

This is the core script of SexLab.

SexLab itself is optional, but due to how Papyrus works this script must be present.

If SexLab is installed, nothing else is required.

https://www.loverslab.com/files/file/20058-sexlab-se-sex-animation-framework-v166b-01182024/

If SexLab is not used:

1. Install SexLab but leave `SexLab.esm` disabled, keeping the scripts.
2. Or install the provided `SexlabFramework_DummyScript.zip`.

## Installation

- Install with the mod manager of your choice.
- Run FNIS / Nemesis / Pandora.
- When upgrading version, use a new savegame.

## Demo Location

The demo area is outside the regular world.

Use:

```text
coc pamaTestZone
```

## How to summon Devices into the World

- Open the MCM.
- Enable **Spells** on the first page.
- The spawning and NPC-command spells will appear under the Alteration magic tab.

## Issues / Compatibility

### Crash when using Guillotine / Chopping Block

This is attributed by the author to NiOverride.

Preferred solution:

- Install **Next-Gen Decapitations**:
  https://www.nexusmods.com/skyrimspecialedition/mods/135254

Alternative workaround:

```ini
[Overlays/Face]
iNumOverlays=0
iSpellOverlays=0
```

For Special Edition, the relevant file is:

`Data\SKSE\Plugins\skee64.ini`

This workaround disables face overlays.

### SMP hair / bodies behaving incorrectly with Gravity Impaler

Known issue on the author's side.

No user-side fix is currently provided.

### SexLab Defeat

The author recommends **Baka´s version**:

https://www.loverslab.com/files/file/18689-sexlab-defeat-baka-edition-lese/

The old original version is not supported.

### Devious Devices

Not supported and untested.

The author does not state absolute incompatibility, but warns that DD can interfere heavily with other mods and that DD-related issues are unsupported.

## Troubleshooting

- Mods placing the Player or NPCs under an **Essential Alias** can be problematic because those actors cannot be killed normally.
- Certain scripted followers or NPCs managed by follower frameworks may be impossible to kill or may behave incorrectly on death.
- If heads do not get chopped off, verify requirements and version.
- Spitroast may fail to recolor head/hair correctly in some cases due to headpart naming limitations.

## Notes NEFARAM-Rhiven

- **Core PAMA component.**
- In the proposed PAMA architecture, this should be treated as the low-level technical foundation for lethal/nonlethal devices.
- NEFARAM-Rhiven already contains:
  - powerofthree's Papyrus Extender;
  - ZaZ Animation Pack;
  - SexLab Framework;
  - Pandora.
- **Next-Gen Decapitations should be treated as quasi-mandatory for this build**, because:
  - PAMA strongly recommends it to avoid CTDs / face-overlay issues;
  - Sovngarde Aftermath requires it;
  - NEFARAM Discord feedback independently reports it as the fix for decapitation crashes.
- Prefer NG Decapitations over disabling face overlays in `skee64.ini`.
- First test should use **nonlethal mode**.
- Use `coc pamaTestZone` to validate devices independently before enabling lethal Prison Alternative events.
- Test explicitly with:
  - Acheron / Practical Defeat;
  - player Essential Alias behavior;
  - followers;
  - 3BA/SMP hair-body behavior on Gravity Impaler.
- Avoid wearing Devious Devices during the initial PAMA test cycle.
- If lethal mode is later enabled, validate the full execution → Sovngarde Aftermath → Tamriel return flow.
