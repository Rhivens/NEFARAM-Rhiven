# RennasRanch 0.3.0 — Integration & Test Protocol

> **Status:** candidate mod / not integrated  
> **Target build:** NEFARAM-Rhiven after migration to **17.3.8** and full stabilization  
> **Documented mod version:** **0.3.0**  
> **Mod:** **RennasRanch**  
> **Source:** https://www.loverslab.com/files/file/45943-rennasranch/  
> **Scope:** verification, integration, regression testing, and rollback procedure

---

## 1. Purpose

This document defines a controlled procedure for evaluating **RennasRanch**, a ponyplay-focused Skyrim mod built around a large custom worldspace called the **Secluded Valley**.

The mod adds:

- a large new worldspace;
- many NPCs involved in pony training;
- a training / progression system;
- buffs and benefits unlocked through training;
- daily tasks;
- free-roam tasks;
- behavior / performance tracking;
- punishments and corrective measures;
- Devious Devices interactions;
- pose checks;
- tether / hitch mechanics;
- contraption scenes;
- cart / draft work gameplay;
- custom weather and ambience;
- MCM controls and recovery options.

The objective is to determine whether the mod can be safely added to NEFARAM-Rhiven without destabilizing:

- SexLab;
- Devious Devices NG;
- OSL Aroused;
- RaceMenu overlays;
- Pandora-generated behaviors;
- Papyrus workload;
- Falkreath-area worldspace / terrain;
- follower and quest systems;
- DynDOLOD / xLODGen output.

---

## 2. Planned integration order

Current preferred order after NEFARAM 17.3.8 stabilization:

1. **NEFARAM 17.3.8 migration**
2. **Global stabilization / regression pass**
3. **Animal Mansion Reborn**
4. **Ponyplay / Secluded Valley mod**
5. **Naked Defeat**

### Rationale

This ponyplay mod is more invasive than Animal Mansion Reborn because it contains:

- a large new worldspace;
- a rewritten main loop;
- persistent training / performance state;
- scripted control locking and restoration;
- tethering;
- Devious Devices contraptions;
- cart physics;
- pose tracking;
- punishment logic.

However, it is still preferable to validate it **before Naked Defeat**, because Naked Defeat changes the defeat / bleedout / Acheron architecture and would make troubleshooting more ambiguous.

---

## 3. Requirements audit

Source requirements:

- SexLab
  - author does not use SexLab P+, but expects it may work;
- SexLab Aroused
  - author uses OSL Aroused;
- Devious Devices NG **0.4.2+**
  - author recommends DD Vibration Update Beta if not on 0.4.3rc;
- Fuz Ro D-oh;
- UIExtensions;
- KS Hairdos
  - meshes and textures only are required;
  - plugin does not need to be active;
- Kris's Papyrus Extender
  - formerly Scrab's Papyrus Extender;
- RaceMenu
  - required for overlays such as dirt and brands;
- Zaki's Dirt Textures
  - textures only;
  - SlaveTats or RaceMenu version can be used;
- Papyrus Tweaks NG
  - not a hard requirement but explicitly recommended;
- dependencies of all the above.

### NEFARAM-Rhiven pre-check

Before installation, verify exact installed versions of:

- [ ] SexLab
- [ ] OSL Aroused / SexLab Aroused implementation
- [ ] Devious Devices NG
- [ ] Fuz Ro D-oh
- [ ] UIExtensions
- [ ] KS Hairdos assets
- [ ] Kris / Scrab Papyrus Extender
- [ ] RaceMenu
- [ ] Papyrus Tweaks NG
- [ ] Zaki dirt textures or equivalent current overlay stack

### Important

Do not install duplicate frameworks merely because they are listed as requirements.

Use the existing NEFARAM-Rhiven stack whenever it already satisfies the dependency.

---

## 4. Installation preparation

Create a dedicated MO2 profile, for example:

`ELEANOR - Ponyplay TEST`

Clone from the fully stabilized 17.3.8 profile.

Before enabling the mod:

