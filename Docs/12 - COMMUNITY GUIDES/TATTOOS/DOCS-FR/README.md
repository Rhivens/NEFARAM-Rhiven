# Étendre l'écosystème de tatouages dans NEFARAM 17.3.x

> **Statut :** guide communautaire pour NEFARAM 17.3.x. La pile décrite ici a été installée et auditée statiquement dans NEFARAM-Rhiven 17.3.7, puis conservée dans la base 17.3.8. Certains tests d'exécution restent incomplets ; utilisez une sauvegarde jetable.
>
> **Périmètre :** ce guide ajoute la sélection automatique, l'estompage temporaire et deux grands catalogues de tatouages aux fondations déjà incluses dans NEFARAM d'origine. Il ne remplace pas SlaveTats et ne décrit pas une mise à niveau depuis d'anciennes versions de RTC/Fade.

## 1. Ce que NEFARAM d'origine fournit déjà

NEFARAM 17.3.x d'origine inclut déjà la base essentielle des tatouages. Dans l'instantané d'origine du panneau gauche de MO2, ces deux mods figurent sous `[35 - Sexlab Content]` :

- `SlaveTatsSE`
- `SlaveTatsNG`

La liste d'origine contient aussi SexLab et les composants plus larges utilisés par cette pile, notamment `powerofthree's Papyrus Extender` et `JContainers`. Conservez toujours les versions et fichiers gagnants fournis par votre installation NEFARAM fonctionnelle, sauf si les instructions actuelles d'un mod exigent explicitement autre chose.

Autrement dit, ce guide n'ajoute **pas** le moteur de rendu de base des tatouages. Il étend la fondation existante avec un moteur d'application automatique, la prise en charge de l'estompage, des packs de tatouages et des règles RTC modulaires.

## 2. Ce que ce guide ajoute

Les éléments suivants sont de véritables ajouts à NEFARAM 17.3.x d'origine :

1. `Fade Tattoos Continued` **2.1.0**
2. `Rape Tattoos Continued` **2.0.3**
3. `Rape Tats Continued 2.0.3 QoL Extension` **rev1**
4. `Alpia Slavetats Pack` — configuration All-in-One documentée ci-dessous
5. `Alpia Rtats Settings All in One`
6. `Zaki Tattoos General Pack SE` **1.1.1** — Full Pack, avec textures corps/pieds 4K et mains/visage 2K
7. `Zaki RTC Settings`
8. L'override communautaire facultatif `Rhiven RTC Settings`, distribué sous le nom `Rhiven RTC Settings.zip`

Le huitième élément est disponible publiquement dans le dossier parent de ce guide sous le nom [`Rhiven RTC Settings.zip`](../Rhiven%20RTC%20Settings.zip). Le mod/l'archive MO2 se nomme **Rhiven RTC Settings**, tandis que le preset réel qu'il contient se nomme `zzz-Rhiven-RTC.json`.

RTC et Fade Tattoos Continued remplacent leurs anciens équivalents. N'installez pas simultanément les anciennes versions et les versions Continued.

## 3. Vue d'ensemble de l'architecture

Chaîne fonctionnelle :

```text
Catalogues de tatouages Alpia et Zaki
             |
             v
SlaveTats / SlaveTatsNG -> Rape Tattoos Continued -> Fade Tattoos Continued
             ^                      ^
             |                      |
 définitions/textures          règles de sélection automatique
 de tatouages                  des fichiers JSON de presets RTC
