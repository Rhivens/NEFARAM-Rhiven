# NEFARAM — Guide de modding et d’ordre de chargement

> Version Markdown du guide Word original : [NEFARAM_Modding_Guide_1.4_FR.docx](./NEFARAM_Modding_Guide_1.4_FR.docx)  
> **Édition Shatanoid & Skinny PeTe • v1.4 (WIP) — fonctionnelle • mise à jour le 17/07/2026**
>
> Cette version Markdown est destinée à la consultation technique rapide. Les captures FOMOD et captures de réglages xLODGen / TexGen / DynDOLOD restent dans le DOCX original.

## À faire

- Encore plus de mods !
- Rape Tats Configurator — terminé !
- Patches Aroused et armures — WIP par Skinny — terminé, ils se trouvent plus bas.
- Distribution des armures — travail en cours au 17/09.

# 1. Configuration de base

> **Attention :** ne poursuivez pas ce guide si vous ne savez pas lancer xLODGen, TexGen et DynDOLOD.

## Graphismes (ENB)

Depuis la mise à jour actuelle de Pi-Cho (9.7), quelque chose ne va vraiment pas ; Shatan a donc abandonné Pi-Cho au profit de Silent Horizons 2.

**Ce changement n’est pas indispensable :** le Pi-Cho de NEFARAM est déjà très correct.

### KreatE

Possibilité d’utiliser un fichier déjà préparé.

### Silent Horizons 2

Alternative recommandée par l’auteur du guide au moment de sa rédaction.

## Realore et remarques générales

1. Télécharger Realore.
2. L’installer et l’activer.
3. Le placer au-dessus de BNP Frostnip Skin.
4. Garder les deux actifs.

Motif indiqué dans le guide : les visages rendent mieux lorsque Realore est écrasé par BNP.

Le guide rappelle qu’un PC solide est recommandé et que xLODGen, TexGen et DynDOLOD sont indispensables pour reproduire le rendu proposé.

## Pandora

Lancer Pandora et cocher tout ce qui est nouveau.

Relancer Pandora après toute installation ou mise à jour d’animations SexLab.

Le guide indique qu’une installation complète peut atteindre environ **51 000 animations**.

Prévoir du temps pour xLODGen, TexGen et DynDOLOD : environ une heure sur la plupart des PC d’après les auteurs, jusqu’à 6 à 8 heures sur une machine moins puissante.

## Résumé historique xLODGen / TexGen / DynDOLOD

> Cette partie du guide original est explicitement marquée comme ancienne / incomplète. Utiliser de préférence la procédure complète de la section 3 plus bas.

1. Dans MO2, panneau gauche :
   - décocher `TexGen Output` et `DynDOLOD Output` ;
   - cocher `xLODGen Resource` et `SSE Tamriel`.
2. Lancer xLODGen avec les réglages détaillés plus loin.
3. Après xLODGen :
   - désactiver `xLODGen Resource - SSE Terrain Tamriel` ;
   - lancer TexGen ;
   - lancer DynDOLOD.
4. Avant de relancer DynDOLOD :
   - activer `TexGen Output` et `DynDOLOD Output` ;
   - supprimer `Occlusion.esp` et `DynDOLOD.esp` présents dans l’ancien `DynDOLOD Output`.
5. Une fois terminé :
   - laisser `xLODGen Resource SSE Tamriel` désactivé ;
   - activer les sorties xLODGen, TexGen et DynDOLOD.

## RapeTats Configurator

Télécharger le programme, le configurer selon sa description et le lancer depuis MO2.

Le guide indique ensuite de remplacer le fichier généré par celui fourni sur Discord.

---

# 2. Ordre de chargement

## Séparateur — Utilitaires

1. Perk Point Book ESL — version 1.3.
2. Where Are You
3. Dragons Come Back
4. Fade Tattoos Continued — requis pour Devious Curses
5. Rape Tattoos Continued — requis pour Devious Curses
6. RTats QOL EXtension
7. Clean Crafting
8. Collectibles Helper
9. Lazy Item Edit
10. SkyPatcher
11. Crackling Fire
12. Petite to Plenty - CBPC Configuration 9.0 — choisir la première option, normalement la v9
13. Chooey's Choice Requirements
14. SunHelm Auto Eat and Drink
15. Build With Gold
16. Invisible Helmets
17. Invisible Dragon Priest Masks
18. Magic Effects Remover
19. Removed Scabbards (Sheaths) 1H Sword Vanilla Skyrim
20. Faster Mining Animation (Very Fast)

