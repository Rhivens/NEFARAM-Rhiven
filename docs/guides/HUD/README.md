# Sous-chantier HUD & Interface — NEFARAM-Rhiven

> **Statut : planifié — installation et calibration différées.**
>
> Ce document est une **feuille de route**, pas une configuration HUD déjà validée. La partie définitive d'Eleanor n'a pas commencé. On termine d'abord les ajouts classiques au modpack, puis on traite l'interface comme un chantier autonome, avant la checklist de lancement.
>
> **Base de référence :** NEFARAM 17.3.7 personnalisé, profil MO2 `ELEANOR Stable`. Les instantanés à actualiser lors du chantier sont `load-order/NEFARAM-RHIVEN-MODDED-MO2-LEFT.md` et `load-order/NEFARAM-RHIVEN-MODDED-MO2-RIGHT.md`.

## Objectif

Construire le HUD personnel d'Eleanor : menus harmonisés avec Vel'dun, widgets utiles et lisibles, positionnement et échelles choisis librement, sans copier obligatoirement la disposition Nolvus. Documenter les réglages pour les **reproduire sur une nouvelle partie**, en identifiant ce qui peut réellement être exporté et ce qui reste lié à une sauvegarde.

## Décisions et constats déjà établis

- **SkyUI 5.2 conservé** et **MCM Helper 1.5.0 conservé**. Nithog a confirmé sur Discord que la version récente de Vel'dun peut fonctionner avec ce couple ; la position de l'objet 3D dans le MCM SkyUI peut demander un ajustement. Ce retour ne remplace pas un test complet dans NEFARAM-Rhiven.
- **Vel'dun UI 1.0.6** prévu, **non validé en jeu** dans cette configuration. Placer initialement le mod à la fin du séparateur `04 - User Interface`, après `Compare Equipment NG - Rhiven`. Ajuster sa priorité MO2 uniquement en fonction des vrais conflits de fichiers.
- Les quatre **reskins Dragonborn** ont été désactivés dans MO2 : `Dragonborn UI - SkyUI Reskin - Rhiven`, `Dragonborn Reskin - Skyrim Character Sheet - Rhiven`, `Dragonborn - Wheeler Reskin - Rhiven`, `Dragonborn - Wheeler Reskin Edge UI Color Options - Rhiven`. **Wheeler**, **Perfected Wheeler**, **Compare Equipment NG** et **Skyrim Character Sheet** restent des fonctionnalités distinctes.
- **Dear Diary Dark Mode** et ses patchs sont conservés pour les tests ; Vel'dun pourra gagner les conflits d'apparence pertinents. Ne pas supposer une compatibilité complète sans audit MO2 et tests.
- Le FOMOD principal et les éventuels modules complémentaires sont **à sélectionner selon les composants installés**, et non tous d'office : Vel'dun UI Patches, Overhauls, RaceMenu DIP, Wheeler. QuickLoot seulement si besoin réel.
- **STB Active Effects est déjà présent** ; **STB Widgets est un ajout envisagé**, connu de l'ancienne installation mais pas encore restauré.
- La capture HUD issue de Nolvus fournie en conversation sert à identifier **quel mod affiche quoi**, **pas** à imposer des coordonnées, des dimensions ou une disposition.
- On travaille de préférence sur un **profil MO2 de laboratoire** avec sauvegardes séparées et on protège `ELEANOR Stable`. Vérifier également les sorties partagées entre profils.

## Inventaire fonctionnel à examiner

| Composant | Usage envisagé | État / vérification |
|---|---|---|
| STB Widgets | Résistances, armure et statistiques complémentaires | À installer ou évaluer ; menu via touche End selon référence Nolvus, raccourci réel à vérifier |
| STB Active Effects | Effets actifs | Présent ; vérifier son interaction avec Vel'dun et STB Widgets |
| SL Widgets | Informations SexLab | Présent ; réglages et persistance à auditer |
| A Matter of Time | Horloge et calendrier | Présent ; MCM et éventuel preset Seasons |
| Compass Navigation Overhaul | Boussole et marqueurs de navigation | Présent ; réglages/INI et raccourcis à relever |
| TrueHUD | Barres et informations de combat | Présent ; MCM Player Info |
| SunHelm | Faim, soif, fatigue / survie | Présent ; décider quoi afficher pour éviter les doublons |
| Widget complémentaire Bathing in Skyrim Renewed (BiSR) | Hygiène / bain | Présent ; ne pas confondre avec Dirt & Blood de l'exemple Nolvus |
| Equipment Durability System NG | Usure de l'équipement | Présent ; preset et paramètres visuels à déterminer |
| Vel'dun UI | Thème visuel des menus | À installer et tester, avec modules sélectionnés |
| SkyHUD / autres interfaces NEFARAM | Positionnement et intégration HUD | Présents ; auditer les conflits de fichiers et les réglages |

