# 16 - Roadmap de finalisation NEFARAM-Rhiven 1.1

Cette fiche fixe l'ordre de travail jusqu'au lancement de la partie définitive.

**Avancement documentaire mis à jour le 25/10/2026 — cible : NEFARAM-Rhiven 1.1.**

**L'installation du socle actuellement retenu est terminée.** Les snapshots des deux panneaux MO2 ont été mis à jour dans [load-order](../load-order/README.md). Une copie complète de l'instance NEFARAM d'origine a permis les essais réversibles. L'instance stable a été remise en place sous `C:\JEUX\NEFARAM` ; l'instance expérimentale Community Shaders est conservée séparément sous `C:\JEUX\NEFARAM_CS`. Une dernière vague de **mods candidats** est maintenant étudiée avant le gel définitif ; aucun de ces candidats n'est considéré comme intégré tant que son audit et, si nécessaire, ses tests dédiés ne sont pas terminés.

La **migration technique 17.3.7 -> 17.3.8 est terminée et validée**. Les validations exclusivement liées au gameplay réel restent suivies dans la fiche de migration et la checklist ; elles ne remettent pas en cause la baseline technique 17.3.8.

Ordre de travail restant : **terminer la chaîne LOD xLODGen → TexGen → DynDOLOD pour Animal Mansion Reborn → effectuer les smoke tests AMR et Naked Defeat encore ouverts → décider d'une publication éventuelle du patch AMR après validation → gel fonctionnel → passage de Skyrim en français → traduction des mods → checklist pré-finale → départ via NEFARAM_Start → paramétrage des MCM → validation et jeu.**

**Étape KID / modesty Eleanor validée le 16/10/2026 :** audit de la collection personnelle terminé, couverture existante AND / OSL / SLA / BOOBIES contrôlée, complément `Eleanor Modesty KID - Rhiven` créé avec `Rhiven_Eleanor_Modesty_KID.ini`, et chargement confirmé dans le log Keyword Item Distributor sans erreur de parsing propre au fichier Rhiven. Les réactions réelles aux tenues restent volontairement à vérifier pendant la partie définitive.

Les phases 1 à 4 ci-dessous conservent l'historique et les contrôles détaillés. Leurs cases de tests non cochées restent à confirmer : **installation terminée ne signifie pas que tous les tests fonctionnels sont validés**. Elles ne constituent plus une liste de mods à installer.

Baseline actuelle : **NEFARAM 17.3.8**, profil MO2 **Eleanor Stable 17.3.8**.

> Important : la partie définitive doit démarrer depuis la sauvegarde fournie **NEFARAM_Start**, conformément à la baseline du dépôt, et non depuis le bouton vanilla `New Game`.

---

## Phase 0 - Règles de travail

- [ ] Installer et tester **un bloc logique à la fois**.
- [ ] **Avant toute désactivation/réactivation de mods pour un test MO2, créer un backup du panneau gauche et du panneau droit / load order des plugins.** Restaurer ou comparer après le test avant de poursuivre.
- [ ] Conserver une sauvegarde de test jetable pour les validations pré-finales.
- [ ] Ne pas considérer comme compatible un ancien mod uniquement parce qu'il fonctionnait sous l'ancien NEFARAM V16.
- [ ] Pour les anciens mods issus de V16, contrôler les dépendances modernes avant installation : runtime Skyrim, SKSE, Address Library, DLL éventuelles, SexLab, Papyrus, animations et frameworks associés.
- [ ] Ne pas remplacer un ancien mod qui fonctionne encore proprement uniquement parce qu'il est ancien.
- [ ] Après chaque bloc validé, mettre à jour la documentation du dépôt si nécessaire.
- [ ] Une fois la Phase 2 terminée : **gel fonctionnel du modpack**. Aucun nouvel ajout gameplay sauf correction nécessaire.

---

## Phase 1 - Dernières animations — décisions du 11/10/2026

- [x] **Gulan0 Female Random Idle v1.0 + v2.0** : installation, OAR et sélection par variante testées. **Non retenues dans la configuration active** : trois mods Gulan0 Idle / Settings conservés mais **DÉCOCHÉS** dans MO2. **Seamless Varied Feminine Idles** (déjà fourni par NEFARAM) reste privilégié pour Eleanor.
- [x] **Gulan0 Animations - Walk / Run / Sprinting Rework** : version **OAR Player Only** installée et animations marche/course/sprint confirmées dans l'Animation Log. Priorité utilisateur **1000002** conservée dans un mod dédié.
- [x] **Sprint Revised** : fichier féminin `mt_sprintforward.hkx` conservé.
- [x] **female_run_Update (août 2026)** : cinq HKX de course testés puis **retirés** après comparaison esthétique ; course originale Gulan0 conservée.
- [x] Sauvegarde et rangement des réglages OAR `user.json` dans des mods Rhiven.
- [ ] Surveillance en partie réelle des états spéciaux (armes, entraves, transitions de locomotion).

**Procédure détaillée et architecture :** [Guide ANIMATIONS / OAR](guides/ANIMATIONS/README.md).

Sources :
- https://www.nexusmods.com/skyrimspecialedition/mods/165916
- https://www.nexusmods.com/skyrimspecialedition/mods/185003
- https://www.nexusmods.com/skyrimspecialedition/mods/164743

---
 
### Éléments sortis des ajouts restants