## Musique

1. Nyghtfall - Dark Fantasy Music - With Vanilla Music
2. The Sounds of Towns and Cities

## Mods de poses optionnels

1. Halo Poser — choisir `00`, version normale 43.
2. GomaPeroPoses_SE
3. BakaFactory's Poses Pack

## Animations

1. Dynamic Random Non-Combat Female idle animations OAR
2. Swimming Animations
3. Thundertrot Horse Animations
4. Thundertrot Directional Move
5. 360 Ward
6. Conditional Female Aroused Animations OAR
7. Female Merchant Counter Animations

## Mods Mihail Monsters

1. Frogs - Mihail Monsters and Animals
2. Whale Bones on Coasts
3. House Cats
4. Flies Around Corpses
5. Sea Turtles
6. Ancient Atmoran Remains
7. mummified animals 1.1 (se-ae)
8. hawk replacer sse
9. Bone Colossi and Gravelords (SE-AE)
10. emperor penguins se
11. Bloody Mammoth Carcasses (se-ae)
12. chickens and chicks (se-ae)
13. more cow variants (se-ae)
14. seagulls (se-ae)
15. swans (se-ae)
16. barn owls (se-ae)
17. Frogs (se-ae)

## SexLab

1. SexLab Animations Slots — FOMOD : « 165+ AE 2000/3000/5000 », 2000 conseillé ; ESP ESL.
2. Demonic Creatures V2
3. Slal NibblesAnims 5.82
4. NCK30 SLAL SE
5. K4 Anims
6. GS SLAL
7. GS SLAL CREATURES
8. Billy Animations
9. BakaFactory
10. Anubs Animations
11. SC_HorseReplacer — les deux fichiers
12. Equestrian - An SC Horses Overhaul
13. SC Horses - Glowing Horse Fix
14. Let Horses be Horses-Equestrian SC Overhaul patch
15. Equestrian - An SC Horses Overhaul - Patch
16. SC Horse Replacer ABC Patch SSE
17. SC Horses Mane Fix
18. Labrador Replacer

Pour Billy Animations et les suivants : mettre à jour les animations déjà présentes dans NEFARAM ou placer les nouvelles versions plus bas dans l’ordre de chargement, lancer Pandora, puis en jeu ouvrir SL Anim Loader dans le MCM, activer et enregistrer les animations.

## Apparence des personnages

1. Aesthetic Facial Piercing
2. Starsight Eyes
3. Gothic Makeup for RaceMenu
4. Pocky's 4k human female makeup
5. Ancient Beauty Makeup - RM Overlays
6. Beauty Marks - Racemenu Overlays
7. Bitchcraft Tattoos - Racemenu 4k Overlays
8. Lovely Makeup - Racemenu Overlays
9. Lovely Makeup 2 - Racemenu Overlays
10. Misery's Infernal Inks - RaceMenu Overlays for 3BA
11. RX Overlays
12. Lyru's Tattoo pack collection 2
13. Tattoo Model Suicide Girl SE
14. Tattoo Model Suicide Girl SE ESL
15. Obi's Tattoos 3BA 4K
16. Goam Elven Ears - Redone
17. ED Horns SSE
18. Obi's Warpaints 2k
19. Feral Eyes
20. Feral Eyes - Lashes Nouveaux
21. Stalker Overlay 3BA - BodyPaint Tattoos
22. ED Horns - Proper RaceMenu Integration
23. Racemenu Handnails
24. MuDynamicNormalMap
25. Yyvengar Bodypaints - Female (CBBE 3.4)
26. Pubix Full
27. LM's Eyebrows 2k - Standalone 1.1
28. FRECKLES - Racemenu Overlay Collection ESL
29. Beauty Marks 2 - Racemenu Overlays
30. Fabulous Makeup 2 - Racemenu Overlays

## Remplacements de personnages

