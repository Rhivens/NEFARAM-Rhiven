# Captive Player 1.9 — Protocole de test d’intégration NEFARAM-Rhiven

> **Statut : INTÉGRATION ENVISAGÉE — VALIDATION EN JEU REQUISE**
>
> Cette fiche définit un protocole conservateur pour tester **Captive Player** sans lui confier directement les défaites Acheron. L’architecture validée de Naked Defeat reste prioritaire tant que tous les cas ci-dessous ne sont pas passés.

---

## 1. Objectif et limite de validation

L’objectif est d’évaluer Captive Player comme **destination de Simple Slavery++**, et non comme second gestionnaire général des défaites.

Principe retenu :

> **Naked Defeat reste le propriétaire exclusif des défaites Acheron.**

Captive Player doit rester installé et actif pour être disponible dans Simple Slavery++, mais son poids dans les conséquences Acheron doit être réglé à **0** pendant toute la première phase de test.

Cette fiche ne confirme pas encore :

- que Naked Defeat envoie effectivement chaque branche attendue vers Simple Slavery++ ;
- que Simple Slavery++ sélectionne Captive Player de façon fiable ;
- que le retour de Captive Player vers Simple Slavery++ ne peut pas former une boucle ;
- que toutes les intégrations Devious Devices et tatouages fonctionnent dans la configuration Rhiven actuelle.

Ces points sont précisément l’objet du protocole.

---

## 2. Architecture cible

### Chaîne principale de défaite à préserver

```text
Combat
  ↓
Acheron
  ↓
Acheron - Naked Defeat Bridge
  ↓
Naked Defeat
```

Captive Player ne doit pas apparaître comme conséquence directe de cette chaîne.

### Branche d’intégration à tester

```text
Naked Defeat
  ↓ branche éventuelle vers l’esclavage
Simple Slavery++
  ↓ destination sélectionnée
Captive Player
```

### Entrée de contrôle indépendante

```text
Simple Slavery++
  ↓ vente aux enchères de test
Captive Player
```

Cette entrée directe doit être validée avant le flux complet depuis une défaite.

---

## 3. Règles de sécurité du test

- Utiliser un **profil MO2 dédié** dérivé du profil Naked Defeat validé.
- Utiliser une **sauvegarde de test jetable**, créée avant l’entrée dans Simple Slavery++.
- Ne pas tester sur la sauvegarde principale.
- Ne pas désactiver Naked Defeat, son Bridge ou le Rhiven Fix pour faire fonctionner Captive Player.
- Ne pas augmenter le poids Acheron de Captive Player pendant cette campagne de test.
- Ne pas activer plusieurs nouvelles destinations Simple Slavery++ à la fois.
- Conserver les archives et réglages précédents pour permettre un rollback complet.
- Après chaque cas, noter le résultat, le lieu, la sauvegarde utilisée et toute erreur visible ou Papyrus pertinente.

---

## 4. Préconditions

### Mods et frameworks

- [ ] Acheron actif et fonctionnel.
- [ ] Acheron - Naked Defeat Bridge actif.
- [ ] Naked Defeat 6.50 FULL + patch 6.51 actifs.
- [ ] Naked Defeat - Rhiven Fix actif.
- [ ] Practical Defeat Reanimated désactivé.
- [ ] Yamete Kudasai entièrement désactivé.
- [ ] Simple Slavery++ actif et son MCM initialisé.
- [ ] Captive Player 1.9 actif.
- [ ] Captive Followers et ses prérequis actifs.
- [ ] Pandora régénéré après l’installation des éléments qui ajoutent des animations ou comportements.
- [ ] Aucun plugin ou master manquant au lancement.

### Compatibilités à inclure dans le profil de test

- [ ] Devious Devices NG.
- [ ] SlaveTats NG.
- [ ] Rape Tattoos Continued.
- [ ] Fade Tattoos Continued.

L’absence volontaire d’un de ces mods doit être consignée : un test réalisé sans lui ne valide pas sa compatibilité.

---

## 5. Checklist MCM — Acheron