```

- **SlaveTats / SlaveTatsNG** enregistre les tatouages et gère les overlays RaceMenu.
- **Les packs principaux Alpia et Zaki** fournissent les définitions de tatouages et fichiers de textures.
- **Rape Tattoos Continued (RTC)** décide quand appliquer un tatouage éligible et lequel, selon les réglages MCM et les fichiers de règles RTC.
- **Fade Tattoos Continued** suit les marques temporaires et les supprime au fil du temps selon sa configuration.
- **Alpia RTC Settings, Zaki RTC Settings et les presets utilisateur facultatifs** définissent la sélection automatique et le regroupement de RTC. Ils n'ajoutent aucune texture.

RTC peut utiliser des réglages distincts pour le joueur, les PNJ et les esclaves ZaZ. Si le joueur appartient à `zbfFactionSlave`, les réglages d'esclave ZaZ peuvent également s'appliquer à lui.

## 4. Deux types différents de JSON

Cette distinction est essentielle pour diagnostiquer un tatouage manquant ou mal regroupé.

| Type de JSON | Utilisé par | Objectif | Contenu typique |
| --- | --- | --- | --- |
| JSON de catalogue SlaveTats | SlaveTats | Définit les tatouages pouvant être enregistrés et affichés | Nom, zone, section, chemin de texture |
| JSON de réglages ou preset RTC | Rape Tattoos Continued | Contrôle l'éligibilité automatique et le regroupement logique | Clés de chemins de textures avec règle `Group` et données RTC associées |

Par exemple, le catalogue SlaveTats All-in-One d'Alpia et le fichier de réglages RTC d'Alpia servent deux systèmes différents. Installer le pack de tatouages ne fournit pas automatiquement les règles de regroupement RTC, et installer les règles RTC ne fournit pas les textures référencées.

Un tatouage peut donc être :

- présent dans SlaveTats mais absent d'un fichier de règles RTC dédié ;
- présent dans un preset RTC mais inutilisable parce que son entrée de catalogue ou sa texture manque ;
- disponible pour une application manuelle par SlaveTats tout en étant exclu de la sélection automatique de RTC.

Le choix All-in-One d'un installateur de pack est également sans rapport avec la fusion de plusieurs presets RTC par la QoL Extension.

## 5. Prérequis et fondations NEFARAM

La documentation RTC interne identifie les fondations pertinentes suivantes :

- SexLab ;
- SlaveTats et ses prérequis ;
- Fade Tattoos, dans sa version d'origine prise en charge ou Continued ;
- `powerofthree's Papyrus Extender` (l'auteur de RTC indique avoir testé à partir de la version 5.5.0) ;
- JContainers pour les données de configuration ;
- les overlays RaceMenu via l'écosystème SlaveTats existant.

ZaZ est facultatif pour RTC lui-même et devient pertinent lors de l'utilisation de la catégorie d'acteurs `zbfFactionSlave` de RTC.

NEFARAM d'origine contient déjà les principales fondations ci-dessus. Ce guide ne recommande pas de les remplacer préventivement. En cas de comportement inhabituel, inspectez les versions et fichiers gagnants avant de modifier la base.

## 6. Installation dans MO2 et ordre du panneau gauche

Utilisez la section `[Sexlab Content]` d'origine comme point de référence public. Ajoutez le bloc d'extension vers la fin de cette section, après le contenu existant. Le projet validé l'a placé après `Advanced Nudity Detection`.

Utilisez cet ordre de haut en bas dans le panneau gauche de MO2 :

```text
Fade Tattoos Continued
Rape Tattoos Continued
Rape Tats Continued 2.0.3 QoL Extension rev1
Alpia Slavetats Pack
Alpia Rtats Settings All in One
Zaki Tattoos General Pack SE
Zaki RTC Settings
Rhiven RTC Settings (facultatif)
```

La dernière entrée est une couche d'override finale volontaire. Installez l'archive publique `Rhiven RTC Settings.zip` comme mod MO2 séparé ; son fichier interne `zzz-Rhiven-RTC.json` porte délibérément ce nom afin d'être chargé tard après les presets Alpia et Zaki. Un override utilisateur personnalisé peut occuper le même emplacement logique si le preset Rhiven n'est pas utilisé.

Règle de conflit essentielle :

> **La QoL Extension doit gagner ses conflits de scripts face à RTC.**

Fichiers qui se chevauchent normalement :

```text
Scripts/rapeTattoos.pex
Scripts/rapeTattoos_mcm.pex
Scripts/rapeTattoos_utils.pex
```

