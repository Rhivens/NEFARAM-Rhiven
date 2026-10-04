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
| Flat World Map Framework FOMOD Lite - Rhiven | Validated | 42 - FWMF Maps - Rhiven | FWMF 1.9.990 base framework; installed with Skyrim map support and current NEFARAM compatibility patches |
| Skyrim Paper Map by Caro Tuts for FWMF - Rhiven | Validated | 42 - FWMF Maps - Rhiven | Paper map assets for Skyrim; no ESP added; validated in-game |
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

## Reviewed but not retained

| Mod | Status | Reason |
|---|---|---|
| Artisan Soaps for Bathing in Skyrim Renewed | Rejected | Visual overlap with the selected Seamless Soap stack; simpler setup preferred |
| Dirtiness Lvl5 Fix for Widget Addon - Bathing In Skyrim Renewed | Planned | Tracked on Nexus but not installed; only needed if the widget disappears at dirtiness level 5 |

## Planned / candidates

No Wheeler-related legacy dependency is currently planned. The older `dMenu + dMenu NG + Wheeler Refined` stack was intentionally not restored because Perfected Wheeler works correctly with the SKSE Menu Framework already included in NEFARAM 17.3.6.

The dirtiness level 5 widget fix remains a conditional candidate only.