- [ ] export / save MO2 left-pane snapshot;
- [ ] export / save right-pane / plugin load order;
- [ ] save current DynDOLOD / xLODGen state;
- [ ] note current Papyrus Tweaks NG settings;
- [ ] confirm no unrelated test mods are active;
- [ ] prepare a disposable new-game test profile or dedicated test save.

> Do not perform first-pass validation on the final Eleanor save.

---

## 5. First installation pass

Install the mod normally through MO2.

Then:

1. inspect all files before launching;
2. identify ESP/ESM/ESL plugins;
3. identify scripts;
4. identify animations / behavior files;
5. identify RaceMenu overlays;
6. identify meshes / textures;
7. identify BodySlide projects;
8. identify worldspace / LOD assets;
9. identify INI / JSON / SKSE configuration files;
10. inspect overwrite conflicts in MO2.

### Animation generation

The author explicitly requires running:

- FNIS,
- Nemesis,
- **or Pandora**

after installation.

For NEFARAM-Rhiven:

- use **Pandora Behaviour Engine**;
- confirm the mod is detected correctly;
- record Pandora warnings / errors;
- compare output against the stable profile.

---

## 6. BodySlide

Version 0.3.0 introduces at least one item that must be built in BodySlide.

Procedure:

1. open BodySlide through MO2;
2. search using the mod name;
3. identify all projects belonging to the mod;
4. build only the required project(s);
5. enable **Build Morphs** if applicable;
6. redirect output to a dedicated MO2 mod, e.g.:

`Ponyplay - BodySlide Output - Rhiven`

Do not mix the generated files into the main Eleanor BodySlide output until integration has been validated.

---

## 7. xEdit audit

Load the entire profile in xEdit.

Inspect the new plugin(s) for:

- [ ] worldspace edits;
- [ ] exterior cells;
- [ ] Falkreath edits;
- [ ] road south of Falkreath;
- [ ] city markers;
- [ ] dungeon markers;
- [ ] navmesh;
- [ ] landscape;
- [ ] placed objects;
- [ ] persistent references;
- [ ] factions;
- [ ] packages;
- [ ] quests;
- [ ] globals;
- [ ] keywords;
- [ ] RaceMenu overlay records if applicable;
- [ ] Devious Devices references;
- [ ] new masters;
- [ ] deleted references;
- [ ] ITMs / obvious accidental edits.

Run:

- **Check for Errors**
- conflict inspection
- dependency / master review

Do **not** clean records automatically without understanding whether they are intentional.

---

## 8. Falkreath compatibility audit

The mod makes minor terrain edits on the **road south of Falkreath** and adds basic markers to Falkreath and other locations.

This is a critical area in NEFARAM-Rhiven because the build contains significant Falkreath / road / landscape modifications.

Verify conflicts against at least:

- Cities of the North — Falkreath;
- COTN Falkreath patch collection;
- Northern Roads;
- Northern Roads patch collections;
- landscape fixes;
- Lux / Lux Orbis / Lux Via where relevant;
- Seasons-related exterior changes;
- Falkreath city / exterior NPC or marker edits;
- any Animal Mansion Reborn additions if AMR is already installed.

### In-game route test

Walk the full route manually:

- Falkreath town center;
- Dead Man's Drink vicinity;
- south road;
- border approach;
- entrance / transition to Secluded Valley.

Look for:

- terrain seams;
- floating objects;
- buried statics;
- broken road pieces;
- blocked navmesh;
- duplicate objects;
- inaccessible doors;
- bad markers;
- NPC pathing failures.

---

## 9. New worldspace audit

The mod adds a large custom worldspace.

Verify:

- [ ] worldspace loads correctly;
- [ ] map works;
- [ ] fast travel behavior is correct;
- [ ] weather is active;
- [ ] ambient sounds work;
- [ ] interiors connect correctly;
- [ ] NPC schedules function;
- [ ] no obvious navmesh failures;
- [ ] no persistent unloading / loading problems;
- [ ] no broken LOD transitions;
- [ ] no missing terrain or distant objects.

Version 0.3.0 adds proper weather and sounds intended to feel similar to the Whiterun tundra.

---

## 10. LOD strategy

