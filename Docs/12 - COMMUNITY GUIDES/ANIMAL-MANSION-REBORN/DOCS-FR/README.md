# Animal Mansion Reborn 1.8 — Guide communautaire NEFARAM 17.3.8

> ⚠️ **IMPORTANT — MODIFICATION AVANCÉE DU MODPACK**
>
> Cette intégration n'est **pas une simple installation prête à l'emploi**.
>
> Un **patch de compatibilité Rhiven dédié est fourni avec ce guide**, mais l'intégration d'Animal Mansion Reborn dans NEFARAM exige malgré tout d'importantes modifications du modpack et une bonne compréhension du modding de Skyrim.
>
> L'installation implique la gestion de l'ordre de chargement, des patchs de compatibilité, la régénération de Synthesis, une validation dans xEdit et un workflow complet de régénération des LOD avec xLODGen, TexGen et DynDOLOD.
>
> Ce guide s'adresse donc aux utilisateurs ayant déjà **une certaine expérience de la modification de grandes listes de mods Skyrim** et à l'aise avec le diagnostic des conflits et des sorties générées.
>
> Travaillez toujours à partir d'une sauvegarde ou d'une instance NEFARAM clonée avant de commencer l'intégration.
>
> Si vous n'êtes pas à l'aise avec xEdit et la régénération des LOD, il est fortement recommandé de conserver la configuration NEFARAM d'origine.

> **Base de référence :** NEFARAM 17.3.8 officiel
> **Statut actuel :** **INTÉGRATION TECHNIQUE EFFECTUÉE — WORKFLOW LOD TERMINÉ — VALIDATION DU GAMEPLAY REPORTÉE À UNE PARTIE NORMALE/DÉFINITIVE**
>
> Cette intégration communautaire a passé ses contrôles techniques, achevé le workflow LOD complet et réussi l'inspection visuelle des sorties générées. La validation plus large des quêtes, de la navigation, des scènes et des sauvegardes est volontairement reportée à une partie normale/définitive.

## Installation rapide / TL;DR

1. Partez d'une base **NEFARAM 17.3.8 officielle** non modifiée.
2. Installez **Animal Mansion Reborn 1.8** et ses prérequis documentés.
3. Activez `Animal Mansion Reborn.esp`.
4. Gardez `COTN -Falkreath AMR.esp` activé.
5. Gardez le fichier fourni `AMR The Great Town of Shor's Stone Patch.esp` **activé** aux côtés de `COTN -Falkreath AMR.esp`.
6. Activez `Animal Mansion Reborn - Rhiven Patch.esp` après le patch de Shor's Stone et les autres plugins dont il résout les conflits avec AMR. Il complète les patchs de compatibilité fournis ; il ne les remplace pas.
7. Placez Animal Mansion assez tôt pour que les gagnants NEFARAM, Lux et les patchs générés déjà établis conservent leurs valeurs finales prévues. N'utilisez pas de séparateurs MO2 personnels ni les positions absolues des plugins d'un autre utilisateur.
8. Relancez **Synthesis** après le placement définitif des plugins.
9. Pour cette intégration, reconstruisez les LOD générés dans cet ordre : **xLODGen -> TexGen -> DynDOLOD**.
10. Confirmez que les sorties générées sont activées, puis démarrez Animal Mansion comme indiqué ci-dessous.

Le workflow LOD et l'inspection visuelle des sorties générées sont terminés. La validation plus large du gameplay se poursuivra pendant une partie normale/définitive.

## Exigences et prérequis

- **NEFARAM 17.3.8 officiel** comme base de référence.
- **Animal Mansion Reborn 1.8**.
- Tous les prérequis documentés par Animal Mansion Reborn 1.8. Ce guide n'ajoute ni ne devine une liste de dépendances distincte.
- Le patch de compatibilité fourni `COTN -Falkreath AMR.esp`.
- Le patch de compatibilité fourni `AMR The Great Town of Shor's Stone Patch.esp`.
- `Animal Mansion Reborn - Rhiven Patch.esp`.
- MO2 et les outils NEFARAM existants utilisés pour régénérer les sorties Synthesis et LOD.
- Une partie normale/définitive pour la validation plus large du gameplay.

