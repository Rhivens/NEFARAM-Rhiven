# NEFARAM-Rhiven — Étude préliminaire d’intégration de Naked Defeat 6.51

> **Statut : AUDIT xEdit PRÉLIMINAIRE ACHEVÉ — COMPATIBILITÉ EN JEU NON VALIDÉE**
>
> Cette fiche consigne uniquement les informations fournies avec le patch 6.51, les observations faites dans MO2 et les résultats du contrôle xEdit réalisé.
>
> Naked Defeat 6.51 est un **patch incrémental à installer sur Naked Defeat 6.50 FULL**. La configuration 6.50 demeure la référence de retour arrière tant que l’audit Papyrus et les essais en jeu ne sont pas terminés.

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

Cette fiche ne valide ni la stabilité en partie, ni la compatibilité complète de la chaîne Acheron → Bridge → Naked Defeat 6.51.

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

Le contrôle final de ce nouveau patch n’a pas été explicitement confirmé. Son état doit donc rester **à vérifier** avant validation.

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

L’anomalie de la branche 01 n’est pas corrigée à ce stade. Elle peut correspondre à une branche inachevée ou à une erreur, mais aucune de ces hypothèses n’est retenue sans analyse des scripts.

> **Décision : attendre l’analyse Papyrus avant toute modification.**

### 8.3 Scènes follower

Des scènes liées aux followers ont également été signalées par xEdit.

Aucune correction n’a été appliquée : leur rôle et leur chemin d’exécution doivent être examinés lors de l’audit Papyrus, puis vérifiés en jeu.

---

## 9. État des contrôles

### Terminé

- [x] nature incrémentale du patch documentée ;
- [x] base 6.50 FULL requise consignée ;
- [x] ordre MO2 observé consigné ;
- [x] contenu principal de l’archive 6.51 relevé ;
- [x] masters de `Naked Defeat.esp` vérifiés ;
- [x] Check for Errors de `Naked Defeat.esp` exécuté ;
- [x] Check for Errors du Rhiven Fix exécuté ;
- [x] quatre overrides du Rhiven Fix vérifiés ;
- [x] Check for Errors de l’Acheron Bridge exécuté ;
- [x] conflit `Synthesis_1.esp` sur `nade_Stick` identifié ;
- [x] nouveau `Naked Defeat - Synthesis Fix.esp` créé et placé après Synthesis ;
- [x] références manquantes principales et scènes concernées consignées.

### À vérifier ou à réaliser

- [ ] contrôle final explicite de `Naked Defeat - Synthesis Fix.esp` ;
- [ ] décompilation et audit comparatif des scripts Papyrus ;
- [ ] analyse de la référence `A90E2541` et des chemins Civilian Rape ;
- [ ] analyse de la référence `A90008D7` dans la branche whipping 01 ;
- [ ] analyse des scènes follower signalées ;
- [ ] vérification fonctionnelle d’AudioUtilTTS facultatif si nécessaire ;
- [ ] tests de la chaîne Acheron → Bridge → Naked Defeat 6.51 ;
- [ ] tests ciblés des fonctions citées dans le changelog ;
- [ ] tests de non-régression ;
- [ ] verdict de compatibilité.

---

## 10. Plan de tests en jeu

Les essais doivent être effectués uniquement depuis **Start NEFARAM**.

### Socle de non-régression

- [ ] défaite par humanoïde ;
- [ ] défaite par créature ;
- [ ] défaite avec follower ;
- [ ] transmission correcte des assaillants par le Bridge ;
- [ ] lancement et fin correcte d’une scène Naked Defeat ;
- [ ] sortie correcte du bleedout Acheron ;
- [ ] retour normal des contrôles ;
- [ ] libération correcte des assaillants ;
- [ ] absence de pacification permanente ;
- [ ] stripping et conséquences d’inventaire ;
- [ ] absence d’animation bloquée ;
- [ ] plusieurs défaites dans la même session ;
- [ ] sauvegarde après un événement terminé ;
- [ ] fermeture complète du jeu ;
- [ ] rechargement et poursuite normale de la partie.

### Cas ciblés 6.51

- [ ] détection et sélection des scènes ;
- [ ] Afterlife ;
- [ ] NymBETA ;
- [ ] Naked Falling ;
- [ ] Tripping ;
- [ ] Naked Curses ;
- [ ] pièges de serrures ;
- [ ] pièges de conteneurs ;
- [ ] branche whipping 01 ;
- [ ] scènes follower signalées ;
- [ ] comportement avec `IndecencyRapeProb = 0` ;
- [ ] vérification en jeu de `nade_Stick` avec le Synthesis Fix.

---

## 11. Sécurité et rollback

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

## 12. Verdict provisoire

> **AUDIT xEdit PRÉLIMINAIRE ACHEVÉ — COMPATIBILITÉ EN JEU NON VALIDÉE**
>
> Naked Defeat 6.51 s’installe comme patch incrémental au-dessus de la 6.50 FULL. Le Rhiven Fix reste nécessaire au vu des quatre corrections toujours observées. L’Acheron Bridge ne présente pas d’erreur xEdit. Un conflit de `Synthesis_1.esp` avec la correction CRDT de `nade_Stick` a nécessité un nouveau **Naked Defeat - Synthesis Fix.esp**, dont le contrôle final reste à confirmer.
>
> Les références manquantes `A90E2541` et `A90008D7`, ainsi que les scènes follower signalées, ne sont pas corrigées sans analyse Papyrus. `IndecencyRapeProb` doit rester à `0`.
>
> Aucun verdict de compatibilité ne sera prononcé avant l’audit Papyrus et les tests en jeu depuis **Start NEFARAM**.

---

*Fiche d’étude préliminaire — NEFARAM-Rhiven.*
