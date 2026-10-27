# NEFARAM-Rhiven — Étude d’intégration de Naked Defeat 6.51

> **Statut : ÉTUDE CONCLUE — INTÉGRATION CŒUR VALIDÉE EN JEU**
>
> Cette fiche clôt l’étude préliminaire de Naked Defeat 6.51. Elle rassemble les contrôles MO2, l’audit xEdit, l’audit de cohérence Papyrus et les essais InGame effectivement réalisés sur le profil dédié.
>
> Naked Defeat 6.51 reste un **patch incrémental à installer sur Naked Defeat 6.50 FULL**. La validation porte sur le cœur de l’intégration Acheron → Bridge → Naked Defeat ; les cas rares, la défaite avec follower et les réglages fins du MCM restent réservés à la partie finale.

---

## 1. Objet et portée

Cette étude vise à :

- documenter le contenu annoncé de Naked Defeat 6.51 ;
- consigner son installation observée dans MO2 ;
- vérifier statiquement les plugins concernés dans xEdit ;
- déterminer l’état du **Naked Defeat - Rhiven Fix** avec la 6.51 ;
- documenter le conflit constaté avec `Synthesis_1.esp` ;
- isoler les erreurs xEdit qui nécessitent encore une analyse Papyrus ;
- préparer les essais en jeu sans déclarer prématurément la compatibilité.

Cette fiche valide le fonctionnement central observé de la chaîne Acheron → Bridge → Naked Defeat 6.51. Elle ne transforme pas en succès les cas non joués : les fonctions ciblées du changelog qui n’ont pas été reproduites, la défaite avec follower et les réglages fins MCM restent en suivi.

---

## 2. Référence et principe d’installation

### Environnement de référence

- **NEFARAM 17.3.8**
- Skyrim AE runtime **1.6.1170**
- Acheron **1.11.3**
- Naked Defeat **6.50 FULL**, puis patch **6.51**
- Mod Organizer 2
- xEdit / SSEEdit **4.1.5f**
- profil de test : `Eleanor 17.3.8 - Naked Defeat`

### Nature du paquet

Le paquet 6.51 est un **patch incrémental**. Il ne remplace pas l’installation complète de la 6.50 : il doit être installé **après Naked Defeat 6.50 FULL** et l’écraser.

Les captures MO2 montrent l’ordre suivant :

```text
Naked Defeat 6.50 FULL
└─ Naked Defeat 6.51 patch
   └─ Naked Defeat - Rhiven Fix
      └─ Acheron - Naked Defeat Bridge
```

Pour les plugins, l’ordre documenté reste :

```text
Naked Defeat.esp
Naked Defeat - Rhiven Fix.esp
Acheron - Naked Defeat Bridge.esp
...
Synthesis_1.esp
Naked Defeat - Synthesis Fix.esp
```

Le nouveau **Naked Defeat - Synthesis Fix.esp** doit être placé après `Synthesis_1.esp`.

> La seule sauvegarde autorisée pour la poursuite des essais est **Start NEFARAM**.

---

## 3. Changelog officiel 6.51 reçu

Les informations communiquées pour la 6.51 indiquent :

- une installation sous forme de patch incrémental sur **6.50 FULL** ;
- **AudioUtilTTS facultatif** ;
- des améliorations de la détection et des scènes ;
- des modifications ou améliorations concernant **Afterlife** ;
- des modifications ou améliorations concernant **NymBETA** ;
- des modifications ou améliorations concernant **Naked Falling** ;
- des modifications ou améliorations concernant **Tripping** ;
- des modifications ou améliorations concernant **Naked Curses** ;
- des modifications ou améliorations des pièges liés aux serrures et aux conteneurs.

Aucun détail supplémentaire n’est déduit au-delà de ce changelog reçu.

---

## 4. Contenu observé du patch 6.51

Le patch contient :

- `Naked Defeat.esp` ;
- des scripts Papyrus compilés `.pex` ;
- des fichiers `Interface` ;
- des fichiers JSON sous `SKSE` / `SLATE`.

Le patch 6.51 ne contient pas les sources Papyrus correspondantes.

Les sources de la 6.50 restent disponibles pour une analyse ultérieure, avec la réserve qu’elles ne permettent pas à elles seules de confirmer les changements internes des scripts compilés de la 6.51.

---

## 5. Masters de Naked Defeat 6.51

Sept masters sont présents :

1. `Skyrim.esm`
2. `Update.esm`
3. `SexLab.esm`
4. `Dragonborn.esm`
5. `Dawnguard.esm`
6. `SexLabAroused.esm`
7. `ZaZAnimationPack.esm`

Aucun master **AudioUtilTTS** n’est présent dans `Naked Defeat.esp`. Cela concorde avec son caractère facultatif annoncé, sans constituer à lui seul un test fonctionnel.

---

## 6. Résultats xEdit

### 6.1 Naked Defeat.esp

