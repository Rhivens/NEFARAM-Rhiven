# Orkish Bounty Hunters 0.4

Source: https://www.loverslab.com/files/file/31675-orkish-bounty-hunters/

## About This File

Did you know that Vanilla Skyrim has bounty hunters who will come after you If you have a high enough Bounty somewhere?

No? well, no problem. They are pretty shitty anyway.

BUUUT, wouldn't it be cool if committing crimes (even minor ones) would actually result in someone competent coming after you in order to cash in that Bounty?

Apparently there are some people who Think so, and therefore, I made this mod.

## So, what is this Mod?

Just as I said, It adds a specialized group of Bounty hunting orks to the world which will send Hunting parties of varying strength after the player if their Bounty exceeds a MCM configurable Threshold.

The mod was initially meant to serve complement to my other mod Prison Alternative, by providing some means for the player to actually end Up in Jail. But as Development progressed, I came up with with a few features which make this mod worthwhile on its own.

## Hunting parties

Whenever your bounty in one of the Holds exceeds the threshold set in the MCM, there is a possibility that you might get ambushed By a hunting party.

Composition and strength of those parties increases with your Bounty. There is a large number of checks in place to ensure these attacks dont happen while anything of importance is going on, so it shouldn't break any other mods or vanilla story Events.

Attacks will only happen in the Tamriel worldspace — not in interiors, cities, Solstheim, or modded locations like Bruma.

## Specialized combat

In order to ensure compatibility with other combat defeat mods, The Orks use a special scripted poison damage which will accumulate with each hit you take.

The total poison accumulation is indicated by a small onscreen widget and increased poison levels will increasingly blur your vision and reduce your movement speed.

If the poison meter reaches 100%, you will fall unconscious.

There is a chance for your follower to save you if they are nearby and still standing.

## Defeat Outcomes

When you are defeated and your follower didnt manage to save the day, an Outcome will be selected. Probabilities can be adjusted in the MCM.

The first and Default outcome is the simple transfer To Jail.

This works For PA-enabled Jails, but also for Vanilla Jails.

It does **not** support POP or DCL.

## Ork camps

The other outcome for now is the Ork camp.

This temporary camp serves as a stopgap for the night before the Player is brought to a more permanent location.

Only regular Jail is supported for now, but more dangerous locations may be added in the future.

When brought to this temporary camp, the Player has the choice between trying to escape or waiting it out.

Depending on how many PA-Bad Ends mods are installed, going to Jail might be fairly dangerous, so escaping can become a meaningful alternative.

## Escapes

If the player Decides to attempt an Escape, the primary objective is to get away from the camp without waking up the sleeping orks.

Due to the after effects of the poison, movement speed is reduced and the player will go down in a single hit if the orks get to them.

Optionally, the player can also try to retrieve their items from the camp chest and free followers from the cage.

Followers will also get recaptured with a single hit if the orks are alarmed, but may serve as a distraction during the escape.

## Aftermaths

If you get recaptured during your Escape, the Orks will react accordingly.

If **Pama's Deadly Furniture** is installed, some outcomes can become significantly more severe or final for the player or companions.

If the escape was successful but gear or followers had to be left behind, a small follow-up quest allows the player to retrieve them later or discover what happened to them.

## Notes

This entire Project is still in a relatively early phase, so the outcomes and content are somewhat limited right now, but may receive major expansions in the future.

The currently available content has gone through testing by the author and supporters and should be mostly stable, although issues may still exist.

## Compatibility

### Compatible

- Pretty much all other combat Defeat mods
  - Avoid using surrender hotkeys during OBH events.
- Prison Alternative — highly recommended.
- Pama's Deadly Furnitures — needed for some outcomes.
- Followers — system supports up to three followers.

### Incompatible / Risky

- Devious Devices
  - Just having DD installed **could** be fine.
  - Wearing DD restraints during an OBH event can break the event.
- Certain standalone followers which use scripted effects/teleportation.
- Follower frameworks which use similar teleportation/scripting, including AFT or NFF.

## Notes NEFARAM-Rhiven

- Très bon complément à **Prison Alternative**, car il fournit une voie organique vers l'incarcération : prime → chasse → KO → transfert en prison.
- Le système de défaite basé sur un **poison scripté** est conçu pour éviter la concurrence directe avec les frameworks de defeat classiques.
- Test spécifique à réaliser avec **Acheron / Practical Defeat** afin de vérifier que le KO OBH ne déclenche pas une récupération concurrente.
- Ne pas utiliser de hotkey de surrender pendant un événement OBH.
- Premier test conseillé sans aucun Devious Device équipé.
- **Pama's Deadly Furniture** doit être présent pour certains outcomes avancés.
- Le support followers est limité à trois compagnons pour les événements OBH.
- À placer comme **couche périphérique / générateur d'arrestations** après le cœur Prison Alternative dans l'organisation logique du bloc PAMA.
