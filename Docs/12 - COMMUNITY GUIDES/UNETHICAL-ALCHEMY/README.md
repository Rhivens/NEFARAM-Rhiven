# Unethical Alchemy 1.0.0 — NEFARAM Community Guide

> **Baseline validated:** NEFARAM 17.3.8  
> **Status:** structural correction validated; functional gameplay validation still required  
> **Recommended patch:** [`Unethical Alchemy - Rhiven Fix.zip`](Unethical%20Alchemy%20-%20Rhiven%20Fix.zip)

Unethical Alchemy adds a small adult alchemy encounter at **Heartwood Mill**. Its content includes a new alchemy trainer and SexLab partner, an alchemy lore/skill book, the long-lasting **Joy** effect, and abortifacient-themed roleplay content.

This guide describes a generic integration into NEFARAM. It deliberately uses relative load-order relationships: do not copy another user's MO2 separators, profile names, or absolute plugin positions.

## Important limitations

- The mod author documents pregnancy functionality specifically for **Hentai Pregnancy**.
- Treat that functionality as **unsupported and unverified with every other fertility framework unless it has been tested explicitly**.
- This guide does **not** claim compatibility with Beeing Female or any other fertility framework.
- The author reports **Deviously Accessible** and the older **Unethical Illusion** as incompatible. Do not enable either alongside Unethical Alchemy.
- Technical validation of the supplied fix does not prove quest, SexLab, Joy, fertility, or save-game behavior. Test those systems in game.

## Installation and relative load order

1. Start from a backed-up or cloned NEFARAM setup.
2. Install **Unethical Alchemy 1.0.0** and follow the original mod page for its requirements.
3. Enable `unethicalalchemy.esp` after all of its required masters.
4. Install the supplied [`Unethical Alchemy - Rhiven Fix.zip`](Unethical%20Alchemy%20-%20Rhiven%20Fix.zip) as a separate mod.
5. Enable `Unethical Alchemy - Rhiven Fix.esp` and make it load **after** `unethicalalchemy.esp`.
6. Keep later NEFARAM conflict-resolution or generated plugins in their established relative order. Review their winning records rather than moving Unethical Alchemy to an arbitrary absolute position.
7. Check the final Heartwood Mill cell, NPC, dialogue, alchemy, and magic-effect winners in xEdit before testing.

The audited archive contained scripts, sound, source files, and `unethicalalchemy.esp`. No DLL/SKSE binary, OAR/Pandora animation payload, or MO2 file conflict was identified during the validated installation, but users should still inspect their own final setup.

## Recommended compatibility and quality patch

`Unethical Alchemy - Rhiven Fix.esp` is a deliberately minimal override.

The original NPC record for **Agryn Gaering** contains one AI package reference whose target record does not exist in the loaded plugin/master set. The patch:

- removes only that orphaned package reference;
- preserves Agryn Gaering's seven valid AI packages;
- preserves the rest of the NPC data;
- leaves the original mod plugin untouched.

The published patch passes xEdit **Check for Errors** with:

> **2 processed records / 0 errors**

If another plugin also edits Agryn Gaering, inspect the final NPC winner and merge only the required data. Do not forward the entire record blindly.

## Confirmed XCWT finding — do not apply the old deletion advice

An older LoversLab report described `XCWT - Water = NULL` issues in these cells:

- `[CELL:0000BCFB]` in Tamriel 32,-25;
- `HeartwoodMillExterior [CELL:0000BCDA]` in Tamriel 32,-24.

Those issues **do not reproduce in the current NEFARAM 17.3.8 stack**. In the validated load order, both cells contain valid `XCWT` references to the `RiverWaterFlow` `WATR` record.

**Do not delete either XCWT field based on the old report.** Removing a currently valid water reference would create a new error rather than fix one. Always inspect the final winning records in your own load order before changing a CELL.

## Compatibility checks

### Heartwood Mill

Inspect the final records for:

- CELL and placed-reference edits;
- Agryn Gaering's AI packages and pathing;
- navmesh-sensitive changes;
- ownership or faction changes;
- dialogue conditions tied to the mill;
- landscape or worldspace overrides, if present.

In game, enter and leave Heartwood Mill repeatedly, save and reload there, and observe Agryn's daily movement. Stop testing if pathing, doors, or cell transitions fail consistently.

### Alchemy overhauls

NEFARAM may include alchemy changes such as Apothecary, Alchemy Plus, or Alchemy Recipe Expansion. Review conflicts involving:

- ingredients and ingestibles;
- Joy and abortifacient magic effects;
- keywords, values, magnitudes, and durations;
- recipes or leveled lists;
- the lore/skill book;
- trainer and NPC records.

Confirm in game that recipes are not duplicated or broken and that item effects still match their descriptions.

### SexLab and arousal

The source material confirms adult scenes but does not fully document the implementation. Verify:

- that all requirements from the original mod page are installed;
- that the intended dialogue starts a valid scene;
- whether specific animation tags are requested;
- whether scenes are consensual, player-controlled, or forced as expected;
- whether Joy changes SexLab statistics, arousal, orgasm/satisfaction, or an independent quest state;
- that autonomous SexLab systems do not interrupt the encounter.

Test against the SexLab and arousal systems active in your own NEFARAM setup, especially SLO Aroused NG and any dialogue, survival, approach, or defeat systems that can start competing scenes.

### Joy behavior

Joy is described as making ordinary sex feel less satisfying for approximately **400 hours**. Its exact storage and expiration behavior must be verified in game.

On a disposable save:

1. trigger or consume Joy through the intended encounter;
2. confirm the expected scene and post-Joy state;
3. run a normal SexLab scene and observe the intended difference;
4. save, quit, reload, and confirm the state persists correctly;
5. advance time and confirm that the state expires cleanly;
6. check for stuck effects, quest state, or repeated script errors.

Do not assume that the stated duration or the meaning of "less satisfying" is compatible with every arousal configuration until observed.

### Pregnancy and abortifacient content

The documented functional target is **Hentai Pregnancy**. Without that framework, treat the abortifacient as roleplay-only unless a separate, specifically tested compatibility solution proves otherwise.

Verify that the item or dialogue remains safe, produces no persistent script errors, and does not alter another fertility framework's state incorrectly. Do not use this guide as evidence of Beeing Female compatibility.

## Practical test plan

Use a disposable save, never the save intended for a long playthrough.

- Follow Elgrim's intended introduction path.
- Find Agryn Gaering at Heartwood Mill and observe his AI schedule.
- Test trainer, dialogue, and SexLab options.
- Obtain the alchemy lore/skill book.
- Exercise the full Joy persistence and expiration test above.
- Check Joy and abortifacient records under the active alchemy overhaul.
- Confirm that abortifacient content is harmless when Hentai Pregnancy is absent.
- Enter and exit Heartwood Mill several times, then save and reload there.
- Run xEdit Check for Errors on the relevant plugin set after settling the final order.

## Troubleshooting

### Agryn does not move or follow his schedule

- Confirm that `Unethical Alchemy - Rhiven Fix.esp` loads after `unethicalalchemy.esp`.
- Inspect the final Agryn Gaering NPC record and verify that the seven valid packages remain.
- Check for a later NPC overhaul that replaces his package list.
- Test outside any currently running quest or autonomous scene.

### Heartwood Mill has water, pathing, or cell problems

- Inspect the final CELL and placed-reference winners in xEdit.
- Do **not** delete `XCWT` from `0000BCFB` or `0000BCDA`; the validated 17.3.8 stack points both to `RiverWaterFlow`.
- Check location overhauls and navmesh-sensitive conflicts separately.
- Reproduce the issue on a disposable save before making a patch.

### Joy has no effect or never clears

- Confirm that the intended encounter completed and that all original requirements are active.
- Check active magic effects, quest state, and Papyrus logs for repeated errors.
- Test save/reload and time advancement without other autonomous scenes running.
- Roll back if the state remains stuck; do not continue a permanent save with an unverified persistent effect.

### The SexLab scene does not start

- Verify the original mod's requirements and the health of the existing SexLab installation.
- Confirm that another approach, survival, dialogue, or defeat system is not occupying the actor.
- Test with a minimal set of competing autonomous systems on a disposable save.

### Abortifacient behavior is unexpected

- Stop using the item on that save.
- Treat non-Hentai Pregnancy behavior as unsupported.
- Restore the pre-test save rather than trying to repair a fertility state mid-playthrough.

## Safe rollback

If the integration fails validation:

1. close the game;
2. disable the base mod and its Rhiven fix together;
3. discard every save created after enabling or exercising the mod;
4. restore the backed-up NEFARAM profile/order if it changed;
5. resume from the untouched pre-installation save.

Do not uninstall a scripted quest mod mid-playthrough and then continue the same developed save. A clean rollback means returning to a save from before the mod was present.

## Validation status

Validated:

- targeted Agryn Gaering package correction;
- preservation of all seven valid AI packages;
- patch Check for Errors: **2 records / 0 errors**;
- reported XCWT NULL condition at `0000BCFB` and `0000BCDA`: **not reproduced** in the current NEFARAM 17.3.8 stack;
- both validated XCWT fields reference `RiverWaterFlow` and must not be deleted.

Still requires user-side functional validation:

- Agryn's pathing and daily AI at Heartwood Mill;
- introduction, dialogue, training, and SexLab flow;
- Joy implementation, persistence, gameplay effect, and expiration;
- behavior under the active alchemy overhaul;
- safe roleplay-only behavior of abortifacient content when Hentai Pregnancy is absent;
- compatibility with any fertility system other than the specifically documented Hentai Pregnancy target.
