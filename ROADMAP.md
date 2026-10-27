# Roadmap de finalisation NEFARAM-Rhiven 1.1

Cette roadmap ne conserve que les travaux encore à réaliser. Les intégrations terminées, les validations historiques et les candidats non retenus sont documentés dans leurs fiches techniques, le [changelog](CHANGELOG.md) et l'[historique des mods non retenus](Docs/MODS-NOT-RETAINED.md).

**Baseline actuelle :** NEFARAM 17.3.8 · profil MO2 `Eleanor Stable 17.3.8`.

**Phase active :** passage complet en français. Le socle fonctionnel est gelé ; les nouveaux changements doivent répondre à un besoin concret de correction ou de finalisation.

> La partie définitive doit démarrer depuis la sauvegarde fournie **NEFARAM_Start**, et non depuis le bouton vanilla `New Game`.

## 1. Validation technique restante — Unethical Alchemy 1.0.0

L'archive publique `Unethical Alchemy - Rhiven Fix.zip` est désormais conservée sous `Docs/03 - PATCHES FIXES/`. Le correctif ciblé d'Agryn Gaering passe déjà `Check for Errors` avec **2 records / 0 erreur**. Les vérifications suivantes restent ouvertes et ne doivent pas être confondues avec la publication désormais terminée :

- [ ] Vérifier dans xEdit les deux signalements LoversLab :
  - `[CELL:0000BCFB]` dans Tamriel 32,-25 : `CELL \ XCWT - Water -> Found a NULL reference, expected: WATR` ;
  - `HeartwoodMillExterior [CELL:0000BCDA]` dans Tamriel 32,-24 : même signalement `XCWT - Water = NULL`.
- [ ] Confirmer que ces entrées sont réellement erronées avant toute correction.
- [ ] Si l'erreur est confirmée, étendre le correctif en supprimant uniquement les `XCWT` invalides et en préservant toutes les autres données des CELL.
- [ ] Lancer `Check for Errors` sur le mod de base et le patch, avec une cible de **0 erreur**.
- [ ] Créer le guide communautaire Unethical Alchemy seulement après cette validation complémentaire.

Référence technique : [Unethical Alchemy 1.0.0](Docs/06%20-%20GAMEPLAY/UNETHICAL%20ALCHEMY/UNETHICAL-ALCHEMY-1.0.0-INTEGRATION.md).

## 2. Examen différé du patch PAMA candidat partagé sur Discord

Naked Defeat 6.51 est désormais **intégré et fonctionnel** ; sa [fiche d'étude](Docs/06%20-%20GAMEPLAY/NAKED%20DEFEAT/NAKED-DEFEAT-6.51-PRELIMINARY-INTEGRATION-STUDY.md) reste conservée comme référence technique. Après la validation complémentaire d'Unethical Alchemy 1.0.0 déjà placée en tête de cette roadmap, cet examen PAMA devient le prochain chantier technique majeur. Le fichier partagé est un candidat de test construit pour **NEFARAM 17.0.3** ; il ne doit pas être intégré à la baseline actuelle sans audit préalable.

Le patch proposé :

- fusionne trois plugins ESP en un seul plugin marqué ESL ;
- corrige trois zones de terrain à Falkreath ;
- restaure les navmeshes vanilla de Morthal, Dawnstar et Falkreath écrasés par Punishment Pack ;
- retire les tenues de prison des factions criminelles des différentes châtellenies ;
- conserve le mod de mesh **ZaZ Ankle Chains** ;
- est conçu pour respecter l'éclairage NEFARAM et les données issues de Synthesis, avec un placement annoncé comme sûr après les sorties Synthesis et les plugins Lux.

- [ ] Auditer le plugin candidat contre **NEFARAM-Rhiven 17.3.8**, sans reprendre comme acquises les conclusions établies pour 17.0.3.
- [ ] Vérifier en priorité que ses corrections de navmesh sont toujours actuelles dans Morthal, Dawnstar et Falkreath.
- [ ] Comparer chaque override avec les patches PAMA Rhiven existants, notamment les correctifs de Windhelm, Solitude, Falkreath et ZaZ Ankle Chains, afin d'identifier les doublons, régressions ou remplacements possibles.
- [ ] Contrôler les interactions avec l'éclairage NEFARAM, Lux et la sortie Synthesis actuelle avant de décider du placement final.
- [ ] Prononcer un verdict séparé : rejet, adoption partielle, remplacement ciblé ou intégration complète après validation xEdit et tests en jeu.

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
