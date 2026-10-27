# SexLab Approach Redux 3.62 for NEFARAM

> **Status:** technical integration validated; gameplay validation and long-term tuning remain user-dependent
>
> **Version:** SexLab Approach Redux **3.62**
>
> **Scope:** installation, MO2 placement, Pandora generation, MCM initialization, compatibility monitoring, and functional testing

This community guide explains how to add SexLab Approach Redux 3.62 to an existing NEFARAM installation. The integration does **not** require a custom patch.

## What SexLab Approach Redux does

SexLab Approach Redux adds autonomous NPC approaches and a reactive social layer. Nearby NPCs can initiate conversations and sexual interactions instead of waiting for the player to start every encounter. The available dialogue and behavior depend on the mod's conditions, character traits, relationships, arousal settings, and enabled integrations.

It is primarily a scripted dialogue and event system, not a worldspace or quest-location expansion. The main integration concern is therefore event timing and ownership rather than landscape or navmesh conflicts.

## Approach vs SLHH

SexLab Approach Redux is **not redundant with SLHH Expansion**.

- **SexLab Approach Redux** focuses on autonomous NPC approaches, social interactions, and sexual dialogue or events.
- **SLHH Expansion** focuses more heavily on harassment and aggressive encounters.

The two mods can coexist because their roles are complementary. However, both can initiate interactions around the player, so careless settings may produce too many events, stacked forcegreets, competing dialogue, or overlapping scene starts. Use conservative chances and meaningful cooldowns, then tune both MCMs together before deciding that the mods are incompatible.

## Requirements and the existing NEFARAM stack

SexLab Approach Redux requires the usual SexLab and animation ecosystem. Original NEFARAM already provides the main stack used by Approach:

- SexLab Framework;
- an OSL/SLO Aroused-compatible stack;
- Fuz Ro D-oh / Silent Voice;
- SLAL support;
- Baka Motion Data Pack;
- Pandora Behaviour Engine.

Original NEFARAM also already contains the relevant surrounding ecosystem, including:

- `[35 - Sexlab Content]`;
- BaboDialogue and BaboDialogue Stability Patch;
- SLHH Expansion;
- SexLab Survival;
- the Devious Devices stack elsewhere in the list;
- other adult gameplay and autonomous-event systems.

Do **not** install duplicate copies of frameworks that NEFARAM already supplies. Confirm the requirements against your current NEFARAM version and profile before adding optional files.

## Before installation

1. Clone your working MO2 profile.
2. Back up or export both the MO2 left-pane order and right-pane plugin order.
3. Use a disposable test save or a new test game.
4. Keep unrelated experimental changes out of the test profile.
5. Record the current Pandora output and MCM state so rollback remains simple.

## MO2 placement

Place SexLab Approach Redux in or near the original NEFARAM `[Sexlab Content]` section.

Use relative placement principles:

- keep the mod with other SexLab content rather than copying an absolute position from another profile;
- keep its required frameworks active and earlier in the left pane;
- inspect which files win every MO2 conflict;
- preserve any required master-before-dependent order in the right pane;
- place only relevant compatibility files after the components they are intended to support.

The correct exact position may change as NEFARAM evolves; use the original separator and preserve the relationships between frameworks, content, compatibility files, and generated output.

## Installation procedure

1. Install **SexLab Approach Redux 3.62** through MO2.
2. Inspect the archive structure, enabled plugin, scripts, animations, JSON data, and MCM files.
3. Review all MO2 conflicts and verify the plugin's masters.
4. Install only optional compatibility files that match systems actually present and enabled in your profile.
5. Ensure the current 3.62 `SLAppAutoMCM.json` has the intended conflict result; do not restore an older generated preset automatically.
6. Run Pandora.
7. Launch Skyrim only after Pandora completes cleanly.
8. Begin with conservative frequencies and probabilities rather than aggressive settings.

## Pandora

NEFARAM uses **Pandora, not FNIS**, for this workflow.