Les fichiers sources `.psc` correspondants peuvent également entrer en conflit lorsque les sources sont incluses. Contrôlez les fichiers gagnants dans MO2 au lieu de vous fier uniquement à leur position visuelle.

## 7. Importance de la RTC QoL Extension

RTC de base stocke ou consomme une configuration principale. La QoL Extension rev1 ajoute un workflow modulaire capable de charger et de fusionner plusieurs fichiers JSON de presets. Chaque pack de tatouages — et un override personnel final — peut ainsi rester séparé, sans obliger l'utilisateur à modifier manuellement un grand `settings.json`.

Commandes MCM utiles de la QoL Extension :

| Commande | Utilisation recommandée |
| --- | --- |
| `Test / Reload configs` | Reconstruire le mapping fusionné sur une sauvegarde de test et inspecter la console ou les journaux |
| `Merge all into settings.json` | Éviter l'usage occasionnel ; écrit une configuration consolidée et supprime dans la pratique la séparation entre presets |
| `Enable detailed Papyrus logging` | Activer seulement temporairement pour diagnostiquer un problème, puis désactiver |

L'approche modulaire facilite les mises à jour et le dépannage : les presets des auteurs restent intacts et un petit delta final peut n'exprimer que les changements voulus.

## 8. Emplacements JSON, ordre de fusion et priorité

Le workflow QoL documenté dans les sources internes prend en charge des presets supplémentaires sous :

```text
Data/SKSE/Plugins/RapeTattoos/
```

L'emplacement historique des données utilisateur peut également intervenir :

```text
Documents/My Games/Skyrim Special Edition/JCUser/rTats/
  settings.json
  colorConfig.json
  presets/
```

Lorsqu'un `settings.json` principal existe sous `Data/SKSE/Plugins/RapeTattoos/`, le comportement QoL examiné donne la priorité à cet emplacement comme configuration principale. Les presets supplémentaires de ce chemin Data sont chargés après ceux du chemin historique `JCUser/rTats/presets/`. Pour les clés en double, la règle chargée en dernier gagne.

Ne supposez pas qu'un fichier gagne uniquement parce que son mod MO2 se trouve plus bas dans le panneau gauche. L'ordre de découverte et de fusion des presets compte également.

### Enseignement observé dans le projet

Pendant la validation interne, un override personnalisé dont le nom commençait par un nombre (`99-...`) a été fusionné **avant** les presets Alpia et Zaki. Ses modifications de clés en double ont été écrasées. Renommer le même fichier avec un préfixe alphabétique tardif `zzz-...` l'a fait fusionner après Alpia et Zaki ; des overrides représentatifs sont alors apparus correctement dans le MCM de RTC.

Il s'agit d'un résultat observé dans la configuration validée, non d'une garantie universelle pour toute version QoL ou tout système de fichiers. Si vous avez délibérément besoin d'une couche d'override finale, un nom comme :

```text
zzz-Custom-RTC.json
```

peut être utile. Vérifiez toujours l'ordre réel avec `Test / Reload configs` et inspectez la console ou le journal Papyrus. Ne déduisez pas la priorité du seul nom de fichier.

Le test interne a aussi montré que l'absence du dossier facultatif `JCUser/rTats/presets/` pouvait produire un avertissement sans empêcher la fusion des presets situés dans le chemin Data.

## 9. Preset Rhiven facultatif — distribution et raison d'être

Le téléchargement public se nomme :

```text
Rhiven RTC Settings.zip
```

Il est disponible à côté du guide anglais sous le nom [`Rhiven RTC Settings.zip`](../Rhiven%20RTC%20Settings.zip). L'archive installe le preset à cet emplacement :

```text
SKSE/Plugins/RapeTattoos/zzz-Rhiven-RTC.json
```

Le nom de l'archive/du mod et celui du preset sont volontairement différents : **Rhiven RTC Settings** est le paquet MO2 public, tandis que `zzz-Rhiven-RTC.json` est le véritable preset RTC ; son préfixe `zzz-` indique son rôle prévu de couche d'override tardive.

