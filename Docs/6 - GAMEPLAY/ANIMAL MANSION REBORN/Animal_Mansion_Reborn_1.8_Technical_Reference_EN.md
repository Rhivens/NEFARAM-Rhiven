# Animal Mansion Reborn 1.8 — Technical Reference

> **Purpose:** compact technical reference for future NEFARAM-Rhiven integration work.  
> **Source:** French reorganized guide `Animal_Mansion_Reborn_1.8_Guide_FR_Rhiven.docx`.  
> **Documented mod version:** 1.8 (2026-10-19).

---

## 1. Overview

**Animal Mansion Reborn** is a complete reboot of the earlier Animal Mansion series:

- The Animal Mansion
- The Animal Mansion Redux
- Animal Mansion Plus
- Animal Mansion 4

It reuses ideas, NPC concepts and quest concepts from the earlier mods, but it is a new mod rather than a simple continuation.

The story starts with **Thaena**, who inherits an abandoned mansion in the lawless region between Falkreath and Hammerfell. She initially intends to turn it into an inn, but the business develops in a very different direction.

The mod includes:

- an introductory quest;
- mansion construction;
- acquisition of the first animals;
- repeatable private shows;
- dog and horse sale demonstrations;
- animal training quests;
- side quests;
- additional followers / NPC content;
- a financial ledger tracking the mansion's income, expenses and profit.

There is **no MCM**.

---

## 2. Player and follower support

- Male and female player characters are supported.
- Creature animations always place the player character in the female animation role.
- A male player character is not forced to participate in creature scenes.
- The mod supports **one female follower** for creature-related activities.
- A female follower can be used instead of the player character for some activities.
- Vanilla and custom followers are expected to work.
- **Tirwin** from *Animal Research* receives custom dialogue when used as the follower; the documentation specifically says to leave Ragnar behind.
- Additional female followers can be acquired through the mod's quests.
- Current voice acting uses **xVASynth**.

### Integration concern

Because NEFARAM-Rhiven uses **Nether's Follower Framework** plus several custom-framework followers, follower handling must be tested carefully rather than assumed safe.

---

## 3. Quest start

To start the mod:

1. Enter **Dead Man's Drink** in Falkreath.
2. Wait for the introductory conversation to begin.
3. Speak to **Valga Vinicia**, the innkeeper.

---

## 4. Animation generation

> **Important:** the mod includes animations.

After installation or after changing animation files, run:

- **GenerateFNISforUsers**, or
- the equivalent behavior-generation tool used by the current setup.

### NEFARAM-Rhiven note

The current Rhiven setup uses **Pandora Behaviour Engine**, so future integration should verify whether the installed AMR package behaves correctly with Pandora and whether any mod-specific FNIS assumptions exist.

Do not assume FNIS is required merely because the original documentation names it.

---

## 5. Requirements

### Legendary Edition

- Fores New Idles in Skyrim (FNIS)
- SexLab
- SexLab Animation Loader

### Special Edition / Anniversary Edition

- Fores New Idles in Skyrim SE (FNIS SE)
- SexLab
- SexLab Animation Loader

### Original reference links

- FNIS LE: https://www.nexusmods.com/skyrim/mods/11811
- SexLab LE: https://www.loverslab.com/files/file/150-skyrim-sexlab-sex-animation-framework-v162-updated-jun-3rd-2016/
- SLAL LE: https://www.loverslab.com/files/file/2488-sexlab-animation-loader/
- FNIS SE: https://www.nexusmods.com/skyrimspecialedition/mods/3038
- SexLab SE/AE: https://www.loverslab.com/files/file/20058-sexlab-se-sex-animation-framework-v166b-01182024/
- SLAL SE/AE: https://www.loverslab.com/files/file/23737-sexlab-animation-loader/

---

## 6. Required animation coverage

The documentation expects the following creature animation combinations:

| Creature | Required / preferred combinations |
|---|---|
| Dog | CF; preferably also FFC, CCF and CCCF |
| Wolf | CF; preferably also FFC, CCF, CCCF and CCCCF |
| Horse | CF; preferably also FFC |

### Recommended pack

**Billyy's SLAL Animations**

https://www.loverslab.com/files/file/3999-billyys-slal-animations-2025-7-1/

Some scenes attempt to call a specific Billyy animation. If that animation is not present, AMR falls back to tag-based animation selection.

### Integration concern

