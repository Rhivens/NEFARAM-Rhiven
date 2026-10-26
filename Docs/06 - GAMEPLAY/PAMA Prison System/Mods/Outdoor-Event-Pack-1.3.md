# Prison Alternative - Outdoor Event Pack 1.3

Source: https://www.loverslab.com/files/file/33689-prison-alternative-outdoor-event-pack/

## About This File

### What is This Mod?

An Extension for my Prison Mod "Prison Alternative" which adds new Events to the Experience (work in Progress).

This particular extension is focused on outcomes which happen **outside Jails and cities**.

Like the author's other extensions, events can be lethal, but this pack adds skill-based escape mechanics that can allow the player or follower to survive.

## How to trigger Events

- For potentially deadly events, enable **Lethality** in Prison Alternative's MCM.
- Get imprisoned.
- Spend time in prison, misbehave in prison, or reach the end of the sentence depending on the Event.
- The event is then selected according to Prison Alternative's system.

## Currently Available Events

### Left for dead (hanging)

**Type:** Release Event

The Dragonborn and follower are brought to a scenic location outside the city.

SexLab content can optionally occur before the execution sequence.

The player and follower are then placed into a hanging setup and left to their fate.

### Escape mechanics

- Make sure the Event appears in Prison Alternative's **Event** tab before getting jailed.
- Escape is possible by rapidly pressing the **Spacebar**.
- Difficulty can be adjusted in the MCM.
  - Around **1.0**: manageable.
  - Around **2.0**: extremely difficult without automated input.
- Every Prison Alternative-enabled hold has its own event location.
- Locations can be disabled individually in the MCM if they conflict with other mods.
- Disabling a location removes the corresponding setup from the world and disables that Event for the affected hold.

## Quality-of-life Features

- The walking sequence from jail to the event location can be skipped with:
  - Spacebar;
  - Left Shift;
  - E.
- Every event location includes a pull chain that can be used to start scenes without going through jail first.
- NPC-only executions are possible.
- To make an NPC eligible, mark them as a pseudo-follower with:

```text
setplayerteammate 1
```

- Undressing or equipping special gear must be handled manually before the scene if desired.

### Persistent Corpses

NPCs executed through these event locations remain where they died until manually removed or until guards need the location for new victims.

Persistence survives game and cell reloads.

## Requirements

- Prison Alternative and its requirements.
- Zap8 / Zap8+.
- FNIS / Nemesis / Pandora.
- powerOfThree's Papyrus Extender.
- Pama´s Deadly Furniture Scripts **V2.4.0 or higher**.

## Installation

- Install with Vortex or MO2.
- A **new save is recommended**.
- Existing-save use is explicitly at the user's own risk.
- If installed on an existing save:
  - clear the Event Registry in Prison Alternative's MCM;
  - re-register Events;
  - verify that the Event list is complete and has no duplicates.

## Incompatibilities

### Devious Devices

Soft incompatibility.

The author allows experienced users to try it, but support is not provided if DD causes issues.

### Devious Cursed Loot

Not supported.

### Random Sex mods

Can potentially break scenes.

The author's own YARM is stated to be safe.

### Baka's Fill Her Up

A deflation event occurring at a bad moment can break the animation visually.

The author states that this should **not** cause lasting damage.

## Notes NEFARAM-Rhiven

- This is a **core PAMA prison extension** for the current project.
- It belongs after:
  - Pama's Deadly Furniture;
  - Prison Alternative;
  - Sovngarde Aftermath;
  and alongside the other Prison Alternative event packs.
- First validation cycle:
  - **Lethality OFF**;
  - no Devious Devices equipped;
  - confirm the Event is registered exactly once.
- When lethal testing begins, validate the full execution → Sovngarde Aftermath flow.
- The per-hold enable/disable switches are extremely useful in NEFARAM-Rhiven:
  - if one outdoor placement conflicts with another mod, disable only that hold rather than removing the whole addon.
- Because event locations exist outside cities, test each enabled hold for:
  - object overlap;
  - terrain clipping;
  - NPC pathing;
  - nearby worldspace additions.
- The walk-skip function provides a practical workaround if escort pathing becomes unreliable.
- **Baka's Fill Her Up requires a dedicated compatibility test**:
  - test with no inflation;
  - test with inflation active;
  - verify whether deflation can occur during the event;
  - if necessary, prevent or postpone deflation during PAMA scenes.
- Persistent corpses should be monitored conservatively in a long-running save.
- Prefer integrating this addon before the final Eleanor New Game, as recommended by the author.