Avant de modifier le profil, sauvegardez l'ordre du panneau gauche de MO2 et l'ordre des plugins. Conservez les sorties générées existantes jusqu'à ce que le placement final des plugins soit fixé.

## Installation et ordre relatif

Les noms exacts des séparateurs et les positions absolues varient selon les installations. Utilisez les relations suivantes plutôt que la capture d'écran personnelle de l'ordre de chargement d'un autre utilisateur :

1. Installez et activez **Animal Mansion Reborn 1.8**.
2. Placez `Animal Mansion Reborn.esp` avant les couches tardives de NEFARAM relatives à l'environnement, aux villes, à l'éclairage et aux patchs générés lorsque ces plugins ultérieurs contiennent déjà l'état final correct.
3. Chargez `COTN -Falkreath AMR.esp` après ses masters requis et gardez-le actif. Il repositionne les marqueurs et déclencheurs de quête propres à AMR pour la géométrie COTN de Falkreath.
4. Chargez `AMR The Great Town of Shor's Stone Patch.esp` après ses masters requis et gardez-le actif.
5. Chargez `Animal Mansion Reborn - Rhiven Patch.esp` après le patch actif de Shor's Stone et après les autres records qu'il doit fusionner ou corriger.
6. Préservez les gagnants Lux / NEFARAM établis plus tard lorsqu'ils fournissent déjà l'état environnemental final correct.
7. Ne régénérez Synthesis qu'une fois l'ensemble de plugins AMR et le placement des patchs de compatibilité finalisés.
8. N'exécutez les outils LOD qu'une fois Synthesis et le patch de compatibilité manuel dans leur état final prévu.

Le principe recherché est simple : utilisez le placement dans l'ordre de chargement pour les conflits déjà correctement résolus, et le patch Rhiven uniquement pour les records qui nécessitent une fusion explicite. Ne transférez pas massivement des groupes entiers de conflits dans un autre patch.

## Patch de compatibilité Rhiven — Ce qu'il corrige

`Animal Mansion Reborn - Rhiven Patch.esp` est une couche de compatibilité minimale. Son résultat **Check for Errors** dans xEdit est :

> **21 records traités / 0 erreur**

Le patch :

- préserve les chemins actuels des modèles bipèdes mâle et femelle du Husky de MNC ;
- complète le patch de compatibilité actif de Shor's Stone dans la pile finale auditée ;
- restaure les ajouts INFO manquants des dialogues AMR tout en conservant la structure finale des dialogues fournie par les gagnants ultérieurs ;
- ne comprend que les ajustements CELL localisés requis par les conflits audités ;
- évite tout transfert large ou aveugle de CELL entières ou de groupes de conflits.

Le patch Rhiven ne remplace ni le patch COTN Falkreath ni le patch fourni de Shor's Stone, et il ne remplace pas la génération Synthesis ou LOD. Il a été construit et validé dans xEdit avec le patch de Shor's Stone actif.

## Addon BodySlide AMR facultatif

Si vous installez l'addon facultatif **AMR BodySlide** :

1. Conservez le preset **Zeroed Sliders** de NEFARAM.
2. Activez **Build Morphs**.
3. Filtrez la liste des tenues avec **AMR**.
4. Exécutez **Batch Build** pour les entrées AMR filtrées.
5. Dans l'idéal, dirigez les fichiers générés vers un mod de sortie MO2 dédié afin qu'ils restent isolés et faciles à gérer.

Une reconstruction BodySlide seule ne modifie que les meshes. Elle ne nécessite **pas** de relancer Synthesis, xLODGen, TexGen ou DynDOLOD.

## Notes de compatibilité

### COTN Falkreath