- **Fancy Magecore** : installé ; validation visuelle définitive encore à faire.
- **Fitting Room** : installé en test comparatif avec Outfit Gallery ; décision définitive suivie dans la checklist 13.
- **Campfire 2026** : **écarté** après évaluation bénéfice/risque ; garder le socle Campfire NEFARAM existant. Ne pas le réintroduire comme installation planifiée.
- **Bandit Paradise 1.6.5** : **exclu** après audit, effort d'intégration et risques narratifs/Script/SexLab jugés disproportionnés.
- **Devious Carriages Redux 1.0.6** : installé avec patch CFTO et voix ; contrôle statique effectué, tests fonctionnels différés.
- **TDF Aroused Rape v3.2** : module Aroused Rape uniquement (pas l'ancien Sexy Idles) installé ; SSEEdit 90 records, 0 erreur ; tests en jeu différés.
- **SexLab Dangerous Nights 2 SE 2.6** : ajouté au bloc NSFW ; audit ESP/Papyrus/MCM réalisé, SSEEdit 147 records, 0 erreur ; contrôle du nettoyage des acteurs et tests in-game encore à effectuer. Réglages initiaux MCM consignés dans la checklist 13.

---

## Phase 2 - Bloc tatouages : installation terminée, contrôles à confirmer

**État au 13/10/2026 :** l'installation des mods prévus est terminée, conformément au point d'avancement de Fabien. Les audits et tests ci-dessous restent suivis séparément, sans les déclarer validés par cette seule annonce.

Ce bloc doit être traité comme **un ensemble cohérent**, pas comme une suite de mods indépendants.

### Ordre de référence du bloc

1. **Rape Tattoos Continued 2.0.3**
2. **Fade Tattoos Continued 2.1.0**
3. **No Overlap for Rape Tattoo 1.00**
4. **Remove Your Tats SE**
5. **Zaki Tattoo Pack LE/SE 1.2.1**
6. **Alpia Scribbles SlaveTats Pack 08.2026**

Sources :

- https://www.loverslab.com/files/file/27999-rape-tattoos-continued/
- https://www.loverslab.com/files/file/27994-fade-tattoos-continued/
- https://www.loverslab.com/files/file/45084-no-overlap-for-rape-tattoo/
- https://www.loverslab.com/files/file/31435-remove-your-tats-se/
- https://www.loverslab.com/files/file/26261-zaki-tattoo-pack-lese/
- https://www.loverslab.com/files/file/30951-alpia-scribbles-slavetats-pack/

### 2.1 Compatibilité générale

- [ ] Vérifier les versions requises de SlaveTats / SexLab / JContainers / PapyrusUtil et autres dépendances.
- [ ] Comparer avec le fonctionnement connu sous l'ancien NEFARAM V16.
- [ ] Vérifier que les mods ne reposent pas sur une API supprimée ou renommée.
- [ ] Rechercher les éventuels patches modernes nécessaires.

### 2.2 Audit JSON

Pour chaque pack contenant des JSON :

- [ ] Valider la syntaxe JSON.
- [ ] Vérifier les noms de packs / sections.
- [ ] Repérer les doublons d'entrées.
- [ ] Repérer les IDs / noms de tatouages identiques.
- [ ] Vérifier les chemins des textures.
- [ ] Vérifier que toutes les textures référencées existent.
- [ ] Rechercher les entrées orphelines.
- [ ] Vérifier les catégories / zones corporelles.
- [ ] Repérer les anciennes conventions LE éventuellement problématiques.
- [ ] Vérifier les caractères spéciaux / encodage.
- [ ] Corriger uniquement via un override Rhiven lorsque c'est possible.

### 2.3 Cohérence fonctionnelle du bloc

- [ ] Vérifier l'application d'un tatouage par SlaveTats.
- [ ] Vérifier l'application via Rape Tattoos Continued.
- [ ] Vérifier le fade temporel.
- [ ] Vérifier No Overlap sur plusieurs applications successives.
- [ ] Vérifier Remove Your Tats.
- [ ] Vérifier que les packs Zaki et Alpia restent sélectionnables et correctement catégorisés.
- [ ] Tester plusieurs overlays simultanés.
- [ ] Contrôler corps / visage / mains / pieds selon les packs.
- [ ] Tester sauvegarde -> sortie jeu -> rechargement.
- [ ] Vérifier l'absence de disparition ou duplication d'overlays.

### 2.4 Validation du bloc

- [ ] Aucun JSON invalide.
- [ ] Aucun chemin texture mort connu.
- [ ] Aucun conflit logique évident entre Rape / Fade / No Overlap / Remove.
- [ ] Test en jeu validé sur sauvegarde jetable.
- [ ] Documenter les corrections Rhiven éventuelles.

---

## Phase 3 - Gel fonctionnel du modpack

**État au 13/10/2026 :** la liste d'installation est terminée et les snapshots sont à jour. Préserver cette base pendant la finalisation ; les corrections nécessaires et les changements retenus lors de l'étude graphique restent possibles sur la copie de travail.

- [ ] Plus aucun mod gameplay ajouté sans nécessité réelle.
- [x] Mettre à jour `03-MODS-ADDED.md` au fil des candidats retenus ; dernière mise à jour : 24/10/2026.
- [ ] Mettre à jour `04-MODS-REMOVED.md` pour les candidats rejetés / retirés si pertinent.
- [x] Mettre à jour le snapshot MO2 gauche : [liste Rhiven actuelle](../load-order/NEFARAM-RHIVEN-MODDED-MO2-LEFT.md).
- [x] Mettre à jour le snapshot plugins / load order : [liste Rhiven actuelle](../load-order/NEFARAM-RHIVEN-MODDED-MO2-RIGHT.md).
- [x] Terminer l'installation de tous les mods prévus.
- [x] Effectuer une copie intégrale de l'instance NEFARAM avant les essais graphiques et conserver le retour arrière.
- [ ] Vérifier la copie avant modification : profil MO2, chemins des exécutables et des sorties, lancement et sauvegardes de test doivent pointer vers l'instance de travail.
- [x] Conserver l'instance stable d'origine comme référence de retour arrière ; la remettre sous `C:\JEUX\NEFARAM` après le test CS.
- [ ] Effectuer un premier test stabilité global avant le chantier graphique.

---

## Phase 4 - UI / HUD Eleanor : intégration installée, validation à confirmer

**État au 14/10/2026 :** Vel'dun UI principal et Patches **1.0.6** conservés (la 1.0.7 du principal avait perturbé ESC), Vel'dun UI Overhauls installé, Modern Wait Menu et habillage Vel'dun visibles en jeu. Bestiaire Vel'dun et icônes Dragonborn colorées également observés ; validation fonctionnelle exhaustive toujours à faire. Voir le [guide HUD](guides/HUD/README.md).

Les éventuels correctifs techniques se font sur la copie de travail, sans reconstruire précipitamment l'interface NEFARAM. Vérifier la compatibilité des composants UI ; **reporter les réglages détaillés des widgets et les préférences HUD à la session de configuration des MCM (phase 8)**. Leur ordre précis dans cette session reste à déterminer.

- [ ] Confirmer l'audit de **Vel'Dun UI** déjà installé, en vérifiant les versions de SkyUI et MCM Helper de NEFARAM, ainsi que les options FOMOD réellement utiles.
- [ ] Contrôler la cohabitation avec Dear Diary Dark Mode, Wheeler, TrueHUD, les widgets et le système de menus actuel.
- [x] Réactiver après comparaison les reskins Dragonborn souhaités (Wheeler, icônes de catégories SkyUI et STB Active Effects) ; les icônes colorées sont visibles en jeu. Le test d'effets actifs STB reste différé.
- [ ] Valider le bon fonctionnement technique (affichage 3D, carte / inventaire, HUD de base, hotkeys essentielles et stabilité), sans figer la disposition des widgets.
- [x] Identifier l'emplacement du patch Modern Wait Menu dans **Vel'dun UI Overhauls** (et non dans Vel'dun UI Patches), sélectionner Modern Wait Menu et le reskin Bestiary 16:9, conserver Quest Journal sur Skip (QJO non installé).
- [ ] Valider une attente complète, ESC, Favoris et Bestiaire avec contenu ; confirmer STB Active Effects lorsque le PJ a des effets.
- [ ] Préparer la traduction externe `Translation.json` d'Outfit Gallery 1.0.15 dans la phase FR (format à vérifier). Conserver l'automatisation des tenues des compagnons désactivée.
- [x] **Phoenix Katana** est désormais installé avec son plugin de personnalisation Eleanor ; validation finale en jeu/traduction reste suivie dans le contrôle pré-playthrough.
- [ ] Suivre le **chantier HUD détaillé** dans [guides/HUD/README.md](guides/HUD/README.md) ; ne pas dupliquer ici ses choix et ses tests.

Source : https://www.nexusmods.com/skyrimspecialedition/mods/176230

---

## Phase 5 - Étude graphique finale — choix effectué le 14/10/2026

**Décision graphique : conserver l'architecture ENB issue de la configuration validée sous 17.3.7 et maintenue après migration 17.3.8, avec Silent Horizons 2 complété par ReShade 6.8.0 et le preset Sswaye LUT13.** Community Shaders a été essayé sur une instance séparée, puis écarté au profit du rendu préféré et du retour à la configuration fonctionnelle d'origine.

### 5.1 Comparatif réalisé

- [x] Préserver la base originale et effectuer les essais dans une copie réversible.
- [x] Tester Silent Horizons 2 (SH2) sur la machine réelle : RTX 4070 12 Go.
- [x] Vérifier des extérieurs, intérieurs, paysages enneigés et le rendu d'eau.
- [x] Tester Community Shaders 1.9.1 + Effects 11 + NAT Effect 11 sur un profil expérimental.
- [x] Vérifier les dépendances Water for ENB : `DynDOLOD.esm` et `_NEFARAM_____MAIN_____.esp` utilisent des masters / références de l'ancienne chaîne d'eau. Water for ENB a été conservé pendant l'essai CS ; Water for CS n'a pas été retenu.
- [x] Comparer les deux solutions en jeu : tonalité extérieure CS appréciée, mais rendu SH2 globalement préféré. Le zoom caméra fonctionnait sur la base d'origine / SH2 et non dans la configuration CS expérimentale ; cause exacte non isolée. SkyParkour nécessitait simplement son activation MCM sur la partie de test.
- [x] Écarter CS comme configuration finale **sans attribuer automatiquement tous les problèmes observés à son moteur**.
- [x] Rétablir l'instance NEFARAM d'origine sous `C:\JEUX\NEFARAM` et conserver l'essai CS sous `C:\JEUX\NEFARAM_CS`.

**Références :**
- [Silent Horizons 2](https://www.nexusmods.com/skyrimspecialedition/mods/99398)
- [Guide NEFARAM ENB → Community Shaders / NAT Effect 11](guides/NEFARAM_Guide_ENB_vers_Community_Shaders_NAT_Effect_11.md) — documentation consultée pendant les essais ; procédure historique issue de NEFARAM 17.2.1, non retenue pour la configuration finale.

### 5.2 Configuration retenue — Silent Horizons 2

- [x] Restaurer les fichiers du preset SH2 personnalisé depuis le slot 3 sauvegardé : `enbseries/`, `enbseries.ini`, `enblocal.ini`.
- [x] Conserver les binaires ENB de la base d'origine (`d3d11.dll`, `d3dcompiler_46e.dll`), sans reconstruire les plugins ou les sorties DynDOLOD.
- [x] Contrôler les valeurs de parallaxe du preset SH2.
- [x] Confirmer dans l'interface ENB : **Interior – Exposure (in EVs) = +0.50**.
- [x] Valider le lancement en jeu, le retour du zoom caméra et le rendu extérieur. Relevé ponctuel d'environ **74,9 FPS** dans un essai ; ne constitue pas un benchmark complet.
- [ ] Confirmer la stabilité sur plusieurs lieux / conditions et avec les fonctions essentielles du modpack.

### 5.3 ReShade — finition graphique

- [x] Installer **ReShade 6.8.0 Full Add-on Support** à côté d'ENB, via `dxgi.dll`, sans remplacer `d3d11.dll`.
- [x] Installer les ressources Sswaye dans `reshade-shaders/Shaders` et `reshade-shaders/Textures`, puis configurer leurs chemins dans ReShade.
- [x] Tester les presets **Sswaye Normal** et **Sswaye LUT13** sur une scène extérieure comparable.
- [x] **Retenir Sswaye LUT13** : rendu préféré ; le preset Normal est jugé trop coloré, LUT21 trop bleu.
- [x] Vérifier que le preset LUT13 active bien `DPX.fx`, `Clarity.fx` et `LUT13.fx` et que les effets sont détectés.
- [ ] Vérifier les FPS / frametimes sur plusieurs scènes, la météo et les intérieurs avec **SH2 + ReShade LUT13**.
- [ ] Confirmer que le preset choisi persiste après redémarrage ; sauvegarder une copie définitive des configurations ENB et ReShade.
- [ ] Finaliser les snapshots MO2 et documenter les fichiers graphiques retenus, si leur état diffère des listes de référence.

### Décision et gel graphique

**Choix graphique arrêté le 14/10/2026 : Silent Horizons 2 + ReShade / Sswaye LUT13.** Ne pas reprendre la migration Community Shaders sans nouveau besoin explicite.

- [x] Choisir la solution sur le rendu, les essais en jeu et le retour aux fonctionnalités connues.
- [ ] **Prononcer le gel graphique définitif** après validation de la persistance et des tests de stabilité, sans modifications majeures supplémentaires.

---

### Complément au gel des mods — signalisation française (14/10/2026)

- [x] Désactiver l'ancien trio Road Signs Overhaul 2.0 / Questionable Clutter Remover BOS / Blended Roads BOS (conservé dans MO2 en retour arrière) après disparition du panneau supplémentaire mal placé près de Rivebois lors du diagnostic.
- [x] Installer `Point The Way - Rhiven` avec `My Road Signs are Beautiful - French` et valider visuellement plusieurs panneaux en français près de Rivebois, en météo pluvieuse.
- [ ] Vérifier le placement / les éventuelles incohérences LOD à distance et confirmer l'ordre exact des plugins depuis un nouvel export MO2 ; **aucune régénération DynDOLOD n'a été effectuée**.
- [ ] Actualiser les deux snapshots MO2 Rhiven après export de l'état courant ; conserver les snapshots de la baseline originale inchangés.

---

## Phase 5 bis - Étude des derniers candidats avant gel définitif

**État au 25/10/2026 :** cette phase reste ouverte avant la francisation finale. Les blocs graphismes et QoL sont retenus ; Horde a été rejeté au profit de NFF ; LL Integration 0.8 a passé son essai contrôlé ; SexLab Approach Redux 3.62 et Unethical Alchemy 1.0.0 sont techniquement intégrés et passent désormais en validation gameplay. **Naked Defeat 6.50 reste techniquement validé avec smoke tests in-game à terminer. Animal Mansion Reborn 1.8 a franchi l'audit, la création du patch Rhiven, la validation xEdit et la régénération Synthesis ; la chaîne LOD est en cours et les smoke tests AMR restent à faire.**

### Procédure standard d'étude

Pour chaque mod candidat :

1. **Lire la description complète et les fichiers disponibles** ; pour LoversLab, utiliser une fiche locale propre basée sur la description copiée par Fabien afin de conserver une référence stable.
2. **Lister les prérequis exacts** : Skyrim runtime, SKSE, Address Library, DLL, frameworks, SexLab, Papyrus, UI, animation, BodySlide, OAR/Pandora, etc.
3. **Comparer avec la baseline réelle** `NEFARAM 17.3.8 / Eleanor Stable 17.3.8` et les snapshots MO2 gauche/droite.
4. **Identifier les doublons fonctionnels** avec les mods déjà présents.
5. **Auditer les dépendances et patches existants** avant tout remplacement d'un framework déjà intégré.
6. **Classer le risque** :
   - **Faible** : ajout isolé, sans remplacement structurel ;
   - **Moyen** : chevauchement fonctionnel, nouveaux plugins/scripts ou réglages à harmoniser ;
   - **Élevé** : remplacement de framework, dépendances transversales, animation/LOD/BodySlide ou impacts sur de nombreux patches.
7. **Décider avant installation** :
   - `CANDIDAT` ;
   - `À TESTER` ;
   - `RETENU` ;
   - `REJETÉ` ;
   - `REPORTÉ APRÈS PLAYTHROUGH`.
8. Pour les mods classés **À TESTER**, utiliser un profil/copie jetable ; ne jamais faire le premier essai sur le futur save définitif.
9. Si le mod est retenu : documenter installation, FOMOD, ordre MO2, plugins, patches, traductions, tests et retour arrière.
10. Après validation : mettre à jour cette roadmap, `03-MODS-ADDED.md`, `04-MODS-REMOVED.md`, `08-TESTING.md` et les snapshots si l'état final du build change.

### Ordre d'étude retenu

#### 5 bis.1 - Graphismes : MESH2 + ENB Dynamic Cubemaps

**Verdict au 23/10/2026 : bloc RETENU et validé en jeu.**

- [x] Étudier **MESH2 ENB - Max's Edited Silent Horizons 2 1.2.1** comme évolution de Silent Horizons 2 1.13.
- [x] Étudier **ENB Dynamic Cubemaps 1.01** dans le même chantier.
- [x] Travailler sur une copie réversible de la configuration ENB actuelle. **Rollback confirmé : ENB and ReShade Manager v5.1.1, Set 3 = `SH2 + ReShade Sswaye LUT13` ; Set 4 = `SH2 + ReShade LUT13 + MESH2`.**
- [x] MESH2 n'a **pas** été installé en overwrite brut : les helpers/DOF additionnels ont été ajoutés et les réglages utiles ont été fusionnés sélectivement dans la base SH2 1.13 afin de préserver les paramètres modernes de SH2 (LOD Shadow, weather, fog, extender, etc.).
- [x] Réglages MESH2 repris de façon ciblée : yeux, SSS peau, AO/SSIL, IBL, Complex Grass, Complex Material, Dynamic Cubemap et une partie du tuning eau.
- [x] Conserver dans le Slot 4 les valeurs structurelles SH2 1.13 : `EnableDepthOfField=false`, `EnableLens=false`, `EnablePrepass=false`, `EnableLODShadow=true`, `EnableMultipleWeathers=true`.
- [x] Le fichier généré `Shaders/Features/TerrainHelper.ini` a été rangé dans un mod MO2 dédié **`MESH2 - TerrainHelper Config`**, à activer uniquement lorsque le Slot 4 MESH2 est utilisé.
- [x] Comparer visuellement MESH2 avec **Silent Horizons 2 + ReShade Sswaye LUT13** sur des scènes identiques. Après plusieurs tests, le rendu MESH2 est préféré.
- [x] Mesurer l'impact FPS sur scène comparable : relevé indicatif d'environ **63,1 FPS avec MESH2** contre **70,7 FPS avec SH2** sur le point de comparaison utilisé ; coût accepté après tests complémentaires.
- [x] Contrôler les réflexions sur yeux, métaux, armures, eau et surfaces brillantes : aucun artefact notable observé après réglage.
- [x] Installer **ENB Dynamic Cubemaps 1.01** après `Quality CubeMaps - HD Cube Maps` dans les Late Loaders afin qu'il gagne les conflits globaux de cubemaps.
- [x] Conserver `NEFARAM Patches` gagnant sur `chrome_e.dds`, `glacierice_e.dds` et `ore_obsidian_e.dds`. Les deux premiers sont des DDS très légers ; `ore_obsidian_e.dds` est une vraie cubemap statique 64x64 (~25 Ko) conservée comme exception volontaire NEFARAM.
- [x] Tester ENB Dynamic Cubemaps en jeu : pas d'yeux anormaux, pas de matériaux aberrants, pas de reflet visuellement cassé.
- [x] Vérifier la persistance des réglages et le retour arrière via le Set 3.
- [x] Verdict final : **RETENU — MESH2 intégré sélectivement à SH2 1.13 + ENB Dynamic Cubemaps validé. Risque résiduel faible, coût GPU modéré et accepté.**

#### 5 bis.2 - QoL / interface légère

**Needs Widget AIO — couche d'affichage finale**

- [x] Retenir **Needs Widget AIO** comme remplacement final de `Widget Addon - Keep It Clean - Bathing in Skyrim`.
- [x] Confirmer la présence du preset fourni **Vel'Dun**, son activation et son fonctionnement en jeu.
- [x] Confirmer la séparation des responsabilités : **Needs Widget AIO = affichage uniquement / SunHelm = besoins / BiSR = hygiène**.
- [ ] Confirmer que **`Widget Addon - Keep It Clean - Bathing in Skyrim - Rhiven`** reste désactivé / rollback only et que `WA_BathWidget.esp` reste inactif.
- [ ] Actualiser les snapshots MO2 gauche/droite après cette vérification ; les exports actuels montrent encore l'ancien Widget Addon.
- [ ] Vérifier pendant la partie définitive l'absence de doublon d'affichage de besoins ou d'hygiène.
- [ ] Reporter l'harmonisation complète avec SunHelm, STB Widgets et les autres éléments HUD à la **méga-session UI / MCM** de la partie définitive : positionnement, fading, opacité, doublons et priorités.
- [x] Verdict final : **RETENU ET VALIDÉ EN JEU — preset Vel'Dun, couche d'affichage uniquement.**

**Dino's Easy Quest Fix**

- [x] Vérifier les prérequis et la compatibilité avec le runtime 1.6.1170 : SKSE64, Address Library et SkyUI déjà présents dans la baseline.
- [x] Installer dans `43 - Added Mods SFW` sans conflit de fichiers MO2.
- [x] Confirmer le plugin `DinosEasyQuestFix.esp` actif et flaggé ESL.
- [x] Vérifier la présence des sources fournies par l'auteur : sources Papyrus et sources complètes du composant SKSE/native incluses dans l'archive.
- [x] Valider le MCM en jeu : les quêtes actives sont correctement listées avec leur stage courant.
- [x] Valider la vue détaillée sur une quête réelle : affichage du stage courant, texte associé, objectif actif, prochain stage disponible et commande `Advance to next stage`.
- [x] Confirmer que le mod sert d'outil d'assistance et de diagnostic rapide et ne remplace pas l'analyse via `sqs`, `sqv`, xEdit ou Papyrus lorsqu'une quête est réellement cassée.
- [x] Règle d'usage retenue : sauvegarde manuelle avant tout avancement forcé ; utiliser `Advance to next stage` uniquement lorsqu'un blocage est identifié, afin d'éviter de sauter récompenses, scripts ou branches nécessaires.
- [x] Verdict final : **RETENU — faible risque, excellente valeur QoL / diagnostic, fonctionnement validé en jeu.**

**Item Vault - Plugin Explorer**

- [x] Comparer précisément avec **AddItemMenu** et **Modex 3.0.2** déjà installés.
- [x] Installer Item Vault sans ESP et sans conflit de fichiers MO2 ; intégration purement SKSE + assets.
- [x] Vérifier l'ouverture et l'indexation sur la très grande load order Rhiven : ouverture instantanée observée avec environ **46 831 items / 466 plugins**.
- [x] Vérifier la recherche globale et par plugin sur un cas réel : **Phoenix Katana - Eleanor** retrouvé en quelques secondes via `Rhiven_Eleanor_Katana.esp`.
- [x] Confirmer les fonctions supplémentaires utiles : navigation items/plugins, NPC, sorts, objets, téléportation, inventaires, kits, recherche, actions directes et preview 3D.
- [x] Comparaison d'usage retenue : **AddItemMenu** conservé comme outil rapide et familier ; **Item Vault** devient l'explorateur complet.
- [x] **Modex 3.0.2 - Rhiven** et **Modex - 3.0.2 Patch - Rhiven** désactivés en test de remplacement ; aucun master manquant détecté après désactivation.
- [x] Ne pas supprimer Modex immédiatement : le conserver temporairement en rollback et confirmer son inutilité pendant les premières heures de la partie finale.
- [x] Verdict final : **RETENU — faible risque, excellente valeur QoL, performances d'indexation très satisfaisantes. Modex devient redondant dans l'usage actuel.**

#### 5 bis.3 - Framework followers : Horde contre NFF

**Verdict au 23/10/2026 : HORDE REJETÉ / NFF CONSERVÉ.**

- [x] Installer et auditer **Horde 3.0.1** comme remplacement potentiel de Nether's Follower Framework : archive propre, aucun conflit MO2, `Horde.esp` ESL-flagged.
- [x] Confirmer que Horde couvre les fonctions principales recherchées : gestion de groupe, follow/wait/summon/dismiss, homes, sandbox, équipements, commandes et jusqu'à 20 followers.
- [x] Tester la désactivation contrôlée du stack NFF.
- [x] Le test de retrait a révélé que `nwsFollowerFramework.esp` est master direct de nombreux plugins générés / NEFARAM, notamment plusieurs `Synthesis_*.esp`, `_NEFARAM_PEGI16_DeviousFollower.esp`, `_NEFARAM_PEGI18_Babo.esp`, `_NEFARAM_____MAIN_____.esp` et `SDA NFF Patch.esp`.
- [x] Conclusion : remplacer NFF imposerait une régénération Synthesis et une chirurgie sur plusieurs patches NEFARAM, sans bénéfice proportionné pour un gameplay où les followers sont rarement utilisés.
- [x] Réactiver NFF et restaurer le load order d'origine après l'essai ; contrôle qualité effectué à partir du snapshot du panneau droit.
- [x] **Horde a été supprimé du build.**
- [x] **Nether's Follower Framework 2.8.5 reste la solution retenue.**
- [x] `Outfit Gallery - Visual Outfit Manager 1.0.16` reste la solution existante pour les tenues ; aucun framework supplémentaire de type PrismaUI n'est ajouté.
- [x] Nouvelle règle de sécurité issue de ce test : **backup panneau gauche + panneau droit/load order avant toute désactivation/réactivation de mods pour essai**.
- [x] Verdict final : **REJETÉ — intérêt fonctionnel réel, mais coût d'intégration disproportionné et dépendances transversales trop nombreuses.**

#### 5 bis.4 - LoversLab : intégrations légères et sociales

Les fiches LoversLab sont préparées à partir des descriptions copiées par Fabien avant décision.

- [x] **SexLab Approach Redux 3.62** — **TECHNIQUEMENT VALIDÉ / GAMEPLAY À TESTER**. Installé avec la branche OAR ; seul conflit MO2 notable : ancien `SLAppAutoMCM.json` dans `SKSE Output`. Le JSON vide 3.62 est conservé comme baseline propre ; MCM complet, `OnlyinTown`, `Sex CoolTime` et toggles SLHH/Babo/FillHerUp/Survival/DDI présents. xEdit : 5 546 records, un warning VMAD connu dans `SLApproachAskForSex2Quest` (aliases 0/2/3 orphelins dans le fragment généré, section Aliases actuelle vide). Aucun correctif invasif : la branche AskForSex2 sera testée in-game. Le preset `NEFARAM - 263` reste une **référence de tuning** ; fréquence/probabilité Approach volontairement réduite pour Eleanor. Voir [SEXLAB-APPROACH-REDUX-INTEGRATION.md](guides/SEXLAB-APPROACH-REDUX-INTEGRATION.md).
- [x] **Unethical Alchemy 1.0.0** — **TECHNIQUEMENT CORRIGÉ / GAMEPLAY À TESTER**. Installé sans conflit MO2 ; archive légère (ESP + scripts/source + sons). xEdit a trouvé une référence AI-package orpheline sur `Agryn Gaering` (`xx002436`, introuvable). Création de `Unethical Alchemy - Rhiven Fix.esp`, chargé après le mod principal, supprimant uniquement cette entrée morte et conservant les 7 packages valides ; **Check for Errors du fix : 0 erreur / 2 records**. Reste à tester Heartwood Mill, dialogues/training, Joy, interactions Apothecary et comportement de l'abortifacient. L'intégration grossesse documentée vise Hentai Pregnancy ; sous Rhiven/Beeing Female NG, traiter l'abortifacient comme RP-only tant qu'une compatibilité BFNG n'est pas démontrée. Voir [UNETHICAL-ALCHEMY-1.0.0-INTEGRATION.md](guides/UNETHICAL-ALCHEMY-1.0.0-INTEGRATION.md).
- [x] **SLSF Fame Comments Reloaded 1.3 SE** — fiche créée : [SLSF-FAME-COMMENTS-RELOADED-INTEGRATION.md](guides/SLSF-FAME-COMMENTS-RELOADED-INTEGRATION.md). Le mod est déjà actif dans la baseline avec `FameCommentsReloaded.esp` et `SLSF Comments Voice`; travail restant : confirmer l'archive 1.3, documenter/tuner le MCM, contrôler les Fame Events et préparer la coexistence avec Public Whore Comments / SexLab Approach.
- [x] **Public Whore Comments 1.7** — fiche d'intégration créée : [PUBLIC-WHORE-COMMENTS-INTEGRATION.md](guides/PUBLIC-WHORE-COMMENTS-INTEGRATION.md). Public Whore et FameComments sont déjà présents ; audit restant : compatibilité réelle avec SLO/OSL Aroused NG et test de densité PWC + SLSF Fame Comments.
- [ ] Décider l'ordre d'intégration des mods sociaux uniquement après comparaison de leurs hooks, dialogues et fréquence d'événements.
- [ ] Verdict global du bloc : **EN COURS** — Approach 3.62 et Unethical Alchemy sont techniquement intégrés ; SLSF Fame Comments est déjà actif ; Public Whore Comments reste à évaluer/tuner avec les autres systèmes sociaux avant fermeture du bloc.

#### 5 bis.5 - LoversLab : gros contenus / systèmes lourds

**Animal Mansion Reborn 1.8 — intégration technique terminée, validation finale en cours**

- [x] Audit complet effectué sur la baseline actuelle **NEFARAM-Rhiven 17.3.8** ; plugin principal : **30 175 records / 0 erreur xEdit**.
- [x] Patch COTN Falkreath contrôlé : **0 erreur** ; conservé actif pour ses repositionnements AMR propres à la géométrie COTN.
- [x] Patch `AMR The Great Town of Shor's Stone Patch.esp` conservé actif dans la pile AMR finale testée ; ses records sensibles NAVI / navmesh ont été audités dans cette pile et restent à confirmer par les smoke tests gameplay.
- [x] Stratégie de load order confirmée : laisser Lux, NEFARAM et Synthesis gagner lorsqu'ils portent déjà le bon état final, sans duplication inutile.
- [x] Créer `Animal Mansion Reborn - Rhiven Patch.esp` comme couche minimale et réversible.
- [x] Construire et valider le patch Rhiven avec le patch Shor's Stone actif, comme complément minimal : préserver le correctif MNC/Husky, fusionner les ajouts de dialogue AMR et appliquer les ajustements CELL strictement nécessaires.
- [x] Valider le patch Rhiven dans xEdit : **21 records / 0 erreur**.
- [x] Régénérer Synthesis après placement final d'AMR et du patch Rhiven.
- [x] Retenir le workflow LOD complet **xLODGen → TexGen → DynDOLOD**.
- [ ] Terminer xLODGen — **génération en cours**.
- [ ] Exécuter TexGen puis DynDOLOD et contrôler les outputs générés.
- [ ] Tester uniquement sur profil clone / sauvegarde jetable.
- [ ] Smoke tests minimum : démarrage de quête, mansion, Falkreath, Shor's Stone, scènes créatures, navigation NPC/follower, portes et transitions de cellules, sauvegarde/rechargement, absence de CTD reproductible.
- [ ] Si les smoke tests passent : décider de la publication du patch et de la note d'intégration, puis annoncer éventuellement la disponibilité sur le Discord NEFARAM avec demande de retours communautaires.
- [ ] Statut actuel : **TECHNIQUEMENT INTÉGRÉ / PATCH XEDIT VALIDÉ / LOD EN COURS / GAMEPLAY NON ENCORE VALIDÉ**.

Guide détaillé : [ANIMAL-MANSION-INTEGRATION.md](guides/ANIMAL-MANSION-INTEGRATION.md).

**RennasRanch 0.3.0**

- [ ] Utiliser la fiche d'intégration déjà créée.
- [ ] Reprendre l'audit sur la baseline 17.3.8 stable.
- [ ] Vérifier worldspace, Falkreath, BodySlide, animations, DD, overlays, LOD et scripts.
- [ ] Installer uniquement sur profil clone après validation documentaire.
- [ ] Verdict initial : **À TESTER PLUS TARD — risque élevé / contenu conséquent**.

**Naked Defeat AE/SE**

- [x] Installer et auditer **Naked Defeat 6.50** sur le profil clone `Eleanor 17.3.8 - Naked Defeat`, après backup des panneaux gauche et droit.
- [x] Auditer le plugin principal : 798 records ; les erreurs utiles ont été classées entre défauts réels et résidus anciens / sous-systèmes abandonnés.
- [x] Créer `Naked Defeat - Rhiven Fix.esp` avec seulement quatre overrides ciblés : deux wrist chains et deux armes ; **Check for Errors : 0 erreur / 5 records**.
- [x] Identifier la branche **Civilian Rape** comme incomplète dans 6.50 : propriété `qst2` active vers une quête absente. Décision : `IndecencyRapeProb = 0` dans le MCM, sans reconstruction artificielle de la quête.
- [x] Installer et valider `Acheron - Naked Defeat Bridge.esp` : 3 records, **0 erreur xEdit** ; architecture retenue **Acheron → Bridge → Naked Defeat**.
- [x] Auditer les extras OAR : **Bowed Animations - fixed** retenu ; **Crawl Animations V2** conservé décoché car Bowed écrase directement les mêmes fichiers OAR.
- [x] Auditer Yamete Kudasai : chevauchement élevé avec les conséquences Acheron/Naked Defeat et événements YAML concurrents. Décision : désactiver le **mod MO2 complet YameteKudasai** pendant le smoke test.
- [x] Auditer **Practical Defeat Reanimated** : chevauchement maximal avec Naked Defeat. Décision : désactiver Practical Defeat + voicepack pendant le smoke test ; retrait définitif conditionné à la validation gameplay.
- [x] Conserver `Acheron - Simple Recover` et `Acheron - Diary of Mine Extension` actifs ; ils ne remplacent pas la chaîne principale Naked Defeat.
- [ ] Relancer Pandora après désactivation de Yamete Kudasai.
- [ ] Smoke test : plusieurs défaites, dont humanoïde, créature et follower ; contrôler fin de scène, stripping/vol éventuel, récupération et absence de blocage bleedout.
- [ ] Vérifier explicitement la sortie de l'état Acheron defeated / bleedout, le retour des contrôles et la libération correcte des assaillants.
- [ ] Vérifier une répétition de plusieurs événements dans la même session puis save / exit / reload.
- [ ] Si le smoke test passe : considérer **Practical Defeat remplacé** et conserver Yamete Kudasai désactivé par défaut dans le build Rhiven.
- [x] Documentation détaillée : [NAKED-DEFEAT-INTEGRATION.md](guides/NAKED-DEFEAT-INTEGRATION.md).
- [ ] Verdict actuel : **TECHNIQUEMENT VALIDÉ / TESTS IN-GAME EN COURS**.

#### 5 bis.6 - Outils de travail hors runtime

Ces outils ne sont pas des composants du modpack actif et peuvent être évalués indépendamment.

**ReSaver++**

- [ ] Identifier précisément la version / provenance / différences avec ReSaver/FallrimTools.
- [ ] Vérifier formats de sauvegarde supportés et fonctions de nettoyage/diagnostic.
- [ ] Ne jamais effectuer de nettoyage automatique sur une sauvegarde importante sans copie préalable.
- [ ] Statut : **À ÉTUDIER**.

**Skyrim PEX to PSC Decompiler**

- [ ] Installer/tester comme outil externe de diagnostic Papyrus.
- [ ] Vérifier qualité de décompilation sur quelques scripts connus.
- [ ] Conserver les sources décompilées uniquement comme aide d'analyse, jamais comme preuve absolue du code source original.
- [ ] Statut : **OUTIL RECOMMANDÉ À TESTER**.

**LL Integration 0.8**

- [x] Fiche technique créée : [LL-INTEGRATION-0.8-TECHNICAL-REVIEW.md](guides/LL-INTEGRATION-0.8-TECHNICAL-REVIEW.md).
- [x] Classé comme **outil externe de workflow navigateur ↔ bridge local ↔ MO2**, sans impact direct sur le runtime Skyrim.
- [x] Auditer le dépôt officiel, la politique de confidentialité, les permissions Firefox et le stockage des cookies avant installation. Audit source effectué sur `tricktricktrick/LL-Integration` : cookies LoversLab filtrés côté Firefox puis stockés localement en JSON non chiffré ; permissions et stockage documentés ; dépôt source-available.
- [x] Tester **Firefox + installateur MO2 normal**, sans toolbar expérimentale : installation réussie, entrée `Tools > LL Integration` visible dans MO2.
- [x] Politique retenue : mode d'update **Download only** / installation manuelle ; ne jamais remplacer automatiquement un mod Rhiven.
- [x] Détection active validée : bridge natif `C:\Users\Rhiven\AppData\Local\LLIntegration\native-app`, plugin MO2 `C:\JEUX\NEFARAM\plugins\ll_integration`, cible active `C:\JEUX\NEFARAM`, Downloads `D:\SKYRIM SE - Downloads`, cookies LoversLab exportés vers le stockage local JSON.
- [x] Capture navigateur validée depuis **LoversLab** puis depuis une source externe **SubscribeStar/CloudFront** : les archives ont été déposées correctement dans MO2 Downloads. **Statut : RETENU comme outil de maintenance externe**, avec risque runtime Skyrim nul et règles de prudence sur cookies/métadonnées.
- [ ] **Voice Finder et update-check approfondis restent optionnels à valider plus tard** ; ils ne bloquent pas l'adoption du workflow capture/source actuel.

### Critère de fermeture de la phase 5 bis

Ordre de fermeture mis à jour au 25/10/2026 :

1. **Terminer la chaîne LOD d'Animal Mansion Reborn** : xLODGen en cours, puis TexGen et DynDOLOD.
2. **Effectuer les smoke tests AMR** et ne déclarer l'intégration gameplay validée qu'après réussite reproductible.
3. **Terminer les tests in-game de Naked Defeat** et prononcer le verdict final sur le remplacement de Practical Defeat / Yamete Kudasai.
4. Donner à chaque autre candidat restant un verdict explicite : **retenu, rejeté ou reporté**.
5. Ne publier / annoncer le patch AMR qu'après validation finale ou avec un statut de test explicitement indiqué.
4. **Geler fonctionnellement la load order.**
5. Passer à la **Phase 6 — traduction FR**.

Les mods retenus doivent être intégrés et documentés **avant** le passage complet en français afin d'éviter de traduire deux fois une load order encore mouvante.

---

## Phase 6 - Passage complet en français

A effectuer après gel du load order pour éviter de retraduire des plugins encore mouvants.

- [ ] Passer Skyrim / ressources prévues en français selon la méthode retenue.
- [ ] Traduire les mods ajoutés nécessitant une traduction.
- [ ] Vérifier ESP/ESM/ESL.
- [ ] Vérifier MCM / fichiers Interface / strings.
- [ ] Vérifier les textes présents dans les scripts sources lorsque pertinent.
- [ ] Ne jamais laisser une traduction écraser scripts, DLL, meshes ou autres assets sans justification.
- [ ] Tester dialogues, notifications, menus et MCM.
- [ ] Mettre à jour `07-TRANSLATIONS-FR.md`.

---

## Phase 7 - Contrôle technique pré-final

Cette phase complète la checklist `13-PRE-PLAYTHROUGH-CHECKLIST.md`.

### MO2 / fichiers

- [ ] Vérifier l'ordre du panneau gauche.
- [ ] Vérifier l'ordre des plugins.
- [ ] Inspecter les conflits de fichiers importants.
- [ ] Inspecter / vider MO2 Overwrite.
- [ ] Ranger les sorties générées dans leurs mods dédiés.
- [ ] Vérifier les séparateurs et noms Rhiven.

### Plugins / xEdit

- [ ] Vérifier les erreurs des plugins ajoutés.
- [ ] Vérifier les conflits inattendus.
- [ ] Vérifier les masters manquants.
- [ ] Vérifier les ESL / ESPFE lorsque pertinent.
- [ ] Contrôler le nombre de plugins lourds.
- [ ] Utiliser LOOT comme **outil de diagnostic**, jamais comme tri automatique aveugle de l'instance finalisée.

### SKSE / DLL / frameworks

- [ ] Vérifier chaque DLL SKSE ajoutée.
- [ ] Vérifier Address Library et dépendances.
- [ ] Vérifier l'absence d'ancien binaire incompatible hérité de V16.
- [ ] Vérifier SexLab et les extensions retenues.
- [ ] Vérifier SlaveTats et le bloc tatouages final.

### Animations

- [ ] Lancer Pandora après le dernier changement animation.
- [ ] Vérifier l'absence d'erreur bloquante.
- [ ] Tester locomotion, idles, combat et scènes framework représentatives.

### BodySlide / morphs / physics

- [ ] Régénérer uniquement ce qui doit l'être.
- [ ] Contrôler CBBE 3BA / morphs.
- [ ] Vérifier SMP / collisions / vêtements ajoutés.

### Test stabilité final

- [ ] Lancement depuis MO2.
- [ ] Chargement de la sauvegarde de validation.
- [ ] Sauvegarde manuelle.
- [ ] Rechargement.
- [ ] Changement de cellules.
- [ ] Fast travel si pertinent.
- [ ] Intérieur / extérieur.
- [ ] Combat.
- [ ] Scène SexLab représentative.
- [ ] Test tatouages.
- [ ] Test UI.
- [ ] Vérifier logs uniquement en cas de symptôme ou erreur reproductible.

---

## Phase 8 - Lancement de la partie définitive

### 8.1 Nouvelle partie — départ propre

- [ ] Démarrer depuis **NEFARAM_Start**.
- [ ] Créer Rhiven / personnage définitif.
- [ ] Laisser les scripts de démarrage et enregistrements MCM se stabiliser.
- [ ] Sauvegarde propre de référence avant configuration lourde.

### 8.2 Mega-session MCM

- [ ] Appliquer le preset NEFARAM prévu.
- [ ] **SexLab Approach Redux 3.62 :** partir des defaults propres 3.62, puis reprendre sélectivement les bonnes idées du preset historique `NEFARAM - 263` plutôt que l'importer en bloc. À revoir explicitement : SLHH, BaboDialogue, DDI, SexLab Survival, `basechancemultiplier=0.7`, fréquence 70 s, seuils d'arousal 25/25/80, `Unique Actor`, relation minimum, `OnlyinTown` et `Sex CoolTime`. Conserver une densité d'événements modérée.
- [ ] Configurer les MCM par blocs logiques.
- [ ] Régler les systèmes SexLab / arousal / tatouages retenus.
- [ ] Régler survie / besoins / hygiène.
- [ ] Régler fertilité.
- [ ] Régler UI / HUD.
- [ ] Régler Wheeler et hotkeys.
- [ ] Rechercher les conflits de touches.
- [ ] Faire une sauvegarde de référence après configuration.

### 8.3 Validation avant vraie partie

- [ ] Quitter complètement Skyrim.
- [ ] Relancer.
- [ ] Charger la sauvegarde MCM configurée.
- [ ] Vérifier que les paramètres persistent.
- [ ] Faire quelques tests représentatifs.
- [ ] Si aucun problème bloquant n'apparaît : **NEFARAM-Rhiven 1.1 est considéré finalisé pour le playthrough.**
- [ ] Lancer la vraie partie et jouer.

---

## Règle après finalisation

Après lancement de la vraie partie :

> **Pas de modification structurelle du socle sans raison sérieuse.**

Les futurs ajouts doivent être évalués selon trois questions :

1. Apportent-ils réellement quelque chose au playthrough ?
2. Peuvent-ils être installés proprement sur une partie en cours ?
3. Le bénéfice justifie-t-il le risque sur une instance désormais stable ?

La réponse `non` à l'une de ces questions doit fortement pousser au report jusqu'au prochain playthrough.
