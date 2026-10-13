# 15 - Roadmap de finalisation NEFARAM-Rhiven 1.1

Cette fiche fixe l'ordre de travail jusqu'au lancement de la partie définitive.

**Avancement mis à jour le 13/10/2026 — cible : NEFARAM-Rhiven 1.1.**

**L'installation de tous les mods prévus est terminée.** Les snapshots des deux panneaux MO2 ont été mis à jour dans [load-order](../load-order/README.md). La copie intégrale de `C:\JEUX\NEFARAM` est **en cours** pour conserver l'instance stable de référence et travailler sur une copie.

Ordre de travail restant : **terminer et vérifier la copie de travail → audit graphique final et choix ENB / Community Shaders → passage de Skyrim en français → traduction des mods → checklist pré-finale → départ de la nouvelle partie → paramétrage des MCM → validation et jeu.**

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
- [ ] Terminer la copie intégrale de `C:\JEUX\NEFARAM` — **copie en cours**.
- [ ] Vérifier la copie avant modification : profil MO2, chemins des exécutables et des sorties, lancement et sauvegardes de test doivent pointer vers l'instance de travail.
- [ ] Conserver l'instance stable d'origine comme référence de retour arrière.
- [ ] Effectuer un premier test stabilité global avant le chantier graphique.

---

## Phase 4 - UI / HUD Eleanor : intégration installée, validation à confirmer

**État au 13/10/2026 :** Vel'dun UI et Vel'dun UI Patches figurent dans le snapshot MO2 actuel ; l'installation globale est annoncée terminée. Les contrôles de compatibilité et de fonctionnement restent à confirmer ci-dessous.

Les éventuels correctifs techniques se font sur la copie de travail, sans reconstruire précipitamment l'interface NEFARAM. Vérifier la compatibilité des composants UI ; **reporter les réglages détaillés des widgets et les préférences HUD à la session de configuration des MCM (phase 8)**. Leur ordre précis dans cette session reste à déterminer.

- [ ] Confirmer l'audit de **Vel'Dun UI** déjà installé, en vérifiant les versions de SkyUI et MCM Helper de NEFARAM, ainsi que les options FOMOD réellement utiles.
- [ ] Contrôler la cohabitation avec Dear Diary Dark Mode, Wheeler, TrueHUD, les widgets et le système de menus actuel.
- [ ] Conserver les reskins Dragonborn UI désactivés pendant l'évaluation ; prévoir un retour arrière réversible.
- [ ] Valider le bon fonctionnement technique (affichage 3D, carte / inventaire, HUD de base, hotkeys essentielles et stabilité), sans figer la disposition des widgets.
- [ ] Suivre le **chantier HUD détaillé** dans [guides/HUD/README.md](guides/HUD/README.md) ; ne pas dupliquer ici ses choix et ses tests.

Source : https://www.nexusmods.com/skyrimspecialedition/mods/176230

---

## Phase 5 - Étude graphique finale

**Prochaine étape principale.** La construction du modpack est déclarée terminée : l'audit conservatoire de phase 1 peut désormais être suivi de l'audit graphique final de phase 2. Attendre la fin et la vérification de la copie avant toute modification graphique.

- [ ] Prendre les load orders GitHub actuels comme référence documentaire et comparer avec l'état de l'audit conservatoire.
- [ ] Relever les versions, configurations et fichiers gagnants réels avant de conclure sur une compatibilité.
- [ ] Mesurer le rendu actuel sur la machine de Fabien : RTX 4070 12 Go, 64 Go RAM, résolution effective et fréquence écran à confirmer ; cible **60–70 FPS**.
- [ ] Préparer un plan de migration progressif et réversible avec ordre d'installation, tests intermédiaires et points de retour arrière.
- [ ] Effectuer les essais sur la copie de travail avec des sauvegardes de test dédiées.

### Option A - Optimisation de l'ENB actuel

Commencer par évaluer l'optimisation du preset ENB actuellement utilisé. Tester un autre preset reste une option, pas une décision acquise.

**Silent Horizons 2** — candidat à comparer après vérification de ses prérequis ; changer de preset ne se confond pas avec régler l'ENB actuel.
https://www.nexusmods.com/skyrimspecialedition/mods/99398

Travail :

- [ ] Identifier précisément l'ENB / météo / éclairage actuels.
- [ ] Contrôler les presets et overrides existants.
- [ ] Tester Silent Horizons 2 sans démolir le socle graphique actuel.
- [ ] Mesurer FPS, frametimes, VRAM et stabilité dans plusieurs scènes représentatives.
- [ ] Vérifier intérieurs, extérieurs, nuit, météo, neige, eau, peau, transparences et effets.
- [ ] Conserver l'existant si le gain esthétique ne justifie pas la modification.

### Option B - Community Shaders

- [ ] Lire le [guide NEFARAM ENB → Community Shaders / NAT Effect 11](guides/NEFARAM_Guide_ENB_vers_Community_Shaders_NAT_Effect_11.md), réorganisé à partir des notes Discord.
- [ ] Revalider cette procédure pour **NEFARAM 17.3.7** et les versions retenues : le document source vise **17.2.1**.
- [ ] Identifier les composants ENB remplacés ou non par Community Shaders.
- [ ] Construire un test réversible.
- [ ] Vérifier compatibilités avec météo, éclairages, parallax, grass, water, skin, SMP et UI.
- [ ] **Vel'dun UI Patches** : lors des essais Community Shaders, Bottled Shaders ou Open Shaders, relancer le FOMOD de Vel'dun UI Patches (actuellement v1.0.7), réexaminer l'option **Community Shaders** de la page 5 (actuellement **Skip**) et l'activer uniquement si la pile de shaders correspondante est retenue ; vérifier ensuite les conflits MO2.
- [ ] Mesurer performances et rendu dans les mêmes scènes que l'ENB.

### Documentation NEFARAM et décision graphique

- [x] Localiser la fiche Discord déjà conservée : [NEFARAM — ENB vers Community Shaders avec NAT Effect 11](guides/NEFARAM_Guide_ENB_vers_Community_Shaders_NAT_Effect_11.md).
- [ ] Étudier ses recommandations et vérifier les compatibilités actuelles avant application.

### Décision graphique

- [ ] Comparer **ENB optimisé vs Community Shaders** sur la machine réelle.
- [ ] Décider sur rendu + stabilité + performances, pas sur préférence théorique.
- [ ] Documenter la solution gagnante.
- [ ] Une fois validée : **gel graphique**.

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
