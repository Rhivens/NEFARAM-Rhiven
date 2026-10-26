# Naked Defeat AE/SE 6.50 FULL — Guide FR

> **Référence technique NEFARAM Rhiven**  
> Version documentée : **Naked Defeat 6.50 FULL**  
> Ce fichier Markdown est conçu pour une lecture rapide, la recherche dans GitHub et nos futurs audits techniques.  
> Le document Word reste la version illustrée / lisible “humaine”.

---

## Sommaire

- [Présentation](#présentation)
- [État général des versions récentes](#état-général-des-versions-récentes)
- [Installation](#installation)
- [Mise à jour](#mise-à-jour)
- [Désinstallation](#désinstallation)
- [Prérequis stricts](#prérequis-stricts)
- [Prérequis fortement recommandés](#prérequis-fortement-recommandés)
- [Dépendances souples et bridges](#dépendances-souples-et-bridges)
- [Compatibilités et incompatibilités](#compatibilités-et-incompatibilités)
- [Réglages MCM problématiques](#réglages-mcm-problématiques)
- [FAQ / dépannage](#faq--dépannage)
- [Changelog 6.50 FULL](#changelog-650-full)

---

# Présentation

**Naked Defeat AE/SE** est un mod de type *Defeat* très complet centré sur les situations où les **NPC battent le joueur**.

La branche récente inclut notamment un système de **Local Slavery à long terme**.

L’auteur indique que les versions récentes ont été largement retravaillées afin d’améliorer :

- la détection des coups et coups critiques ;
- la gestion du bleedout ;
- la fiabilité du démarrage des scènes ;
- la sélection des acteurs ;
- les transitions internes entre les différentes étapes du mod ;
- la gestion du ragdoll ;
- la stabilité générale lors des gros combats ;
- la facilité de configuration pour les nouveaux utilisateurs.

Support de l’auteur :  
❤️ https://www.patreon.com/nymra ❤️

---

# État général des versions récentes

## Version 6.40 et ultérieures

Évaluation donnée par l’auteur :

| Système | État annoncé |
|---|---:|
| Combat Hit / Critical Hit System | 85 % |
| Combat Bleedout | 75 % |
| Fiabilité de lancement des scènes | 80 % |
| Sélection des acteurs | 75 % |
| Transitions internes | 90 % |
| Petits bugs gênants | 85 % |
| Accessibilité pour débutants | 55 % |
| Gestion du ragdoll | 90 % |

### Remarques

- Le système de coups / coups critiques a été **complètement refondu** et accéléré dans les combats comportant beaucoup d’acteurs.
- Le bleedout a également été **complètement refondu**.
- La sélection des acteurs fonctionne correctement avec les acteurs vanilla et proches ; certains cas particuliers comme des créatures démoniaques peuvent encore être imparfaits.
- L’auteur a ajouté davantage de contrôles et de vérifications dans le mod et dans le MCM.
- Un effort important a été consacré à la compatibilité des animations et scènes avec le ragdoll.

## Version 5.xx et antérieures

L’auteur considère rétrospectivement ces anciennes versions comme moins fiables :

| Système | État annoncé |
|---|---:|
| Combat Hit / Critical Hit System | 20 % |
| Combat Bleedout | 30 % |
| Fiabilité de lancement des scènes | 50 % |
| Sélection des acteurs | 60 % |
| Transitions internes | 70 % |
| Petits bugs gênants | 40 % |
| Accessibilité pour débutants | 10 % |
| Gestion du ragdoll | 40 % |

Le mod restait globalement fonctionnel, mais certaines façons de jouer pouvaient révéler davantage de problèmes.

---

# Installation

1. Installer le mod comme n’importe quel autre mod Skyrim.
2. **Mod Organizer 2 est fortement recommandé** par l’auteur.
3. Laisser Naked Defeat **écraser ZAP Animation Pack** lorsque nécessaire : le mod contient certains remplacements d’animations, notamment pour des positions ligotées.
4. Dans le MCM :

   `MCM → System → Mod Enabled [x]`

5. Sauvegarder puis recharger la partie.

## Téléchargements EXTRA

Les téléchargements additionnels sont indépendants de la version principale du mod.

### EXTRA — Profiles JSON

Contient des fichiers JSON vierges afin d’éviter de devoir les laisser dans `Overwrite`.

### EXTRA — Crawl / Bowed

Nécessaire si l’on souhaite que le personnage puisse :

- ramper ;
- avancer courbé ;
- chercher un emplacement ;
- tenter de s’échapper avec ces postures.

### Textures

Des textures 1K sont incluses avec le mod principal.

Des variantes 2K / 4K sont disponibles séparément.

### BodySlide — FuckingBelts

Les fichiers BodySlide sont nécessaires uniquement si **The Amazing World of Bikini Armor** n’est pas déjà installé.

## Recommandations supplémentaires de l’auteur

L’auteur recommande notamment :

- **ZAZ No Collision Furnitures**
- son pack **Foreplay SLAL**

## Configuration SLATE

Après avoir enregistré les animations SLAL :

1. Ouvrir le MCM de **SLATE**.
2. Importer les actions depuis **OsmelMC Action Log**.
3. Importer les actions depuis **Nymra Action Log**.
4. Appliquer les actions importées.

Selon le nombre d’animations installées, l’auteur indique que cela peut représenter environ **2 000 à 3 000 actions**.

---

# Mise à jour

L’auteur essaie de rendre chaque nouvelle version de Naked Defeat aussi compatible que possible avec les sauvegardes existantes.

En règle générale :

- **pas besoin de nouvelle partie** ;
- **pas besoin de clean save**.

Si une version exige une nouvelle partie ou une procédure particulière, l’auteur indique qu’il le signalera clairement dans le changelog.

## FNIS / Pandora

Le changelog précise normalement lorsqu’une nouvelle exécution de FNIS/Pandora est nécessaire.

L’auteur indique qu’à sa connaissance, les fichiers FNIS n’ont pas été modifiés depuis les versions 3.xx.

## Ce qu’il ne faut normalement PAS faire

Il n’est généralement pas nécessaire de :

1. désinstaller Naked Defeat dans MO2 ;
2. lancer la sauvegarde ;
3. sauvegarder sans le mod ;
4. quitter ;
5. installer la nouvelle version.

> **Conseil de l’auteur :** ne perdez pas de temps à réparer quelque chose dont vous ne savez même pas s’il est cassé. En cas de doute, demander d’abord sur le thread de support.

---

# Désinstallation

> [!WARNING]
> **SE/AE : NE PAS SUPPRIMER L’ESP d’une sauvegarde existante.**

Le mod utilise du **Form 43** et l’auteur avertit que retirer l’ESP d’une sauvegarde peut provoquer une corruption de sauvegarde.

### Méthode recommandée

- Tester Naked Defeat sur une **nouvelle partie** ou un **profil copié**.
- Pour arrêter son fonctionnement sans retirer l’ESP :
  1. décocher / désactiver Naked Defeat dans son MCM ;
  2. sauvegarder ;
  3. recharger la partie.

Dans cet état, Naked Defeat ne fera plus rien mais réservera toujours un slot ESP.

---

# Prérequis stricts

Le mod est annoncé comme testé et fonctionnel sur :

- **Skyrim AE 1.6.1170**
- et devrait fonctionner sur des versions antérieures.

La compatibilité Legendary Edition n’est plus une priorité.

## SexLab

- **SexLab 1.66 + SLU+**
- ou **SexLab P+**

SexLab P+ peut encore présenter certaines incompatibilités mineures, notamment autour de certaines options de foreplay.

## ZaZ Animation Pack

Utiliser **ZaZ 8+**.

Versions mentionnées :

- CBBE / UUNP ;
- 3BA.

> [!IMPORTANT]
> L’auteur demande explicitement de ne pas utiliser les versions ZaZ 6.xx, 7.xx ou 9.xx pour cette configuration documentée.

Pour 3BA, certaines distributions nécessitent également **ZaZ 8+ DoggyBelt**.

L’auteur indique également :

- ne pas enregistrer les animations ZaZ dans SexLab ;
- ignorer les alertes génériques affirmant que ZaZ 8+ serait incompatible avec tout.

## Arousal

- **OSL Aroused Reborn**
- ou une autre version compatible de SL Aroused.

## Extenders

- **powerofthree’s Papyrus Extender**
- **Scrab’s Papyrus Extender** — requis depuis Naked Defeat 5.26
- **MfG Fix NG**

---

# Prérequis fortement recommandés

L’auteur les décrit techniquement comme des dépendances souples, mais considère qu’ils sont pratiquement indispensables pour profiter pleinement du mod.

> [!IMPORTANT]
> Naked Defeat est un mod complexe. Un load order instable, surchargé ou mal configuré peut révéler ses faiblesses de manière brutale.

## Frameworks / gameplay

- **Devious Devices NG 0.4.0**
- **Bathing in Skyrim Renewed 2.4.4+**  
  Particulièrement recommandé pour Local Slavery.
- **SLATE**  
  Très important pour les fonctions de foreplay et d’exécution.
- **SLAL — SexLab Animation Loader**

## Packs SLAL cités

### Billyy SLAL

Fortement recommandé pour de nombreux scénarios impliquant notamment Wheel / Yoke / Armbinder.

### Anubs SLAL

Même type d’intérêt pour plusieurs scénarios.

### BakaFactory SLAL (Babo)

Considéré par l’auteur comme un pack SLAL de base important.

### FunnyBizness SLAL

Contient beaucoup d’animations anciennes, mais aussi plusieurs animations uniques. Peut nécessiter davantage de travail de configuration.

### Proxie SLAL

> **REQUIS pour DEATH / EXECUTION.**

### Leito SLAL

Considéré comme un pack SLAL de base.

### Milky SLAL

Considéré comme un pack SLAL de base.

### Sailing Rebel SLAL

Pack compatible mentionné par l’auteur.

### Nymra SLAL Pack

> **REQUIS pour DEATH / EXECUTION.**

### Nymra Forced Foreplay SLAL Pack

Optionnel pour FOREPLAY.

Avec le nouveau Action Log SLATE de Nymra, ce pack peut devenir moins nécessaire.

### Nymra Golden Shower SLAL

N’est plus requis.

### NCK30 SLAL

Mentionné notamment pour le scénario **Girlfriend**.

### Psyche SLAL

Recommandé pour certaines animations de bondage, rough et furniture.

---

# Mods complémentaires recommandés

## Spank That Ass — Monoman1

Utilisé pour certaines actions de groping avec furniture.

## WetFunction Redux

Naked Defeat peut faire perdre de la stamina au personnage afin de déclencher certains effets WetFunction lors de situations déterminées.

## Simple Slavery Plus Plus

Peut être utilisé avec Naked Defeat.

Naked Defeat peut vendre le personnage comme esclave et gérer ensuite ses propriétaires.

## ZAP — No Collision Furnitures

Très fortement recommandé par l’auteur afin d’améliorer l’expérience avec les furnitures.

## ZAP — Faster in and out of furnitures

Également fortement recommandé.

## Slave Tattoos

Compatible / recommandé.

## Rape Tattoos Continued

Compatible / recommandé.

## Fade Tattoos Continued

Compatible / recommandé.

## RapeHands / WhipMarks

Pour que ces overlays fonctionnent correctement :

1. ouvrir le MCM de **RapeTats** ;
2. rechercher les entrées **RapeHands** et **WhipMarks** ;
3. vérifier leur statut ;
4. si elles sont définies sur **Excluded**, les passer à **Unassigned**.

---

# Dépendances souples et bridges

## Acheron

Télécharger le **Acheron Bridge** présent dans les téléchargements de Naked Defeat.

Puis désactiver dans Naked Defeat :

`Defeat on Bleedout`

afin d’éviter que les deux systèmes ne gèrent le même événement.

## Devious Enchanted Chests

Fonctionne bien avec l’option **Naked Loot**.

L’auteur travaille également sur un système de pièges utilisant Devious Chests.

---

# Compatibilités et incompatibilités

## Mods nécessitant une configuration adaptée

### SexLab Defeat

Les deux mods couvrent des fonctions similaires.

L’auteur travaille / a travaillé sur un bridge de compatibilité.

Réglage conseillé :

- désactiver **NPC rapes Player** dans le MCM de SexLab Defeat.

### Cursed Loot

Désactiver la fonction de **combat defeat** de Cursed Loot.

Sans cela, elle risque de faire doublon avec Naked Defeat.

---

## Incompatibles ou fortement déconseillés

### SexLab Submit

Même type de fonction principale.

### Death Alternative — Your Money or Your Life

Même type de fonction.

Peut éventuellement fonctionner après réglages, mais l’auteur ne le garantit pas.

### Peril

Même type de fonction.

### Dragonborn in Distress

Même type de fonction.

---

## Problématiques

### Ultimate Combat

L’auteur indique qu’Ultimate Combat casse le système de whipping pour plusieurs mods.

Il recommande d’utiliser un autre mod de combat.

### Interactive BDSM

Ce mod verrouille lui-même le personnage dans certaines furnitures.

L’auteur n’a pas effectué de tests complets mais déconseille actuellement de l’utiliser avec Naked Defeat.

---

# Réglages MCM problématiques

## ZaZ Animation Pack

Dans son MCM, désactiver :

`Overwrite Bound Animations`

Cela peut notamment éviter des conflits avec **Shout Like a Virgin**.

## SexLab + SexLab Utility Plus

Désactiver le filtre :

`ZaZ Animation Filter`

Si des problèmes étranges surviennent avec les furnitures, tester également les options Furniture de SLU+ et les ajuster / désactiver si nécessaire.

---

# Walkthrough et raccourcis

La documentation complète du walkthrough ainsi que les raccourcis ont été déplacés par l’auteur dans le **PDF Guide** inclus dans l’archive téléchargée.

---

# FAQ / dépannage

## Où trouver le Papyrus.0.log ?

Tutoriel de l’auteur :

https://www.loverslab.com/topic/256333-papyrus-log-tutorial/

---

## Mon écran devient flou

C’est volontaire.

Le blur sert de transition entre certaines scènes et masque certains changements visuellement abrupts.

Le système a été pensé en particulier pour les utilisateurs ENB.

Pour le désactiver :

`MCM → System → Disable Blur [x]`

Si le blur reste bloqué :

`CTRL + ALT + K`

Puis signaler le problème sur le thread de support.

---

## La bouche reste ouverte

Procédure donnée par l’auteur :

1. installer Naked Defeat **6.4 ou ultérieur** ;
2. charger la sauvegarde ;
3. désactiver Naked Defeat ;
4. attendre 5 à 10 secondes ;
5. sauvegarder et recharger ;
6. attendre ;
7. réactiver Naked Defeat ;
8. attendre 5 à 10 secondes ;
9. sauvegarder et recharger de nouveau.

---

## SLATE / Action Log ne fonctionne pas

1. Vérifier que le dernier fichier `SLATE_ActionLog - Nymra.json` est installé et non écrasé.
2. Charger la sauvegarde.
3. Aller dans :

   `MCM → SLATE → SETTINGS → Import Action Log Files`

4. Sélectionner le fichier contenant **nymra**.
5. Quitter l’écran / valider.
6. Dans SLATE → Settings, utiliser :

   `Import Actions From file`

7. Puis :

   `Re-apply recorded actions`

8. Fermer le MCM.
9. **Sauvegarder puis recharger la sauvegarde.**
10. Vérifier le MCM de Naked Defeat : le statut attendu doit être **TRUE**.

---

## CTD avec X ou Y

L’auteur estime qu’un CTD n’est généralement pas directement causé par Naked Defeat.

Vérifications prioritaires :

- mauvais mesh ;
- charge script trop élevée ;
- installation incorrecte ;
- load order problématique.

Pour demander du support, joindre également un **papyrus.log**.

---

## Une scène ne démarre pas

Essayer :

- d’augmenter le rayon de recherche ;
- valeur recommandée par l’auteur : **5000 minimum** ;
- vérifier qu’aucune option nécessaire n’est désactivée ;
- vérifier que des packs SLAL compatibles sont bien installés.

Pour le support : joindre le **Papyrus log**.

---

## Mon personnage est invulnérable

Ouvrir la console :

```text
TGM
```

---

## SexLab Defeat / Babo Defeat / Bane Defeat

Désactiver l’option :

`NPC rapes player`

dans le MCM du mod concerné.

---

## Intégration SD+

Elle existe déjà.

Voir :

`MCM → Aftermath`

L’auteur indique qu’aucune intégration supplémentaire n’est prévue.

---

## Sauvegarde corrompue

Voir la section **Désinstallation**.

Ne pas retirer sauvagement l’ESP d’une sauvegarde existante.

---

## Un scénario ne progresse plus

- générer un `Papyrus.0.log` ;
- signaler le problème ;
- en urgence, utiliser :

`Alt + K → Abort All`

---

## Mon follower ne fonctionne pas

Dans le MCM :

1. saisir le nom du follower dans :

   `System → Named Follower`

2. utiliser :

   `Alt + K → Debug Wheel → Update Followers`

---

## Serana ne fonctionne pas

Même procédure :

1. saisir **Serana** dans `System → Named Follower` ;
2. `Alt + K → Debug Wheel → Update Followers`.

---

## Mes objets de quête ont été volés

Ce problème est censé être corrigé depuis les versions 5.xx.

Le signaler s’il se reproduit.

---

## Un objet XYZ est retiré / volé

Essayer de le placer dans les options de strip de SexLab comme objet à ne pas retirer.

Si cela ne fonctionne pas, signaler le problème.

---

## Un autre mod se déclenche quand je suis vaincu

L’auteur explique qu’il ne peut pas empêcher directement un autre mod d’écouter le même événement.

Il faut généralement :

- désactiver la fonction correspondante dans l’autre mod ;
- ou retirer le mod incompatible.

Des patches seraient possibles, mais chaque mise à jour de ces mods nécessiterait potentiellement une maintenance.

**SexLab Aroused Creatures** a notamment été connu pour ce genre de déclenchement, mais le problème devrait désormais être corrigé.

---

## Les furnitures n’apparaissent pas

Vérifier la version de ZaZ Animation Pack.

La configuration documentée attend **ZAP 8+**.

---

## Compatible avec ZAP 9.x ?

L’auteur pense que cela peut fonctionner si ZAP 9 est rétrocompatible, mais il n’a pas suffisamment travaillé avec cette version pour la garantir.

---

## Zoom caméra cassé / attaque désactivée

Essayer dans l’ordre :

1. console :

   ```text
   EPC
   ```

2. touche d’action **K**.

Ce problème peut arriver avec certains mods de free camera utilisant leur propre raccourci FlyCam.

Si un mod exécute :

`ConsoleUtil.ExecuteCommand("TFC")`

SexLab peut perturber l’état de caméra lorsqu’il force un retour en première / troisième personne.

Solutions proposées :

- utiliser le patch **ScreenShotAssist** de l’auteur ;
- utiliser un autre mod de caméra ;
- vérifier les scripts source du mod concerné.

---

## Contrôles désactivés / impossible de bouger

1. essayer `EPC` dans la console ;
2. essayer la touche **K** ;
3. si cela se produit après la fin d’un événement Naked Defeat, envoyer un `papyrus.0.log`.

Référence :

https://www.nexusmods.com/skyrim/articles/368

---

## Caméra bloquée derrière le personnage

Dégainer une arme puis la rengainer.

Les poings / le mode non armé ne fonctionnent pas pour cette méthode.

Sinon :

`Alt + K → Debug Wheel → Unstuck Player`

ou :

`Alt + K → Debug Wheel → Fix Camera`

---

## Personnage qui tourne / caméra verrouillée

Utiliser :

- **Unstuck Player**
- **Fix Camera**

dans le Debug Wheel (`Alt + K`).

---

## Zoom molette impossible

Même procédure :

- **Unstuck Player**
- **Fix Camera**

---

## Le MCM n’apparaît pas

Effectuer les étapes dans l’ordre et ne passer à la suivante que si nécessaire.

### Étape 1

Console :

```text
ski_configmanagerinstance 1
```

### Étape 2

Placer `Naked Defeat.esp` vers la fin du load order ESP.

### Étape 3 — nouvelle partie

Installer / initialiser SexLab dans son MCM.

Attendre si nécessaire, puis :

- sauvegarder ;
- recharger ;
- vérifier l’apparition du MCM Naked Defeat.

### Étape 4 — partie existante

- voyager / faire quelques fast travels ;
- sauvegarder ;
- recharger.

### Étape 5

Installer **Jaxonz MCM Kicker SE**.

### Étape 6

Vérifier la santé générale du load order et si les autres MCM apparaissent correctement.

### Étape 7

Activer le logging Papyrus, lancer le jeu, puis fournir le `papyrus.0.log` si le MCM reste absent.

---

# Changelog 6.50 FULL

**Publication : 11 octobre**

## Installation / mise à jour

- supprimer tous les anciens patches ;
- version **FULL**, car beaucoup de temps s’est écoulé depuis la version précédente ;
- ajout de nouveaux fichiers son ;
- le sound design est actuellement une priorité de développement pour l’auteur ;
- **non compatible avec les community patches**, notamment certains patches SLP+ de crajjjj ;
- l’auteur prévoit d’intégrer progressivement leurs correctifs.

## SexLab P+

> **Pas de support spécial SexLab P+ à ce stade.**

SLPP n’est pas testé ni officiellement supporté, même s’il peut fonctionner avec certains problèmes.

---

## SLATE Action Log

Un nouvel Action Log SLATE a été créé.

Il est requis à partir de cette version.

Tag attendu :

`NymLogVersion021`

---

## Nouvelle option MCM — Dynamic Whipping

Ajoute une variation dynamique de la vitesse pendant les séquences de whipping.

Objectif : réduire la répétitivité.

---

## Nouvelle option MCM — Moan on Whip Cooldown

Le système de réactions vocales au hit lors du whipping a également été modifié.

Objectif :

- obtenir idéalement une réaction par coup ;
- éviter l’empilement de réactions longues.

Le cooldown est exprimé en unités où, selon l’auteur :

- **1 = 0,1 seconde**
- **10 = 1 seconde**

Une valeur trop élevée peut réduire fortement le nombre de réactions.

---

## Général

Améliorations annoncées :

- meilleures scènes de créatures pendant les défaites humaines ;
- meilleures scènes humaines pendant certaines défaites de créatures ;
- nombreux petits bugs corrigés ;
- corrections de timing ;
- transitions blur améliorées ;
- sélection d’acteurs accélérée ;
- sélection de scénarios améliorée ;
- correction d’un problème où des scènes échouées pouvaient être relancées trop tard pendant le capture game et figer le mod ;
- amélioration de la scène **Fast Travel Ritual**.

L’auteur précise que le travail sur la sélection d’acteurs / scénarios est toujours en cours.

---

# Local Slavery — changements 6.50

Nombreuses corrections de bugs.

## Show Respect to the Guards

Correction d’un problème avec cette tâche.

Pour qu’elle fonctionne :

- ne pas être trop loin ;
- ne pas être trop près ;
- faire face au garde **frontalement**.

Sinon, le personnage peut tenter une interaction différente, ce qui est volontaire.

## Fiabilité des tâches

L’auteur indique que les tâches devraient désormais fonctionner de manière plus fiable et répétable.

Certaines tâches peuvent encore mal correspondre au hold dans lequel le personnage est détenu. C’est toujours WIP.

## Nouvelles tâches

- travailler dans un champ sur une ferme proche ;
- travailler à la meule / **Mill Stone**.

Il est possible de faire apparaître certaines stations de crafting manquantes, car tous les holds ne possèdent pas forcément toutes les infrastructures requises.

## Exhaustion / Rest

Un système de fatigue / repos utilisant également la nourriture est en cours de développement.

Il n’est pas encore finalisé.

---

# Intégration progressive du patch crajjjj

État annoncé :

**environ 30 % implémenté**

L’auteur intègre le patch élément par élément.

Certaines corrections peuvent être adaptées différemment.

Une vérification complète est prévue une fois l’intégration terminée.

### Correctifs déjà intégrés / mentionnés

- la récupération du bleedout est restaurée lors de la libération / fin de Defeat ;
- **Unstuck** dans le debug wheel fonctionne réellement ;
- le démarrage de Defeat ne peut plus rester bloqué indéfiniment après un événement ragdoll manqué ;
- les chemins d’abandon du whipping ne laissent plus l’état du whipper actif ;
- corrections autour de certains types incorrects de `defeated by` provoqués par friendly fire ou des bystanders ;
- le second assaillant Acheron est ajouté correctement à la faction ennemie ;
- les whippers humanoïdes sont gérés dans `SelectWhipper()` ;
- les scene protectors sont de nouveau créés à chaque scène de whipping.

---

# Roadmap / travail de fond

> Ces éléments ne sont **pas encore implémentés publiquement** dans la version 6.50.

Travaux annoncés :

- **Local Slavery dans les donjons** pour humains — environ 50 % ;
- créatures et animaux prévus également ;
- invocation du cheval avec une carotte — environ 50 % ;
- scène adaptée associée ;
- système dynamique d’équipement de langue, dans l’esprit de SexLab Utility Plus ;
- stripping dynamique pendant Foreplay / SexStage 1 ;
- scènes spécialisées de strip pour créatures et animaux ;
- système de scènes sur furniture par placement hors fonction SexLab classique ;
- interactions de torture sur furnitures via assets placés.

---

# Notes NEFARAM Rhiven

Cette fiche est une **référence documentaire**, pas une validation automatique de compatibilité.

Avant toute modification de notre installation NEFARAM :

1. vérifier la version réellement installée de Naked Defeat ;
2. comparer les dépendances avec le load order actuel ;
3. contrôler les réglages SexLab / SLU+ / ZAZ / Acheron ;
4. vérifier les patches communautaires éventuellement présents ;
5. tester les changements sur un profil MO2 dédié si nécessaire.

---

*Document Markdown de référence — NEFARAM Rhiven.*
