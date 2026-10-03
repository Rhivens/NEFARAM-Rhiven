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

## Planned / candidates

No Wheeler-related legacy dependency is currently planned. The older `dMenu + dMenu NG + Wheeler Refined` stack was intentionally not restored because Perfected Wheeler works correctly with the SKSE Menu Framework already included in NEFARAM 17.3.6.
