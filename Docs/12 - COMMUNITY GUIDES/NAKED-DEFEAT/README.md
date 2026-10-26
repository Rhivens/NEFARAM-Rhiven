# Naked Defeat for NEFARAM-Rhiven

This guide covers the validated Naked Defeat setup for **NEFARAM-Rhiven 17.3.8** with **Naked Defeat 6.50**.

## Architecture

```text
Acheron
→ Acheron - Naked Defeat Bridge
→ Naked Defeat
→ Naked Defeat - Rhiven Fix
```

Acheron detects defeat and bleedout. The bridge forwards the event to Naked Defeat, which handles the post-defeat consequence and recovery flow. The Rhiven Fix is a small corrective plugin for malformed records in Naked Defeat 6.50.

## Required setup

Keep enabled:

- Naked Defeat 6.50 FULL
- Acheron - Naked Defeat Bridge
- Naked Defeat - Rhiven Fix
- Naked Defeat - EXTRA - OAR Bowed Animations - fixed

Disable:

- Yamete Kudasai — disable the **entire MO2 mod**, not only its ESP
- Practical Defeat Reanimated
- Practical Defeat Reanimated Voicepack
- Naked Defeat - EXTRA - OAR Crawl Animations V2

Yamete Kudasai and Practical Defeat overlap with Acheron's consequence handling and Naked Defeat's post-defeat system. Leaving them active creates competing outcomes and makes the defeat chain unreliable.

### MO2 and plugin order

Keep the Naked Defeat components together in the MO2 left panel, with the base mod before the Rhiven Fix and the Acheron Bridge. The important plugin order is:

```text
Naked Defeat.esp
Naked Defeat - Rhiven Fix.esp
Acheron - Naked Defeat Bridge.esp
```

The Rhiven Fix must load after `Naked Defeat.esp` so its corrected records win. The bridge loads after both as the integration layer.

### Pandora and OAR

Regenerate Pandora after disabling Yamete Kudasai. YK includes behavior and animation content, so removing it from the active stack requires rebuilding the animation output.

Use **OAR Bowed Animations fixed** and keep **OAR Crawl Animations V2** disabled because the two packages overlap heavily. OAR Bowed is an OAR replacement package and does not, by itself, require Pandora generation.

## Mandatory settings

In the Naked Defeat MCM:

- Set **Defeat on Bleedout = OFF** when using the Acheron Bridge. Acheron and the bridge own the bleedout handoff.
- Set **IndecencyRapeProb = 0**. Naked Defeat 6.50 contains a missing Civilian Rape quest reference; do not attempt to reconstruct that quest.

## Naked Defeat - Rhiven Fix

Download: **[Naked Defeat - Rhiven Fix.zip](Naked%20Defeat%20-%20Rhiven%20Fix.zip)**

The patch:

- fixes malformed `nade_WristChains_L` and `nade_WristChains_R` Additional Races entries by removing invalid REFR entries;
- normalizes malformed `CRDT - Critical Data > Effect` fields on `nade_BoneMace` and `nade_Stick` to `NULL`;
- passes xEdit validation with **5 processed records and 0 errors**.

Keep `Naked Defeat - Rhiven Fix.esp` as a standalone plugin. Do not merge it into `Naked Defeat.esp`; the separate override remains reversible and easy to audit.

## Validation status

Core gameplay is validated. The following tests have passed:

- humanoid defeat;
- creature defeat;
- bleedout recovery;
- repeated defeat events;
- save and reload after completed events.

Follower defeat, final MCM tuning, and the final stable-profile verdict remain pending. Extended playtesting is ongoing.

## Rollback

Until you are satisfied with the setup, keep Yamete Kudasai, Practical Defeat Reanimated, and its voicepack installed but disabled. If you need to roll back, restore the previous defeat stack rather than editing Naked Defeat destructively.

For detailed technical notes and the full test protocol, see the [internal integration guide](../../06%20-%20GAMEPLAY/NAKED%20DEFEAT/NAKED-DEFEAT-INTEGRATION.md).
