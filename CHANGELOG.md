# Changelog

## 2026-10-25

### Bathing in Skyrim guide and Needs Widget AIO status

- Reworked `docs/09-SURVIVAL-BLOOD-HYGIENE.md` into a publication-ready English guide with a compact Quick Setup section followed by the complete technical procedure, validation register, troubleshooting and pre-playthrough checks.
- Restored **Needs Widget AIO** as the final retained and validated display layer, with its supplied **Vel'Dun** preset present, active and tested in game.
- Kept the validated responsibility split explicit: **EBT = environment / Just Blood = actors / BiSR = hygiene / SunHelm = needs / Campfire = camping / Needs Widget AIO = display only**.
- Kept `Widget Addon - Keep It Clean - Bathing in Skyrim - Rhiven` and `WA_BathWidget.esp` classified as retired, disabled and available only for rollback.
- Synchronized the added-mod inventory, finalization roadmap and pre-playthrough checklist with the same status language.

### Animal Mansion Reborn 1.8 — technical integration

- Completed the full AMR conflict audit against the current **NEFARAM-Rhiven 17.3.8** baseline.
- Retained `COTN -Falkreath AMR.esp` after its clean xEdit result and confirmed functional placement role.
- Kept the supplied Shor's Stone patch disabled because of unresolved NAVI / navmesh references.
- Created **`Animal Mansion Reborn - Rhiven Patch.esp`** as a minimal compatibility layer covering the MNC Husky model assignment, safe Shor's Stone placement reconstruction, required AMR dialogue merges and localized CELL adjustments.
- Validated the Rhiven patch with xEdit Check for Errors: **21 processed records / 0 errors**.
- Regenerated **Synthesis Output** after final AMR and Rhiven patch placement.
- Selected the complete **xLODGen → TexGen → DynDOLOD** workflow; xLODGen generation is currently in progress.
- Current status: **technical integration complete; generated-output chain and final AMR in-game smoke tests still pending**. No gameplay validation is claimed yet.
- Updated the AMR guide, finalization roadmap, added-mod inventory, testing sheet and pre-playthrough checklist to reflect the same status.

## 2026-10-24

### Defeat-system migration — Naked Defeat 6.50

- Began the controlled migration of the NEFARAM defeat stack from **Acheron + Practical Defeat Reanimated + Yamete Kudasai** to **Acheron + Naked Defeat 6.50**.
- Retained **Acheron 1.11.3**, **Acheron - Simple Recover** and **Acheron - Diary of Mine Extension** as the framework/support layer; disabled **Practical Defeat Reanimated**, its voicepack and the complete **YameteKudasai** MO2 mod for deterministic testing.
- Installed and audited **Naked Defeat 6.50**, **Acheron - Naked Defeat Bridge**, and the optional OAR packages. **Bowed Animations - fixed** is retained; **Crawl Animations V2** remains installed but disabled because Bowed overwrites the same locomotion files.
- Created **Naked Defeat - Rhiven Fix.esp** with only four targeted overrides: two malformed wrist-chain ARMA records and two malformed WEAP CRDT records. xEdit Check for Errors: **0 errors / 5 processed records**.
- Validated **Acheron - Naked Defeat Bridge.esp** in xEdit: **0 errors / 3 processed records**. The target runtime chain is now **Acheron → Acheron Bridge → Naked Defeat**.
- Identified an incomplete **Civilian Rape** branch in Naked Defeat 6.50: the active `qst2` property points to a missing quest. Required Rhiven workaround: **`IndecencyRapeProb = 0`** in the Naked Defeat MCM.
- Audited Naked Defeat's remaining xEdit warnings and deliberately left obsolete / unreferenced quest, package, dialogue and scene residue untouched instead of performing blind cleanup.
- Reviewed Yamete Kudasai scripts and Acheron consequence YAML; the overlap with Naked Defeat is high enough to make concurrent testing unreliable and community troubleshooting also identifies the combination as incompatible.
- Reused the former Practical Defeat plugin area for the final relative order: **`Naked Defeat.esp → Naked Defeat - Rhiven Fix.esp → Acheron - Naked Defeat Bridge.esp`**.
- Added a full English migration guide for NEFARAM users: [Naked Defeat integration](docs/guides/NAKED-DEFEAT-INTEGRATION.md), including a placeholder for the future public Rhiven Fix download.
- Current status: **technical integration verified and validated; in-game testing in progress**. Remaining critical checks include humanoid/creature/follower defeat, repeated events, Acheron bleedout recovery, actor release/pacification cleanup, and save/reload stability.


### LoversLab final-candidate pass — Approach Redux and Unethical Alchemy

- Installed **SexLab Approach Redux 3.62 - Rhiven** using the **OAR** branch. The only MO2 file conflict observed is with the historical `SKSE Output/SKSE/Plugins/BakaFactory/SLAppAutoMCM.json`; the empty 3.62 JSON is retained as the clean active baseline.
- Confirmed the 3.62 MCM initializes correctly and exposes the current options, including **OnlyinTown**, **Sex CoolTime** and compatibility toggles for SLHH, BaboDialogue, FillHerUp, SexLab Survival and DDI.
- Preserved the old `NEFARAM - 263` AutoMCM JSON as a **tuning reference only**. Selected historical values will be reconsidered during the final Mega-session MCM rather than imported blindly; Approach frequency/probability will be kept deliberately lower for Eleanor.
- xEdit Check for Errors on `SexLab Approach.esp` processed **5,546 records** and identified one VMAD warning group in `SLApproachAskForSex2Quest`: the generated fragment still references aliases 0, 2 and 3 while the quest's current Aliases section is empty. No invasive correction is applied; the AskForSex2 branch is flagged for targeted in-game validation.
- Installed **Unethical Alchemy 1.0.0 - Rhiven**. Archive is lightweight (ESP + scripts/source + sound), with no MO2 file conflicts and no DLL/OAR/Pandora payload identified.
- xEdit found one genuine unresolved AI-package reference on **Agryn Gaering**: package FormID `xx002436` did not exist. Created **Unethical Alchemy - Rhiven Fix.esp** as a dedicated override removing only that orphaned package entry while preserving Agryn's seven valid packages.
- The Rhiven fix passed xEdit **Check for Errors: 0 errors / 2 records** and is enabled immediately after the base mod.
- Current status for both mods: **technical integration complete / retained for gameplay testing**. Approach still needs autonomous-dialogue/AskForSex2 and overlap testing; Unethical Alchemy still needs Heartwood Mill, Joy, Apothecary and BFNG/abortifacient behavior checks.

## 2026-10-23

### Final candidate pass — graphics and QoL validations

