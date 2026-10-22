# Unethical Alchemy 1.0.0 — Integration Study

> **Status:** candidate / not yet integrated  
> **Target build:** NEFARAM-Rhiven **17.3.8** / profile **Eleanor Stable 17.3.8**  
> **Documented version:** **1.0.0**  
> **Source:** user-supplied LoversLab description  
> **Category:** small quest / NPC / alchemy / SexLab content mod  
> **Scope:** prerequisites, pregnancy-framework interaction, incompatibilities, alchemy-overhaul interaction, testing and rollback

---

## 1. Purpose

Unethical Alchemy adds a small adult-content alchemy encounter centered on a new trainer / sex partner at **Heartwood Mill**.

The source description states that:

- Elgrim can point the player toward another alchemy teacher;
- the new NPC is located at Heartwood Mill;
- the NPC acts as an alchemy trainer and sex partner;
- he can give the player an alchemy lore / skill book after trying a dose of **Joy** with him;
- Joy creates a long-lasting effect where normal sex feels less satisfying for approximately **400 hours**;
- the NPC can provide abortifacients for roleplay purposes;
- if **Hentai Pregnancy** is installed, the abortifacient can terminate early pregnancies or advance late pregnancies to a post-pregnancy residual-lactation stage.

The author explicitly documents incompatibility with:

- **Deviously Accessible**;
- the older **Unethical Illusion**.

---

## 2. Current Rhiven relevance

This is not a framework replacement and not a large worldspace expansion.

Its attraction for Rhiven is mainly:

- a small localized adult-RP quest / encounter;
- an alchemy-themed side activity;
- a persistent gameplay effect through Joy;
- a possible pregnancy / abortifacient roleplay interaction.

Compared with large candidates such as Animal Mansion, RennasRanch or Naked Defeat, the expected structural footprint is much smaller.

---

## 3. Pregnancy framework mismatch

The source description documents functional pregnancy integration specifically for **Hentai Pregnancy**.

The current Rhiven fertility architecture does **not** use Hentai Pregnancy.

Current project documentation instead specifies:

- **Beeing Female NG** as primary fertility framework;
- **Fertility Adventures Redux - Rhiven**;
- stock **Fertility Mode disabled**.

Therefore:

> The abortifacient's real pregnancy-control functionality must be considered **unsupported / unverified** on the current Rhiven stack.

Possible outcomes:

1. the abortifacient remains a harmless RP item/dialogue option but does nothing to BFNG;
2. it works only partially through generic pregnancy-state assumptions;
3. it references Hentai Pregnancy-specific forms/scripts and therefore simply skips functionality when that framework is absent;
4. it may produce errors if the integration is not properly optional.

### Required check

Before installation:

- [ ] inspect plugin masters;
- [ ] inspect scripts for Hentai Pregnancy references;
- [ ] confirm whether integration is conditional;
- [ ] verify absence of hard dependency;
- [ ] determine whether a BFNG patch exists or would be required.

Do **not** assume cross-framework compatibility.

---

## 4. Alchemy-overhaul interaction

The current Rhiven left pane already contains:

- `Alchemy Plus`;
- `Apothecary - An Alchemy Overhaul`;
- `Alchemy Recipe Expansion`.

Unethical Alchemy adds at least:

- an alchemy trainer;
- an alchemy lore / skill book;
- Joy-related alchemical content;
- abortifacient content.

Therefore an xEdit check is required for:

- ingredient records;
- potion / ingestible records;
- magic effects;
- books;
- leveled lists if any;
- trainer/class records;
- NPC records;
- Heartwood Mill cell/reference edits.

### Main concern

If Joy or abortifacients use vanilla alchemy keywords/effects, Apothecary or related overhauls may alter expected magnitude/duration/value/keywords.

This is not automatically a conflict, but it must be verified.

---

## 5. Joy mechanic

The source describes Joy as producing a very strong sexual-memory effect:

> normal sex will feel less satisfying afterward until the memory fades, approximately 400 hours later.

The exact implementation is not described in the source text.

Possible implementation types include:

- magic effect;
- quest variable;
- faction/rank;
- global variable;
- script-based modifier;
- SexLab event hook.

### Required technical audit

- [ ] identify how Joy state is stored;
- [ ] identify the exact duration logic;
- [ ] determine whether “400 hours” means game hours;
- [ ] determine what “less satisfying” changes technically;
- [ ] check whether arousal, orgasm, satisfaction or another mod API is modified;
- [ ] verify compatibility with current **SLO Aroused NG**;
- [ ] verify state survives save/reload correctly;
- [ ] verify state expires cleanly.

This is the most important gameplay-system check in the mod.

---

## 6. SexLab / arousal interaction

The source confirms that the mod includes sex content, but does not specify detailed requirements in the supplied description.

Before adoption, verify:

- [ ] SexLab Framework requirement;
- [ ] whether specific animation tags are requested;
- [ ] whether scenes are player-controlled or forced;
- [ ] whether any arousal framework API is used;
- [ ] whether Joy modifies SexLab statistics or independent quest state;
- [ ] whether scenes can collide with other autonomous systems.

Given the current Rhiven stack, test against:

- SLO Aroused NG;
- SLSF Reloaded / Fame Comments;
- SexLab Survival;
- BaboDialogue;
- SexLab Approach Redux if later retained;
- defeat systems.

Expected conflict risk is probably lower than for Approach or Naked Defeat because the content appears localized and dialogue-driven.

---

## 7. Heartwood Mill edits

The NPC is located at **Heartwood Mill**.

Therefore inspect:

- cell edits;
- navmesh edits;
- placed references;
- packages;
- ownership/faction changes;
- dialogue conditions tied to the mill;
- landscape/worldspace edits if any.

### Risk level

