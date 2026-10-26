# SLSF Fame Comments Reloaded 1.3 SE — Integration & MCM Reference

> **Status:** already present in the active build / documentation catch-up  
> **Current target build:** NEFARAM-Rhiven **17.3.8** / profile **Eleanor Stable 17.3.8**  
> **Documented version:** **1.3 SE**  
> **Source:** user-supplied LoversLab description  
> **Scope:** architecture reference, current-build verification, MCM tuning, event-density control, coexistence with Public Whore Comments and other reactive systems, regression testing and rollback notes

---

## 1. Current Rhiven state

The current NEFARAM-Rhiven 17.3.8 snapshots already contain:

- `SLSF Reloaded 4.1.2 - Rhiven`;
- `SLSF Reloaded.esp`;
- `FameCommentsReloadedSE`;
- `FameCommentsReloaded.esp`;
- `SLSF Comments Voice`.

Therefore **SLSF Fame Comments Reloaded is not a new installation candidate** for the current build.

This document serves to:

1. identify what the mod actually does;
2. confirm the exact installed version / archive;
3. document its interaction with SLSF Reloaded 4.1.2;
4. prepare final MCM settings;
5. control overlap with additional comment / approach systems;
6. define regression tests before the definitive playthrough.

---

## 2. Purpose

SLSF Fame Comments Reloaded is a comment and SexLab-event expansion for **SexLab Sexual Fame Reloaded (SLSF Reloaded)**.

Its goal is to make NPCs react to the player's accumulated local sexual reputation and visible state instead of ignoring it.

The supplied description documents reactions to:

- public nudity;
- sexual fame;
- visible cum;
- visible Devious Devices;
- SexLab activity;
- player race / partner type through fame categories;
- prostitution / whore fame;
- submission / masochism fame;
- creature activity;
- marriage / cheating / cuckold states;
- follower-specific contexts.

Unlike a simple subtitle pack, the mod can also generate **fame events** that cause active gameplay outcomes.

---

## 3. Version 1.3 — important changes

The supplied description states that the Reloaded branch was adapted specifically for **SLSF Reloaded**, replacing the old SLSF dependency path.

Version **1.3**:

- removes the former **Markarth quest**;
- removes the **ZaZ dependency**;
- increments SLSF Reloaded fame levels through Fame Comments events.

These changes make v1.3 the correct branch to document for the current Rhiven setup.

The older **3.72** download belongs to the legacy SLSF branch and must not be confused with the Reloaded SE/AE version.

---

## 4. Comment scale

The source description reports:

- **2,400+ NPC comments** tied to nakedness and/or local sexual fame;
- **2,500+ custom follower comments** distributed across Serana, Mjoll and Faendal;
- two additional universal follower-comment sets;
- hundreds of comments capable of triggering active fame events.

This is therefore one of the largest dialogue / reaction layers in the adult-social stack.

### Rhiven consequence

Comment frequency must be treated as a system-level tuning issue, not as a cosmetic preference.

This becomes especially important if **Public Whore Comments 1.7** is later added.

---

## 5. SLSF Reloaded fame architecture

The mod uses local fame tracked by SLSF Reloaded in **24 settled areas**.

The supplied description lists fame categories including:

- Likes Women;
- Likes Men;
- Exhibitionist;
- Oral;
- Anal;
- Slut;
- Submissive;
- Orc;
- Argonian;
- Khajiit;
- Bestiality;
- Whore;
- Masochist;
- Cheating;
- Cuckold.

Most comments based on accumulated fame only trigger in locations where SLSF Reloaded tracks local fame.

However, non-fame comments — for example reactions to being naked, bound or currently having sex — can occur outside those locations.

---

## 6. How fame is generated

According to the supplied description, fame can increase through actions including:

- sex with women / men;
- public nudity;
- visible cum;
- visible tattoos / devices where SLSF interprets them as exhibitionism;
- oral / anal activity;
- aggressive SexLab activity as victim;
- sex with Orcs, Argonians, Khajiit or creatures;
- prostitution / whore-tagged behavior;
- masochist-tagged behavior;
- cheating on a spouse;
- spouse activity with others when cuckold state is configured.

The exact current behavior is controlled by **SLSF Reloaded 4.1.2**, not by Fame Comments alone.

---

## 7. Fame Events

