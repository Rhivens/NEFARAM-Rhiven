# Naked Defeat for NEFARAM-Rhiven

This guide documents the current **Naked Defeat 6.52** setup used with **NEFARAM-Rhiven 17.3.8**. Version 6.52 is an incremental patch installed over **Naked Defeat 6.50 FULL**.

It is intended as a practical community guide: enough information to reproduce the working setup without carrying over the full internal xEdit / script audit.

To avoid turning one tested modlist into a universal rule, this page uses two scopes:

- **Validated on NEFARAM-Rhiven** means the item was observed or tested on the Rhiven profile.
- **General recommendation** means a safe setup or troubleshooting practice that other lists should adapt to their own load order.

## Validated baseline

This setup was validated with:

- **NEFARAM-Rhiven 17.3.8**
- **Skyrim AE runtime 1.6.1170**
- **Acheron 1.11.3**
- **Naked Defeat 6.50 FULL + patch 6.52**
- **Mod Organizer 2**
- **Open Animation Replacer**
- **Pandora Behaviour Engine+**

## Target architecture

```text
Acheron
→ Acheron - Naked Defeat Bridge
→ Naked Defeat 6.50 FULL + patch 6.52
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
- patch incrémental **Naked Defeat 6.52**, installé juste après la 6.50 FULL
- traduction MCM compatible avec la **6.52**, installée après le patch si elle est utilisée
- `Naked Defeat - EXTRA - Acheron Bridge (SE).zip`
- `Naked Defeat - Rhiven Fix.zip`

Les textures **WhipMarks** sont déjà intégrées depuis Naked Defeat 6.50. Ne réactivez pas un ancien ajout WhipMarks séparé par-dessus cette installation.

### Optional OAR packages

- `Naked Defeat - EXTRA - OAR Crawl Animations V2.7z`
- `Naked Defeat - EXTRA - OAR Bowed Animations - fixed.7z`

The packages overlap heavily and should not be active together. The current Rhiven test preference is:

> **Crawl active / Bowed disabled**

This is a preference/test choice, not an absolute technical requirement. Bowed can be used instead if Crawl is disabled.

## MO2 setup

### Keep enabled

A simplified working block is:

```text
Acheron - Death Alternative 1.11.3
Acheron - Sacrosanct Patch
Acheron - Simple Recover
Acheron - Diary of Mine Extension

Naked Defeat 6.50 FULL
Naked Defeat 6.52 patch
Naked Defeat MCM translation compatible with 6.52
Naked Defeat - Rhiven Fix
Acheron - Naked Defeat Bridge
Naked Defeat - EXTRA - OAR Crawl Animations V2
```

If Sacrosanct is part of your build, keep `Acheron - Sacrosanct Patch` enabled in this position. It is part of the validated NEFARAM-Rhiven stack.

### Disable

```text
Yamete Kudasai
Practical Defeat Reanimated
Practical Defeat Reanimated Voicepack
Naked Defeat - EXTRA - OAR Bowed Animations fixed
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

The 6.52 patch and MCM translation are left-panel file overrides and do not add a second `Naked Defeat.esp`. `Naked Defeat - Synthesis Fix.esp` is still required after `Synthesis_1.esp` so Synthesis does not overwrite the corrected `nade_Stick` record; its final explicit Check for Errors result remains to be recorded.

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

In Naked Defeat 6.52, the `nade_CrimeEffect` property `qst2` still points to the missing **Civilian Rape** quest.

The safest current workaround is:

```text
IndecencyRapeProb = 0
```

Do not attempt to reconstruct the missing quest manually.

## Audio, TTS and SKSE configuration

For the tested Rhiven audio setup:

- replace **AudioUtil 0.9.13** with **AudioUtil 0.9.30**; do not keep both versions active;
- add **AudioUtil TTS 0.5.1**;
- add the **Kokoro English** voice/model package required by the chosen TTS setup;
- keep these SKSE/audio components before Naked Defeat in the MO2 left panel so the 6.52 files and its translation can win where intended.

Suggested left-panel relationship:

```text
AudioUtil 0.9.30
AudioUtil TTS 0.5.1
Kokoro English
...
Naked Defeat 6.50 FULL
Naked Defeat 6.52 patch
Naked Defeat MCM translation compatible with 6.52
Naked Defeat - Rhiven Fix
Acheron - Naked Defeat Bridge
```

AudioUtil TTS is optional from Naked Defeat's plugin-master point of view, but it is part of the documented Rhiven audio setup. On the Rhiven profile, AudioTTS tracking has been validated InGame. Fine MCM/SKSE tuning and balancing are still reserved for the final playthrough.

## Pandora and OAR

A Pandora regeneration is required after disabling Yamete Kudasai because YK contains behavior / animation assets and an FNIS list.

After disabling YK:

1. confirm the correct MO2 profile is active;
2. regenerate Pandora;
3. verify there is no blocking generation error.

The OAR replacement packages do not require Pandora merely because they are OAR replacements.

Use:

> **OAR Crawl active / OAR Bowed disabled**

because the two packages overlap heavily. This is Rhiven's current test preference; selecting Bowed instead is valid if Crawl is disabled.

The **6.52 incremental patch itself contains only ESP, PEX and PSC files**, so updating to 6.52 does **not** require another Pandora run. The earlier Pandora run documented above was required because Yamete Kudasai behavior content was removed, not because of the 6.52 patch.

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

## 6.52 static audit notes

### Validated on NEFARAM-Rhiven

- xEdit Check for Errors on `Naked Defeat.esp` 6.52: **1228 records / 18 errors**;
- `Naked Defeat - Rhiven Fix.esp` remains required for `nade_Stick`, `nade_BoneMace`, `nade_WristChains_R` and `nade_WristChains_L`;
- `Naked Defeat - Synthesis Fix.esp` remains required after `Synthesis_1.esp` to preserve the `nade_Stick` correction;
- `nade_CrimeEffect.qst2` still targets the missing Civilian Rape quest, so `IndecencyRapeProb = 0` remains mandatory;
- `nade_WhipAction_01` and `nade_WalkTo_01` remain invalid legacy packages and were deliberately left unpatched;
- old follower `crux`, `crux2` and `crux3` scenes remain malformed/legacy and were deliberately left intact.

### General recommendation

Do not automatically “clean” every xEdit warning. Patch only a record whose current code path or reproducible gameplay symptom demonstrates that it is active and broken. Other modlists should verify their own winning overrides, especially after Synthesis or similar generated patches.

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

### Validated on NEFARAM-Rhiven

- humanoid defeat;
- creature defeat;
- Acheron → Naked Defeat handoff;
- bleedout recovery;
- repeated defeat events;
- save / exit / reload after completed events;
- furniture escape: press Space once, wait for the progress messages, then press Space again only when the message says the restraints are loose enough.
- MO2 and the MCM display **6.52** after activation;
- new `Resist` and `Progress` hotkeys are visible;
- new robbery options are visible;
- Chest Quest Robbery spawns its chest;
- the player's belongings transfer into the chest;
- the items can be recovered from the chest;
- AudioTTS tracking works.

The general defeat-flow save/exit/reload test above was completed previously. It must not be confused with Chest Quest Robbery persistence: **save → full Skyrim exit → reload while the robbery chest is still active has not been tested**.

### General recommendations for other setups

- use a cloned MO2 profile and a disposable save for first tests;
- keep `IndecencyRapeProb = 0` while the missing quest reference remains;
- keep only one of Crawl or Bowed active;
- preserve the required relative plugin order and inspect generated-patch overrides;
- independently verify recovery, repeated defeats and save/reload behavior on your own list.

### Still pending / extended playtesting

- follower defeat;
- Chest Quest Robbery persistence with an active chest across save → full exit → reload;
- individual validation of every untested 6.52 branch;
- final xEdit result for `Naked Defeat - Synthesis Fix.esp`;
- final MCM/SKSE tuning;
- final stable-profile verdict;
- less common edge cases during the definitive playthrough.

Current status:

> **NAKED DEFEAT 6.52 CURRENT PATCH — CORE INTEGRATION, CHEST QUEST ROBBERY FLOW AND AUDIOTTS TRACKING VALIDATED ON NEFARAM-RHIVEN; EXTENDED PLAYTESTING ONGOING**

## Known minor observation

### Bathing in Skyrim / Golden Shower

The Naked Defeat handoff can correctly trigger the Bathing in Skyrim cleaning animation, but visual dirt / cum layers may not always be removed depending on the surrounding setup.

This is currently treated as **non-blocking**.

## Rollback

Until you are satisfied with the setup:

- keep Yamete Kudasai installed but disabled;
- keep Practical Defeat Reanimated installed but disabled;
- keep the Practical Defeat voicepack installed but disabled;
- keep the unused OAR alternative installed but disabled;
- keep a backup of the MO2 left-panel and plugin order.

If the setup fails your own tests, restore the previous defeat stack rather than editing `Naked Defeat.esp` destructively.

## Advanced technical notes

For the complete internal audit, xEdit reasoning, bridge inspection, detailed test protocol and known unused / malformed records, see:

[NEFARAM-Rhiven Naked Defeat internal integration guide](../../06%20-%20GAMEPLAY/NAKED%20DEFEAT/NAKED-DEFEAT-INTEGRATION.md)

[Closed Naked Defeat 6.51 integration study](../../06%20-%20GAMEPLAY/NAKED%20DEFEAT/NAKED-DEFEAT-6.51-PRELIMINARY-INTEGRATION-STUDY.md)
