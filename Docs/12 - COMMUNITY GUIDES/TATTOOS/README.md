# Extending the Tattoo Ecosystem in NEFARAM 17.3.x

> **Status:** Community guide for NEFARAM 17.3.x. The stack described here was installed and statically audited in NEFARAM-Rhiven 17.3.7, then retained in the 17.3.8 baseline. Some runtime tests remain incomplete; use a disposable save.
>
> **Scope:** This guide adds automatic selection, temporary fading, and two large tattoo catalogs to the tattoo foundations already included in stock NEFARAM. It does not replace SlaveTats or describe an upgrade from older RTC/Fade releases.

## 1. What stock NEFARAM already provides

Stock NEFARAM 17.3.x already includes the essential tattoo foundation. In the original MO2 left-pane snapshot, both of these mods are present under `[35 - Sexlab Content]`:

- `SlaveTatsSE`
- `SlaveTatsNG`

The original list also already contains SexLab and the broader framework components used by this stack, including `powerofthree's Papyrus Extender` and `JContainers`. Always keep the versions and file winners provided by your working NEFARAM installation unless a mod's current instructions explicitly require otherwise.

In other words, this guide does **not** add the basic tattoo renderer. It extends the existing foundation with an automatic application engine, fading support, tattoo packs, and modular RTC rules.

## 2. What this guide adds

The following are genuine additions to stock NEFARAM 17.3.x:

1. `Fade Tattoos Continued` **2.1.0**
2. `Rape Tattoos Continued` **2.0.3**
3. `Rape Tats Continued 2.0.3 QoL Extension` **rev1**
4. `Alpia Slavetats Pack` — the All-in-One setup documented below
5. `Alpia Rtats Settings All in One`
6. `Zaki Tattoos General Pack SE` **1.1.1** — Full Pack, with 4K body/feet and 2K hands/face textures
7. `Zaki RTC Settings`
8. An optional future community override named `zzz-Rhiven-RTC.json`

The eighth item is a planned optional preset. **It is not currently published or downloadable in this repository.** Do not expect to find it in the guide directory or elsewhere in the public repository.

RTC and Fade Tattoos Continued replace their older counterparts. Do not install the old and Continued versions in parallel.

## 3. Architecture overview

The functional chain is:

```text
Alpia and Zaki tattoo catalogs
             |
             v
SlaveTats / SlaveTatsNG -> Rape Tattoos Continued -> Fade Tattoos Continued
             ^                      ^
             |                      |
 tattoo definitions/textures   automatic-selection rules
                                from RTC preset JSON files
```

- **SlaveTats / SlaveTatsNG** registers tattoos and manages RaceMenu overlays.
- **Alpia and Zaki main packs** provide tattoo definitions and texture files.
- **Rape Tattoos Continued (RTC)** decides when and which eligible tattoos are applied, according to MCM settings and RTC rule files.
- **Fade Tattoos Continued** tracks temporary marks and removes them over time according to its configuration.
- **Alpia RTC Settings, Zaki RTC Settings, and optional user presets** define RTC's automatic selection and grouping behavior. They do not add tattoo textures.

RTC can use different settings for the player, NPCs, and ZaZ slaves. If the player is in `zbfFactionSlave`, the ZaZ-slave settings can also apply to the player.

## 4. Two different kinds of JSON

This distinction is critical when diagnosing a missing or incorrectly grouped tattoo.

| JSON type | Used by | Purpose | Typical content |
| --- | --- | --- | --- |
| SlaveTats catalog JSON | SlaveTats | Defines tattoos that can be registered and displayed | Name, area, section, texture path |
| RTC settings or preset JSON | Rape Tattoos Continued | Controls automatic eligibility and logical grouping | Texture-path keys with a `Group` rule and related RTC data |

For example, the Alpia All-in-One SlaveTats catalog and the Alpia RTC settings file serve different systems. Installing the tattoo pack does not automatically supply RTC grouping rules, and installing RTC rules does not supply the textures they reference.

A tattoo can therefore be:

- present in SlaveTats but absent from a dedicated RTC rule file;
- present in an RTC preset but unusable because its catalog entry or texture is missing;
- available for manual SlaveTats application while excluded from RTC's automatic selection.