Fame Comments Reloaded can generate gameplay events as a subset of fame comments.

The supplied description includes:

- forced player stripping;
- spanking;
- NPC masturbation;
- forced SexLab activity;
- unpaid SexLab offers;
- paid SexLab offers;
- bound SexLab scenes;
- multi-actor events;
- creature-related events.

These generally occur at higher fame levels, although other conditions such as nudity can lower the effective trigger threshold.

They may also be restricted by:

- NPC type;
- location;
- time of day;
- fame category;
- player equipment / weapon state depending on MCM settings.

### Rhiven implication

This means SLSF Fame Comments must be treated as an **active event generator**, not merely a comments mod.

It therefore overlaps conceptually with:

- SexLab Approach Redux;
- Public Whore / Public Whore Comments;
- TDF SexLab Aroused Rape;
- SL Dangerous Nights;
- BaboDialogue;
- SexLab Survival;
- defeat / recovery systems.

---

## 8. Comment Probability

The supplied source documents **Comment Probability** as a key SLSF / Fame Comments frequency control.

The cited default is **70%**.

This setting affects:

- ordinary fame comments;
- fame-event comments.

### Rhiven policy

Do not assume 70% is appropriate for the final Rhiven stack.

If **Public Whore Comments 1.7** is later integrated, both systems must be tuned together.

Recommended final strategy:

- retain SLSF Fame Comments as the **general reputation layer**;
- set Public Whore Comments lower as the **specific Public Whore context layer**;
- evaluate total comments per minute rather than each mod independently.

---

## 9. Harsh-comment filtering

The source description states that:

- comments can become harsher as fame increases;
- especially harsh comments can be disabled through MCM;
- friends, confidants, allies and lovers do not deliver the most hostile comments;
- universal follower comments can be configured toward either judgmental or encouraging tones.

This gives enough flexibility to prevent the system from becoming tonally absurd for Eleanor.

### Final-playthrough recommendation

Start with harsh-comment options conservative.

Increase only if the social tone feels too mild.

---

## 10. Follower comments

Follower comments are optional through MCM.

The source documents:

- universal follower-comment sets;
- custom comment sets for **Faendal**, **Mjoll** and **Serana**;
- unique environmental / location / combat context;
- arousal-dependent lines for Mjoll and Serana;
- fame-event subsets capable of initiating SexLab activity.

Documented scale includes approximately:

- Faendal: 550+ custom comments;
- Mjoll: 820+ custom comments;
- Serana: 1,200 custom comments.

Serana and Mjoll also have conditional fame-event comments.

### Rhiven concern

NEFARAM-Rhiven already contains a heavily customized Serana ecosystem.

Follower-specific Fame Comments must therefore be checked against:

- Serana Dialogue Add-On;
- Serana voice / content replacements;
- follower framework behavior;
- any custom follower dialogue system.

Do not assume subtitle comments are harmless merely because they are unvoiced.

---

## 11. Marriage / spouse systems

Fame Comments Reloaded includes its own extended spouse / marriage handling.

The supplied description documents:

- marriage without requiring the Temple of Mara ceremony;
- purchasable wedding rings;
- follower marriage through mod dialogue;
- relationship-type settings;
- cheating / cuckold detection;
- spouse sex requests;
- player solicitation;
- NPC approaches to player / spouse;
- spouse approaches to NPCs;
- spouse approaches to player;
- spouse public stripping;
- cuckold quests / repeating events.

This is significantly more than simple spouse commentary.

### Rhiven implication

If Eleanor uses these systems, their overlap with:

- vanilla marriage;
- follower frameworks;
- SexLab Approach Redux;
- Public Whore Comments spouse logic;
- other relationship mods

must be tested.

For the first definitive playthrough configuration, leave unused relationship subsystems disabled unless Fabien explicitly wants them.

---

## 12. Arrest / bounty system

At extreme fame values in hold capitals, the mod can generate:

- warning letters from Jarls;
- increased guard-event probability;
- local bounty;
- possible guard arrest.

This is a gameplay-changing subsystem.

### Rhiven concern

The build already contains:

- vanilla / modded arrest flows;
- PAMA / Prison Alternative;
- defeat-related systems;
- Public Whore Jail Replacement.

Therefore Jarl-warning / fame-arrest behavior should be treated as a dedicated compatibility test.

