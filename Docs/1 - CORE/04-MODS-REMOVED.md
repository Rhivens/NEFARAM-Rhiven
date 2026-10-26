# 04 - Removed / disabled mods

This file tracks stock NEFARAM mods that are deliberately disabled, removed or superseded.

No stock mod should be listed here unless the change is intentional and understood.

## Current changes

| Mod | Action | Reason | Replaced by | Test result |
|---|---|---|---|---|
| Fertility Mode | Disabled / left unchecked | Being Female NG is preferred for cycle, HUD and pregnancy mechanics; running two fertility frameworks in parallel is intentionally avoided | Beeing Female NG 3.6.0 - Rhiven | BFNG technical initialization and animation integration validated |
| Road Signs Overhaul 2.0 - Rhiven | Disabled / retained in MO2 | Added sign by Riverwood visibly displaced / floating (ref `FE6B8849`, base `000D8D9B`); disappeared with RSO disabled on a diagnostic save | Point The Way - Rhiven + My Road Signs are Beautiful - French | French road signs visible and correctly assembled at tested Riverwood locations; wider/LOD checks pending |
| Road Signs 2.0 - Questionable Clutter Remover (BOS) - Rhiven | Disabled / retained in MO2 | Optional patch belonging to deactivated Road Signs Overhaul stack | Point The Way - Rhiven + My Road Signs are Beautiful - French | No longer needed with RSO disabled |
| Road Signs Overhaul 2.0 - Blended Roads Patch(BOS) - Rhiven | Disabled / retained in MO2 | Optional patch belonging to deactivated Road Signs Overhaul stack | Point The Way - Rhiven + My Road Signs are Beautiful - French | No longer needed with RSO disabled |
| Practical Defeat Reanimated | Disabled in Naked Defeat test profile / rollback retained | Full Acheron consequence chain overlaps Naked Defeat; would make validation ambiguous | Naked Defeat 6.50 via Acheron Bridge | Final removal pending successful Naked Defeat smoke test |
| Practical Defeat Reanimated Voicepack | Disabled in Naked Defeat test profile / rollback retained | Voicepack belongs to Practical Defeat and is not needed when the parent mod is disabled | Naked Defeat stack | Pending same smoke-test verdict as Practical Defeat |
| YameteKudasai | Disabled in Naked Defeat test profile / rollback retained | Its Acheron YAML consequences compete with Naked Defeat and cover similar defeat / surrender outcomes | Naked Defeat stack for primary defeat consequences | Keep fully disabled during smoke test; possible future return only for niche Hunter's Pride / NPC-defeat functions |
| Naked Defeat - EXTRA - OAR Crawl Animations V2 - Rhiven | Disabled / rollback retained | Bowed Animations fixed overwrites the same Naked Defeat OAR locomotion files | Naked Defeat - EXTRA - OAR Bowed Animations fixed - Rhiven | Bowed retained as active variant |

## Template

| Mod | Action | Reason | Replaced by | Test result |
|---|---|---|---|---|
| Example Mod | Disabled | Conflict / preference / obsolete | Replacement Mod - Rhiven | Pending |
