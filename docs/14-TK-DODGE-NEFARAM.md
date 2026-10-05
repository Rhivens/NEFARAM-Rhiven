# TK Dodge on NEFARAM 17 — Rhiven Procedure

> Status: **validated integration path / to be installed and tested on NEFARAM-Rhiven**
>
> Target: **NEFARAM 17.3.6**, Skyrim AE 1.6.1170, Pandora, MCO/TDM/Precision stack.
>
> Source basis: NEFARAM Discord guide by **thoshy**, updated for NEFARAM 17 on **2026-08-05**, with troubleshooting reports through **2026-09-25**.

## Goal

Add a reliable directional dodge mechanic to NEFARAM-Rhiven without disturbing the existing combat/animation stack.

Rhiven target behaviour:

- directional dodge forward / backward / left / right;
- keyboard use;
- preferred key: **Left Alt**;
- **roll dodge first** (not step dodge);
- keep compatibility with Pandora, MCO, TDM and Precision;
- retain i-frames during the dodge;
- test base TK Dodge animations before adding a cosmetic dodge animation replacer.

---

## 1. Mods to install

Create an optional MO2 separator:

```
TK Dodge
```

Install, in this order:

1. **IFrame Generator RE AE Support**  
   https://www.nexusmods.com/skyrimspecialedition/mods/82737

2. **TK Dodge For RE**  
   https://www.nexusmods.com/skyrimspecialedition/mods/15309  
   Download **only** the optional file named `TK Dodge For RE`.

3. **TK Dodge RE v0.55-rc3**  
   https://www.nexusmods.com/skyrimspecialedition/mods/56956

4. **TK Dodge First Person 8 Ways Dodge**  
   Same Nexus page as TK Dodge RE.

5. **TK Dodge Animation Pandora Patch**  
   https://www.nexusmods.com/skyrimspecialedition/mods/111788

6. **TK Dodge NG**  
   https://www.nexusmods.com/skyrimspecialedition/mods/115408

Optional animation replacer — choose **one only** after the base setup works:

- **Dynamic Dodge Animation**  
  https://www.nexusmods.com/skyrimspecialedition/mods/79598
- **Smooth Slip Dodge Animation**  
  https://www.nexusmods.com/skyrimspecialedition/mods/63660

Do **not** install both optional animation replacers together.

---

## 2. TK Dodge RE FOMOD

For **TK Dodge RE v0.55-rc3**, select only the behaviour options required by the NEFARAM guide:

- `Behavior edits for dodge only`
- `TK dodge standalone`
- `TK dodge standalone - Enable Sheathed Dodge`
- `TK dodge standalone - Cancel concentration spell when dodging`
- `TK dodge standalone - Forward dodge scurry fix`

Do not add unrelated behaviour variants during the first integration test.

---

## 3. MO2 priority / placement

The complete TK Dodge group must load **before Pandora Output**.

Recommended layout:

```
[TK Dodge]
IFrame Generator RE AE Support
TK Dodge For RE
TK Dodge RE
TK Dodge First Person 8 Ways Dodge
TK Dodge Animation Pandora Patch
TK Dodge NG
(optional animation replacer)
...
Pandora Output
```

Important:

- **TK Dodge NG must be below TK Dodge RE**.
- **Pandora Output must be below the entire TK Dodge stack**.
- Do not move Pandora Output above these mods.

The original NEFARAM guide places the Dodge separator with the late loaders specifically so the dodge mods remain above Pandora Output.

---

## 4. INI rule — important

There is a `TK Dodge RE.ini` in both:

- the TK Dodge RE mod;
- the TK Dodge NG mod.

Because **TK Dodge NG loads after TK Dodge RE**, the INI inside **TK Dodge NG wins**.

Therefore:

> Edit only the `TK Dodge RE.ini` contained in the **TK Dodge NG** mod.

Editing the copy inside TK Dodge RE has no practical effect while TK Dodge NG overwrites it.

### Rhiven setting

For Eleanor, start with:

```ini
StepDodge = false
```

This keeps the **roll dodge**, which is the current Rhiven preference.

If we later want to compare step dodge:

```ini
StepDodge = true
```

### Smooth Slip note

Smooth Slip Dodge Animation is intended for a step/slide style. If we test it later, switch `StepDodge = true` in the **TK Dodge NG copy** of `TK Dodge RE.ini`.

---

## 5. Pandora

Open Pandora after the mods are installed.

Enable both TK Dodge entries:

- **TK Dodge RE / Ultimate Combat**
- **TK Dodge Standalone**

Then regenerate the Pandora output.

This is mandatory.

A reported NEFARAM case produced T-poses / broken dodge behaviour because `TK Dodge Standalone` had been accidentally unchecked. Reinstalling TK Dodge RE with the correct FOMOD selections and enabling both Pandora entries fixed the problem.

---

## 6. IFrame Generator

**IFrame Generator RE AE Support** is not graphical frame generation.

It is a framework used to provide **invincibility frames during dodge animations**.

Keep it in the stack unless later testing shows a specific incompatibility.

---

## 7. First test — base TK Dodge only

Do **not** install Dynamic Dodge Animation or Smooth Slip Dodge Animation for the first test.

