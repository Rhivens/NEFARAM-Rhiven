# Intégration PAMA — Prison Alternative / NEFARAM-Rhiven

> **Statut : bloc principal PAMA installé et validé pour l'intégration dans NEFARAM-Rhiven**
>
> Le cœur complet de PAMA est maintenant installé et les principaux audits xEdit ciblés et tests en jeu ont été effectués. Les quelques éléments restants relèvent d'observations à long terme / pendant une partie réelle et ne bloquent actuellement pas l'intégration.

## Position par rapport à NEFARAM d'origine

NEFARAM d'origine utilise des séparateurs génériques **Added Mods** vers le bas du panneau gauche de MO2.

La configuration Rhiven conserve ce principe, mais la section personnelle a été réorganisée et **numérotée** afin de garder une structure lisible et reproductible.

L'écosystème PAMA est regroupé dans son propre séparateur dédié :

`44 - PRISON PAMA SYSTEM`

Ce séparateur n'existe **pas** dans NEFARAM d'origine. Il appartient à l'organisation Rhiven ajoutée par-dessus **NEFARAM 17.3.7**.

### Ordre logique utilisé pour le bloc PAMA

1. Next-Gen Decapitations - Sovngarde INI - Rhiven
2. Pama's Deadly Furniture 3.4.5 Revision 2
3. Prison Alternative 2.0.3
4. Pama Sovngarde Aftermath 1.0.0
5. Punishment Pack 1.3.0
6. Outdoor Event Pack 1.3
7. Bad Ends Windhelm 1.3.0
8. Rhiven Windhelm patches
9. Bad Ends Riften 1.3.2
10. Bad Ends Solitude 1.8.0 Revision 2
11. PAMA - Solitude Location Patch - Rhiven
12. Orkish Bounty Hunters 0.4

Cela décrit principalement le **panneau gauche de MO2 / l'architecture fonctionnelle**. Ne le recopiez pas aveuglément dans l'ordre des plugins du panneau droit sans vérifier les masters et les overrides gagnants.

## Objectif

L'objectif est d'ajouter un écosystème PAMA / Prison Alternative cohérent à NEFARAM-Rhiven, tout en préservant autant que possible l'architecture NEFARAM existante.

Composants principaux retenus :

1. **Pama's Deadly Furniture 3.4.5 Revision 2**
2. **Prison Alternative - A modular Prison System 2.0.3**
3. **Pama Sovngarde Aftermath 1.0.0**
4. **Prison Alternative - Punishment Pack 1.3.0**
5. **Prison Alternative - Outdoor Event Pack 1.3**
6. **Bad Ends Revived: Windhelm 1.3.0**
7. **Bad Ends Revived: Riften 1.3.2**
8. **Bad Ends Revived: Solitude 1.8.0 Revision 2**
9. **Orkish Bounty Hunters 0.4**

## Architecture fonctionnelle

```text
Pama's Deadly Furniture
        ↓
Prison Alternative
        ↓
Pama Sovngarde Aftermath
        ↓
Punishment Pack / Outdoor Event Pack / Bad Ends
        ↓
Orkish Bounty Hunters
```

- **Deadly Furniture** fournit la couche technique des dispositifs létaux et non létaux.
- **Prison Alternative** est le système de prison central et le registre des événements.
- **Sovngarde Aftermath** assure la continuité après certaines exécutions PAMA.
- **Punishment / Outdoor / Bad Ends** ajoutent des événements de prison et régionaux.
- **Orkish Bounty Hunters** offre une voie dynamique vers l'arrestation / l'emprisonnement.

## Dépendances importantes déjà présentes dans NEFARAM-Rhiven

La configuration comprend déjà les fondations importantes utilisées par cette pile :

- SKSE
- SkyUI
- SexLab Framework
- ZaZ Animation Pack
- powerofthree's Papyrus Extender
- Pandora
- ConsoleUtil Extended
- Acheron - Death Alternative
- Practical Defeat Reanimated
- Devious Devices
- Troubles of Heroine
- Simple Slavery / Simple Slavery Rebuild

## Next-Gen Decapitations

Next-Gen Decapitations est fortement recommandé par Deadly Furniture et requis par Sovngarde Aftermath.

Dans la configuration Rhiven, le mod d'origine reste dans le bloc d'ajouts SFW et un override MO2 dédié sert à la configuration propre à Sovngarde :

`Next-Gen Decapitations - Sovngarde INI - Rhiven`

Réglages :

```ini
[Misc]
iCanBeResurrected = 2
bAdvancedNPCMaintenance = 0
```

