# 15 - Roadmap de finalisation NEFARAM-Rhiven 1.1

Cette fiche fixe l'ordre de travail jusqu'au lancement de la partie définitive.

**Avancement mis à jour le 14/10/2026 — cible : NEFARAM-Rhiven 1.1.**

**L'installation de tous les mods prévus est terminée.** Les snapshots des deux panneaux MO2 ont été mis à jour dans [load-order](../load-order/README.md). Une copie complète de l'instance NEFARAM d'origine a permis les essais réversibles. L'instance stable a été remise en place sous `C:\JEUX\NEFARAM` ; l'instance expérimentale Community Shaders est conservée séparément sous `C:\JEUX\NEFARAM_CS`.

Ordre de travail restant : **terminer les contrôles du choix graphique Silent Horizons 2 + ReShade LUT13 → gel graphique → passage de Skyrim en français → traduction des mods → checklist pré-finale → départ via NEFARAM_Start → paramétrage des MCM → validation et jeu.**

Les phases 1 à 4 ci-dessous conservent l'historique et les contrôles détaillés. Leurs cases de tests non cochées restent à confirmer : **installation terminée ne signifie pas que tous les tests fonctionnels sont validés**. Elles ne constituent plus une liste de mods à installer.

Baseline actuelle : **NEFARAM 17.3.7**, profil MO2 **ELEANOR Stable**.

> Important : la partie définitive doit démarrer depuis la sauvegarde fournie **NEFARAM_Start**, conformément à la baseline du dépôt, et non depuis le bouton vanilla `New Game`.

---

## Phase 0 - Règles de travail

- [ ] Installer et tester **un bloc logique à la fois**.
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
- [ ] Mettre à jour `03-MODS-ADDED.md`.
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
- [ ] Finaliser **Phoenix Katana** : installation, personnalisation des records dans un plugin Rhiven séparé, tests Eleanor ; tâche prévue avant les traductions.
- [ ] Suivre le **chantier HUD détaillé** dans [guides/HUD/README.md](guides/HUD/README.md) ; ne pas dupliquer ici ses choix et ses tests.

Source : https://www.nexusmods.com/skyrimspecialedition/mods/176230

---

## Phase 5 - Étude graphique finale — choix effectué le 14/10/2026

**Décision : conserver la base NEFARAM 17.3.7 d'origine et adopter ENB + Silent Horizons 2, complété par ReShade 6.8.0 et le preset Sswaye LUT13.** Community Shaders a été essayé sur une instance séparée, puis écarté au profit du rendu préféré et du retour à la configuration fonctionnelle d'origine.

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
