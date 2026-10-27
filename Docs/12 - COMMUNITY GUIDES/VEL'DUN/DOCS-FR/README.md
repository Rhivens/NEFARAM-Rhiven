# Vel'Dun UI pour NEFARAM

> **Statut : validé en jeu sur une configuration basée sur NEFARAM 17.3.x.**
>
> Ce guide décrit une méthode pratique pour remplacer la **présentation visuelle de Dear Diary Dark Mode** par **Vel'Dun UI**, tout en conservant intact le système d'interface existant de NEFARAM.

Le but n'est pas de démanteler toute la pile d'interface de NEFARAM. Vel'Dun devient la nouvelle couche visuelle, tandis que les mods d'interface fonctionnels et les patchs de compatibilité peuvent rester en place lorsqu'ils sont toujours requis.

---

## 1. Base de référence validée

La configuration utilisée pour la validation reposait sur :

- **NEFARAM 17.3.x**
- validation effectuée précisément dans un environnement **17.3.8**
- runtime Skyrim AE **1.6.1170**
- **SkyUI 5.2**
- **MCM Helper 1.5.0**
- Mod Organizer 2

### Note importante sur la compatibilité de SkyUI

Vel'Dun ne nécessite **pas** de migration vers SkyUI 6.0 pour cette configuration.

L'auteur de Vel'Dun a confirmé que l'interface peut fonctionner avec **SkyUI 5.2**, déjà utilisé par NEFARAM. Il est donc possible d'intégrer Vel'Dun sans remplacer la base SkyUI existante.

> **Approche recommandée : conservez SkyUI 5.2 et MCM Helper 1.5.0.**

---

## 2. Versions actuellement validées

Versions conservées pendant les tests :

- **Vel'Dun UI main 1.0.6**
- **Vel'Dun UI Patches 1.0.6**

### À propos de Vel'Dun 1.0.7

La version **1.0.7 du module principal Vel'Dun UI** a provoqué un problème avec le menu Échap / système pendant les tests.

Par conséquent :

> **Vel'Dun UI main 1.0.7 n'est pas considéré comme validé dans ce guide.**

En cas de problème avec le menu Échap, vérifiez que le module principal Vel'Dun UI est toujours en version **1.0.6**.

### Distinction importante : Vel'Dun UI Overhauls

L'installateur **Vel'Dun UI Overhauls** peut afficher la version **1.0.7**.

Il s'agit d'un module distinct, à ne pas confondre avec la version du paquet principal Vel'Dun UI.

---

## 3. Avant de commencer

Avant de modifier l'interface :

1. clonez si possible votre profil MO2 actuel ;
2. conservez une sauvegarde de votre modlist / ordre du panneau gauche ;
3. conservez une sauvegarde de l'ordre de chargement de vos plugins ;
4. utilisez une sauvegarde de test sûre pour les premiers contrôles en jeu.

Les modifications de l'interface sont généralement faciles à annuler dans MO2, mais conserver intact le profil NEFARAM d'origine simplifie beaucoup le dépannage.

---

## 4. Créer un séparateur MO2 dédié

Créez un nouveau séparateur dans le panneau gauche de MO2, par exemple :

```text
UI-CUSTOM
```

Placez les fichiers liés à Vel'Dun dans ce bloc dédié.

Ne vous fiez pas aux numéros de séparateurs d'une autre modlist. La position exacte des séparateurs peut varier d'une installation NEFARAM à l'autre.

---

## 5. Fichiers principaux de Vel'Dun

La configuration principale validée utilise :

```text
Vel'Dun UI
Vel'Dun UI Patches
Vel'Dun UI Overhauls
```

Ordre relatif recommandé :

```text
Vel'Dun UI
Vel'Dun UI Patches
Vel'Dun UI Overhauls
```

Les entrées placées plus bas dans le panneau gauche de MO2 ont une priorité de fichiers plus élevée.

Il faut donc laisser Vel'Dun UI Overhauls gagner les fichiers visuels correspondant aux options que vous avez délibérément sélectionnées dans son installateur.

---

## 6. Dear Diary Dark Mode : que faut-il retirer ?

Ne désinstallez ou ne désactivez **pas** aveuglément toute la pile Dear Diary Dark Mode.

Cette migration constitue avant tout un **remplacement visuel**.

Certains fichiers ou patchs de compatibilité liés à DDDM peuvent rester nécessaires à d'autres mods installés. L'approche la plus sûre consiste à :

1. conserver le système d'interface NEFARAM existant ;
2. installer Vel'Dun plus bas dans le panneau gauche de MO2 ;
3. inspecter les conflits de fichiers ;
4. laisser Vel'Dun gagner les fichiers d'interface visuels prévus ;
5. conserver les patchs de compatibilité fonctionnels lorsqu'ils restent nécessaires.

> L'objectif est de remplacer l'apparence, pas de supprimer tout composant qui mentionne Dear Diary Dark Mode.

Après chaque changement de conflit, testez en jeu les menus concernés.

---

## 7. Options de Vel'Dun UI Overhauls

