# Pama´s Interactive Gallows 3.0

Source: https://www.loverslab.com/files/file/12352-pama%C2%B4s-interactive-gallows/

## About This File

This mod provides a self-contained, physics-enabled gallows kit that can be used on the Player Character or NPCs.

## New Features

- Havok-enabled rope connected to the victim's neck during both animation and ragdoll phases.
- Virtually seamless transition from animated state to ragdoll.
- Fully self-contained and does not require quest scripting.
- Torture functionality:
  - hoist victims to choke them;
  - release them without killing them.
- Dead victims remain tied up.
- Corpses can be removed from the rope without breaking the bindings.
- Automated mode available, including for Player Character use.
- Nonlethal mode available.
- Extensive customization via script properties.

## Installation

- Install with the mod manager of your choice or manually.
- Let it overwrite **ZAP8**, **ZAP8+** and **Heretical Resources** if asked.
- Run FNIS / Nemesis / Pandora as appropriate for the current setup.

## How to use on yourself

- Approaching the gallows should display the notification `Gallow Ready`.
- If it does not initialize, attack/punch the gallows or try activating the lever/wheel.
- Player Character usage is automated by default.

## How to use on NPCs

- Command a follower to use the gallows furniture, or use `SetFavorState` for another NPC.
- Use the lever to trigger the sequence.
- Use the side wheel to hoist the victim.
- Attacking the gallows once brings a living victim back to their feet.
- Attacking it again releases them.
- If the victim is dead, attacking the gallows removes the corpse and resets the device.

## Demo Location

- `GallowsLanding`, east of Whiterun.
- An identically named cell exists in the Creation Kit.
- A nonlethal ESP variant is provided for users who do not want to edit the setup manually.

## Known Issues

- Historical issue: the device could fail on repeated Player Character use after a lethal sequence; the source page marks this as solved.
- Loading a savegame very close to the gallows may prevent proper initialization.
  - Workaround: attack/punch the gallows to initialize it.
- Visual alignment varies with victim size.
- The device is optimized for Vanilla-like body scale.
- Third-person view can break on larger Player Characters.
  - Suggested workaround from the author: temporarily scale the character to approximately **0.97–0.95** before using the gallows.

## Compatibility Issues

### SexLab Defeat

The author requires a specific fixed/Bane variant of SexLab Defeat rather than the old default v5.3.5.

Source thread:
https://www.loverslab.com/topic/19941-sexlab-defeat/page/505/

### Interactive BDSM

Not compatible in lethal mode.

If Interactive BDSM is used, the author recommends the **nonlethal** version of the gallows.

## For Modders

A separate illustrated setup manual is available from the author.

### Functional properties

- `rope`: select the rope in the Render Window.
- `Dummy`: rigid-body dummy.
- `wheel`: side wheel / activator.
- `Lever`: lever / activator.
- `Trapdoor`: trapdoor reference; Vanilla trapdoors are supported.
- `zbf`: ZBF keyword recognition.

### Optional properties

- `Collar`: neck rope / collar. Recommended source value: `zbfCollarRopeExtreme02`.
- `cuffs`: restraints used on the victim. Demo value: `zbfCuffsRope02`.
- `tieFeet`: whether ankles are tied.
- `damageModifierPlayer`: choking damage per second to the Player Character.
- `damageModifierNPC`: choking damage per second to NPCs.
- `automaticForPlayer`: automated sequence for Player Character.
- `automaticForNPC`: automated sequence for NPCs.
- `removeCuffsOnRelease`: remove cuffs when a living victim is released.
- `nonLethal`: characters become unconscious rather than dying and are released after a delay.
- `deathCamDuration`: death-camera duration, also used as unconscious duration in nonlethal mode.
  - Applies only to deaths caused by this gallows.
  - Does not alter death-camera settings from other mods.
- `onlyRopeShootdwn`: not yet used.

## Sound Properties

No sound files are selected in this version. The author notes that suitable sounds may be added through a future ZAP release.

## Notes NEFARAM-Rhiven

- **Optional module**, not required by the Prison Alternative / PAMA core.
- Functionally overlaps with **Pama´s Deadly Furniture**, which already provides gallows-related lethal/nonlethal functionality.
- The strongest unique value is as a **standalone interactive gallows / sandbox device** and as a modder resource.
- The instruction to overwrite ZAP8 / ZAP8+ / Heretical Resources deserves caution in a large curated build.
- Do not allow those overwrites blindly; inspect actual file conflicts in MO2 before choosing winners.
- The third-person camera warning is especially relevant for NEFARAM-Rhiven because the build is intended to be played primarily in third person.
- Current recommendation:
  - keep documented;
  - do not include in the initial PAMA core installation;
  - reconsider only if standalone gallows interaction is specifically wanted.
