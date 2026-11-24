# NEFARAM-Rhiven 17.3.8 — Naked Defeat 7.00 + Hotfix 1 integration (November 2026)

> **STATUS — STATIC AUDIT COMPLETED; SAVE MIGRATION / BASIC WORLD INTERACTIONS OBSERVED; DEFEAT GAMEPLAY VALIDATION PENDING.**
>
> This is the **current integration section**. Everything under **Historical integration archive (6.50–6.52)** is preserved for traceability, not as an instruction to install those older versions.

## Current target and migration

- Skyrim AE **1.6.1170**; NEFARAM-Rhiven **17.3.8**; Acheron **1.11.3**; MO2 test profile **`Eleanor 17.3.8 - Naked Defeat`**.
- Naked Defeat **7.00 FULL + official Hotfix 1** replaces **6.50 FULL and all incremental 6.52/6.53 patches**. Disable old bases, patches and old translations; never allow 6.53 `.pex` files to override 7.00.
- New **hard dependency: Papyrus Ini Manipulator** (Rhiven already has 1.9.8).
- **Acheron → Acheron - Naked Defeat Bridge → Naked Defeat 7.00** remains the tested *static* architecture. Acheron detects bleedout; Naked Defeat handles consequences. Do not run **Yamete Kudasai** (including its consequence YAML assets) or **Practical Defeat Reanimated / voicepack** alongside this stack.
- **Crawl OAR V2 enabled / Bowed OAR disabled** on this profile; keep only one alternative enabled.
- Nymra states that **save compatibility is a first priority** and Naked Defeat is designed not to require a new game. This is an author intention, not a guarantee for every setup or third-party bridge. Keep the 6.53 save and a cloned MO2 profile as rollback points.

### MO2 — actual Rhiven test layout

```text
DISABLED: Naked Defeat 6.50 FULL / 6.52 / 6.53 / old FR
DISABLED: separate 7.00 FULL and Hotfix modules (after creating fusion)
ENABLED:  Naked Defeat 7.00 FULL + Hotfix 1 — FUSION (Hotfix PEX files winning)
ENABLED:  Naked Defeat 7.00 FUSION FR (built from the hotfixed 7.00 scripts)
DISABLED: Naked Defeat - EXTRA - Profile JSONs (legacy)
ENABLED:  Naked Defeat - EXTRA - ConfigINIs
ENABLED:  Naked Defeat - Rhiven Fix (provisional)
ENABLED:  Acheron - Naked Defeat Bridge (provisional 7.00 compatibility)
ENABLED:  Naked Defeat - EXTRA - OAR Crawl Animations V2
DISABLED: Naked Defeat - EXTRA - OAR Bowed Animations
DISABLED: Yamete Kudasai / Practical Defeat Reanimated / its voicepack
ENABLED:  Naked Defeat - Synthesis Fix after Synthesis_1.esp (provisional)
```

The **FUSION is a Rhiven maintenance choice**, not an official requirement: community users can instead keep FULL → Hotfix → compatible FR override, provided the **translated PEX files originate from the Hotfix**, not from 6.53. Check MO2's **Data** and **Conflicts** tabs; priority alone does not prove the final assets are correct.

### New external configuration

Naked Defeat 7.00 replaces `nadeConfig.JSON` and legacy hairstyle JSON files with **`NakedConfig/*.ini`**. Papyrus looks for paths such as `Data/NakedConfig/nade_HairStyles.ini`. The Rhiven EXTRA module uses:

```text
Naked Defeat - EXTRA - ConfigINIs/
└── NakedConfig/
    ├── nade_Config.ini
    ├── nade_DefeatSex.ini
    ├── nade_FactionBehavior.ini
    ├── nade_Followers.ini
    ├── nade_Furniture.ini
    ├── nade_HairStyles.ini
    ├── nade_NakedLoot.ini
    ├── nade_PublicPunishment.ini
    └── nade_TTS_Options.ini
```

The nine default EXTRA INIs were compared with FULL and matched. The Hotfix archive also included `nade_Config_Factions.ini` (internal version 653), which was not found among the INI paths referenced by examined 7.00 sources; leave it untouched rather than overwriting `nade_FactionBehavior.ini`. In MO2, the red **No valid game data** flag on this INI-only package was non-blocking: MO2's Conflicts view showed its nine INIs overriding the FULL equivalents. Verify virtual paths, not the icon alone.

**Eleanor's hairstyles** were migrated from three 6.53 JSON profiles into `nade_HairStyles.ini`: ten Free, ten Messy and ten Slave entries, preserving original names and the repeated `HairFemaleRedguard04` weighting. Old JSONs are kept disabled for rollback.

### Translation and animation tags