Le mod d'origine reste ainsi intact et la configuration propre à PAMA est isolée.

## Notes de compatibilité

### Devious Devices

PAMA considère Devious Devices comme une **incompatibilité légère** dans plusieurs cas.

La présence de DD peut convenir, mais les problèmes deviennent beaucoup plus probables si le joueur porte activement des entraves DD lorsqu'une arrestation, une incarcération ou un événement PAMA tente d'équiper et de contrôler ses propres entraves.

Règle pratique pour les tests :

- gardez DD installé ;
- évitez les entraves DD actives pendant les premiers tests PAMA ;
- si un problème survient en partie réelle, reproduisez-le avec exactement le même état d'entraves avant de modifier quoi que ce soit.

### Devious Cursed Loot

DCL ne fait pas partie de cette configuration et n'est volontairement pas ajouté à la pile PAMA.

### Acheron / systèmes de défaite

Prison Alternative peut coexister avec des systèmes de défaite.

Orkish Bounty Hunters est particulièrement intéressant, car il utilise son propre mécanisme scripté de poison / neutralisation au lieu de réduire la santé du joueur à zéro. Pendant les tests, cela a évité l'interception par Acheron / Practical Defeat et a permis à OBH de conserver le contrôle de sa propre séquence de défaite.

### Mods de scènes aléatoires

La documentation PAMA avertit que des mods lançant des scènes aléatoires au mauvais moment peuvent interrompre les événements PAMA.

Cela reste un point à surveiller pendant la partie réelle, et non une incompatibilité confirmée dans la configuration actuelle.

### Fill Her Up Baka

La documentation d'Outdoor Event Pack indique qu'une déflation mal synchronisée peut produire des problèmes visuels pendant les animations.

Aucun problème bloquant n'a été observé jusqu'ici, mais ce point reste à surveiller pendant une partie réelle.

## Patchs de compatibilité Rhiven

Ces téléchargements sont conçus spécifiquement pour la **pile de compatibilité NEFARAM-Rhiven** documentée. Ne les installez pas aveuglément dans des configurations sans rapport ; confirmez d'abord que vous utilisez les mêmes mods et rencontrez les mêmes conflits.

### Mesh des chaînes de chevilles ZaZ de NEFARAM

[Télécharger le patch NEFARAM ZaZ Ankle Chains](../PAMA%20-%20NEFARAM%20ZaZ%20Ankle%20Chains%20Patch%20-%20Rhiven.zip)

Bad Ends Windhelm inclut une ancienne copie de `meshes\ZaZ-UltimateDataPack\ZaZ - HDT\ZaZAnkleChainsRagdolls_1.nif`. Le bloc PAMA étant placé tard, ce fichier pourrait écraser le mesh patché de NEFARAM. Installez et activez cette archive après Bad Ends Windhelm, ou assez tard dans le panneau gauche de MO2 pour gagner ce conflit de fichiers. Il s'agit d'un override de mesh, non d'un patch ESP.

### Navmesh de Windhelm

[Télécharger le patch Windhelm Navmesh](../PAMA%20-%20Windhelm%20Navmesh%20Patch%20-%20Rhiven.zip)

Bad Ends Windhelm réintroduit d'anciennes données de navmesh, pratiquement similaires à celles de la version vanilla. Cet ESP marqué ESL préserve les gagnants finaux prévus :

- `000FC117` / `WindhelmBridge04` depuis `WindhelmSSE - Exterior NavMesh Fixes.esp`
- `0004B66C` / `WindhelmCandlehearthHallExterior` depuis `CapitalWindhelmExpansion - SkyrimSewers.esp`

Chargez-le après Bad Ends Windhelm et les plugins sources/correctifs pertinents qu'il réconcilie. Validation xEdit : **0 erreur / 7 records**.

### Location de Solitude

[Télécharger le patch Solitude Location](../PAMA%20-%20Solitude%20Location%20Patch%20-%20Rhiven.zip)

Ce patch minimal marqué ESL restaure `XLCN - Location = SolitudeLocation [00018A5A]` sur `SolitudeOrigin [00037EE9]` tout en préservant les données de cellule gagnantes de PAMA. Chargez-le après Bad Ends Solitude afin que l'affectation restaurée gagne. Aucune fusion de navmesh n'a été conservée, car le pathfinding observé à Solitude fonctionnait correctement. Validation xEdit : **0 erreur / 17 records**.

### Terrain de Falkreath

[Télécharger le correctif LAND de Falkreath](../PAMA%20-%20Falkreath%20LAND%20-%20Rhiven%20Fix.zip)