Likely low unless the mod edits existing NPCs or navmesh heavily.

Still perform xEdit conflict review because localized mods can silently overwrite cell/navmesh records.

---

## 8. Incompatibilities

### Deviously Accessible

The author explicitly marks **Deviously Accessible** as incompatible.

Current Rhiven snapshots reviewed for this study do not show that mod by name.

Before installation:

- [ ] search all active left-pane mods again;
- [ ] search plugin list for related plugin names;
- [ ] verify no renamed/merged equivalent is present.

### Old Unethical Illusion

The author also states incompatibility with the older **Unethical Illusion**.

Before installation:

- [ ] verify it is not active;
- [ ] check for leftover plugin/scripts from a previous manual install if ever used;
- [ ] do not run both simultaneously.

---

## 9. Fertility / roleplay decision

Because Rhiven uses BFNG rather than Hentai Pregnancy, there are two sensible integration paths.

### Option A — use Unethical Alchemy without functional abortion integration

Treat the abortifacient as roleplay-only.

Advantages:

- no fertility-framework surgery;
- minimal integration risk;
- preserves the quest/content itself.

### Option B — create or locate a BFNG compatibility patch

Only consider if the mod is otherwise retained and Fabien specifically wants the abortifacient to affect BFNG pregnancy.

Requirements:

- inspect BFNG API/state handling;
- inspect Unethical Alchemy scripts;
- confirm safe early-pregnancy termination logic;
- confirm late-stage behavior;
- test lactation/post-pregnancy transition carefully.

### Current recommendation

Prefer **Option A** unless a clean existing BFNG integration already exists.

Do not modify the fertility system merely to make this small side feature work.

---

## 10. Required archive audit

Before any install:

- [ ] list all files in archive;
- [ ] inspect FOMOD if present;
- [ ] inspect plugin masters;
- [ ] inspect scripts;
- [ ] inspect quests;
- [ ] inspect NPC/dialogue records;
- [ ] inspect Joy effect implementation;
- [ ] inspect pregnancy integration;
- [ ] inspect Heartwood Mill edits;
- [ ] inspect alchemy records;
- [ ] check for loose scripts that overwrite other mods;
- [ ] check for bundled old frameworks/assets.

---

## 11. Test profile

Suggested profile:

`Eleanor 17.3.8 - Unethical Alchemy TEST`

Use a disposable save.

Do not test first on the definitive stable save.

---

## 12. Functional test plan

### Quest / dialogue

- [ ] find intended introduction path through Elgrim;
- [ ] locate NPC at Heartwood Mill;
- [ ] verify trainer dialogue;
- [ ] verify SexLab dialogue;
- [ ] obtain lore / skill book;
- [ ] verify no blocked vanilla dialogue.

### Joy

- [ ] consume / trigger Joy;
- [ ] verify intended scene;
- [ ] verify persistent post-Joy state;
- [ ] test normal SexLab scene afterward;
- [ ] save / quit / reload;
- [ ] confirm state remains valid;
- [ ] advance time;
- [ ] confirm state eventually clears.

### Abortifacient

Without Hentai Pregnancy:

- [ ] verify item/dialogue is still safe;
- [ ] verify no Papyrus spam/errors;
- [ ] verify it does not damage BFNG state;
- [ ] confirm it behaves as RP-only unless proven otherwise.

### Alchemy

- [ ] verify item effects under Apothecary;
- [ ] verify values/keywords;
- [ ] verify no recipe duplication or broken crafting entries.

### Location

- [ ] enter/exit Heartwood Mill repeatedly;
- [ ] save/reload at location;
- [ ] verify NPC packages/navmesh;
- [ ] verify no pathing issues.

---

## 13. xEdit checklist

Check conflicts with:

- Apothecary;
- Alchemy Plus;
- Alchemy Recipe Expansion;
- any Heartwood Mill/location overhaul;
- NPC overhauls affecting the added/edited NPC;
- dialogue overhauls;
- SexLab-related keyword/quest records.

Priority focus:

1. cell/navmesh;
2. NPC;
3. quest/dialogue;
4. alchemy records;
5. magic effects;
6. books;
7. scripts cannot be fully validated through xEdit and require archive inspection.

---

## 14. Translation implications

If retained, translate:

- NPC name if appropriate;
- quest names;
- dialogue;
- Joy item/effect text;
- abortifacient item text;
- book;
- notifications;
- MCM text if any.

Add final translation work to `docs/07-TRANSLATIONS-FR.md` only when the mod is formally retained.

---

## 15. Rollback

If rejected during testing:

1. remove the test-profile mod;
2. revert xEdit patch if one was created;
3. discard disposable saves;
4. do not attempt to clean a developed save;
5. leave stable profile untouched.

If retained later, document exact:

- archive version;
- install choices;
- plugin position;
- conflict-resolution patch;
- translation;
- MCM / gameplay settings;
- Joy behavior;
- fertility behavior.

---

## 16. Provisional verdict

**CANDIDATE — LOW/MEDIUM STRUCTURAL RISK, WITH ONE IMPORTANT FUNCTIONAL MISMATCH.**

### Positive points

- small localized content;
- limited apparent world impact;
- interesting alchemy/RP flavor;
- likely much lighter than major adult-content frameworks;
- pregnancy interaction is optional in concept.

### Main uncertainty

The author's functional abortifacient integration targets **Hentai Pregnancy**, while Rhiven uses **Beeing Female NG**.

Therefore the pregnancy feature should currently be treated as **RP-only / unsupported until proven otherwise**.

### Recommended study priority

Moderate.

Worth testing if Fabien likes the content, but there is no reason to alter the current fertility framework solely for this mod.

**Roadmap verdict:** **CANDIDATE À ÉTUDIER — prometteur, probablement léger, fertilité à traiter séparément.**