- Retained **MESH2 ENB - Max's Edited Silent Horizons 2 1.2.1** as the preferred evolution of the existing **Silent Horizons 2 1.13 + ReShade / Sswaye LUT13** setup.
- Integrated MESH2 **selectively rather than by full overwrite**: kept the modern SH2 1.13 structure and merged targeted settings for eyes, skin SSS, AO/SSIL, IBL, Complex Grass, Complex Material, Dynamic Cubemap and selected water parameters.
- Preserved **ENB Manager Set 3** as the clean rollback reference (`SH2 + ReShade Sswaye LUT13`) and retained **Set 4** as the active MESH2 variant (`SH2 + ReShade LUT13 + MESH2`).
- Isolated the runtime-generated `Shaders/Features/TerrainHelper.ini` into the dedicated MO2 override **MESH2 - TerrainHelper Config**, enabled only with the MESH2 slot.
- A/B testing favored the MESH2 rendering despite a moderate accepted performance cost on the reference scene (about **63.1 FPS MESH2 vs 70.7 FPS SH2**).
- Installed and validated **ENB Dynamic Cubemaps 1.01** after **Quality CubeMaps - HD Cube Maps**. No abnormal eye reflections, broken materials or other obvious visual artifacts were observed in-game.
- Kept `NEFARAM Patches` winning the three intentional cubemap exceptions `chrome_e.dds`, `glacierice_e.dds` and `ore_obsidian_e.dds`; the obsidian file is a genuine 64×64 static cubemap retained as an intentional NEFARAM visual exception.
- Added and validated **Needs Widget AIO** with the supplied **Vel'dun** preset. It correctly appears in-game and consolidates survival/needs information without replacing the underlying survival systems.
- Disabled **Widget Addon - Keep It Clean - Bathing in Skyrim - Rhiven** as a redundant widget layer; it remains installed for rollback until the final cleanup pass.
- Added and validated **Dino's Easy Quest Fix**. Its MCM correctly lists active quests, current stages, objectives and next stages; it is retained as a diagnostic/assistance tool, with manual-save-before-advance as the usage rule.
- Added and validated **Item Vault - Plugin Explorer**. On the Rhiven load order it opened instantly while indexing about **46,831 items across 466 plugins**, and found the custom **Phoenix Katana - Eleanor** within seconds.
- **AddItemMenu remains active** as the fast familiar item tool. **Modex 3.0.2 - Rhiven** and **Modex - 3.0.2 Patch - Rhiven** were disabled as redundant during the Item Vault comparison; no missing masters appeared. Both remain installed temporarily for rollback until several hours of final-playthrough use confirm they are unnecessary.

## 2026-10-21

### NEFARAM 17.3.8 — technical migration complete

- Completed the controlled manual migration of the customized Rhiven build from **NEFARAM 17.3.7 to 17.3.8** without running Wabbajack against the customized installation.
- Promoted **`Eleanor Stable 17.3.8`** as the current stable MO2 baseline; pre-migration profiles remain rollback references.
- Migrated and validated the main 17.3.8 technical replacements, including **SKSE64 2.2.8**, **Address Library v13**, **SPID 7.3.3**, **powerofthree's Tweaks 1.17.1**, **AnimObject Swapper 2.0.0**, **S.L.A.C.K 1.5.1**, **JContainers SE 4.3.3**, **Native EditorID Fix 1.2.3**, **PEPE 2.3.7.0**, **KID 4.1.0** and **XPMF 0.7.1**.
- Migrated gameplay/framework components including **Acheron 1.11.3**, **Advanced Nudity Detection 4.1.5**, **SLSF Reloaded 4.1.2**, **Modex 3.0.2**, **PPA 0.0.38** and **Cinematic Conversation Camera 1.5.0**. Startup/technical validation is complete; explicitly documented gameplay-only checks remain deferred to the definitive playthrough where appropriate.
- Added and retained the 17.3.8 content-sensitive Rhiven choices: **RaceMenu Portraits 1.2.0**, **Skyrim Performance Solution 1.0.64** with a dedicated Rhiven INI, **Acheron — Sacrosanct Patch 1.1.0**, **Serana Revamped / Lust of a Mother voice layer**, and **Valerica Lust of a Mother 1.25 Slab Edition**.
- Confirmed the setup remains **CBBE/3BA**, so official UBE-specific PPA steps are not applicable.
- Final structural audit confirmed **1,988 plugins** versus the **1,985-plugin** pre-migration baseline; the three intended additions are `PerkEntryPointExtender.esl`, `Acheron - Sacrosanct Patch.esp` and `KVSeranaLustOfAMother.esp`, while all pre-existing plugins retain their relative order.
- Refreshed the Rhiven MO2 left/right snapshots to reflect the active 17.3.8 setup.
- The migration phase is closed, but the full customized build is not yet declared playthrough-ready: **French translations, final pre-playthrough checks and several gameplay-only validations remain in progress**.
- Full procedure and validation register: [Update NEFARAM 17.3.7 -> 17.3.8](docs/15-UPDATE-17.3.7-TO-17.3.8.md).

## 2026-10-16

### Eleanor outfits — KID / modesty classification validated

- Completed the full modesty / nudity-classification audit for Eleanor's personal outfit collection under `15.1 - Outfits Eleanor`.
- Compared the added outfits against NEFARAM's existing `modesty_KID.ini` plus specialized Advanced Nudity Detection / OSL / SLA / BOOBIES KID files.
- Kept existing community coverage when sufficient and created only the missing Rhiven `NoModesty*` rules.
- Created the dedicated reversible MO2 mod `Eleanor Modesty KID - Rhiven` containing `Rhiven_Eleanor_Modesty_KID.ini`; no original NEFARAM/community KID file was edited.
- Reviewed specialized KID coverage for Aradia Bikini, COCO Luscious Lady, Dark Dreams, COCO Caress of Venus, Aether, Nocturne Armor, ELLE Dark Rebel and Stalhrim Bikini; confirmed those files provide complementary AND / SLA / BOOBIES classifications rather than replacing the Rhiven modesty layer.
- Keyword Item Distributor startup log confirms `Rhiven_Eleanor_Modesty_KID.ini` is detected and loaded; no parsing error attributable to the Rhiven file was found.
- Remaining validation is intentionally post-start: verify actual modesty / AND / OSL reactions with Eleanor wearing representative outfits in the definitive playthrough.
- Status: **KID / modesty integration complete; French translation pass is next.**

## 2026-10-14

### UI/HUD — Vel'Dun, Modern Wait Menu, Bestiaire et reskins Dragonborn (14/10/2026)