Il ne corrige pas un framework, ne remplace pas la QoL Extension et n'est pas requis pour faire fonctionner RTC, Alpia ou Zaki. Son rôle prévu est de fournir une couche d'override finale cohérente après le chargement des presets des auteurs Alpia et Zaki.

D'après le delta personnalisé validé en interne, un tel preset peut :

- harmoniser la casse des noms de groupes et certaines conventions de regroupement ;
- préserver les presets des auteurs en ne remplaçant que les clés choisies ;
- marquer sélectivement des catégories comme `(excluded)` pour l'usage automatique de RTC ;
- définir un comportement volontaire pour les entrées Full Body et Full Face ;
- garder la personnalisation isolée, vérifiable et amovible.

Les exclusions de contenu de ce preset relèvent d'une politique personnelle, non de corrections techniques ou de valeurs universelles. Examinez-les avant utilisation au lieu de les considérer comme la bonne configuration pour tous.

Installez le ZIP comme mod MO2 distinct et conservez-le après les réglages RTC d'Alpia et Zaki dans le panneau gauche. Exécutez ensuite `Test / Reload configs` et vérifiez l'ordre de fusion observé ; le nom tardif est volontaire, mais le journal RTC effectif reste la référence.

## 10. Installation et audit d'Alpia

Le projet testé utilisait le pack principal `Alpia Slavetats Pack` dans sa configuration **All-in-One**.

- Les extensions séparées Orc et Riekling n'étaient pas installées.
- Leurs presets RTC séparés n'étaient pas utilisés.
- Le `Public Whore Tattoo Replacer` séparé n'était pas installé.
- Le pack principal peut tout de même contenir des tatouages sur le thème Public Whore ; ce n'est pas le même composant que le remplacement séparé.

Le preset correspondant `Alpia Rtats Settings All in One` a été installé après le pack principal.

### Résultats de l'audit statique

Les deux fichiers JSON fournis par Alpia ont été analysés et comparés :

| Constat | Résultat |
| --- | ---: |
| Entrées du catalogue SlaveTats | **1 214** |
| Entrées configurées pour RTC | **1 205** |
| Entrées du catalogue sans règle RTC dédiée | **9** |
| Différences de casse dans les chemins de textures | **24** |
| Chemins de catalogue en double | **0** |
| Erreurs de syntaxe JSON | **0** |

La comparaison n'a trouvé aucune référence de texture RTC absente du catalogue SlaveTats lorsque la casse était ignorée. Cela ne prouve **pas** que JContainers ou RTC considère comme équivalentes des clés dont la casse diffère, ni que chaque fichier `.dds` référencé est physiquement présent ou s'affiche correctement.

Les neuf entrées sans règle RTC dédiée restent disponibles dans SlaveTats. Leur comportement automatique exact doit être testé, et non déduit du comptage statique.

Ces chiffres sont des **résultats d'audit statique**, pas la preuve d'une couverture exhaustive à l'exécution.

## 11. Installation de Zaki et précaution concernant No Overlap

Le projet testé utilisait :

- `Zaki Tattoos General Pack SE` **1.1.1** ;
- le **Full Pack**, contenant **841 entrées** ;
- des textures hybrides : **corps/pieds 4K** et **mains/visage 2K** ;
- aucun plugin RaceMenu facultatif ;
- aucune extension 8K ;
- aucun pack Zaki Beast.

Le fichier personnalisé du projet `Zaki RTC Settings` contenait **841 clés de textures** avec des affectations `Group`. Il était chargé après le pack de tatouages.

### Ne le remplacez pas aveuglément par No Overlap

`No Overlap for Rape Tattoo` a fait l'objet d'un audit statique, mais n'a **pas été installé tel quel**. Il s'agit d'un preset RTC tiers, non d'une extension de scripts.

Sa configuration Zaki couvre **528** clés Zaki. Comparée au preset de projet à 841 clés :

- **313 entrées Zaki sont omises** ;
- environ **137 entrées présentent des réaffectations de groupes importantes** (**161** différences en comptant aussi les simples changements de casse).

