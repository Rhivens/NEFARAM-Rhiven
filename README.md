# NEFARAM - Rhiven

Personal customization, maintenance notes and technical documentation for **NEFARAM 17.3.8**.

This repository keeps a clean and reproducible record of every change made to the stock NEFARAM installation: added or removed mods, patches, fixes, translations, UI work, load orders, generated outputs and testing notes.

## Current baseline

- **NEFARAM:** 17.3.8
- **MO2 profile:** `Eleanor Stable 17.3.8`
- Stock installation validated before customization
- Definitive playthrough starts from the supplied **NEFARAM_Start** save
- Personal additions use the suffix **`- Rhiven`**
- MO2 separators are numbered for easier navigation

## Documentation convention

- `Docs/01` through `Docs/11`, together with `Docs/VALIDATION`, form the **internal Rhiven workshop and reference**: technical research, integration notes, xEdit reasoning, patch records and testing. The repository remains public and readable, but these files are not simplified end-user guides.
- `Docs/12 - COMMUNITY GUIDES` contains the **simplified and validated guides intended for the NEFARAM community**.

Start with the [Docs index](Docs/README.md).

## Repository structure

### Internal workshop and reference

- [01 - CORE](Docs/01%20-%20CORE/)
  - [Baseline](Docs/01%20-%20CORE/01-BASELINE.md)
  - [MO2 conventions](Docs/01%20-%20CORE/02-MO2-CONVENTIONS.md)
  - [Mods added](Docs/01%20-%20CORE/03-MODS-ADDED.md)
  - [Mods removed or disabled](Docs/01%20-%20CORE/04-MODS-REMOVED.md)
- [02 - UPDATES & MIGRATIONS](Docs/02%20-%20UPDATES%20&%20MIGRATIONS/)
  - [Update 17.3.6 to 17.3.7](Docs/02%20-%20UPDATES%20&%20MIGRATIONS/14-UPDATE-17.3.6-TO-17.3.7.md)
  - [Update 17.3.7 to 17.3.8](Docs/02%20-%20UPDATES%20&%20MIGRATIONS/15-UPDATE-17.3.7-TO-17.3.8.md)
- [03 - PATCHES FIXES](Docs/03%20-%20PATCHES%20FIXES/PATCHES-FIXES.md)
- [04 - ANIMATIONS](Docs/04%20-%20ANIMATIONS/README.md)
- [05 - UI-HUD](Docs/05%20-%20UI-HUD/)
  - [UI](Docs/05%20-%20UI-HUD/DRAGONBORN-UI.md)
  - [Vel'Dun](Docs/05%20-%20UI-HUD/VEL'DUN.md)
- [06 - GAMEPLAY](Docs/06%20-%20GAMEPLAY/)
  - [Survival, blood and hygiene](Docs/06%20-%20GAMEPLAY/BATHING%20IN%20SKYRIM/09-SURVIVAL-BLOOD-HYGIENE.md)
  - [Fertility system](Docs/06%20-%20GAMEPLAY/BEEING%20FEMALE%20NG/12-FERTILITY-SYSTEM.md)
  - [Animal Mansion Reborn integration](Docs/06%20-%20GAMEPLAY/ANIMAL%20MANSION%20REBORN/ANIMAL-MANSION-INTEGRATION.md)
  - [Naked Defeat integration](Docs/06%20-%20GAMEPLAY/NAKED%20DEFEAT/NAKED-DEFEAT-INTEGRATION.md)
- [07 - HOMES](Docs/07%20-%20HOMES/LAKEVIEW-MANOR-AS-IT-SHOULD-BE.md)
- [08 - OUTFITS](Docs/08%20-%20OUTFITS/10-OUTFITS-ELEANOR.md)
- [09 - VISUALS](Docs/09%20-%20VISUALS/)
- [10 - TRANSLATIONS](Docs/10%20-%20TRANSLATIONS/)
  - [French translations](Docs/10%20-%20TRANSLATIONS/07-TRANSLATIONS-FR.md)
  - [Skyrim FR field safety](Docs/10%20-%20TRANSLATIONS/SKYRIM-FR-FIELD-SAFETY.md)
- [11 - TOOLS](Docs/11%20-%20TOOLS/)
- [VALIDATION](Docs/VALIDATION/)
  - [Testing and validation](Docs/VALIDATION/08-TESTING.md)
  - [Pre-playthrough checklist](Docs/VALIDATION/13-PRE-PLAYTHROUGH-CHECKLIST.md)
- [Finalization roadmap](ROADMAP.md)

### Community guides

- [12 - COMMUNITY GUIDES](Docs/12%20-%20COMMUNITY%20GUIDES/)
  - [Animal Mansion Reborn](Docs/12%20-%20COMMUNITY%20GUIDES/ANIMAL-MANSION-REBORN/ANIMAL-MANSION-NEFARAM-17.3.8-COMMUNITY-GUIDE.md)
  - [Bathing in Skyrim](Docs/12%20-%20COMMUNITY%20GUIDES/BATHING-IN-SKYRIM/BATHING-IN-SKYRIM-NEFARAM-17.3.8-COMMUNITY-GUIDE.md)
  - [Lakeview Manor - As It Should Be](Docs/12%20-%20COMMUNITY%20GUIDES/LAKEVIEW-MANOR-AS-IT-SHOULD-BE/README.md)
  - [Naked Defeat](Docs/12%20-%20COMMUNITY%20GUIDES/NAKED-DEFEAT/README.md)
  - [PAMA Prison System — English](Docs/12%20-%20COMMUNITY%20GUIDES/PAMA-Prison-System/README-EN.md) / [French](Docs/12%20-%20COMMUNITY%20GUIDES/PAMA-Prison-System/README-FR.md)
  - [NEFARAM Modding Guide](Docs/12%20-%20COMMUNITY%20GUIDES/NEFARAM-MODDING-GUIDE-by-SkinnyPete/NEFARAM_Modding_Guide_1.4_FR.md)

### Load-order snapshots

- [Load-order index](Load-Order/README.md)
- [Original NEFARAM — MO2 left pane](Load-Order/NEFARAM-ORIGINAL-MO2-LEFT.md)
- [Original NEFARAM — MO2 right pane / plugins](Load-Order/NEFARAM-ORIGINAL-MO2-RIGHT.md)
- [Rhiven modded — MO2 left pane](Load-Order/NEFARAM-RHIVEN-MODDED-MO2-LEFT.md)
- [Rhiven modded — MO2 right pane / plugins](Load-Order/NEFARAM-RHIVEN-MODDED-MO2-RIGHT.md)

### History

- [Changelog](CHANGELOG.md)
- [Mods not retained](Docs/MODS-NOT-RETAINED.md)

## Working principle

The stock NEFARAM installation remains the reference. Personal changes are isolated whenever possible, documented, and tested by logical blocks before the definitive playthrough begins.

This repository documents configuration and personal work only. Original mods remain the property of their respective authors.
