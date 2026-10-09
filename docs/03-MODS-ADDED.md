# 03 - Added mods

This file tracks mods added on top of the stock NEFARAM 17.3.7 installation.

## Status legend

- **Installed** — present and enabled
- **Testing** — installed but not yet fully validated
- **Validated** — tested and kept
- **Planned** — candidate for later installation
- **Rejected** — tested or reviewed and not retained

## Added mods

| Mod | Status | Section | Reason / Notes |
|---|---|---|---|
| Terrain Helper - Generated INI - Rhiven | Validated | 02 - SKSE Utility Mods | Isolates generated `TerrainHelper.ini` from MO2 Overwrite |
| Dragonborn UI - SkyUI Reskin - Rhiven | Validated | 04 - User Interface | UI reskin validated in-game; existing NEFARAM UI stack kept active |
| Dragonborn Reskin - Skyrim Character Sheet - Rhiven | Validated | 04 - User Interface | Dragonborn-style reskin for the existing Skyrim Character Sheet; validated in-game |
| Wheeler - Quick Action Wheel Of Skyrim - Rhiven | Validated | 04 - User Interface | Base Wheeler assets / quick action wheel; required by Perfected Wheeler |
| Perfected Wheeler - Apocrypha Menu Framework - Rhiven | Validated | 04 - User Interface | Modern Wheeler implementation using the existing NEFARAM SKSE Menu Framework; no dMenu / dMenu NG needed |
| Dragonborn - Wheeler Reskin - Rhiven | Validated | 04 - User Interface | Dragonborn-style Wheeler appearance; validated in-game |
| Dragonborn - Wheeler Reskin Edge UI Color Options - Rhiven | Validated | 04 - User Interface | Optional Edge UI color scheme loaded after the main Wheeler reskin |
| Compare Equipment NG 0.3.18 | Validated | 04 - User Interface | Pure SKSE QoL mod; comparison cards, difference indicators and armor-type warning tested successfully; no ESP/plugin |
| Flat World Map Framework FOMOD Lite - Rhiven | Validated | 43 - FWMF Maps - Rhiven | FWMF 1.9.990 base framework; installed with Skyrim map support and current NEFARAM compatibility patches |
| Skyrim Paper Map by Caro Tuts for FWMF - Rhiven | Validated | 43 - FWMF Maps - Rhiven | Paper map assets for Skyrim; no ESP added; validated in-game |
| Enhanced Blood Textures - Rhiven | Validated | 30 - Character Visual | EBT 4.0 installed in SPID mode; used for environmental blood visuals |
| Enhanced Blood Textures SE - Settings Loader (SPID Version) - Rhiven | Validated | 30 - Character Visual | Settings Loader matched to the EBT SPID install |
| EBT - Just Blood Body Patch - Rhiven | Validated | 30 - Character Visual | Disables EBT body blood decals so Just Blood remains responsible for actor blood |
| Bathing in Skyrim - Renewed - Rhiven | Validated | 21 - Survival | BiSR 2.7.11; core hygiene / bathing system |
| Bathing in Skyrim - BAIN (Multi-Language) - Rhiven | Validated | 21 - Survival | Localization-friendly BiSR package; no French included in current package |
| Zaki 8K-4K Textures for Bathing in Skyrim Renewed - Rhiven | Validated | 21 - Survival | High-resolution dirt overlays; female level 4 selected, male textures omitted |
| Bathing in Skyrim - Renewed - Animal Fat and Linen - Rhiven | Validated | 21 - Survival | Crafting / washing resources for the BiSR stack |
| Bathing in Skyrim - Generic Soap Distribution - Rhiven | Validated | 21 - Survival | Distributes soap / wash-rag items |
| Bathing in Skyrim - Renewed - Seamless Soap - Rhiven | Validated | 21 - Survival | Renewed-specific seamless soap visual effect |
| Bathing in Skyrim SE - SST MORE VISIBLE BUBBLES - Rhiven | Validated | 21 - Survival | Optional more-visible bubble effect for Seamless Soap |
| Bathing in Skyrim - Wash Me - Rhiven | Validated | 21 - Survival | Wash Me Renewed 1.3; Any follower / NSFW / Big basin |
| Widget Addon - Keep It Clean - Bathing in Skyrim - Rhiven | Validated | 21 - Survival | Original widget addon 1.7.2, patched by BiSR for Renewed compatibility |
| Malignis Animations - Bathing in Skyrim Renewed - Rhiven | Validated | 24 - Animations | BiSR bathing animations; placed at the bottom of the animation block |
| Invicta Couture Black Rose BHUNPv4 Extra 2K - Rhiven | Installed | 15.1 - Outfits Eleanor | Original asset / texture package for the 3BA conversion |
| Invicta Couture Black Rose CBBE 3BA - Rhiven | Installed | 15.1 - Outfits Eleanor | CBBE 3BA conversion; BodySlide generated |
| [qdaro] Silver Witch 3BA SMP - Rhiven | Installed | 15.1 - Outfits Eleanor | 3BA SMP outfit; BodySlide generated |
| DX Fetish Fashion Volume 2 SE - CBBE Physics 3BA - Rhiven | Installed | 15.1 - Outfits Eleanor | 3BA outfit; BodySlide generated |
| Invicta Couture Lingerie BHUNP SMP - Rhiven | Installed | 15.1 - Outfits Eleanor | Original asset / texture package for the 3BA conversion |
| Invicta Couture Lingerie CBBE 3BA - Rhiven | Installed | 15.1 - Outfits Eleanor | CBBE 3BA conversion; BodySlide generated |
| Chain Bikini Armor - CBBE 3BA - Rhiven | Installed | 15.1 - Outfits Eleanor | CBBE 3BA outfit; BodySlide generated |
| ELLE - Dark Rebel 3BA - Rhiven | Installed | 15.1 - Outfits Eleanor | 3BA outfit; BodySlide generated |
| Minou Aradia Bikini SE 3BAv2 - Rhiven | Installed | 15.1 - Outfits Eleanor | 3BAv2 outfit; BodySlide generated |
| Aether CBBE 3BA - Rhiven | Installed | 15.1 - Outfits Eleanor | CBBE 3BA outfit; BodySlide generated |
| Lady Ritual CBBE 3BA - Rhiven | Installed | 15.1 - Outfits Eleanor | CBBE 3BA outfit; BodySlide generated |
| Bisquits Priestess of Mara - Rhiven | Installed | 15.1 - Outfits Eleanor | Outfit added to Eleanor wardrobe block; BodySlide generated where applicable |
| Forgotten Princess - CBBE 3BA - Rhiven | Installed | 15.1 - Outfits Eleanor | CBBE 3BA outfit; BodySlide generated |
| COCO 2B Wedding Outfit - CBBE 3BA - Rhiven | Installed | 15.1 - Outfits Eleanor | CBBE 3BA outfit; BodySlide generated |
| [Predator] MME Milk Harness v3 - Rhiven | Installed | 15.1 - Outfits Eleanor | CBBE 3BA Complex Material variants selected; BodySlide generated |
| Bodyslide Output - Eleanor | Installed | 15.1 - Outfits Eleanor | Dedicated generated-mesh output for personal outfit additions |
| Lakeview. Manor - As It Should Be - Rhiven | Installed | 41 - Homes Eleanor | Eleanor's future Lakeview Manor overhaul; full gameplay validation pending access to the Hearthfire property |
| Lakeview Manor - As It Should Be - (CC) Fishing Compatibility Patch - Rhiven | Installed | 41 - Homes Eleanor | Compatibility patch for Creation Club Fishing content |
| Lakeview Manor - As It Should Be - FR - Rhiven | Installed | 41 - Homes Eleanor | French translation layer for the Lakeview Manor overhaul |
| Fertility Adventures Redux - Rhiven | Testing | 42 - Fertility System | Narrative pregnancy / partner reaction layer; installed before BFNG so the BFNG FOMOD integration can detect and patch it |
| Beeing Female NG 3.6.0 - Rhiven | Testing | 42 - Fertility System | Preferred fertility / pregnancy framework replacing the optional stock Fertility Mode; technical initialization and Pandora compatibility validated |
| Beeing Female NG - HUD Re-Alignment Patch - Rhiven | Testing | 42 - Fertility System | Repacked preset-only addon adding Align1-Align6 INI layouts under BeeingFemale/HUD; structural compatibility with BFNG 3.6.0 verified, final in-game placement pending |