Le `settings.json` mixte de No Overlap qui a été examiné contenait aussi 254 clés Sexy Supplemental. L'installer comme fichier de réglages principal pourrait donc introduire du contenu sans rapport ou remplacer un mapping existant plus complet.

Les modifications de groupes logiques de No Overlap n'ont pas été vérifiées exhaustivement par rapport à la géométrie UV réelle. Examinez et fusionnez volontairement les règles souhaitées ; ne remplacez pas aveuglément le preset plus complet à 841 clés.

## 12. Sémantique du regroupement RTC

RTC limite normalement la sélection automatique à **un tatouage par groupe configuré**, sous réserve du reste de sa logique et de ses réglages.

Deux valeurs spéciales sont importantes :

- `(excluded)` — RTC ne doit jamais sélectionner automatiquement cette entrée. Le tatouage peut rester disponible pour une application manuelle dans SlaveTats si son catalogue et sa texture sont installés.
- `(unassigned)` — l'entrée n'est pas limitée par un groupe nommé, mais elle consomme toujours un emplacement d'overlay et reste soumise à la capacité des overlays.

Les groupes sont des libellés logiques. Ils ne constituent **pas** une détection géométrique des chevauchements UV. Deux textures affectées à des groupes logiques différents peuvent malgré tout se chevaucher visuellement, et une texture étendue peut couvrir plusieurs zones physiques alors que RTC ne voit que son groupe configuré.

Ne normalisez pas aveuglément les différences de casse des groupes. Confirmez d'abord le comportement réel, surtout lorsque des clés ou libellés de groupes ne diffèrent que par la casse.

## 13. Configuration MCM initiale

Après l'initialisation de RTC sur une sauvegarde jetable :

1. Ouvrez le MCM `Rape Tattoos`.
2. Ouvrez `General`.
3. Sélectionnez **`LOAD TATTOO CONFIG PAGES`**.
4. Attendez l'apparition de `Tattoos Page 1`, `Tattoos Page 2` et des pages suivantes.
5. Avec la QoL Extension installée, exécutez **`Test / Reload configs`**.
6. Inspectez la console ou les journaux temporaires de diagnostic pour chaque preset attendu et sa position dans la fusion.
7. Ouvrez des Tattoo Pages représentatives et comparez les groupes affectés aux règles prévues.

L'apparition des Tattoo Pages prouve que les pages ont été générées. Elle ne prouve **pas** qu'un override final a été chargé en dernier ou a gagné les clés en double.

La journalisation Papyrus détaillée peut aider au diagnostic, mais ne doit pas rester activée en jeu normal. Les fonctions de débogage de RTC peuvent également produire de nombreuses notifications et traces.

## 14. Persistance et fichiers utilisateur

L'état utilisateur et les réglages de RTC peuvent faire intervenir :

```text
Documents/My Games/Skyrim Special Edition/JCUser/rTats/settings.json
Documents/My Games/Skyrim Special Edition/JCUser/rTats/colorConfig.json
Documents/My Games/Skyrim Special Edition/JCUser/rTats/presets/
Data/SKSE/Plugins/RapeTattoos/
```

La QoL Extension peut également prendre en charge une destination de couleurs configurable sous `Data/SKSE/Plugins/RapeTattoos/ColorConfig/`.

Vérifiez où les fichiers sont réellement créés et mis à jour dans **votre** installation. Les chemins virtuels de MO2, le dossier Documents de Windows, les permissions et la présence d'un fichier de réglages principal dans le chemin Data peuvent déterminer l'emplacement actif.

Pour figer une configuration fonctionnelle connue, sauvegardez `JCUser/rTats` séparément du profil MO2. Une sauvegarde du profil seule peut ne pas inclure les données utilisateur écrites dans Documents.

## 15. Overlays RaceMenu et `skee.ini`

SlaveTats utilise en définitive les emplacements d'overlay RaceMenu. Les limites effectives sont configurées par zone dans le fichier gagnant `SKSE/Plugins/skee.ini`, notamment :

