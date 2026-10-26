# Bad Ends Revived: Windhelm 1.3.0

Source: https://www.loverslab.com/files/file/19047-bad-ends-revived-windhelm/

## About This File

### What is This Mod?

An Extension for my Prison Mod "Prison Alternative" which adds new events to the Experience.

Events are Themed around Bad Ends and Executions, inspired by the Original Mod by Torm.

Just a bit less Buggy.

## Requirements

- Prison Alternative (see above), and its requirements.
- Zap8(+)

## Installation

- Install with Mod manager of your choice and rum FNIS/Nemesis.
- When Loading/Starting a game, new Events will automatically register themselves and will show up in the "Event" Tab of Prison Alternative´s MCM.

## About NPC Executions

- This Feature should be considered as an Encore, rather than an meaningful Gameplay Element. NPC executions require manual activation via the chain on the Left side of the Gallows.
- Any NPC can be "marked" as follower by selecting them in the console and typing `setplayerteammate 1`. This will make them visible to the Device and a valid candidate for execution. They Also have to be somewhere in Windhelm in order to be detected by the script.

## Incompatibilities

- Devious Devices (soft incompatibility. If you know what you are doing, you can use this alongside DD, but it requires caution)
- The Original "Bad Ends" by Torm
- City overhauls for Windhelm (results might vary.)
- This mod makes navmesh changes to `CandleheartHallExterior` and `WindhelmBridge3`. So it will conflict with mods which edit the same Area. Putting this mod far down in the load order COULD make it work.

## Troubleshooting

- If you get Black screen while in Prison: Go into PA´s MCM and manually reset the Registry and re-Register the Events. check if all Events are correctly displayed in the List. If not, repeat.
- Its recommended to use a new save when using this mod. While older saves seem to work in the vast majority of cases, using an older save can sometimes result in scenes becoming stuck.
- You are on SSE and the Ankle chains have missing textures? use this and let it overwrite Zap files: `SSE_ZapAnkleChainFix.zip`

## Notes NEFARAM-Rhiven

- **Audit xEdit obligatoire** avant validation finale.
- NEFARAM-Rhiven contient déjà **Capital Windhelm Expansion** ainsi que plusieurs correctifs de navmesh et de collision.
- Vérifier en priorité les cellules / zones `CandleheartHallExterior` et `WindhelmBridge3`.
- Ne pas placer automatiquement le plugin PAMA "tout en bas" sans vérifier les overrides : cela pourrait corriger PAMA tout en annulant des corrections de Capital Windhelm Expansion.
- Premier test conseillé sans Devious Devices équipés.
- Vérifier le registre des Events de Prison Alternative après installation.
- Si les ankle chains ont des textures manquantes sur SSE/AE, conserver le correctif `SSE_ZapAnkleChainFix.zip` comme piste dédiée.
