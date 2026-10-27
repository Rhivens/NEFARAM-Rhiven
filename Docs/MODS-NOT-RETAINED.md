# Historique des mods non retenus

Ce fichier conserve les décisions closes qui ne doivent plus encombrer la roadmap active. Il s'agit d'un historique, pas d'une liste de travaux à reprendre.

## HORDE 3.0.1

**Décision du 23/10/2026 : REJETÉ — Nether's Follower Framework 2.8.5 conservé.**

Le test de retrait a montré que `nwsFollowerFramework.esp` est un master direct de nombreux plugins générés ou propres à NEFARAM, notamment plusieurs `Synthesis_*.esp`, `_NEFARAM_PEGI16_DeviousFollower.esp`, `_NEFARAM_PEGI18_Babo.esp`, `_NEFARAM_____MAIN_____.esp` et `SDA NFF Patch.esp`. Remplacer NFF aurait nécessité une régénération Synthesis et des modifications transversales de plusieurs patches, sans bénéfice proportionné pour l'usage prévu. HORDE a été retiré du build et NFF réactivé.

## Public Whore Comments 1.7

**Décision : traité et non retenu.**

La fiche d'étude avait identifié comme points principaux la coexistence avec Public Whore et SLSF Fame Comments, la densité des commentaires et la compatibilité avec l'implémentation d'arousal du build. La décision de ne pas retenir le mod est close ; la [fiche d'étude](06%20-%20GAMEPLAY/PUBLIC%20WHORE/PUBLIC-WHORE-COMMENTS-INTEGRATION.md) reste disponible comme référence historique.

## RennasRanch 0.3.0

**Décision : non retenu.**

L'étude le classait comme un contenu conséquent à risque élevé, nécessitant des contrôles du worldspace, de Falkreath, de BodySlide, des animations, de Devious Devices, des overlays, des LOD et des scripts. Le candidat est fermé et ne doit pas être repris comme tâche active. La [fiche d'étude](06%20-%20GAMEPLAY/RENNAS%20RANCH/PONYPLAY-SECLUDED-VALLEY-INTEGRATION.md) reste disponible pour la traçabilité.