The All-in-One choice in a tattoo pack installer is also unrelated to the QoL Extension's merging of multiple RTC preset files.

## 5. Requirements and NEFARAM foundations

The internal RTC documentation identifies these relevant foundations:

- SexLab;
- SlaveTats and its prerequisites;
- Fade Tattoos, either the supported original or Continued implementation;
- `powerofthree's Papyrus Extender` (the RTC author documented testing from version 5.5.0);
- JContainers for configuration data;
- RaceMenu overlays through the existing SlaveTats ecosystem.

ZaZ is optional for RTC itself and is relevant when using RTC's `zbfFactionSlave` actor category.

Stock NEFARAM already contains the principal framework pieces above. This guide does not recommend replacing them pre-emptively. If behavior is unusual, inspect versions and winning files before changing the baseline.

## 6. MO2 installation and left-pane order

Use the stock `[Sexlab Content]` section as the public reference point. Add the extension block near the end of that section, after the existing content. The validated project placed it after `Advanced Nudity Detection`.

Use this order from top to bottom in the MO2 left pane:

```text
Fade Tattoos Continued
Rape Tattoos Continued
Rape Tats Continued 2.0.3 QoL Extension rev1
Alpia Slavetats Pack
Alpia Rtats Settings All in One
Zaki Tattoos General Pack SE
Zaki RTC Settings
optional user override preset
```

The last entry is a generic slot for a deliberate final override. The future `zzz-Rhiven-RTC.json`, once actually published, would belong there as a separate MO2 mod or otherwise isolated file source.

The essential conflict rule is:

> **The QoL Extension must win its script conflicts against RTC.**

Expected overlapping files include:

```text
Scripts/rapeTattoos.pex
Scripts/rapeTattoos_mcm.pex
Scripts/rapeTattoos_utils.pex
```

The corresponding `.psc` source files can also conflict when sources are included. Check file winners in MO2 rather than relying only on visual position.

## 7. Why the RTC QoL Extension matters

Base RTC stores or consumes a main configuration. The QoL Extension rev1 adds a modular workflow that can load and merge multiple preset JSON files. This allows each tattoo pack—and a final personal override—to remain separate instead of requiring users to hand-edit one large `settings.json`.

Useful QoL MCM commands:

| Command | Recommended use |
| --- | --- |
| `Test / Reload configs` | Rebuild the merged mapping on a test save and inspect console or log output |
| `Merge all into settings.json` | Avoid casual use; it writes a consolidated configuration and collapses the practical separation between presets |
| `Enable detailed Papyrus logging` | Enable only temporarily while diagnosing a problem, then turn it off |

The modular approach makes pack updates and troubleshooting easier: author presets remain intact, and a small final delta can express only intentional changes.

## 8. JSON locations, merge order, and priority

The QoL workflow documented in the internal sources supports additional presets under:

```text
Data/SKSE/Plugins/RapeTattoos/
```

The historical user-data location can also be involved:

```text
Documents/My Games/Skyrim Special Edition/JCUser/rTats/
  settings.json
  colorConfig.json
  presets/
```

When a main `settings.json` exists under `Data/SKSE/Plugins/RapeTattoos/`, the reviewed QoL behavior gives that location priority as the principal configuration. Additional presets from that Data path are loaded after presets in the historical `JCUser/rTats/presets/` path. For duplicate keys, the rule loaded later wins.

Do not assume that a file wins merely because its MO2 mod is lower in the left pane. The preset discovery and merge sequence also matters.

### Observed lesson from the project

During internal validation, a custom override with a numeric-prefixed filename (`99-...`) was merged **before** the Alpia and Zaki presets. Its duplicate-key changes were overwritten. Renaming the same file with a late alphabetical `zzz-...` prefix caused it to merge after Alpia and Zaki, and representative overrides then appeared correctly in the RTC MCM.

This is an observed result from the validated setup, not a universal promise about every QoL build or filesystem. If you intentionally need a final override layer, a name such as:

```text
zzz-Custom-RTC.json
```

