# Naked Defeat pour NEFARAM-Rhiven

Ce guide décrit la configuration validée de **Naked Defeat 6.50** utilisée avec **NEFARAM-Rhiven 17.3.8**.

Il s'agit d'un guide communautaire pratique : il contient les informations nécessaires pour reproduire la configuration fonctionnelle, sans reprendre l'intégralité de l'audit interne xEdit et des scripts.

## Base de référence validée

Cette configuration a été validée avec :

- **NEFARAM-Rhiven 17.3.8**
- **Skyrim AE runtime 1.6.1170**
- **Acheron 1.11.3**
- **Naked Defeat 6.50**
- **Mod Organizer 2**
- **Open Animation Replacer**
- **Pandora Behaviour Engine+**

## Architecture cible

```text
Acheron
→ Acheron - Naked Defeat Bridge
→ Naked Defeat
→ Naked Defeat - Rhiven Fix
```

Responsabilités :

- **Acheron** détecte la défaite et gère l'état de l'acteur vaincu / en bleedout.
- **Acheron - Naked Defeat Bridge** transmet le joueur vaincu et ses assaillants à Naked Defeat.
- **Naked Defeat** gère les scènes, conséquences et la récupération après la défaite.
- **Naked Defeat - Rhiven Fix** corrige quatre records mal formés dans Naked Defeat 6.50.

Le principe recherché est le suivant :

> **Acheron gère la détection de la défaite et l'état des acteurs ; Naked Defeat gère les conséquences et les scènes.**

## Fichiers utilisés

### Requis

- `Naked Defeat 6-50 - FULL - (AE + SE).7z`
- `Naked Defeat - EXTRA - Acheron Bridge (SE).zip`
- `Naked Defeat - Rhiven Fix.zip`

### Paquet OAR conservé

- `Naked Defeat - EXTRA - OAR Bowed Animations - fixed.7z`

### Paquet OAR à ne pas utiliser avec Bowed

- `Naked Defeat - EXTRA - OAR Crawl Animations V2.7z`

Le paquet Bowed recouvre largement Crawl. La configuration Rhiven validée conserve donc :

> **Bowed actif / Crawl désactivé**

## Configuration MO2

### À conserver activé

Bloc fonctionnel simplifié :

```text
Acheron - Death Alternative 1.11.3
Acheron - Sacrosanct Patch
Acheron - Simple Recover
Acheron - Diary of Mine Extension

Naked Defeat
Naked Defeat - Rhiven Fix
Acheron - Naked Defeat Bridge
Naked Defeat - EXTRA - OAR Bowed Animations fixed
```

Si Sacrosanct fait partie de votre installation, conservez `Acheron - Sacrosanct Patch` activé à cet emplacement. Il appartient à la pile NEFARAM-Rhiven validée.

### À désactiver

```text
Yamete Kudasai
Practical Defeat Reanimated
Practical Defeat Reanimated Voicepack
Naked Defeat - EXTRA - OAR Crawl Animations V2
```

Important :

> Désactivez le **mod MO2 Yamete Kudasai entier**, pas seulement `YameteKudasai.esp`.

Yamete Kudasai fournit également des fichiers YAML de conséquences Acheron. Laisser ces fichiers actifs tout en désactivant uniquement l'ESP peut conserver des issues Acheron concurrentes ou défectueuses.

Practical Defeat et Naked Defeat sont tous deux des systèmes complets de conséquences après une défaite. Les exécuter simultanément rend le propriétaire de l'événement de défaite ambigu et peut produire des résultats incohérents.

## Ordre des plugins validé

Placement testé :

```text
SLNights.esp
Naked Defeat.esp
Naked Defeat - Rhiven Fix.esp
Acheron - Naked Defeat Bridge.esp
BaboInteractiveDia.esp
```

Ordre interne essentiel :

```text
Naked Defeat.esp
→ Naked Defeat - Rhiven Fix.esp
→ Acheron - Naked Defeat Bridge.esp
```

Rhiven Fix doit charger après `Naked Defeat.esp` afin que ses records corrigés gagnent les conflits. Acheron Bridge charge ensuite après les deux en tant que couche d'intégration.

> Ne triez pas aveuglément avec LOOT un ordre de chargement NEFARAM finalisé. Préservez l'ordre relatif testé, sauf si vous avez vous-même vérifié les overrides obtenus.

## Premier lancement

Lors du premier lancement :

1. Ouvrez le MCM de Naked Defeat.
2. **Activez d'abord Naked Defeat.**
3. Configurez seulement ensuite les raccourcis et les autres options.

Si Naked Defeat n'est pas lui-même activé, la réaffectation des raccourcis peut sembler ne pas fonctionner.

## Réglages obligatoires

Dans le MCM de Naked Defeat :

- définissez **Defeat on Bleedout = OFF** lorsque vous utilisez Acheron Bridge ;
- définissez **IndecencyRapeProb = 0**.

### Pourquoi Defeat on Bleedout doit être sur OFF

Acheron possède déjà la transition de défaite / bleedout. Autoriser Naked Defeat à se déclencher indépendamment lors du bleedout créerait deux systèmes essayant de gérer le même événement.

### Pourquoi IndecencyRapeProb doit être égal à 0

Naked Defeat 6.50 contient encore dans un script une référence à une quête **Civilian Rape** manquante.

La solution de contournement actuelle la plus sûre est :

```text
IndecencyRapeProb = 0
```

N'essayez pas de reconstruire manuellement la quête manquante.

## Pandora et OAR