- `[Overlays/Body]`
- `[Overlays/Hands]`
- `[Overlays/Feet]`
- `[Overlays/Face]`

N'augmentez pas ces limites préventivement. Reproduisez d'abord un problème de capacité et inspectez le fichier gagnant actuel et le nombre d'overlays actifs. Des emplacements supplémentaires peuvent alourdir la synchronisation de SlaveTats et ne corrigent ni les catalogues manquants, ni les chemins de textures invalides, ni un regroupement RTC incorrect.

Les tatouages Full Body et Full Face peuvent aussi chevaucher d'autres entrées par conception. Traitez cela comme un choix de configuration volontaire, pas comme un problème que les groupes logiques peuvent toujours empêcher.

## 16. Compatibilité et précautions

- RTC indique explicitement **SlaveTats Performance Patch (Sejra)** comme incompatible.
- RTC indique explicitement **Monoman's Rape Tattoos Tweaked** comme incompatible.
- Un conflit historique de `Scripts/SlaveTatsMCMMenu.pex` impliquant PAH Diary Of Mine et SlaveTats NG est documenté en interne. Des fichiers différents ont été observés, mais aucun échec reproductible n'a été établi. Ne changez pas le gagnant fonctionnel connu sans test ciblé.
- Si le comportement est incohérent, contrôlez la version effective de JContainers et son fichier gagnant dans MO2. Un autre mod peut fournir une ancienne copie.
- Les raccourcis de débogage RTC peuvent entrer en conflit avec d'autres mods. Gardez le débogage RTC désactivé en jeu normal.
- Ne changez pas les scripts gagnants et ne fusionnez pas les fichiers de configuration à l'aveugle en réaction à un seul symptôme.
- Évitez les mises à niveau depuis d'anciennes installations RTC en cours de partie sans procédure de migration testée.

## 17. Liste de contrôle de validation

Utilisez une sauvegarde jetable et distinguez les contrôles statiques des résultats d'exécution.

- [ ] Confirmez les huit composants installés prévus pour votre configuration, à l'exclusion du preset Rhiven facultatif si vous avez choisi de ne pas l'installer.
- [ ] Vérifiez que la QoL Extension gagne ses conflits de scripts RTC.
- [ ] Reconstruisez ou actualisez le registre SlaveTats si le workflow SlaveTats installé l'exige.
- [ ] Exécutez `LOAD TATTOO CONFIG PAGES` après l'initialisation de RTC.
- [ ] Exécutez `Test / Reload configs`.
- [ ] Confirmez que les presets Alpia et Zaki sont signalés comme chargés.
- [ ] Confirmez l'ordre réel de fusion des presets, surtout pour tout override utilisateur final.
- [ ] Contrôlez dans le MCM des entrées représentatives autorisées, `(excluded)`, `(unassigned)`, Full Body et Full Face.
- [ ] Appliquez plusieurs tatouages Alpia et Zaki manuellement et via RTC.
- [ ] Vérifiez les chemins de textures par leur rendu réel, pas uniquement par les références JSON.
- [ ] Sauvegardez, rechargez et confirmez la persistance des overlays et de la configuration.
- [ ] Testez l'expiration Fade des tatouages temporaires.
- [ ] Testez les catégories joueur, PNJ et ZaZ si vous les utilisez.
- [ ] Confirmez les limites effectives d'overlays Body, Hands, Feet et Face.
- [ ] Refaites un test avec le débogage désactivé après le diagnostic.

Le projet source n'a pas achevé la couverture exhaustive des applications aléatoires, tous les scénarios Fade ni la validation visuelle de chaque texture. Ne marquez pas toute la pile comme entièrement validée à partir de quelques exemples réussis.

## 18. Dépannage

### Un tatouage manque

Contrôlez les trois couches séparément :

1. Le JSON de catalogue SlaveTats contient-il la définition ?
2. Le preset RTC pertinent contient-il une règle si l'application automatique est attendue ?
3. Le fichier de texture référencé existe-t-il réellement et s'affiche-t-il ?

