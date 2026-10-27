# Vel'Dun UI for NEFARAM

> **Status: validated in-game on a NEFARAM 17.3.x based setup.**
>
> This guide describes a practical way to replace the **Dear Diary Dark Mode visual presentation** with **Vel'Dun UI** while keeping the existing NEFARAM UI framework intact.

The goal is not to dismantle the whole NEFARAM interface stack. Vel'Dun is used as the new visual layer, while functional UI mods and compatibility patches can remain in place where they are still required.

---

## 1. Validated baseline

The configuration used for validation was based on:

- **NEFARAM 17.3.x**
- validated specifically on a **17.3.8** environment
- Skyrim AE runtime **1.6.1170**
- **SkyUI 5.2**
- **MCM Helper 1.5.0**
- Mod Organizer 2

### Important SkyUI compatibility note

Vel'Dun does **not** require a migration to SkyUI 6.0 for this setup.

The Vel'Dun author confirmed that the UI can work with **SkyUI 5.2**, which is already used by NEFARAM. This makes it possible to integrate Vel'Dun without replacing the existing SkyUI foundation.

> **Recommended approach: keep SkyUI 5.2 and MCM Helper 1.5.0.**

---

## 2. Versions currently validated

The versions retained during testing are:

- **Vel'Dun UI main 1.0.6**
- **Vel'Dun UI Patches 1.0.6**

### About Vel'Dun 1.0.7

The **main Vel'Dun UI 1.0.7** caused an issue with the Escape / system menu during testing.

For that reason:

> **Vel'Dun UI main 1.0.7 is not considered validated in this guide.**

If you encounter Escape-menu problems, verify that the main Vel'Dun UI is still on **1.0.6**.

### Important distinction: Vel'Dun UI Overhauls

The **Vel'Dun UI Overhauls** installer may display **1.0.7**.

This is a separate module and must not be confused with the version of the main Vel'Dun UI package.

---

## 3. Before you start

Before changing the interface:

1. clone your current MO2 profile if possible;
2. keep a backup of your current modlist / left-pane order;
3. keep a backup of your plugin load order;
4. use a safe test save for the first in-game checks.

UI changes are usually easy to reverse in MO2, but keeping the original NEFARAM profile untouched makes troubleshooting much easier.

---

## 4. Create a dedicated MO2 separator

Create a new separator in the MO2 left panel, for example:

```text
UI-CUSTOM
```

Place the Vel'Dun-related files in this dedicated block.

Do not rely on separator numbers from another modlist. The exact position of separators can differ between NEFARAM installations.

---

## 5. Core Vel'Dun files

The core validated setup uses:

```text
Vel'Dun UI
Vel'Dun UI Patches
Vel'Dun UI Overhauls
```

Recommended relative order:

```text
Vel'Dun UI
Vel'Dun UI Patches
Vel'Dun UI Overhauls
```

Lower entries in the MO2 left panel have higher file priority.

Vel'Dun UI Overhauls should therefore be allowed to win the visual files related to the options you intentionally selected in its installer.

---

## 6. Dear Diary Dark Mode: what should be removed?

Do **not** blindly uninstall or disable the entire Dear Diary Dark Mode stack.

This migration is primarily a **visual replacement**.

Some DDDM-related files or compatibility patches may still be required by other installed mods. The safer approach is:

1. keep the existing NEFARAM UI framework;
2. install Vel'Dun lower in the MO2 left panel;
3. inspect file conflicts;
4. allow Vel'Dun to win the intended visual interface files;
5. keep functional compatibility patches where they are still needed.

> The objective is to replace the appearance, not to remove every component that happens to mention Dear Diary Dark Mode.

After each conflict change, test the affected menus in-game.

---

## 7. Vel'Dun UI Overhauls options

Only install options for mods and menus that are actually present in your setup.

Do **not** select every FOMOD option automatically.

### Modern Wait Menu

If you use **Modern Wait Menu**:

1. install the original Modern Wait Menu;
2. place it before Vel'Dun in the custom UI block;
3. in **Vel'Dun UI Overhauls**, select:

```text
Wait/Sleep Menu
→ 2. Modern Wait Menu
```

The circular wait menu and Vel'Dun skin were confirmed visually in-game.

The full waiting mechanic itself should still be tested on your own setup.

Suggested order:

```text
UI-CUSTOM

Modern Wait Menu
Vel'Dun UI
Vel'Dun UI Patches
Vel'Dun UI Overhauls
```

### The Dragonborn's Bestiary

If **The Dragonborn's Bestiary** is installed and you use a 16:9 display, the validated Overhauls choice was:

```text
2A. Bestiary Patch
```

The Vel'Dun Bestiary skin was observed working in-game.

If you use another aspect ratio, choose the option appropriate to your own setup.

### Quest Journal

If your setup contains only **Knotwork for SkyUI V5** and does **not** contain Quest Journal Overhaul, choose:

```text
Quest Journal
→ Skip
```

If your installation does include Quest Journal Overhaul, select the option that matches your actual installed mod instead.

### Other optional patches

Options for components such as RaceMenu, QuickLoot or other supported menus should only be installed when the corresponding mod is present.

> Match the Vel'Dun FOMOD to your installation. Do not build your installation around every available Vel'Dun patch.

---

## 8. Generic MO2 layout

A simple community layout can look like this:

```text
UI-CUSTOM
├─ Modern Wait Menu                 # optional
├─ Vel'Dun UI
├─ Vel'Dun UI Patches
└─ Vel'Dun UI Overhauls
```

Additional UI mods can remain elsewhere in the normal NEFARAM stack unless a specific Vel'Dun option requires them to be placed near this block.

The important point is the relative priority of the Vel'Dun files, not a specific separator number.

---

