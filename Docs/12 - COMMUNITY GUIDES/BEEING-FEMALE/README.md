# Beeing Female NG for NEFARAM

> **Status: technical integration validated on a NEFARAM 17.3.x-based setup.**
>
> Full cycle, pregnancy, and birth gameplay validation remains dependent on the user's settings and is not claimed by this guide.

This guide describes a conservative way to use **Beeing Female NG 3.6.0** as NEFARAM's primary fertility framework, together with **Fertility Adventures Redux**. It keeps the original NEFARAM architecture as the baseline and avoids adding a child-actor framework.

---

## 1. What this replaces

Original NEFARAM includes **Fertility Mode** as an optional fertility framework under:

```text
[39 - OPTIONAL MODS]
```

When using the stack in this guide, keep **Fertility Mode disabled**. Running it alongside Beeing Female NG would duplicate the fertility-framework role and is outside the validated setup.

The replacement stack is:

```text
Fertility Adventures Redux
Beeing Female NG 3.6.0
Beeing Female NG HUD Re-Alignment addon    # optional
```

---

## 2. NEFARAM baseline

The original NEFARAM installation already contains the main ecosystem components used by this integration:

- SexLab Framework
- SkyUI
- PapyrusUtil
- Address Library
- powerofthree's Papyrus Extender
- Spell Perk Item Distributor (SPID)
- SlaveTats / SlaveTatsNG
- Bathing in Skyrim Renewed
- SexLab Fill Her Up Baka Edition (FHU)
- Milk Mod Economy (MME)
- Simple Children
- Pandora Behaviour Engine
- P.A.I.A
- P.A.I.A Expansion (Pregnancy and Inflation animations)

This guide assumes that the normal NEFARAM installation is already operational. It does not replace NEFARAM's general setup and validation instructions.

---

## 3. Before installing

Before changing the fertility stack:

1. clone your current MO2 profile if possible;
2. back up the MO2 left-pane mod order;
3. back up the plugin load order;
4. choose a safe, disposable test save;
5. confirm that the stock **Fertility Mode** entry remains disabled.

Do the initial configuration and gameplay checks on the test save before continuing a long playthrough.

---

## 4. MO2 placement

Install the new stack under the original NEFARAM separator:

```text
[41 - Added Mods]
├─ Fertility Adventures Redux
├─ Beeing Female NG 3.6.0
└─ Beeing Female NG HUD Re-Alignment addon    # optional
```

This is a relative layout, not a prescription for exact absolute positions. NEFARAM installations can differ after user customization.

The important rules are:

- keep **Fertility Mode** disabled in `[39 - OPTIONAL MODS]`;
- keep Fertility Adventures Redux and Beeing Female NG together in `[41 - Added Mods]`;
- place the optional HUD addon after Beeing Female NG so its additional HUD presets are available;
- allow Beeing Female NG's P.A.I.A patches to win their relevant OAR configuration conflicts.

Do not move or reinstall the existing P.A.I.A base mods solely for this integration. They already belong to the original NEFARAM animation stack.

---

## 5. Beeing Female NG FOMOD choices

### Validated selections

Select:

- **Open Animation Replacer**
- **Fertility Adventures Redux patch**
- **SPID item distribution**
- **P.A.I.A base patch**
- **P.A.I.A Expansion patch**
- **SlaveTats womb / birth-count tattoo packs**

These selections match the components already present in the original NEFARAM ecosystem.

### Options skipped during validation

Do not select these when reproducing the validated low-complexity setup:

- **FMR-Immersive Effects**
- **RS Children child actors**
- **Creature child actors**

These options were not part of the technical validation and should not be treated as required additions.

---

## 6. Child-system guidance

Original NEFARAM uses **Simple Children**, not RS Children. No migration to RS Children or another child-actor framework is needed for this setup.

For the lowest-complexity validated path, configure the birth output as:

```text
Gem
```

This preserves the pregnancy and birth loop without introducing persistent child actors. Do not install the creature-child addon unless you intentionally want to build and test that additional, currently unvalidated layer.

---

## 7. Recommended first MCM configuration

Use the following as a conservative starting point, then adjust only after the basic integration is stable:

| Setting | Recommended starting value | Notes |
|---|---|---|
| Player pregnancy | Enabled | Part of the validated policy |
| NPC pregnancy | Disabled | Reduces initial complexity; not a universal requirement |
| Visual scaling type | BodyMorph | Validated configuration |
| BodyMorph profile | CBBE 3BA | Validated configuration |
| Birth output | Gem | Avoids adding a child-actor framework |
| Creature conception | User choice | Remains test-dependent and was not finalized |

Pregnancy probabilities and cycle duration were not finalized during technical validation. Choose them for your own playthrough only after confirming that the base system is stable.

### BodyMorph coexistence

Beeing Female NG, SexLab Fill Her Up Baka Edition, and Milk Mod Economy may all apply BodyMorph changes. Start with conservative morph amplitudes in their MCMs and test the combined result.

