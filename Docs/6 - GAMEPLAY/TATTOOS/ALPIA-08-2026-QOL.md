# Alpia Scribbles — intégration NEFARAM-Rhiven (08.2026)

**Projet :** NEFARAM-Rhiven 17.3.7 — MO2 `ELEANOR Stable`  
**Statut au 11/10/2026 :** installé, audit statique effectué ; **tests en jeu non encore réalisés**.  
**Sources :** [documentation originale d'Alpia](./Alpia%20Scribbles%20Slavetats%20Pack.docx), [guide général des tatouages](./README.md), fichiers JSON et sources Papyrus transmis lors de l'audit.

> Cette fiche est un aide-mémoire technique **spécifique à notre instance** ; la documentation DOCX de l'auteur reste la référence, notamment pour les cartes UV, les zones corporelles et les options de téléchargement.

## 1. Composition et ordre MO2 observés

Tous ces ajouts sont à la fin de `[35 - SexLab Content]`, après `Advanced Nudity Detection`.

| Ordre panneau gauche | Mod | Rôle |
| --- | --- | --- |
| 1 | `Fade Tattoos Continued - Rhiven` — 2.1.0 | Durée / disparition des marques temporaires |
| 2 | `Rape Tattoos Continued - Rhiven` — 2.0.3 | Moteur de sélection et d'application |
| 3 | `Rape Tats Continued 2.0.3 QoL Extension - Rhiven` — rev1 | Patch des scripts RTC, fusion automatique des JSON |
| 4 | `Alpia Slavetats Pack - Rhiven` — 08.2026 All-in-One | Catalogue SlaveTats et textures |
| 5 | `Alpia Rtats Settings All in One - Rhiven` | Preset RTC principal Alpia |

**Ne pas inverser RTC et QoL :** les fichiers du correctif doivent gagner les conflits contre les originaux RTC. Conflits attendus : `rapeTattoos.pex`, `rapeTattoos_mcm.pex`, `rapeTattoos_utils.pex` et leurs trois sources `.psc`.

Le pack Alpia principal est installé **All-in-One**, **sans** les extensions séparées Orc et Riekling. Le `Public Whore Tattoo Replacer` distinct n'a pas été installé. Le pack principal peut néanmoins comporter des tatouages thématiques « Public Whore », ce qui n'est pas la même chose que le replacer.

## 2. Bien distinguer les deux types de JSON

| Fichier | Utilisateur | Fonction |
| --- | --- | --- |
| `Alpia V2.json` | SlaveTats | Tableau d'entrées `name`, `area`, `section`, `texture` : catalogue visible dans SlaveTats |
| `Alpia V2 rtats settings.json` | Rape Tattoos Continued | Objet dont chaque clé est le chemin d'une texture `.dds` et contient au minimum `Group` : règles de sélection automatique |

**All-in-One du FOMOD SlaveTats ≠ fusion des presets RTC.** Ce sont deux mécanismes indépendants.

Fichier RTC actif dans MO2 :

```text
Alpia Rtats Settings - Rhiven/
└── SKSE/
    └── Plugins/
        └── RapeTattoos/
            └── Alpia V2 rtats settings.json
```

Les fichiers `Alpia - Orc Rtats Settings.json` et `Alpia - Riek Rtats Settings.json` ont été **masqués dans MO2** (non utilisés tant que les packs associés ne sont pas installés).

## 3. QoL Extension rev1 — emplacement des presets et priorité

D'après le manuel Alpia et les sources fournies, le correctif charge et fusionne plusieurs `.json`, ce qui évite de modifier le `settings.json` d'origine pour chaque pack.

Chemins pris en charge :

```text
Data/SKSE/Plugins/RapeTattoos/
    settings.json                    # devient le fichier principal / cible d'écriture s'il existe
    Alpia V2 rtats settings.json     # preset additionnel
    AutreAuteur.json                 # autre preset éventuel
```

Le chemin historique reste reconnu :

```text
Documents/My Games/Skyrim Special Edition/
└── JCUser/
    └── rTats/
        ├── settings.json
        ├── colorConfig.json
        └── presets/
            └── AutreAuteur.json
```

**Priorité :** `Data/SKSE/Plugins/RapeTattoos/` prime pour le `settings.json` principal lorsqu'il existe ; les presets supplémentaires de ce répertoire sont chargés après ceux de `JCUser/rTats/presets/`. Pour les doublons de clés, la configuration chargée en dernier prend le dessus.

Dans un même répertoire : fichiers non préfixés par un nombre d'abord (ordre alphabétique), puis fichiers à préfixe numérique (ordre numérique), pour permettre une priorité volontaire.

**Dans notre installation actuelle :** aucun besoin de créer **manuellement** `JCUser/rTats` pour déposer le preset Alpia. **Ne pas en conclure que RTC n'utilisera jamais JCUser :** son fichier principal et ses réglages persistants peuvent encore dépendre du chemin historique en l'absence de `Data/.../settings.json`. Vérifier la création et l'écriture effective lors du test MCM ; ne pas présumer d'une persistance automatique dans le mod MO2.

**Couleurs :** le correctif annonce également une destination configurable, notamment `Data/SKSE/Plugins/RapeTattoos/ColorConfig/colorConfig.json`. Vérifier la destination effectivement choisie avant d'éditer ou de sauvegarder.

## 4. Audit croisé des JSON Alpia (11/10/2026)

Contrôles réalisés sur `Alpia V2.json` et `Alpia V2 rtats settings.json` transmis directement :

| Mesure | Résultat |
| --- | ---: |
| Entrées du catalogue SlaveTats | **1 214** |
| Entrées configurées RTC | **1 205** |
| Références RTC absentes du catalogue, comparaison insensible à la casse | **0** |
| Entrées SlaveTats sans règle RTC dédiée | **9** |
| Différences de casse sur les chemins des textures | **24** |
| Doublons de chemins dans le catalogue SlaveTats | **0** |
| Erreurs de syntaxe JSON | **0** |

**Les neuf entrées sans règle RTC** (toujours disponibles pour SlaveTats) :

1. `Full - Beggar`
2. `Full - Beggar (red)`
3. `Full - Prostitute + Addons (red)`
4. `Full - Public Whore (red)`
5. `Nipples - R bite mark L heart`
6. `L + R Breast - Oppai (Kanji)`
7. `RBc - Slave`
8. `R Upper Back - Bad kitty`
9. `L Upper Side - Cumslut 2`

**Réserves importantes :** la comparaison ignore la casse, mais cela **ne démontre pas** que les clés de configuration manipulées par JContainers sont insensibles à la casse. Les 24 variantes sont donc à valider en jeu ou en audit ciblé du comportement exact des clés. Le catalogue JSON ne démontre pas non plus la présence physique de tous les fichiers DDS dans l'archive.

## 5. Groupes et prévention des chevauchements

Dans RTC, `Group` représente une zone **logique** ; la limite usuelle est d'un tatouage par groupe. Ce n'est **pas** une détection géométrique de la surface réellement couverte sur la texture UV.

- `(excluded)` : l'entrée ne doit pas être choisie automatiquement.
- `(unassigned)` : entrée hors groupe restrictif ; reste soumise aux capacités des overlays.
- La configuration Alpia contient **119 entrées exclues** et **48 non assignées** (regroupement des libellés sans distinction de casse).
- Les variations `Front Lower` / `front lower` ou `(Excluded)` / `(excluded)` méritent une vérification du comportement JContainers / Papyrus avant toute « normalisation » automatique.

**No Overlap audité le 11/10/2026 :** il s'agit de presets JSON tiers (528 règles Zaki, 254 Sexy Supplemental dans sa variante mixte), non installés. Voir [Zaki](./ZAKI-GENERAL-RTC.md). Le delta [Eleanor](./ELEANOR-RTC-SETTINGS.md) exclut six thèmes Alpia et harmonise des noms de groupes ; efficacité à confirmer en jeu.

## 6. Fonctions utiles du MCM RTC QoL

| Commande | Usage recommandé |
| --- | --- |
| `Test / Reload configs` | À utiliser sur sauvegarde de test pour reconstruire la carte et examiner le rapport (Papyrus ou console si ConsoleUtil installé) |
| `Merge all into settings.json` | **Ne pas utiliser pour l'instant** ; écrit une configuration consolidée et fait perdre l'intérêt pratique des presets séparés |
| `Enable detailed Papyrus logging` | Temporaire en cas de diagnostic, désactivé en partie normale |

Le correctif conserve les noms de ModEvents `RapeTattoos_addTattoo` et `RapeTattoos_addTattooV2` observés dans les sources. Les appels de futurs mods devront être testés en situation réelle ; se reporter au [guide API](./README.md).

## 7. Vérifications avant partie définitive

- [x] Installation MO2 des cinq composants et ordre général relevé.
- [x] Conflits de scripts QoL → RTC conformes à la fonction du patch.
- [x] Fichier RTC Alpia principal conservé, presets Orc/Riek masqués.
- [x] Audit de syntaxe et croisement statique des deux JSON.
- [ ] Reconstruire le registre SlaveTats dans son MCM ; regarder si la console signale des erreurs JSON.
- [ ] Dans RTC, lancer `Test / Reload configs` puis examiner la liste / le journal.
- [ ] Vérifier le traitement effectif des 24 clés avec casse différente et des variantes de groupes.
- [ ] Confirmer la présence des textures `.dds` et leur affichage sur un personnage de test.
- [ ] Appliquer quelques tatouages, sauvegarder, recharger ; contrôler l'intégration Fade Tattoos.
- [ ] Vérifier où `settings.json` et `colorConfig.json` sont réellement créés/modifiés et leur persistance.
- [ ] Conserver le debug désactivé et ne pas augmenter les limites `skee.ini` sans besoin mesuré.
- [x] Réaliser les audits statiques Zaki et No Overlap ; documents disponibles.
- [x] Installer le delta Eleanor dans un mod séparé ; **validation en jeu à venir**.

## 8. Sources et limites

- [Alpia Scribbles — documentation originale Word](./Alpia%20Scribbles%20Slavetats%20Pack.docx) : description des collections, FOMOD, instructions RTC, patch QoL rev1, schémas des zones corporelles.
- [TATTOOS/README.md](./README.md) : architecture SlaveTats / Fade / RTC et exemples d'API.
- `Alpia V2.json` et `Alpia V2 rtats settings.json` : inventaires audités, **non déposés ici** ; chiffres consignés pour le suivi.
- `rapeTattoos.psc`, `rapeTattoos_mcm.psc`, `rapeTattoos_utils.psc` : sources du patch transmises pour revue ; **pas de diff exhaustif avec les trois sources RTC d'origine**, ni preuve de compilation/chargement in-game.

**Politique du projet :** conserver les fichiers auteurs intacts et les adaptations éventuelles dans des mods MO2 Rhiven séparés, traçables et réversibles.