Before adding AMR to NEFARAM-Rhiven, verify:

- installed Billyy version;
- required creature animation registrations;
- More Nasty Critters / Creature Framework state;
- tag availability in the current SexLab registry;
- whether any required animations are filtered or disabled by current NEFARAM settings.

---

## 7. Potential conflicts

### Random scene generators

Mods that independently start random SexLab scenes with the player or NPCs are **not strictly incompatible**, but should be disabled while running AMR quests if they interfere with scripted encounters.

This is a major integration point for NEFARAM because the pack contains several systems capable of initiating scenes.

### Border / worldspace edits

AMR opens Skyrim's borders to place new content outside the normal playable area.

Potential conflict class:

- mods editing land beyond Skyrim's normal borders;
- border-gate overhauls;
- mods editing nearby navmesh / landscape / exterior cells.

The AMR documentation states that no conflict is expected with mods using **Pale Pass**, including:

- Beyond Skyrim — Bruma
- Rigmor of Cyrodiil

This should still be verified against the actual NEFARAM-Rhiven worldspace stack.

---

## 8. Patches mentioned by the documentation

The FOMOD includes or historically added patches for:

- JK's Skyrim
- Cities of the North
- Redbag's Falkreath
- Across the Border — Diverse Border Gates
- The Great Town of Shor's Stone
- Orc Strongholds All-in-One

### NEFARAM-Rhiven relevance

Current Rhiven setup includes, among others:

- Cities of the North — Falkreath
- The Great Town of Shor's Stone
- Spaghetti's Orc Strongholds
- Beyond Skyrim — Bruma
- Northern Roads
- multiple landscape/navmesh patch collections

Therefore the future integration audit must inspect **Falkreath, the border area and mansion-adjacent cells in xEdit** before the mod is accepted into the stable profile.

---

## 9. BodySlide

BodySlide files are optional and are only needed if AMR outfits are to be rebuilt for the player's or followers' body preset.

Recommended workflow from the documentation:

1. Launch BodySlide.
2. Enter `AMR` in **Filter outfits...**
3. Confirm that only Animal Mansion Reborn body / clothing / armor projects remain visible.
4. Enable **Build Morphs** and the relevant option above **Batch Build...**
5. Select the desired preset.
6. Click **Batch Build...**
7. Select the desired AMR slider sets.
8. Build the output.

Holding **CTRL** while clicking **Batch Build...** allows a custom output folder to be selected.

### NEFARAM-Rhiven note

For the Rhiven setup, output should ideally be generated into a **dedicated MO2 output mod** rather than directly into Data or an unrelated BodySlide output.

---

## 10. Main quests

Main story quest names:

1. **The Borderlands**
2. **Stand-in Bitch**
3. **Building the Business**
4. **The Ways of the Wolf**
5. **In Too Deep**
6. **The Animal Mansion**

---

## 11. Repeatable content

### Repeatable show quests

- Dog Show
- Wolf Show
- Horse Show

### Job Board repeatable quests

- Stand-in Bitch
- A Mare for Hire

### Quest stages reference

The original documentation points to:

https://www.loverslab.com/topic/268522-animal-mansion-reborn/page/2/#findComment-7346245

This may be useful for troubleshooting stuck quests.

---

## 12. Version history

### 1.8 — 2026-10-19

- Fixed an issue that could cause the player character to trespass in House Battle-Born.

### 1.7 — 2026-10-18

- Fixed several bugs, including training quests being repeatable when they should not be.
- Completed training quest logs.
- Fixed minor dialogue issues.

### 1.6 — 2026-10-17

- Added two dog sale quests.
- Added two horse sale quests.
- Added two animal training quests.
- Added Thaena's financial ledger, updated after each main quest.
- Limited animal show dialogue to 10:00–21:00.
- Fixed a missing scene for the Battle-Born farm horse sale.
- Fixed a bug allowing Jala and Eveli to be taken simultaneously.
- Updated the JK's Skyrim patch.
- Additional navmesh cleaning.

### 1.5 — 2026-08-08

- Added patch for Across the Border — Diverse Border Gates.
- Added patch for The Great Town of Shor's Stone.

### 1.4 — 2026-08-02

- Revised Falkreath border dialogue for male followers.
- Updated follower detection so actors with `ActorTypeAnimal` or `ActorTypeCreature` are not treated as followers.
- Added Falkreath border dialogue for `NordFemale` guards.
- Changed Thaena and Jala outfit handling to use SexLab store / reequip functions, including custom outfits.
- Added Orc Strongholds All-in-One patch.
- Further cleanup.