1. Aela - Chooey's Choice
2. Daegon Legacy - Chooey's Choice SkySights
3. Man of Skyrim Resources
4. Man of Skryim
5. True Sons of Skyrim Refined Resources
6. True Sons of Skyrim Refined
7. Project ja-Kha'jay — récupérer également le HOTFIX « optimized skeletons ».
8. SkyPatcher - Children of the Hist

Pour True Sons of Skyrim Refined et Man of Skyrim Refined, choisir globalement les options préférées. Pour la skin, installer SkySight Skins et la sélectionner pendant l’installation.

Pour les replacers Milf Factory, choisir les réglages souhaités.

## Ajouts graphiques (NSFW)

1. Kanjs - Mace of Molag Bal Animated
2. Kanjs - Spellbreaker Animated
3. Remiros' Dawnbreaker
4. Remiros' Ebony Blade
5. Porny Mods — choisir selon les préférences.
6. Real Wheat Fields - Option A
7. Blended Shorelines — supprime les bordures d’eau dentelées (ESL)
8. High Quality Ivy
9. High Quality Ivy For Stumps and Logs - HLT
10. High Quality Ivy for Fences Everywhere
11. Parallax With Shadows
12. Nature of the Wild Lands
13. Nature of the Wild Lands - Patch Collection
14. Nature of the Wild Lands 3.0 - 3D hybrid LOD
15. Nature of the Wild Lands - Regions Addon
16. Nature of the Wild Lands - Landscape textures
17. Shrubbery Symphony - Enhanced Greenery
18. Shrubbery Symphony - Enhanced Greenery - Seasons
19. Skyrim 202X - 2K
20. Parallax Meshes - Riften Ground - 2K
21. Parallax Meshes - Whiterun
22. Nix's Floating Islands Of Whiterun
23. The Great City of Rorikstead
24. Forgotten Vale HD by CleverCharff 4K
25. ICFurs Improved Reach Fern
26. Kanjs - Beef and Human Flesh Animated and Beating Motion
27. Kanjs - Forgotten Vale Cave Worm
28. Praedy's repository - SE
29. Praedy's Chantry of Auriel AIO - SE
30. Praedy's College of Winterhold - SE
31. Praedy's Fort Dawnguard - SE
32. Praedy's Castle Volkihar - SE
33. Praedy's Sky AIO - SE
34. Praedy Willow's elder scroll and elder council amulet
35. Clear Frozen Lakes and Ponds
36. DynDOLOD The Little Things
37. Standing Stones AIO with New Fixes
38. More Auriel Statues
39. New Night Mother SE
40. New Dragon Word Wall
41. Rally's Blackreach Mushrooms
42. Silver Objects SMIMed
43. Standing Stones AIO with New Fixes — Patches
44. All Maker Wind Stone
45. Arc's Gem Holder Redux
46. Arcs Bear Trap redux
47. WiZkiD Hunter's Camp Overhaul (2K)
48. TMD The Rift Leaves 2K
49. Waterplants for Skyrim
50. Missives 2.03 SSE
51. Missives 2.12RU_EN
52. SL Dirty Deeds Missives
53. Immersive Laundry 1.0d SSE
54. Laundry Improvements 1.0
55. Immersive Laundry - Animated

## Armures — patch

### COCO

Prendre les versions 3BA + patch Heels Sound s’il n’est pas déjà inclus.

1. COCO 2B Wedding Outfit
2. COCO Mulan
3. COCO Goddess Of War
4. COCO Goddess Of War V2
5. COCO Succubus
6. COCO Battle Angels
7. COCO RONIN
8. COCO Scarlet Rose
9. COCO Caress of Venus
10. COCO Demon Shade
11. COCO Fairy Queen
12. COCO Snow Queen
13. COCO Twilight Sorceress

### Mods Aokili

Télécharger le fichier principal en 2K ainsi que les versions 4K non-complex pour les armures ci-dessous.

Le guide estime que la 8K apporte peu en jeu normal et recommande de ne la tester qu’avec beaucoup de VRAM disponible.

14. Dracania Armor
15. Azure Knight Armor
16. Elven Sentry Armor
17. Royal Vanguard Armor
18. Star Guardian
19. Lavatera Armor

### Autres armures