Do not enable or aggressively tune it without checking where the resulting arrest path is handed off.

---

## 13. Requirements — Reloaded branch

For the **Reloaded** version, the supplied description points to:

- **SLSF Reloaded**;
- its dependencies.

The current Rhiven build already contains and has technically validated **SLSF Reloaded 4.1.2**.

The legacy branch lists additional direct dependencies such as:

- SkyUI;
- UIExtensions;
- Fuz Ro D-oh;
- SexLab Framework;
- ZaZ Animation Packs;
- SexLab Aroused Redux.

Those legacy requirements must **not** be blindly applied to v1.3 Reloaded.

Notably, version 1.3 explicitly removes the ZaZ dependency.

### Current arousal stack

Rhiven uses **SLO Aroused NG**.

Because Fame Comments contains arousal-conditioned dialogue, the actual v1.3 archive should still be inspected to confirm which arousal API / forms it calls, but the current working 17.3.8 installation already demonstrates that the plugin can load in the Rhiven stack.

---

## 14. Voice pack

The current Rhiven left pane includes:

- `SLSF Comments Voice`.

The supplied source links a generic female voice pack for the Reloaded comments.

Before finalization:

- [ ] identify exact installed voice-pack version;
- [ ] compare it with Fame Comments Reloaded 1.3;
- [ ] determine coverage;
- [ ] verify no outdated voice assets override newer dialogue unexpectedly;
- [ ] decide whether incomplete voice coverage is acceptable.

The source description itself says core comments are non-voiced subtitles, so voice support is optional.

---

## 15. Rhiven-specific false-fame risks

The source warns that SLSF exhibitionist fame can be increased by several visible effects that are not literally nudity.

Relevant examples include:

- visible cum;
- tattoos;
- devices;
- drool / visual overlays from other mods.

This matters heavily in Rhiven because Eleanor uses:

- a substantial tattoo / SlaveTats ecosystem;
- Devious Devices;
- Dripping When Aroused NG;
- multiple body / effect systems.

The source specifically recommends disabling **Gag Drooling** in Dripping When Aroused for the legacy SLSF path to avoid drool being interpreted as visible tattoos and therefore exhibitionism.

### Rhiven action

Do not copy old legacy settings blindly.

Instead, verify current **SLSF Reloaded 4.1.2** behavior with the active Rhiven overlays / devices / drool effects and adjust only if false fame is reproduced.

---

## 16. Current-build audit checklist

Before the definitive playthrough:

- [ ] confirm exact Fame Comments Reloaded archive version = **1.3**;
- [ ] confirm `FameCommentsReloaded.esp` masters;
- [ ] confirm SLSF Reloaded 4.1.2 integration;
- [ ] identify installed voice-pack version;
- [ ] inspect current MCM defaults;
- [ ] document current Comment Probability;
- [ ] document enabled Fame Event categories;
- [ ] document harsh-comment settings;
- [ ] document follower-comment settings;
- [ ] document spouse / relationship systems enabled or disabled;
- [ ] document Jarl warning / bounty behavior;
- [ ] verify weapon-blocking option for forced fame events if desired;
- [ ] verify no stale settings inherited from the 17.3.7 migration save are being mistaken for definitive New Game defaults.

---

## 17. MCM baseline recommendation

For the first Eleanor playthrough test:

### Comment layer

- use a **moderate** Comment Probability;
- keep harshest comments limited initially;
- enable follower comments only if desired;
- choose follower tone deliberately.

### Fame Events

Start conservative:

- disable or reduce event categories that overlap strongly with other autonomous systems;
- avoid enabling every forced-event category simultaneously;
- keep paid / unpaid propositions distinct from forced events where possible;
- treat creature events separately.

### Marriage / spouse

- leave extended spouse / cuckold systems disabled unless explicitly part of Eleanor's intended playthrough.

### Arrest / bounty

- keep conservative until compatibility with PAMA / jail replacement behavior is confirmed.

---

## 18. Public Whore Comments coexistence

If **Public Whore Comments 1.7** is added:

- SLSF Fame Comments remains the **broad local-reputation system**;
- PWC becomes the **specific Public Whore context layer**.

Mandatory tuning test:

1. Fame Comments active at chosen baseline;
2. PWC at low probability;
3. measure total commentary;
4. raise PWC gradually;
5. if needed, lower Fame Comments slightly rather than maximizing both.

Watch for:

- two comments about essentially the same event;
- rapid subtitle replacement;
- repeated comments from the same NPC;
- comments firing during quest dialogue;
- comments immediately before / after force-greets;
- excessive SexLab event generation.

---

## 19. SexLab Approach Redux coexistence

If Approach Redux is later installed, Fame Comments must be regression-tested.

Approach can initiate autonomous NPC dialogue, while Fame Comments can generate both comments and events.

Verify:

- comment does not interrupt Approach force-greet;
- Fame Event does not start while Approach owns the player;
- Approach does not fire while a Fame Event scene is active;
- NPCs return to normal AI afterward;
- total autonomous-event density remains acceptable.

---

## 20. PAMA / arrest compatibility

Because Fame Comments can eventually produce hold bounties / arrests:

- test one controlled Jarl warning;
- test one bounty path;
- observe which arrest system receives the player;
- verify PAMA / Prison Alternative does not intercept unexpectedly;
- verify Public Whore Jail Replacement behavior if relevant;
- verify player control restoration;
- save / exit / reload after the arrest flow.

This test is required only if the Jarl punishment subsystem is retained.

---

## 21. Fame Event regression matrix

Test representative categories one at a time:

- [ ] stripping;
- [ ] spanking;
- [ ] NPC masturbation;
- [ ] voluntary sex offer;
- [ ] paid sex offer;
- [ ] forced sex event;
- [ ] bound sex;
- [ ] multi-actor event;
- [ ] creature event if enabled.

For each:

- correct trigger context;
- correct actors;
- no duplicate scene;
- no actor reservation leak;
- controls restored;
- NPC AI restored;
- no stuck quest;
- save / reload safe.

---

## 22. Comment-density test

Perform controlled observations in at least:

- Whiterun;
- Riften;
- Solitude;
- Windhelm;
- Riverwood;
- an inn;
- one quiet settlement.

Record approximately:

- comments per 5 minutes;
- repeated lines;
- fame-event count;
- follower comments;
- overlap with Public Whore / PWC if present;
- overlap with Babo / Approach if present.

The target is **reactive Skyrim**, not nonstop NPC commentary.

---

## 23. Acceptance criteria for current Rhiven build

The existing Fame Comments integration can be considered final for the definitive playthrough if:

- [ ] exact v1.3 archive is confirmed;
- [ ] SLSF Reloaded 4.1.2 integration is clean;
- [ ] comment frequency is acceptable;
- [ ] false fame from overlays / effects is controlled;
- [ ] follower comments do not interfere with custom follower dialogue;
- [ ] Fame Events retained by Fabien work reliably;
- [ ] autonomous-event overlap remains manageable;
- [ ] arrest / bounty subsystem is either validated or deliberately disabled;
- [ ] save / reload remains clean;
- [ ] final MCM configuration is documented.

---

## 24. Rollback / troubleshooting principle

Because the mod is already part of the active baseline, do **not** remove it casually from a developed save if problems appear.

Before the definitive playthrough, all aggressive testing should use disposable saves.

If a problem is found before the final start:

1. reproduce on the test profile;
2. identify whether the issue comes from Fame Comments, SLSF Reloaded or another autonomous system;
3. reduce / disable the relevant MCM feature first where appropriate;
4. only consider removing the mod before the definitive game is created;
5. refresh documentation and snapshots if the active build changes.

---

## 25. Current decision

**KEEP IN BUILD — already integrated; final MCM / regression pass required.**

This mod is already structurally part of NEFARAM-Rhiven and works on top of the validated SLSF Reloaded 4.1.2 stack.

The remaining job is not deciding whether to install it, but deciding **how much of it to unleash**.

Primary finalization priorities:

1. confirm exact v1.3 archive;
2. tune Comment Probability;
3. tune Fame Events;
4. control overlap with Public Whore Comments if PWC is added;
5. regression-test with SexLab Approach Redux if Approach is added;
6. validate or disable the Jarl warning / bounty / arrest subsystem;
7. document the definitive Eleanor MCM profile.

**Roadmap verdict:** **RETAINED BASELINE COMPONENT — MCM TUNING REQUIRED.**