| SkyPatcher - AE - Rhiven | Installed | 43 - Added Mods SFW | Runtime patching / distribution framework added for modern mod integrations; used by OMNOMS for Banish Mimic scroll distribution |
| Object Impact Framework (OIF) - Rhiven | Installed | 43 - Added Mods SFW | SKSE framework required by O.S.H.I.T.; installed as the framework only, without the optional Cut Food config |
| Trap Needs to be Real Trap - Rhiven | Testing | 44 - Added Mods NSFW | TNTR 0.74 base; Replacer + New Baka Traps + OAR patch + Nemesis-style behavior patch selected for Pandora-compatible generation |
| EET Extra Evil Traps - Rhiven | Testing | 44 - Added Mods NSFW | Extra Evil Traps 1.2.3; Bear Trap and Snare Trap patches selected for TNTR 0.73/0.74 |
| O Skyrim Has Insane Traps - Rhiven | Testing | 44 - Added Mods NSFW | O.S.H.I.T trap-placement / impact layer; requires OIF |
| OMNOMS Not So Obvious Mimics - Rhiven | Testing | 44 - Added Mods NSFW | OMNOMS 1.3.0; patched Mimic script, hidden activation text, SkyPatcher distribution via Magic Vendors + Spell Tomes, O.S.H.I.T compatibility patch enabled |
| Deadly Bear Trap - Rhiven | Testing | 44 - Added Mods NSFW | Additional bear-trap placement layer used with the TNTR/EET ecosystem |
| Watch Your Step - Rhiven | Testing | 44 - Added Mods NSFW | v1.2 main file for TNTR >0.46 / ESP-FE references; old O.S.H.I.T v0.4-only optional file intentionally skipped |