1. Believable weapons
2. Champion of Azura
3. Dark Elf Blader
4. Demon Seducer Outfit
5. Dread Sovereign 3BA 4k
6. Vampire Temptress Armor
7. Shadow Knight
8. Ryan Reos High Priestess
9. Ryan Reos Battle Bunny Akali
10. SucubusSister

## Patches personnalisés

### SkinnyPete Armor Material Patch

Le guide indique qu’il faut installer toutes les armures concernées, sauf si l’on sait supprimer proprement les masters manquants.

### SkinnyRandomArmorPatches

Les armures ne sont pas toutes obligatoires, mais elles sont recommandées par les auteurs du guide.

## Artefacts et armes daedriques

1. Azura's Star Rework
2. Clavicus Vile Artifacts Rework
3. Dawnbreaker Rework
4. Ebony Blade Rework
5. Ebonymail Rework
6. Harkon's Sword Rework
7. Hircine Artifact Rework
8. Mace of Molag Bal Rework
9. Mehrunes Razor Rework
10. Oghma Infinium Rework
11. Ring of Namira Rework
12. Skeleton Key Rework
13. Skull of Corruption Rework
14. SpellBreaker Rework
15. Volendrung Rework
16. Wabbajack Rework

## Presets BodySlide

1. 3BA - Arcade Miss Fortune BodySlide 3BA
2. 3BA - Evelynn BodySlide 3BA
3. 3BA - KDA Kai'Sa BodySlide 3BA
4. 3BA - Qiyana BodySlide 3BA
5. 3BA - Sivir BodySlide 3BA
6. 3BA CBBE - Pool Party Miss Fortune BodySlide preset
7. Aelwyn - 3BA Bodyslide Preset
8. Aesthetic Diamond - 3BA Bodyslide Preset
9. Alina body preset - 3BA Bodyslide
10. Beauty Body Preset - 3BA Bodyslide
11. Chapter 1 - Cataclysm - CBBE 3BA Bodyslide Preset
12. Diamond Body 3BA - BodySlide Preset
13. Dibella's mommy 3BA Bodyslide
14. Domitia Body - BodySlide CBBE 3BA Preset
15. EVE's Stellar Ass 3BA Bodyslide preset (Stellar Blade)
16. Halloween Cosplay Girl 3BA Bodyslide Preset
17. My Exquisite Body - CBBE 3BA Bodyslide Preset
18. My Lovely Body - Fantasy Beauty - 3BA Bodyslide Preset
19. NTZ's APPLE PIE - 3BA Bodyslide Preset
20. Pomona Amphora Bodyslide Preset 3BA
21. Safiyya 3BA - Bodyslide Presets
22. Sevia Bodyslide Preset 3BA
23. Sexy Lass - CBBE 3BA bodyslide preset
24. Smaller Fantasy Body - 3BA Bodyslide Preset
25. Tea Body 3BA - BodySlide Preset
26. The Elegance Beauty - CBBE 3BA Bodyslide Preset
27. The Tinraa Body - Matriarch - CBBE 3BA Bodyslide preset
28. Umbrael's Umbrage - 3BA Bodyslide Preset
29. Untamed Beauty - 3BA Bodyslide Preset
30. Widowmaker's Ass Bodyslide 3BA

## MCO

1. Le guide indique un passage au MCO de Thoshy et renvoie vers son guide sur Discord.
2. Crouch Sliding
3. Crouch Sliding – Pandora Fix

## Tatouages

1. Alpia Slavetats Pack
2. Alpia Slavetats Pack Riekling
3. Alpia Slavetats Pack Orc
4. Chucktats tattoos
5. Horse Slut Tats
6. Marts Slavetats
7. Marts Tats Orc Slave
8. Meeko's Bitch Tats
9. Zaki Tattoos SE

## Guides FOMOD

Le DOCX original contient les captures de sélection FOMOD pour :

- Chooey's Choice Requirements
- The Sounds of Towns and Cities
- High Quality Ivy
- Nature of the Wild Lands
- Shrubbery Symphony
- Project ja-Kha'jay
- True Sons of Skyrim Refined / Man of Skyrim Refined

Les captures sont conservées dans le document Word, qui reste la référence visuelle.