- [ ] Vérifier que la conséquence **Naked Defeat / Acheron - Naked Defeat Bridge** est active.
- [ ] Vérifier que son poids est supérieur à 0 et correspond au profil Naked Defeat de référence.
- [ ] Régler le poids de **Captive Player à 0**.
- [ ] Vérifier qu’aucune autre conséquence générale de défaite ne concurrence Naked Defeat.
- [ ] Capturer ou noter tous les poids avant le premier test.
- [ ] Après sauvegarde/rechargement, confirmer que le poids de Captive Player reste à 0.

Résultat attendu :

> Une défaite Acheron ordinaire est toujours récupérée par Naked Defeat, jamais directement par Captive Player.

---

## 6. Checklist MCM — Simple Slavery++

- [ ] Vérifier que Captive Player est détecté comme destination disponible.
- [ ] Pour la première passe, activer **uniquement Captive Player** parmi les destinations candidates utiles au test.
- [ ] Désactiver temporairement la sélection aléatoire d’autres destinations si le MCM le permet.
- [ ] Noter les réglages de sélection, de poids ou de chance applicables.
- [ ] Vérifier les options de démarrage et de sortie de la vente aux enchères.
- [ ] Vérifier qu’aucun ancien réglage ne pointe vers un mod absent ou désactivé.
- [ ] Après sauvegarde/rechargement, confirmer que Captive Player reste détecté et sélectionné.

Résultat attendu :

> Une enchère Simple Slavery++ contrôlée peut envoyer le joueur vers Captive Player sans intervention d’Acheron.

---

## 7. Checklist MCM — Captive Player

- [ ] Vérifier que Captive Player est initialisé et activé.
- [ ] Vérifier que les options liées à Devious Devices correspondent au profil de test.
- [ ] Vérifier la touche de lutte et éviter tout conflit de raccourci.
- [ ] Noter les réglages de résolution de captivité, d’évasion, de prison et de retour vers Simple Slavery++.
- [ ] Pour la première passe, neutraliser si possible les sorties non indispensables afin d’isoler le flux testé.
- [ ] Vérifier les options de créatures et de scènes selon la configuration Rhiven retenue.
- [ ] Vérifier les options ou détections liées à SlaveTats NG / Rape Tattoos Continued.
- [ ] Conserver Fade Tattoos Continued actif pour observer l’évolution normale des overlays.
- [ ] Après sauvegarde/rechargement, vérifier que le MCM reste disponible et que ses réglages persistent.

---

## 8. Cas de test

### T01 — Non-interception d’une défaite Acheron

1. Charger la sauvegarde de départ hors de toute quête de captivité.
2. Confirmer dans Acheron : Naked Defeat actif, Captive Player à 0.
3. Provoquer une défaite standard contre des ennemis déjà utilisés pour les tests Naked Defeat.
4. Observer la conséquence sélectionnée.
5. Répéter au moins trois fois, avec retour à la même sauvegarde de départ.

**PASS :** les trois défaites sont transférées au Bridge puis à Naked Defeat ; Captive Player ne démarre jamais directement.

**FAIL :** Captive Player intercepte une défaite, une autre conséquence générale démarre, ou Naked Defeat ne reçoit pas l’événement.

### T02 — Persistance du poids Acheron à 0

1. Régler Captive Player à 0.
2. Sauvegarder, quitter complètement le jeu puis relancer.
3. Recharger et contrôler le MCM Acheron.
4. Rejouer une défaite standard.

**PASS :** le poids reste à 0 et Naked Defeat conserve la défaite.

**FAIL :** le poids change, Captive Player redevient éligible ou le routage varie après rechargement.

### T03 — Simple Slavery++ vers Captive Player

1. Utiliser une méthode de test contrôlée pour entrer dans Simple Slavery++ sans passer par une défaite Acheron.
2. Lancer la vente aux enchères.
3. Vérifier que Captive Player est la destination retenue.
4. Laisser la transition se terminer sans commande console de contournement.

**PASS :** le joueur quitte correctement l’enchère, entre dans une captivité Captive Player fonctionnelle et peut sauvegarder/recharger.

**FAIL :** aucune destination n’est trouvée, une autre destination démarre, la transition bloque, ou la quête Captive Player reste incomplète.

### T04 — Boucle centrale Captive Player

Depuis l’état obtenu par T03 :

1. Vérifier l’arrivée au lieu de captivité.
2. Tester l’attente et la touche de lutte.
3. Jouer au moins une scène de captivité.
4. Tester une issue d’évasion ou de libération.
5. Vérifier le retour à un état de jeu normal.
6. Sauvegarder et recharger pendant la captivité, puis après sa résolution.

