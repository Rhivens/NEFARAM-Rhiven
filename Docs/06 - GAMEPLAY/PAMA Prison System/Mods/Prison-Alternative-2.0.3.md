# Prison Alternative - A modular Prison System 2.0.3

Source: https://www.loverslab.com/files/file/17619-prison-alternative-a-modular-prison-system/

## About This File

> READ THE REQUIREMENTS AND COMPATIBILITY SECTIONS BEFORE COMPLAINING!

## What is this mod?

A lightweight Prison system with special emphasis on compatibility, extendability and an intuitive feel to the game.

It is designed as a natural extension of the Vanilla prison system, without assuming that the full Devious Devices mod family is installed.

The mod also includes synthesized voices.

## Events

Prison Alternative uses an **event-based modular structure**, similar in principle to Daymoyl or Simple Slavery.

New events can be added without creating hard dependencies.

Trigger chances for specific Events can be configured in the MCM.

The system provides three main event categories:

### Daily Events

Occur on a daily basis while incarcerated.

The severity of the crime influences the duration of the prison sentence.

### Punishing Events

Can occur when the player:

- is recaptured after a failed escape;
- commits another crime while in prison.

### Release Events

Occur after the player has served the full sentence.

Possible outcomes include:

- normal release;
- alternative outcomes such as a Simple Slavery transfer.

## Escape System

The escape rules are designed to be more natural than Vanilla.

- The player must actually leave the city rather than simply reach the first door.
- Guards' barracks can no longer be bypassed casually.
- If the player is defeated by a guard while escaping, they are returned to the cell and punished.
- The author states that this does **not** interfere with combat defeat mods.

Optional behavior:

- for more serious crimes;
- or after at least one recapture;

the player can be cuffed, making further escape attempts more difficult.

## Follower and NPC Support

Optional features include:

- followers can also be arrested and shackled in the player's cell;
- follower detention / bailout system;
- followers left behind during an escape remain jailed until bailed out.

## Requirements and Installation

- SKSE
- SkyUI
- Zap8 / Zap8+
  - use the correct LE or SE/AE version.
- SexLab — optional.
- SimpleSlavery++ — optional.

After installation, run FNIS / Nemesis / Pandora as appropriate for the current setup.

## Official Addons

- Bad Ends Revived: Windhelm
- Bad Ends Revived: Riften
- Bad Ends Revived: Solitude
- Prison Alternative - Punishment Pack

## Adding new addons mid-game

Installing new addons mid-game is **not recommended**.

If it must be done:

1. Open Prison Alternative's MCM.
2. Go to the **Events** tab.
3. Clear the Registry.
4. Re-register Events.
5. Repeat until all Events are displayed correctly.
6. Make sure **no Event is registered twice**.

## Compatible Mods

- Mods that normally send the player to Vanilla prison.
  - Examples from the author: Daymoyl, Peril, Dragonborn in Distress.
- Extensible Follower Framework.
- Open Cities.
- Skyrim Sewers.
- Similar city-modifying mods.
- SexLab Adventures.
- Mods affecting Cidna Mine or the Chill:
  - Prison Alternative has no effect on those areas.

## Partially Compatible

### Defeat mods

The author states that **any Defeat mod** can be partially compatible.

Important distinction:

- **Health-threshold-based knockdowns should be disabled.**
- **Bleedout-based defeat triggers work without problem.**

### Troubles of Heroine

Works on its own.

Problems are expected when combined with **Devious Cursed Loot**.

### Got to Bed

Use the **most recent version**.

Older versions may cause issues.

### Prison Overhaul Patched

Not intended to be used together directly.

A `PA-POP.zip` patch can be used if the goal is to retain POP bounty hunters.

### Multi-follower frameworks other than EFF

Examples given by the author:

- Nether's Follower Framework;
- Amazing Follower Tweaks.

Followers managed by those systems may be detected, but some framework features may need to be disabled while the player is in prison.

Use at your own risk.

## NOT Compatible

### Devious Devices

The author lists Devious Devices and mods depending on it as unsupported / incompatible.

Important nuance:

- simply having DD installed does not appear to cause immediate problems;
- wearing DD restraints while entering or participating in Prison Alternative content can break things.

### Devious Cursed Loot

Can technically be used by experienced users, but the author warns that it **can and will break the game if handled carelessly**.

For NEFARAM-Rhiven, treat DCL as **not compatible** with the PAMA prison stack.

### Forced-scene mods in Prison

Any external mod that forces the player through scenes while incarcerated can interfere with Prison Alternative.

## Common Issues

### Broken Pathfinding

The author attributes this to external factors rather than Prison Alternative itself.

If pathfinding breaks, investigate the surrounding setup and conflicting mods.

### Stuck on black screen

Usually caused by incorrectly registered Events.

Recommended procedure:

1. Open the MCM.
2. Clear the Event Registry.
3. Re-register Events.
4. Verify the list carefully.

If that does not resolve the issue, a new game is recommended.

## Notes NEFARAM-Rhiven

- **This is the core framework of the PAMA prison project.**
- It should be installed before the event packs and Bad Ends addons.
- Current intended integration stack:
  - Pama's Deadly Furniture;
  - Prison Alternative;
  - Pama Sovngarde Aftermath;
  - Punishment Pack;
  - Outdoor Event Pack;
  - Bad Ends Windhelm / Riften / Solitude;
  - Orkish Bounty Hunters.
- NEFARAM-Rhiven already contains:
  - SKSE;
  - SkyUI;
  - ZaZ Animation Pack;
  - SexLab Framework;
  - Simple Slavery / Simple Slavery Rebuild;
  - Acheron;
  - Practical Defeat Reanimated;
  - Troubles of Heroine;
  - Devious Devices.
- **Primary compatibility rule:** do not enter Prison Alternative content with DD restraints equipped during the first validation cycle.
- **Defeat configuration must be checked carefully:**
  - prefer bleedout-based defeat;
  - disable health-threshold knockdowns if present.
- Acheron / Practical Defeat require an explicit integration test, even though PA claims defeat-mod compatibility.
- Troubles of Heroine is acceptable by itself; DCL should remain absent.
- Random / forced scene systems active during incarceration should be identified and disabled or controlled if needed.
- Because many PAMA addons recommend a new game, the preferred strategy is to integrate and validate the full block **before starting the final Eleanor playthrough**.
- After all addons are installed, confirm the Event Registry contains each event **exactly once**.
