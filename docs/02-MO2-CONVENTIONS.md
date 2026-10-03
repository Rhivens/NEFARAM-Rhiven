# 02 - MO2 conventions

## Profiles

Main profile:

- `ELEANOR Stable`

Possible temporary profiles:

- `ELEANOR Dev`
- `ELEANOR Test`

## Personal naming convention

Every manually added or generated mod should end with:

`- Rhiven`

Examples:

- `Dragonborn UI - SkyUI Reskin - Rhiven`
- `Terrain Helper - Generated INI - Rhiven`
- `Some Compatibility Patch - Rhiven`

This allows all personal changes to be found instantly with the MO2 filter.

## Separator convention

MO2 left-pane separators are numbered for readability.

Examples:

- `01 - Major Patches`
- `02 - SKSE Utility Mods`
- `03 - Fixes`
- `04 - User Interface`
- ...
- `41 - Added Mods`

## General rule

Whenever practical:

1. keep stock NEFARAM mods untouched;
2. isolate generated or modified files into a dedicated `- Rhiven` mod;
3. document why the override exists;
4. test after each logical modification block;
5. avoid adding/removing large scripted mods after the real playthrough begins.