- xTranslator / ESP-ESM Translator can reuse 6.53 translations, but only apply textual changes to **7.00 FULL + Hotfix 1** assets. Never copy translated 6.53 compiled scripts on top of Hotfix 1.
- Rhiven created a separate French override of the fused 7.00 package. The final compiled output still requires **in-game smoke tests**.
- The new **Nymra Action Log** (`NymLogVersion022`) must be registered / reapplied through **SLATE**; refresh Naked Defeat MCM afterward to re-evaluate soft dependencies. Check the SLATE requirement indicator.
- Nymra notes **SLATE does not natively work with SexLab P+**; a third-party converter exists but is not validated here. This build uses the existing SexLab setup; do not assume compatibility from reports about P+.
- **Bathing in Skyrim Renewed** is the preferred bathing integration. One reported issue after defeat concerns the bathing mod's watcher detection; compare its own hotkey with Naked Defeat's Shift+K Bathing action if reproduced.

## 7.00 source, xEdit and Bridge audit

### Version comparison

Source archives reviewed: `ND_Sources_6.53.zip`, `ND_Sources_7.0.zip`, `ND_Sources_7.0_Hotfix.zip`.

| Comparison | Changed `.psc` scripts | Added / removed |
| --- | ---: | ---: |
| 6.53 → 7.00 FULL | 18 | 0 |
| 7.00 FULL → Hotfix 1 | 6 | 0 |
| 6.53 → 7.00 Hotfix 1 | 18 | 0 |

Each archive contains 244 `.psc` files. These counts describe the **sources inspected**, not the number of shipped compiled scripts.

### Confirmed upstream correction

In `nade_storage_qf_scr.psc`, `GetDefeatType_FromFaction()`, the duplicate `FactionsPredators[7]` condition formerly mapping both Sabrecats and Chaurus was corrected; Chaurus now uses `FactionsPredators[3]`. Nymra acknowledged Rhivens_'s report and stated it was fixed; the correction was also observed in 7.00.

### Acheron Bridge

- Quest `achnadeBridgeQuest` uses scripts `achnadeBridgeQuestScript.psc` and `QF_achnadeBridgeQuest_0A005900.psc`.
- Bridge sends `StartNakedDefeatExternal` with **six assailant slots**; the matching event handler in `nade_configquest_scr.psc` remained unchanged between 6.53, FULL and Hotfix.
- **Potential diagnostic weakness:** the Bridge does not confirm a successful start after event dispatch. If first assailant (`Enemy00`) is missing, Naked Defeat can decline to start. This is **not a reproduced root cause** of a defeat loop.
- Bridge overrides `nade_Sandbox` (12 PKCU inputs vs 2 in the 7.00 base). The newer Naked Defeat AI package management uses Skyrim.esm sandbox packages in one examined path, reducing a presumed direct override conflict; **complete package interaction remains untested**.
- Do **not** rewrite the Bridge or its sandbox package preemptively. Revisit on reproducible defeat issues.

### ESP record anomalies / corrective patches

SSEEdit review reconfirmed `nade_WristChains_L/R` (invalid `REFR` references inside Additional Races) and `nade_Stick` / `nade_BoneMace` (malformed `CRDT → Effect`). Rhiven Fix normalizes those; Synthesis Fix protects `nade_Stick` after `Synthesis_1.esp`.

**Author clarification:** Nymra says those four records are **legacy Naked Dungeons artifacts that are never called/used**. Therefore these patches are **optional cleanup / local overrides**, not confirmed gameplay requirements for Naked Defeat 7.00. The patches remain enabled **provisionally** on Rhiven's test profile, pending final review of masters and winning overrides. Avoid presenting them as universally mandatory.

`HighHrothgar` CELL and `RuinsCandleSconceOn2` REFR conflicts were inspected; no reproducible 7.00 issue established.

### Open Papyrus observations — NOT confirmed bugs

- `nade_allegiancequest_qf_scr.psc`, `AreaScanDuplicateEnemies()`: `storqst.CurrentLocationDefeatType; = "NoDefeatType"` has a semicolon that comments out the assignment. Determine whether the surrounding revised first-match scan intentionally makes this obsolete.
- `nade_storage_qf_scr.psc`, `Actor_ResetPackages()`: `ActorUtil.ClearPackageOverride(akActor)` may clear overrides owned by other mods; investigate API semantics and test before calling it a compatibility defect.
- `nade_calmquest_qf_scr.psc` Hotfix adds a control-release path for non-Escape-Crawl endings. Other exits (captivity, interrupted scenes, rescue) still require gameplay testing.
- First assailant validity, scenario selection failures and repeat knockdown/recovery loops remain diagnostic targets; none is proven to originate from the Bridge.

## Actual 7.00 migration observations and limits

**Observed:** existing 6.53 save loaded under the 7.00 FR fusion; Eleanor changed cells, used bathing and saved again. No specific Naked Defeat issue was isolated in initial ReSaver++ inspection. This is **not** proof that defeat scenarios or bridge recovery work.