can be useful. Always verify the actual order with `Test / Reload configs` and inspect the console or Papyrus log. Do not infer priority from the filename alone.

The internal test also showed that a missing optional `JCUser/rTats/presets/` directory could produce a warning without stopping the Data-path presets from being merged.

## 9. Optional Rhiven preset — why it exists

The planned public filename is:

```text
zzz-Rhiven-RTC.json
```

**This preset is optional and not yet published. It is not currently included anywhere in the public repository.**

It is not a framework fix, does not replace the QoL Extension, and is not required for RTC, Alpia, or Zaki to work. Its intended role is to provide a coherent final override layer after the Alpia and Zaki author presets have loaded.

Based on the internally validated custom delta, such a preset can:

- harmonize group-name casing and selected grouping conventions;
- preserve the original author presets by overriding only chosen keys;
- selectively mark chosen categories as `(excluded)` for automatic RTC use;
- set deliberate behavior for Full Body and Full Face entries;
- keep the customization isolated, reviewable, and removable.

Content exclusions used during internal validation were personal policy choices, not technical corrections or universal defaults. Any public preset must have those choices reviewed explicitly before release rather than presenting them as the correct setup for every user.

If this preset is published later, it should be added as a separate downloadable JSON file. This guide should then be updated with a direct link, checksum, or exact repository path. Until that happens, do not create a placeholder and do not treat the filename as a download instruction.

## 10. Alpia setup and audit

The tested project used the main `Alpia Slavetats Pack` in its **All-in-One** configuration.

- The separate Orc and Riekling extensions were not installed.
- Their separate RTC presets were not used.
- The separate `Public Whore Tattoo Replacer` was not installed.
- The main pack can still contain tattoos with a Public Whore theme; that is not the same component as the separate replacer.

The matching `Alpia Rtats Settings All in One` preset was installed after the main pack.

### Static audit findings

The two supplied Alpia JSON files were parsed and cross-compared:

| Finding | Result |
| --- | ---: |
| SlaveTats catalog entries | **1,214** |
| RTC-configured entries | **1,205** |
| Catalog entries without a dedicated RTC rule | **9** |
| Texture-path casing differences | **24** |
| Duplicate catalog paths | **0** |
| JSON syntax errors | **0** |

The comparison found no RTC texture reference absent from the SlaveTats catalog when compared without regard to case. That does **not** prove that JContainers or RTC treats differently cased keys as equivalent, and it does not prove that every referenced `.dds` file is physically present or renders correctly.

The nine catalog entries without dedicated RTC rules remain available to SlaveTats. Their exact automatic behavior should be tested rather than inferred from the static count.

These figures are **static audit findings**, not evidence of exhaustive runtime coverage.

## 11. Zaki setup and No Overlap caution

The tested project used:

- `Zaki Tattoos General Pack SE` **1.1.1**;
- the **Full Pack**, containing **841 entries**;
- hybrid textures: **4K body/feet** and **2K hands/face**;
- no optional RaceMenu plugin;
- no 8K extension;
- no Zaki Beast pack.

The project-customized `Zaki RTC Settings` contained **841 texture keys** with `Group` assignments. It was loaded after the tattoo pack.

### Do not blindly replace it with No Overlap

`No Overlap for Rape Tattoo` was statically audited but was **not installed as-is**. It is a third-party RTC preset, not a script extension.

Its Zaki configuration covers **528** Zaki keys. Compared with the 841-key project preset:

- **313 Zaki entries are omitted**;
- approximately **137 entries have substantial group reassignments** (**161** differences when casing-only changes are also counted).

The mixed No Overlap `settings.json` that was reviewed also contained 254 Sexy Supplemental keys. Installing it as a main settings file could therefore introduce unrelated content or replace a more complete existing mapping.

No Overlap's logical group changes were not exhaustively verified against actual UV geometry. Review and merge any desired rules deliberately; do not replace the fuller 841-key preset blindly.

## 12. RTC grouping semantics

RTC normally limits automatic selection to **one tattoo per configured group**, subject to the rest of RTC's logic and settings.

Two special values matter:

- `(excluded)` — RTC should never choose the entry automatically. The tattoo may still remain available for manual application through SlaveTats if its catalog and texture are installed.
- `(unassigned)` — the entry is not restricted by a named group, but it still consumes an overlay slot and remains subject to overlay capacity.

Groups are logical labels. They are **not geometric UV-overlap detection**. Two textures assigned to different logical groups can still overlap visually, and one broad texture can cover several physical areas even though RTC sees only its configured group.

Group casing differences should not be normalized blindly. Confirm the actual behavior first, particularly when keys or group labels differ only by case.

## 13. Initial MCM setup

After RTC has initialized on a disposable save:

1. Open the `Rape Tattoos` MCM.
2. Open `General`.
3. Select **`LOAD TATTOO CONFIG PAGES`**.
4. Wait for `Tattoos Page 1`, `Tattoos Page 2`, and subsequent pages to appear.
5. With the QoL Extension installed, run **`Test / Reload configs`**.
6. Inspect console output or temporary diagnostic logs for every expected preset and its merge position.
7. Open representative Tattoo Pages and compare assigned groups with the intended rules.

The appearance of Tattoo Pages proves that pages were generated. It does **not** prove that a final override loaded last or won duplicate keys.

Detailed Papyrus logging can be useful during diagnosis but should not remain enabled during normal play. RTC's debug features can also generate many notifications and traces.

## 14. Persistence and user files

RTC user state and settings can involve:

```text
Documents/My Games/Skyrim Special Edition/JCUser/rTats/settings.json
Documents/My Games/Skyrim Special Edition/JCUser/rTats/colorConfig.json
Documents/My Games/Skyrim Special Edition/JCUser/rTats/presets/
Data/SKSE/Plugins/RapeTattoos/
```

The QoL Extension may also support a configurable color destination under `Data/SKSE/Plugins/RapeTattoos/ColorConfig/`.

Verify where files are actually created and updated in **your** installation. MO2 virtual paths, the Windows Documents location, permissions, and the presence of a Data-path main settings file can affect which location is active.

When freezing a known-good setup, back up `JCUser/rTats` separately from the MO2 profile. A profile backup alone may not include user data written to Documents.

## 15. RaceMenu overlays and `skee.ini`

SlaveTats ultimately uses RaceMenu overlay slots. The effective limits are configured by area in the winning `SKSE/Plugins/skee.ini`, including:

- `[Overlays/Body]`
- `[Overlays/Hands]`
- `[Overlays/Feet]`
- `[Overlays/Face]`

Do not increase these limits pre-emptively. First reproduce a capacity problem and inspect the current winning file and active overlay counts. Additional slots can increase the cost of SlaveTats synchronization and do not repair missing catalogs, invalid texture paths, or incorrect RTC grouping.

Full Body and Full Face tattoos may also overlap other entries by design. Treat that as an intentional configuration decision, not something logical groups can always prevent.

## 16. Compatibility and cautions

- RTC explicitly lists **SlaveTats Performance Patch (Sejra)** as incompatible.
- RTC explicitly lists **Monoman's Rape Tattoos Tweaked** as incompatible.
- A historical `Scripts/SlaveTatsMCMMenu.pex` conflict involving PAH Diary Of Mine and SlaveTats NG is documented internally. Different files were observed, but no reproducible failure was established. Do not change the known working winner without a targeted test.
- If behavior is inconsistent, check the effective JContainers version and MO2 file winner. Another mod can package an older copy.
- RTC debug hotkeys can conflict with other mods. Keep RTC debug disabled in normal play.
- Do not change script winners or merge configuration files blindly in response to a single symptom.
- Avoid upgrading from older RTC installations mid-playthrough unless you have a tested migration procedure.

## 17. Validation checklist

Use a disposable save and distinguish static checks from runtime results.

