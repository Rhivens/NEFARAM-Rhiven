# NEFARAM-Rhiven — Roadmap nouvelle partie & évolution du modpack

**Version de travail :** 2.0 — chantier ouvert le **17 novembre 2026**  
**Socle de référence :** NEFARAM **17.3.8** · profil MO2 `Eleanor 17.3.8 - Naked Defeat`  
**État :** **PLANIFICATION / AUCUNE MIGRATION VALIDÉE**  
**Objectif :** préparer une **nouvelle partie propre**, intégrer les derniers changements ciblés, et **récupérer au maximum les réglages MCM** déjà réalisés pour éviter environ quatre heures de reconfiguration.

> [!IMPORTANT]
> La configuration NEFARAM-Rhiven précédente a été finalisée (phases 6 à 8 de l'ancienne roadmap) puis testée pendant **plusieurs jours de jeu**. **Ces validations ne sont pas à recommencer intégralement** : seuls les changements du présent chantier et leurs interactions sont à contrôler.
>
> Cette roadmap **remplace** l'ancienne procédure de finalisation. Les étapes historiques restent consultables via l'historique Git de `ROADMAP.md`, le [changelog](CHANGELOG.md) et les [documents de validation](Docs/VALIDATION/08-TESTING.md).

---

## 0. Scénario de départ et principe de sécurité

### Sauvegardes déjà disponibles

- **`NEFARAM_Start`** : sauvegarde d'origine à charger pour entrer dans la salle d'attente **Skyrim Unbound**, puis créer le personnage et lancer la partie.
- **`Eleanor_Start`** : sauvegarde personnelle réalisée **après** environ 2 h de création d'Eleanor et 4 h de réglages MCM, **avant** son départ pour Bordeciel.
- **Eleanor** : preset RaceMenu **JSON** déjà sauvegardé ; l'apparence peut être restaurée indépendamment de `Eleanor_Start`. Préserver également les éléments éventuels nécessaires à la tête et aux overlays.

### Stratégie privilégiée

1. **Exporter les MCM de `Eleanor_Start`**, dans un profil de test qui conserve **tous les mods actuels**.
2. Modifier le modpack **sur une copie du profil / de l'installation**, puis régénérer les sorties nécessaires.
3. Charger **`NEFARAM_Start`** avec le modpack modifié.
4. Réimporter les paramètres MCM **compatibles**, recréer Eleanor via RaceMenu et initialiser les nouveaux mods.
5. Créer une **nouvelle sauvegarde de départ** et effectuer des tests avant de quitter Skyrim Unbound.

**Solution secondaire, seulement si nécessaire :** examiner sur une **copie** si `Eleanor_Start` peut être réutilisée après les suppressions. Ce n'est **pas** la voie par défaut, car des quêtes, scripts et aliases peuvent déjà être initialisés dans cette sauvegarde.

> [!CAUTION]
> **Ne jamais écraser `NEFARAM_Start`, `Eleanor_Start`, le preset RaceMenu, les fichiers MCM exportés ou le profil MO2 validé.** Ne pas désinstaller des mods scriptés sur la sauvegarde d'origine et ne pas lancer de nettoyage ReSaver automatique.

---

## Phase 1 — Sauvegarder et éprouver la récupération MCM [PRIORITÉ ABSOLUE]

**But :** vérifier que les ~4 h de configuration MCM peuvent être transférées avant la moindre modification structurelle.

- [ ] Sauvegarder `Eleanor_Start`, `NEFARAM_Start`, le preset RaceMenu JSON et les fichiers de configuration hors du dossier de travail.
- [ ] Créer une **copie de test du profil MO2 actuel** ; conserver intact le profil validé.
- [ ] Vérifier **MCM Memory** : version, compatibilité Skyrim/SKSE, dépendances, éventuels conflits avec **MCM Recorder** et mode de restauration manuelle sur sauvegarde préexistante.
- [ ] Installer MCM Memory **sur la copie de test uniquement**.
- [ ] Charger `Eleanor_Start` avec sa **modlist d'origine**, attendre l'initialisation de tous les MCM et réaliser un **export complet** vers un profil externe.
- [ ] Vérifier concrètement la **liste des MCM et le nombre de paramètres exportés** ; noter les menus absents ou incomplets.
- [ ] Examiner spécialement les mods avec **activation / initialisation préalable** : **BeeingFemale NG**, **Private Needs**, **Bathing in Skyrim**, et tout autre MCM utilisant des pages dynamiques.
- [ ] Tester, idéalement sur une **copie de `NEFARAM_Start` et à modlist inchangée**, une **restauration manuelle** des paramètres ; vérifier les activations, valeurs, raccourcis, widgets et états effectivement restaurés.
- [ ] Inventorier les configurations **non couvertes** : JSON externes, profils propres à certains mods, UI/HUD, Wheeler, touches, widgets, etc.
- [ ] Sauvegarder l'export MCM et rédiger un bref bilan **réussi / partiel / insuffisant**.

**Critère de passage :** un export utilisable **et une restauration réellement testée**. Ne pas présumer que tous les MCM, boutons d'activation ou états de scripts sont transférables ; prévoir les réglages manuels résiduels.

---

## Phase 2 — Préparer la nouvelle configuration MO2

**But :** intervenir uniquement sur un environnement réversible.

- [ ] Dupliquer / sauvegarder le profil MO2 et les sorties générées importantes (Pandora, Synthesis, BodySlide si concerné).
- [ ] Relever la **version exacte des mods actuels**, les dépendances et les correctifs Rhiven avant les modifications.
- [ ] Contrôler les conflits et dépendances des ESP/ESL concernés avec **MO2, LOOT/xEdit et la liste des masters**.
- [ ] Conserver une liste **avant / après** (modlist, plugins et load order) pour la documentation GitHub.
- [ ] Ne pas réouvrir sans raison la validation de toutes les traductions, de l'UI et des systèmes déjà éprouvés.

### Suppressions prévues

- [ ] **Enslaved by the Thalmor** — retirer le mod et contrôler ses éventuels dépendants / patches.
- [ ] **Unethical Alchemy** — retirer le mod **et son correctif Rhiven associé**, après vérification des dépendances.
- [ ] **SexLab Approach / Approach Redux** — retirer le mod, ses éventuels patches, ses traductions dédiées et ses dépendants ; abandonner les anciens réglages MCM correspondants.

### Ajouts / évolutions prévues

- [ ] **Unethical SpellCraft** — intégrer selon l'étude déjà menée ; revérifier la version retenue, les requirements, conflits et traduction avant installation.
- [ ] **Estrus Unified 1.3** — intégrer en version fusionnée (voir phase 3).
- [ ] **SLIF NG** — évaluer l'ajout et son profil **CBBE 3BA**, avec vérification de l'ancien SLIF et de ses patches.
- [ ] **Fill Her Up** — **étude seulement** : comparer la Baka Edition actuellement installée (+ FR) à **FHU Crajjj Edition 1.0.5**, notamment les scripts, dépendances, intégration SLIF NG et traduction. **Aucun remplacement automatique décidé.**
- [ ] Vérifier si les autres frameworks corporels demandent des ajustements : **BeeingFemale NG, Aroused BodyMorphs, Milk Mod Economy**, et les mods déjà présents.

---

## Phase 3 — Estrus Unified 1.3 : intégration ciblée

**Documentation de référence :** [Estrus Unified](Docs/06%20-%20GAMEPLAY/ESTRUS%20CHAURUS/Estrus%20Unified) et [dossier Estrus](Docs/06%20-%20GAMEPLAY/ESTRUS%20CHAURUS/).

### Architecture confirmée

À partir de **Unified 1.1**, Chaurus, Spider et Dwemer sont fusionnés dans **`EstrusUnified.esp` + `EstrusUnified.dll`**. La version **1.3** inclut les ressources / animations Estrus nécessaires. Le guide historique Yiin & PastryFish reposait sur les anciens modules séparés ; **PastryFish a confirmé sur Discord NEFARAM le 17 novembre 2026 que ces anciens modules ne sont plus à installer et a corrigé son guide**. Le chargement sans masters manquants a été confirmé, mais les tests de stabilité / gameplay restent à faire.

- [ ] Installer **Estrus Unified 1.3** et ses **dépendances générales** correspondant à notre version de Skyrim.
- [ ] **Ne pas installer / activer** les anciens `EstrusChaurus.esp`, `EstrusSpider.esp`, `EstrusDwemer.esp`, `zzEstrus.esp`, `EstrusForSkyrimNG.dll` et leurs anciens patches de scripts.
- [ ] Chercher d'éventuels **mods tiers qui référencent encore les anciens noms de plugins ou FormIDs** ; les examiner avant d'activer le nouveau profil.
- [ ] Vérifier le **FOMOD 1.3** : `Core` obligatoire ; patch **MME** uniquement si version / configuration correspondante et **sans cocher ce patch si MME Extensions est utilisé** ; patch **SexLab Parasites** selon sa version et les autres patches de scripts.
- [ ] Contrôler **`EstrusUnified.dll`**, animation assets et sortie Pandora. Ne pas confondre le dossier `SLIFNG` inclus dans Unified avec une installation complète du framework SLIF NG.
- [ ] **BeeingFemale NG** : confirmer dans le MCM la détection de Unified et la gestion des grossesses / morphs.
- [ ] **SLIF NG / CBBE 3BA** : tester les changements de ventre / poitrine / fesses, leur cumul et remise à zéro.
- [ ] **Devious Devices** : vérifier l'intégration native de Unified ; ne pas ajouter préventivement les anciens patches ED/ES DDI des addons séparés.
- [ ] **Oninus Lactis NG 2.1.0** : optionnel, décision et compatibilité à valider ; vérifier slot FOMOD / CBPC si retenu.
- [ ] **Companions Chaurus / Spider : désactivés** dans le MCM ; ne pas activer **Summon Snap** dans Pandora.
- [ ] **OviBody : exclu** ; **Curse of Life : exclu**.
- [ ] Tester, sur sauvegarde jetable, les déclenchements Chaurus / Spider / Dwemer, les animations, la récupération du contrôle et les interactions avec SexLab.

> **Nuance :** l'absence de masters manquants et la réussite du chargement ne prouvent pas à elles seules la stabilité prolongée ni la compatibilité de tous les mods tiers.

---

## Phase 4 — Génération des sorties et contrôles pré-lancement

- [ ] Vérifier les règles de priorité MO2 et les scripts écrasés par les patches sélectionnés.
- [ ] Régénérer **Pandora** après le changement d'animations/comportements ; conserver la sortie dédiée active et confirmer la fin sans erreurs bloquantes.
- [ ] **Synthesis : inspecter les patchers actifs** et les changements de plugins / records. Régénérer si la nouvelle modlist invalide ou modifie les sorties produites ; ne pas conserver un patch obsolète.
- [ ] Régénérer **BodySlide** uniquement pour les ajouts qui le nécessitent ; vérifier **Build Morphs** pour le corps concerné.
- [ ] Contrôler les masters manquants, les warnings LOOT pertinents, les conflits xEdit et les plugins générés.
- [ ] Examiner `Overwrite` et actualiser les snapshots **MO2 gauche / droite / loadorder / modlist / plugins** une fois la configuration figée.

---

## Phase 5 — Nouvelle partie, MCM et restauration d'Eleanor

1. [ ] Charger la sauvegarde officielle **`NEFARAM_Start`**, **pas** le bouton vanilla `New Game`.
2. [ ] Attendre l'enregistrement / la stabilisation des MCM du **nouveau** modpack.
3. [ ] Effectuer la **restauration MCM manuelle** depuis l'export validé en phase 1.
4. [ ] Activer et initialiser les MCM qui l'exigent (**BeeingFemale NG, Private Needs, Bathing in Skyrim**, etc.) avant ou pendant la restauration **selon le fonctionnement réel de chaque mod**.
5. [ ] Vérifier l'absence d'erreurs dues aux **mods retirés** : leurs réglages ne doivent pas être réinjectés dans des systèmes inexistants.
6. [ ] Configurer manuellement les **nouveaux MCM** (notamment Estrus Unified et, si retenu, SLIF NG / nouveau FHU).
7. [ ] Contrôler les réglages hérités : survie, SexLab, fertilité, overlays, HUD, widgets, TrueHUD, SkyHUD, Wheeler, raccourcis AZERTY.
8. [ ] Recréer **Eleanor** à partir du preset **RaceMenu JSON** ; vérifier la tête, cheveux, overlays, équipement et morphologie.
9. [ ] Créer une nouvelle sauvegarde distincte, par exemple **`Eleanor_Start_Rhiven_v2`**, sans écraser les points de départ historiques.
10. [ ] **Quitter complètement Skyrim**, relancer, charger cette nouvelle sauvegarde et vérifier la **persistance** des MCM, de l'apparence, des menus et raccourcis.
11. [ ] Quand la sauvegarde de départ est validée, quitter la salle Unbound et commencer la nouvelle partie en Bordeciel.

---

## Phase 6 — Validation ciblée en jeu et clôture

- [ ] Valider démarrage, chargement, sauvegarde/rechargement, changement de cellule, déplacements et combats.
- [ ] Contrôler les scénarios affectés par les suppressions / ajouts de mods.
- [ ] Vérifier **Estrus Unified** (scènes et sortie sans blocage, gestion des grossesses, restauration des morphs, compatibilité BeeingFemale NG).
- [ ] Vérifier **SLIF NG** et le cumul des demandes corporelles provenant de **BeeingFemale NG, Fill Her Up, Aroused BodyMorphs, MME et Estrus Unified**, uniquement pour les intégrations réellement présentes.
- [ ] Tester les interactions **Devious Devices / SexLab**, les animations créatures concernées et les éventuels dispositifs de récupération.
- [ ] Contrôler les journaux utiles et, si nécessaire, **inspecter** les sauvegardes avec ReSaver **sans nettoyage automatique**.
- [ ] Vérifier la persistance et la stabilité sur **plusieurs sessions de jeu**, plutôt que sur un simple chargement.
- [ ] Mettre à jour [CHANGELOG.md](CHANGELOG.md), les fiches de mods, les snapshots MO2 et la [documentation de validation](Docs/VALIDATION/08-TESTING.md).
- [ ] Marquer la nouvelle baseline **VALIDÉE / PLAYTHROUGH READY** seulement après ces tests.

### Critères de réussite

- **Nouvelle partie issue de `NEFARAM_Start`**, sans héritage des scripts des mods supprimés.
- **Eleanor recréée** avec succès via RaceMenu.
- **Maximum de paramètres MCM conservés**, et écarts résiduels répertoriés.
- **Aucun master manquant**, sorties Pandora/Synthesis cohérentes et contrôles principaux concluants.
- **Persistance vérifiée** après fermeture complète de Skyrim et plusieurs reprises de sauvegarde.
- Aucun défaut bloquant lié aux changements ciblés lors des premières sessions.

---

## Décisions actées et questions ouvertes

| Sujet | État |
|---|---|
| Repartir d'une **nouvelle partie** | **Décidé** |
| Utiliser `NEFARAM_Start` comme point de départ privilégié | **Décidé**, sous réserve d'une restauration MCM satisfaisante |
| Protéger `Eleanor_Start` et l'ancien profil MO2 | **Obligatoire** |
| Recréer Eleanor via preset RaceMenu JSON | **Prévu** |
| Évaluer MCM Memory avant modification | **Priorité n° 1**, restauration à éprouver |
| Supprimer Enslaved by the Thalmor, Unethical Alchemy, SexLab Approach | **Prévu**, dépendances à contrôler |
| Ajouter Unethical SpellCraft | **Prévu**, version et intégration à confirmer |
| Ajouter Estrus Unified 1.3 sans les anciens modules Estrus | **Décidé**, vérification des dépendants encore requise |
| OviBody / Curse of Life / compagnons Estrus | **Exclus / désactivés** |
| SLIF NG et coexistence des BodyMorphs | **Étude et validation à mener** |
| Remplacer Fill Her Up Baka par Crajjj Edition | **Non décidé** ; étude comparative requise |
| Oninus Lactis NG | **Facultatif**, décision à finaliser |
| Pandora | **À régénérer** |
| Synthesis | **À contrôler puis régénérer si nécessaire** |

---

## Règle de conduite

> **Sauvegarder → exporter les MCM → tester leur restauration → modifier sur un profil de travail → régénérer → charger `NEFARAM_Start` → restaurer → valider → partir en Bordeciel.**
>
> Les anciennes heures de test restent acquises. **Nous validons les différences, pas l'ensemble du modpack depuis zéro.**
