# Roadmap de finalisation NEFARAM-Rhiven 1.1

Cette roadmap retrace les étapes finales validées et les derniers contrôles de début de partie. Les intégrations terminées, les validations historiques et les candidats non retenus sont documentés dans leurs fiches techniques, le [changelog](CHANGELOG.md) et l'[historique des mods non retenus](Docs/MODS-NOT-RETAINED.md).

**Baseline actuelle :** NEFARAM 17.3.8 · profil MO2 `Eleanor 17.3.8 - Naked Defeat`.

**État au 10 novembre 2026 :** phases 6 et 7 déclarées terminées ; phase 8 (création d'Eleanor, paramétrage et vérification de persistance) validée. **PLAYTHROUGH READY / ACTIVE** pour le démarrage, avec contrôles des scénarios en jeu restant à effectuer. Le socle fonctionnel est gelé.

> La partie définitive doit démarrer depuis la sauvegarde fournie **NEFARAM_Start**, et non depuis le bouton vanilla `New Game`.

## 1. Phase 6 — passage complet en français ✅

- [x] Passer Skyrim et les ressources prévues en français selon la méthode retenue.
- [x] Traduire les mods ajoutés qui le nécessitent.
- [x] Vérifier les textes des ESP/ESM/ESL, MCM, fichiers Interface, strings et scripts sources lorsque pertinent.
- [x] Ne jamais laisser une traduction écraser scripts, DLL, meshes ou autres assets sans justification.
- [x] Tester dialogues, notifications, menus et MCM.
- [x] Mettre à jour la [fiche des traductions françaises](Docs/10%20-%20TRANSLATIONS/07-TRANSLATIONS-FR.md).

## 2. Phase 7 — contrôle technique pré-final ✅

Le détail opérationnel reste centralisé dans la [checklist pré-playthrough](Docs/VALIDATION/13-PRE-PLAYTHROUGH-CHECKLIST.md) et la [fiche de validation](Docs/VALIDATION/08-TESTING.md).

- [x] Vérifier le panneau gauche MO2, l'ordre des plugins, les conflits importants, les sorties générées et `Overwrite`.
- [x] Mettre à jour les snapshots MO2 Rhiven après le dernier état retenu.
- [x] Contrôler masters manquants, erreurs xEdit, ESL/ESPFE et DLL SKSE ajoutées.
- [x] Lancer Pandora après le dernier changement d'animations et vérifier l'absence d'erreur bloquante.
- [x] Régénérer uniquement les sorties BodySlide, morphs ou physiques qui doivent réellement l'être.
- [x] Effectuer le test de stabilité pré-final depuis MO2 : lancement, chargement, sauvegarde/rechargement, changements de cellules, combat et scènes représentatives.

## 3. Phase 8 — configuration définitive validée ✅

- [x] Démarrer depuis **NEFARAM_Start** et créer le personnage définitif.
- [x] Laisser les scripts de démarrage et les enregistrements MCM se stabiliser, puis créer une sauvegarde propre.
- [x] Configurer les MCM par blocs logiques : gameplay, SexLab/arousal/tatouages, survie, fertilité, UI/HUD, Wheeler et raccourcis.
- [x] Régler les widgets et préférences HUD pendant cette session finale, conformément aux fiches UI/validation.
- [ ] **Suivi de début de partie :** confirmer en jeu le réglage conservateur de SexLab Approach Redux 3.62 depuis les valeurs propres 3.62 ; ne pas importer aveuglément les anciennes valeurs. Voir sa [fiche d'intégration](Docs/06%20-%20GAMEPLAY/SEXLAB%20APPROACH%20REDUX/SEXLAB-APPROACH-REDUX-INTEGRATION.md).
- [x] Quitter complètement Skyrim, relancer, charger la sauvegarde configurée et vérifier la persistance des paramètres.
- [x] Si aucun problème bloquant n'apparaît, considérer NEFARAM-Rhiven 1.1 finalisé et lancer la partie.

### Réglages et contrôles confirmés pendant la finalisation

- Profil définitif : `Eleanor 17.3.8 - Naked Defeat` ; snapshots MO2 et traductions FR mis à jour.
- Pandora : **39 546 animations ajoutées**, génération terminée en **11,36 s** (message de fin reçu).
- SkyHUD : boussole replacée en haut ; crosshair permanent fonctionnel.
- TrueHUD repositionné ; widgets Beeing Female NG ajustés ; profil BodyMorph `CBBE 3BA.ini`.
- SkyUI > Avancé > Carte d'objets : **alignement Centre**, **axe horizontal -20**, **axe vertical -120** (test avec un livre).
- Tailor **3.0.1** retenu pour les tenues d'Eleanor : raccourci AZERTY **Maj+W** fonctionnel.
- Naked Defeat : Naked Loot désactivé ; Naked Curses à 0 %. Vérification SSEEdit de la propriété `IndecencyRapeProb` : **Float = 0** dans `nade_ConfigQuest` ; curseur MCM absent/commenté, aucun changement de l'ESP nécessaire.
- Sauvegarde manuelle créée ; fermeture complète du jeu, relancement et rechargement réussis ; **persistance des MCM, HUD et raccourcis confirmée**.

### Vérifications de gameplay restantes (non bloquantes pour commencer, mais non validées)

- [ ] Tester sur sauvegarde jetable la chaîne **Acheron → bridge → Naked Defeat**, contre humanoïdes et créatures, avec retour des contrôles, nettoyage des assaillants et sauvegarde/rechargement après événement.
- [ ] Vérifier les risques de déclenchements simultanés entre événements civils, Public Whore, autres mods et châtiments publics.
- [ ] Tester Dangerous Nights et ses interactions de sommeil sur une sauvegarde de test.
- [ ] Confirmer en jeu les interactions d'équipement/tenues et les systèmes de survie/fertilité au fil des premières sessions.
- [ ] Reporter les corrections pertinentes dans la [checklist détaillée](Docs/VALIDATION/13-PRE-PLAYTHROUGH-CHECKLIST.md) et la [fiche de validation](Docs/VALIDATION/08-TESTING.md).

Les anomalies rares découvertes ensuite seront traitées au cas par cas, sans rouvrir une validation générique de chaque intégration déjà retenue.

## 4. Backlog non bloquant

- [ ] Évaluer **ReSaver++** : provenance, différences avec ReSaver/FallrimTools et formats pris en charge. Ne jamais nettoyer automatiquement une sauvegarde importante sans copie préalable.

## Règle après finalisation

> **Pas de modification structurelle du socle sans raison sérieuse.**

Un ajout futur doit apporter un bénéfice réel, pouvoir être intégré proprement à une partie en cours et justifier son risque sur une instance stable. Dans le doute, le reporter au prochain playthrough.