- [ ] Confirm all eight installed components that are intended for your setup, excluding the unpublished optional preset unless you created your own equivalent.
- [ ] Verify the QoL Extension wins its RTC script conflicts.
- [ ] Rebuild or refresh the SlaveTats registry if required by the installed SlaveTats workflow.
- [ ] Run `LOAD TATTOO CONFIG PAGES` after RTC initializes.
- [ ] Run `Test / Reload configs`.
- [ ] Confirm Alpia and Zaki presets are reported as loaded.
- [ ] Confirm the actual preset merge order, especially for any final user override.
- [ ] Check representative allowed, `(excluded)`, `(unassigned)`, Full Body, and Full Face entries in the MCM.
- [ ] Apply several Alpia and Zaki tattoos manually and through RTC.
- [ ] Verify texture paths by checking actual rendering, not only JSON references.
- [ ] Save, reload, and confirm overlay and configuration persistence.
- [ ] Test Fade expiration for temporary tattoos.
- [ ] Test player, NPC, and ZaZ categories if you use them.
- [ ] Confirm the effective Body, Hands, Feet, and Face overlay limits.
- [ ] Re-test with debug disabled after diagnosis.

The source project did not complete exhaustive random-application coverage, every Fade scenario, or visual validation of every texture. Do not mark the whole stack as fully validated from a few successful examples.

## 18. Troubleshooting

### A tattoo is missing

Check the three layers independently:

1. Does the SlaveTats catalog JSON contain the definition?
2. Does the relevant RTC preset contain a rule if automatic application is expected?
3. Does the referenced texture file actually exist and render?

Refresh the SlaveTats registry if required after installing a new catalog.

### A custom exclusion or group is not respected

- Run `Test / Reload configs`.
- Inspect the reported merge sequence.
- Confirm the exact duplicate texture key and its casing.
- Confirm that the final override filename really loads after the author presets.
- Remember that MO2 left-pane position alone does not prove RTC merge priority.

### Settings do not persist

- Inspect both the actual `JCUser/rTats` location and the Data-path configuration.
- Check Windows permissions and whether the game is writing to the Documents folder you expect.
- Determine which `settings.json` is active before editing or restoring files.
- Back up both the MO2 configuration source and external user data.

### Tattoo Pages are missing

- Wait for RTC and MCM registration to finish.
- Open `General` and use `LOAD TATTOO CONFIG PAGES`.
- If pages still do not appear, check RTC initialization, script winners, dependencies, and logs.

### Too many tattoos overlap

- Review the RTC logical groups for the affected texture keys.
- Check whether entries are `(unassigned)` or intentionally Full Body/Full Face.
- Do not assume RTC performs geometric overlap detection.
- Test group changes on a disposable save before consolidating presets.

### Synchronization or performance problems

- Inspect active overlay counts and the winning `skee.ini`.
- Check for incompatible SlaveTats/RTC patches.
- Confirm the JContainers winner.
- Disable detailed RTC debug logging.
- Do not raise overlay limits until a measured capacity need is established.

## 19. Validation status and disclaimer

This extension stack was installed and statically audited in **NEFARAM-Rhiven 17.3.7** and retained into the **17.3.8 baseline**.

The following were confirmed in the internal setup:

- the stock-versus-added component separation from original and modded MO2 snapshots;
- the expected left-pane extension order;
- the QoL Extension's intended RTC script winners;
- static Alpia and Zaki JSON counts described in this guide;
- console-observed merging of Alpia, Zaki, and a late alphabetical custom preset;
- representative MCM results showing that the late custom preset's overrides won after reloading.

The following remain non-exhaustively tested according to the source documentation:

- full random application coverage across all catalog entries;
- Fade behavior in every relevant case;
- exhaustive verification of every physical texture file and placement;
- all player, NPC, and ZaZ category combinations;
- every interaction between broad Full Body/Full Face textures and other overlays.

Community users should validate this stack on disposable saves before adopting it in a permanent playthrough.

## 20. Internal project references

These repository documents contain the detailed project audit trail. They are internal technical records rather than generic installation instructions:

- [Tattoo architecture and development notes](../../06%20-%20GAMEPLAY/TATTOOS/README.md)
- [Alpia and RTC QoL integration audit](../../06%20-%20GAMEPLAY/TATTOOS/ALPIA-08-2026-QOL.md)
- [Zaki General and No Overlap audit](../../06%20-%20GAMEPLAY/TATTOOS/ZAKI-GENERAL-RTC.md)
