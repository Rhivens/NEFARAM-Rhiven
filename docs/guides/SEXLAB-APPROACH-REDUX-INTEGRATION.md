# SexLab Approach Redux 3.62 — Integration & Test Protocol

> **Status:** installed / technical validation complete / gameplay validation pending  
> **Target build:** NEFARAM-Rhiven after migration to **17.3.8** and stabilization  
> **Documented version:** **3.62**  
> **Scope:** compatibility verification, controlled integration, interaction testing, MCM tuning and rollback  
> **Historical note:** Fabien recalls having probably used SexLab Approach Redux in an older NEFARAM v16 setup. This has not yet been verified against an archived v16 load order.

---

## 1. Purpose

SexLab Approach Redux adds autonomous NPC interactions directed at a female player character.

Instead of requiring the player to initiate every conversation, nearby NPCs can approach the player on their own. Their dialogue and behavior may vary according to personality / character values assigned by the mod.

The main interest for NEFARAM-Rhiven is therefore not a new questline or worldspace, but a more reactive social layer that can interact with the existing adult gameplay stack.

---

## 2. Source description summary

Main documented behavior:

- female-oriented design;
- random NPCs may approach the player;
- conversations can concern ordinary matters or rumors about the player;
- NPC reactions vary depending on character traits assigned by the system;
- interactions are initiated by NPCs instead of always by the player.

The mod is designed to coexist with several BakaFactory ecosystem mods.

---

## 3. Requirements

### Required

For Skyrim SE/AE:

- SexLab Framework 1.63+;
- OSL Aroused **or** SexLab Aroused Redux BakaFactory Edited;
- Fuz Ro D-oh / Silent Voice;
- SLAL animation support;
- FNIS-equivalent behavior generation;
- Baka Motion Data Pack.

### NEFARAM-Rhiven equivalents already present

Current Rhiven snapshots already contain:

- SexLab Framework;
- OSL / SLO Aroused NG;
- Fuz Ro D-oh;
- SLAL;
- Baka Motion Data Pack;
- Pandora Behaviour Engine.

Therefore no duplicate framework should be installed.

For Rhiven, use **Pandora**, not FNIS, unless a future version of the mod explicitly requires otherwise.

---

## 4. Optional integrations mentioned by the author

The documented optional integrations include:

- **SLHH Expansion**;
- **Devious Devices Integration**;
- **BaboDialogue**;
- Populated Skyrim for BaboDialogue;
- Citizens of Tamriel SE.

### Relevant Rhiven state

NEFARAM-Rhiven already contains:

- **SLHH Expansion**;
- **Devious Devices NG**;
- **BaboDialogue** + Stability Patch;
- Citizens of Tamriel content / SexLab integration where present in the pack.

This makes SexLab Approach Redux a particularly relevant candidate because much of its intended ecosystem already exists.

---

## 5. Important Rhiven-specific note: Devious Followers

Devious Followers is present in the modpack but is normally **disabled in its MCM** for Fabien's gameplay.

For SexLab Approach Redux testing, treat Devious Followers as inactive unless deliberately enabled for a dedicated compatibility test.

This reduces the number of autonomous systems competing for player control during normal gameplay.

---

## 6. Primary compatibility concern

The main risk is **not** landscape, navmesh or worldspace conflict.

The main risk is competition between mods that can independently initiate:

- dialogue;
- approach events;
- forced interactions;
- SexLab scenes;
- harassment events;
- player control changes.

The test plan must therefore focus on event density, scene ownership and recovery.

---

## 7. Mods to monitor during testing

Highest-priority neighboring systems:

- SLHH Expansion;
- BaboDialogue;
- SexLab Survival;
- TDF SexLab Aroused Rape;
- SL Dangerous Nights;
- Practical Defeat / future Naked Defeat if present;
- Yamete Kudasai / Acheron defeat stack;
- Devious Devices;
- any random-event or harassment system active in the profile.

Devious Followers can normally be excluded from the first-pass conflict matrix because it is disabled through its MCM.

---

## 8. Planned integration timing

Preferred order:

1. migrate to NEFARAM 17.3.8;
2. stabilize the base profile;
3. validate Animal Mansion Reborn;
4. validate RennasRanch;
5. test SexLab Approach Redux on a cloned profile;
6. only then continue toward the Naked Defeat integration project.

Because SexLab Approach Redux does not add a large worldspace, it can also be tested opportunistically on a clean 17.3.8 clone before the larger content mods if needed.

---

## 9. Dedicated MO2 test profile