Ce patch ESPFE/ESL corrige le trou dans le terrain à l'entrée de Falkreath, dans la cellule Tamriel `-9,-22`, LAND `0000AC81` (CELL `00009C81`). Le problème venait de `PaOutdoorEventPack.esp`, qui écrasait la chaîne de compatibilité ultérieure ; il n'était causé ni par Animal Mansion Reborn ni par le cœur de PAMA.

Le patch copie l'override LAND correct de `Northern Roads - COTN Falkreath - LFFGM patch.esp` et doit se charger après `PaOutdoorEventPack.esp`. La validation en jeu a confirmé la disparition du trou. Aucune régénération de Synthesis ou des LOD n'est nécessaire pour cette correction précise.

## Audit de Windhelm

Bad Ends Windhelm a été installé et audité par rapport à la pile Windhelm actuelle de NEFARAM-Rhiven.

### Conflits de navmesh détectés

Deux navmeshes PAMA se sont révélés plus anciens / pratiquement similaires à la version vanilla par rapport à la configuration gagnante actuelle de NEFARAM :

- `000FC117` — WindhelmBridge04
- `0004B66C` — WindhelmCandlehearthHallExterior

Gagnants prévus :

- `WindhelmSSE - Exterior NavMesh Fixes.esp` pour `000FC117`
- `CapitalWindhelmExpansion - SkyrimSewers.esp` pour `0004B66C`

Un patch dédié marqué ESL a été créé :

`PAMA - Windhelm Navmesh Patch - Rhiven.esp`

Bad Ends Windhelm a été ajouté comme master explicite.

Check for Errors dans xEdit :

- **0 erreur**
- **7 records**

### Conflit du mesh des chaînes de chevilles ZaZ

Bad Ends Windhelm fournissait également une ancienne copie de :

`meshes\ZaZ-UltimateDataPack\ZaZ - HDT\ZaZAnkleChainsRagdolls_1.nif`

La version actuellement patchée par NEFARAM est volontairement restaurée après PAMA avec :

`PAMA - NEFARAM ZaZ Ankle Chains Patch - Rhiven`

## Audit de Riften

Bad Ends Riften 1.3.2 a été installé et contrôlé par rapport à la configuration actuelle, notamment Riften of Reverie.

Résultats :

- total Pandora : **39 252** animations (**+30**)
- aucun conflit de fichiers MO2 notable
- le principal navmesh PAMA concerné est `000429CE` dans `RiftenCityNorth`
- Riften of Reverie ne remplace pas ce navmesh
- l'extension du navmesh de PAMA correspond à son échafaud / agencement d'exécution
- **aucun patch de compatibilité de navmesh n'est requis**

### Problème visuel mineur

Un puits vanilla traverse la plateforme de l'échafaud PAMA.

Décision actuelle :

- ne pas créer de patch pour un seul objet ;
- pendant la partie définitive, identifier formellement la référence du puits dans la console et utiliser `disable`.

Il s'agit d'un petit nettoyage visuel, non d'une incompatibilité structurelle.

## Audit de Solitude

Bad Ends Solitude 1.8.0 Revision 2 a été installé et audité dans `SolitudeWorld`.

Résultats :

- total Pandora : **39 298** animations (**+46**)
- la zone d'exécution vanilla est réutilisée proprement
- PAMA et `Animal_Research.esp` modifient tous deux le navmesh `000CAD79`
- leurs zones de gameplay réelles sont spatialement distinctes
- Saffron a été observée en jeu quittant l'auberge, marchant dehors, utilisant son marqueur d'appui contre le mur puis revenant normalement
- décision : **ne pas fusionner les navmeshes**

Une fusion ajouterait un risque inutile puisqu'aucun problème fonctionnel de pathfinding n'est actuellement observé.

### Correction de la Location de Solitude

Le record de cellule gagnant `SolitudeOrigin [00037EE9]` de PAMA supprimait :

`XLCN - Location = SolitudeLocation [00018A5A]`

Un patch minimal marqué ESL a été créé :

`PAMA - Solitude Location Patch - Rhiven.esp`

Son seul objectif est de restaurer l'affectation de location manquante tout en préservant les données de cellule gagnantes de PAMA.

Check for Errors dans xEdit :

- **0 erreur**
- **17 records**

## Orkish Bounty Hunters 0.4

OBH a été testé directement avec les commandes de débogage de son MCM.

### Parcours validés