The author includes vanilla-quality LODs for the custom worldspace but explicitly recommends generating custom LODs.

Preferred NEFARAM-Rhiven procedure:

1. perform all functional tests first using supplied LODs;
2. do **not** immediately regenerate the full final LOD stack;
3. once compatibility is validated:
   - run xLODGen if required;
   - run TexGen;
   - run DynDOLOD;
4. compare new output against the stable build;
5. visually inspect the Secluded Valley from several viewpoints.

Final integration should use generated LOD matching the Rhiven load order.

---

## 11. MCM baseline

Before starting the quest:

- open the mod MCM;
- document every page with screenshots;
- record default values;
- identify:
  - skip intro functions;
  - pose reset;
  - force pose reset;
  - cart recovery / reset;
  - punishment / behavior settings;
  - overlay options;
  - SlaveTats / RaceMenu dirt option;
  - any debug functions.

### Rule

Do **not** use intro skip functions during the first validation run.

The author recommends completing the introduction normally at least once.

---

## 12. Quest start test

The mod starts in **Falkreath**, inside the inn.

Expected behavior:

1. enter the inn;
2. new NPC is present;
3. NPC greets the player;
4. introduction starts normally;
5. transition toward the Secluded Valley works;
6. no unrelated scene framework interrupts the intro.

Record:

- exact quest names;
- quest IDs if easily available;
- stage progression;
- NPC aliases;
- any Papyrus warnings.

---

## 13. Core loop validation

Version 0.3.0 rewrites almost the entire main gameplay loop.

Therefore test the core loop repeatedly.

Validate:

- [ ] morning / daily start;
- [ ] task selection;
- [ ] task completion;
- [ ] task failure;
- [ ] task reset;
- [ ] daily rotation;
- [ ] behavior tracking;
- [ ] performance tracking;
- [ ] punishment chance;
- [ ] corrective-measure logic;
- [ ] training gain;
- [ ] buffs / benefits;
- [ ] free-roam transitions;
- [ ] curfew logic;
- [ ] sleep / day transition if used.

Run at least **three full in-game days** before calling the loop stable.

---

## 14. Free-roam task tests

Version 0.3.0 adds five shorter free-roam tasks with a changing daily selection.

For each task record:

- quest name;
- giver;
- start condition;
- objective;
- expected completion;
- failure state;
- behavior score / demerit effects;
- control state afterward;
- save/reload behavior.

Repeat until every available task has been seen at least once.

---

## 15. Draft Work / cart test protocol

The new **Draft Work** daily task uses physics-enabled carts / carriages.

This is a high-risk subsystem.

Test:

### Attachment

- [ ] cart attaches correctly;
- [ ] visual alignment is acceptable;
- [ ] player controls match expected state;
- [ ] no duplicate attachment;
- [ ] reattach works;
- [ ] MCM recovery function works.

### Movement

Test:

- straight road;
- slope;
- turn;
- collision;
- uneven terrain;
- stopping;
- animation start while tethered;
- save/reload while task is active.

### Detachment

Verify:

- cart detaches cleanly;
- wagon sounds stop;
- controls return;
- player does not remain tethered;
- quest progresses;
- no invisible collision remains.

Because the changelog repeatedly mentions cart / tether reliability, this subsystem must receive multiple repetitions.

---

## 16. Tether / leash validation

Historical fixes specifically mention:

- hitch teleport;
- unleash logic;
- controls staying locked;
- tether / retether glitches;
- termination while leashed.

Test:

- normal leash start;
- normal leash end;
- forced distance;
- teleport condition;
- scene interruption;
- cell transition;
- save/reload;
- MCM recovery;
- quest abort if available.

After every test verify:

- movement;
- camera;
- activation;
- menus;
- combat controls;
- sprint;
- sneak;
- interaction keys.

---

## 17. Pose system validation

Version 0.3.0 adds:

- pose compliance checks;
- pose reset hotkey;
- force pose reset in selected scenarios.

Test:

- correct pose;
- wrong pose;
- changing pose before check;
- reset hotkey;
- force reset;
- save/reload while posed;
- scene start while posed;
- scene end;
- task completion;
- punishment trigger.