| Outfit Gallery - Visual Outfit Manager - Rhiven | Validated | 43 - Added Mods SFW | SKSE-based visual wardrobe manager for Eleanor; F8 opens the gallery and F9 captures the current outfit; initial in-game UI test successful |
| Regional Outfitters - Stalls of Skyrim - Rhiven | Validated | 43 - Added Mods SFW | SkyPatcher-driven themed armor/gear merchants; installed with Capital Windhelm, Obscure's College of Winterhold and AI Overhaul patches; multiple-city coc validation completed without CTD or obvious placement issue |

| Private Needs - Orgasm 1.11.1 - Rhiven | Validated | 44 - Added Mods NSFW | Updated from previously used 1.8.3; used only for bladder/bowel needs, orgasm-related features disabled; initial in-game test confirmed bladder/bowel percentages and chair/toilet furniture interaction |

## Reviewed but not retained

| Mod | Status | Reason |
|---|---|---|
| Artisan Soaps for Bathing in Skyrim Renewed | Rejected | Visual overlap with the selected Seamless Soap stack; simpler setup preferred |
| Dirtiness Lvl5 Fix for Widget Addon - Bathing In Skyrim Renewed | Planned | Tracked on Nexus but not installed; only needed if the widget disappears at dirtiness level 5 |
| Inflation Framework NG | Planned | Tracked on Nexus only; reserve option if BFNG / FHU / MME BodyMorph coexistence cannot be tuned cleanly through their native MCM settings |
| NAKED START - NO ESP NO CRASH 1.1.0 | Rejected | Does not trigger with NEFARAM's supplied-start-save / Skyrim Unbound workflow; repeated tests kept the complete randomly assigned starting equipment despite timing/config changes |

## Planned / candidates

No Wheeler-related legacy dependency is currently planned. The older `dMenu + dMenu NG + Wheeler Refined` stack was intentionally not restored because Perfected Wheeler works correctly with the SKSE Menu Framework already included in NEFARAM 17.3.7.

The dirtiness level 5 widget fix remains a conditional candidate only.