Les indications de touches dans une image Nolvus ne sont **pas** des raccourcis déjà validés pour NEFARAM-Rhiven.

## Feuille de route

### 1. Préparation — après les mods classiques
- [ ] Terminer les ajouts hors interface et mettre à jour les deux instantanés MO2.
- [ ] Créer un profil de test `ELEANOR HUD TEST`, avec sauvegardes spécifiques au profil et vérification des sorties communes.
- [ ] Inventorier tous les widgets, leurs dépendances, les éventuels doublons et les modules réellement nécessaires.
- [ ] Déterminer la résolution, le format d'écran, les réglages d'échelle et les touches déjà utilisées.

### 2. Intégration Vel'dun
- [ ] Installer le fichier principal Vel'dun UI 1.0.6 ; relever précisément les options FOMOD.
- [ ] Évaluer séparément Patches, Overhauls, RaceMenu DIP et Wheeler ; ignorer les modules non requis.
- [ ] Vérifier conflits **gagnés/perdus** MO2, fichiers Interface/SWF, INI, polices, boussole, widgets et éventuels plugins.
- [ ] Vérifier menus SkyUI, objet 3D, fiches d'objets, MCM, RaceMenu, Wheeler, boussole et HUD en jeu.

### 3. Calibration HUD en partie de laboratoire
- [ ] Activer uniquement les widgets retenus et éliminer les informations redondantes.
- [ ] Positionner progressivement les groupes (navigation, combat, survie, statuts, horloge, hygiène).
- [ ] Noter pour chaque élément : visibilité, ancrage, X/Y si accessibles, échelle, police/couleur, raccourci, conditions d'affichage.
- [ ] Tester exploration, combat, inventaire, dialogue, magie, changement d'heure et situations de survie.
- [ ] Vérifier qu'aucun HUD ne masque un menu ou un autre widget.

### 4. Conservation et restauration
- [ ] Identifier **mod par mod** le stockage effectif : INI/JSON/TOML, export MCM/FISS/Settings Loader, cosave, sauvegarde Papyrus ou autre.
- [ ] Sauvegarder les fichiers de configuration exportables **sans écraser les originaux NEFARAM** ; décrire les chemins et la méthode de restauration.
- [ ] Noter les valeurs MCM qui ne sont pas exportables et produire des captures comparatives avec la résolution de référence.
- [ ] Tester la restauration sur **une nouvelle sauvegarde vierge du laboratoire** ; ne pas supposer qu'une configuration dépendante d'une save est portable.
- [ ] Conserver une capture de référence du HUD final ; une fiche GitHub seule ne garantit pas la restauration automatique de tous les MCM.

### 5. Validation avant la vraie partie
- [ ] Vérifier l'absence de collisions de raccourcis, de doublons et de problèmes de lisibilité.
- [ ] Figer les versions des modules UI et les options choisies.
- [ ] Reporter les fichiers transférables dans le profil définitif après validation, et prévoir les MCM à reconfigurer après démarrage.
- [ ] Documenter la procédure courte « HUD Eleanor : restauration sur nouvelle partie ».
- [ ] Cocher le chantier dans `docs/13-PRE-PLAYTHROUGH-CHECKLIST.md` **uniquement après les tests réussis**.

## Fiche de calibration à dupliquer pour chaque widget

```text
Composant / version :
Fonction :
Actif dans le profil définitif : oui / non / à décider
Position / ancrage :
Coordonnées X / Y (si disponibles) :
Échelle :
Aspect / affichage :
Touche(s) :
Menu de réglage : MCM / overlay / INI / autre
Fichier(s) de configuration et chemin(s) :
Emplacement réel de sauvegarde des paramètres :
Export / import possible : vérifié / non / partiel
Procédure de restauration sur nouvelle partie :
Captures de référence :
Tests effectués :
Remarques / interactions avec Vel'dun :
```

## Règle de conservation

**Ne pas modifier ni effacer les configurations d'origine simplement pour « nettoyer ».** Chaque changement doit rester réversible dans MO2 ; distinguer observations vérifiées, hypothèses, et choix esthétiques personnels.

---
*Ouverture du sous-chantier : octobre 2026. Aucune disposition HUD définitive n'est arrêtée.*