N'installez que les options destinées aux mods et menus réellement présents dans votre configuration.

Ne sélectionnez **pas** automatiquement toutes les options du FOMOD.

### Modern Wait Menu

Si vous utilisez **Modern Wait Menu** :

1. installez le Modern Wait Menu d'origine ;
2. placez-le avant Vel'Dun dans le bloc d'interface personnalisé ;
3. dans **Vel'Dun UI Overhauls**, sélectionnez :

```text
Wait/Sleep Menu
→ 2. Modern Wait Menu
```

Le menu d'attente circulaire et le skin Vel'Dun ont été confirmés visuellement en jeu.

Le fonctionnement complet de l'attente doit néanmoins être testé dans votre propre configuration.

Ordre suggéré :

```text
UI-CUSTOM

Modern Wait Menu
Vel'Dun UI
Vel'Dun UI Patches
Vel'Dun UI Overhauls
```

### The Dragonborn's Bestiary

Si **The Dragonborn's Bestiary** est installé et que vous utilisez un écran 16:9, le choix Overhauls validé était :

```text
2A. Bestiary Patch
```

Le skin Bestiary de Vel'Dun a été observé en fonctionnement en jeu.

Pour un autre format d'image, choisissez l'option adaptée à votre configuration.

### Quest Journal

Si votre configuration contient uniquement **Knotwork for SkyUI V5** et ne contient **pas** Quest Journal Overhaul, choisissez :

```text
Quest Journal
→ Skip
```

Si Quest Journal Overhaul est installé, sélectionnez plutôt l'option correspondant au mod réellement présent.

### Autres patchs facultatifs

Les options destinées à RaceMenu, QuickLoot ou à d'autres menus pris en charge ne doivent être installées que si le mod correspondant est présent.

> Adaptez le FOMOD de Vel'Dun à votre installation. Ne construisez pas votre installation autour de tous les patchs Vel'Dun disponibles.

---

## 8. Agencement MO2 générique

Un agencement communautaire simple peut ressembler à ceci :

```text
UI-CUSTOM
├─ Modern Wait Menu                 # facultatif
├─ Vel'Dun UI
├─ Vel'Dun UI Patches
└─ Vel'Dun UI Overhauls
```

Les autres mods d'interface peuvent rester ailleurs dans la pile NEFARAM normale, sauf si une option Vel'Dun précise exige leur placement près de ce bloc.

Le point important est la priorité relative des fichiers Vel'Dun, et non un numéro de séparateur précis.

---

## 9. Stratégie de résolution des conflits

Ne résolvez pas les conflits d'interface en laissant Vel'Dun tout écraser sans discernement.

### Vel'Dun doit normalement gagner

Pour les fonctionnalités sélectionnées dans Vel'Dun UI Overhauls, les fichiers visuels SWF/interface fournis par Vel'Dun doivent généralement gagner.

Pendant la validation, les exemples comprenaient :

```text
sleepwaitmenu.swf
PlatformButtons.swf
bestiarymenu.swf
bestiarywidget.swf
favoritesmenu.swf
```

Ces fichiers ont été autorisés à gagner lorsque la fonctionnalité Vel'Dun correspondante avait été volontairement sélectionnée.

### Certains patchs fonctionnels NEFARAM peuvent devoir gagner

Un conflit de fichiers n'est pas automatiquement un problème.

Certains patchs NEFARAM existent pour la compatibilité fonctionnelle plutôt que pour l'apparence. Ne les écrasez pas aveuglément uniquement parce que Vel'Dun est installé plus bas.

Méthode recommandée :

1. ouvrez l'onglet **Conflicts** dans MO2 ;
2. identifiez le fichier écrasé ;
3. déterminez s'il est avant tout visuel ou fonctionnel ;
4. laissez Vel'Dun gagner l'élément visuel prévu ;
5. préservez les corrections fonctionnelles lorsqu'elles sont requises ;
6. testez le menu concerné en jeu.

---

## 10. Intégrations HUD facultatives

Vel'Dun n'exige pas une reconstruction complète du HUD.

Vous pouvez continuer d'utiliser votre pile préférée de HUD et widgets.

### Needs Widget AIO

**Needs Widget AIO** est un compagnon facultatif utile, car il propose un agencement qui s'intègre bien à Vel'Dun et peut centraliser les informations de besoins provenant de :

- **SunHelm**
- **Bathing in Skyrim**

Si vous utilisez Needs Widget AIO, un ancien widget complémentaire Bathing in Skyrim / Keep It Clean est généralement superflu et peut être désactivé afin d'éviter un double affichage des besoins.

Needs Widget AIO est **facultatif** et n'est pas requis par Vel'Dun.

### Autres composants HUD

Les systèmes HUD existants comme SkyHUD, TrueHUD, A Matter of Time, Oxygen Meter, Casting Bar, les widgets STB ou des outils similaires peuvent rester dans votre configuration.

Leur position, échelle et visibilité doivent être réglées selon votre résolution d'écran et vos préférences.

---

