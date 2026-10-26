# Public Whore Comments 1.7 — Integration & Test Protocol

> **Status:** candidate mod / not currently integrated  
> **Target build:** NEFARAM-Rhiven **17.3.8** / profile **Eleanor Stable 17.3.8**  
> **Documented version:** **1.7**  
> **Source:** user-supplied LoversLab description  
> **Scope:** dependency verification, dialogue-density control, coexistence with Public Whore / SLSF Fame Comments, arousal integration, in-game validation and rollback

---

## 1. Purpose

**Public Whore Comments (PWC)** is a dialogue / reaction expansion for **Visio Diaboli's Public Whore**.

Version 1.7 adds **more than 1,300 NPC comments** reacting to the player's current or previous Public Whore status and to a wide set of contextual conditions.

The source description explicitly states that the mod **does not change Public Whore gameplay**. Its role is to add variety, reactivity and immersion around the existing Public Whore system.

For NEFARAM-Rhiven, the main question is therefore not whether the mod introduces a new gameplay framework, but whether its large dialogue layer can coexist cleanly with the already active social / fame / comment systems.

---

## 2. Source-described features

The source description documents comments based on:

- current Public Whore status;
- prior Public Whore status;
- current / prior Public Whore location;
- Dragonborn status;
- thane status;
- player race;
- visible cum;
- yokes;
- player and NPC arousal;
- marriage / spouse status;
- follower status;
- guard status;
- beggar / elderly client permissions;
- player solicitation permissions;
- creature-content settings;
- some comments delivered while the player is in SexLab animations;
- “bump into NPC” comments;
- first-person player “thoughts” displayed as notifications.

For active Public Whore sexual activity, comments can also reflect:

- actor count;
- main partner gender;
- animation tags:
  - Rough;
  - Vaginal;
  - Oral;
  - Anal;
- creature involvement;
- creature type, specifically Dog or Horse where detected.

Most content is written with a female player in mind, although male-player comments are also included.

---

## 3. Public Whore MCM-dependent behavior

The source description says PWC reads several Public Whore MCM choices and changes comments accordingly.

Examples documented by the author:

- if a female player's gender preference is set to **male**, female NPCs are not treated as potential PW clients and can use more sympathetic comments;
- if creature content is enabled, NPCs can comment on beast encounters;
- followers normally do not deliver PWC comments unless followers are allowed to approach the Public Whore;
- spouse followers are an exception and can always use spouse-specific comments;
- guards can comment on being excluded if guards are not allowed to approach;
- NPCs can react if beggars / elderly people are allowed to approach;
- NPCs can react if the player is allowed to solicit customers.

This means PWC is not merely a generic dialogue pack: it depends on Public Whore's own configuration state.

---

## 4. Comment frequency control

PWC includes an in-game frequency control.

According to the source description:

- speak to a **Jarl**;
- choose **“About how everyone talks about me...”**;
- adjust comment frequency.

The documented default is **70%**.

The author explicitly states that this 70% default is the same frequency as the default used by **SLSF Fame Comments**.

### Rhiven implication

NEFARAM-Rhiven already contains and activates:

- `SLSF Reloaded 4.1.2 - Rhiven`;
- `FameCommentsReloadedSE`;
- `FameCommentsReloaded.esp`.

Therefore PWC and Fame Comments must be tested together with conservative frequencies.

The goal is to avoid excessive idle commentary, repeated reactions or a constant stream of contextual comments.

---

## 5. Marriage / spouse handling

The source description uses the **Bond of Matrimony** ring as the recognition mechanism.

A female Public Whore is recognized as married when wearing the ring.

A follower can receive spouse-specific comments when also wearing a Bond of Matrimony ring.

The mod does not require the vanilla Temple of Mara marriage ceremony for this recognition; the rings are the relevant condition according to the supplied description.

PWC also exposes spouse dialogue used to select a personality / reaction type toward the player's Public Whore status.

Documented spouse personality concepts include:

- unwilling cuckold;
- enjoys sharing / watching;
- cheated-on / vengeful.

This interaction also records spouse gender for later NPC comments.

### Rhiven test point

If Eleanor uses a spouse during the definitive playthrough, this branch should be validated separately from generic follower comments.

---

## 6. First-person “thoughts”

Version 1.6 added more than 100 first-person “thoughts”.