Rerun Pandora after installing SexLab Approach Redux because animation and behavior support are part of the integration process. Confirm that the correct MO2 profile is active, generate the output, review the result for blocking errors, and launch the game only after a clean Pandora pass.

If you later add, remove, or change related behavior or animation packages, regenerate Pandora again.

## xEdit audit and known warning

`SexLab Approach.esp` was checked with **SSEEdit 4.1.5**.

- **Processed records:** 5,546
- **Result:** one warning/error group
- **Affected quest:** `SLApproachAskForSex2Quest "SLApproachAsktoOtherQuest" [QUST:xx012AFD]`
- **Affected fragment:** `SLApp_QF_AskForSex2Quest_04012AFD`

The fragment contains three orphaned VMAD alias references:

```text
Alias_initialActor -> Alias[0]
Alias_PlayerRef    -> Alias[2]
Alias_TargetActor  -> Alias[3]
```

The quest's current **Aliases** section is empty.

Do **not** auto-clean the plugin or edit this VMAD/fragment blindly. Treat it as a known structural warning, most likely left over from an earlier quest layout, and specifically test the `AskForSex2` / ask-other branch in game.

The warning does not prevent the plugin from loading, the MCM from registering, or the current 3.62 settings from appearing. It is a focused gameplay-test requirement, not evidence that an unsupported repair should be invented.

## Clean MCM initialization

Version 3.62 ships an empty `SLAppAutoMCM.json`. It was validated as a clean initialization state when it won the MO2 conflict over an older file in `SKSE Output`.

With that clean 3.62 file active:

- the MCM registered correctly;
- all pages loaded;
- no blank fields were observed;
- newer options such as `OnlyinTown` and `Sex CoolTime` appeared;
- compatibility toggles for SLHH, BaboDialogue, FillHerUp, SexLab Survival, and DDI were present.

Do not blindly restore or import an older generated preset. First allow 3.62 to initialize cleanly and confirm that every page and field is available.

## Historical NEFARAM preset

An older generated preset was identified at:

```text
SKSE Output/SKSE/Plugins/BakaFactory/SLAppAutoMCM.json
```

It identifies itself as `NEFARAM - 263`, version `2`. Treat it only as a record of historical behavior, **not** as a drop-in preset for 3.62.

That preset favored moderate-to-high approach density and enabled several integrations, but it predates newer settings such as `OnlyinTown` and `Sex CoolTime`. Importing it blindly can leave new options undefined or carry event-density choices that are unsuitable for the current profile.

## Recommended first MCM strategy

Start from the clean 3.62 defaults and establish a stable basic approach loop before expanding the feature set.

- Keep approach frequency and probability conservative.
- Use meaningful cooldowns.
- Enable integrations deliberately, one at a time.
- Review `OnlyinTown` and `Sex CoolTime` explicitly.
- Review Unique Actor, relationship requirements, and player/NPC arousal thresholds.
- Avoid enabling every optional event or actor category at once.
- Save a new preset only after the current configuration has been tested.

The goal is occasional, context-appropriate interaction—not a continuous queue of NPC events.

## Compatibility and interaction notes

The following systems deserve focused monitoring. Their presence is not, by itself, proof of incompatibility.

### SLHH Expansion

Approach and SLHH have complementary roles, but both may initiate interactions. Watch for simultaneous starts, stacked dialogue, duplicate actor selection, control locks, or one system firing before the other has released the player.

### BaboDialogue

BaboDialogue is part of the same broader interaction ecosystem. Watch for repeated forcegreets, dialogue loops, package conflicts, and scene requests occurring too close together.

### Devious Devices

If DDI-related options are enabled, verify device detection, dialogue conditions, equip/unlock behavior, and clean restoration of the player state after scenes. Enable these options only after the basic approach system is stable.

### SexLab Survival

SexLab Survival can add its own contextual events and social pressure. Test approaches during normal Survival gameplay and shortly after Survival events. Adjust cooldowns before assuming a hard conflict.

