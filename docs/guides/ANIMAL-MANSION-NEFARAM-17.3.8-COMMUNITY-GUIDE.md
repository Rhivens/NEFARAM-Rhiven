# Animal Mansion Reborn 1.8 — NEFARAM 17.3.8 Community Guide

> ⚠️ **IMPORTANT — ADVANCED MODPACK MODIFICATION**
>
> This integration is **not a simple plug-and-play installation**.
>
> A dedicated **Rhiven compatibility patch is provided with this guide**, but integrating Animal Mansion Reborn into NEFARAM still requires significant changes to the modpack and a good understanding of Skyrim modding.
>
> The installation involves load-order management, compatibility patches, Synthesis regeneration, xEdit validation and a full LOD regeneration workflow with xLODGen, TexGen and DynDOLOD.
>
> This guide is therefore intended for users who already have **some experience modifying large Skyrim modlists** and who are comfortable troubleshooting conflicts and generated outputs.
>
> Always work from a backup or cloned NEFARAM instance before starting the integration.
>
> If you are not comfortable using xEdit and regenerating LODs, keeping the original NEFARAM setup is strongly recommended.

> **Baseline:** official NEFARAM 17.3.8
> **Current status:** **TECHNICALLY INTEGRATED — LOD WORKFLOW COMPLETE — GAMEPLAY VALIDATION DEFERRED TO A NORMAL/DEFINITIVE PLAYTHROUGH**
>
> This community integration has passed its technical checks, completed the full LOD workflow and passed generated-output visual inspection. Broader quest, navigation, scene and save-game validation is intentionally deferred to a normal/definitive playthrough.

## Quick Setup / TL;DR

1. Start from an unmodified **official NEFARAM 17.3.8** baseline.
2. Install **Animal Mansion Reborn 1.8** and its documented requirements.
3. Enable `Animal Mansion Reborn.esp`.
4. Keep `COTN -Falkreath AMR.esp` enabled.
5. Keep the supplied `AMR The Great Town of Shor's Stone Patch.esp` **enabled** alongside `COTN -Falkreath AMR.esp`.
6. Enable `Animal Mansion Reborn - Rhiven Patch.esp` after the Shor's Stone patch and the other plugins whose AMR conflicts it resolves. It complements the supplied compatibility patches; it does not replace them.
7. Keep Animal Mansion early enough for the established NEFARAM, Lux and generated-patch winners to retain their intended final values. Do not use personal MO2 separators or copy another user's absolute plugin positions.
8. Rerun **Synthesis** after the final plugin placement.
9. For this integration, rebuild generated LOD in this order: **xLODGen -> TexGen -> DynDOLOD**.
10. Confirm the generated outputs are enabled, then start Animal Mansion as described below.

The LOD workflow and generated-output visual inspection are complete. Broader gameplay validation will continue during a normal/definitive playthrough.

## Requirements and prerequisites

- **Official NEFARAM 17.3.8** as the baseline.
- **Animal Mansion Reborn 1.8**.
- All requirements documented by Animal Mansion Reborn 1.8. This guide does not add or guess at a separate dependency list.
- The supplied `COTN -Falkreath AMR.esp` compatibility patch.
- The supplied `AMR The Great Town of Shor's Stone Patch.esp` compatibility patch.
- `Animal Mansion Reborn - Rhiven Patch.esp`.
- MO2 and the existing NEFARAM tools used to regenerate Synthesis and LOD outputs.
- A normal/definitive playthrough for broader gameplay validation.

Before changing the profile, back up the MO2 left pane and plugin order. Preserve the existing generated outputs until the final plugin placement is settled.

## Installation and relative order

The exact separator names and absolute positions vary between installations. Use the following relationships rather than a personal load-order screenshot:

1. Install and enable **Animal Mansion Reborn 1.8**.
2. Place `Animal Mansion Reborn.esp` before the late NEFARAM environment, city, lighting and generated-patch layers where those later plugins already contain the correct final state.
3. Load `COTN -Falkreath AMR.esp` after its required masters and keep it active. It repositions AMR-specific markers and quest triggers for the COTN Falkreath geometry.
4. Load `AMR The Great Town of Shor's Stone Patch.esp` after its required masters and keep it active.
5. Load `Animal Mansion Reborn - Rhiven Patch.esp` after the active Shor's Stone patch and after the other records it is intended to merge or correct.
6. Preserve the established later Lux / NEFARAM winners where they already provide the correct environment state.
7. Regenerate Synthesis only after the AMR plugin set and compatibility patch placement are final.
8. Run the LOD tools only after Synthesis and the manual compatibility patch are in their intended final state.

The intended principle is simple: use load-order placement for conflicts that are already resolved correctly, and use the Rhiven patch only for the records that require an explicit merge. Do not broadly forward entire conflict groups into another patch.

## Rhiven Compatibility Patch — What it fixes

`Animal Mansion Reborn - Rhiven Patch.esp` is a minimal compatibility layer. Its xEdit **Check for Errors** result is:

> **21 processed records / 0 errors**

The patch:

- preserves the current MNC male and female Husky biped model paths;
- complements the active Shor's Stone compatibility patch in the final audited stack;
- restores the missing AMR dialogue INFO additions while retaining the final dialogue structure supplied by later winners;
- includes only the localized CELL adjustments required by the audited conflicts;
- avoids broad or blind forwarding of whole CELL or conflict groups.

The Rhiven patch does not replace either the COTN Falkreath patch or the supplied Shor's Stone patch, and it does not replace Synthesis or LOD generation. It was built and xEdit-validated with the Shor's Stone patch active.

## Optional AMR BodySlide addon

If you install the optional **AMR BodySlide addon**:

1. Keep NEFARAM on the **Zeroed Sliders** preset.
2. Enable **Build Morphs**.
3. Filter the outfit list for **AMR**.
4. Run **Batch Build** for the filtered AMR entries.
5. Ideally, direct the generated files to a dedicated MO2 output mod so they remain isolated and easy to manage.

A BodySlide-only rebuild changes meshes only. It does **not** require rerunning Synthesis, xLODGen, TexGen or DynDOLOD.

## Compatibility notes

### COTN Falkreath

`COTN -Falkreath AMR.esp` is required for this integration and must remain active. It passed xEdit Check for Errors with **0 errors** and contains functional AMR marker and trigger placement for the COTN layout. Its broader in-game validation is deferred to the normal/definitive playthrough.

### The Great Town of Shor's Stone

Keep `AMR The Great Town of Shor's Stone Patch.esp` active. The Rhiven patch was built and xEdit-validated with it active and is a complementary layer, not a reconstruction or replacement of the supplied patch.

Earlier audit concerns around NAVI / navmesh and door-link records remain useful technical cautions because those records are sensitive to the final settlement geometry. They were audited in the active final stack; broader NPC pathing, follower pathing and door-transition validation is deferred to the normal/definitive playthrough.

### MNC and Husky models

AMR's `HuskyBareAA [02018B35]` override restores the vanilla male Husky mesh and drops the MNC female assignment. The Rhiven patch preserves the MNC male and female biped model paths without performing a wider MNC merge.

### Dialogue

Later dialogue winners can omit AMR-added INFO entries. The Rhiven patch merges only the missing AMR additions into the final dialogue structure. Text differences caused by English strings overriding another language are translation issues, not compatibility fixes covered by this patch.

### Lux, NEFARAM and Synthesis winners

Later Lux, NEFARAM and Synthesis records should continue to win when they already contain the intended final environment state. Typical examples include CELL lighting, image space, fog, ambient data and other environment forwards. Do not duplicate those correct winners in the Rhiven patch.

## Generated outputs

The required order is:

1. settle the final AMR and compatibility-patch placement;
2. rerun **Synthesis**;
3. run **xLODGen**;
4. run **TexGen**;
5. run **DynDOLOD**;
6. inspect the generated terrain and object LOD in game.

The full chain is required for this integration because AMR contains exterior worldspace content and at least one visible `LAND` record under:

`WhiterunWorld -> WhiterunWindDistrict02`

Current documented state:

- Synthesis: complete;
- xLODGen: complete;
- TexGen: complete;
- DynDOLOD: complete;
- generated-output visual inspection: complete.

The complete generated-output chain and its visual inspection are finished.

## Starting Animal Mansion

1. Enter **Dead Man's Drink** in Falkreath.
2. Listen to the introductory conversation.
3. Speak to **Valga Vinicia**.

## Troubleshooting

### Shor's Stone NPC or follower pathing is broken

- Confirm that `AMR The Great Town of Shor's Stone Patch.esp` is active and that the Rhiven patch loads after it.
- Confirm that the Rhiven patch is enabled and loads after the records it corrects.
- Test NPC pathing, followers, doors and transitions on a disposable save.
- Stop validation if the problem is reproducible; do not mechanically forward NAVI / NAVM records into another patch as a quick fix.

### A door or transition is broken

- Check both sides of the transition and the associated teleport marker.
- Verify that the correct settlement and compatibility plugins are active.
- Treat Shor's Stone door links as navmesh-sensitive rather than as ordinary placement records.

### A Husky uses the wrong mesh

- Confirm that `Animal Mansion Reborn - Rhiven Patch.esp` wins the `HuskyBareAA [02018B35]` conflict.
- Verify that no later plugin restores AMR's older model assignment or removes the MNC female path.

### Expected AMR dialogue is missing

- Confirm that the Rhiven patch loads after the dialogue records it merges.
- Inspect whether another later plugin removes the AMR INFO entries from the final DIAL winner.
- Treat language-only string changes separately from compatibility behavior.

### Objects are missing nearby or at distance

- Confirm that Synthesis was rebuilt after the final plugin placement.
- Confirm that the full `xLODGen -> TexGen -> DynDOLOD` chain completed in that order.
- Inspect the final generated outputs before treating the issue as an AMR plugin problem.

### A modified cell repeatedly crashes

- Reproduce the issue on a disposable save.
- Check whether it occurs on entry, exit or only after quest activity.
- Treat a persistent CTD in an AMR-modified cell as a stop condition. The integration is not gameplay-valid while it remains reproducible.

## Advanced technical notes

The public patch is intentionally small. The audit found that many apparent AMR conflicts were already resolved correctly by later Lux, NEFARAM or Synthesis winners, so those records were not copied into the compatibility patch.

Useful reference points:

- `HuskyBareAA [02018B35]`: preserves the modern MNC male and female biped model paths.
- `DGCrimeForcegreetTopic [000267DE]`: final DIAL winner needs the missing AMR INFO additions.
- `DGCrimeWantedTopic [0002A37F]`: final DIAL winner needs the missing AMR INFO additions.
- `OfferServicesTopic [00076FBB]`: final DIAL winner needs the missing AMR INFO additions.
- Shor's Stone exterior door `REFR [000177DE]`: exposes an `XNDP - Navmesh Door Link` and is navmesh-sensitive; it must not be forwarded mechanically.
- `WhiterunWorld -> WhiterunWindDistrict02`: contains at least one visible AMR `LAND` record, which is why this integration uses the complete LOD chain.

The base `Animal Mansion Reborn.esp` also passed xEdit Check for Errors with **30,175 processed records / 0 errors**. That result and the Rhiven patch's **21 processed records / 0 errors** establish technical validation only; they do not prove quest, navigation, scene or save-game behavior in play.

## Status and release notes

**TECHNICALLY INTEGRATED — LOD WORKFLOW COMPLETE — GAMEPLAY VALIDATION DEFERRED TO A NORMAL/DEFINITIVE PLAYTHROUGH**

Completed:

- full conflict audit;
- base AMR xEdit Check for Errors;
- COTN Falkreath patch xEdit validation;
- minimal Rhiven compatibility patch creation and xEdit validation;
- Synthesis regeneration;
- xLODGen generation;
- TexGen generation;
- DynDOLOD generation;
- generated-output visual inspection.

Deferred:

- broader gameplay validation during a normal/definitive playthrough.

The integration is technically validated and LOD-complete. Gameplay validation remains intentionally deferred and should not be presented as complete until established through normal play.