- Conservé **Vel'dun UI 1.0.6** et **Vel'dun UI Patches 1.0.6** : la version principale 1.0.7 avait été écartée après un problème observé avec le menu Échap en jeu. Ne pas la réinstaller automatiquement.
- Identifié dans le changelog de Nithog que l'habillage **Modern Wait Menu** appartient au module séparé **Vel'dun UI Overhauls** et non au principal ou au pack Patches. Installé **Modern Wait Menu - Rhiven** avec **Vel'dun UI Overhauls - Rhiven** ; capture du FOMOD Overhauls affichant la version **1.0.7**, option `Wait/Sleep Menu → 2. Modern Wait Menu`.
- Dans le même FOMOD : **Dragonborn's Bestiary → 2A. Bestiary Patch** (16:9) ; **Quest Journal → Skip** (Knotwork SkyUI est présent, mais Quest Journal Overhaul n'est pas installé).
- Rétabli les reskins personnels **Dragonborn Reskin - SkyUI Inventory Category Icons - Rhiven** et **Dragonborn Reskin - STB Active Effects - Rhiven**. L'ordre gauche MO2 constaté : Modern Wait Menu → Wheeler → Perfected Wheeler → Compare Equipment NG → STB Widgets → Vel'dun UI → Vel'dun UI Patches → Vel'dun UI Overhauls → Dragonborn Wheeler reskins → Dragonborn Category Icons → Dragonborn STB Active Effects → presets HUD.
- MO2 montre Vel'dun Overhauls gagnant sur `interface/sleepwaitmenu.swf`, `interface/Shared Elements/PlatformButtons.swf`, `interface/bestiarymenu.swf` et `interface/exported/widgets/bestiary/bestiarywidget.swf`; `favoritesmenu.swf` est également remplacé (contrôle fonctionnel des favoris encore conseillé).
- **Tests en jeu visuels réussis** : menu d'attente circulaire Vel'dun affiché, menu Bestiary redessiné affiché (vide sur le personnage de test), icônes d'inventaire Dragonborn colorées visibles. La présence d'effets actifs STB n'a pas été testée faute d'effet sur le PJ. La capture ne démontre pas encore l'exécution d'une attente complète, ni la persistance après redémarrage, ni un contrôle exhaustif du menu Échap.
- **Outfit Gallery** mise à jour de **1.0.14 à 1.0.15** : ouverture de l'interface confirmée en jeu ; fonctions de galerie/presets multiples à approfondir dans la partie réelle ; automatisation des tenues des compagnons **non souhaitée**, vérifier et laisser désactivée. Une traduction FR externe `Translation.json` est envisagée via un mod MO2 indépendant, après vérification du format.
- Avant francisation : reste **Phoenix Katana** à installer, puis à personnaliser dans un plugin Rhiven séparé pour Eleanor. Ne pas déclarer le katana déjà installé ni les traductions déjà effectuées.


### Panneaux routiers — remplacement RSO par Point The Way + My Road Signs are Beautiful FR

- Found a visibly displaced / floating added sign near Riverwood. More Informative Console identified `RoadSignFalkreath01L`, base `000D8D9B`, reference `FE6B8849`, last changed by `RoadSignsOverhaul 2.0.esp` in the test load order.
- Disabled `Road Signs Overhaul 2.0 - Rhiven` for a disposable-save diagnostic: the extra sign disappeared. Confirmed it was a **supplementary sign near the original**, not a broken vanilla sign.
- Disabled (retained in MO2 for rollback): `Road Signs Overhaul 2.0 - Rhiven`, `Road Signs 2.0 - Questionable Clutter Remover (BOS) - Rhiven`, and `Road Signs Overhaul 2.0 - Blended Roads Patch(BOS) - Rhiven`.
- Installed and enabled in left-pane block `41 - Homes Eleanor`: **`Point The Way - Rhiven`** (additional road signs) and **`My Road Signs are Beautiful - French`** (French inscription / weathered texture replacer, 1.6.1FR).
- French FOMOD selections documented: principal **version abîmée 4K–2K**, Point The Way **texture gravée 4K–2K**, Beyond Skyrim – Bruma **4K–2K**, Wyrmstooth **4K–2K**, Cutting Room Floor **Non merci** (not separately installed; the French PNO bundle is not in this build); absent optional mods **Non merci**.
- In a fresh disposable in-game test near Riverwood, French signs appeared legible (e.g. Rivebois, Blancherive, Solitude, Épervine). Signs were assembled properly in the observed locations; the former floating extra sign was gone. No purple missing-texture symptoms observed in the shared screenshots. Conditions were rainy/foggy; general weather and distance testing remain pending.
- **No TexGen/DynDOLOD regeneration performed.** Since Point The Way adds placed objects, LOD integrity is not claimed fully validated; watch for distant mismatches during normal travel. No save from the diagnostic run should become the definitive playthrough baseline.
- **Documentation note:** older historical entries for RSO refer to the former configuration, not the current active mod set. Full MO2 snapshot files await a new export from the actual installed setup.

### Choix graphique final — Silent Horizons 2 + ReShade Sswaye LUT13

- Completed the graphics comparison on **NEFARAM 17.3.7** after finishing the planned mod installations. Reference setup: **1920×1080**, display **74.97 Hz**, RTX 4070 12 GB, target around **60–70 FPS**.
- Tested **Silent Horizons 2 Universal Core 1.13** against the previous ENB preset. Saved the personalized configuration in ENB Manager **Slot 3**, including **Interior Exposure +0.50**, preserved DLAA and verified terrain/complex parallax settings. In-game checks showed good rendering for interiors, snow, night scenes and water; observations included roughly **74.9 FPS** in several test locations.
- Trialed **Community Shaders 1.9.1 + Effects 11 + NAT Effect 11**, including Lux CS and related components, on a separate test configuration. The exterior color balance and water looked good, but overall graphical depth was less convincing to the user; a camera zoom regression was observed on the CS setup. The SkyParkour test issue was traced to its **MCM activation**, not proven to be caused by CS.
- Investigated Water for ENB compatibility during the CS trial: **DynDOLOD.esm** and **_NEFARAM_____MAIN_____.esp** still depended on the Water for ENB plugin chain. Water for ENB was temporarily retained for that test rather than removing required masters; no speculative DynDOLOD edits were made.
- **Decision:** do **not** retain Community Shaders for the final setup. Returned to the clean pre-experiment NEFARAM instance at `C:\JEUX\NEFARAM`; preserved the CS experiment separately as `C:\JEUX\NEFARAM_CS`. Reinstalled the previously validated **Silent Horizons 2 – Rhiven** preset from the saved Slot 3 files, confirmed Interior Exposure **+0.50**, parallax values, successful in-game launch and **working camera zoom**.
- Installed **ReShade 6.8.0 Full Add-on Support** alongside ENB, using `dxgi.dll` for ReShade while retaining ENB's `d3d11.dll`. Installed Sswaye's provided shaders/textures, set ReShade effect/texture search paths and confirmed shaders compiled and loaded.
- Compared **Sswaye ReShade Normal** against **LUT13** in the same exterior scene. **LUT13 selected** (enabled effects: `DPX.fx`, `Clarity.fx`, `LUT13.fx`); Normal judged too colorful and LUT21 too blue.
- **Follow-up:** validate preset persistence after restart, test stability and FPS/frametimes in more scenes, save final ENB/ReShade configurations, then move on to French localization, pre-final checklist and the final game start via `NEFARAM_Start`.
- Updated [finalization roadmap](docs/16-FINALISATION-ROADMAP.md) to reflect the decision and remaining checks.