---

# 3. xLODGen, TexGen et DynDOLOD — procédure complète

*Merci à Thoshy dans le guide source.*

## 3.1 Mettre à jour les outils et ressources nécessaires

Commencer par supprimer les dossiers xLODGen et DynDOLOD dans `nefaram\tools` si une mise à jour complète est nécessaire.

- **xLODGen** : récupérer la version actuelle depuis Step Modifications, puis la décompresser dans `nefaram\tools`.
- **DynDOLOD & TexGen** : récupérer DynDOLOD 3 Alpha depuis Nexus Mods et le décompresser dans `nefaram\tools`.
- **DynDOLOD DLL NG** : installer normalement dans MO2 et choisir « Remplacer » lorsque MO2 le demande.
- **DynDOLOD Resources SE 3** : installer normalement dans MO2 ; dans le FOMOD, cocher tout sauf **Holy Cow** et **Low Res Textures HD**.
- **Terrain Noise Texture SE** : installer et activer dans MO2.
- **DynDOLOD The Little Things** : installer normalement et placer son plugin **après Synthesis, mais avant DynDOLOD.esp et Occlusion.esp**.

> Ne mettre à jour que ce qui doit l’être / installer uniquement ce qui manque.

## 3.2 Nettoyer les anciennes sorties

Vider le contenu des dossiers suivants dans `NEFARAM\MODS` :

- `XLODGEN OUTPUT`
- `TEXGEN OUTPUT`
- `DYNDOLOD OUTPUT`

## 3.3 Régler DynDOLOD_SSE.ini

Dans :

```text
\Tools\DynDOLOD\Edit Scripts\DynDOLOD
```

ouvrir `DynDOLOD_SSE.ini` et définir :

```ini
Expert=1
Level32=1
```

## 3.4 Définir les dossiers de sortie

Définir les sorties **en dehors du dossier mods de MO2**.

Créer un dossier contenant trois sous-dossiers :

- `XLODGEN OUTPUT`
- `TEXGEN OUTPUT`
- `DYNDOLOD OUTPUT`

Pour xLODGen, modifier le chemin de sortie dans les arguments de l’exécutable MO2.

Pour TexGen et DynDOLOD, définir le chemin de sortie directement dans les programmes.

## 3.5 Lancer xLODGen

1. Activer `xLODGen Resource – SSE Terrain Tamriel`.
2. Vérifier que son plugin est également actif.
3. Lancer xLODGen.
4. Dans la fenêtre de gauche : clic droit → **Select All** pour activer tous les worldspaces.
5. Cocher **uniquement Terrain LOD**.
6. Décocher :
   - Object LOD
   - Trees
   - Occlusion
7. Appliquer les réglages LOD4 / LOD8 / LOD16 / LOD32 des captures du DOCX original.
8. Lancer la génération.

Le guide indique que cette étape peut prendre plusieurs heures.

## 3.6 Copier la sortie xLODGen

Copier ou déplacer la sortie créée vers `xLODGen Output` dans MO2.

## 3.7 Désactiver la ressource terrain

Désactiver `xLODGen Resource – SSE Terrain Tamriel`.

Le guide original indique explicitement qu’il manque encore à cette version une procédure validée pour le **grass cache**.

## 3.8 Lancer TexGen

Lancer TexGen avec les réglages illustrés dans le DOCX original.

Le guide contient deux captures de réglages, dont une variante présentée comme **« Réglages TexGen améliorés — utilisez ceux-ci pour le moment »**.

## 3.9 Copier la sortie TexGen

Copier ou déplacer la sortie TexGen vers `TexGen Output` dans MO2.

## 3.10 Lancer DynDOLOD

Lancer DynDOLOD.

Le guide mentionne un fichier de réglages fourni via Mega sur le Discord NEFARAM, à charger dans DynDOLOD puis à adapter au dossier de sortie.

## 3.11 Copier la sortie DynDOLOD

Copier ou déplacer la sortie vers `DynDOLOD Output` dans MO2.

## 3.12 Vérifier les plugins finaux

Dans l’onglet Plugins, vérifier que les éléments suivants sont activés :

- `DynDOLOD.esm`
- `DynDOLOD.esp`
- `Occlusion.esp`

