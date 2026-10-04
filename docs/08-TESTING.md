# 08 - Testing & validation

This file records important validation steps before the real playthrough.

## Baseline validation

### Stock NEFARAM 17.3.6

- MO2 launch: **OK**
- Game launch: **OK**
- `NEFARAM_Start` save: **OK**
- Waiting room / configuration screen: **OK**
- Clean exit without creating a gameplay save: **OK**

## Current tests

### Dragonborn UI

Status: **VALIDATED**

- In-game test: **OK**
- Core menus and UI: **OK**
- Existing NEFARAM UI stack: **functional**
- Dragonborn UI visual overrides: **OK**
- No blocking compatibility issue observed
- Safe to keep enabled in `ELEANOR Stable`

### Dragonborn Reskin - Skyrim Character Sheet

Status: **VALIDATED**

- In-game test: **OK**
- Character Sheet opens normally: **OK**
- Dragonborn visual style applied correctly: **OK**
- No visible layout or text issue observed
- Safe to keep enabled in `ELEANOR Stable`

### Wheeler / Perfected Wheeler

Status: **VALIDATED**

Installed stack:

- `Wheeler - Quick Action Wheel Of Skyrim - Rhiven`
- `Perfected Wheeler - Apocrypha Menu Framework - Rhiven`
- `Dragonborn - Wheeler Reskin - Rhiven`
- `Dragonborn - Wheeler Reskin Edge UI Color Options - Rhiven`

Validation:

- In-game launch: **OK**
- Wheeler opens correctly: **OK**
- Perfected Wheeler detected in SKSE Menu Framework: **OK**
- Settings panel / Mod Control Panel: **OK**
- Resize / wheel layout controls: **OK**
- Dragonborn reskin: **OK**
- Edge UI color option: **OK**
- Test binding on `Caps Lock`: **OK**
- No ESP/plugin added by the four Wheeler mods
- Final hotkey layout intentionally deferred until the real playthrough setup
- Decision: keep enabled in `ELEANOR Stable`

### Compare Equipment NG 0.3.18

Status: **VALIDATED**

- Installed in `04 - User Interface` after the Dragonborn / Wheeler reskin block
- Pure SKSE implementation: **no ESP/plugin**
- Equipment comparison windows: **OK**
- Difference indicators: **OK**
- Armor-type mismatch color warning: **OK**
- Dragonborn UI compatibility during test: **OK**
- Decision: keep enabled in `ELEANOR Stable`

### FWMF + Skyrim Paper Map by Caro Tuts

Status: **VALIDATED**

- FWMF base: `Flat World Map Framework FOMOD Lite - Rhiven` v1.9.990
- Map: `Skyrim Paper Map by Caro Tuts for FWMF - Rhiven`
- MO2 section: `43 - FWMF Maps - Rhiven`
- In-game map test: **OK**
- Paper map rendering: **OK**
- No purple map / missing texture issue observed
- Map markers and map behavior: **OK**
- Caro Tuts map adds no ESP
- FWMF plugins remain at the bottom of the plugin order, after the late NEFARAM / LOD stack
- Safe to keep enabled in `ELEANOR Stable`

### Blood + Bathing in Skyrim Renewed stack

Status: **VALIDATED**

Core design:

- EBT = environment
- Just Blood = actors
- BiSR = hygiene
- SunHelm = needs
- Campfire = camping

Validation:

- Enhanced Blood Textures 4.0 SPID: **OK**
- EBT Settings Loader SPID: **OK**
- Just Blood retained: **OK**
- EBT / Just Blood body patch: **OK**
- Bathing in Skyrim Renewed 2.7.11 MCM detected: **OK**
- Blood-related MCM/options detected: **OK**
- BiSR addon stack detected: **OK**
- Widget Addon detected and patched by BiSR: **OK**
- Malignis animations: **OK**
- Wash Me - Renewed: **OK**
- No animation error observed
- No blocking file conflict observed in the final stack
- Plugin count after stack: **203 heavy plugins**

Pandora validation:

- `FNIS_BiS_WashMe_List`: detected
- `FNIS_Bathing_in_Skyrim_List`: detected
- `FNIS_Bathing_in_Skyrim_Malignis_List`: detected
- Total animations added: **38,349**
- Generation completed successfully
- Final Pandora output isolated in the MO2 `Pandora Output` mod

Decision:

- keep the complete stack enabled in `ELEANOR Stable`
- `Dirtiness Lvl5 Fix` remains tracked only and will be installed only if the widget fails at dirtiness level 5

### Eleanor outfit block / BodySlide

Status: **PREPARED — IN-GAME VISUAL VALIDATION PENDING**

- Created separator `15.1 - Outfits Eleanor`
- Installed the current personal outfit batch
- Created dedicated `Bodyslide Output - Eleanor`
- Output path: `C:\JEUX\NEFARAM\mods\Bodyslide Output - Eleanor`
- BodySlide preset: `- Zeroed Sliders -`
- BodySlide generation: **COMPLETED**
- MME Milk Harness v3: CBBE 3BA **CM** variants selected
- Added outfit plugins are already ESL-flagged / ESP-FE
- Personal outfit plugins kept together before FWMF, preserving the late-loader / generated-plugin architecture
- Next step: in-game visual / physics validation

### Lakeview Manor - As It Should Be

Status: **INSTALLED — GAMEPLAY VALIDATION PENDING**

Installed stack:

- `Lakeview. Manor - As It Should Be - Rhiven`
- `Lakeview Manor - As It Should Be - (CC) Fishing Compatibility Patch - Rhiven`
- `Lakeview Manor - As It Should Be - FR - Rhiven`

MO2 section:

- `41 - Homes Eleanor`

Validation cannot be completed immediately because normal Hearthfire progression is required first:

- complete the required Falkreath Jarl progression;
- obtain and purchase the Lakeview Manor plot;
- build the manor far enough to access the affected areas.

When available in the real playthrough, test exterior placement, interior, cellar, lighting, activators, storage, Fishing compatibility and NPC navigation.

Decision:

- keep installed;
- do **not** mark Validated until Lakeview Manor can be tested in normal gameplay.

## Test entry template

### YYYY-MM-DD — Change tested

- **Change:**
- **Launch:** OK / KO
- **Save load:** OK / KO
- **UI / gameplay:** OK / KO
- **Conflicts observed:**
- **Result:**
- **Decision:**