- **800 records**
- **18 erreurs** signalées par Check for Errors

Ces erreurs ne sont pas toutes considérées comme des corrections automatiques à effectuer. Les références et scènes ci-dessous ont été isolées pour analyse.

### 6.2 Naked Defeat - Rhiven Fix.esp

- **5 records**
- **0 erreur**

Le plugin contient son en-tête et quatre overrides :

- ARMA `WristChains R` ;
- ARMA `WristChains L` ;
- WEAP `Stick` ;
- WEAP `BoneMace`.

Les quatre overrides restent applicables avec la 6.51 :

- les deux ARMA corrigent deux références REFR incorrectes dans **Additional Races** ;
- les deux WEAP corrigent un champ **CRDT - Effect** vide en le remplaçant par `NULL`.

Le Rhiven Fix n’est donc pas rendu obsolète par les observations xEdit effectuées sur la 6.51.

### 6.3 Acheron - Naked Defeat Bridge.esp

- **3 records**
- **0 erreur**

Aucune erreur xEdit n’a été relevée dans le Bridge. Ce résultat est un contrôle statique et ne valide pas encore son fonctionnement en jeu avec la 6.51.

---

## 7. Conflit avec Synthesis et correctif dédié

`Synthesis_1.esp` écrase la correction **CRDT - Effect = NULL** appliquée à `nade_Stick`.

Un nouveau plugin a donc été créé :

> **Naked Defeat - Synthesis Fix.esp**

Il doit être chargé après `Synthesis_1.esp` et conserver pour `nade_Stick` :

- **CRDT - Effect** : `NULL` ;
- **TNAM** : le son original de Naked Defeat.

Le contrôle final explicite de ce nouveau patch n’a pas été consigné dans les essais reçus. Son état reste donc **à vérifier** et il n’est pas compté parmi les éléments validés en jeu.

---

## 8. Références manquantes et décisions provisoires

### 8.1 Référence A90E2541

La référence manquante `A90E2541` apparaît dans :

- `nade_CrimeEffect` → VMAD → propriété `qst2` ;
- `nade_RapeForceGreet` → QNAM ;
- `nade_RQDV0` → QNAM.

En l’absence d’une quête valide identifiée pour cette référence, la décision demeure :

> **Maintenir `IndecencyRapeProb = 0`.**

Ce réglage ne doit pas être réactivé avant que le chemin concerné ait été compris et validé.

### 8.2 Référence A90008D7 et branche whipping

La référence manquante `A90008D7` apparaît dans le champ QNAM de :

- `nade_WhipAction_01` ;
- `nade_WalkTo_01`.

Cependant :

- la scène `nade_WhipQuest_01_scene` pointe vers la quête valide `nade_WhipQuest_01 [A90059F4]` ;
- cette scène utilise les deux packages `nade_WhipAction_01` et `nade_WalkTo_01` ;
- la branche 02, `nde_WhipAction_02`, possède un QNAM valide `A90059E0`.

L’anomalie de la branche 01 n’est pas corrigée. La lecture des sources Papyrus disponibles pour la 6.50 indique que la logique actuelle de whipping ne semble pas s’appuyer sur ces anciens packages ; la 6.51 ne fournissant que les scripts compilés modifiés, cette conclusion reste une analyse de cohérence et non une preuve de suppression interne.

> **Décision maintenue : ne pas modifier ces records sans symptôme InGame reproductible.**

### 8.3 Scènes follower

Des scènes historiques `crux`, `crux2` et `crux3` liées aux followers ont également été signalées par xEdit. Dans les sources Papyrus disponibles, leurs appels sont désactivés ou commentés ; `cruxSAVE` apparaît comme une sauvegarde de développement sans référence active.

Aucune correction n’a été appliquée. La défaite avec follower n’ayant pas été validée InGame, ces anomalies restent documentées et surveillées.

---

## 9. Audit de cohérence Papyrus

Le patch 6.51 fournit des scripts Papyrus compilés `.pex`, mais pas leurs sources correspondantes. L’audit n’a donc pas prétendu reconstituer ligne par ligne les changements internes de la 6.51.

Le contrôle a consisté à :

- inspecter le flux du Bridge, qui envoie `StartNakedDefeatExternal` avec jusqu’à six assaillants ;
- recouper les propriétés VMAD et les records signalés par xEdit avec les sources Papyrus disponibles de la 6.50 ;
- vérifier que la récupération Acheron prévue par les scripts utilise les chemins de libération d’acteurs attendus ;
- distinguer les anomalies historiques inactives des chemins encore appelés ;
- confirmer par les essais InGame que le handoff, la fin de scène et la récupération fonctionnent réellement en 6.51.

Résultats et limites :