## 9. Conflict strategy

Do not resolve UI conflicts by making Vel'Dun overwrite everything indiscriminately.

### Vel'Dun should normally win

For features selected in Vel'Dun UI Overhauls, the visual SWF/interface files provided by Vel'Dun should generally win.

During validation, examples included:

```text
sleepwaitmenu.swf
PlatformButtons.swf
bestiarymenu.swf
bestiarywidget.swf
favoritesmenu.swf
```

These files were allowed to win when their corresponding Vel'Dun feature was intentionally selected.

### NEFARAM functional patches may still need to win

A file conflict is not automatically a problem.

Some NEFARAM patches exist for functional compatibility rather than appearance. Do not override those blindly just because Vel'Dun is installed later.

Recommended method:

1. open the **Conflicts** tab in MO2;
2. identify which file is being overwritten;
3. determine whether it is primarily visual or functional;
4. keep Vel'Dun winning the intended visual asset;
5. preserve functional fixes when required;
6. test the affected menu in-game.

---

## 10. Optional HUD integrations

Vel'Dun does not require a complete HUD rebuild.

You can continue using your preferred HUD and widget stack.

### Needs Widget AIO

**Needs Widget AIO** is a useful optional companion because it provides a layout that integrates well with Vel'Dun and can centralize needs information from:

- **SunHelm**
- **Bathing in Skyrim**

If you use Needs Widget AIO, an older complementary Bathing in Skyrim / Keep It Clean widget is generally unnecessary and can be disabled to avoid duplicate needs displays.

Needs Widget AIO is **optional** and is not required for Vel'Dun itself.

### Other HUD components

Existing HUD systems such as SkyHUD, TrueHUD, A Matter of Time, Oxygen Meter, Casting Bar, STB widgets or similar tools can remain in your setup.

Their position, scale and visibility should be calibrated according to your own screen resolution and preferences.

---

## 11. In-game validation checklist

After installing Vel'Dun, test the interface before continuing a long playthrough.

### Core menus

- [ ] Main / system menu
- [ ] Escape menu
- [ ] Inventory
- [ ] Magic menu
- [ ] Favorites
- [ ] Map
- [ ] Console
- [ ] MCM
- [ ] SkyUI item preview / 3D object positioning

### Optional menus

Test these only if installed:

- [ ] Modern Wait Menu
- [ ] The Dragonborn's Bestiary
- [ ] Quest Journal modifications
- [ ] QuickLoot or other patched menus

### HUD

- [ ] HUD remains readable
- [ ] no invisible panels
- [ ] no missing icons
- [ ] no broken fonts
- [ ] no duplicated widgets
- [ ] no important widget overlaps
- [ ] no input / hotkey conflicts

Finally:

1. exit Skyrim completely;
2. restart the game;
3. verify that the UI still loads correctly;
4. confirm that any configurable HUD settings persist as expected.

---

## 12. Troubleshooting

### Escape / system menu is broken

First check the version of the **main Vel'Dun UI package**.

The main **1.0.7** build caused an Escape-menu issue in the validated test environment.

Return to:

```text
Vel'Dun UI main 1.0.6
```

and test again.

Do not confuse this with a **Vel'Dun UI Overhauls** installer that may itself display version 1.0.7.

### A menu still looks like Dear Diary Dark Mode

Check the MO2 left-pane conflict priority.

Make sure the relevant Vel'Dun SWF or interface file is actually winning.

Also verify that the correct option was selected in the Vel'Dun FOMOD.

### A patched menu is missing or broken

Check that:

1. the original mod is really installed;
2. the matching Vel'Dun patch was selected;
3. the correct aspect-ratio option was selected;
4. another UI mod is not overwriting the same SWF afterward.

### Duplicate needs widgets

If you use **Needs Widget AIO**, disable older redundant needs widgets where appropriate.

In particular, an older complementary **Keep It Clean / Bathing in Skyrim widget addon** is not needed when Needs Widget AIO already provides the required Bathing in Skyrim information.

### Strange UI behavior after adding optional reskins

Temporarily disable the optional reskin and test again.

Vel'Dun itself should be validated first before additional visual layers are added.

---

## 13. Validation status

The following have been validated in-game in the reference NEFARAM-based setup:

- Vel'Dun UI main **1.0.6**
- Vel'Dun UI Patches **1.0.6**
- Vel'Dun UI Overhauls integration
- operation with **SkyUI 5.2**
- operation with **MCM Helper 1.5.0**
- general menu appearance
- Modern Wait Menu visual integration
- Bestiary visual integration
- use of Vel'Dun as the visual winner over the relevant stock / Dear Diary Dark Mode interface files

Some optional menu functions, HUD positions, widget layouts and hotkeys remain dependent on each user's own installation.

> **Vel'Dun is validated as a working NEFARAM UI replacement path, but optional UI combinations should still be tested individually.**

---

## 14. Recommended final approach

For most NEFARAM users, the safest migration is:

```text
Keep the existing NEFARAM UI framework
        ↓
Keep SkyUI 5.2 + MCM Helper 1.5.0
        ↓
Create UI-CUSTOM
        ↓
Install Vel'Dun UI 1.0.6
        ↓
Install Vel'Dun UI Patches 1.0.6
        ↓
Install only the required Vel'Dun UI Overhauls options
        ↓
Inspect MO2 file conflicts
        ↓
Let Vel'Dun win the intended visual assets
        ↓
Test every affected menu in-game
```

This keeps the migration reversible and avoids unnecessary changes to the rest of the NEFARAM interface stack.

---

## Advanced internal reference

The detailed integration notes used to build this community guide are available here:

[Vel'Dun UI / HUD internal integration notes](../../05%20-%20UI-HUD/VEL'DUN.md)
