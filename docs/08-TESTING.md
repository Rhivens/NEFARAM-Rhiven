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

### FWMF + Skyrim Paper Map by Caro Tuts

Status: **VALIDATED**

- FWMF base: `Flat World Map Framework FOMOD Lite - Rhiven` v1.9.990
- Map: `Skyrim Paper Map by Caro Tuts for FWMF - Rhiven`
- MO2 section: `42 - FWMF Maps - Rhiven`
- In-game map test: **OK**
- Paper map rendering: **OK**
- No purple map / missing texture issue observed
- Map markers and map behavior: **OK**
- Caro Tuts map adds no ESP
- FWMF plugins remain at the bottom of the plugin order, after the late NEFARAM / LOD stack
- Safe to keep enabled in `ELEANOR Stable`

## Test entry template

### YYYY-MM-DD — Change tested

- **Change:**
- **Launch:** OK / KO
- **Save load:** OK / KO
- **UI / gameplay:** OK / KO
- **Conflicts observed:**
- **Result:**
- **Decision:**