ReSaver baseline (6.53 save): about **191,218 script instances**, **365 missing spawned-object instances**, **11 suspended stacks** (Animated Carriage-related), zero queued unbinds. First 7.00 save: about **191,427 instances**, **380 missing**, **11 suspended**; after a separate *experimental cleaned-copy* load, bathing and cell changes: about **191,269 instances**, **22 missing** and no suspended stacks observed. These data are **time-dependent snapshots**, not evidence of a Naked Defeat regression or proof that cleaning helped. Preserve original saves; do not treat ReSaver cleanup as required for this upgrade. Some missing ActorBase references were still held by `FWAbilityBeeingFemale`; attribution of their creation remains unverified.

### Mandatory first live tests — PENDING

1. Confirm Naked Defeat MCM registration and dependency indicators, especially **Papyrus Ini Manipulator** and SLATE, and register the new Action Log.
2. With Acheron Bridge, **Defeat on Bleedout must be 0** to avoid duplicate handlers. Confirm Acheron handling enabled. Keep `IndecencyRapeProb = 0` until the legacy missing-quest path is rechecked specifically in 7.00; do not assume the 6.52 result was retested.
3. Trigger a simple human enemy defeat **without follower**, check assailant classification, scenario start, end, controls restored and Acheron rescue/release.
4. Test repeated defeats, creature defeat, captivity / furniture escape, non-Escape-Crawl ending and save → quit → reload after a completed event.
5. Check Bathing in Skyrim Renewed both through its own shortcut and Naked Defeat Shift+K after defeat; compare watcher detection only if an issue arises.
6. Monitor new package behavior and search radius (Nymra confirms enemies converging from the scan radius is intentional); adjust in MCM/INI as appropriate.
7. Revisit bridge scripts and `nade_Sandbox` only if a reproducible failure warrants investigation.

**Verdict:** 7.00 **is ready for controlled gameplay testing**, not yet certified as fully validated on Rhiven's main save.

---

# Historical integration archive — Naked Defeat 6.50–6.52 (retain for reference)

> **Archived baseline only.** Following sections reflect what was true at the time of the 6.52 integration. References to “current”, mandatory Rhiven Fix, 6.52 filenames, record counts and old MCM settings must **not** override the current 7.00 guidance above.


> **Status: NAKED DEFEAT 6.52 CORE INTEGRATION VALIDATED — EXTENDED PLAYTESTING ONGOING**
>
> This guide documents the NEFARAM-Rhiven migration from the previous **Acheron + Practical Defeat Reanimated + Yamete Kudasai** stack to **Acheron + Naked Defeat 6.50 FULL + the current 6.52 incremental patch**.
>
> File structure, xEdit records, the available Papyrus sources, the Acheron Bridge and the corrective patches were audited. The earlier 6.51 core validation remains part of the test history. On 6.52, MO2/MCM exposure, the new hotkeys and robbery controls, Chest Quest Robbery and AudioTTS tracking were validated as described below. Follower defeat, untested branches, Chest Quest Robbery persistence across a full save/quit/reload cycle and final MCM tuning remain outside the validated set.

---

## 1. Target architecture

The migration keeps **Acheron** as the actual defeat framework and replaces the previous consequence stack with Naked Defeat.

### Previous NEFARAM defeat stack

Typical NEFARAM 17.3.x setup:

```text
Acheron
├─ Simple Recover
├─ Diary of Mine Extension
├─ Yamete Kudasai
└─ Practical Defeat Reanimated
```

Practical Defeat and Yamete Kudasai both add their own Acheron consequences and post-defeat logic.

### New Rhiven architecture

```text
Acheron
├─ Simple Recover
├─ Diary of Mine Extension
└─ Acheron - Naked Defeat Bridge
   └─ Naked Defeat 6.50 FULL + 6.52 patch
      └─ Naked Defeat - Rhiven Fix
```

Reference flow:

> **Acheron → Acheron - Naked Defeat Bridge → Naked Defeat**

Responsibilities:

- **Acheron**: defeat / bleedout framework.
- **Acheron - Naked Defeat Bridge**: forwards the defeated player and assailants to Naked Defeat.
- **Naked Defeat**: post-defeat scenes, consequences and recovery logic.
- **Naked Defeat - Rhiven Fix**: small xEdit corrective patch for four malformed records in Naked Defeat 6.50.
- **Simple Recover**: may remain active; it does not replace the main post-defeat consequence chain.
- **Diary of Mine Extension**: may remain active.

---

## 2. Baseline used for this integration

Validated against:

- **NEFARAM 17.3.8**
- Skyrim AE runtime **1.6.1170**
- Acheron **1.11.3**
- Naked Defeat **6.50 FULL + patch 6.52**
- Mod Organizer 2
- xEdit / SSEEdit **4.1.5f**
- Open Animation Replacer
- Pandora Behaviour Engine+

