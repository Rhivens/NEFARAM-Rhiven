# 03 - Added mods

This file tracks mods added on top of the stock NEFARAM 17.3.6 installation.

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

## Reviewed but not retained

| Mod | Status | Reason |
|---|---|---|
| Artisan Soaps for Bathing in Skyrim Renewed | Rejected | Visual overlap with the selected Seamless Soap stack; simpler setup preferred |
| Dirtiness Lvl5 Fix for Widget Addon - Bathing In Skyrim Renewed | Planned | Tracked on Nexus but not installed; only needed if the widget disappears at dirtiness level 5 |
| Inflation Framework NG | Planned | Tracked on Nexus only; reserve option if BFNG / FHU / MME BodyMorph coexistence cannot be tuned cleanly through their native MCM settings |

## Planned / candidates

No Wheeler-related legacy dependency is currently planned. The older `dMenu + dMenu NG + Wheeler Refined` stack was intentionally not restored because Perfected Wheeler works correctly with the SKSE Menu Framework already included in NEFARAM 17.3.6.

The dirtiness level 5 widget fix remains a conditional candidate only.

`Inflation Framework NG` is also tracked only. The first real-playthrough tests will use native BodyMorph handling in BFNG, Fill Her Up and Milk Mod Economy; the framework will be reconsidered only if a reproducible morph-coexistence problem appears.