Create a clone such as:

`ELEANOR - SL Approach TEST`

Rules:

- keep the stable profile untouched;
- use a disposable test save / new game;
- no unrelated experimental mods;
- keep baseline MO2 left/right snapshots;
- document every MCM page before changing values.

---

## 10. Installation procedure

1. Install SexLab Approach Redux through MO2.
2. Inspect file structure.
3. Identify plugin(s), scripts, animation files, JSON/INI data and MCM files.
4. Check MO2 conflicts.
5. Verify masters.
6. Run Pandora.
7. Launch only after a clean Pandora pass.
8. Do not immediately raise event frequencies.

If the installed archive contains optional compatibility files, install only those actually relevant to the Rhiven stack.

---

## 11. xEdit audit

Load the complete test profile in xEdit.

Check:

- masters;
- quests;
- aliases;
- packages;
- factions;
- globals;
- dialogue topics;
- conditions;
- keywords;
- SexLab references;
- SLHH references;
- BaboDialogue references;
- Devious Devices references;
- leveled / distributed NPC logic if present;
- deleted references;
- ITMs / accidental edits;
- plugin errors.

Run **Check for Errors**.

### 11.1 xEdit result on 3.62

`SexLab Approach.esp` was checked with SSEEdit 4.1.5.

Result:

- processed records: **5,546**;
- xEdit result: **1 warning/error group**;
- affected quest: `SLApproachAskForSex2Quest "SLApproachAsktoOtherQuest" [QUST:xx012AFD]`;
- affected generated quest-fragment script: `SLApp_QF_AskForSex2Quest_04012AFD`;
- three VMAD properties reference quest aliases that no longer exist:
  - `Alias_initialActor -> Alias[0]`;
  - `Alias_PlayerRef -> Alias[2]`;
  - `Alias_TargetActor -> Alias[3]`;
- the quest's current **Aliases** section is empty, confirming that these are orphaned alias references in the generated fragment.

Decision:

- **do not edit or auto-clean this VMAD/quest fragment**;
- treat it as a known structural warning, most likely a leftover from an earlier quest layout;
- specifically test the `AskForSex2` / ask-other branch in-game;
- if the branch works and no Papyrus/scene failure appears, retain the mod without invasive correction.

This warning does **not** prevent the plugin from loading, registering its MCM or exposing the new 3.62 settings.

Do not clean automatically without confirming whether records are intentional.

---

## 12. Baseline MCM strategy

### 12.1 Clean 3.62 initialization validated

First in-game launch was performed with the **empty `SLAppAutoMCM.json` shipped by SexLab Approach Redux 3.62 winning the MO2 conflict** over the older file present in `SKSE Output`.

Result:

- MCM registered correctly;
- all pages loaded normally;
- no blank/broken fields observed;
- new 3.61/3.62 options were present, including `OnlyinTown` and `Sex CoolTime`;
- compatibility toggles for SLHH, BaboDialogue, FillHerUp, SexLab Survival and DDI were present;
- therefore the empty JSON is a valid clean initialization state and does not need to be replaced for basic operation.

### 12.2 Historical NEFARAM preset discovered in SKSE Output

An older generated/exported file was found at:

`SKSE Output/SKSE/Plugins/BakaFactory/SLAppAutoMCM.json`

It identifies itself as:

- `exportlabel = "NEFARAM - 263"`;
- `version = "2"`.

This file is treated as a **historical NEFARAM preset/reference**, not as the active 3.62 configuration.

Useful historical values worth considering during the final MCM session include:

- `basechancemultiplier = 0.7`;
- Appearance / Breasts / Butt = `80 / 80 / 80`;
- approach frequency = `70`;
- PC minimum arousal = `25`;
- NPC minimum arousal = `25`;
- dialogue arousal = `80`;
- morality = `0`;
- character range = `0–3`;
- relationship requirement = `2`;
- 3P probability = `10`;
- house visit chance = `5`;
- house stay duration = `24`;
- Asking for Sex = `20`;
- Rape Chance = `10`;
- Asking Name = `10`;
- Sexual Harassment = `10`;
- Relationship Change Chance = `40`;
- SLHH integration = enabled;
- BaboDialogue integration = enabled;
- DDI integration = enabled;
- SexLab Survival integration = enabled;
- followers = disabled;
- guards = disabled;
- hirelings = disabled;
- visitors = disabled;
- Dremora = disabled;
- elder race = disabled;
- out-of-sight detection = disabled;
- Unique Actor = enabled.