Dedicated test profile:

`Eleanor 17.3.8 - Naked Defeat`

The stable profile was not used for the first integration pass.

---

## 3. Files used

### Required

- `Naked Defeat 6-50 - FULL - (AE + SE).7z`
- patch incrémental **Naked Defeat 6.52**, installé après la 6.50 FULL
- traduction MCM compatible avec la **6.52**, installée après le patch 6.52 si elle est utilisée
- `Naked Defeat - EXTRA - Acheron Bridge (SE).zip`

Les textures **WhipMarks** sont déjà intégrées au paquet depuis la 6.50 ; aucun ancien ajout WhipMarks séparé ne doit écraser cette version.

### Optional OAR packages

- `Naked Defeat - EXTRA - OAR Crawl Animations V2.7z`
- `Naked Defeat - EXTRA - OAR Bowed Animations - fixed.7z`

The packages overlap heavily and must not be active together. For the current 6.52 playtest, Rhiven is using:

> **Crawl active / Bowed disabled**

This is a current preference/test choice, not an absolute technical requirement to use Crawl. Bowed remains a valid alternative when Crawl is disabled.

---

## 4. Rhiven Fix download

> ### Naked Defeat - Rhiven Fix
>
> **Download:** [Naked Defeat - Rhiven Fix.zip](NAKED-DEFEAT/Naked%20Defeat%20-%20Rhiven%20Fix.zip)

The ZIP is MO2-ready and contains:

```text
Naked Defeat - Rhiven Fix/
├─ Naked Defeat - Rhiven Fix.esp
└─ meta.ini
```

Do not merge this patch into the original Naked Defeat plugin. Keeping it as a small standalone override makes the fix reversible and easy to audit.

---

## 5. MO2 left-panel migration

### Keep enabled

- `Acheron - Death Alternative 1.11.3 - Rhiven`
- `Acheron - Sacrosanct Patch - Rhiven` if already part of the NEFARAM-Rhiven setup
- `Acheron - Simple Recover`
- `Acheron - Diary of Mine Extension`
- `Naked Defeat 6.50 FULL - Rhiven`
- `Naked Defeat 6.52 patch - Rhiven`
- the compatible Naked Defeat MCM translation, if used
- `Naked Defeat - Rhiven Fix`
- `Naked Defeat - EXTRA - Acheron Bridge (SE) - Rhiven`
- `Naked Defeat - EXTRA - OAR Crawl Animations V2 - Rhiven`

### Disable

- `YameteKudasai`
- `Practical Defeat Reanimated`
- `Practical Defeat Reanimated Voicepack`
- `Naked Defeat - EXTRA - OAR Bowed Animations fixed - Rhiven`

Important:

> Disable the **entire YameteKudasai MO2 mod**, not only `YameteKudasai.esp`.

Yamete Kudasai ships Acheron consequence YAML files. Leaving those files active while removing only the ESP may cause Acheron to keep trying to resolve YK consequences against a missing plugin.

### Suggested left-panel block

```text
Acheron - Death Alternative 1.11.3 - Rhiven
Acheron - Sacrosanct Patch - Rhiven
Acheron - Simple Recover
Acheron - Diary of Mine Extension
YameteKudasai - DISABLED vs Naked Defeat
SMUTbooks_SE
Naked Defeat 6.50 FULL - Rhiven
Naked Defeat 6.52 patch - Rhiven
Naked Defeat MCM translation compatible with 6.52 - Rhiven
Naked Defeat - Rhiven Fix
Naked Defeat - EXTRA - Acheron Bridge (SE) - Rhiven
Naked Defeat - EXTRA - OAR Crawl Animations V2 - Rhiven
Naked Defeat - EXTRA - OAR Bowed Animations fixed - DISABLED vs Crawl
Practical Defeat Reanimated - DISABLED vs Naked Defeat
```

The exact separator/category is not critical. Keeping the Naked Defeat block together is recommended for maintenance.

---

## 6. Plugin load order

The Rhiven integration reuses the **former Practical Defeat location** in the plugin order instead of inserting Naked Defeat near the top of the Acheron framework stack.

Current tested placement:

```text
SLNights.esp
Naked Defeat.esp
Naked Defeat - Rhiven Fix.esp
Acheron - Naked Defeat Bridge.esp
BaboInteractiveDia.esp
```

The important internal order is:

> **Naked Defeat.esp → Naked Defeat - Rhiven Fix.esp → Acheron - Naked Defeat Bridge.esp**

Reasoning:

- the Rhiven Fix must load after Naked Defeat so its four corrected records win;
- the Acheron Bridge is an integration layer and can safely load after the base plugin and corrective patch;
- the three plugins were validated together in this order.

Do not use automatic LOOT sorting blindly on a finalized NEFARAM instance.

---

## 7. Why Practical Defeat is disabled

