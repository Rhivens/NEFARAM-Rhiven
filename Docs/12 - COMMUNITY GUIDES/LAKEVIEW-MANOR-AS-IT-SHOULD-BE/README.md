# Lakeview Manor - As It Should Be

This guide documents the safe installation and Hearthfire construction sequence for **Lakeview Manor - As It Should Be** in a NEFARAM setup.

The mod changes Lakeview Manor's main house and, when selected in the FOMOD, its cellar and exterior. It relies on a specific Hearthfire construction state, so the order in which the base house, wings, furniture and cellar objects are built matters. Extra furniture or different wings can leave the vanilla construction state out of step with the layout expected by the mod.

> **Community modification warning:** Back up your NEFARAM profile and use a named backup save before installing or building. Do not test the sequence for the first time on your only long-term save.

## Prerequisites and precautions

Before starting:

- use a mod manager and read every FOMOD option;
- make a named save before any Lakeview construction and back it up outside the active save folder if possible;
- complete the prerequisite quests given by the Jarl of Falkreath;
- buy the Lakeview Manor plot;
- avoid building extra furniture before the mod's required conversion steps;
- if Lakeview is already heavily built in the current save, do not assume the procedure can safely reconstruct or undo those choices;
- use the optional Creation Club Fishing compatibility patch only when CC Fishing is present and the patch applies to your setup.

If you have never built a Hearthfire house, the mod author suggests practicing first: build the complete vanilla house and its wings to learn the system, then revert to the named save created before the practice build.

## Installation branches

The FOMOD provides two main files that are independent of each other, plus optional files. Follow the construction branch that matches what you installed.

### `LKVM Main House`

This branch covers the main-house overhaul. Follow steps 1–11 below, then complete steps 12–14 for the cellar and exterior when those parts are included in your setup.

### `LKVM Cellar and Exterior`

If this is the only main file installed, skip the main-house construction steps and go directly to steps 12–14.

The Rhiven load-order snapshot places the Lakeview files together in its existing homes area. Treat that as an original NEFARAM/Rhiven placement reference, not as a requirement to create or copy a custom separator name. Preserve the relevant relative file order from your own FOMOD choices and resolve right-pane placement from actual conflicts.

## Author build procedure

Follow this sequence exactly.

1. Make a named save game and, preferably, back it up.
2. Download and install the mod with your mod manager. Let the FOMOD guide the selection of the two independent main files and any optional files.
3. Buy the Lakeview plot if you do not already own it. Complete the Falkreath Jarl's prerequisite quests first.
4. Travel to Lakeview.
5. Select the correct branch:
   - If `LKVM Main House` is installed, continue with steps 6–11.
   - If only `LKVM Cellar and Exterior` is installed, skip to steps 12–14.
6. Activate the Drafting Table and build `Small House Layout`. Then activate the Carpenter's Workbench and build all of its structural components, including the walls and floor.
7. Repeat the construction process for:
   - `Main Hall`
   - `East Wing – Kitchen`
   - `North Wing – Alchemy Laboratory`
   - `West Wing – Bedroom`
8. Return to the Drafting Table and select `remodel house into entryway`.
9. Enter the house.
10. At the bedroom workbench, build only:
    - `Child's Bed & Chest x 2`
    - `Double Bed`

    > **DO NOT BUILD ANYTHING ELSE AT THE BEDROOM WORKBENCH.**

11. Return to the Drafting Table outside and disable all workbenches.
12. Build the cellar. Enter it and build only:
    - `Child Practice Dummy`

    > **DO NOT BUILD ANYTHING ELSE IN THE CELLAR.**

13. Exit the cellar and disable its workbench.
14. Build the `Animal Pen`, `Garden`, `Apiary` and `Stable` if they have not already been built.

## Safe test workflow

1. Keep the named pre-build save and its backup untouched.
2. Perform the complete construction sequence on a test copy or otherwise recoverable save.
3. Verify the house exterior, entrance, main interior and intended furniture.
4. Verify the cellar and its required practice dummy.
5. Verify the animal pen, garden, apiary and stable when built.
6. If the optional CC Fishing patch is active, verify the relevant Fishing integration as well.
7. Enter and leave the house and cellar, then save, fully exit the game and reload before continuing normal play.

Do not treat a successful first entrance as complete validation. Check the built layout carefully before committing the result to a long playthrough.

## Troubleshooting

### The wrong wings were selected

The author procedure specifically calls for the Kitchen, Alchemy Laboratory and Bedroom wings. Stop the test and return to the named pre-build save rather than assuming another wing combination is supported.

### Extra bedroom furniture was built

The bedroom instruction is intentionally restrictive. Return to the named pre-build save and repeat the sequence, building only the two `Child's Bed & Chest` sets and the `Double Bed`.

### Extra cellar objects were built

The cellar instruction is also intentionally restrictive. Return to the named pre-build save and build only the `Child Practice Dummy` inside the cellar.

### Workbenches were not disabled

Return to the relevant point in the procedure if the current save still permits it: disable all exterior workbenches after the main-house steps, and disable the cellar workbench after leaving the cellar. If the state is uncertain, revert to the backup save and repeat the sequence cleanly.

### The cellar was built incorrectly

Do not add more objects in an attempt to correct it. Compare the save against steps 12–13 and revert to the named pre-build save when the required state cannot be confirmed.

### The mod was installed after the house was already heavily built

This guide does not establish a safe conversion path for a heavily constructed existing Lakeview Manor. Keep that save intact, test the mod from a pre-construction or disposable save, and consult the mod author's documentation before attempting any migration.

### The layout still looks wrong

Confirm the installed branch, the selected wings, the two restricted furniture steps, disabled workbenches and any optional compatibility patch relevant to the setup. Do not invent corrective console commands or continue adding furniture; revert and reproduce the documented sequence first.

## Validation status

### Author procedure

The construction sequence and the two strict furniture restrictions come from the mod author's process.

### Maintainer testing

The maintainer has personally followed and validated this exact sequence in two separate Skyrim environments:

- **Nolvus**
- **NEFARAM 16**

That is useful real-world confirmation of the process, not a universal guarantee for every load order, save state or later NEFARAM 17.x customization. Test safely in your own environment before continuing a long playthrough.

## Internal reference

For the maintained Rhiven integration notes, exact local file stack and current-version status, see:

[Lakeview Manor - As It Should Be internal documentation](../../07%20-%20HOMES/LAKEVIEW-MANOR-AS-IT-SHOULD-BE.md)
