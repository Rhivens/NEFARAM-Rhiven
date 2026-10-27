# Sous-chantier HUD & Interface — NEFARAM-Rhiven

> **Statut : interface Vel'Dun actuelle, intégrée et validée visuellement/en jeu après plusieurs essais ; calibration détaillée HUD/MCM reportée à la partie définitive.**
>
> **Référence actuelle UI/HUD :** cette fiche décrit la direction active de NEFARAM-Rhiven. L'ancienne configuration Dragonborn UI, elle aussi validée en jeu mais désormais remplacée, reste documentée dans [`DRAGONBORN-UI.md`](DRAGONBORN-UI.md).
>
> Ce document combine les **observations validées en jeu** et la **feuille de route** pour la calibration HUD restant à faire. La partie définitive d'Eleanor n'a pas commencé. On termine d'abord les ajouts classiques au modpack, puis on traite l'interface comme un chantier autonome, avant la checklist de lancement.
>
> **Validation initiale :** personnalisation réalisée sous NEFARAM 17.3.7, profil MO2 `ELEANOR Stable`.  
> **Baseline actuelle :** NEFARAM-Rhiven 17.3.8, profil `Eleanor Stable 17.3.8`. Les instantanés `load-order/NEFARAM-RHIVEN-MODDED-MO2-LEFT.md` et `load-order/NEFARAM-RHIVEN-MODDED-MO2-RIGHT.md` ont depuis été rafraîchis pour la 17.3.8.


## État réel au 14 octobre 2026 — personnalisation UI