## 2026-10-11

### Animations Eleanor — Seamless conservé, Gulan0 locomotion validé

- Investigated Gulan0 Female Random Idle V1 and V2 in OAR 3.2.0; priority 900009 allowed in-game testing, and an OAR user.json recorded 62 unwanted variants disabled.
- After comparing with the old NEFARAM V16 notes and the current NEFARAM stock animations, decided to keep **Seamless Varied Feminine Idles** for idle poses. Gulan0 Idle V1, V2 and idle settings remain locally present but **unchecked** in MO2.
- Installed **Gulan0 Walk-Run-Sprint OAR-player**; confirmed player-only OAR conditions and 11 female movement HKX (5 walk / 5 run / 1 sprint).
- Found Legacy DAR submod 1000001 winning original movement events. Applied a Gulan0 female priority override **1000002** via a separate OAR user.json and verified walk/run/sprint replacements in Animation Log.
- Compared August 2026 female_run_Update with original Gulan0 running animations and **removed the five update HKX** by aesthetic preference; kept the **female Sprint Revised** replacement `mt_sprintforward.hkx` only.
- Preserved the original animations and unmodified conditions of NEFARAM's special animation frameworks. OAR user configurations staged in dedicated Rhiven MO2 mods; future-new-game settings do not depend on the temporary start-save.
- Added [ANIMATIONS technical guide](docs/guides/ANIMATIONS/README.md) with installation, diagnostics, priority/persistence and rollback procedures.
- Status: **animation configuration selected and observed working; rare gameplay states still to be monitored during Eleanor's real playthrough**.

## 2026-10-09

### Simple Offence Suppression MCM 0.6

- Installed `Simple Offence Suppression MCM - Rhiven` immediately beneath stock `Simple Offence Suppression` in MO2 block `22`; the original is an SKSE DLL mod without ESP.
- No new file conflicts observed; `Simple Offence Suppression MCM.esp` is ESL-flagged (observed MO2 plugin priority 1950 / FE:C67).
- MCM initialized in-game; options for allowing friendly fire outside combat and while sneaking are visible. The copy of `po3_SimpleOffenceSuppression.ini` in SKSE Output was apparently rewritten but values remained unchanged in the before/after files.
- Status: **MCM initialized; actual friendly-fire damage and AI reaction testing deferred to real gameplay**.

### FLICK / Menu Studio / Fitting Room 1.2.0 — wardrobe experiment

- Installed `FLICK - Fuzz's Legally Intelligible Core Kit - Rhiven`, `Menu Studio - Rhiven` (1.2.0), and `Fitting Room - Rhiven` (1.2.0) in `43 - Added Mods SFW`; FLICK/Menu Studio showed no file conflicts; Menu Studio has no ESP.
- Reused existing `ImGui Icons`, `Show Player In Menus`, and `Show Player In Menus - Persistent Zoom Fix`; kept the existing SkyUI 5.2 / Dragonborn UI configuration intact.
- Menu Studio FOMOD: `The dressing room` + `The star dome`; starry studio environment observed in-game. Custom `Eleanor's Dressing Room` backdrop retained as a future optional creative project.
- Fitting Room FOMOD: `Freeform`, `Leave my face alone`, `All dyes unlocked`; face replacement/RaceMenu preset loading disabled, dyes available, no prerequisite physical outfit.
- FLICK configuration pages registered and opened in-game. Changed Fitting Room editor shortcut to `N` (`iEditorKeyDIK=49`); editor opens **while Skyrim inventory is open**, not directly from open-world gameplay (`iDirectEntryKeyDIK=0`).
- Real in-game editor verified: scanned outfit plugin collections, listed Aether and many other outfit sets, and previewed Aether on Eleanor inside Menu Studio's star environment. This is a **visual transmog / appearance**, not actual gear added to inventory.
- `Outfit Gallery - Visual Outfit Manager - Rhiven` remains installed but was unchecked only during the Fitting Room test. **Do not remove either wardrobe tool yet**: choose Outfit Gallery, Fitting Room or coexistence at pre-playthrough decision point.
- Pending: verify saved/applied transmog persists outside editor, decide desired physical-gear vs cosmetic appearance workflow, confirm scenes/undressing (SexLab / Devious Devices), and test any keybind conflicts. Scene suspension is configured but not yet validated with SexLab.

## 2026-10-08

### Missives / Replacing Boards / SL Dirty Deeds — installed and first in-game check

- Installed `Missives 2.03 SSE - Rhiven`, `Replacing Boards for Missives - Rhiven` (v2.12) and `SL Dirty Deeds Missives - Rhiven` (v1.4.2) under `46 - Added Mods NSFW`.
- Replacing Boards is the higher-priority complete Missives replacement: `Missives.esp`, `Missives.bsa` and MCM configuration are overridden; original Nexus installation is retained beneath it in MO2.
- Enabled Dirty Deeds' core ESP and `Race Edits` ESP after `Missives.esp`.
- Initial xEdit Check for Errors: Missives 2,399 records / 0 errors; Dirty Deeds 340 / 0; Race Edits 6 / 0.
- Full-load-order audit of the five modified creature races found a male-height rollback in WolfRace `0001320A` (1.000000 → 1.200000) from Race Edits; Falmer, Giant, Troll and Frost Troll relevant changes retained.
- Created `SL Dirty Deeds - Race Compatibility - Rhiven.esp` (ESL-flagged), loaded after Race Edits: restores WolfRace male height to `1.000000` while keeping `Allow PC Dialogue`. xEdit Check for Errors: **0 errors / 2 records**.
- In-game Whiterun check: Missives MCM General / Rewards displayed correctly; replacement noticeboard placed and accessible without obvious clipping; Dirty Deeds contract notes present in its inventory.
- Status: **installation and initial integration validated; full Dirty Deeds quest and scene tests deferred to the real playthrough**. French translations deferred until modpack completion.