Practical Defeat and Naked Defeat are both full post-defeat consequence systems for Acheron.

Their responsibilities overlap heavily:

- player defeat handling;
- stripping / theft;
- SexLab scenes;
- followers;
- recovery;
- struggle / post-defeat states;
- possible slavery / capture outcomes.

Running both would make it difficult to know which consequence system owns a defeat event.

For the Rhiven migration:

> **Practical Defeat Reanimated and its voicepack are disabled.**

If the in-game Naked Defeat smoke test passes, Practical Defeat will be considered superseded in this build.

Keep it installed only as rollback until validation is complete.

---

## 8. Why Yamete Kudasai is disabled

Yamete Kudasai is not merely a small NPC utility. Its scripts and Acheron consequence files cover many of the same defeat domains as Naked Defeat:

- Acheron player defeat consequences;
- humanoid assaults;
- creature assaults;
- surrender;
- SexLab scenes;
- stripping and robbery;
- followers;
- blackout / relocation;
- recovery;
- Simple Slavery handoff;
- NPC defeat consequences;
- Hunter's Pride actions.

The official-style Acheron consequence YAML shipped with YK can participate in Acheron's consequence selection.

That means leaving YK enabled while testing the Naked Defeat bridge may result in:

> one defeat being routed to Naked Defeat and another being routed to Yamete Kudasai.

This would make the bridge appear unreliable even if it is working correctly.

Community troubleshooting reports also explicitly identify **Yamete Kudasai + Naked Defeat** as an incompatible defeat-stack combination and recommend using **Acheron + Naked Defeat Bridge** instead.

Rhiven decision:

> **Yamete Kudasai is fully disabled for this architecture.**

A theoretical future reintroduction only for niche Hunter's Pride / NPC-defeat features would require YK Hostile and Surrender consequences to be neutralized. That is not part of the current Rhiven configuration.

---

## 9. Acheron Bridge audit

Plugin:

`Acheron - Naked Defeat Bridge.esp`

xEdit result:

- **3 processed records**
- **0 errors**

The bridge quest contains:

- `PlayerRef`
- `Assailant01`
- `Assailant02`
- `Assailant03`
- `Assailant04`
- `Assailant05`
- `Assailant06`

The bridge script registers a short update and then sends:

`StartNakedDefeatExternal`

with up to six assailants before stopping itself.

This confirms that the bridge is a lightweight adapter rather than a second defeat framework.

Static verdict:

> **VALIDATED**

---

## 10. Naked Defeat 6.50–6.52 xEdit and Papyrus audit

The original 6.50 baseline contained approximately **798 records**.

The initial xEdit Check for Errors reported 18 error/warning groups.

Those results were audited individually rather than cleaned automatically.

### 10.1 Records corrected by the Rhiven Fix

The corrective patch contains only four intended overrides:

- `nade_WristChains_L`
- `nade_WristChains_R`
- `nade_BoneMace`
- `nade_Stick`

#### Wrist chains

Both ARMA records contained two invalid entries under `Additional Races`.

Those entries were REFR records pointing to placed cave balcony references rather than RACE records.

The Rhiven Fix removes only those invalid entries.

#### Wooden Stick / Bone Cudgel

Both WEAP records contained malformed:

`CRDT - Critical Data > Effect`

with zero bytes of data.

Copying the records as overrides caused xEdit to normalize the field correctly to:

`NULL - Null Reference [00000000]`

No additional weapon changes were made.

### 10.2 Rhiven Fix validation

`Naked Defeat - Rhiven Fix.esp`

Check for Errors:

- **5 processed records**
- **0 errors**

Static verdict:

> **VALIDATED**

---

### 10.3 Preserved 6.51 continuity history

The 6.51 plugin contains **800 records** and reports the same 18 xEdit error/warning groups that were reviewed rather than automatically cleaned. The Rhiven Fix still contains **5 records / 0 errors**, and the Acheron Bridge remains at **3 records / 0 errors**.

The 6.51 archive ships changed compiled `.pex` files without matching sources. Papyrus validation therefore combines:

- source-level inspection of the available 6.50 scripts and the Bridge;
- VMAD and record cross-checks in the 6.51 plugin;
- in-game confirmation of the paths that matter to the integration.

This supports the following conclusions without overclaiming a full 6.51 decompilation:

- the missing Civilian Rape quest remains protected by `IndecencyRapeProb = 0`;
- old whip packages and old follower crucifixion scenes remain documented and untouched because available sources show inactive/disabled paths;
- the Acheron handoff and recovery paths are confirmed functionally by the 6.51 tests;
- historical warnings are not reclassified as fixed merely because core gameplay passed.

A separate `Naked Defeat - Synthesis Fix.esp` was created to restore the `nade_Stick` CRDT correction after `Synthesis_1.esp`. Its final explicit Check for Errors result was not part of the received test evidence and therefore remains pending.