Le guide les place tout en bas de l’ordre de chargement.

---

# 4. Après l’installation

## Keywords à ajouter

- `Survival_ArmorWarm/Cold`
- Keywords liés à Aroused

## Liste des modifications d’armures

| Armure / modification | Matériau de base | Mis à jour | Modification effectuée | Vendeur | Niveau |
|---|---|---|---|---|---:|
| J3 Fishnet Fashion 3BA | X | X | X | Birna | |
| NARAKA BLADEPOINT WINTER BELL 3BA SMP | X | X | X | Birna | |
| Dread Sovereign 3BA | Elfique | X | X | Oengul War-Anvil | |
| Obi's Derketo Priestess Outfit - 3BA | Elfique | X | X | Lucan Valerius | |
| Obi's Druchii Armor 3BA | Ébonite | X | X | Tonilia | |
| Ryan Reos Battle Bunny Akali | Daedrique | X | X | Eorlund Gray-Mane | |
| Ryan Reos High Priestess | Elfique | Tak | Dragonscale | Ulfberth War-Bear | 35 |
| Royal Vanguard Armor | Ébonite | X | X | Gunmar | |
| Elven Sentry Armor | Elfique | X | X | Lod | |
| Lavatera Armor | Nordique lourd ? | X | X | Rustleif | |
| Shattered Royal Armor | Daedrique | X | X | Hestla | |
| Star Guardian | Elfique | X | X | Gunmar | |
| Dracania Armor | Ébonite | X | X | Ghorza gra-Bagol | |
| SucubusSister 3BA | X | X | X | Hestla | |
| Wayward Knight Set | X | X | X | | |
| YoRHa 2B Attire | X | X | X | Lucan Valerius | |
| [COCO] 2B Wedding Outfit | Elfique | Tak | Verre | Filnjar | |
| [COCO] Battle Angels | Elfique | Tak | Acier | Adrianne Avenicci | |
| [COCO] Caress of Venus | Elfique | Tak | Dwemer | Ghorza gra-Bagol | |
| [COCO] Demon Shade | Elfique | Tak | Daedrique | Tonila | |
| [COCO] Fairy Queen | Elfique | X | X | Birna | |
| [COCO] Goddess Of War | Elfique | Tak | Acier | Beirand | |
| [COCO] Goddess of War V2 | Elfique | Tak | Dwemer | Oengul War-Anvil | |
| [COCO] Lace Lingerie Pack | Elfique | X | X | Birna | |
| [COCO] Mulan | Elfique | Tak | Elven Glided | Grelka | |
| [COCO] RONIN | Elfique | Tak | Daedrique | Balimund | |
| [COCO] Scarlet Rose | Elfique |  | Écailles | Adrianne Avenicci | |
| [COCO] Snow Queen | Elfique | X | X | Birna | |
| [COCO] Succubus | Elfique | Tak | Verre | Hestla | |
| [COCO] Twilight Sorceress | Elfique |  | Fourrure | Glover Mallory | |
| [Daymarr] Shadow Knight | Elfique | X | X | Balimund | |
| [Enovilum] Vampire Temptress Armor | Brak ? | X | X | Hestla | |
| Azure Knight Armor | Ébonite | X | X | Gunmar | |
| Believable weapons | X | X | X | any blacksmith? | |
| Champion of Azura | X | X | X | Gunmar | |
| Dark Elf Blader | X | X | X | Alvor | |
| Demon Seducer Outfit | X | X | X | Birna | |
| Dread Sovereign 3BA 4k | Elfique | Tak | Ébonite | Eorlund Gray-Mane | |
| ELLE - Attractive Underwear Collection | X | X | X | Birna | |
| ELLE - Dark Assassin | X | X | X | Alvor | |
| ELLE - October Seer | X | X | X | Hestla | |
| ELLE - Wicked Corruption | X | X | X | Hestla | |

### Légende du tableau source

- **Mis à jour (Tak/X - Oui/X)**
- **Modification effectuée / X = aucune modification nécessaire**
- **Ajouté à un vendeur : Oui/Non + vendeur**
- **A = ajouté, mais méthode pas encore définie**
- **Niveau d’apparition** si renseigné