### PAMA / Prison Alternative — core block validated

- Completed installation of the planned PAMA core with Bad Ends Riften 1.3.2, Bad Ends Solitude 1.8.0 Revision 2 and Orkish Bounty Hunters 0.4.
- Added a concise PAMA README header explaining how the Rhiven setup extends NEFARAM's original `Added Mods` area with numbered personal separators and a dedicated `44 - PRISON PAMA SYSTEM` block.
- Bad Ends Riften:
  - Pandora total: **39,252** (+30)
  - targeted xEdit audit completed
  - PAMA navmesh retained; no compatibility patch required
  - minor vanilla-well visual overlap deferred to the definitive playthrough
- Bad Ends Solitude:
  - Pandora total: **39,298** (+46)
  - targeted xEdit and in-game pathing checks completed
  - Animal Research / Saffron pathing observed working
  - added `PAMA - Solitude Location Patch - Rhiven.esp` to restore `SolitudeLocation` on `SolitudeOrigin [00037EE9]`
  - xEdit Check for Errors: **0 errors / 17 records**
- Orkish Bounty Hunters:
  - manual ambush start validated
  - scripted poison / KO flow validated without defeat-framework interception
  - jail, camp, escape and recapture paths validated
  - one isolated recapture CTD was not reproducible during repeated retests
- Final Pandora checkpoint for the complete tested PAMA block: **39,298 animations**.
- Decision: PAMA core accepted for the Rhiven build; remaining work is limited to real-playthrough observation and the intentionally deferred full Sovngarde return scenario.

## 2026-10-07

### NEFARAM 17.3.7 — active Rhiven baseline

- Current customized instance now runs on **NEFARAM 17.3.7**.
- The active setup includes the 17.3.7 migration components previously staged for review:
  - Inventory Refresh Fix
  - Standing Stealth
  - Core Impact Framework 2.0.7
  - Meshes Optimization Project
  - SLSF Reloaded 4.1.1
- Refreshed the MO2 left-pane and right-pane/plugin snapshots so the repository matches the current local instance.

### PAMA / Prison Alternative — staged integration

- Created dedicated MO2 separator `44 - PRISON PAMA SYSTEM`.
- Installed and began validating:
  - Next-Gen Decapitations
  - Pama's Deadly Furniture 3.4.5 Revision 2
  - Prison Alternative 2.0.3
  - Pama Sovngarde Aftermath 1.0.0
  - Punishment Pack 1.3.0
  - Outdoor Event Pack 1.3
  - Bad Ends Revived: Windhelm 1.3.0
- Added dedicated `Next-Gen Decapitations - Sovngarde INI - Rhiven` override with the Sovngarde resurrection settings.
- Deadly Furniture:
  - nonlethal ragdoll / recovery flow validated in `pamaTestZone`
  - lethal guillotine execution tested without CTD
- Prison Alternative:
  - MCM and Event Registry initialized correctly
  - vanilla arrest and Whiterun prison handoff validated
  - existing vanilla `CivilWarCot01L` (BaseID `000E2826`) works correctly; no replacement required in Whiterun
- Sovngarde Aftermath:
  - MCM initialized
  - lethal PAMA execution correctly transferred the test character to Sovngarde
  - full return scenario intentionally left untested to avoid spoilers
- Pandora checkpoints progressed from 39,142 (Deadly Furniture) to 39,222 animations after the currently installed PAMA modules.
- Bad Ends Windhelm xEdit audit found obsolete / vanilla-like navmesh overrides.
- Created `PAMA - Windhelm Navmesh Patch - Rhiven.esp`:
  - `000FC117` restored from WindhelmSSE Exterior NavMesh Fixes
  - `0004B66C` restored from Capital Windhelm Expansion - Skyrim Sewers
  - ESP flagged ESL
  - Bad Ends Windhelm added as explicit master
  - xEdit Check for Errors: **0 errors / 7 records**
- Created `PAMA - NEFARAM ZaZ Ankle Chains Patch - Rhiven` so the NEFARAM-patched `ZaZAnkleChainsRagdolls_1.nif` wins over the older Bad Ends Windhelm copy.
- Remaining PAMA core work: Riften audit, Solitude audit, Orkish Bounty Hunters, city pathing tests, and the complete Sovngarde return test.

### TNTR / trap ecosystem — initial integration

- Added modern runtime frameworks in `43 - Added Mods SFW`:
  - `SkyPatcher - AE - Rhiven`
  - `Object Impact Framework (OIF) - Rhiven`
- Added the TNTR trap stack in `44 - Added Mods NSFW`:
  - `Trap Needs to be Real Trap - Rhiven` — TNTR 0.74
  - `EET Extra Evil Traps - Rhiven` — EET 1.2.3
  - `O Skyrim Has Insane Traps - Rhiven`
  - `OMNOMS Not So Obvious Mimics - Rhiven` — OMNOMS 1.3.0
  - `Deadly Bear Trap - Rhiven`
  - `Watch Your Step - Rhiven` — v1.2
- TNTR FOMOD selections:
  - Replacer enabled
  - New Baka Traps enabled
  - OAR patch selected
  - Nemesis-style behavior patch selected for use with Pandora
- EET configured with patched Bear Trap and Snare Trap scripts for TNTR 0.73 / 0.74.
- OMNOMS configured with:
  - patched TNTR v0.7x Mimic script
  - Mimic activation-text replacement
  - experimental vanilla-chest shader replacement disabled
  - SkyPatcher distribution to Magic Vendors + Spell Tomes
  - General Vendors distribution disabled
  - O.S.H.I.T compatibility patch enabled
- Corrected MO2 conflict priority so OMNOMS loads after O.S.H.I.T and its `SKSE\\Plugins\\ObjectImpactFramework\\OSHIT-OIF.json` override wins as intended.
- Watch Your Step uses the current v1.2 main file for TNTR >0.46; the old O.S.H.I.T v0.4-only optional file was not installed.
- Initial New Game validation:
  - game launch: **OK**
  - no startup CTD observed
  - no obvious initialization anomaly observed
  - TNTR MCM registered
  - TNTR: Extra Evil Traps MCM registered
  - TNTR: Not So Obvious Mimics MCM registered
- Stack status: **technical initialization validated / real-game field testing still pending**.
- Planned early-playthrough checks include Mimics, Bear Trap, Snare/QTE, O.S.H.I.T / Watch Your Step placement, and interactions with Fill Her Up Baka, Devious Devices and Acheron / Practical Defeat.
- Load-order snapshot refresh intentionally deferred until the remaining planned mods are installed.

