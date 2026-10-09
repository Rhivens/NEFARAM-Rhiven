# 13 - Pre-playthrough checklist

This checklist is the launch gate for the definitive **NEFARAM-Rhiven** playthrough.

Rule:

- everything under **Pre-install / Before New Game** must be completed, intentionally rejected, or explicitly moved to the post-install section before the real playthrough starts;
- everything under **Post-install / New Game** is checked only after the definitive character and save have been created.

---

## Pre-install / Before New Game

### Build completion

- [ ] Finish the NEFARAM-Rhiven customization pass.
- [ ] Review remaining tracked / candidate mods and either install, reject or defer them explicitly.
- [ ] Confirm the final MO2 separator structure and numbering.
- [ ] Refresh the final MO2 left-pane snapshot.
- [ ] Refresh the final plugin / load-order snapshot.

### Outfit integration

- [ ] **Decide Eleanor's definitive wardrobe workflow before starting the real playthrough:** compare `Outfit Gallery - Visual Outfit Manager - Rhiven` (managing outfits / real gear) versus `Fitting Room - Rhiven` (cosmetic transmog without adding real clothes), or deliberately retain both if they provide useful complementary functions.
  - Both mods are currently kept in MO2; **Outfit Gallery is only temporarily disabled for Fitting Room testing**, not removed.
  - Record which mod(s) should be active in the definitive profile; verify no competing shortcuts or overlapping equipment features.
  - Fitting Room 1.2.0 initial in-game check: FLICK/editor works from inventory with `N`, outfits such as Aether appear and preview on Eleanor; Menu Studio uses `The dressing room` + `The star dome`. Saving/applied appearance persistence and SexLab/Devious Devices undressing behavior remain unverified.
  - Keep `Leave my face alone` / `Freeform` / `All dyes unlocked` unless intentionally changed; check transmog suspension during scenes and avoid assuming that cosmetically worn pieces count as real equipment.

- [ ] Complete in-game visual / physics validation of the personal Eleanor outfit block.
- [ ] Audit added Eleanor outfits against the existing Advanced Nudity Detection / OSL / modesty keyword stack.
- [ ] Identify which personal outfits are already covered by existing KID rules.
- [ ] Create a dedicated Rhiven KID INI for missing outfit keywords instead of editing NEFARAM's original files.
- [ ] Validate representative outfit categories so reactions behave as expected.

### Translations

- [ ] Complete the French translation pass for added mods that need it.
- [ ] Review BFNG / FAR strings and menus.
- [ ] Review Simple Inn Bath / Xtended Stay if translation is useful or needed.
- [ ] Confirm no translation mod overwrites scripts or non-language assets unexpectedly.

### Fertility system preparation

- [ ] Confirm BFNG / FAR remain technically validated after the final build.
- [ ] Keep the intended definitive settings documented:
  - player pregnancy only;
  - NPC pregnancy disabled;
  - birth output = Gem;
  - BodyMorph profile = CBBE 3BA.
- [ ] Decide the planned creature-fertility policy before the final MCM session.
- [ ] If still needed, run one full pregnancy / birth validation on a disposable test save.
- [ ] Keep Inflation Framework NG as tracking-only unless a reproducible native BodyMorph coexistence problem appears.

### Gameplay / economy / survival

- [ ] Identify the MCM controlling inn-room prices.
- [ ] Align Simple Inn Bath cost with the chosen inn economy.
- [ ] Validate Xtended Stay with the final inn-price configuration.
- [ ] Review survival / hygiene interaction after all related mods are finalized.
- [ ] Confirm Bathing in Skyrim Renewed + Simple Inn Bath behavior in at least one inn.

### UI / controls preparation

- [ ] **Restore a clearly visible vanilla-style Skyrim crosshair before the definitive playthrough.**
  - Audit `Contextual Crosshair` first; disable or reconfigure it if it suppresses / shrinks the reticle.
  - Check crosshair-related settings in True Directional Movement, SmoothCam / its presets, and any HUD layer that can hide or replace the reticle.
  - Re-test `Better Third Person Selection - BTPS` with the final crosshair setup; keep BTPS only if object selection remains comfortable and predictable.
  - Validate in first person and third person: aiming, picking small objects, doors/containers, NPC activation, bows/spells.
  - Prefer a small Rhiven config/override over adding another crosshair mod if the vanilla reticle can be restored cleanly.
- [ ] **Paper map Find Location marker - Rhiven:** study a custom `map.swf` edit inspired by *Red-Circle In Paper Map* instead of overwriting the current UI stack with a third-party SWF.
  - Identify the winning `map.swf` in MO2 first.
  - Back up the winning SWF and inspect it with JPEXS Free Flash Decompiler.
  - Replace only the Find Location marker asset (red circle or custom Rhiven marker), avoiding ActionScript / class changes.
  - Package the edited SWF as a dedicated Rhiven UI override.
  - Validate map opening, Find Location, zoom, panning and general FWMF / Dear Diary Dark Mode compatibility in-game.
- [ ] Review all mods that add hotkeys.
- [ ] Prepare the final personal hotkey plan.
- [ ] Check for obvious hotkey conflicts before the real start.
- [ ] Confirm the final paper map / FWMF setup remains intact after all additions.

### Final technical pass