The historical preset predates the current 3.62 options and therefore must **not** be imported blindly. In particular it contains no explicit values for newer settings such as `OnlyinTown` and `Sex CoolTime`.

### 12.3 Final-playthrough policy

For the final Eleanor playthrough:

1. start from the clean 3.62 defaults;
2. use `NEFARAM - 263` only as a tuning reference;
3. re-enable integrations deliberately, one by one;
4. prioritize SLHH / BaboDialogue / DDI / SexLab Survival only after confirming their current behavior;
5. keep event density conservative;
6. explicitly review `OnlyinTown`, `Sex CoolTime`, Unique Actor, relationship requirement and arousal thresholds during the Mega-session MCM;
7. save a new Rhiven preset/export only after final settings are validated.


For the first functional test:

- keep approach frequency low;
- keep cooldowns conservative;
- avoid enabling every optional event;
- keep SLHH integration enabled only if the option is clearly documented;
- keep DD integration conservative;
- do not enable overlapping systems merely to stress-test everything at once.

The goal of first-pass testing is to prove that the basic approach loop works.

---

## 13. Basic approach test

Validate:

- [ ] NPC approaches the player autonomously;
- [ ] approach begins only in valid contexts;
- [ ] dialogue starts correctly;
- [ ] dialogue branches are coherent;
- [ ] NPC personality / behavior variation is visible;
- [ ] player can end the conversation normally;
- [ ] NPC returns to normal AI;
- [ ] no permanent package / follow state remains;
- [ ] controls are restored;
- [ ] save/reload remains functional.

Repeat with several NPC archetypes and locations.

---

## 14. Location matrix

Test in:

- Falkreath;
- Whiterun;
- Riften;
- Solitude;
- Windhelm;
- a small settlement;
- an inn;
- an exterior road;
- an interior with many NPCs;
- an area with very few NPCs.

Observe whether approach frequency scales sensibly with NPC density.

---

## 15. SLHH Expansion interaction test

Since SLHH Expansion is already part of NEFARAM-Rhiven, this is a priority test.

Check:

- normal SexLab Approach event;
- SLHH-triggered harassment;
- approach followed by SLHH-related branch if supported;
- SLHH event while Approach is on cooldown;
- Approach event shortly after SLHH completion;
- save/reload after either event.

Watch for:

- simultaneous initiation;
- stacked dialogues;
- duplicate actors;
- player control lock;
- NPC AI stuck in approach package;
- scene start while another system still owns the player.

---

## 16. BaboDialogue interaction test

BaboDialogue is already present in the Rhiven build and is explicitly listed by the author as an optional integration.

Test:

- regular BaboDialogue event;
- regular Approach event;
- one system triggering shortly after the other;
- rumor / reputation style dialogue if applicable;
- repeated interaction with the same NPC;
- event in crowded city cells.

Watch specifically for:

- duplicate dialogue hooks;
- repeated greeting loops;
- NPC package conflicts;
- simultaneous scene requests;
- excessive event frequency.

---

## 17. Devious Devices integration

If the mod exposes DD-specific interactions:

- verify device detection;
- verify equipped-device conditions;
- verify dialogue branches with restrained player;
- verify no duplicate device equip;
- verify no broken unlock state;
- verify scene end restores player state.

Do not activate extra DD compatibility options unless the base approach system is already stable.

---

## 18. SexLab Survival interaction

SexLab Survival can itself create contextual adult gameplay and social pressure.

Test:

- city approach while Survival systems are active;
- approach during normal survival gameplay;
- approach shortly after Survival event;
- inn / road events;
- save/reload after mixed interactions.

If event density becomes excessive, tune cooldowns rather than immediately declaring incompatibility.

---

## 19. TDF Aroused Rape interaction

TDF Aroused Rape is present in Rhiven's added NSFW section.

This is a high-value overlap test because both mods can react to NPC proximity / arousal / context.

Check:

- no simultaneous event ownership;
- no duplicate SexLab scene start;
- no repeated actor reservation;
- normal recovery after either mod completes.

If both systems are desirable, use conservative probability settings.

---

## 20. Dangerous Nights interaction

SL Dangerous Nights is also part of the Rhiven profile.

Test:

- daytime Approach behavior;
- evening behavior;
- nighttime behavior;
- immediately after sleeping;
- immediately after a Dangerous Nights event.

Goal: prevent event chains from becoming absurdly dense.

---

## 21. Defeat-stack interaction

Current Rhiven contains Acheron / Yamete Kudasai / Practical Defeat, with Naked Defeat planned later.