### Outfit Gallery - Visual Outfit Manager

- Installed `Outfit Gallery - Visual Outfit Manager - Rhiven` in `43 - Added Mods SFW`.
- Initial file-conflict review showed only documentation / license file overlaps with other CommonLibSSE-based mods; no functional conflict observed.
- In-game validation:
  - SKSE menu opens correctly: **OK**
  - default gallery hotkey `F8`: **OK**
  - no startup CTD observed
- Purpose: provide Eleanor with a scalable visual wardrobe manager for the large personal outfit / armor collection.
- Status: **Validated**.

### Regional Outfitters - Stalls of Skyrim

- Installed `Regional Outfitters - Stalls of Skyrim - Rhiven` in `43 - Added Mods SFW`.
- SkyPatcher framework reused from the current Rhiven setup.
- FOMOD compatibility patches selected for mods present in NEFARAM-Rhiven:
  - Capital Windhelm
  - Obscure's College of Winterhold
  - AI Overhaul
- Other city / college overhaul patches left disabled because the corresponding mods are not present in the current modlist.
- In-game validation performed with console `coc` tests across several cities.
- Results:
  - game stability: **OK**
  - no CTD observed
  - no obvious stall / vendor placement problem observed in the tested locations
- Status: **Validated** for initial integration; normal long-term inventory refresh behavior will be observed during the real playthrough.


### Private Needs - Orgasm 1.11.1

- Installed / updated `Private Needs - Orgasm 1.11.1 - Rhiven` in `44 - Added Mods NSFW`.
- Previous personal reference version was 1.8.3; 1.11.1 includes substantial SKSE-side runtime changes and fixes.
- Rhiven usage remains deliberately limited to **natural needs**:
  - bladder
  - bowel
  - urination / defecation animations and interactions
  - orgasm-related urination disabled in MCM
- Optional integrations intentionally skipped for now:
  - Dynamic Bloodpool Framework / puddles
  - Dooty
  - SkyrimNet
- Initial in-game validation:
  - launch: **OK**
  - bladder fullness percentage displayed correctly
  - bowel fullness percentage displayed correctly
  - vanilla chair / furniture toilet interaction works correctly
  - no CTD observed
- The tested functionality worked before a new Pandora generation, so no missing behavior dependency was observed for the current use case.
- Status: **Validated for the Rhiven natural-needs configuration**.

### NakedStart 1.1.0 — rejected

- Tested `NAKED START - NO ESP NO CRASH 1.1.0` as a possible no-record naked-start solution.
- Correct SKSE plugin structure confirmed.
- Multiple NEFARAM start tests retained the complete randomly assigned outfit / weapon set.
- Config tests with a longer settle window and item-menu shutdown disabled did not change the behavior.
- Likely incompatibility: NEFARAM begins from the supplied `NEFARAM_Start` save and then runs its custom Skyrim Unbound / RaceMenu / teleport sequence, while NakedStart expects a true Skyrim `New Game` event to arm itself.
- Decision: **Rejected / removed from final build**.


### Riverhome

- Installed Riverwood Riverhome SE/AE Port as an additional Eleanor home.
- xEdit review found an invalid deleted override of vanilla cell `0005EAC7` (`aaaMarkers`) in `Riverhome v1.4.esp`.
- Removed only the bad Riverhome override while preserving the actual Riverhome cell.
- Re-ran xEdit `Check for Errors`: **0 errors**.
- In-game validation:
  - exterior integration: **OK**
  - bridge / river placement: **OK**
  - interior: **OK**
  - no obvious terrain break or major visual conflict observed
- No DynDOLOD / xLODGen regeneration performed yet; exterior LOD will be handled during the final generated-output pass.

### Road Signs Overhaul 2.0

- Installed:
  - `Road Signs Overhaul 2.0 - Rhiven`
  - `Road Signs 2.0 - Questionable Clutter Remover (BOS) - Rhiven`
  - `Road Signs Overhaul 2.0 - Blended Roads Patch(BOS) - Rhiven`
- Kept the existing `Skyrim Vanilla Remix Signs` texture stack.
- In-game validation showed readable, correctly placed signs around Riverwood / Whiterun / Falkreath routes.
- No LOD regeneration required at this stage.
- Added a future checklist task for a **Rhiven French texture-only road-sign translation** while preserving the original visual style.

### TK Dodge

- Created dedicated MO2 separator `37.1 - TK Dodge` inside Late Loaders.
- Installed the final TK Dodge stack:
  - `IFrame Generator RE AE Support - Rhiven`
  - `TK Dodge For RE - Rhiven`
  - `TK Dodge RE - Script Free - Rhiven`
  - `TK dodge firstperson 8 ways dodge - Rhiven`
  - `TK Dodge Animation Pandora Fix Patch - Rhiven`
  - `TK Dodge NG - Rhiven`
  - `Dynamic Dodge Animation - Rhiven`
- TK Dodge RE FOMOD:
  - standalone
  - sheathed dodge enabled
  - concentration-spell cancel enabled
  - forward dodge scurry fix enabled
- Dynamic Dodge Animation configured for:
  - `TK Dodge RE-0.55-rc3`
  - `Sway` attack-cancel behavior
- TK Dodge NG initial configuration keeps `StepDodge = false` for rolling dodges.
- Pandora correctly detected:
  - `TK Dodge RE / Ultimate Combat`
  - `TK Dodge Standalone`
- Pandora generation completed successfully with **38,375 total animations added**.
- In-game validation completed successfully:
  - out-of-combat dodge: **OK**
  - combat dodge: **OK**
  - no T-pose / behavior failure observed
- TK Dodge stack marked **Validated**.

### Documentation / repository maintenance

- Added Markdown technical counterparts for easier repository-side consultation:
  - `docs/guides/NEFARAM_Guide_Installation_Creation_Kit_MO2_FR.md`
  - `docs/guides/NEFARAM_Guide_TK_Dodge_FR.md`
  - `docs/guides/NEFARAM_Modding_Guide_1.4_FR.md`
- Kept the original DOCX guides as the richer visual references.
- Updated `docs/13-PRE-PLAYTHROUGH-CHECKLIST.md` with the future French Road Signs texture task.
- Synchronized the current MO2 left/right load-order reference files with the local NEFARAM-Rhiven instance.

## 2026-10-06

### NEFARAM 17.3.7 migration preparation

- NEFARAM 17.3.7 detected as a save-compatible update.
- Chosen strategy: controlled manual migration instead of running Wabbajack over the customized installation.
- Identified the 17.3.7 delta:
  - Inventory Refresh Fix
  - Standing Stealth
  - Meshes Optimization Project
  - SLSF Reloaded LL update
