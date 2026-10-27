# Naked Defeat for NEFARAM-Rhiven

This guide documents the validated **Naked Defeat 6.51** setup used with **NEFARAM-Rhiven 17.3.8**. Version 6.51 is an incremental patch installed over **Naked Defeat 6.50 FULL**.

It is intended as a practical community guide: enough information to reproduce the working setup without carrying over the full internal xEdit / script audit.

## Validated baseline

This setup was validated with:

- **NEFARAM-Rhiven 17.3.8**
- **Skyrim AE runtime 1.6.1170**
- **Acheron 1.11.3**
- **Naked Defeat 6.50 FULL + patch 6.51**
- **Mod Organizer 2**
- **Open Animation Replacer**
- **Pandora Behaviour Engine+**

## Target architecture

```text
Acheron
→ Acheron - Naked Defeat Bridge
→ Naked Defeat 6.50 FULL + patch 6.51
→ Naked Defeat - Rhiven Fix
```

Responsibilities:

- **Acheron** detects defeat and manages the defeated / bleedout actor state.
- **Acheron - Naked Defeat Bridge** forwards the defeated player and assailants to Naked Defeat.
- **Naked Defeat** handles the post-defeat scenes, consequences and recovery flow.
- **Naked Defeat - Rhiven Fix** corrects four malformed records in Naked Defeat 6.50.

The intended principle is:

> **Acheron handles defeat detection and actor state; Naked Defeat handles consequences and scenes.**

## Files used

### Required

- `Naked Defeat 6-50 - FULL - (AE + SE).7z`
- patch incrémental **Naked Defeat 6.51**, installé juste après la 6.50 FULL
- **MCM FR 6.51**, installé après le patch 6.51
- `Naked Defeat - EXTRA - Acheron Bridge (SE).zip`
- `Naked Defeat - Rhiven Fix.zip`

Les textures **WhipMarks** sont déjà intégrées depuis Naked Defeat 6.50. Ne réactivez pas un ancien ajout WhipMarks séparé par-dessus cette installation.

### OAR package retained

- `Naked Defeat - EXTRA - OAR Bowed Animations - fixed.7z`

### OAR package not used together with Bowed

- `Naked Defeat - EXTRA - OAR Crawl Animations V2.7z`

The Bowed package overlaps heavily with Crawl, so the validated Rhiven setup keeps:

> **Bowed active / Crawl disabled**

## MO2 setup

### Keep enabled

A simplified working block is:

```text
Acheron - Death Alternative 1.11.3
Acheron - Sacrosanct Patch
Acheron - Simple Recover
Acheron - Diary of Mine Extension

Naked Defeat 6.50 FULL
Naked Defeat 6.51 patch
Naked Defeat MCM FR 6.51
Naked Defeat - Rhiven Fix
Acheron - Naked Defeat Bridge
Naked Defeat - EXTRA - OAR Bowed Animations fixed
```

If Sacrosanct is part of your build, keep `Acheron - Sacrosanct Patch` enabled in this position. It is part of the validated NEFARAM-Rhiven stack.

### Disable

```text
Yamete Kudasai
Practical Defeat Reanimated
Practical Defeat Reanimated Voicepack
Naked Defeat - EXTRA - OAR Crawl Animations V2
```

Important:

> Disable the **entire Yamete Kudasai MO2 mod**, not only `YameteKudasai.esp`.

Yamete Kudasai also ships Acheron consequence YAML files. Leaving those files active while disabling only the ESP can leave competing or broken Acheron outcomes registered.

Practical Defeat and Naked Defeat are both full post-defeat consequence systems. Running both at the same time makes it unclear which system owns the defeat event and can produce inconsistent results.

## Validated plugin order

The tested placement is:

```text
SLNights.esp
Naked Defeat.esp
Naked Defeat - Rhiven Fix.esp
Acheron - Naked Defeat Bridge.esp
BaboInteractiveDia.esp
```

The essential internal order is:

```text
Naked Defeat.esp
→ Naked Defeat - Rhiven Fix.esp
→ Acheron - Naked Defeat Bridge.esp
...
Synthesis_1.esp
→ Naked Defeat - Synthesis Fix.esp
```

The 6.51 patch and MCM FR are left-panel file overrides and do not add a second `Naked Defeat.esp`. `Naked Defeat - Synthesis Fix.esp` belongs after `Synthesis_1.esp`; its final explicit xEdit validation remains to be recorded.

The Rhiven Fix must load after `Naked Defeat.esp` so its corrected records win. The Acheron Bridge then loads after both as the integration layer.

> Do not blindly auto-sort a finalized NEFARAM load order with LOOT. Preserve the tested relative order unless you have verified the resulting overrides yourself.

## First launch

On the first launch:

1. Open the Naked Defeat MCM.
2. **Enable Naked Defeat first.**
3. Only then configure hotkeys and the remaining options.

If Naked Defeat itself is not enabled, hotkey rebinding may appear not to work.

## Mandatory settings

In the Naked Defeat MCM:

- Set **Defeat on Bleedout = OFF** when using the Acheron Bridge.
- Set **IndecencyRapeProb = 0**.

### Why Defeat on Bleedout must be OFF

Acheron already owns the defeat / bleedout handoff. Allowing Naked Defeat to trigger independently on bleedout would create two systems trying to handle the same event.

### Why IndecencyRapeProb must be 0

Naked Defeat 6.50 still contains a script reference to a missing **Civilian Rape** quest.

The safest current workaround is:

```text
IndecencyRapeProb = 0
```

Do not attempt to reconstruct the missing quest manually.

## Audio, TTS and SKSE configuration

For the 6.51 setup:

- replace **AudioUtil 0.9.13** with **AudioUtil 0.9.30**; do not keep both versions active;
- add **AudioUtil TTS 0.5.1**;
- add the **Kokoro English** voice/model package required by the chosen TTS setup;
- keep these SKSE/audio components before Naked Defeat in the MO2 left panel so the 6.51 files and its translation can win where intended.

Suggested left-panel relationship:

```text
AudioUtil 0.9.30
AudioUtil TTS 0.5.1
Kokoro English
...
Naked Defeat 6.50 FULL
Naked Defeat 6.51 patch
Naked Defeat MCM FR 6.51
Naked Defeat - Rhiven Fix
Acheron - Naked Defeat Bridge
```

AudioUtil TTS is optional from Naked Defeat's plugin-master point of view, but it is part of the documented Rhiven audio setup. The 6.51 SKSE menu exposes many configurable options. Only the functional base is retained here; fine MCM/SKSE tuning and balancing are deliberately reserved for the final playthrough.

## Pandora and OAR

A Pandora regeneration is required after disabling Yamete Kudasai because YK contains behavior / animation assets and an FNIS list.

After disabling YK:

1. confirm the correct MO2 profile is active;
2. regenerate Pandora;
3. verify there is no blocking generation error.

The **OAR Bowed Animations fixed** package itself does not require Pandora merely because it is an OAR replacement package.

Use:

> **OAR Bowed active / OAR Crawl disabled**

because the two packages overlap heavily.

## Naked Defeat - Rhiven Fix

Download:

**[Naked Defeat - Rhiven Fix.zip](Naked%20Defeat%20-%20Rhiven%20Fix.zip)**

The ZIP is MO2-ready and contains:

```text
Naked Defeat - Rhiven Fix/
├─ Naked Defeat - Rhiven Fix.esp
└─ meta.ini
```

The patch intentionally corrects only four records.

### Wrist-chain ARMA records

- `nade_WristChains_L`
- `nade_WristChains_R`

Both contained invalid `REFR` entries under `Additional Races`. Those invalid entries are removed.

### Weapon records

- `nade_BoneMace`
- `nade_Stick`

Both contained a malformed:

`CRDT - Critical Data > Effect`

The Rhiven Fix normalizes that field to:

`NULL - Null Reference [00000000]`

No weapon stats or gameplay values are changed.

### Validation

`Naked Defeat - Rhiven Fix.esp`:

- **5 processed records**
- **0 xEdit errors**

Keep the patch as a standalone plugin. Do **not** merge it into `Naked Defeat.esp`.

## Recommended smoke test

If possible, use a cloned MO2 profile and a disposable test save before committing the change to your main playthrough.

Minimum checks:

- defeat by a humanoid;
- defeat by a creature;
- Naked Defeat starts through the Acheron Bridge;
- the player exits Acheron bleedout cleanly;
- player controls return normally;
- assailants are released and are not permanently pacified;
- trigger another defeat in the same session;
- save after a completed defeat event;
- fully exit Skyrim;
- reload that save;
- confirm normal gameplay still works after reload.

A scene starting successfully is not enough by itself. The player must also recover cleanly from Acheron's defeated state.

## If something is wrong

Investigate before considering the setup stable if any of these become reproducible:

- the player remains in bleedout;
- controls never return;
- assailants remain permanently pacified;
- the Acheron Bridge fires but Naked Defeat does not start;
- a second defeat no longer works;
- save / reload breaks the defeat chain.

## Cleaning stale MCM entries

After fully disabling Yamete Kudasai and Practical Defeat, old empty MCM entries may remain visible in an existing save.

A SkyUI MCM refresh can remove those stale menus:

```text
setstage ski_configmanagerinstance 1
```

Use this only after the old mods are fully disabled.

## Validation status

### Validated

- humanoid defeat;
- creature defeat;
- Acheron → Naked Defeat handoff;
- bleedout recovery;
- repeated defeat events;
- save / exit / reload after completed events;
- furniture escape: press Space once, wait for the progress messages, then press Space again only when the message says the restraints are loose enough.

### Still pending / extended playtesting

- follower defeat;
- individual validation of every 6.51 changelog branch;
- final xEdit result for `Naked Defeat - Synthesis Fix.esp`;
- final MCM/SKSE tuning;
- final stable-profile verdict;
- less common edge cases during the definitive playthrough.

Current status:

> **NAKED DEFEAT 6.51 CORE GAMEPLAY VALIDATED — EXTENDED PLAYTESTING ONGOING**

## Known minor observation

### Bathing in Skyrim / Golden Shower

The Naked Defeat handoff can correctly trigger the Bathing in Skyrim cleaning animation, but visual dirt / cum layers may not always be removed depending on the surrounding setup.

This is currently treated as **non-blocking**.

## Rollback

Until you are satisfied with the setup:

- keep Yamete Kudasai installed but disabled;
- keep Practical Defeat Reanimated installed but disabled;
- keep the Practical Defeat voicepack installed but disabled;
- keep OAR Crawl installed but disabled;
- keep a backup of the MO2 left-panel and plugin order.

If the setup fails your own tests, restore the previous defeat stack rather than editing `Naked Defeat.esp` destructively.

## Advanced technical notes

For the complete internal audit, xEdit reasoning, bridge inspection, detailed test protocol and known unused / malformed records, see:

[NEFARAM-Rhiven Naked Defeat internal integration guide](../../06%20-%20GAMEPLAY/NAKED%20DEFEAT/NAKED-DEFEAT-INTEGRATION.md)

[Closed Naked Defeat 6.51 integration study](../../06%20-%20GAMEPLAY/NAKED%20DEFEAT/NAKED-DEFEAT-6.51-PRELIMINARY-INTEGRATION-STUDY.md)
