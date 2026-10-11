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

## Contrôle MCM complémentaire — 11/10/2026

Capture après renommage et rechargement : les entrées `Horse Breeding/1B - Horsecock Property.dds`, `Cow/1B - Livestock Sex Slave.dds` et trois entrées `BBC` sont affichées **`(EXCLUDED)`**. Sur le même écran, les entrées autorisées `Nord` et `General` restent dans `MISC 1 - B`, tandis que `Crime/RA side - punish.dds` est affecté à `RIGHT ARM`. Deux entrées `Dog` avaient également été constatées exclues lors du test précédent.

**Résultat :** conformité observée de ces cas représentatifs dans le MCM. **Restent à vérifier :** `Kitten`, `Dragonwhore breeding`, les règles Full Body et l'application effective en jeu. Les observations ne garantissent pas que chaque entrée des six collections est correcte.

## Vérification supplémentaire MCM — 11/10/2026 (pages 2 et 4)

La capture de la page 2 montre `Dragonwhore breeding/LA - make me a mommy` comme **`(EXCLUDED)`**, ainsi que `Cow/LA - Massage my tits`. Sur la page 4, `Kitten/LB - tamed`, `Dog/LB - Submissive`, `Horse Breeding/Spermtank LB` et `Cow/LB - Milktank` apparaissent également **`(EXCLUDED)`**. Les autres tatouages `Mage`, `Crime`, `Nord`, `Bandit`, `General`, `Prostitute` sont toujours affectés à des groupes corporels ordinaires.

**Bilan MCM : au moins une entrée vérifiée pour chacun des six thèmes exclus** (BBC déjà vu page 1). Test représentatif concluant, non exhaustif ; les applications aléatoires et Full Body restent à tester.

## Contrôle MCM Full Face — 11/10/2026 (page 40)

Sur la page 40 RTC, des entrées Full Face sont autorisées : `Toilet Prison` et `Slut Pop` en groupe `FACE`, `Public Whore` et `Prostitute + Addons` en `FACE`, ainsi que `Nord Breeder (head)` en `FOREHEAD`. Les entrées Full Face `BBC 2`, `BBC 3` et `Kitten` restent correctement `(EXCLUDED)`. Les variantes `Public Whore (red)` et `Prostitute + Addons (red)` demeurent exclues, sans preuve qu'il s'agisse d'un dysfonctionnement (exclusions héritées possibles).

**Attention :** page Full **visage/tête**, ne démontre pas encore l'activation ni le rendu des Full **Body**. Vérification corporelle et application en jeu toujours en attente.