- **Vel'dun UI principal 1.0.6 + Patches 1.0.6 conservés.** La 1.0.7 du mod principal avait causé un problème avec le menu Échap ; ne pas proposer cette mise à jour comme acquise. Le FOMOD affiché pour **Vel'dun UI Overhauls** était quant à lui marqué **1.0.7** : distinguer les versions de ces modules.
- **Modern Wait Menu original** installé en haut du bloc `47 - UI - Rhiven`. L'habillage Nithog se trouve dans **Vel'dun UI Overhauls**, option FOMOD `Wait/Sleep Menu → 2. Modern Wait Menu`. Le nouveau menu circulaire a été vu en jeu, sans test exhaustif du mécanisme d'attente.
- **The Dragonborn's Bestiary** : FOMOD Overhauls `2A. Bestiary Patch` pour le 16:9. Habillage Vel'dun observé en jeu ; aucun contenu à ce stade sur le PJ de test.
- **Quest Journal** : `1. Skip` car seul **Knotwork pour SkyUI V5 2.1.0** est installé, pas Quest Journal Overhaul ni sa déclinaison Knotwork.
- **Reskins Dragonborn personnels réactivés** : `Dragonborn Reskin - SkyUI Inventory Category Icons - Rhiven` (icônes colorées observées) et `Dragonborn Reskin - STB Active Effects - Rhiven` (pas encore testé avec un effet actif). Les deux mods Wheeler Dragonborn sont également visibles actifs dans MO2.
- Ordre panneau gauche (éléments clés) : `Modern Wait Menu` → `Vel'dun UI` → `Vel'dun UI Patches` → `Vel'dun UI Overhauls` → `Dragonborn - Wheeler Reskin` + options → `Dragonborn Reskin - SkyUI Inventory Category Icons` → `Dragonborn Reskin - STB Active Effects`. Priorité bas de liste pour les fichiers identiques.
- Dans l'onglet Conflits de **Vel'dun UI Overhauls**, les fichiers `sleepwaitmenu.swf`, `PlatformButtons.swf`, `bestiarymenu.swf` et `bestiarywidget.swf` sont gagnants. `favoritesmenu.swf` gagne aussi ; tester les favoris pour exclure une régression inattendue.
- **Outfit Gallery 1.0.15** : menu visible en jeu ; `External (Translation.json)` disponible comme piste pour une future traduction FR, après inspection du format. Tenues automatiques pour compagnons **à laisser désactivées**. Usage multiple et sauvegarde des tenues à tester sur la vraie Eleanor ; comparaison avec Fitting Room non close.
- **Contrôles restant ouverts :** valider une attente complète, le menu Échap après cette combinaison, l'affichage STB avec effet actif, le Bestiaire avec du contenu, le menu Favoris, l'absence de conflit de touches, et le maintien des réglages au redémarrage. Ne pas confondre captures visuelles et validation fonctionnelle exhaustive.
- Sources : [Vel'dun UI](https://www.nexusmods.com/skyrimspecialedition/mods/176230) ; [Modern Wait Menu](https://www.nexusmods.com/skyrimspecialedition/mods/117661) ; [Outfit Gallery](https://www.nexusmods.com/skyrimspecialedition/mods/193410).

## Objectif

Construire le HUD personnel d'Eleanor : menus harmonisés avec Vel'dun, widgets utiles et lisibles, positionnement et échelles choisis librement, sans copier obligatoirement la disposition Nolvus. Documenter les réglages pour les **reproduire sur une nouvelle partie**, en identifiant ce qui peut réellement être exporté et ce qui reste lié à une sauvegarde.

## Décisions et constats déjà établis

- **SkyUI 5.2 conservé** et **MCM Helper 1.5.0 conservé**. Nithog a confirmé sur Discord que la version récente de Vel'dun peut fonctionner avec ce couple ; la position de l'objet 3D dans le MCM SkyUI peut demander un ajustement. Ce retour ne remplace pas un test complet dans NEFARAM-Rhiven.
- **Vel'dun UI principal 1.0.6 + Patches 1.0.6** sont installés et conservés après plusieurs essais visuels et en jeu. La version 1.0.7 du mod principal n'est pas validée : elle a provoqué un problème avec le menu Échap. Le numéro 1.0.7 affiché par le FOMOD de **Vel'dun UI Overhauls** désigne ce module complémentaire et ne doit pas être confondu avec la version retenue du mod principal.
- Lors de la bascule initiale, les quatre **reskins Dragonborn** suivants avaient été désactivés dans MO2 : `Dragonborn UI - SkyUI Reskin - Rhiven`, `Dragonborn Reskin - Skyrim Character Sheet - Rhiven`, `Dragonborn - Wheeler Reskin - Rhiven`, `Dragonborn - Wheeler Reskin Edge UI Color Options - Rhiven`. Les deux reskins Wheeler ont ensuite été explicitement réactivés, de même que les reskins d'icônes d'inventaire et de STB Active Effects recensés plus haut. **Wheeler**, **Perfected Wheeler**, **Compare Equipment NG** et **Skyrim Character Sheet** restent des fonctionnalités distinctes. L'ancienne configuration complète est conservée dans [`DRAGONBORN-UI.md`](DRAGONBORN-UI.md).
- **Dear Diary Dark Mode** et ses patchs sont conservés ; Vel'dun gagne les conflits d'apparence pertinents observés. Ne pas conclure pour autant à une compatibilité fonctionnelle exhaustive avant la fin de l'audit MO2 et des tests reportés.
- Le FOMOD principal et les modules complémentaires ont été sélectionnés **selon les composants installés**, et non tous d'office. **Vel'dun UI Patches 1.0.6** et **Vel'dun UI Overhauls** sont intégrés ; RaceMenu DIP, Wheeler et QuickLoot ne doivent être retenus que si leur besoin réel est confirmé.
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
| Vel'dun UI | Thème visuel des menus | Principal 1.0.6 + Patches 1.0.6 intégrés et validés visuellement/en jeu ; Overhauls observé fonctionnel visuellement ; contrôles fonctionnels détaillés encore ouverts |
| SkyHUD / autres interfaces NEFARAM | Positionnement et intégration HUD | Présents ; auditer les conflits de fichiers et les réglages |

Les indications de touches dans une image Nolvus ne sont **pas** des raccourcis déjà validés pour NEFARAM-Rhiven.

## Feuille de route

### 1. Préparation — après les mods classiques
- [ ] Terminer les ajouts hors interface et mettre à jour les deux instantanés MO2.
- [ ] Créer un profil de test `ELEANOR HUD TEST`, avec sauvegardes spécifiques au profil et vérification des sorties communes.
- [ ] Inventorier tous les widgets, leurs dépendances, les éventuels doublons et les modules réellement nécessaires.
- [ ] Déterminer la résolution, le format d'écran, les réglages d'échelle et les touches déjà utilisées.

### 2. Intégration Vel'dun
- [x] Installer et conserver **Vel'dun UI principal 1.0.6 + Patches 1.0.6** après plusieurs essais visuels et en jeu ; ne pas valider le mod principal 1.0.7 à cause du problème observé avec le menu Échap.
- [x] Intégrer **Vel'dun UI Overhauls** et constater visuellement le Modern Wait Menu, l'habillage du Bestiaire et les fichiers gagnants recensés plus haut ; son FOMOD peut afficher 1.0.7 sans modifier la version retenue du mod principal.
- [x] Réactiver uniquement les reskins Dragonborn explicitement conservés et confirmer visuellement les icônes d'inventaire ; garder les vérifications STB et Wheeler détaillées ouvertes.
- [ ] Relever exhaustivement les options FOMOD retenues et évaluer séparément RaceMenu DIP, Wheeler et les autres modules éventuels ; ignorer les modules non requis.
- [ ] Achever l'audit des conflits **gagnés/perdus** MO2, fichiers Interface/SWF, INI, polices, boussole, widgets et éventuels plugins au-delà des fichiers déjà observés.
- [ ] Compléter les tests fonctionnels des menus SkyUI, objet 3D, fiches d'objets, MCM, RaceMenu, Wheeler, boussole et HUD, ainsi que les contrôles ouverts listés dans l'état réel.

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