Validate the base stack first.

Test in game:

- dodge forward;
- dodge backward;
- dodge left;
- dodge right;
- weapon drawn;
- weapon sheathed;
- one-handed weapon;
- two-handed weapon;
- dual wield;
- spell in one hand;
- spells in both hands / dual casting;
- first person;
- third person;
- MCO combat;
- TDM movement;
- Precision combat;
- stamina cost;
- i-frame behaviour;
- repeated dodge under combat load;
- save -> quit -> reload -> retest.

Target key for Rhiven: **Left Alt**.

The Discord guide confirms users were testing Left Alt, but the source discussion does not document the exact key-binding path. Verify the final key binding in the installed TK Dodge NG configuration rather than assuming a menu or INI entry.

---

## 8. Optional animation stage

Only after the base dodge is stable:

### Option A — Dynamic Dodge Animation

NEFARAM guide author preference.

FOMOD selections:

- `TK Dodge RE 0.55 rc3`
- `Sway`

Retest the complete matrix above.

### Option B — Smooth Slip Dodge Animation

Download:

- `Smooth Slip Dodge I TDM 360 movement users`

Then set in the **TK Dodge NG copy** of `TK Dodge RE.ini`:

```ini
StepDodge = true
```

Retest.

Do not keep both animation replacers installed simultaneously.

---

## 9. Troubleshooting

### T-pose on dodge

Check first:

1. TK Dodge NG is below TK Dodge RE.
2. Pandora Output is below the TK Dodge stack.
3. Pandora has both:
   - `TK Dodge RE / Ultimate Combat`
   - `TK Dodge Standalone`
4. TK Dodge RE was installed with the exact FOMOD options from this procedure.
5. Regenerate Pandora.

A September 2026 NEFARAM user fixed a T-pose issue after discovering that the standalone TK Dodge Pandora option had been lost during previous troubleshooting.

### Character rolls in place / no directional movement

Check:

- TK Dodge Animation Pandora Patch is installed;
- Pandora was regenerated after installation;
- both TK Dodge Pandora entries are enabled;
- TK Dodge RE FOMOD contains the standalone behaviour;
- test **base TK Dodge animations** before blaming an animation replacer;
- update Pandora if the local build is old.

### Step dodge does not activate

Almost always check the **winning INI** first.

The effective file is:

```
TK Dodge NG -> TK Dodge RE.ini
```

not the same-named INI inside TK Dodge RE.

### Left Alt does nothing

Check:

- TK Dodge NG is actually installed/enabled;
- the final key bind is really Left Alt;
- both Pandora TK Dodge entries are checked;
- Pandora has been regenerated;
- Windows keyboard/language switching is not intercepting the key combination.

A September 2026 discussion also reported a keyboard-language overlay appearing during failed dodge input, so OS-level shortcut interference is worth checking.

### Dual-casting issue

A September 2026 user reported standing still while trying to dodge with two destruction spells equipped, while the guide author could dodge in all directions with Flames in both hands.

Conclusion: dual casting should work, but keyboard/input configuration can still interfere. Treat this as an input troubleshooting case before changing the dodge stack.

---

## 10. NEFARAM updates

Custom-added dodge mods may need to be protected from Wabbajack/NEFARAM update cleanup depending on the update workflow.

The Discord discussion suggests using the existing NEFARAM `[NoDelete]` convention for custom TK Dodge mods, but load-order/plugin placement and Pandora generation still need to be rechecked after an update.

Do not assume an update preserves:

- MO2 priority;
- plugin order;
- Pandora selections;
- Pandora Output;
- local INI changes.

After every NEFARAM update:

1. verify all TK Dodge mods are still present;
2. verify TK Dodge NG is below TK Dodge RE;
3. verify Pandora Output is below the dodge stack;
4. verify the winning NG INI;
5. regenerate Pandora if behaviours changed;
6. perform a quick four-direction dodge test.

---

## 11. Rhiven acceptance criteria

The integration is accepted only if:

- [ ] Left Alt triggers dodge reliably.
- [ ] Forward roll works.
- [ ] Backward roll works.
- [ ] Left roll works.
- [ ] Right roll works.
- [ ] Sheathed dodge works.
- [ ] Drawn-weapon dodge works.
- [ ] Dual casting does not lock movement.
- [ ] No T-pose.
- [ ] No roll-in-place bug.
- [ ] No conflict observed with MCO.
- [ ] No conflict observed with TDM.
- [ ] No conflict observed with Precision.
- [ ] I-frames behave as expected.
- [ ] Stamina use is acceptable.
- [ ] Save / reload remains stable.
- [ ] Pandora rebuild completes cleanly.

Only then consider an optional animation replacer.

---

## Source note

This procedure is based on the NEFARAM Discord thread **"How to add TK Dodge to Nefaram"**, authored by **thoshy**, updated for **NEFARAM 17** on 2026-08-05, plus troubleshooting exchanges from September 2026.

Rhiven-specific decisions in this document:

- start with **roll dodge** (`StepDodge = false`);
- target **Left Alt**;
- validate the base implementation before cosmetic animation replacement;
- prioritize a minimal and reversible integration.
