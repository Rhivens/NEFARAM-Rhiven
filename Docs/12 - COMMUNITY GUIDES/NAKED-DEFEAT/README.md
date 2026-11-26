# Naked Defeat 7.00 + Hotfix 1 for NEFARAM-Rhiven

> **Current community guide — updated 24 November 2026.** The 7.00 file structure and a mid-save load have been checked on NEFARAM-Rhiven 17.3.8; **in-game defeat scenarios with Acheron Bridge are still pending validation**. The earlier 6.52 guide is preserved separately in [LEGACY-6.52.md](LEGACY-6.52.md).

## 7.00 at a glance

- **Skyrim AE 1.6.1170**, **NEFARAM-Rhiven 17.3.8**, **Acheron 1.11.3**, MO2.
- Install **Naked Defeat 7.00 FULL**, then **7.00 Hotfix 1** so its scripts win.
- **New hard dependency:** [Papyrus Ini Manipulator](https://www.nexusmods.com/skyrimspecialedition/mods/65634).
- Keep **Acheron - Naked Defeat Bridge** for the Acheron integration (static event interface checked, 7.00 gameplay recovery still to be tested).
- Do **not** install 7.00 over the old 6.50 FULL / 6.52 / 6.53 module chain. Disable prior patches, old translated PEX and mismatched third-party fixes.
- On Rhiven's profile **Yamete Kudasai is completely disabled**, including its Acheron YAML files, as are **Practical Defeat Reanimated and its voicepack**.
- Choose **one** Naked Defeat locomotion pack: Rhiven uses OAR Crawl V2, with OAR Bowed disabled.

### MO2 installation — standard or Rhiven FR fusion

**Recommended general layout:**

```text
Naked Defeat 7.00 FULL                 [enabled]
Naked Defeat 7.00 Hotfix 1             [enabled; overwrites FULL]
Naked Defeat - EXTRA - ConfigINIs      [enabled; optional personalized INIs]
Acheron - Naked Defeat Bridge          [enabled for Acheron users]
Naked Defeat - OAR Crawl V2            [optional; not with Bowed]
```

**Rhiven's personalized French test layout:** an **English FULL + Hotfix 1 FUSION** module is enabled, followed by a **7.00 FUSION FR** override built from the **hotfixed compiled scripts**; the separate FULL and Hotfix source modules are disabled. This fusion is a **personal workaround to keep translated script strings while preserving Hotfix code**, not a requirement for other users.

**Important for translators:** older 6.53 translated `.pex` files must **not** overwrite 7.00 Hotfix scripts. Make the French translation from the final **7.00 + Hotfix** files, not from a 6.53 binary replacement.

## New external `NakedConfig` files

Version 7.00 replaces `nadeConfig.JSON` and the three old hairstyle JSONs with INI files in **`Data/NakedConfig/`**. The MO2 custom config mod should expose `NakedConfig/` directly at its root. Nymra recommends placing customized INIs in a separate EXTRA module that wins over default configs.

Typical files: `nade_Config.ini`, `nade_DefeatSex.ini`, `nade_FactionBehavior.ini`, `nade_Followers.ini`, `nade_Furniture.ini`, `nade_HairStyles.ini`, `nade_NakedLoot.ini`, `nade_PublicPunishment.ini`, `nade_TTS_Options.ini`.

For Rhiven, the 6.53 Free/Messy/Slave hairstyle JSONs were migrated to one `nade_HairStyles.ini` (ten entries per group). **Known 7.00 + Hotfix 1 issue (confirmed by Nymra, fix promised for the next patch):** the `GetHairStyle()` INI branches are guarded by his internal `Nym()` test. On a regular character, the **K** hotkey may still require the old hairstyle JSON files and display a missing-JSON warning if they are absent. **Workaround validated in game:** re-enable the old hairstyle JSONs alongside the new INI files; the hotkey then works again. Check the next official patch before removing legacy JSONs.

## First launch and key configuration

1. Confirm **Papyrus Ini Manipulator** loads; open the Naked Defeat MCM, enable the mod, then configure hotkeys.
2. Apply the **new Nymra Action Log (`NymLogVersion022`) through SLATE**. Close and reopen Naked Defeat MCM to refresh optional dependency checks. A community report associates missing animation tags with missing SLATE registration.
3. **Acheron Bridge users: set Naked Defeat “Defeat on Bleedout” to 0/OFF**; Acheron handles the original bleedout event. Confirm Naked Defeat's Acheron handling is enabled.
4. On the Rhiven setup, retain **`IndecencyRapeProb = 0` provisionally** until the old missing Civilian Rape quest route is re-audited against the 7.00 ESP. The previous 6.52 finding must not be asserted as newly verified in 7.00.
5. If using **Bathing in Skyrim Renewed**, it is the bathing integration Nymra intends to keep supporting. A watcher-detection issue after defeat has been reported by another player; if reproducible, compare Bathing Renewed's hotkey with Naked Defeat's **Shift+K → Bathing**.
6. If enemies converge from across a cell during defeat, Nymra says that is currently intentional; reduce the **search radius** if necessary.

**SLATE and SexLab P+:** Nymra says SLATE is not natively compatible with SexLab P+; a third-party converter has been discussed but is **not validated here**. Do not assume this guide confirms SLP+ compatibility.

## Acheron Bridge and fixes — current evidence

The Bridge sends the `StartNakedDefeatExternal` event with six assailant slots; Naked Defeat 7.00 Hotfix retains the matching handler. **Static interface looks compatible**, but end-to-end Acheron recovery / multiple defeats **still require live tests**. The Bridge also overrides an older `nade_Sandbox` AI package; do not patch this without a reproduced problem.

**Rhiven Fix is NOT required for Naked Defeat 7.00 + Hotfix 1.** `Naked Defeat - Rhiven Fix.esp` only cleans four malformed legacy records (`nade_WristChains_L/R`, `nade_Stick`, `nade_BoneMace`). `Naked Defeat - Synthesis Fix.esp` preserves the `nade_Stick` correction after `Synthesis_1.esp`. **Author clarification:** Nymra states these specific legacy Naked Dungeons records are **not called or used**. Thus the corrections are **optional cleanup for Rhiven**, not established requirements for 7.00 gameplay. They remain active provisionally on Rhiven's test profile, but **a normal 7.00 install does not need either Rhiven Fix or Synthesis Fix**. Do not copy these personal overrides to unrelated load orders.

Nymra also confirmed the duplicated Chaurus/Sabrecats faction test reported during the 6.54 Preview review has been corrected in 7.00's source.

## Mid-save update and validation boundary

**Nymra explicitly designs Naked Defeat to update without starting a new game.** His stated priority is save compatibility; this is not a promise that every third-party bridge or customized patch will be bug-free.

On the Rhiven profile, an existing 6.53 save successfully **loaded under 7.00**, was saved again, and the player could travel between cells and use bathing. Initial ReSaver++ comparisons showed **no Naked Defeat-specific issue identified**. **This is not a completed defeat test.**

**Still to test before declaring 7.00 validated:** MCM and SLATE recognition; defeat by human / creature; Acheron-to-Naked Defeat handoff; control restoration with and without Escape Crawl; captivity/furniture escape; repeated defeats; save/exit/reload after defeat; Bathing Renewed after a defeat.

Keep the original 6.53 save and a cloned MO2 profile available for rollback. Do not clean ReSaver entries as a prerequisite for this update.

## Background / technical audit

The internal integration record includes source diff (6.53 → 7.00 FULL → Hotfix 1), ESP/Bridge checks, known unconfirmed script issues and ReSaver baseline:

[Internal technical audit and migration history](../../06%20-%20GAMEPLAY/NAKED%20DEFEAT/NAKED-DEFEAT-INTEGRATION.md)

---

## Historical 6.52 guide

The previous guide is preserved for reference in [LEGACY-6.52.md](LEGACY-6.52.md). Its older requirements (including references to the Rhiven Fix as mandatory) **do not apply to Naked Defeat 7.00 + Hotfix 1**.