- [ ] Run Pandora after the last animation-related installation / update.
- [ ] Confirm Pandora finishes without blocking errors.
- [ ] Regenerate any final generated outputs that truly require a last pass.
- [ ] Clear / inspect MO2 Overwrite and move intentional generated files into dedicated output mods.
- [ ] Review xEdit for unexpected conflicts introduced by personal additions.
- [ ] Review the final heavy-plugin count.
- [ ] Enable `Cached Recursive Directory Walk` only when customization is considered stable, if still desired.
- [ ] Perform a final launch test from MO2.
- [ ] Perform a final load / save / reload sanity test on the temporary validation save.

### Final launch preparation

- [ ] Confirm no known blocking incompatibility remains.
- [ ] Confirm no major translation task remains.
- [ ] Confirm no required keyword / outfit-classification task remains.
- [ ] Confirm no mandatory generated-output pass remains.
- [ ] Confirm all pre-install tasks above are complete, intentionally rejected, or explicitly moved to the post-install section.

---

## Post-install / New Game

These tasks are intentionally performed only after the definitive playthrough has started.

### New game initialization

- [ ] Create the definitive new game from the intended NEFARAM starting point.
- [ ] Select the desired NEFARAM difficulty preset through MCM Recorder.
- [ ] Let all startup scripts / MCM registrations settle before final configuration.
- [ ] Make a clean early baseline save before heavy gameplay progression.

### Mega MCM session

- [ ] Perform the full MCM configuration session.
- [ ] **Enable Bathing in Skyrim Renewed (BiSR)** in its MCM; it is disabled by default.
- [ ] **Enable Private Needs - Orgasm (PNO)** in its MCM; it is disabled by default.
- [ ] Configure BFNG with the planned player-only / Gem / CBBE 3BA settings.
- [ ] Tune BFNG / Fill Her Up / Milk Mod Economy morph amplitudes conservatively.
- [ ] Configure the remaining gameplay / survival systems consistently with the selected difficulty.
- [ ] Finalize Wheeler hotkeys and layout.
- [ ] Finalize all other hotkeys.
- [ ] Resolve any hotkey conflicts found during real gameplay.
- [ ] Finalize HUD positioning once every HUD-capable mod is active.
- [ ] Save configuration presets through Settings Loader / MCM Recorder where supported.

### Early-game validation

- [ ] Verify Advanced Nudity Detection / OSL / modesty reactions with Eleanor's actual worn outfits.
- [ ] Verify Simple Inn Bath and Xtended Stay in normal gameplay with the final economy settings.
- [ ] Verify Bathing in Skyrim Renewed integration during normal play.
- [ ] Verify BFNG widgets and cycle state during normal play.
- [ ] Verify Wheeler / UI / map behavior in normal gameplay.
- [ ] Watch the first sessions for repeated errors or abnormal save growth.
- [ ] Test the TNTR trap ecosystem very early in the definitive playthrough: Bear Trap, Snare/QTE, OMNOMS Mimic, O.S.H.I.T and Watch Your Step.
- [ ] Verify TNTR interactions with Fill Her Up Baka, Devious Devices and Acheron / Practical Defeat before significant progression.
- [ ] **Riften / Bad Ends:** during the definitive Eleanor playthrough, disable the vanilla well that clips through the PAMA execution scaffold (console `disable` after positively identifying the well reference); re-check the scaffold area afterward.

### Lakeview Manor / Eleanor home

These checks wait until Lakeview is legitimately available in the real playthrough.

- [ ] Validate Lakeview Manor - As It Should Be.
- [ ] Check exterior placement.
- [ ] Check interior and cellar.
- [ ] Check storage, activators and lighting.
- [ ] Check CC Fishing compatibility.
- [ ] Check NPC navigation / follower behavior if relevant.
- [ ] Build the final in-world wardrobe / storage organization for Eleanor's clothes.

### Final post-start confirmation

- [ ] Confirm the definitive save can be saved, exited, reloaded and continued normally.
- [ ] Confirm no new blocking conflict appears after the first real gameplay sessions.
- [ ] Mark the NEFARAM-Rhiven build as **PLAYTHROUGH READY / ACTIVE**.

---

## Future / Optional backlog

Items here do **not** block the definitive playthrough.

- [ ] **Eleanor's Dressing Room (Menu Studio):** consider a custom backdrop / dressing-room scene after stabilization and FR translation; optional cosmetic project, not a launch blocker.
- [ ] **Outfit Gallery - Visual Outfit Manager:** study a possible patch allowing outfit pieces to be retrieved from one or more designated in-world wardrobe / storage containers instead of requiring Eleanor to carry the full wardrobe in her inventory.
- [ ] **RaceMenuAtelier - SKSE RM UI:** test it on the definitive New Game before actual play begins, ideally in the Skyrim Unbound waiting room; validate character creation, camera / UI behavior and preset handling, and remove it immediately if it causes crashes or instability.
- [ ] **Campfire 2026:** re-evaluate after a few days of community feedback; compare the Regular build against the current NEFARAM Campfire setup before deciding whether to adopt it.
- [ ] **Inflation Framework NG:** keep on hold and only study / test it if BFNG + Fill Her Up + Milk Mod Economy BodyMorph behavior becomes unstable, cumulative or difficult to tune cleanly through their native MCM settings.
- [ ] **Road Signs Overhaul 2.0 - FR Textures - Rhiven:** create a texture-only MO2 override for RSO 2.0 translating sign destinations into French (e.g. Blancherive, Rivebois, Épervine), while preserving the original visual style, DDS format/compression, alpha and mipmaps; no ESP/ESL, textures only.