- Confirmed current Core Impact Framework is 1.2.8 while Standing Stealth requires CIF 2.0.3+.
- Target CIF version identified as 2.0.7.
- Target SLSF package currently identified as `SLSF Reloaded 4.1.1.zip`; detailed release-note comparison still pending.
- Meshes Optimization Project held for review pending NEFARAM Discord guidance on FOMOD / overwrite choices.
- Added dedicated migration document: `docs/14-UPDATE-17.3.6-TO-17.3.7.md`.

## 2026-10-05

### Eleanor outfits — final stack

- Finalized the `15.1 - Outfits Eleanor` block with the definitive personal outfit list.
- Added the second outfit batch:
  - ELLE - Delicate Zhuque 3BA
  - COCO Luscious Lady
  - COCO Caress of Venus
  - Nocturne Armor 3BA - SMP
  - Spartan Hoplite Female Version
  - Daggerfall Archmage Outfit Remake 3BA stack, including 1.2 update, NON CS PBR override and hood/cape physics fix
  - Sexy Tsun Armor 3BA ESL
  - Leolic Armor
  - Elf Stalhrim Bikini Armor
  - Dark Dreams + 3BA BodySlide conversion
  - Misc High Heels Stilettos Eins
- Kept Daggerfall's NON CS PBR files below the PBR base/update so they win the intended mesh/material overrides for the ENB setup.
- xEdit `Check for Errors` returned **0 errors** for the newly checked outfit plugins.
- Confirmed `Dark Dreams.esp` requires FormID compacting before ESL flagging; it is intentionally kept as a heavy ESP.
- `Bodyslide Output - Eleanor` remains last in the personal outfit block.

### Pre-playthrough checklist

- Added `docs/13-PRE-PLAYTHROUGH-CHECKLIST.md` as the definitive launch checklist for NEFARAM-Rhiven.
- Split the checklist into **Pre-install / Before New Game**, **Post-install / New Game**, and **Future / Optional backlog**.
- Added the planned outfit keyword / KID audit, translation pass, final MCM session, Lakeview validation, Pandora / generated-output checks and final go/no-go criteria.

## 2026-10-04

### Fertility system / Beeing Female NG

- Kept stock optional `Fertility Mode` disabled.
- Installed `Fertility Adventures Redux - Rhiven`.
- Installed `Beeing Female NG 3.6.0 - Rhiven`.
- Installed a cleaned / repacked `Beeing Female NG - HUD Re-Alignment Patch - Rhiven` containing only:
  - `BeeingFemale/HUD/Align1.ini` through `Align6.ini`
- BFNG FOMOD selections:
  - Open Animation Replacer
  - Fertility Adventures Redux patch
  - SPID item distribution
  - P.A.I.A base patch
  - P.A.I.A Expansion patch
  - SlaveTats womb / birth-count tattoo packs
- Deliberately skipped:
  - FMR-Immersive Effects patch
  - RS Children child actors
  - Creature child actors
  - SkyChild integration
- Confirmed NEFARAM uses `Simple Children`; no child-replacer migration was introduced.
- `Inflation Framework NG` reviewed and placed on Nexus tracking only; not installed unless native BodyMorph coexistence proves insufficient.
- Initial game launch:
  - BFNG 3.6.0 initialized correctly
  - MCM detected
  - SexLab compatibility: OK
  - Bathing in Skyrim compatibility: OK
  - BF items distributed correctly through the selected integration
  - console showed no BFNG blocking error
- Pandora regenerated after BFNG installation:
  - `FNIS_BeeingFemale_List` detected
  - generation completed successfully
  - **38,367 total animations added**
- Re-test after Pandora:
  - `BeeingFemale Animations = COMPATIBLE`
- Intended real-playthrough configuration is documented but **not applied yet**:
  - player pregnancy only
  - NPC pregnancy disabled
  - birth output = Gem
  - BodyMorph profile = CBBE 3BA
  - final HUD / morph amplitudes / fertility probabilities deferred to the global MCM setup after the definitive character start
- Heavy-plugin count at this stage: **211**.
- Added dedicated documentation: `docs/12-FERTILITY-SYSTEM.md`.

### Eleanor home / Lakeview Manor

- Created dedicated MO2 separator `41 - Homes Eleanor`.
- Created temporary holding separator `42 - Added Mods (En attente)`.
- Renumbered the dedicated map block to `43 - FWMF Maps - Rhiven`.
- Installed:
  - `Lakeview. Manor - As It Should Be - Rhiven`
  - `Lakeview Manor - As It Should Be - (CC) Fishing Compatibility Patch - Rhiven`
  - `Lakeview Manor - As It Should Be - FR - Rhiven`
- Lakeview is intentionally isolated from NEFARAM's existing player-home block and related fixes / patches.
- Full in-game validation is **pending** because normal Hearthfire progression is required: Falkreath Jarl progression, plot purchase and manor construction.
- Added dedicated documentation: `docs/11-HOME-ELEANOR.md`.


### User Interface / QoL

- Installed `Compare Equipment NG` v0.3.18 in `04 - User Interface`.
- Kept QuickLoot IE optional / not required for this setup.
- Confirmed the mod is pure SKSE and adds no ESP/plugin.
- In-game validation:
  - comparison cards: **OK**
  - item differences: **OK**
  - armor-type mismatch color warning: **OK**
  - Dragonborn UI compatibility: **OK**
- Compare Equipment NG marked **Validated**.

### Blood architecture

- Kept stock `Just Blood - Dirt and Blood Lite` for actor blood.
- Installed `Enhanced Blood Textures - Rhiven` v4.0 in **SPID Compatible** mode.
- Installed `Enhanced Blood Textures SE - Settings Loader (SPID Version) - Rhiven` v2.0.2.
- Installed `EBT - Just Blood Body Patch - Rhiven` to prevent EBT body-blood overlap with Just Blood.
- Validated the split:
  - **EBT = environment**
  - **Just Blood = actors**

### Bathing in Skyrim Renewed

- Installed `Bathing in Skyrim - Renewed - Rhiven` v2.7.11.
- Installed source scripts and MO2 support files.
- Enabled Base Object Swapper, Description Framework, SkyPatcher and Widget Addon compatibility.
- Selected Zaki SOS / CBBE texture families in the BiSR FOMOD.
- Installed `Bathing in Skyrim - BAIN (Multi-Language) - Rhiven`.
- Confirmed the BAIN package currently provides no French language pack; localized plugin support retained for future translation work.