Before Naked Defeat integration:

- verify Approach does not fire while player is defeated;
- verify it does not fire during Acheron recovery;
- verify no approach package remains attached after a defeat;
- verify NPCs return to normal behavior.

After Naked Defeat is integrated, repeat the same matrix.

---

## 22. Dialogue collision test

Stress-test only after the basic mod is stable.

Use a busy city and temporarily raise Approach frequency moderately.

Watch for:

- two NPCs approaching simultaneously;
- one NPC starting while another dialogue is active;
- approach during merchant dialogue;
- approach during quest dialogue;
- approach during follower dialogue;
- approach during scene transition.

Expected result: the mod should gracefully delay, cancel or reject invalid starts.

---

## 23. Papyrus monitoring

Because this is primarily a scripted event/dialogue mod, Papyrus behavior matters.

Enable logging only on the test profile.

Look for:

- repeated registration errors;
- stuck update loops;
- unresolved aliases;
- failed scene start;
- NPC approach package never clearing;
- SexLab scene request failures;
- repeated MCM polling;
- SLHH / Babo cross-event errors.

Compare logs:

- idle city state;
- during approach;
- immediately after approach;
- after several in-game hours;
- after save/reload.

---

## 24. Save / reload matrix

Test saves:

1. before an approach;
2. while NPC is walking toward the player;
3. during dialogue;
4. immediately after dialogue;
5. after a SexLab branch if one occurs;
6. after an SLHH-related event;
7. after a BaboDialogue event;
8. after city transition;
9. after sleep;
10. after defeat / recovery.

For each:

- save;
- exit to desktop;
- relaunch;
- reload;
- verify controls;
- verify NPC AI;
- verify no dialogue loop;
- verify approach system resumes normally.

---

## 25. Frequency tuning

The objective is immersion, not constant interruption.

For Eleanor, prefer:

- moderate or low approach probability;
- meaningful cooldowns;
- no rapid repeat from the same NPC;
- no chain of adult events every few minutes.

The target feeling should be:

> NPCs occasionally notice and approach Eleanor.

Not:

> every citizen in Skyrim has formed a queue.

---

## 26. Acceptance criteria

SexLab Approach Redux can be accepted into the stable Rhiven profile if:

- [ ] xEdit shows no unresolved structural issue;
- [ ] Pandora output is clean;
- [ ] autonomous approaches work;
- [ ] NPC AI resets correctly;
- [ ] dialogue does not loop;
- [ ] SLHH coexistence is stable;
- [ ] BaboDialogue coexistence is stable;
- [ ] DD interactions are stable if enabled;
- [ ] SexLab Survival does not produce destructive overlap;
- [ ] TDF Aroused Rape does not double-trigger scenes;
- [ ] Dangerous Nights remains sane;
- [ ] defeat/recovery state blocks inappropriate approaches;
- [ ] Papyrus shows no runaway behavior;
- [ ] save/reload matrix passes;
- [ ] event frequency remains immersive rather than intrusive.

---

## 27. Rollback

If validation fails:

1. stop using the dedicated test save;
2. disable/remove the mod from the test profile;
3. restore Pandora output from the stable baseline if needed;
4. do not reuse test saves on the stable Eleanor profile;
5. do not attempt to "clean" a save as a substitute for rollback.

---

## 28. Final integration record

After validation, record here:

- exact archive name;
- exact version;
- download URL;
- plugin name(s);
- MO2 left-pane placement;
- right-pane placement;
- optional patches installed;
- Pandora notes;
- xEdit notes;
- MCM baseline;
- SLHH settings;
- BaboDialogue settings;
- cooldown / frequency settings;
- Papyrus observations;
- known exclusions;
- final verdict;
- validation date.

---

## 29. Current decision

**TECHNICALLY VALIDATED / RETAINED FOR IN-GAME TESTING — SexLab Approach Redux 3.62.**

The mod is especially promising for NEFARAM-Rhiven because most of its required and optional ecosystem is already present.

Technical installation, file-conflict review and clean MCM initialization are validated. The single xEdit issue is the documented orphaned-alias VMAD warning in `SLApproachAskForSex2Quest`; no invasive correction is planned before functional testing.

Its main remaining integration challenge is gameplay: confirm autonomous approaches and the AskForSex2 branch, then tune event density conservatively alongside SLHH, BaboDialogue, SexLab Survival, TDF and Dangerous Nights. Final Eleanor settings should use a lower approach frequency/probability than an aggressive default stack.