They are displayed as upper-left notifications and can be triggered by:

- nearby NPCs;
- player arousal levels.

Some have associated animations.

The source description provides two priest interactions:

- disable the thoughts;
- confess that the player likes being the Public Whore, changing their tone / character.

### Rhiven risk

NEFARAM-Rhiven already has many notification-producing systems.

The first test should determine whether these thoughts improve immersion or create excessive HUD / notification noise.

They are optional from a gameplay-preference perspective because the source describes a way to disable them in game.

---

## 7. Requirements from the supplied source

### Required

- **Public Whore**
  - author recommends **version 1.2.4**;
- **SexLab Aroused Redux**.

### Optional

- xVASynth voice pack documented for **PWC version 1.1**.

The supplied description does **not** state that the old v1.1 voice pack fully covers all dialogue added through version 1.7.

Therefore voice coverage for 1.7 must not be assumed complete.

---

## 8. Current NEFARAM-Rhiven state

The current 17.3.8 load-order snapshots already contain:

### Public Whore ecosystem

- `Public Whore`;
- `Public Whore 1.2.4 Windhelm Ending Patch`;
- `Public Whore Jail Replacement`;
- `NymphoElf Public Whore Patch`;
- `Public Whore Voice`;
- `Public Whore.esp`.

The presence of a **1.2.4-specific patch** makes version 1.2.4 highly relevant to the current setup, but the exact installed Public Whore core version should still be confirmed directly in MO2 before PWC installation.

### Fame / comment ecosystem

- `SLSF Reloaded 4.1.2 - Rhiven`;
- `FameCommentsReloadedSE`;
- `FameCommentsReloaded.esp`;
- `SLSF Comments Voice`.

### Arousal implementation

The current left pane contains:

- `SLO Aroused NG`;
- related OSL / Advanced Nudity Detection KID integration.

The supplied PWC source explicitly lists **SexLab Aroused Redux** as its requirement.

It does **not** explicitly state that SLO / OSL Aroused NG is supported as a substitute.

Therefore compatibility must be verified from the actual PWC archive:

- plugin masters;
- scripts;
- expected quest / global / faction API;
- whether the active Rhiven arousal framework exposes the same interfaces required by PWC.

Do **not** install a second arousal framework merely to satisfy the description until this is checked.

---

## 9. Version 1.7 changes relevant to Rhiven

Version 1.7 specifically reports:

- corrected naked detection so it no longer depends on the Public Whore naked-rules setting;
- current / prior PW-in-location comments restricted to one of the nine Public Whore locations;
- removal of PWC comments from Dibella-faction NPCs;
- additional harsh comments conditioned on low relationship rank.

These changes are directly relevant to immersion and false-positive reduction.

Earlier fixes that remain important include:

- blocking PWC comments while the player is in a dialogue menu;
- fixes for creature detection;
- fixes for current-PW comments firing in the wrong town;
- improved prior-PW location logic;
- numerous condition fixes.

For Rhiven, **version 1.7 should be the only version evaluated** unless a later version exists when installation begins.

---

## 10. Main integration risks

### 10.1 Comment saturation

This is the primary known risk.

NEFARAM-Rhiven already has:

- SLSF Fame Comments;
- Public Whore itself;
- BaboDialogue and other reactive social systems;
- additional adult-context mods capable of dialogue / notifications.

PWC adds over 1,300 comments and defaults to 70% frequency.

A technically compatible setup may still be undesirable if NPCs comment too often.

### 10.2 Dialogue competition

Version 1.6 added a script intended to block PWC comments while the PC is in a dialogue menu, which is encouraging.

Still test interaction with:

- quest conversations;
- merchant dialogue;
- follower dialogue;
- BaboDialogue events;
- Public Whore approach / client dialogue;
- future SexLab Approach Redux if installed.

### 10.3 SexLab-scene comments

A subset of PWC comments can fire during SexLab animations.

Test whether this remains immersive and does not interfere with:

- scene dialogue / subtitles;
- other commentary systems;
- control restoration;
- scene termination.

### 10.4 Arousal API compatibility

This is the most important technical uncertainty before installation.

The source names SexLab Aroused Redux, while Rhiven uses SLO / OSL Aroused NG.

Actual archive inspection is required.

---

## 11. Pre-installation archive audit

Before enabling the mod:

- [ ] record exact archive name and version;
- [ ] inspect plugin name(s);
- [ ] inspect masters;
- [ ] inspect scripts and source files if included;
- [ ] identify any direct dependency on `SexLabAroused.esm` or specific SLA scripts;
- [ ] confirm whether SLO / OSL Aroused NG satisfies those interfaces;
- [ ] inspect dialogue quests / topics / conditions;
- [ ] inspect any Public Whore quest/global references;
- [ ] inspect MCM / frequency implementation;
- [ ] check for loose files conflicting with existing Public Whore or Fame Comments assets;
- [ ] inspect optional voice-pack compatibility separately.

If the arousal dependency is not satisfied cleanly, stop before installation.

---

## 12. xEdit audit

After installation on a test profile:

- [ ] verify masters;
- [ ] run **Check for Errors**;
- [ ] inspect dialogue topics and conditions;
- [ ] inspect Public Whore quest/global references;
- [ ] inspect location conditions for the nine PW locations;
- [ ] inspect relationship-rank conditions;
- [ ] inspect Dibella-faction exclusions;
- [ ] inspect naked-detection conditions;
- [ ] identify any overrides of records from Public Whore or other mods;
- [ ] confirm no unexpected worldspace / navmesh / gameplay records are modified.

Because the source says PWC does not alter PW gameplay, unexpected gameplay-record edits should receive particular scrutiny.

---

## 13. Dedicated test profile

Use a clone of the current stable baseline, for example:

`Eleanor 17.3.8 - PWC TEST`

Rules:

- do not test first on the definitive playthrough;
- keep `Eleanor Stable 17.3.8` untouched;
- use a disposable save;
- no unrelated experimental mods;
- record Public Whore MCM settings;
- record SLSF Fame Comments frequency before starting.

---

## 14. First-pass conservative configuration

Do **not** begin with both comment systems at their documented defaults.

Suggested test strategy:

1. keep **Fame Comments** at the current known Rhiven setting;
2. set **PWC significantly below 70%** for the first test;
3. observe comment density in several locations;
4. raise PWC gradually only if commentary feels too sparse.

The objective is not maximum dialogue output.

The target is contextual reaction without making every NPC constantly comment on Eleanor.

---

## 15. Basic validation matrix

### Public Whore state

Test:

- [ ] not currently Public Whore;
- [ ] current Public Whore;
- [ ] former Public Whore;
- [ ] current PW in correct location;
- [ ] current PW outside correct location;
- [ ] former PW in another hold / town.

Version 1.7 specifically claims fixes for location scoping; these must be verified.

### NPC categories

Test:

- [ ] generic male NPC;
- [ ] generic female NPC;
- [ ] guard;
- [ ] follower;
- [ ] spouse follower;
- [ ] beggar / elderly NPC if relevant;
- [ ] Dibella-faction NPC.

Expected for Dibella-faction NPCs: no PWC comments, according to the 1.7 changelog.

### Relationship rank

Test:

- [ ] neutral / low relationship;
- [ ] friendly NPC;
- [ ] spouse / high relationship.

Verify harsh-comment conditioning feels consistent with the 1.7 changes.

---

## 16. Public Whore MCM interaction tests

Vary one setting at a time.

Test:

- [ ] female PC / male preference;
- [ ] creature content off;
- [ ] creature content on;
- [ ] follower approach off;
- [ ] follower approach on;
- [ ] guard approach off;
- [ ] guard approach on;
- [ ] beggar / elderly approach off/on if used;
- [ ] player solicitation off/on.

Confirm PWC reacts to each configuration as described.

---

## 17. SexLab-scene tests

Use controlled scenes only on the disposable save.

Test combinations where practical:

- [ ] one partner;
- [ ] multiple actors;
- [ ] male main partner;
- [ ] female main partner;
- [ ] Rough tag;
- [ ] Vaginal tag;
- [ ] Oral tag;
- [ ] Anal tag;
- [ ] creature scene;
- [ ] Dog / Horse if those systems are enabled in the test profile.

Verify:

- comments match the actual scene context;
- no obvious stale scene state survives after the animation;
- no comment spam loops;
- other dialogue / notifications remain usable.

---

## 18. SLSF Fame Comments coexistence test

This is a mandatory Rhiven-specific test.

Run the same location with:

1. Fame Comments active / PWC low;
2. Fame Comments active / PWC medium;
3. optionally lower Fame Comments while raising PWC.

Observe:

- comments per minute;
- repeated NPC lines;
- whether both mods react to the same event at once;
- notification / subtitle readability;
- whether contextual PWC comments are drowned out by generic fame comments.

Do not simply run both at 70% and declare the result representative.

The final configuration should prioritize variety and context, not raw frequency.

---

## 19. Future SexLab Approach Redux interaction

If **SexLab Approach Redux 3.61** is later installed, repeat a smaller regression matrix.

PWC itself is primarily a comment layer, while Approach can initiate NPC interactions.

Check:

- no PWC comment interrupts or collides with an Approach dialogue;
- no rapid comment immediately before/after an Approach force-greet;
- no repeated interaction loop caused by the same NPC;
- overall social-event density remains acceptable.

This is a future regression test, not a current installation blocker.

---

## 20. First-person thoughts test

Test the notification system separately.

- [ ] verify thoughts appear under expected conditions;
- [ ] test at low and high player arousal;
- [ ] observe any associated animation;
- [ ] confirm priest dialogue can disable thoughts;
- [ ] confirm the alternate “likes being the public whore” tone can be selected if desired;
- [ ] decide whether Eleanor should retain this feature.

Because the feature is optional in practice, disable it if it creates HUD clutter.

---

## 21. Spouse test

If spouse content is to be used:

- [ ] equip Bond of Matrimony on Eleanor;
- [ ] equip Bond of Matrimony on the spouse follower where relevant;
- [ ] verify spouse-specific dialogue appears;
- [ ] choose each personality type on a disposable test if practical;
- [ ] confirm spouse gender is recognized correctly;
- [ ] verify post-PW comments remain coherent after status ends.

No Temple of Mara ceremony is required for the ring-based detection described by the source.

---

## 22. Save / reload validation

Test saves:

1. before PW status;
2. during PW status;
3. after comments have fired;
4. during / after a SexLab scene;
5. after changing PWC comment frequency;
6. after changing spouse personality;
7. after enabling/disabling first-person thoughts.

For each:

- save;
- exit to desktop;
- relaunch;
- reload;
- confirm settings persist;
- confirm no repeated dialogue loop;
- confirm comments resume normally.

---

## 23. Acceptance criteria

Public Whore Comments 1.7 can be accepted into the stable Rhiven build if:

- [ ] exact Public Whore version is confirmed compatible;
- [ ] active Rhiven arousal framework satisfies PWC's actual dependency/API requirements;
- [ ] xEdit shows no unresolved structural issue;
- [ ] correct-location / wrong-location behavior matches 1.7 expectations;
- [ ] Dibella-faction exclusion works;
- [ ] relationship-rank filtering behaves sensibly;
- [ ] Public Whore MCM-dependent comments work;
- [ ] SexLab-scene contextual comments are correct and stable;
- [ ] spouse handling works if retained;
- [ ] first-person thoughts are either accepted or cleanly disabled;
- [ ] PWC + SLSF Fame Comments frequency can be tuned to an immersive level;
- [ ] no dialogue collision or repeated spam is observed;
- [ ] save / reload remains clean.

---

## 24. Rollback

If rejected:

1. stop using the dedicated PWC test save;
2. disable / remove PWC from the test profile;
3. restore the original stable profile;
4. do not use save cleaning as a substitute for rollback;
5. retain this document with the rejection reason.

---

## 25. Current decision

**Promising candidate / documentary audit complete.**

Reasons in favor:

- Public Whore is already part of NEFARAM-Rhiven;
- the current build already contains the relevant Public Whore ecosystem;
- PWC does not claim to modify Public Whore gameplay;
- version 1.7 includes several condition / location / naked-detection fixes;
- the added comments could significantly improve contextual reactivity.

Main uncertainties:

1. exact compatibility with Rhiven's **SLO / OSL Aroused NG** implementation must be confirmed from the archive;
2. **comment density** with `FameCommentsReloaded.esp` must be tuned deliberately;
3. interaction with future **SexLab Approach Redux** should be regression-tested if Approach is later installed.

**Provisional roadmap verdict:** **CANDIDATE — LOW/MEDIUM STRUCTURAL RISK, MEDIUM IMMERSION-SPAM RISK.**
