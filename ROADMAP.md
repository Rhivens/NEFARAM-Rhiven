# Roadmap de finalisation NEFARAM-Rhiven 1.1

Cette roadmap ne conserve que les travaux encore à réaliser. Les intégrations terminées, les validations historiques et les candidats non retenus sont documentés dans leurs fiches techniques, le [changelog](CHANGELOG.md) et l'[historique des mods non retenus](Docs/MODS-NOT-RETAINED.md).

**Baseline actuelle :** NEFARAM 17.3.8 · profil MO2 `Eleanor Stable 17.3.8`.

**Phase active :** passage complet en français. Le socle fonctionnel est gelé ; les nouveaux changements doivent répondre à un besoin concret de correction ou de finalisation.

> La partie définitive doit démarrer depuis la sauvegarde fournie **NEFARAM_Start**, et non depuis le bouton vanilla `New Game`.

## 1. Publications à récupérer depuis le PC maison

### Animal Mansion Reborn

- [ ] Récupérer `Animal Mansion Reborn - Rhiven Patch` depuis l'installation MO2.
- [ ] L'empaqueter en ZIP si nécessaire et le publier sous `Docs/03 - PATCHES FIXES/`.
- [ ] Mettre à jour le [registre des patches](Docs/03%20-%20PATCHES%20FIXES/PATCHES-FIXES.md).
- [ ] Mettre à jour le [guide communautaire AMR](Docs/12%20-%20COMMUNITY%20GUIDES/ANIMAL-MANSION-REBORN/ANIMAL-MANSION-NEFARAM-17.3.8-COMMUNITY-GUIDE.md) avec le lien du patch publié.