**PASS :** la captivité progresse, se résout et rend le contrôle au joueur sans quête bloquée ni état Acheron/Naked Defeat résiduel.

**FAIL :** blocage de scène, contrôles non rendus, captivité impossible à résoudre, réactivation inattendue d’une défaite ou sauvegarde corrompue.

### T05 — Flux complet Naked Defeat vers Simple Slavery++

Ce test ne doit être lancé qu’après T01 à T04 réussis.

1. Identifier une branche Naked Defeat réellement prévue pour aboutir à Simple Slavery++.
2. Provoquer cette branche sans modifier le poids Acheron de Captive Player.
3. Confirmer la séquence exacte : Acheron → Bridge → Naked Defeat → Simple Slavery++.
4. Confirmer ensuite : Simple Slavery++ → Captive Player.
5. Résoudre la captivité et vérifier le retour au jeu normal.

**PASS :** chaque transfert se produit une seule fois, dans l’ordre attendu, et Captive Player n’est appelé qu’après Simple Slavery++.

**FAIL :** Captive Player démarre avant Simple Slavery++, Naked Defeat est contourné, plusieurs quêtes de conséquence se superposent ou la chaîne s’interrompt.

### T06 — Risque de boucle Captive Player → Simple Slavery++ → Captive Player

La fiche Captive Player indique que certains dénouements peuvent renvoyer le joueur vers Simple Slavery++ ; cette branche doit être considérée à risque tant qu’elle n’est pas testée.

1. Partir d’une captivité Captive Player propre obtenue par T03.
2. Provoquer, si possible sans commande forcée, une issue qui renvoie vers Simple Slavery++.
3. Observer la destination proposée à l’issue de la nouvelle enchère.
4. Si Captive Player est de nouveau sélectionné, ne jouer qu’un seul second cycle contrôlé.
5. Arrêter le test si un troisième transfert automatique vers Simple Slavery++ se prépare.

**PASS :** le retour vers Simple Slavery++ est maîtrisable et permet de choisir une sortie différente, d’exclure Captive Player ou de terminer la chaîne sans répétition automatique.

**FAIL :** Captive Player est resélectionné sans possibilité de sortie, les transferts se répètent indéfiniment, ou plusieurs instances de quête restent actives.

> En cas de boucle confirmée, Captive Player ne doit pas être retenu comme destination Simple Slavery++ tant qu’un réglage sûr ou un correctif dédié n’est pas disponible.

### T07 — Devious Devices NG

1. Entrer dans Captive Player avec Devious Devices NG actif.
2. Vérifier l’équipement et le retrait des dispositifs et contraptions.
3. Tester lutte, attente, scène, évasion/libération et changement de lieu.
4. Vérifier l’inventaire et les slots après résolution.
5. Sauvegarder/recharger avec des dispositifs actifs.

**PASS :** les dispositifs sont posés et retirés proprement, les animations se jouent et aucun verrou ou slot fantôme ne subsiste.

**FAIL :** dispositif invisible, impossible à retirer, conflit de contraption, animation bloquée ou état DD persistant après résolution.

### T08 — SlaveTats NG / Rape Tattoos Continued / Fade Tattoos Continued

1. Noter les overlays présents avant la captivité.
2. Déclencher une captivité et observer l’application éventuelle de tatouages.
3. Vérifier les entrées dans SlaveTats NG et l’absence de doublons.
4. Sauvegarder/recharger après application.
5. Laisser Fade Tattoos Continued traiter les tatouages selon sa logique normale.
6. Vérifier qu’une nouvelle captivité ne réapplique pas indéfiniment le même overlay.

**PASS :** les tatouages attendus sont appliqués une seule fois, persistent correctement, s’estompent sans erreur et n’écrasent pas les overlays Rhiven existants.

**FAIL :** doublons, overlays noirs ou absents, perte d’overlays existants, erreurs répétées, saturation des slots ou disparition incorrecte après rechargement.

---

## 9. Matrice de validation