## 11. Liste de contrôle de validation en jeu

Après avoir installé Vel'Dun, testez l'interface avant de poursuivre une longue partie.

### Menus principaux

- [ ] Menu principal / système
- [ ] Menu Échap
- [ ] Inventaire
- [ ] Menu de magie
- [ ] Favoris
- [ ] Carte
- [ ] Console
- [ ] MCM
- [ ] Aperçu des objets SkyUI / positionnement des objets 3D

### Menus facultatifs

Ne testez ceux-ci que s'ils sont installés :

- [ ] Modern Wait Menu
- [ ] The Dragonborn's Bestiary
- [ ] Modifications de Quest Journal
- [ ] QuickLoot ou autres menus patchés

### HUD

- [ ] le HUD reste lisible
- [ ] aucun panneau invisible
- [ ] aucune icône manquante
- [ ] aucune police défectueuse
- [ ] aucun widget en double
- [ ] aucun chevauchement de widget important
- [ ] aucun conflit de saisie / raccourci

Enfin :

1. quittez complètement Skyrim ;
2. relancez le jeu ;
3. vérifiez que l'interface se charge toujours correctement ;
4. confirmez que les réglages HUD configurables persistent comme prévu.

---

## 12. Dépannage

### Le menu Échap / système est défectueux

Vérifiez d'abord la version du **paquet principal Vel'Dun UI**.

La version principale **1.0.7** a provoqué un problème avec le menu Échap dans l'environnement de test validé.

Revenez à :

```text
Vel'Dun UI main 1.0.6
```

et refaites un test.

Ne confondez pas cela avec un installateur **Vel'Dun UI Overhauls** qui peut lui-même afficher la version 1.0.7.

### Un menu ressemble encore à Dear Diary Dark Mode

Vérifiez la priorité des conflits dans le panneau gauche de MO2.

Assurez-vous que le fichier SWF ou d'interface Vel'Dun concerné gagne réellement.

Vérifiez également que la bonne option a été sélectionnée dans le FOMOD de Vel'Dun.

### Un menu patché manque ou est défectueux

Vérifiez que :

1. le mod d'origine est réellement installé ;
2. le patch Vel'Dun correspondant a été sélectionné ;
3. la bonne option de format d'image a été sélectionnée ;
4. aucun autre mod d'interface n'écrase ensuite le même fichier SWF.

### Widgets de besoins en double

Si vous utilisez **Needs Widget AIO**, désactivez les anciens widgets de besoins redondants lorsque c'est pertinent.

En particulier, un ancien addon de widget complémentaire **Keep It Clean / Bathing in Skyrim** n'est pas nécessaire lorsque Needs Widget AIO fournit déjà les informations requises de Bathing in Skyrim.

### Comportement étrange de l'interface après l'ajout de reskins facultatifs

Désactivez temporairement le reskin facultatif et refaites un test.

Vel'Dun lui-même doit être validé avant l'ajout de couches visuelles supplémentaires.

---

## 13. Statut de validation

Les éléments suivants ont été validés en jeu dans la configuration de référence basée sur NEFARAM :

- Vel'Dun UI main **1.0.6**
- Vel'Dun UI Patches **1.0.6**
- intégration de Vel'Dun UI Overhauls
- fonctionnement avec **SkyUI 5.2**
- fonctionnement avec **MCM Helper 1.5.0**
- apparence générale des menus
- intégration visuelle de Modern Wait Menu
- intégration visuelle du Bestiary
- utilisation de Vel'Dun comme gagnant visuel sur les fichiers d'interface concernés de la configuration d'origine / Dear Diary Dark Mode

Certaines fonctions de menus facultatifs, positions du HUD, dispositions de widgets et raccourcis restent dépendants de l'installation propre à chaque utilisateur.

> **Vel'Dun est validé comme méthode fonctionnelle de remplacement de l'interface de NEFARAM, mais les combinaisons d'interface facultatives doivent toujours être testées individuellement.**

---

## 14. Approche finale recommandée

Pour la plupart des utilisateurs de NEFARAM, la migration la plus sûre est :

```text
Conserver le système d'interface NEFARAM existant
        ↓
Conserver SkyUI 5.2 + MCM Helper 1.5.0
        ↓
Créer UI-CUSTOM
        ↓
Installer Vel'Dun UI 1.0.6
        ↓
Installer Vel'Dun UI Patches 1.0.6
        ↓
Installer uniquement les options Vel'Dun UI Overhauls requises
        ↓
Inspecter les conflits de fichiers dans MO2
        ↓
Laisser Vel'Dun gagner les éléments visuels prévus
        ↓
Tester en jeu chaque menu concerné
```

La migration reste ainsi réversible et évite les modifications inutiles du reste de la pile d'interface NEFARAM.

---

## Référence interne avancée

Les notes d'intégration détaillées utilisées pour élaborer ce guide communautaire sont disponibles ici :

[Notes internes d'intégration de Vel'Dun UI / HUD](../../../05%20-%20UI-HUD/VEL'DUN.md)