Actualisez le registre SlaveTats si nécessaire après l'installation d'un nouveau catalogue.

### Une exclusion ou un groupe personnalisé n'est pas respecté

- Exécutez `Test / Reload configs`.
- Inspectez la séquence de fusion signalée.
- Confirmez la clé de texture exacte en double et sa casse.
- Confirmez que le nom de l'override final le fait réellement charger après les presets des auteurs.
- N'oubliez pas que la position dans le panneau gauche de MO2 ne prouve pas à elle seule la priorité de fusion de RTC.

### Les réglages ne persistent pas

- Inspectez l'emplacement réel de `JCUser/rTats` et la configuration du chemin Data.
- Vérifiez les permissions Windows et si le jeu écrit dans le dossier Documents attendu.
- Déterminez quel `settings.json` est actif avant de modifier ou restaurer des fichiers.
- Sauvegardez la source de configuration MO2 et les données utilisateur externes.

### Les Tattoo Pages manquent

- Attendez la fin de l'initialisation de RTC et de l'enregistrement du MCM.
- Ouvrez `General` et utilisez `LOAD TATTOO CONFIG PAGES`.
- Si les pages n'apparaissent toujours pas, contrôlez l'initialisation de RTC, les scripts gagnants, les dépendances et les journaux.

### Trop de tatouages se chevauchent

- Examinez les groupes logiques RTC des clés de textures concernées.
- Vérifiez si les entrées sont `(unassigned)` ou volontairement Full Body/Full Face.
- Ne supposez pas que RTC effectue une détection géométrique des chevauchements.
- Testez les changements de groupes sur une sauvegarde jetable avant de consolider les presets.

### Problèmes de synchronisation ou de performances

- Inspectez le nombre d'overlays actifs et le fichier `skee.ini` gagnant.
- Recherchez les patchs SlaveTats/RTC incompatibles.
- Confirmez le gagnant JContainers.
- Désactivez la journalisation de débogage détaillée de RTC.
- N'augmentez pas les limites d'overlays tant qu'un besoin de capacité mesuré n'est pas établi.

## 19. Statut de validation et avertissement

Cette pile d'extension a été installée et auditée statiquement dans **NEFARAM-Rhiven 17.3.7**, puis conservée dans la **base 17.3.8**.

Éléments confirmés dans la configuration interne :

- séparation des composants d'origine et ajoutés à partir des instantanés MO2 original et modifié ;
- ordre prévu du bloc d'extension dans le panneau gauche ;
- gagnants de scripts RTC attendus de la QoL Extension ;
- comptages JSON statiques Alpia et Zaki décrits dans ce guide ;
- fusion observée dans la console d'Alpia, Zaki et d'un preset personnalisé au nom alphabétiquement tardif ;
- résultats MCM représentatifs montrant que les overrides du preset tardif gagnaient après rechargement.

Éléments qui restent testés de façon non exhaustive selon la documentation source :

- couverture complète de l'application aléatoire pour toutes les entrées des catalogues ;
- comportement de Fade dans tous les cas pertinents ;
- vérification exhaustive de chaque fichier de texture physique et de son placement ;
- toutes les combinaisons de catégories joueur, PNJ et ZaZ ;
- chaque interaction entre de larges textures Full Body/Full Face et d'autres overlays.

Les utilisateurs doivent valider cette pile sur des sauvegardes jetables avant de l'adopter dans une partie permanente.

## 20. Références internes du projet

Ces documents du dépôt contiennent la piste d'audit détaillée du projet. Il s'agit de dossiers techniques internes, non d'instructions d'installation génériques :

- [Architecture des tatouages et notes de développement](../../../06%20-%20GAMEPLAY/TATTOOS/README.md)
- [Audit d'intégration Alpia et RTC QoL](../../../06%20-%20GAMEPLAY/TATTOOS/ALPIA-08-2026-QOL.md)
- [Audit Zaki General et No Overlap](../../../06%20-%20GAMEPLAY/TATTOOS/ZAKI-GENERAL-RTC.md)