This 6.51 result is retained as useful history. It is no longer the current patch baseline.

### 10.4 Current continuity audit for 6.52

The 6.52 `Naked Defeat.esp` contains **1228 records** and reports **18 errors** in xEdit Check for Errors. The higher record count does not invalidate the earlier audit decisions: the error set was reviewed rather than cleaned automatically.

The following corrective plugins remain required:

- `Naked Defeat - Rhiven Fix.esp` for `nade_Stick`, `nade_BoneMace`, `nade_WristChains_R` and `nade_WristChains_L`;
- `Naked Defeat - Synthesis Fix.esp`, loaded after `Synthesis_1.esp`, so Synthesis does not reintroduce the malformed `nade_Stick` CRDT value.

The 6.52 archive contains only:

- `Naked Defeat.esp`;
- compiled Papyrus scripts (`.pex`);
- Papyrus sources (`.psc`).

It contains no behavior or animation output requiring Pandora. Therefore **the 6.52 patch itself does not require a Pandora rerun**. This is separate from the one-time Pandora regeneration already required when Yamete Kudasai was removed from the defeat stack.

The 6.52 inspection also confirms:

- `nade_CrimeEffect` property `qst2` still points to the missing Civilian Rape quest, so `IndecencyRapeProb = 0` remains mandatory;
- `nade_WhipAction_01` and `nade_WalkTo_01` remain invalid legacy whipping packages and are intentionally not patched;
- the old follower `crux`, `crux2` and `crux3` scenes remain malformed/legacy and are intentionally left intact;
- the four Rhiven Fix overrides remain necessary;
- the post-Synthesis protection for `nade_Stick` remains necessary.

---

## 11. Naked Defeat records intentionally left untouched

Several xEdit warnings appear to belong to old, disabled or abandoned internal architecture.

They are documented but not modified without an actual reproducible in-game symptom.

### CaptureQuest Vehicle alias

`nade_CaptureQuest` contains a broken Create Reference alias targeting a missing alias ID.

Current source inspection shows the active logic using another vehicle path instead.

### Old whip packages

`nade_WhipAction_01` and `nade_WalkTo_01` reference a missing owner quest.

Current whip source logic does not appear to rely on those obsolete packages.

### Old follower crucifixion scenes

Several `crux`, `crux2`, `crux3` scene records are structurally malformed.

Their calls are disabled / commented in the current Papyrus sources.

One `cruxSAVE` record is clearly a development backup and has no active references.

### Empty dialogue branch

`nade_TalkQuestNewBranch0` has a NULL Starting Topic.

It is an unreferenced empty dialogue branch and is left untouched.

Rhiven policy:

> **Do not "clean" VMAD, scene or quest warnings merely because xEdit reports them.**
>
> Only patch a record when current code, references or gameplay demonstrate that it is actively broken.

---

## 12. Important Naked Defeat 6.52 issue — Civilian Rape

This is the main functional issue found during the static audit.

`nade_CrimeEffect` contains a VMAD property:

`qst2`

pointing to a missing quest FormID.

Source inspection identifies `qst2` as the:

> **Civilian Rape Quest**

The property and its missing target remain present in Naked Defeat 6.52.

Related orphan records also point to the missing quest.

### Required Rhiven setting

In the Naked Defeat MCM:

> **Set `IndecencyRapeProb = 0`.**

Do not attempt to reconstruct the missing quest from old sources.

This setting is considered mandatory for the current Rhiven integration unless a future Naked Defeat release restores or replaces that subsystem.

---

## 13. OAR integration

### OAR Crawl Animations V2

The package structure is valid and its OAR conditions are scoped to Naked Defeat.

It is currently active in the Rhiven 6.52 playtest.

### OAR Bowed Animations - fixed

The Bowed package uses the same Naked Defeat OAR area and overwrites a large portion of Crawl's locomotion files.

Its condition uses:

- `IsInFaction`
- `Naked Defeat.esp`
- FormID `05AFF`

with a very high OAR priority.

This limits the locomotion replacement to the intended Naked Defeat state rather than globally replacing player movement.

The two packages must not be enabled together because they compete for the same locomotion replacements. Current Rhiven test preference:

> **Crawl active — Bowed disabled**

This is not an absolute technical requirement to use Crawl. It records the current test choice; Bowed can be selected instead as long as Crawl is disabled.

No Pandora generation is required merely because these OAR replacement files are installed.

---

## 14. Pandora regeneration

A Pandora regeneration **is required for this migration** because Yamete Kudasai is removed from the active stack and YK contains animation / behavior assets and an FNIS list.

After disabling Yamete Kudasai:

1. confirm the correct MO2 profile is active;
2. run Pandora Behaviour Engine+;
3. rebuild the current animation output;
4. keep the result in the existing dedicated `Pandora Output` mod;
5. verify no blocking generation error.