Confirm that the player always returns to a valid animation state.

---

## 18. Devious Devices / contraption tests

The mod requires Devious Devices NG 0.4.2+ and contains contraption scenes.

Historical fixes include:

- contraption scenes failing to start;
- heel-offset alignment;
- unlock delays;
- minigame stop conditions;
- controls not restored;
- device swap confusion;
- devices being re-equipped incorrectly.

Test at minimum:

- [ ] contraption scene starts;
- [ ] alignment is acceptable;
- [ ] correct footwear / no-heel variant is used;
- [ ] device equip works;
- [ ] device replacement works;
- [ ] no duplicate equip;
- [ ] unlock works;
- [ ] unlock delay does not soft-lock;
- [ ] escape minigame stops after success;
- [ ] controls restore;
- [ ] footwear is removed/restored correctly;
- [ ] save/reload after completion is safe.

---

## 19. Arousal / vibration

Because the mod uses SexLab Aroused and may make use of DD vibrations:

Verify:

- OSL Aroused values update as expected;
- no duplicate arousal framework is active;
- DD vibration events start and stop;
- no permanent vibration state remains;
- vibration behavior is acceptable with the currently installed DD NG version.

Do not add the optional DD Vibration Update Beta unless it is actually required by the selected DD NG version.

---

## 20. RaceMenu overlays / dirt / brands

RaceMenu is used for dirt / brands.

Zaki's Dirt Textures are expected as textures only.

Test two possible paths only if relevant:

### RaceMenu overlay path

- overlay appears;
- correct texture;
- correct slot;
- removal / replacement works;
- save/reload preserves expected state.

### SlaveTats path

If SlaveTats is used instead:

- disable the RaceMenu / SlaveTats option exactly as intended by the MCM;
- verify no duplicate overlay;
- verify no collision with existing Eleanor tattoos.

### Rhiven warning

Eleanor already uses a substantial overlay / tattoo ecosystem.

Before final integration, inspect:

- RaceMenu overlay slot usage;
- SlaveTats assignments;
- tattoo persistence;
- any mod that fades / removes tattoos;
- voluntary tattoos that must never be overwritten or erased.

---

## 21. Scene framework interference test

The mod contains scripted scenes and can take control of the player.

NEFARAM-Rhiven contains several mods capable of triggering independent scenes.

During tests, watch for interruptions from:

- random SexLab events;
- defeat systems;
- harassment systems;
- prostitution systems;
- follower events;
- Devious Followers;
- quest-specific scenes.

For first validation, if a random-scene system interferes repeatedly, disable **only that system** on the test profile and retest.

Document every required exclusion.

---

## 22. Papyrus performance test

The author states:

- there is no DLL;
- all systems are script-driven;
- scripts are not intended to be heavy;
- they run mainly while the mod is in control;
- Papyrus Tweaks NG is recommended.

Test with Papyrus logging enabled on the test profile.

Look for:

- repeated errors;
- stack dumps;
- runaway update loops;
- missing properties;
- failed aliases;
- device polling loops;
- repeated scene-start failures;
- tether polling that never exits;
- control-restoration loops;
- script instances remaining active after tasks.

Compare idle Papyrus behavior:

- outside the mod;
- inside the valley but not in a task;
- during a daily task;
- during contraption;
- during Draft Work.

---

## 23. Save / reload matrix

At minimum test save/reload:

1. before entering Falkreath inn;
2. during introduction;
3. immediately after entering Secluded Valley;
4. during free roam;
5. during a daily task;
6. while tethered;
7. during Draft Work;
8. after cart detachment;
9. before contraption;
10. after contraption;
11. after punishment;
12. after sleeping / day reset.

For each:

- save;
- exit to desktop;
- relaunch;
- reload;
- confirm quest state;
- confirm controls;
- confirm devices;
- confirm pose state;
- confirm NPC AI;
- confirm no scene resumes incorrectly.

---

## 24. Regression tests outside the mod

After several hours of Valley gameplay, leave the mod content and verify normal Skyrim behavior.

Test:

- Falkreath;
- another city;
- dungeon;
- combat;
- follower recruitment;
- SexLab scene outside AMR / ponyplay content;
- Devious Devices outside the mod;
- fast travel;
- horse / mount if used;
- sleep;
- save/reload.

Goal: confirm the mod does not leave global player states behind.

---

## 25. New-save policy

Version 0.3.0 explicitly requires a **new save** relative to earlier versions.

The author states that 0.3.0 should be suitable for serious saves and intends to avoid future new-save requirements when possible.

For Rhiven:

- integration testing starts on a new disposable save;
- final Eleanor playthrough should only include the mod after the exact target version is frozen and validated;
- do not downgrade the mod mid-playthrough;
- do not assume future updates are save-safe unless the author confirms it.

---

## 26. Known 0.3.0 risk indicators

The changelog shows that the following systems have historically required fixes:

- hitch teleport;
- unleash logic;
- hybrid boots;
- cart attachment;
- quest markers;
- dialogue flags;
- progress dialogue;
- corral pathing;
- morning inspection;
- curfew warning;
- free-roam restart;
- hood dialogue;
- device re-equip;
- device swap;
- contraption scene start;
- heel-offset alignment;
- contraption unlock delay;
- Pony Express unleash;
- gate unlock;
- locked controls;
- contraption escape state;
- NPC following state;
- neck seam;
- generic dialogue quest placement;
- no-heel boot cleanup;
- gag-specific completion;
- wagon sound persistence;
- Draft Work completion;
- BodySlide output path;
- pose reset;
- map marker location;
- dragon attacks;
- animation pause during cart mini-game;
- tether / retether;
- NPC / animal dialogue filtering;
- pacify / truce cloak;
- memory quest pose delay;
- memory quest dialogue.

These are not automatically current bugs.

They are the **highest-value regression targets** because they represent previously fragile code paths.

---

## 27. Acceptance criteria

The mod can be considered ready for the stable Rhiven profile only if:

- [ ] no unresolved xEdit errors;
- [ ] Falkreath / south-road terrain is clean;
- [ ] no critical navmesh conflict;
- [ ] Secluded Valley loads reliably;
- [ ] Pandora generation is clean;
- [ ] required BodySlide item is correct;
- [ ] main introduction works without skip;
- [ ] daily loop survives multiple days;
- [ ] all available task categories can complete;
- [ ] Draft Work works repeatedly;
- [ ] cart attach / detach is reliable;
- [ ] tether system restores controls every time;
- [ ] pose system recovers correctly;
- [ ] contraption scenes start and end correctly;
- [ ] DD devices clean up correctly;
- [ ] overlays do not damage Eleanor's tattoo setup;
- [ ] save/reload matrix passes;
- [ ] Papyrus logs show no persistent runaway errors;
- [ ] leaving the Valley restores normal Skyrim behavior;
- [ ] no critical conflict with Animal Mansion Reborn;
- [ ] no new unexplained CTD pattern appears.

---

## 28. Rollback procedure

Because integration must be isolated in a dedicated MO2 profile:

1. keep the stable 17.3.8 profile untouched;
2. keep pre-install MO2 snapshots;
3. keep pre-install LOD outputs;
4. never reuse test saves for the final playthrough;
5. if the mod fails validation, delete / disable the test profile changes;
6. restore previous behavior and LOD outputs;
7. do not attempt save cleaning as a substitute for a clean rollback.

---

## 29. Final integration notes to record

When validation is complete, update this file with:

- exact mod name;
- exact download URL;
- author;
- installed version;
- plugin names;
- MO2 left-pane placement;
- right-pane placement;
- patches used;
- BodySlide output name;
- Pandora notes;
- xEdit conflict notes;
- LOD generation date;
- MCM baseline;
- known exclusions;
- final compatibility verdict;
- date of validation.

---

## 30. Current decision

**Do not integrate yet.**

First complete and stabilize **NEFARAM 17.3.8**.

Then:

1. integrate and validate **Animal Mansion Reborn**;
2. create a dedicated profile for this ponyplay / Secluded Valley mod;
3. run the full protocol above;
4. only after both are stable, proceed to the **Naked Defeat** integration project.