`COTN -Falkreath AMR.esp` est requis pour cette intégration et doit rester actif. Il a passé Check for Errors dans xEdit avec **0 erreur** et contient un placement fonctionnel des marqueurs et déclencheurs AMR pour l'agencement COTN. Sa validation plus large en jeu est reportée à la partie normale/définitive.

### The Great Town of Shor's Stone

Gardez `AMR The Great Town of Shor's Stone Patch.esp` actif. Le patch Rhiven a été construit et validé dans xEdit avec celui-ci actif ; il s'agit d'une couche complémentaire, non d'une reconstruction ou d'un remplacement du patch fourni.

Les préoccupations relevées précédemment lors de l'audit concernant les records NAVI / navmesh et les liaisons de portes restent des précautions techniques utiles, car ces records sont sensibles à la géométrie finale de la localité. Ils ont été audités dans la pile finale active ; la validation plus large du pathfinding des PNJ et followers, ainsi que des portes et transitions, est reportée à la partie normale/définitive.

### MNC et modèles de Husky

L'override `HuskyBareAA [02018B35]` d'AMR restaure le mesh vanilla du Husky mâle et supprime l'affectation femelle de MNC. Le patch Rhiven préserve les chemins des modèles bipèdes mâle et femelle de MNC sans effectuer de fusion MNC plus large.

### Dialogues

Des gagnants de dialogues plus tardifs peuvent omettre les entrées INFO ajoutées par AMR. Le patch Rhiven fusionne uniquement les ajouts AMR manquants dans la structure finale des dialogues. Les différences de texte dues à des chaînes anglaises qui remplacent une autre langue sont des problèmes de traduction, et non des corrections de compatibilité couvertes par ce patch.

### Gagnants Lux, NEFARAM et Synthesis

Les records Lux, NEFARAM et Synthesis plus tardifs doivent continuer à gagner lorsqu'ils contiennent déjà l'état environnemental final prévu. Les exemples typiques comprennent l'éclairage des CELL, l'espace image, le brouillard, les données ambiantes et d'autres transferts environnementaux. Ne dupliquez pas ces gagnants corrects dans le patch Rhiven.

## Sorties générées

L'ordre requis est :

1. finaliser le placement d'AMR et des patchs de compatibilité ;
2. relancer **Synthesis** ;
3. exécuter **xLODGen** ;
4. exécuter **TexGen** ;
5. exécuter **DynDOLOD** ;
6. inspecter en jeu les LOD de terrain et d'objets générés.

La chaîne complète est requise pour cette intégration, car AMR contient du contenu extérieur de worldspace et au moins un record `LAND` visible sous :

`WhiterunWorld -> WhiterunWindDistrict02`

État documenté actuel :

- Synthesis : terminé ;
- xLODGen : terminé ;
- TexGen : terminé ;
- DynDOLOD : terminé ;
- inspection visuelle des sorties générées : terminée.

La chaîne complète des sorties générées et son inspection visuelle sont achevées.

## Démarrer Animal Mansion

1. Entrez dans **Dead Man's Drink** à Falkreath.
2. Écoutez la conversation d'introduction.
3. Parlez à **Valga Vinicia**.

## Dépannage

### Le pathfinding d'un PNJ ou follower à Shor's Stone est défectueux

- Confirmez que `AMR The Great Town of Shor's Stone Patch.esp` est actif et que le patch Rhiven se charge après lui.
- Confirmez que le patch Rhiven est activé et se charge après les records qu'il corrige.
- Testez le pathfinding des PNJ, les followers, portes et transitions sur une sauvegarde jetable.
- Arrêtez la validation si le problème est reproductible ; ne transférez pas mécaniquement des records NAVI / NAVM dans un autre patch en guise de correction rapide.

### Une porte ou une transition est défectueuse

- Vérifiez les deux côtés de la transition et le marqueur de téléportation associé.
- Vérifiez que les bons plugins de localité et de compatibilité sont actifs.
- Traitez les liaisons de portes de Shor's Stone comme sensibles au navmesh, et non comme de simples records de placement.