| Domaine | Test | Résultat | Notes / preuve |
|---|---|---|---|
| Propriété des défaites Acheron | T01 | ☐ PASS ☐ FAIL | |
| Persistance du poids Captive Player = 0 | T02 | ☐ PASS ☐ FAIL | |
| Simple Slavery++ → Captive Player | T03 | ☐ PASS ☐ FAIL | |
| Captivité et retour au jeu | T04 | ☐ PASS ☐ FAIL | |
| Naked Defeat → Simple Slavery++ → Captive Player | T05 | ☐ PASS ☐ FAIL | |
| Absence de boucle | T06 | ☐ PASS ☐ FAIL | |
| Devious Devices NG | T07 | ☐ PASS ☐ FAIL | |
| SlaveTats / Rape Tattoos / Fade Tattoos | T08 | ☐ PASS ☐ FAIL | |

---

## 10. Critères globaux

### PASS — intégration candidate acceptable

Tous les points suivants sont requis :

- Captive Player reste à un poids Acheron de 0 après redémarrage et rechargement ;
- Naked Defeat reçoit toutes les défaites Acheron ordinaires testées ;
- Simple Slavery++ détecte et lance Captive Player de façon fiable ;
- le flux complet via Naked Defeat, lorsqu’il existe, respecte l’ordre attendu ;
- aucune boucle Captive Player → Simple Slavery++ → Captive Player n’est incontrôlable ;
- la captivité peut être résolue et rend un état de jeu normal ;
- Devious Devices NG ne laisse aucun dispositif ou état fantôme ;
- les tatouages ne créent ni doublons, ni perte d’overlays, ni saturation ;
- les sauvegardes/rechargements critiques fonctionnent ;
- aucun symptôme de deux systèmes de défaite actifs en parallèle n’est observé.

### FAIL — intégration refusée ou investigation requise

Un seul des points suivants suffit à bloquer l’adoption :

- Captive Player intercepte directement une défaite Acheron ;
- Naked Defeat est contourné ou perd la propriété d’une défaite ;
- Simple Slavery++ ne détecte pas Captive Player ou ne termine pas le transfert ;
- une boucle de ré-enchère ne peut pas être interrompue proprement ;
- une quête, scène, contraption, commande joueur ou IA reste bloquée ;
- les dispositifs Devious Devices persistent après la fin attendue ;
- les overlays sont dupliqués, écrasés ou saturés ;
- le problème réapparaît après retour à la sauvegarde de départ et reproduction contrôlée.

---

## 11. Preuves à conserver

- captures des trois MCM avant le test ;
- poids Acheron visibles, dont Captive Player à 0 ;
- destinations actives dans Simple Slavery++ ;
- réglages Captive Player pertinents ;
- nom et heure de chaque sauvegarde de test ;
- ordre réel des transitions de quêtes ;
- captures des dispositifs et overlays avant/après ;
- extrait Papyrus limité à la fenêtre du test en cas d’erreur ;
- résultat PASS/FAIL de chaque cas, sans convertir un test non joué en succès.

---

## 12. Rollback

Si un cas critique échoue :

1. quitter sans écraser la sauvegarde de départ ;
2. désactiver Captive Player comme destination dans Simple Slavery++ ;
3. confirmer que son poids Acheron est toujours à 0 ;
4. revenir au profil MO2 Naked Defeat validé ;
5. désactiver Captive Player et les ajouts installés uniquement pour lui ;
6. restaurer la sauvegarde créée avant l’installation ou avant la première entrée dans Simple Slavery++ ;
7. relancer un test de défaite Naked Defeat de référence ;
8. vérifier la séquence Acheron → Bridge → Naked Defeat et un retour normal au jeu.

Ne pas poursuivre une sauvegarde ayant connu une boucle de quêtes, des dispositifs fantômes ou plusieurs conséquences de défaite simultanées.

---

## 13. Décision provisoire

La configuration candidate est :

```text
Acheron
└─ Naked Defeat Bridge (conséquence active)
   └─ Naked Defeat (propriétaire exclusif des défaites)

Captive Player
├─ actif comme mod
├─ poids Acheron = 0
└─ destination Simple Slavery++ uniquement
```

> **Décision actuelle : protocole prêt, intégration non validée.**
>
> Captive Player ne pourra être retenu dans la configuration Rhiven qu’après validation des huit cas, avec une attention particulière au flux complet, au risque de boucle et aux états persistants Devious Devices / tatouages.