Une régénération de Pandora est nécessaire après la désactivation de Yamete Kudasai, car YK contient des ressources de comportements / animations et une liste FNIS.

Après avoir désactivé YK :

1. vérifiez que le bon profil MO2 est actif ;
2. régénérez Pandora ;
3. vérifiez qu'aucune erreur bloquante n'est signalée pendant la génération.

Le paquet **OAR Bowed Animations fixed** ne nécessite pas à lui seul une régénération de Pandora puisqu'il s'agit d'un paquet de remplacement OAR.

Utilisez :

> **OAR Bowed actif / OAR Crawl désactivé**

car les deux paquets se recouvrent largement.

## Naked Defeat - Rhiven Fix

Téléchargement :

**[Naked Defeat - Rhiven Fix.zip](../Naked%20Defeat%20-%20Rhiven%20Fix.zip)**

Le ZIP est prêt pour MO2 et contient :

```text
Naked Defeat - Rhiven Fix/
├─ Naked Defeat - Rhiven Fix.esp
└─ meta.ini
```

Le patch ne corrige volontairement que quatre records.

### Records ARMA des chaînes de poignets

- `nade_WristChains_L`
- `nade_WristChains_R`

Tous deux contenaient des entrées `REFR` invalides sous `Additional Races`. Ces entrées invalides sont supprimées.

### Records d'armes

- `nade_BoneMace`
- `nade_Stick`

Tous deux contenaient un champ mal formé :

`CRDT - Critical Data > Effect`

Rhiven Fix normalise ce champ en :

`NULL - Null Reference [00000000]`

Aucune statistique d'arme ni valeur de gameplay n'est modifiée.

### Validation

`Naked Defeat - Rhiven Fix.esp` :

- **5 records traités**
- **0 erreur xEdit**

Conservez le patch comme plugin autonome. Ne le fusionnez **pas** dans `Naked Defeat.esp`.

## Smoke test recommandé

Si possible, utilisez un profil MO2 cloné et une sauvegarde de test jetable avant d'appliquer la modification à votre partie principale.

Vérifications minimales :

- défaite face à un humanoïde ;
- défaite face à une créature ;
- Naked Defeat démarre par l'intermédiaire d'Acheron Bridge ;
- le joueur quitte proprement l'état de bleedout d'Acheron ;
- les contrôles du joueur sont rendus normalement ;
- les assaillants sont libérés et ne restent pas pacifiés définitivement ;
- déclenchez une autre défaite au cours de la même session ;
- sauvegardez après un événement de défaite terminé ;
- quittez complètement Skyrim ;
- rechargez cette sauvegarde ;
- vérifiez que le gameplay normal fonctionne encore après le rechargement.

Le simple démarrage réussi d'une scène ne suffit pas. Le joueur doit également récupérer proprement de l'état de défaite d'Acheron.

## En cas de problème

Enquêtez avant de considérer la configuration comme stable si l'un de ces problèmes devient reproductible :

- le joueur reste en bleedout ;
- les contrôles ne reviennent jamais ;
- les assaillants restent pacifiés définitivement ;
- Acheron Bridge se déclenche, mais Naked Defeat ne démarre pas ;
- une deuxième défaite ne fonctionne plus ;
- sauvegarder / recharger casse la chaîne de défaite.

## Nettoyage des anciennes entrées MCM

Après avoir complètement désactivé Yamete Kudasai et Practical Defeat, d'anciennes entrées MCM vides peuvent subsister dans une sauvegarde existante.

Un rafraîchissement des MCM SkyUI peut supprimer ces menus obsolètes :

```text
setstage ski_configmanagerinstance 1
```

N'utilisez cette commande qu'après avoir entièrement désactivé les anciens mods.

## Statut de validation

### Validé

- défaite face à un humanoïde ;
- défaite face à une créature ;
- transmission Acheron → Naked Defeat ;
- récupération après bleedout ;
- événements de défaite répétés ;
- sauvegarde / sortie / rechargement après des événements terminés.

### Toujours en attente / tests prolongés

- défaite des followers ;
- réglages MCM définitifs ;
- verdict final pour le profil stable ;
- cas limites moins courants pendant la partie définitive.

Statut actuel :

> **GAMEPLAY PRINCIPAL VALIDÉ — TESTS PROLONGÉS EN COURS**

## Observation mineure connue

### Bathing in Skyrim / Golden Shower

La transmission de Naked Defeat peut déclencher correctement l'animation de nettoyage de Bathing in Skyrim, mais les couches visuelles de saleté / fluides peuvent ne pas toujours être retirées selon la configuration environnante.

Ce problème est actuellement considéré comme **non bloquant**.

## Retour arrière

Tant que la configuration ne vous satisfait pas :

- conservez Yamete Kudasai installé, mais désactivé ;
- conservez Practical Defeat Reanimated installé, mais désactivé ;
- conservez le voicepack Practical Defeat installé, mais désactivé ;
- conservez OAR Crawl installé, mais désactivé ;
- conservez une sauvegarde de l'ordre du panneau gauche de MO2 et de l'ordre des plugins.

Si la configuration échoue à vos propres tests, restaurez la pile de défaite précédente plutôt que de modifier `Naked Defeat.esp` de manière destructive.

## Notes techniques avancées

Pour l'audit interne complet, le raisonnement xEdit, l'inspection du bridge, le protocole de test détaillé et les records inutilisés / mal formés connus, consultez :

[Guide interne d'intégration de Naked Defeat dans NEFARAM-Rhiven](../../../06%20-%20GAMEPLAY/NAKED%20DEFEAT/NAKED-DEFEAT-INTEGRATION.md)