The reason for this run is the removal of YK behavior content, not the Naked Defeat OAR packs themselves.

The incremental **6.52 patch contains only ESP, PEX and PSC files**. Updating from 6.51 to 6.52 therefore does **not** require another Pandora run.

---

## 15. Acheron bleedout and recovery — critical test point

A defeat mod working correctly with Acheron must not only launch a scene; it must also correctly release the player from the Acheron defeated / pacified state.

The current Naked Defeat sources include Acheron shutdown / recovery logic using functions such as:

- `RescueActor`
- `ReleaseActor`
- Acheron processing disable / enable handling

This is consistent with how other Acheron consequences such as Yamete Kudasai and Practical Defeat manage their own start/end sequence.

Therefore one of the most important in-game tests is:

> **Does the player leave Acheron bleedout cleanly when Naked Defeat ends?**

Also verify that assailants are no longer incorrectly pacified once the sequence is complete.

A successful animation alone is **not** sufficient validation.

---

## 16. Required in-game smoke test

Use a disposable test save / dedicated test profile.

### Before testing

> **First launch:** enable Naked Defeat in its MCM before configuring hotkeys. If the mod itself is not enabled, key rebinding may appear not to work.

- [ ] `YameteKudasai` disabled in MO2
- [ ] `YameteKudasai.esp` absent from active plugins
- [ ] `Practical Defeat Reanimated` disabled
- [ ] `Practical Defeat.esp` absent from active plugins
- [ ] Practical Defeat voicepack disabled
- [ ] exactly one locomotion option active: current Rhiven test uses OAR Crawl
- [ ] OAR Bowed disabled while Crawl is active
- [ ] Naked Defeat Rhiven Fix active
- [ ] Acheron Bridge active
- [ ] Pandora regenerated successfully
- [ ] `IndecencyRapeProb = 0`

### Test cases

- [ ] defeat by humanoid
- [ ] defeat by creature
- [ ] defeat with follower involved
- [ ] Naked Defeat scene starts through Acheron
- [ ] correct assailants are passed to Naked Defeat
- [ ] scene completes
- [ ] player exits Acheron bleedout
- [ ] player controls return normally
- [ ] assailants are released / behave normally afterwards
- [ ] stripping works as expected
- [ ] theft / inventory consequences work as expected
- [ ] no permanent pacification
- [ ] no permanent bleedout
- [ ] no stuck animation state
- [ ] save after a completed defeat event
- [ ] exit Skyrim completely
- [ ] reload the save
- [ ] verify normal gameplay after reload

### Additional useful cases

- [ ] test more than one defeat in the same session
- [ ] test an indoor defeat
- [ ] test an outdoor defeat
- [ ] test a defeat close to cell transition
- [ ] test after a normal combat where the player does **not** get defeated

---

## 17. Pass / fail criteria

### PASS

The migration may be considered gameplay-validated when repeated defeats consistently follow:

> **Acheron → Acheron Bridge → Naked Defeat**

and:

- no Practical Defeat consequence appears;
- no Yamete Kudasai consequence appears;
- Naked Defeat starts reliably;
- recovery from Acheron works;
- no permanent actor state remains;
- save/reload remains stable after completed defeat events.

### FAIL / investigate

Do not finalize the migration if any of these are reproducible:

- player remains in bleedout;
- controls never return;
- Acheron remains disabled globally;
- assailants remain permanently pacified;
- defeat event does not route to Naked Defeat;
- bridge fires but Naked Defeat never starts;
- repeated defeats stop working;
- save/reload breaks the consequence chain.

---

## 18. Rollback

Until in-game validation is complete:

- keep `YameteKudasai` installed but disabled;
- keep `Practical Defeat Reanimated` installed but disabled;
- keep the Practical Defeat voicepack installed but disabled;
- keep the unused OAR alternative installed but disabled;
- keep MO2 left-panel and plugin-order backups.

If Naked Defeat fails the smoke test, restore the previous defeat stack rather than modifying the original Naked Defeat plugin destructively.

---

## 19. Current validation status

### Verified

- [x] Naked Defeat 6.50 installed on dedicated test profile
- [x] main plugin audited in xEdit
- [x] malformed wrist-chain Additional Races identified
- [x] malformed WEAP CRDT fields identified
- [x] Rhiven Fix created
- [x] Rhiven Fix: **0 xEdit errors**
- [x] Acheron Bridge inspected
- [x] Acheron Bridge: **0 xEdit errors**
- [x] bridge Papyrus flow inspected
- [x] Naked Defeat OAR packages inspected
- [x] Bowed vs Crawl conflict understood
- [x] Yamete Kudasai scripts reviewed
- [x] Yamete Kudasai Acheron consequence YAML reviewed
- [x] Practical Defeat overlap identified
- [x] Civilian Rape missing-quest issue identified
- [x] safe MCM workaround defined: `IndecencyRapeProb = 0`
- [x] final plugin relative order defined
- [x] deterministic test architecture defined