- démarrage manuel d'une embuscade : **OK**
- apparition immédiate des chasseurs : **OK**
- combat : **OK**
- accumulation scriptée du poison : **OK**
- perte de connaissance / KO : **OK**
- issue en prison : **OK**
- issue au camp : **OK**
- évasion du camp : **OK**
- recapture : **OK**
- conséquences graves / exécution après recapture : **observées et fonctionnelles**

Le point de compatibilité important est que le poison d'OBH a provoqué la défaite sans réduire la santé du joueur à zéro ; le parcours normal Acheron / Practical Defeat n'a donc pas pris le contrôle.

### CTD isolé

Un CTD est survenu pendant une séquence de recapture après une évasion.

Le journal de crash indiquait une opération `TESObjectREFR` / Papyrus `EnableFunctor` sur une référence invalide.

Cependant :

- la même séquence a été répétée plusieurs fois ;
- le CTD ne s'est **pas** reproduit ;
- la recapture a ensuite fonctionné ;
- les conséquences d'exécution se sont également déclenchées correctement.

Classement actuel :

**CTD isolé non reproductible — à surveiller pendant la partie réelle d'Eleanor, mais ne pas patcher préventivement.**

## Points de contrôle Pandora

Totaux d'animations observés pendant l'installation :

- Deadly Furniture : **39 142**
- Prison Alternative : **39 184** (+42)
- Sovngarde Aftermath : **39 184** (+0)
- Punishment Pack : **39 200** (+16)
- Outdoor Event Pack : **39 200** (+0)
- Bad Ends Windhelm : **39 222** (+22)
- Bad Ends Riften : **39 252** (+30)
- Bad Ends Solitude : **39 298** (+46)

Toutes les générations Pandora répertoriées se sont terminées sans erreur bloquante signalée.

## Résumé de la validation du cœur

### Deadly Furniture

- MCM / prérequis détectés : **OK**
- `coc pamaTestZone` : **OK**
- fonctionnement des meubles non létaux : **OK**
- test contrôlé de guillotine létale : **OK**
- aucun CTD pendant l'exécution testée

### Prison Alternative

- MCM : **OK**
- Event Registry : **OK**
- arrestation vanilla → prison de Whiterun : **OK**
- sommeil en prison / progression de la peine : **OK**
- le lit de camp vanilla de Whiterun fonctionne :
  - EditorID `CivilWarCot01L`
  - Base FormID `000E2826`
  - RefID `0009DC89`

Le lit de prison de Falkreath a également été contrôlé et semble être le lit vanilla :

- EditorID `Bedroll01`
- Base FormID `00036ED3`
- RefID `000EF426`

Cela justifie une **validation prison par prison** plutôt que le remplacement aveugle des lits de prison vanilla.

### Sovngarde Aftermath

- MCM : **OK**
- exécution PAMA létale → transfert vers Sovngarde : **OK**
- aucun CTD pendant la décapitation / transition testée
- retour complet vers Tamriel volontairement reporté afin de ne pas dévoiler le scénario

À valider ultérieurement :

- achèvement du scénario de Sovngarde
- retour vers Tamriel
- restauration correcte de la tête avec `iCanBeResurrected = 2`

## Modules PAMA facultatifs examinés mais absents du bloc principal

### Pama's Permanent Crucifixes 2.0

Contenu autonome facultatif à forte persistance. Non requis pour l'architecture de Prison Alternative.

### Pama's Interactive Beatup Module 2.9

Système facultatif de punition / flagellation. Intéressant, mais non requis pour la pile de prison actuelle.

### Pama's Interactive Gallows 3.0

Système autonome de potence facultatif. Chevauchement fonctionnel avec Deadly Furniture pour l'usage actuel.

### Furniture Alignment Correction for NPCs 4.0.0

Ressource technique sans ESP. Conservée comme éventuel outil de dépannage si un problème précis d'alignement sur un meuble apparaît.

## Conclusion actuelle

Le **cœur PAMA complet prévu est installé et accepté pour intégration** dans NEFARAM-Rhiven.

Les principaux éléments restants sont volontairement reportés plutôt que bloquants :

- achèvement complet Sovngarde → Tamriel / restauration de la tête ;
- observation à long terme pendant la partie réelle d'Eleanor ;
- interaction avec DD uniquement si des entraves actives sont réellement concernées ;
- examen du CTD de recapture OBH uniquement s'il devient reproductible.

La philosophie actuelle reste prudente :

**ne reconstruisez pas inutilement les systèmes NEFARAM qui fonctionnent et ne créez pas de patchs spéculatifs pour des problèmes impossibles à reproduire.**