### Un Husky utilise le mauvais mesh

- Confirmez que `Animal Mansion Reborn - Rhiven Patch.esp` gagne le conflit `HuskyBareAA [02018B35]`.
- Vérifiez qu'aucun plugin ultérieur ne restaure l'ancienne affectation de modèle d'AMR ou ne supprime le chemin femelle de MNC.

### Un dialogue AMR attendu manque

- Confirmez que le patch Rhiven se charge après les records de dialogue qu'il fusionne.
- Vérifiez si un autre plugin ultérieur supprime les entrées INFO d'AMR du gagnant DIAL final.
- Traitez les modifications de chaînes liées uniquement à la langue séparément du comportement de compatibilité.

### Des objets manquent à proximité ou à distance

- Confirmez que Synthesis a été reconstruit après le placement final des plugins.
- Confirmez que la chaîne complète `xLODGen -> TexGen -> DynDOLOD` s'est terminée dans cet ordre.
- Inspectez les sorties générées finales avant de considérer le problème comme venant du plugin AMR.

### Une cellule modifiée provoque des crashs répétés

- Reproduisez le problème sur une sauvegarde jetable.
- Vérifiez s'il survient à l'entrée, à la sortie ou uniquement après une activité de quête.
- Considérez un CTD persistant dans une cellule modifiée par AMR comme une condition d'arrêt. L'intégration n'est pas validée pour le gameplay tant qu'il reste reproductible.

## Notes techniques avancées

Le patch public est volontairement réduit. L'audit a montré que de nombreux conflits AMR apparents étaient déjà correctement résolus par des gagnants Lux, NEFARAM ou Synthesis ultérieurs ; ces records n'ont donc pas été copiés dans le patch de compatibilité.

Points de référence utiles :

- `HuskyBareAA [02018B35]` : préserve les chemins modernes des modèles bipèdes mâle et femelle de MNC.
- `DGCrimeForcegreetTopic [000267DE]` : le gagnant DIAL final doit recevoir les ajouts INFO manquants d'AMR.
- `DGCrimeWantedTopic [0002A37F]` : le gagnant DIAL final doit recevoir les ajouts INFO manquants d'AMR.
- `OfferServicesTopic [00076FBB]` : le gagnant DIAL final doit recevoir les ajouts INFO manquants d'AMR.
- Porte extérieure de Shor's Stone `REFR [000177DE]` : expose un `XNDP - Navmesh Door Link` et est sensible au navmesh ; elle ne doit pas être transférée mécaniquement.
- `WhiterunWorld -> WhiterunWindDistrict02` : contient au moins un record `LAND` visible d'AMR, raison pour laquelle cette intégration utilise la chaîne LOD complète.

Le fichier de base `Animal Mansion Reborn.esp` a également passé Check for Errors dans xEdit avec **30 175 records traités / 0 erreur**. Ce résultat et les **21 records traités / 0 erreur** du patch Rhiven établissent uniquement une validation technique ; ils ne prouvent pas le comportement des quêtes, de la navigation, des scènes ou des sauvegardes en jeu.

## Statut et notes de publication

**INTÉGRATION TECHNIQUE EFFECTUÉE — WORKFLOW LOD TERMINÉ — VALIDATION DU GAMEPLAY REPORTÉE À UNE PARTIE NORMALE/DÉFINITIVE**

Terminé :

- audit complet des conflits ;
- Check for Errors dans xEdit du fichier AMR de base ;
- validation xEdit du patch COTN Falkreath ;
- création et validation xEdit du patch de compatibilité Rhiven minimal ;
- régénération de Synthesis ;
- génération xLODGen ;
- génération TexGen ;
- génération DynDOLOD ;
- inspection visuelle des sorties générées.

Reporté :

- validation plus large du gameplay pendant une partie normale/définitive.

L'intégration est validée techniquement et complète du point de vue des LOD. La validation du gameplay reste volontairement reportée et ne doit pas être présentée comme terminée avant d'avoir été établie en jeu normal.