### Other autonomous systems

TDF SexLab Aroused Rape, SL Dangerous Nights, defeat stacks, and random-event systems can also compete for player control, dialogue, actor reservation, or scene ownership. Monitor them as possible overlap sources rather than treating them as guaranteed incompatibilities.

## Event-density guidance

The main practical risk is several autonomous systems firing close together. Typical symptoms include:

- stacked forcegreets or dialogue windows;
- one scene starting while another system still owns the player;
- the same NPC being reserved by multiple systems;
- controls not being restored;
- NPCs remaining in an approach package;
- repeated events immediately after a prior event ends.

Before declaring incompatibility, lower chances or frequency, raise cooldowns, restrict contexts, and enable integrations in stages. Test one change at a time so the source of any overlap remains identifiable.

## In-game validation checklist

Test the following on the disposable profile and save:

- [ ] An NPC initiates an autonomous approach.
- [ ] Dialogue starts and ends cleanly.
- [ ] The NPC returns to normal AI afterward.
- [ ] Player controls are restored.
- [ ] Saving, fully exiting, and reloading remain safe.
- [ ] No repeated greeting or dialogue loop appears.
- [ ] Approach does not take simultaneous ownership with SLHH, BaboDialogue, or another autonomous system.
- [ ] The `AskForSex2` / ask-other branch works despite the documented xEdit warning.
- [ ] Behavior remains reasonable in a crowded city.
- [ ] Behavior remains reasonable in an inn.
- [ ] Exterior approaches work without persistent AI state.
- [ ] A low-density area does not produce abnormal polling or event spam.

Do not treat one successful scene as complete validation. Repeat events, transition between locations, and test save/reload after completed interactions.

## Troubleshooting

### Approaches are missing or broken

Verify the required frameworks, plugin masters, Pandora output, MCM registration, conditions, cooldowns, and actor eligibility. Confirm that the test context actually satisfies the configured rules.

### Too many events

Lower approach frequency and probability, raise cooldowns, use `OnlyinTown` or other context limits where appropriate, and disable optional event categories until the basic loop is stable.

### Events stack or compete

Reduce overlap with SLHH, BaboDialogue, SexLab Survival, defeat systems, and other autonomous-event mods. Re-enable integrations one at a time and leave enough time between events.

### The MCM has missing or strange fields

Ensure the empty 3.62 `SLAppAutoMCM.json` wins over any stale generated file in `SKSE Output`. Do not blindly import the historical version 2 preset. Allow the current MCM to initialize cleanly.

### xEdit reports the known VMAD warning

Do not auto-clean it and do not reconstruct aliases without authoritative evidence. Test the `AskForSex2` / ask-other branch in game and monitor the resulting dialogue, scene, and recovery behavior.

### An NPC or the player remains stuck

Stop using the affected save as a stable save. Reproduce the issue on the disposable profile, reduce neighboring autonomous systems, and identify which mod still owns dialogue, controls, the actor package, or the scene. Roll back the test profile if clean recovery cannot be established.

## Validation status and disclaimer

The following points are validated for SexLab Approach Redux 3.62 in the documented NEFARAM integration:

- technical installation;
- MO2 file-conflict review;
- required framework availability in NEFARAM;
- clean Pandora workflow;
- clean MCM initialization with the shipped empty JSON;
- correct appearance of current settings and compatibility toggles;
- documentation of the single known xEdit warning.

Full gameplay validation, rare edge cases, save longevity, and long-term coexistence tuning remain dependent on each user's enabled systems and MCM choices. This guide does not claim universal compatibility.

> **No custom patch is required for this integration.**

## Internal technical reference

For the detailed audit and test protocol, see the [SexLab Approach Redux internal integration document](../../06%20-%20GAMEPLAY/SEXLAB%20APPROACH%20REDUX/SEXLAB-APPROACH-REDUX-INTEGRATION.md).