### 1.3 — 2026-07-27

- Updated COTN Falkreath patch.
- Fixed Nuria / Larissa scene positioning.
- Corrected chair animation naming and marker placement for Callia scenes.
- Removed activation from Bertran's drafting table.
- Added a "cover self" animation after Derjala is discovered by the player.
- Changed the initial objective to point to the border guard.
- Removed show offers to Bree or Lithindir while they are walking home.
- Added missing quest log entries.
- Further cleanup.

### 1.2 — 2026-07-23

- Fixed player being set Essential.
- Fixed clients remaining in the show room after the player leaves.
- Added NIF fixes.
- Added missing child voice files.
- Removed house-build activation from the Elinhir carpenter's table.
- Corrected Elinhir guard voices.
- Corrected the Rorikstead guard position for the Stormcloak version.
- Cleaned Falkreath border navmesh.
- Fixed floating fence posts behind the mansion.
- Fixed Eveli's door.
- Added Cities of the North patch to FOMOD.
- Added Redbag's Falkreath patch to FOMOD.
- Added exterior lanterns.
- Exterior lanterns now turn off during daytime.
- Front mansion windows glow at night.
- Assigned ownership to objects in Pelamar's Provisions.
- Removed test Lamias.

### 1.1 — 2026-07-19

- Fixed dialogue bugs.
- Added missing objectives.
- Other minor bug fixes.

---

## 13. NEFARAM-Rhiven integration checklist

Before adding AMR to the stable build:

- [ ] Confirm exact AMR release and file set.
- [ ] Install on a dedicated MO2 test profile.
- [ ] Verify masters and plugin type.
- [ ] Check conflicts in xEdit.
- [ ] Inspect Falkreath and border-area worldspace / navmesh conflicts.
- [ ] Verify COTN Falkreath patch compatibility with the exact COTN build in NEFARAM.
- [ ] Verify The Great Town of Shor's Stone patch.
- [ ] Determine relevance of Orc Strongholds patch to the current Spaghetti's setup.
- [ ] Verify Beyond Skyrim — Bruma / Pale Pass coexistence.
- [ ] Verify Northern Roads / landscape patch interactions.
- [ ] Confirm animation coverage for dog, wolf and horse scenes.
- [ ] Confirm Billyy animation availability and tags.
- [ ] Test with the current SexLab / SLAL registry.
- [ ] Test Pandora behavior generation.
- [ ] Test with Creature Framework / More Nasty Critters.
- [ ] Test follower detection with NFF.
- [ ] Test with one custom-framework follower present but not recruited into NFF.
- [ ] Identify scene-generator mods that may need temporary suspension during AMR quests.
- [ ] Generate AMR BodySlide output into a dedicated MO2 mod if needed.
- [ ] Start a new test game or use a disposable integration save.
- [ ] Validate the complete main quest chain.
- [ ] Validate repeatable quests.
- [ ] Test save / reload during and after scripted encounters.
- [ ] Check Papyrus logs for recurring AMR errors.
- [ ] Confirm no permanent Essential state, stuck follower state, scene state or trespass state remains after quests.

---

## 14. Initial integration risk assessment

### High-priority checks

1. **Worldspace / navmesh**
   - Falkreath
   - border area
   - mansion exterior
   - nearby roads / landscape

2. **Scripted SexLab scenes**
   - random scene generators may interrupt AMR scenes;
   - specific Billyy animations may be requested;
   - fallback relies on tags.

3. **Followers**
   - one female follower is supported;
   - NFF and custom follower frameworks require testing;
   - AMR has already had historical fixes around follower detection.

4. **Creature stack**
   - dog, wolf and horse animation coverage is mandatory;
   - Creature Framework / MNC compatibility should be validated against the actual NEFARAM build.

### Medium-priority checks

- BodySlide assets;
- outfit strip / reequip handling;
- house / interior conflicts;
- dialogue and AI packages;
- patches supplied by FOMOD.

---

## 15. Working rule

This Markdown file is **not an installation approval**.

It is a compact reference intended to make future AMR integration work easier to audit, compare and troubleshoot.

The Word guide remains the human-readable illustrated document.  
This Markdown file is the technical quick-reference version for repository work and future ChatGPT-assisted integration.