### Preserved Naked Defeat 6.51 validation history

- [x] 6.51 incremental patch installed over 6.50 FULL
- [x] 6.51 plugin audited in xEdit
- [x] Rhiven Fix continuity confirmed
- [x] Acheron Bridge handoff tested
- [x] humanoid defeat test
- [x] creature defeat test
- [x] bleedout recovery validation
- [x] repeated-event validation
- [x] save / exit / reload validation
- [x] furniture escape flow validated with timed Space presses and progress messages

### Naked Defeat 6.52 validation

- [x] 6.52 incremental patch installed over 6.50 FULL
- [x] MO2 and the MCM display version **6.52** after activation
- [x] `Naked Defeat.esp` audited in xEdit: **1228 records / 18 errors**
- [x] `Naked Defeat - Rhiven Fix.esp` still required for `nade_Stick`, `nade_BoneMace`, `nade_WristChains_R` and `nade_WristChains_L`
- [x] `Naked Defeat - Synthesis Fix.esp` still required after `Synthesis_1.esp` to protect `nade_Stick`
- [x] `IndecencyRapeProb = 0` remains mandatory because `nade_CrimeEffect.qst2` still targets the missing Civilian Rape quest
- [x] legacy whipping packages and malformed follower crux scenes reviewed and intentionally left unpatched
- [x] new `Resist` and `Progress` hotkeys visible
- [x] new robbery options visible
- [x] Chest Quest Robbery: chest spawn validated InGame
- [x] Chest Quest Robbery: inventory transfer validated InGame
- [x] Chest Quest Robbery: item recovery validated InGame
- [x] AudioTTS tracking validated InGame
- [x] 6.52 content checked: ESP + PEX + PSC only, so no Pandora rerun required for this patch
- [ ] Chest Quest Robbery persistence with an active chest across save → full Skyrim exit → reload
- [ ] follower defeat test
- [ ] individual validation of every untested 6.52 feature
- [ ] final Check for Errors result for the Synthesis Fix
- [ ] final MCM tuning during the final playthrough
- [ ] final verdict for rare edge cases in the stable profile

### Known minor observations

- **Bathing in Skyrim / Golden Shower:** the Naked Defeat handoff successfully triggers the Bathing in Skyrim cleaning animation, but dirt/cum visual layers may not always be removed correctly depending on the setup. This is currently treated as non-blocking.
- After fully disabling **Yamete Kudasai** and **Practical Defeat**, old empty MCM entries may remain registered in an existing save. A SkyUI MCM refresh can remove those stale menus:

```text
setstage ski_configmanagerinstance 1
```

---

## 20. Final 6.52 validation boundary

This integration is **not an untested theory**.

The following parts have already been checked and validated:

- file structure;
- plugin structure;
- xEdit errors;
- bridge quest / aliases;
- bridge Papyrus behavior;
- Naked Defeat source references;
- Acheron interaction logic;
- Yamete Kudasai overlap;
- Practical Defeat overlap;
- OAR scoping;
- corrective Rhiven patch.

However:

> **Naked Defeat 6.52 is the current patch on the 6.50 FULL base. Its new UI exposure, Chest Quest Robbery core flow and AudioTTS tracking have been validated InGame; extended playtesting is still ongoing.**

The Chest Quest Robbery validation covers chest creation, transfer of the player's belongings and recovery of those items. It does **not** include a save → full Skyrim exit → reload while the robbery chest is still active, and this guide must not imply otherwise.

The current build is suitable for continued playtesting, while final balancing and less common edge cases remain subject to adjustment during the final playthrough.

For users who want maximum safety, keep a copy of the original NEFARAM defeat stack and do the first tests on a cloned MO2 profile.

---

## 21. Rhiven target state after core validation

With the core in-game validation passed, the intended defeat stack is:

```text
Acheron - Death Alternative 1.11.3 - Rhiven
Acheron - Sacrosanct Patch - Rhiven
Acheron - Simple Recover
Acheron - Diary of Mine Extension
Naked Defeat 6.50 FULL - Rhiven
Naked Defeat 6.52 patch - Rhiven
Naked Defeat MCM translation compatible with 6.52 - Rhiven
Naked Defeat - Rhiven Fix
Naked Defeat - EXTRA - Acheron Bridge (SE) - Rhiven
Naked Defeat - EXTRA - OAR Crawl Animations V2 - Rhiven
```

with these remaining disabled:

```text
YameteKudasai
Practical Defeat Reanimated
Practical Defeat Reanimated Voicepack
Naked Defeat - EXTRA - OAR Bowed Animations fixed
```

Final target architecture:

> **Acheron for defeat detection and actor state → Naked Defeat for consequences and scenes.**
