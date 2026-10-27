# Bathing in Skyrim - Renewed 2.7.11 — Guide communautaire NEFARAM 17.3.8

> **Avertissement — modification communautaire :** ce guide modifie l'installation officielle de NEFARAM. Sauvegardez votre profil ou travaillez à partir d'une instance NEFARAM clonée avant toute installation.

> **Base de référence :** NEFARAM 17.3.8 officiel
>
> **Statut de validation :** Bathing in Skyrim - Renewed (BiSR) 2.7.11 a été testé en jeu ; l'intégration principale et les animations de bain décrites ici sont fonctionnelles.

## Répartition des rôles

Conservez un responsable clairement défini pour chaque couche de gameplay ou d'affichage :

| Rôle | Composant |
|---|---|
| Sang dans l'environnement | **Enhanced Blood Textures** |
| Sang sur les acteurs | **Just Blood** |
| Hygiène | **Bathing in Skyrim - Renewed (BiSR)** |
| Survie et besoins | **SunHelm** |
| Camping | **Campfire** |
| Affichage uniquement | **Needs Widget AIO** |

Needs Widget AIO ne remplace ni SunHelm ni BiSR. Il ne fait qu'afficher leurs informations.

## Pile d'installation BiSR prise en charge

Installez et activez les éléments suivants :

1. **Bathing in Skyrim - Renewed 2.7.11**
2. **Bathing in Skyrim - BAIN (Multi-Language)**
3. **Zaki 8K-4K Textures for Bathing in Skyrim Renewed**
4. **Bathing in Skyrim - Renewed - Animal Fat and Linen**
5. **Bathing in Skyrim - Generic Soap Distribution**
6. **Bathing in Skyrim - Renewed - Seamless Soap 1.2**
7. **Bathing in Skyrim SE - SST MORE VISIBLE BUBBLES**
8. **Bathing in Skyrim - Wash Me 1.3**
9. **Malignis Animations - Bathing in Skyrim Renewed**, placé avec les mods d'animations

### Choix du FOMOD de BiSR 2.7.11

| Option | Sélection |
|---|---|
| Male textures | **Zaki's SOS** |
| Female textures | **Zaki's CBBE** |
| Base Object Swapper | **Yes** |
| Description Framework | **Yes** |
| SkyPatcher | **Yes** |
| Bathing Token | **No** |
| First Person Messages | **No** |
| Source Scripts | **Yes** |
| Mod Organizer support | **Yes** |

Ne sélectionnez pas les patchs pour :

- CACO ;
- Licenses - Player Oppression ;
- Barefoot Realism ;
- Barefoot Realism Tweaked.

### Paquet BAIN multilingue

Installez le paquet BAIN directement après le cœur de BiSR. Il ne contient **pas** le français : laissez donc la langue sur **None**. Il reste utile comme base prête à être localisée lors de futurs travaux de traduction.

### Choix des addons

- **Zaki textures :** saleté féminine **Level 4 (Recommended)** ; niveau de saleté masculine **None**.
- **Wash Me 1.3 :** **Any follower**, **NSFW**, **Big basin**.
- **Artisan Soaps :** non retenu. La combinaison visuelle choisie associe Seamless Soap et More Visible Bubbles.

## Ordre relatif dans MO2

Utilisez des relations d'ordre plutôt que de copier les numéros de priorité absolus d'une autre installation :

1. Fichiers NEFARAM existants liés aux bassines, à la survie, à SunHelm et à Campfire
2. Cœur de BiSR
3. Paquet BAIN multilingue de BiSR
4. Textures Zaki
5. Animal Fat and Linen
6. Generic Soap Distribution
7. Seamless Soap
8. More Visible Bubbles
9. Wash Me

Placez **Malignis** avec les mods d'animations, après les fichiers qu'il doit remplacer. Placez **Needs Widget AIO** avec les mods d'interface et de HUD.

## Malignis et Pandora

Après avoir installé Malignis avec les mods d'animations, relancez Pandora.

- Envoyez les fichiers générés vers un mod MO2 dédié **Pandora Output**.
- Faites pointer Pandora vers la racine de ce mod de sortie, et non vers un sous-dossier `meshes`.
- Ne générez jamais directement dans le dossier `Data` du jeu.

