# Pama Sovngarde Aftermath 1.0.0

Source: https://www.loverslab.com/files/file/45250-pama-sovngarde-aftermath/

## What is This Mod?

A little quality of life addition to my other Mods (namely Deadly Furnitures), which allows the player to continue the Game even After being executed by some Device. No more immersion Breaking reloads!

This is achieved by Introducing a new Repeatable Questline within Sovngarde, where the Player is teleported upon being executed by Any Deadly Furniture or a Prison Alternative related Scenario.

Complete the Quest, return to Tamriel, and your Adventures can continue.

The Quest Itself is fairly straightforward and will give you plenty of pointers, so you shouldn't have any difficulties completing it.

## What This Mod is NOT

This is **NOT** a combat Defeat mod.

It wont do Anything on its own and will only trigger when another mod explicitly calls it. As I said, Its meant as an addon for MY other mods.

This has the Added benefit that its perfectly compatible with REAL combat defeat mods like Archereon, SL Defeat, Daymyol, and any other.

## Follower Support

This mod supports up to **8 followers**.

If a follower dies to a Deadly Furniture, their Soul will also be moved to Sovngarde and trapped there in one of the devices scattered throughout the Fog.

When the Player Ends up in Sovngarde themselves, they will have the option to Save their companions and return to Tamriel Alongside them.

This should work with most Custom Followers and Follower Frameworks, but results might vary on a case to case basis.

## Notes

- While this mod is fully playable and stable, its not finished, which means that NPC's within the quest might allude to features which aren't implemented yet.
- This mod keeps itself disabled by default, which means you wont see any of its assets or changes within Sovngarde if you go there via the Vanilla quest line or `coc`.
- There are some MCM settings available to limit the amount of humiliation you wanna experience during your stay in Sovngarde.
- Dialogues are written for Female PC, but the Mod will work just fine with males as well.

## Supported Mods

You will need one of those to send you to Sovngarde and start the quest:

- Pama´s Deadly Furniture (scripts)
- Bad Ends Revived: Windhelm
- Bad Ends Revived: Riften
- Bad Ends Revived: Solitude
- Prison Alternative - Outdoor Event Pack
- Prison Alternative - Punishment Pack

## Requirements

- Pama Deadly Furnitures and all its requirements
  - Minimum Public Version: V 3.3.2
  - Minimum Beta Version: V 3.1.9
  - V 3.4.0 or higher strongly recommended by the author
- NGdecaps / Next-Gen Decapitations
- ConsoleUtil Extended

## Installation

- Install with Vortex or MO2.
- Run FNIS / Nemesis / Pandora.
- Its recommended to use a new Save.

### Next-Gen Decapitations configuration

If you Want to get your Head Back in Sovngarde after Dying to a Guilloutine, edit:

`SKSE\Plugins\NextGenDecapitations.ini`

Use:

```ini
[Misc]
# Determines if a decapitated NPC can be resurrected.
# 0: No
# 1: Yes, but the head remains severed
# 2: Yes, and the head is restored
iCanBeResurrected = 2

# Enable advanced NPC maintenance features (1 enable, 0 disable).
# This ensures that heads display correctly and do not reappear unintentionally.
bAdvancedNPCMaintenance = 0
```

## Incompatibilities

- Devious Devices
  - Soft incompatibility.
  - Should be fine as long as you don't actually wear any of its devices.
- Devious Cursed Loot
  - No.
- Random Sex mods
  - Can potentially break scenes.

## Notes NEFARAM-Rhiven

- Ce mod est une **brique centrale du chantier PAMA** dès lors que les événements létaux sont activés.
- Il ne remplace pas Acheron : il n'agit pas comme combat defeat framework et doit être appelé explicitement par un mod PAMA compatible.
- Dans NEFARAM-Rhiven, **ConsoleUtil Extended est déjà présent**.
- **Next-Gen Decapitations** doit être ajouté et configuré avec les deux paramètres ci-dessus.
- Test impératif à réaliser :
  - exécution PAMA réelle ;
  - transfert vers Sovngarde ;
  - quête de retour ;
  - retour en Tamriel ;
  - restauration correcte après décapitation ;
  - absence d'interception parasite par Acheron / Practical Defeat.
- Premier test conseillé sans aucun Devious Device équipé.
- Le mod est à installer avant la vraie partie si possible, conformément à la recommandation de nouvelle sauvegarde.