### BiSR addon stack

- Installed `Zaki 8K-4K Textures for Bathing in Skyrim Renewed - Rhiven`.
- Installed `Bathing in Skyrim - Renewed - Animal Fat and Linen - Rhiven`.
- Installed `Bathing in Skyrim - Generic Soap Distribution - Rhiven`.
- Installed `Bathing in Skyrim - Renewed - Seamless Soap - Rhiven`.
- Installed `Bathing in Skyrim SE - SST MORE VISIBLE BUBBLES - Rhiven`.
- Installed `Bathing in Skyrim - Wash Me - Rhiven` v1.3.
- Wash Me FOMOD:
  - Any follower
  - NSFW
  - Big basin
- Installed original `Widget Addon - Keep It Clean - Bathing in Skyrim - Rhiven` v1.7.2.
- Widget FOMOD set to `None of the above` because NEFARAM uses SunHelm.
- BiSR is loaded after the Widget Addon so its Renewed compatibility patch wins.
- Reviewed Artisan Soaps but did not retain it because Seamless Soap was preferred for the final visual stack.
- Added `Dirtiness Lvl5 Fix for Widget Addon` to Nexus tracking only; not installed unless needed.

### Animations / Pandora

- Moved Malignis Animations to the bottom of `24 - Animations`.
- Corrected Pandora output path from the game Data directory to:
  - `C:\JEUX\NEFARAM\mods\Pandora Output`
- Pandora detected:
  - `FNIS_BiS_WashMe_List`
  - `FNIS_Bathing_in_Skyrim_List`
  - `FNIS_Bathing_in_Skyrim_Malignis_List`
- Pandora generation completed successfully with **38,349 total animations added**.

### Eleanor outfits / BodySlide

- Created dedicated separator `15.1 - Outfits Eleanor`.
- Added the first personal Eleanor outfit batch:
  - Invicta Couture Black Rose
  - Silver Witch
  - DX Fetish Fashion Volume II
  - Invicta Couture Lingerie
  - Chain Bikini Armor
  - Dark Rebel
  - Aradia Bikini
  - Aether
  - Lady Ritual
  - Bisquits Priestess of Mara
  - Forgotten Princess
  - COCO 2B Wedding Outfit
  - MME Milk Harness v3
- Kept required BHUNP source packages for the Invicta conversions while using their CBBE 3BA conversions for Eleanor.
- Created dedicated generated-output mod `Bodyslide Output - Eleanor`.
- Corrected BodySlide output path to:
  - `C:\JEUX\NEFARAM\mods\Bodyslide Output - Eleanor`
- Used `- Zeroed Sliders -` to preserve OBody NG morph handling.
- Generated the full added-outfit BodySlide batch.
- Selected CBBE 3BA **Complex Material (CM)** variants for MME Milk Harness v3 instead of PBR.
- Confirmed the newly added outfit plugins are already ESL-flagged / ESP-FE.
- Adopted a plugin-order convention that keeps personal additions together before FWMF while preserving the technical late-loader / generated-plugin structure.
- Added dedicated documentation: `docs/10-OUTFITS-ELEANOR.md`.
- In-game visual / physics validation of the outfit batch remains pending.

### Validation

- Game launch: **OK**
- New BiSR MCM/options: **OK**
- Blood options / MCM: **OK**
- Animations: **OK**
- No blocking animation or compatibility issue observed.
- Blood + hygiene stack marked **Validated**.
- Heavy-plugin count after the stack: **203**.
- Added dedicated documentation: `docs/09-SURVIVAL-BLOOD-HYGIENE.md`.

## 2026-10-03

### Baseline

- Installed and validated NEFARAM 17.3.6.
- Created MO2 profile `ELEANOR Stable`.
- Numbered MO2 separators.
- Adopted `- Rhiven` suffix for personal additions.

### Terrain Helper

- Isolated generated `TerrainHelper.ini` from MO2 Overwrite.
- Created `Terrain Helper - Generated INI - Rhiven`.

### Dragonborn UI

- Installed `Dragonborn UI - SkyUI Reskin - Rhiven`.
- Kept the existing NEFARAM UI stack active.
- Selected Knotwork-compatible system menu.
- Enabled Sovngarde Font.
- Enabled More Informative Console patch.
- Initial conflict review showed primarily expected UI/visual overwrites.
- In-game validation completed successfully.
- Dragonborn UI marked **Validated**.
- Identified the remaining unskinned window as Skyrim Character Sheet.
- Installed `Dragonborn Reskin - Skyrim Character Sheet - Rhiven`.
- Character Sheet reskin validated successfully in-game.

### Wheeler / Perfected Wheeler

- Restored Wheeler functionality using the modern Perfected Wheeler branch.
- Installed `Wheeler - Quick Action Wheel Of Skyrim - Rhiven`.
- Installed `Perfected Wheeler - Apocrypha Menu Framework - Rhiven`.
- Reused NEFARAM's existing `SKSE Menu Framework` as the supported configuration framework.
- Did **not** reinstall the legacy `dMenu` / `dMenu NG` chain.
- Installed `Dragonborn - Wheeler Reskin - Rhiven`.
- Installed `Dragonborn - Wheeler Reskin Edge UI Color Options - Rhiven`.
- Confirmed Perfected Wheeler appears in the SKSE Mod Control Panel.
- Confirmed Wheeler opens correctly in-game.
- Confirmed resize / layout settings work correctly.
- Initial test used the default `Caps Lock` binding; final Rhiven keymap will be rebuilt before the real playthrough.
- Confirmed the four Wheeler mods add no ESP/plugin.
- Wheeler stack marked **Validated**.

### FWMF / Paper Map

- Created MO2 separator `43 - FWMF Maps - Rhiven` (renumbered from the original personal `42` separator after adding Eleanor's home block).
- Installed `Flat World Map Framework FOMOD Lite - Rhiven` v1.9.990.
- Selected Flat Map Markers AE Updated for Skyrim 1.6.629–1.7.99.
- Selected Skyrim-only map whitelist for the initial setup.
- Enabled Water for ENB support.
- Enabled EVLaS patch.
- Enabled Lux patch.
- Enabled Seasons of Skyrim support for Skyrim.
- Installed the integrated FWMF MCM.
- Installed `Skyrim Paper Map by Caro Tuts for FWMF - Rhiven`.
- Confirmed that the Caro Tuts map itself adds no ESP.
- FWMF plugins installed at the bottom of the plugin order.
- In-game validation completed successfully with no purple map or missing-texture issue.
- FWMF + Caro Tuts marked **Validated**.

### Repository

- Created initial NEFARAM-Rhiven documentation structure.