Le patch est déjà validé techniquement dans xEdit avec **21 records / 0 erreur**. Les éventuels problèmes rencontrés pendant la partie définitive seront traités au cas par cas dans la [fiche d'intégration AMR](Docs/06%20-%20GAMEPLAY/ANIMAL%20MANSION%20REBORN/ANIMAL-MANSION-INTEGRATION.md), sans constituer une phase active de cette roadmap.

### Unethical Alchemy 1.0.0

- [ ] Récupérer `Unethical Alchemy - Rhiven Fix.esp` depuis l'installation MO2.
- [ ] Vérifier dans xEdit les deux signalements LoversLab :
  - `[CELL:0000BCFB]` dans Tamriel 32,-25 : `CELL \ XCWT - Water -> Found a NULL reference, expected: WATR` ;
  - `HeartwoodMillExterior [CELL:0000BCDA]` dans Tamriel 32,-24 : même signalement `XCWT - Water = NULL`.
- [ ] Confirmer que ces entrées sont réellement erronées avant toute correction.
- [ ] Si l'erreur est confirmée, étendre le correctif en supprimant uniquement les `XCWT` invalides et en préservant toutes les autres données des CELL.
- [ ] Lancer `Check for Errors` sur le mod de base et le patch, avec une cible de **0 erreur**.
- [ ] Publier le ZIP final sous `Docs/03 - PATCHES FIXES/` et mettre à jour le registre des patches.
- [ ] Créer le guide communautaire Unethical Alchemy seulement après récupération, validation et publication du patch.

Référence technique : [Unethical Alchemy 1.0.0](Docs/06%20-%20GAMEPLAY/UNETHICAL%20ALCHEMY/UNETHICAL-ALCHEMY-1.0.0-INTEGRATION.md).

### Preset RTC public

- [ ] Récupérer `zzz-Eleanor-RTC.json` depuis l'installation MO2.
- [ ] Relire et valider le JSON avant publication.
- [ ] Renommer la version publique en `zzz-Rhiven-RTC.json`.
- [ ] Vérifier que les choix personnels sont présentés comme tels et non comme des réglages universels.
- [ ] Publier le JSON dans un emplacement logique du dépôt.
- [ ] Mettre à jour le [guide communautaire Tattoos](Docs/12%20-%20COMMUNITY%20GUIDES/TATTOOS/README.md) avec le lien et les notes d'utilisation.

### Registre final des patches

- [ ] Après ces publications, relire le [registre des patches](Docs/03%20-%20PATCHES%20FIXES/PATCHES-FIXES.md) et confirmer que tous les patches Rhiven publiés y sont indexés.

## 2. Migration Naked Defeat 6.51

La configuration Naked Defeat 6.50 est traitée et ne fait plus partie des travaux actifs. La migration 6.51 reste ouverte dans la [fiche d'étude dédiée](Docs/06%20-%20GAMEPLAY/NAKED%20DEFEAT/NAKED-DEFEAT-6.51-PRELIMINARY-INTEGRATION-STUDY.md).

- [ ] Contrôler explicitement `Naked Defeat - Synthesis Fix.esp`.
- [ ] Terminer l'audit comparatif des scripts Papyrus et l'analyse des références/scènes signalées dans la fiche.
- [ ] Effectuer les tests ciblés 6.51 et de non-régression depuis **Start NEFARAM**.
- [ ] Prononcer le verdict de compatibilité et mettre à jour la documentation Naked Defeat.

## 3. Phase 6 — passage complet en français

- [ ] Passer Skyrim et les ressources prévues en français selon la méthode retenue.
- [ ] Traduire les mods ajoutés qui le nécessitent.
- [ ] Vérifier les textes des ESP/ESM/ESL, MCM, fichiers Interface, strings et scripts sources lorsque pertinent.
- [ ] Ne jamais laisser une traduction écraser scripts, DLL, meshes ou autres assets sans justification.
- [ ] Tester dialogues, notifications, menus et MCM.
- [ ] Mettre à jour la [fiche des traductions françaises](Docs/10%20-%20TRANSLATIONS/07-TRANSLATIONS-FR.md).

## 4. Phase 7 — contrôle technique pré-final

Le détail opérationnel reste centralisé dans la [checklist pré-playthrough](Docs/VALIDATION/13-PRE-PLAYTHROUGH-CHECKLIST.md) et la [fiche de validation](Docs/VALIDATION/08-TESTING.md).

- [ ] Vérifier le panneau gauche MO2, l'ordre des plugins, les conflits importants, les sorties générées et `Overwrite`.
- [ ] Mettre à jour les snapshots MO2 Rhiven après le dernier état retenu.
- [ ] Contrôler masters manquants, erreurs xEdit, ESL/ESPFE et DLL SKSE ajoutées.
- [ ] Lancer Pandora après le dernier changement d'animations et vérifier l'absence d'erreur bloquante.
- [ ] Régénérer uniquement les sorties BodySlide, morphs ou physiques qui doivent réellement l'être.
- [ ] Effectuer le test de stabilité pré-final depuis MO2 : lancement, chargement, sauvegarde/rechargement, changements de cellules, combat et scènes représentatives.

## 5. Phase 8 — lancement de la partie définitive

- [ ] Démarrer depuis **NEFARAM_Start** et créer le personnage définitif.
- [ ] Laisser les scripts de démarrage et les enregistrements MCM se stabiliser, puis créer une sauvegarde propre.
- [ ] Configurer les MCM par blocs logiques : gameplay, SexLab/arousal/tatouages, survie, fertilité, UI/HUD, Wheeler et raccourcis.
- [ ] Régler les widgets et préférences HUD pendant cette session finale, conformément aux fiches UI/validation.
- [ ] Pour SexLab Approach Redux 3.62, partir des valeurs propres 3.62 et reprendre seulement les réglages utiles documentés dans sa [fiche d'intégration](Docs/06%20-%20GAMEPLAY/SEXLAB%20APPROACH%20REDUX/SEXLAB-APPROACH-REDUX-INTEGRATION.md).
- [ ] Quitter complètement Skyrim, relancer, charger la sauvegarde configurée et vérifier la persistance des paramètres.
- [ ] Si aucun problème bloquant n'apparaît, considérer NEFARAM-Rhiven 1.1 finalisé et lancer la partie.

Les anomalies rares découvertes ensuite seront traitées au cas par cas, sans rouvrir une validation générique de chaque intégration déjà retenue.

## 6. Backlog non bloquant

- [ ] Évaluer **ReSaver++** : provenance, différences avec ReSaver/FallrimTools et formats pris en charge. Ne jamais nettoyer automatiquement une sauvegarde importante sans copie préalable.

## Règle après finalisation

> **Pas de modification structurelle du socle sans raison sérieuse.**

Un ajout futur doit apporter un bénéfice réel, pouvoir être intégré proprement à une partie en cours et justifier son risque sur une instance stable. Dans le doute, le reporter au prochain playthrough.
