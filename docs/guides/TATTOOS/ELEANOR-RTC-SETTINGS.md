# Eleanor RTC Settings — preset personnalisé (11/10/2026)

**Instance :** NEFARAM-Rhiven 17.3.7 · MO2 `ELEANOR Stable`  
**Statut :** JSON **créé et installé dans MO2** ; **aucun test fonctionnel en jeu pour le moment**.

## Objectif
Conserver intacts les mods auteurs Alpia, Zaki, RTC 2.0.3 et son patch QoL rev1. Personnaliser le *catalogue d'application automatique* RTC lors des événements éligibles, et non le catalogue manuel SlaveTats.

### Emplacement
```text
[35 - SexLab Content]
  Alpia Rtats Settings All in One - Rhiven
  Zaki Tattoos General Pack SE - Rhiven
  Zaki RTC Settings - Rhiven
  Eleanor RTC Settings - Rhiven/
    README.txt
    SKSE/Plugins/RapeTattoos/zzz-Eleanor-RTC.json
```
Le préfixe numérique `99-` est prévu pour appliquer les overrides après les presets non numérotés, conformément à l'ordre documenté dans QoL rev1. Vérification effective à effectuer en jeu. **Ne pas placer un `settings.json` concurrent dans ce mod.**

## Règles souhaitées / décisions de gameplay
- Tatouages automatiques RTC : **visage, tête, bouche et corps autorisés**.
- **Un tatouage par groupe logique** au maximum, en conservant les paramètres RTC ; le groupe n'est pas une détection de recouvrement UV.
- Tatouages **Full Body / Full Face autorisés** même si les chevauchements sont inévitables ; retrait volontaire en jeu.
- Zaki **General** autorisé ; **Zaki Beast non installé**.
- Packs additionnels **Alpia Orc / Riekling non installés**, presets correspondants masqués MO2.
- Six thèmes **Alpia exclus de l'attribution automatique** : `BBC`, `Cow`, `Dog`, `Dragonwhore breeding`, `Horse Breeding`, `Kitten`. Ils restent accessibles dans SlaveTats si leurs textures sont installées.
- Toutes les autres collections Alpia conservent leur statut, sous réserve des overrides détaillés ci-dessous.

## Construction du JSON
Fichiers de référence : `Alpia V2 rtats settings.json` (1 205 règles) et preset Rhiven Zaki (841 règles).

| Traitement annoncé lors de la génération | Volume |
| --- | ---: |
| Entrées Alpia des six collections exclues | 452 |
| Exclusions nouvelles hors entrées déjà marquées `(excluded)` | 407 |
| Harmonisations de casse des groupes Alpia | 293 |
| Éléments « Full » réaffectés | 53 |
| Nombre total de règles overrides du preset Eleanor | 753 |
| Règles Zaki directement modifiées | 0 |

**Important :** chiffres issus de l'étape de génération et de son contrôle statique ; ils doivent être reconfirmés si le fichier est régénéré ou modifié. Certains tatouages Full précédemment `(excluded)` ont été réactivés : vérifier les résultats réels sur les zones multiples.

Le JSON Eleanor doit rester un **delta de configuration** : ne pas recopier aveuglément les 2 046 entrées combinées. Les règles No Overlap ont été analysées, **pas intégrées automatiquement** dans ce premier preset.

## Validation à venir
- [x] Presets Alpia et Zaki fournis et comparés statiquement.
- [x] `zzz-Eleanor-RTC.json` installé dans mod MO2 distinct.
- [ ] Vérifier que le patch QoL fusionne et applique **en dernier** les overrides Eleanor ; contrôler les logs.
- [ ] Vérifier `(excluded)` pour chaque collection interdite et les Full activés.
- [ ] Vérifier l'égalité effective des libellés de groupes entre Alpia et Zaki.
- [ ] Tester événements RTC PC/PNJ et paramètres MCM (le JSON ne cible pas Eleanor à lui seul).
- [ ] Tester sauvegarde/rechargement et disparition via Fade Tattoos.
- [ ] Vérifier nombre et gestion des overlays RaceMenu, sans changer `skee.ini` préventivement.

**À éviter :** bouton MCM `Merge all into settings.json` avant sauvegarde et contrôle du dossier de destination. Les mods auteurs restent inchangés.

Voir [Alpia](./ALPIA-08-2026-QOL.md), [Zaki](./ZAKI-GENERAL-RTC.md) et [guide général](./README.md).

## Observation en jeu — 11/10/2026 (première ouverture MCM)

1. Charger une sauvegarde de test et ouvrir `Rape Tattoos` dans le MCM.
2. Dans l'onglet `General`, sélectionner **`LOAD TATTOO CONFIG PAGES`** (bouton en haut à droite sous `Tattoo configuration`).
3. Attendre que les onglets `Tattoos Page 1`, `Tattoos Page 2`, etc. apparaissent à gauche.
4. Vérifier les groupes dans `Name & Assigned Set` et les clés `Texture Path` ; cela confirme la présence des pages, **pas nécessairement la bonne fusion des overrides**.
5. Contrôler une référence d'une collection exclue et une entrée non exclue, puis journaliser le résultat **avant toute sauvegarde définitive**.

### Problème constaté — à diagnostiquer

Sur `Tattoos Page 1`, `Alpia Scribbles V2\\Dog\\1b - heart cum.dds` apparaît dans le groupe **`MISC 1 - B`**, alors que la configuration Eleanor doit exclure l'ensemble de `Dog`. En revanche, `Horse Breeding\\handjob 25g 1b.dds` apparaît `(EXCLUDED)` mais cette exclusion existe déjà dans la configuration Alpia de référence. **Conclusion :** pages RTC chargées, priorité/fusion de `zzz-Eleanor-RTC.json` **non confirmée** ; ne pas valider encore le preset. Vérifier si les fichiers personnalisés sont lus, leur ordre de fusion et les erreurs de journal avant de modifier les configurations.

## Correctif confirmé par la console — 11/10/2026

Le premier nom `99-Eleanor-RTC.json` était fusionné **avant** Alpia et Zaki et ses overrides étaient ensuite écrasés. Renommage effectué dans MO2 : **`zzz-Eleanor-RTC.json`** (contenu JSON inchangé).

Ordre **observé dans la console** après relance du jeu et `Test / Reload configs` :

```text
Merged Alpia V2 rtats settings.json - 1205 mappings
Merged Zaki-General-RTC-Rhiven.json - 841 mappings
Merged zzz-Eleanor-RTC.json - 753 mappings
Combined tattoo library contains 2920 tattoo mappings
```

**Validation acquise :** découverte du fichier et priorité de fusion désormais correctes. **Validation restante :** vérifier dans les pages MCM que Dog, Kitten, Horse Breeding, BBC, Cow et Dragonwhore breeding deviennent `(EXCLUDED)`, et contrôler les Full Body en jeu. La console signale toujours l'absence du dossier facultatif `Documents/My Games/Skyrim Special Edition/JCUser/rTats/presets/` ; l'analyse se poursuit malgré cet avertissement.

**Pour une nouvelle installation / partie :** conserver `zzz-Eleanor-RTC.json`, puis exécuter `Test / Reload configs` ; ne pas revenir à `99-Eleanor-RTC.json` et ne pas utiliser `Merge all into settings.json` sans sauvegarde.