`Inflation Framework NG` is also tracked only. The first real-playthrough tests will use native BodyMorph handling in BFNG, Fill Her Up and Milk Mod Economy; the framework will be reconsidered only if a reproducible morph-coexistence problem appears.


## PAMA / Prison Alternative block — 2026-10-08

Dedicated MO2 separator: `44 - PRISON PAMA SYSTEM`.

| Mod / Patch | Status | Notes |
|---|---|---|
| Next-Gen Decapitations | Validated for PAMA integration | Installed in SFW additions; foundation for the current PAMA setup |
| Next-Gen Decapitations - Sovngarde INI - Rhiven | Validated | Dedicated INI override: `iCanBeResurrected = 2`, `bAdvancedNPCMaintenance = 0` |
| PamaDeadlyFurniture 3.4.5 Revision 2 - Rhiven | Validated | Core furniture flow tested successfully in `pamaTestZone` |
| Prison Alternative 2.0.3 - Rhiven | Validated | SE/AE + ZaZ-compatible install; Whiterun arrest / jail / cot / sentence progression validated |
| Prison Alternative - Scripts Sources - Rhiven | Support / Disabled | Papyrus sources kept separately for inspection or future edits; disabled for normal play |
| Pama Sovngarde Aftermath 1.0.0 - Rhiven | Validated for integration | Handoff from PAMA validated; full return scenario intentionally deferred |
| Prison Alternative - Punishment Pack 1.3.0 - Rhiven | Validated for integration | Installed cleanly; Pandora +16 animations |
| Prison Alternative - Outdoor Event Pack 1.3 - Rhiven | Validated for integration | Installed cleanly; no additional Pandora animations |
| Bad Ends Revived: Windhelm 1.3.0 - Rhiven | Validated with patches | Pandora +22; Rhiven navmesh + ZaZ compatibility patches retained |
| PAMA - Windhelm Navmesh Patch - Rhiven | xEdit Validated | ESL-flagged compatibility patch for navmeshes `000FC117` and `0004B66C`; 0 xEdit errors |
| PAMA - NEFARAM ZaZ Ankle Chains Patch - Rhiven | Structural Fix | Reapplies NEFARAM's `ZaZAnkleChainsRagdolls_1.nif` after Bad Ends Windhelm |
| Bad Ends Revived: Riften 1.3.2 - Rhiven | Validated for integration | Pandora +30; targeted xEdit audit found no navmesh patch requirement; minor visual well overlap deferred to real playthrough |
| Bad Ends Revived: Solitude 1.8.0 Revision 2 - Rhiven | Validated with patch | Pandora +46; targeted xEdit / in-game pathing checks completed |
| PAMA - Solitude Location Patch - Rhiven | xEdit Validated | ESL-flagged patch restoring `SolitudeLocation` on `SolitudeOrigin [00037EE9]`; 0 xEdit errors |
| Orkish Bounty Hunters 0.4 - Rhiven | Validated for integration | Ambush, scripted KO, jail, camp, escape and recapture paths tested; one isolated CTD was not reproduced |

Current Pandora total after the complete PAMA block: **39,298 animations**.

The full planned PAMA core is now installed. Remaining work is limited to long-term / real-playthrough observation and the intentionally deferred complete Sovngarde return test.

## Missives / SL Dirty Deeds — 2026-10-08

MO2 location: `46 - Added Mods NSFW` (left pane); order retained as listed below. French translation is intentionally deferred until the modpack is fully installed and stable.

| Mod / Patch | Status | Notes |
|---|---|---|
| Missives 2.03 SSE - Rhiven | Testing | Nexus base kept enabled under the replacement in MO2; its shared `Missives.esp` / BSA / MCM files are overridden by the higher-priority replacement |
| Replacing Boards for Missives - Rhiven | Testing | Standalone replacement v2.12 (RU_EN); overwrites `Missives.esp`, `Missives.bsa` and MCM config; HD themed boards, additional locations and integrated Solstheim support; Whiterun board visual placement and interaction verified in-game |
| SL Dirty Deeds Missives - Rhiven | Testing | v1.4.2; `SL Dirty Deeds Missives.esp` plus `SL Dirty Deeds Missives - 1.4.2 - Race Edits.esp`; 15+ repeatable SexLab contracts; notes seen on Whiterun board; actual quest/scene completion left for real playthrough |
| SL Dirty Deeds - Race Compatibility - Rhiven | xEdit Validated | ESL-flagged patch `SL Dirty Deeds - Race Compatibility - Rhiven.esp` overrides WolfRace `0001320A`: restores male height `1.000000` from Synthesis / MoreNastyCritters while retaining `Allow PC Dialogue`; xEdit Check for Errors: 0 errors / 2 records |