- le Bridge reste un adaptateur léger et son plugin conserve **0 erreur xEdit** ;
- la propriété `qst2` de `nade_CrimeEffect` pointe toujours vers la quête Civilian Rape absente : `IndecencyRapeProb = 0` reste obligatoire ;
- les anciens packages de whipping et les anciennes scènes follower restent volontairement intacts faute de chemin actif démontré ;
- aucune décompilation complète des `.pex` 6.51 n’est revendiquée ;
- aucune anomalie historique n’est déclarée corrigée simplement parce que le cœur du gameplay a passé les tests.

---

## 10. État des contrôles

### Validé

- [x] nature incrémentale du patch et base 6.50 FULL documentées ;
- [x] ordre MO2 observé et masters vérifiés ;
- [x] `Naked Defeat.esp` 6.51 contrôlé dans xEdit : **800 records, 18 signalements audités** ;
- [x] Rhiven Fix contrôlé : **5 records, 0 erreur**, quatre overrides toujours pertinents ;
- [x] Acheron Bridge contrôlé : **3 records, 0 erreur** ;
- [x] conflit de `Synthesis_1.esp` sur `nade_Stick` identifié et correctif séparé créé ;
- [x] propriétés VMAD, anciens packages et scènes historiques recoupés avec les sources Papyrus disponibles ;
- [x] chaîne Acheron → Bridge → Naked Defeat 6.51 validée InGame sur le profil dédié ;
- [x] récupération du bleedout, retour des contrôles, répétition d’événements et sauvegarde/rechargement validés ;
- [x] évasion d’un furniture confirmée : une pression sur Espace, attente des messages de progression, puis dernière pression lorsque les liens sont assez lâches.

### Non validé ou restant en suivi

- [ ] contrôle final explicite de `Naked Defeat - Synthesis Fix.esp` ;
- [ ] défaite avec follower ;
- [ ] fonctions du changelog 6.51 non reproduites individuellement (Afterlife, NymBETA, Naked Curses et pièges selon les cas) ;
- [ ] validation fonctionnelle exhaustive de toute la chaîne TTS ;
- [ ] cas rares et longue durée de la partie définitive ;
- [ ] réglages fins et équilibrage du MCM, volontairement réservés à la partie finale.

---

## 11. Tests InGame et couverture

Les essais ont été conduits depuis le profil/socle **Start NEFARAM** prévu pour cette intégration.

### Confirmé InGame

- défaite par humanoïde ;
- défaite par créature ;
- déclenchement de Naked Defeat via l’Acheron Bridge ;
- fin de scène et sortie correcte du bleedout Acheron ;
- retour des contrôles et absence de pacification permanente observée ;
- plusieurs défaites dans une même session ;
- sauvegarde après événement terminé, fermeture complète, rechargement et poursuite normale ;
- mécanique d’évasion des furnitures avec progression affichée et pression finale sur Espace.

### Resté hors validation

- défaite avec follower ;
- validation séparée de chaque fonction annoncée par le changelog 6.51 ;
- contrôle final documenté du Synthesis Fix ;
- réglages fins du MCM et équilibrage de la partie finale.

Le verdict ne couvre donc pas « tout Naked Defeat », mais bien le socle nécessaire pour retenir le patch 6.51 dans l’architecture NEFARAM-Rhiven.

---

## 12. Sécurité et rollback

Jusqu’au verdict final :

- conserver Naked Defeat 6.50 FULL et ses archives ;
- conserver le patch 6.51 séparé dans MO2 ;
- conserver le Rhiven Fix sans le fusionner dans `Naked Defeat.esp` ;
- conserver le Synthesis Fix comme plugin séparé ;
- maintenir `IndecencyRapeProb = 0` ;
- ne pas corriger automatiquement les références manquantes ou les scènes signalées ;
- ne pas utiliser de sauvegarde autre que **Start NEFARAM** pour les essais ;
- sauvegarder l’ordre des mods et des plugins avant les tests ;
- revenir à la chaîne 6.50 si la récupération, les contrôles, les acteurs ou la sauvegarde sont bloqués.

---

## 13. Verdict final de l’étude

> **NAKED DEFEAT 6.51 VALIDÉ POUR L’INTÉGRATION CŒUR — PLAYTEST ÉTENDU EN COURS**
>
> L’audit xEdit confirme la continuité du Rhiven Fix et l’absence d’erreur dans le Bridge. L’audit de cohérence Papyrus explique les anomalies historiques sans les « nettoyer » arbitrairement, tout en maintenant `IndecencyRapeProb = 0` pour la quête Civilian Rape absente.
>
> Les essais InGame confirment le handoff Acheron → Bridge → Naked Defeat 6.51, la récupération, les événements répétés, la sauvegarde/rechargement et l’évasion des furnitures. Les éléments non testés restent explicitement ouverts.
>
> Le patch 6.51 est donc retenu. Les réglages fins du MCM, l’équilibrage et les cas rares seront traités pendant la partie finale.

---

*Étude conclue — NEFARAM-Rhiven.*