Lors de l'exécution réussie consignée, les listes suivantes ont été détectées :

- `FNIS_BiS_WashMe_List`
- `FNIS_Bathing_in_Skyrim_List`
- `FNIS_Bathing_in_Skyrim_Malignis_List`

Pandora s'est terminé correctement avec **38 349 animations générées**.

## Configuration MCM critique de BiSR

BiSR est **désactivé par défaut dans une nouvelle partie**. Une fois l'enregistrement des MCM terminé :

1. Ouvrez le MCM de BiSR et activez le mod.
2. Activez les animations personnalisées.
3. Attribuez à Malignis un **poids en pourcentage non nul** par rapport aux autres ensembles installés, par exemple Baka.
4. Testez plusieurs événements de bain afin de vérifier que les ensembles voulus sont bien joués.

L'enregistrement par Pandora ne suffit pas à activer BiSR ni à attribuer un poids de lecture à Malignis.

## Needs Widget AIO

Needs Widget AIO est une couche d'affichage facultative et recommandée. Le preset **Vel'Dun** fourni était présent, actif et validé en jeu.

Il reste uniquement une couche d'affichage :

- **SunHelm** continue de gérer la survie et les besoins ;
- **BiSR** continue de gérer l'hygiène ;
- **Needs Widget AIO** ne fait qu'afficher leurs informations.

## Éléments validés

Constats directs en jeu pour la configuration documentée :

- BiSR 2.7.11 s'est enregistré et a affiché ses options MCM.
- L'intégration principale de BiSR s'est lancée et a fonctionné en jeu.
- Les animations de bain ont fonctionné sans erreur d'animation observée.
- Pandora a détecté les listes BiSR, Wash Me et Malignis, puis a terminé la génération.
- Needs Widget AIO et le preset Vel'Dun fourni étaient actifs et fonctionnels comme couche d'affichage.

Ce guide ne prétend **pas** valider Simple Inn Bath avec Xtended Stay ; ces vérifications sont toujours en attente.

## Dépannage

### BiSR ne fonctionne pas

- Vérifiez que `Bathing in Skyrim.esp` est actif.
- Attendez la fin de l'enregistrement des MCM.
- Activez BiSR dans son MCM ; il est désactivé par défaut dans une nouvelle partie.
- Sauvegardez, quittez complètement le jeu, relancez-le et vérifiez que le réglage persiste avant de modifier d'autres systèmes.

### T-pose ou échec d'une animation de bain

- Vérifiez que les fichiers d'animations de BiSR, Wash Me et Malignis sont activés.
- Relancez Pandora vers le mod dédié Pandora Output.
- Vérifiez que les trois listes BiSR consignées sont détectées.
- Dans le MCM de BiSR, activez BiSR et les animations personnalisées, puis attribuez un poids non nul à Malignis.
- Inspectez `Overwrite` dans MO2 et la sortie Pandora avant de refaire un test.

### Widgets en double

- Examinez Needs Widget AIO, SunHelm et les autres éléments du HUD.
- Ne conservez qu'un seul widget visible pour chaque valeur.
- Modifiez une seule couche d'affichage à la fois, puis refaites un test sur une sauvegarde jetable.

### Chevauchement du sang sur les acteurs et dans l'environnement

- Laissez Enhanced Blood Textures gérer l'environnement et Just Blood gérer les acteurs.
- Vérifiez que le patch corporel EBT / Just Blood est activé après EBT.

### Conflits de savon ou de bulles

- Conservez la combinaison choisie Seamless Soap et More Visible Bubbles.
- N'ajoutez pas Artisan Soaps sans réauditer volontairement la couche visuelle.

## Résumé de la configuration finale

À partir de **NEFARAM 17.3.8** officiel, cette configuration ajoute une couche d'hygiène BiSR 2.7.11 validée tout en préservant la répartition existante des responsabilités : EBT pour le sang dans l'environnement, Just Blood pour le sang sur les acteurs, SunHelm pour les besoins, Campfire pour le camping et Needs Widget AIO uniquement pour l'affichage.