Race Edits review with full load order: FalmerRace, GiantRace, TrollRace and TrollFrostRace retained their relevant prior values and added `Allow PC Dialogue`; WolfRace required the targeted height compatibility patch. All three mod plugins separately passed initial xEdit Check for Errors (Missives: 2,399 records; Dirty Deeds: 340; Race Edits: 6; 0 errors each).

In-game checkpoint: Missives MCM General / Rewards opened; Whiterun board visible and accessible without obvious clipping; Dirty Deeds notes visible in board inventory. Not yet tested: accepting/completing a Dirty Deeds mission, SexLab scene triggering/rewards, repeatability, and checks at additional board locations. No translation work performed.

## Simple Offence Suppression MCM — 2026-10-09

| Mod | Status | MO2 location | Validation / Notes |
|---|---|---|---|
| Simple Offence Suppression MCM - Rhiven | Testing — MCM validated | Block `22`, directly below stock `Simple Offence Suppression` | MCM addon v0.6 for the existing stock SKSE/DLL-only mod; no MO2 file conflicts observed; `Simple Offence Suppression MCM.esp` ESL-flagged, observed priority 1950 / FE:C67. In-game MCM opened with new stealth / out-of-combat friendly-fire options. Existing `SKSE Output/po3_SimpleOffenceSuppression.ini` retained the same settings before and after the test; genuine combat friendly-fire behavior not tested yet. |

## Fitting Room / Menu Studio / FLICK — 2026-10-09

MO2: `43 - Added Mods SFW`. This is a **trial installation**. Keep `Outfit Gallery - Visual Outfit Manager - Rhiven` installed but disabled during this comparison; the final wardrobe tool decision is deferred to the definitive playthrough preparation.

| Mod | Status | Notes |
|---|---|---|
| FLICK - Fuzz's Legally Intelligible Core Kit - Rhiven | Testing — UI initialized | FLICK NG framework; no MO2 file conflicts observed, and its settings sidebar hosts Fitting Room and Menu Studio |
| Menu Studio - Rhiven | Testing — visual integration observed | v1.2.0; no ESP / no MO2 file conflicts observed. FOMOD: `The dressing room` + `The star dome`. Player shown in the star-themed menu environment using existing `Show Player In Menus` + Persistent Zoom Fix; no replacement of the existing SkyUI 5.2 / Dragonborn UI stack |
| Fitting Room - Rhiven | Testing — initial outfit preview validated | v1.2.0; FOMOD: `Freeform`, `Leave my face alone`, `All dyes unlocked`. FLICK settings registered and editor opens with `N` **from the inventory**. Outfit/plugin browser detects installed outfit sets including Aether; live preview on Eleanor and Menu Studio star background observed. `FittingRoom.ini` contains `iEditorKeyDIK=49` (N), `iDirectEntryKeyDIK=0` (no in-world shortcut), `bLooksRaceMenu=false` and `bReassertAppearance=false`. Appearance/transmog does not grant actual inventory items. Scene compatibility option enabled but SexLab/DD behavior untested. |
| Outfit Gallery - Visual Outfit Manager - Rhiven (existing) | Installed — temporarily disabled for comparison | Retained in MO2; final choice between Outfit Gallery (wardrobe tool), Fitting Room (visual transmog), or coexistence remains undecided. Do not remove either until decision at playthrough start. |

Optional future cosmetic project: custom `Eleanor's Dressing Room` environment/backdrop for Menu Studio. Keep separate from build completion.
