# TK Dodge for NEFARAM

> **Status: in-game validation completed on NEFARAM 17.3.6, 17.3.7, and 17.3.8.**
>
> **Tested runtime:** Skyrim AE 1.6.1170 with the NEFARAM combat stack, including MCO, TDM, Precision, and Pandora.

> **Credit:** This guide is based in part on the original NEFARAM TK Dodge guide by **Thoshy**. The procedure below was reorganized, expanded, and validated in game on NEFARAM 17.3.6, 17.3.7, and 17.3.8.

This guide adds a directional dodge mechanic to NEFARAM while preserving the existing combat and behavior stack. Compatibility was observed with MCO, TDM, Precision, and Pandora in the tested setup. This is not a guarantee for every possible user customization.

The procedure uses the listed TK Dodge Animation Pandora Patch. It does not introduce an additional custom patch.

---

## 1. Before installing

Use a test save and, if possible, clone or back up the current MO2 profile first. Record the existing left-pane priorities and Pandora configuration so they can be restored if needed.

For the first test, install the base TK Dodge stack only. Do **not** add an optional animation replacer until directional dodging works reliably with the default animations.

---

## 2. Required stack

Install these components in this order:

1. **IFrame Generator RE AE Support** — <https://www.nexusmods.com/skyrimspecialedition/mods/82737>
2. **TK Dodge For RE** — <https://www.nexusmods.com/skyrimspecialedition/mods/15309>. From **Optional Files**, install the entry named `TK Dodge For RE`.
3. **TK Dodge RE v0.55-rc3** — <https://www.nexusmods.com/skyrimspecialedition/mods/56956>
4. **TK Dodge First Person 8 Ways Dodge** — available on the TK Dodge RE page.
5. **TK Dodge Animation Pandora Patch** — <https://www.nexusmods.com/skyrimspecialedition/mods/111788>
6. **TK Dodge NG** — <https://www.nexusmods.com/skyrimspecialedition/mods/115408>

After the base stack passes the test matrix, you may add **one** of these animation replacers:

- Dynamic Dodge Animation; or
- Smooth Slip Dodge Animation.

Never install both animation replacers together.

### Why IFrame Generator remains in the stack

IFrame Generator RE AE Support provides invincibility frames during supported dodge animations. Keep it enabled unless testing identifies a specific incompatibility in your setup.

---

## 3. TK Dodge RE FOMOD

For **TK Dodge RE v0.55-rc3**, select the following options:

- `Behavior edits for dodge only`
- `TK dodge standalone`
- `TK dodge standalone - Enable Sheathed Dodge`
- `TK dodge standalone - Cancel concentration spell when dodging`
- `TK dodge standalone - Forward dodge scurry fix`

Avoid adding unrelated behavior variants during the initial integration test.

---

## 4. MO2 priority and placement

The important left-pane priority rules are:

- **TK Dodge NG must be below TK Dodge RE** so the NG files win conflicts.
- The complete TK Dodge stack must remain **above Pandora Output**.
- **Pandora Output must be below the entire dodge stack**, including the optional animation replacer when one is used.

The source procedure follows NEFARAM's Late Loaders placement logic because this keeps the dodge stack above the output mods. An optional separator named `TK Dodge` can be created inside that area as an organization aid; the separator itself is not required.

Recommended relative layout:

```text
[Late Loaders]
[TK Dodge]                                  # optional separator
IFrame Generator RE AE Support
TK Dodge For RE
TK Dodge RE
TK Dodge First Person 8 Ways Dodge
TK Dodge Animation Pandora Patch
TK Dodge NG
(one optional animation replacer)
...
[Overwrites]
Pandora Output
```

The relative priorities are what matter. Do not copy user-specific separator names or assume that every customized NEFARAM installation has identical absolute positions.

---

## 5. Winning INI rule

Both **TK Dodge RE** and **TK Dodge NG** contain a file named `TK Dodge RE.ini`.

Because TK Dodge NG loads after TK Dodge RE, the copy inside **TK Dodge NG wins**. Edit only this effective file:

```text
TK Dodge NG -> TK Dodge RE.ini
```

Editing the same-named file inside TK Dodge RE has no effect while it is overwritten by TK Dodge NG.

Choose the dodge style you prefer in the winning NG INI:

```ini
StepDodge = false
```

This enables roll dodges.

```ini
StepDodge = true
```

This enables step/slide dodges.

Neither value is universally required. It is a user preference, except where an animation replacer is designed around a specific style.

---

## 6. Generate behaviors with Pandora

NEFARAM uses **Pandora**, not FNIS, for this integration.

In Pandora, enable both entries:

- `TK Dodge RE / Ultimate Combat`
- `TK Dodge Standalone`

Then regenerate Pandora. Regenerate it again after reinstalling TK Dodge RE, changing behavior-related files, or changing an animation component.

The documented troubleshooting history shows that a missing `TK Dodge Standalone` selection can produce T-poses or broken directional dodges.

---

## 7. First in-game test

Test the base TK Dodge stack **before** installing Dynamic Dodge Animation or Smooth Slip Dodge Animation. This makes behavior, input, and animation problems much easier to isolate.

Use the actual dodge key configured in your installation; this guide does not prescribe a default key.

Test all of the following:

- forward, backward, left, and right dodge;
- weapon sheathed and drawn;
- one-handed weapon;
- two-handed weapon;
- dual wield;
- spell in one hand;
- spells in both hands and dual casting;
- first person and third person;
- MCO combat behavior;
- TDM movement;
- Precision combat interactions;
- stamina consumption;
- i-frame behavior;
- repeated dodges under combat load;
- save, quit, reload, and retest.

Only add an optional animation replacer after the base stack passes these checks without T-poses, rolls in place, or lost directional movement.

---

## 8. Optional animation replacers

Choose **one option only**, or keep the default TK Dodge animations.

### Option A: Dynamic Dodge Animation

<https://www.nexusmods.com/skyrimspecialedition/mods/79598>

Select these FOMOD choices:

- `TK Dodge RE 0.55 rc3`
- `Sway`

Regenerate Pandora and repeat the complete test matrix.

### Option B: Smooth Slip Dodge Animation

<https://www.nexusmods.com/skyrimspecialedition/mods/63660>

Use this file:

- `Smooth Slip Dodge I TDM 360 movement users`

Smooth Slip is generally paired with the following setting in the winning TK Dodge NG INI:

```ini
StepDodge = true
```

Regenerate Pandora and repeat the complete test matrix.

Do not leave Dynamic Dodge Animation and Smooth Slip Dodge Animation enabled together.

---

## 9. Troubleshooting

### T-pose during a dodge

Check the following in order:

1. TK Dodge NG is below TK Dodge RE.
2. Pandora Output is below the complete TK Dodge stack.
3. Both `TK Dodge RE / Ultimate Combat` and `TK Dodge Standalone` are enabled in Pandora.
4. TK Dodge RE uses the exact FOMOD selections in this guide.
5. Pandora is current and its configured paths are correct.
6. Regenerate Pandora.

The documented NEFARAM troubleshooting case was resolved after the missing standalone behavior was restored.

### Dodge animation plays in place or has no directional movement

Verify that:

- TK Dodge Animation Pandora Patch is installed and active;
- both Pandora entries are enabled;
- the TK Dodge standalone behavior was installed;
- Pandora was regenerated after installation;
- the problem also occurs with the base TK Dodge animations, not only with a replacer;
- the installed Pandora version is current for the setup.

### Step dodge does not activate

Confirm that `StepDodge = true` was saved in:

```text
TK Dodge NG -> TK Dodge RE.ini
```

Do not edit only the overwritten INI inside TK Dodge RE.

### Dodge key is inactive

Check that:

- TK Dodge NG is installed, enabled, and winning the expected conflicts;
- the key being pressed matches the actual configured keybind;
- both Pandora entries remain enabled;
- Pandora was regenerated;
- a Windows or keyboard-language shortcut is not intercepting the input.

No personal key preference is required by this guide.

### Problem while dual casting

The source testing indicates that directional dodge can work with a destruction spell in both hands. If it fails, investigate the keybind, keyboard layout, OS shortcuts, and local configuration first rather than treating it as a confirmed TK Dodge incompatibility.

---

## 10. After a NEFARAM update

The source discussion mentions NEFARAM's `[NoDelete]` naming convention as an optional precaution for custom mods that should survive an update workflow. Whether it is appropriate depends on how you update and maintain your local list; it does not replace post-update validation.

After every NEFARAM update:

1. confirm that every required TK Dodge component is still installed and enabled;
2. confirm that TK Dodge NG remains below TK Dodge RE;
3. confirm that Pandora Output remains below the complete dodge stack;
4. inspect the winning `TK Dodge RE.ini` inside TK Dodge NG;
5. confirm that both TK Dodge entries remain enabled in Pandora;
6. regenerate Pandora if behavior or animation files changed;
7. test forward, backward, left, and right dodge in game.

---

## 11. Validation summary

This integration was validated in game on:

- NEFARAM 17.3.6;
- NEFARAM 17.3.7;
- NEFARAM 17.3.8;
- Skyrim AE 1.6.1170.

In the tested setup, TK Dodge operated alongside the NEFARAM combat stack, including MCO, TDM, Precision, IFrame Generator, and Pandora. User-added combat, animation, input, or behavior changes can alter the result and should be tested separately.

### Final checklist

- [ ] The six required components are installed in the documented order.
- [ ] TK Dodge RE uses the documented FOMOD selections.
- [ ] TK Dodge NG is below TK Dodge RE.
- [ ] Only the winning NG copy of `TK Dodge RE.ini` is edited.
- [ ] The chosen `StepDodge` value matches the intended dodge style.
- [ ] At most one optional animation replacer is enabled.
- [ ] The complete dodge stack is above Pandora Output.
- [ ] `TK Dodge RE / Ultimate Combat` is enabled in Pandora.
- [ ] `TK Dodge Standalone` is enabled in Pandora.
- [ ] Pandora has been regenerated.
- [ ] The base animations passed the complete in-game test before adding a replacer.
- [ ] The four-direction test still passes after a NEFARAM update.

---

## Internal reference

For maintenance history and the cleaned French source, see [NEFARAM — Guide TK Dodge](../../06%20-%20GAMEPLAY/TK-DODGE/NEFARAM_Guide_TK_Dodge_FR.md).
