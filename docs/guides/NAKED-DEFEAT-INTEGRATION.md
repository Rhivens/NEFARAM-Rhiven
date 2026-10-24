# Naked Defeat 6.50 — Intégration NEFARAM-Rhiven

**Baseline :** NEFARAM 17.3.8 / profil de test `Eleanor 17.3.8 - Naked Defeat`  
**Statut :** intégration technique validée, smoke test gameplay restant.

## Architecture retenue

Chaîne de défaite à tester :

**Acheron → Acheron - Naked Defeat Bridge → Naked Defeat**

À garder actifs :

- `Acheron - Death Alternative 1.11.3 - Rhiven`
- `Acheron - Sacrosanct Patch - Rhiven`
- `Acheron - Simple Recover`
- `Acheron - Diary of Mine Extension`
- `Naked Defeat - Rhiven`
- `Naked Defeat - Rhiven Fix`
- `Naked Defeat - EXTRA - Acheron Bridge (SE) - Rhiven`
- `Naked Defeat - EXTRA - OAR Bowed Animations fixed - Rhiven`

À désactiver pour le smoke test :

- `YameteKudasai` — mod MO2 complet
- `Practical Defeat Reanimated`
- `Practical Defeat Reanimated Voicepack`
- `Naked Defeat - EXTRA - OAR Crawl Animations V2 - Rhiven` — conservé comme rollback, mais décoché car Bowed remplace directement les mêmes fichiers OAR.

## Audit xEdit — Naked Defeat 6.50

Le plugin principal contient 798 records. Le Check for Errors initial a signalé 18 erreurs / warnings, dont plusieurs sont des résidus anciens ou des sous-systèmes manifestement abandonnés.

### Correctifs Rhiven retenus

Création de `Naked Defeat - Rhiven Fix.esp` avec seulement quatre overrides :

- `nade_WristChains_L`
- `nade_WristChains_R`
- `nade_BoneMace`
- `nade_Stick`

Corrections :

- suppression de deux références REFR invalides dans `Additional Races` des deux wrist chains ;
- normalisation automatique par xEdit du champ `CRDT > Effect` des deux armes vers `NULL - Null Reference [00000000]`.

Validation du patch :

- **5 records traités**
- **0 erreur**

### Résidus laissés volontairement intacts

- alias `Vehicle [ID12]` de `nade_CaptureQuest` : cible absente, mais source actuelle n'utilise plus cet alias ;
- anciens packages `nade_WhipAction_01` / `nade_WalkTo_01` : owner quest supprimée, non référencés par le flux actuel ;
- scènes follower `crux` / `crux2` / `crux3` : références anciennes, appels désactivés dans les sources actuelles ;
- `nade_TalkQuestNewBranch0` : branche de dialogue vide et non référencée.

Aucun nettoyage invasif n'est effectué sans symptôme en jeu.

## Civilian Rape — fonctionnalité incomplète

Le MGEF `nade_CrimeEffect` possède une propriété `qst2` pointant vers le FormID manquant `E40E2541`.

Les sources montrent que cette propriété correspond à la **Civilian Rape Quest** et qu'elle est encore appelée par `nade_crimeeffect_scr.psc`, alors que la quête correspondante n'existe plus dans l'ESP 6.50.

Deux autres records orphelins pointent vers cette même quête absente :

- `nade_RQDV0`
- `nade_RapeForceGreet`

Décision Rhiven :

> **Régler `IndecencyRapeProb = 0` dans le MCM Naked Defeat.**

Ne pas reconstruire artificiellement la quête manquante.

## Acheron Bridge

`Acheron - Naked Defeat Bridge.esp` :

- 3 records ;
- **0 erreur xEdit** ;
- quête `achnadeBridgeQuest` avec `PlayerRef` + six aliases assaillants ;
- après 0,5 s, le script envoie le ModEvent `StartNakedDefeatExternal` avec jusqu'à six assaillants puis arrête la quête.

Le bridge est retenu comme couche d'adaptation légère entre Acheron et Naked Defeat.

## OAR

### Crawl Animations V2

Structure OAR valide, mais ce pack est conservé décoché.

### Bowed Animations - fixed

Le pack remplace directement une grande partie des mêmes fichiers que Crawl dans `OpenAnimationReplacer/Naked Defeat Crawling`.

Conditions :

- priorité OAR très élevée ;
- `IsInFaction` sur `Naked Defeat.esp`, FormID `05AFF` ;
- donc remplacement limité à l'état Naked Defeat ciblé.

Décision : **Bowed actif, Crawl décoché**.

## Yamete Kudasai — raison de la désactivation

Les scripts YK montrent un chevauchement important avec Naked Defeat :

- conséquences Acheron après défaite ;
- scènes SexLab ;
- stripping / vol ;
- blackout / téléportation ;
- gestion followers ;
- humanoïdes / créatures ;
- surrender ;
- sorties vers Simple Slavery.

Les YAML de conséquences YK sont chargés par Acheron et peuvent entrer dans le tirage des conséquences avec le bridge Naked Defeat. Cela rendrait le smoke test non déterministe.

Décision :

> Désactiver le **mod MO2 complet YameteKudasai** pendant le test, pas seulement l'ESP.

Après validation, YK ne pourrait revenir que pour des fonctions spécifiques (Hunter's Pride / NPC defeat), avec ses conséquences Hostile/Surrender neutralisées. La préférence Rhiven actuelle est toutefois de le laisser désactivé pour garder une architecture plus simple.

## Practical Defeat — raison de la désactivation

Practical Defeat et Naked Defeat couvrent tous deux la chaîne principale de conséquences après défaite Acheron.

Décision :

> `Practical Defeat Reanimated` et son voicepack sont désactivés pour le smoke test.

Si Naked Defeat passe le test, Practical Defeat sera considéré comme remplacé dans le build Rhiven.

## Pandora

Yamete Kudasai contient des animations / behavior et une liste FNIS. Après sa désactivation :

> **Relancer Pandora avant le smoke test.**

Les deux packs OAR Naked Defeat, eux, ne nécessitent pas Pandora à eux seuls.

## Smoke test requis

Sur sauvegarde jetable / profil de test :

1. vérifier que `YameteKudasai.esp` et `Practical Defeat.esp` ne sont plus chargés ;
2. relancer Pandora ;
3. tester une défaite par humanoïde ;
4. tester une défaite par créature ;
5. tester une défaite avec follower ;
6. vérifier la fin de scène et la récupération ;
7. vérifier stripping / vol éventuel ;
8. vérifier l'absence de blocage permanent en bleedout ;
9. confirmer que les défaites passent bien par **Acheron → Bridge → Naked Defeat**.

## Verdict actuel

**TECHNIQUEMENT VALIDÉ / GAMEPLAY À TESTER**

La nouvelle architecture de référence est :

**Acheron = framework de défaite**  
**Acheron Bridge = transmission des assaillants**  
**Naked Defeat = conséquences / scènes**  
**Rhiven Fix = corrections xEdit ciblées**

Practical Defeat et Yamete Kudasai restent disponibles en rollback tant que le smoke test n'est pas terminé.