**Inflation Framework NG is not required.** It was considered only as a reserve option if a reproducible morph-coexistence problem could not be solved through native MCM tuning.

---

## 8. Pandora regeneration

Rerun **Pandora Behaviour Engine** after installing Beeing Female NG. Before regeneration, Beeing Female NG may report its animations as incompatible.

During generation, confirm that Pandora detects:

```text
FNIS_BeeingFemale_List
```

After generation and relaunching the game, open the Beeing Female NG System page and verify:

```text
BeeingFemale Animations = COMPATIBLE
```

Do not treat the installation as animation-ready until that status is shown.

---

## 9. Optional HUD realignment

Beeing Female NG 3.6.0 includes these HUD configuration files:

```text
BeeingFemale/HUD/default.ini
BeeingFemale/HUD/LeftOver.ini
```

The optional HUD Re-Alignment addon adds preset files **Align1** through **Align6**. Their structure was checked against the Beeing Female NG 3.6.0 HUD INIs.

The addon is optional, and no single preset is required by this guide. Choose the preset that best fits your own HUD layout after in-game testing.

---

## 10. Compatibility and conflict notes

### P.A.I.A

**P.A.I.A** and **P.A.I.A Expansion (Pregnancy and Inflation animations)** are already part of the original NEFARAM animation stack. Select their Beeing Female NG patches in the FOMOD, and allow those patches to win the relevant OAR configuration conflicts.

### SlaveTats

NEFARAM already includes **SlaveTats / SlaveTatsNG**. The Beeing Female NG womb and birth-count tattoo packs were selected in the validated setup.

### Bathing in Skyrim

Beeing Female NG detected the existing **Bathing in Skyrim** integration successfully during technical validation.

### FHU and MME

**SexLab Fill Her Up Baka Edition** and **Milk Mod Economy** can coexist in the same environment, but final BodyMorph amplitudes were not established. Tune all three systems conservatively before considering another morph framework.

---

## 11. In-game validation checklist

On a disposable test save, confirm all of the following:

- [ ] Beeing Female NG appears in the MCM.
- [ ] Beeing Female NG initializes successfully.
- [ ] SexLab compatibility is detected.
- [ ] Bathing in Skyrim compatibility is detected.
- [ ] Beeing Female item distribution is operational.
- [ ] Pandora detected `FNIS_BeeingFemale_List` during regeneration.
- [ ] The Beeing Female NG System page reports its animations as **COMPATIBLE**.
- [ ] No blocking Beeing Female NG console error is observed.
- [ ] The chosen HUD layout is readable and does not obstruct the rest of the interface.
- [ ] Morph changes remain reasonable when Beeing Female NG, FHU, and MME are exercised.
- [ ] A complete cycle, pregnancy, and birth test succeeds before the setup is used for a long playthrough.

The first eight items were confirmed during technical validation. HUD preference, final morph tuning, and full pregnancy/birth gameplay remain user- and setup-dependent.

---

## 12. Troubleshooting

### Beeing Female animations show as incompatible

Rerun Pandora, confirm that it detects `FNIS_BeeingFemale_List`, then relaunch the game and check the Beeing Female NG System page again.

### The Beeing Female NG MCM is missing

Allow the game time to finish registering MCMs, then refresh MCM registration through the normal facilities already available in your setup if needed. Do not continue configuration until the menu appears.

### Belly or body morphs look excessive or inconsistent

Reduce the BodyMorph amplitudes in Beeing Female NG, FHU, and MME first. Test again before adding another morph framework.

### Child-actor problems appear

Return to **Gem** birth output and avoid the RS Children or creature-child options unless you are intentionally configuring and testing a separate child-actor setup.

### Two fertility systems appear to be active

Check `[39 - OPTIONAL MODS]` and confirm that the stock **Fertility Mode** entry is still disabled.

### P.A.I.A animations do not behave as expected

Confirm that both P.A.I.A patch options were selected in the Beeing Female NG FOMOD and that the Beeing Female NG patch files win their relevant OAR configuration conflicts. Regenerate Pandora afterward.

---

## 13. Validation scope and disclaimer

The following were technically validated:

- Beeing Female NG initialization;
- MCM registration;
- SexLab compatibility detection;
- Bathing in Skyrim compatibility detection;
- Beeing Female item distribution;
- Pandora integration;
- absence of a blocking Beeing Female NG console error.

The following were not finalized or fully gameplay-validated:

- pregnancy probabilities;
- cycle duration;
- creature-fertility policy;
- final BodyMorph amplitudes;
- FHU/MME coexistence tuning;
- definitive HUD preset;
- a full pregnancy and birth gameplay test.

Treat this guide as a validated technical integration baseline, not as a universal gameplay preset. Complete the remaining choices and tests on a disposable save before committing them to a long playthrough.

---

## 14. Workshop reference

For the technical notes behind this community guide, see the [internal fertility-system integration record](../../06%20-%20GAMEPLAY/BEEING%20FEMALE%20NG/12-FERTILITY-SYSTEM.md).
