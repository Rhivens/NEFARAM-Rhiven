# Pama´s Interactive Beatup Module 2.9

Source: https://www.loverslab.com/files/file/13793-pama%C2%B4s-interactive-beatup-module/

## About This File

This mod is a lightweight framework-like system for interactive punishment scenes involving the player or NPCs.

## What Is This Mod?

It adds a dialogue option to most NPCs allowing the player to initiate a punishment sequence.

The selected NPC is placed into a magically appearing furniture, after which the player can interact with them using the mod's punishment mechanics.

Nearby guards can also be asked to continue the punishment for a chosen duration and with a selected weapon.

The player can also choose to become the subject of the scene.

## Framework Functionality

The important part of the mod is not the demo dialogue itself, but its framework-like implementation.

It is controlled through **ModEvents**, allowing other mods to integrate with it without creating hard dependencies.

The included dialogue options are intended primarily as demonstration functionality and do not appear during normal gameplay unless explicitly enabled.

Detailed documentation of the ModEvents is mentioned by the author as a separate download / pending documentation.

## Main Features

- Dynamic reaction to hits while a character is locked in a device.
- Multiple purpose-made reaction animations.
- Multiple supported devices.
  - Currently 2.
  - More may be added in the future.
- Persistence:
  - characters remain locked when leaving the area;
  - state persists after save reload;
  - guards can also persist.
- Supports 2 victims simultaneously.
- New devices and animations can be added through script properties.

## Installation

- Install with the mod manager of your choice.
- Run FNIS / Nemesis / Pandora as appropriate for the current setup.

## Usage for Non-Modders

Dialogue options are hidden during normal play.

To enable them, the player must wear the **Ring of punishment**.

The ring can be obtained via the MCM.

The MCM also allows configuration of the duration for which the Player Character remains locked in a furniture when asking another NPC to perform the punishment.

## Notes NEFARAM-Rhiven

- **Optional module**, not part of the core Prison Alternative / PAMA prison stack.
- No direct requirement for:
  - Prison Alternative;
  - Bad Ends;
  - Sovngarde Aftermath;
  - Orkish Bounty Hunters.
- The main technical interest is its **ModEvent-based framework design**, which could make it useful for future integrations.
- Persistence should be treated with caution in a large long-running save:
  - actors and guards can remain locked across cell changes and reloads.
- Because the dialogue layer is gated behind the Ring of punishment, the mod should remain unobtrusive if installed but not actively used.
- Current recommendation for NEFARAM-Rhiven:
  - keep documented;
  - do not include in the initial PAMA core installation;
  - reconsider later if another mod explicitly integrates with its ModEvents or if manual sandbox use becomes desirable.
