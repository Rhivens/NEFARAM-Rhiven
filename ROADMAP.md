# Roadmap de finalisation NEFARAM-Rhiven 1.1

Cette roadmap ne conserve que les travaux encore à réaliser. Les intégrations terminées, les validations historiques et les candidats non retenus sont documentés dans leurs fiches techniques, le [changelog](CHANGELOG.md) et l'[historique des mods non retenus](Docs/MODS-NOT-RETAINED.md).

**Baseline actuelle :** NEFARAM 17.3.8 · profil MO2 `Eleanor Stable 17.3.8`.

**Phase active :** passage complet en français. Le socle fonctionnel est gelé ; les nouveaux changements doivent répondre à un besoin concret de correction ou de finalisation.

> La partie définitive doit démarrer depuis la sauvegarde fournie **NEFARAM_Start**, et non depuis le bouton vanilla `New Game`.

## 1. Phase 6 — passage complet en français

- [ ] Passer Skyrim et les ressources prévues en français selon la méthode retenue.
- [ ] Traduire les mods ajoutés qui le nécessitent.
- [ ] Vérifier les textes des ESP/ESM/ESL, MCM, fichiers Interface, strings et scripts sources lorsque pertinent.
- [ ] Ne jamais laisser une traduction écraser scripts, DLL, meshes ou autres assets sans justification.
- [ ] Tester dialogues, notifications, menus et MCM.
- [ ] Mettre à jour la [fiche des traductions françaises](Docs/10%20-%20TRANSLATIONS/07-TRANSLATIONS-FR.md).

## 2. Phase 7 — contrôle technique pré-final

Le détail opérationnel reste centralisé dans la [checklist pré-playthrough](Docs/VALIDATION/13-PRE-PLAYTHROUGH-CHECKLIST.md) et la [fiche de validation](Docs/VALIDATION/08-TESTING.md).

- [ ] Vérifier le panneau gauche MO2, l'ordre des plugins, les conflits importants, les sorties générées et `Overwrite`.
- [ ] Mettre à jour les snapshots MO2 Rhiven après le dernier état retenu.
- [ ] Contrôler masters manquants, erreurs xEdit, ESL/ESPFE et DLL SKSE ajoutées.
- [ ] Lancer Pandora après le dernier changement d'animations et vérifier l'absence d'erreur bloquante.
- [ ] Régénérer uniquement les sorties BodySlide, morphs ou physiques qui doivent réellement l'être.
- [ ] Effectuer le test de stabilité pré-final depuis MO2 : lancement, chargement, sauvegarde/rechargement, changements de cellules, combat et scènes représentatives.

## 3. Phase 8 — lancement de la partie définitive

- [ ] Démarrer depuis **NEFARAM_Start** et créer le personnage définitif.
- [ ] Laisser les scripts de démarrage et les enregistrements MCM se stabiliser, puis créer une sauvegarde propre.
- [ ] Configurer les MCM par blocs logiques : gameplay, SexLab/arousal/tatouages, survie, fertilité, UI/HUD, Wheeler et raccourcis.
- [ ] Régler les widgets et préférences HUD pendant cette session finale, conformément aux fiches UI/validation.
- [ ] Pour SexLab Approach Redux 3.62, partir des valeurs propres 3.62 et reprendre seulement les réglages utiles documentés dans sa [fiche d'intégration](Docs/06%20-%20GAMEPLAY/SEXLAB%20APPROACH%20REDUX/SEXLAB-APPROACH-REDUX-INTEGRATION.md).
- [ ] Quitter complètement Skyrim, relancer, charger la sauvegarde configurée et vérifier la persistance des paramètres.
- [ ] Si aucun problème bloquant n'apparaît, considérer NEFARAM-Rhiven 1.1 finalisé et lancer la partie.

Les anomalies rares découvertes ensuite seront traitées au cas par cas, sans rouvrir une validation générique de chaque intégration déjà retenue.

## 4. Backlog non bloquant

- [ ] Évaluer **ReSaver++** : provenance, différences avec ReSaver/FallrimTools et formats pris en charge. Ne jamais nettoyer automatiquement une sauvegarde importante sans copie préalable.

## Règle après finalisation

> **Pas de modification structurelle du socle sans raison sérieuse.**

Un ajout futur doit apporter un bénéfice réel, pouvoir être intégré proprement à une partie en cours et justifier son risque sur une instance stable. Dans le doute, le reporter au prochain playthrough.
