# TK Dodge pour NEFARAM

> **Statut : validation en jeu terminée sur NEFARAM 17.3.6, 17.3.7 et 17.3.8.**
>
> **Runtime testé :** Skyrim AE 1.6.1170 avec la pile de combat NEFARAM, notamment MCO, TDM, Precision et Pandora.

> **Crédit :** ce guide repose en partie sur le guide TK Dodge original de NEFARAM écrit par **Thoshy**. La procédure ci-dessous a été réorganisée, développée et validée en jeu sur NEFARAM 17.3.6, 17.3.7 et 17.3.8.

Ce guide ajoute une esquive directionnelle à NEFARAM tout en préservant la pile de combat et de comportements existante. La compatibilité avec MCO, TDM, Precision et Pandora a été observée dans la configuration testée. Cela ne garantit pas toutes les personnalisations possibles des utilisateurs.

La procédure utilise le TK Dodge Animation Pandora Patch indiqué. Elle n'introduit aucun patch personnalisé supplémentaire.

---

## 1. Avant l'installation

Utilisez une sauvegarde de test et, si possible, clonez ou sauvegardez d'abord le profil MO2 actuel. Notez les priorités existantes du panneau gauche et la configuration de Pandora afin de pouvoir les restaurer si nécessaire.

Pour le premier test, n'installez que la pile TK Dodge de base. N'ajoutez **pas** de remplacement d'animations facultatif avant que l'esquive directionnelle fonctionne de manière fiable avec les animations par défaut.

---

## 2. Pile requise

Installez ces composants dans cet ordre :

1. **IFrame Generator RE AE Support** — <https://www.nexusmods.com/skyrimspecialedition/mods/82737>
2. **TK Dodge For RE** — <https://www.nexusmods.com/skyrimspecialedition/mods/15309>. Dans **Optional Files**, installez l'entrée nommée `TK Dodge For RE`.
3. **TK Dodge RE v0.55-rc3** — <https://www.nexusmods.com/skyrimspecialedition/mods/56956>
4. **TK Dodge First Person 8 Ways Dodge** — disponible sur la page de TK Dodge RE.
5. **TK Dodge Animation Pandora Patch** — <https://www.nexusmods.com/skyrimspecialedition/mods/111788>
6. **TK Dodge NG** — <https://www.nexusmods.com/skyrimspecialedition/mods/115408>

Une fois la pile de base validée par la matrice de test, vous pouvez ajouter **un seul** des remplacements d'animations suivants :

- Dynamic Dodge Animation ; ou
- Smooth Slip Dodge Animation.

N'installez jamais les deux remplacements d'animations ensemble.

### Pourquoi IFrame Generator reste dans la pile

IFrame Generator RE AE Support fournit des fenêtres d'invincibilité pendant les animations d'esquive prises en charge. Gardez-le activé, sauf si vos tests mettent en évidence une incompatibilité précise dans votre configuration.

---

## 3. FOMOD de TK Dodge RE

Pour **TK Dodge RE v0.55-rc3**, sélectionnez les options suivantes :

- `Behavior edits for dodge only`
- `TK dodge standalone`
- `TK dodge standalone - Enable Sheathed Dodge`
- `TK dodge standalone - Cancel concentration spell when dodging`
- `TK dodge standalone - Forward dodge scurry fix`

Évitez d'ajouter des variantes de comportement sans rapport pendant le test initial d'intégration.

---

## 4. Priorité et placement dans MO2

Règles importantes de priorité dans le panneau gauche :

- **TK Dodge NG doit être sous TK Dodge RE** afin que les fichiers NG gagnent les conflits.
- La pile TK Dodge complète doit rester **au-dessus de Pandora Output**.
- **Pandora Output doit être sous toute la pile d'esquive**, y compris le remplacement d'animations facultatif lorsqu'il est utilisé.

La procédure source suit la logique de placement Late Loaders de NEFARAM, car elle maintient la pile d'esquive au-dessus des mods de sortie. Un séparateur facultatif nommé `TK Dodge` peut être créé dans cette zone pour faciliter l'organisation ; il n'est pas requis.

Agencement relatif recommandé :

```text
[Late Loaders]
[TK Dodge]                                  # séparateur facultatif
IFrame Generator RE AE Support
TK Dodge For RE
TK Dodge RE
TK Dodge First Person 8 Ways Dodge
TK Dodge Animation Pandora Patch
TK Dodge NG
(un remplacement d'animations facultatif)
...
[Overwrites]
Pandora Output
```

Ce sont les priorités relatives qui comptent. Ne copiez pas les noms de séparateurs propres à un utilisateur et ne supposez pas que toutes les installations NEFARAM personnalisées utilisent les mêmes positions absolues.

---

## 5. Règle concernant le fichier INI gagnant

**TK Dodge RE** et **TK Dodge NG** contiennent tous deux un fichier nommé `TK Dodge RE.ini`.

TK Dodge NG étant chargé après TK Dodge RE, la copie située dans **TK Dodge NG gagne**. Ne modifiez que ce fichier effectif :

```text
TK Dodge NG -> TK Dodge RE.ini
```

Modifier le fichier de même nom dans TK Dodge RE n'a aucun effet tant qu'il est écrasé par TK Dodge NG.

Choisissez le style d'esquive souhaité dans le fichier INI NG gagnant :

```ini
StepDodge = false
```

Active les roulades.

```ini
StepDodge = true
```

Active les esquives par pas/glissade.

Aucune valeur n'est universellement imposée. C'est une préférence utilisateur, sauf lorsqu'un remplacement d'animations est conçu pour un style précis.

---

## 6. Générer les comportements avec Pandora

NEFARAM utilise **Pandora, et non FNIS**, pour cette intégration.

Dans Pandora, activez les deux entrées :

- `TK Dodge RE / Ultimate Combat`
- `TK Dodge Standalone`

Régénérez ensuite Pandora. Régénérez-le de nouveau après avoir réinstallé TK Dodge RE, modifié des fichiers liés aux comportements ou changé un composant d'animations.

L'historique de dépannage documenté montre que l'absence de sélection de `TK Dodge Standalone` peut provoquer des T-poses ou des esquives directionnelles défectueuses.

---

## 7. Premier test en jeu

Testez la pile TK Dodge de base **avant** d'installer Dynamic Dodge Animation ou Smooth Slip Dodge Animation. Il sera ainsi beaucoup plus facile d'isoler les problèmes de comportement, de commandes et d'animations.

Utilisez la touche d'esquive réellement configurée dans votre installation ; ce guide n'impose aucune touche par défaut.

Testez tous les points suivants :

- esquive vers l'avant, l'arrière, la gauche et la droite ;
- arme rengainée et dégainée ;
- arme à une main ;
- arme à deux mains ;
- deux armes ;
- sort dans une main ;
- sorts dans les deux mains et lancement double ;
- première et troisième personne ;
- comportement de combat MCO ;
- déplacements TDM ;
- interactions de combat Precision ;
- consommation d'endurance ;
- fonctionnement des i-frames ;
- esquives répétées sous forte charge de combat ;
- sauvegarde, fermeture, rechargement et nouveau test.

N'ajoutez un remplacement d'animations facultatif qu'une fois la pile de base validée sans T-pose, roulade sur place ni perte du mouvement directionnel.

---

## 8. Remplacements d'animations facultatifs

Choisissez **une seule option**, ou conservez les animations TK Dodge par défaut.

### Option A : Dynamic Dodge Animation

<https://www.nexusmods.com/skyrimspecialedition/mods/79598>

Sélectionnez ces choix du FOMOD :

- `TK Dodge RE 0.55 rc3`
- `Sway`

Régénérez Pandora et répétez toute la matrice de test.

### Option B : Smooth Slip Dodge Animation

<https://www.nexusmods.com/skyrimspecialedition/mods/63660>

Utilisez ce fichier :

- `Smooth Slip Dodge I TDM 360 movement users`

Smooth Slip est généralement associé au réglage suivant dans le fichier INI TK Dodge NG gagnant :

```ini
StepDodge = true
```

Régénérez Pandora et répétez toute la matrice de test.

Ne laissez pas Dynamic Dodge Animation et Smooth Slip Dodge Animation activés ensemble.

---

## 9. Dépannage

### T-pose pendant une esquive

Vérifiez dans cet ordre :

1. TK Dodge NG est sous TK Dodge RE.
2. Pandora Output est sous la pile TK Dodge complète.
3. `TK Dodge RE / Ultimate Combat` et `TK Dodge Standalone` sont tous deux activés dans Pandora.
4. TK Dodge RE utilise exactement les sélections FOMOD indiquées dans ce guide.
5. Pandora est à jour et ses chemins configurés sont corrects.
6. Régénérez Pandora.

Le cas de dépannage NEFARAM documenté a été résolu après restauration du comportement standalone manquant.

### L'animation d'esquive se joue sur place ou sans mouvement directionnel

Vérifiez que :

- TK Dodge Animation Pandora Patch est installé et actif ;
- les deux entrées Pandora sont activées ;
- le comportement TK Dodge standalone a été installé ;
- Pandora a été régénéré après l'installation ;
- le problème se produit aussi avec les animations TK Dodge de base, et non uniquement avec un remplacement ;
- la version de Pandora installée est à jour pour la configuration.

### L'esquive par pas ne s'active pas

Confirmez que `StepDodge = true` a été enregistré dans :

```text
TK Dodge NG -> TK Dodge RE.ini
```

Ne modifiez pas uniquement le fichier INI écrasé situé dans TK Dodge RE.

### La touche d'esquive est inactive

Vérifiez que :

- TK Dodge NG est installé, activé et gagne les conflits attendus ;
- la touche pressée correspond au raccourci réellement configuré ;
- les deux entrées Pandora restent activées ;
- Pandora a été régénéré ;
- aucun raccourci Windows ou lié à la langue du clavier n'intercepte la saisie.

Aucune préférence personnelle de touche n'est imposée par ce guide.

### Problème pendant le lancement double

Les tests sources indiquent que l'esquive directionnelle peut fonctionner avec un sort de destruction dans chaque main. En cas d'échec, examinez d'abord le raccourci, la disposition du clavier, les raccourcis du système et la configuration locale, plutôt que de conclure à une incompatibilité confirmée de TK Dodge.

---

## 10. Après une mise à jour de NEFARAM

La discussion source mentionne la convention de nommage `[NoDelete]` de NEFARAM comme précaution facultative pour les mods personnalisés devant survivre à une procédure de mise à jour. Sa pertinence dépend de votre méthode de mise à jour et de maintenance de la liste locale ; elle ne remplace pas la validation après mise à jour.

Après chaque mise à jour de NEFARAM :

1. confirmez que tous les composants TK Dodge requis sont toujours installés et activés ;
2. confirmez que TK Dodge NG reste sous TK Dodge RE ;
3. confirmez que Pandora Output reste sous toute la pile d'esquive ;
4. inspectez le fichier `TK Dodge RE.ini` gagnant dans TK Dodge NG ;
5. confirmez que les deux entrées TK Dodge restent activées dans Pandora ;
6. régénérez Pandora si des fichiers de comportement ou d'animations ont changé ;
7. testez en jeu l'esquive vers l'avant, l'arrière, la gauche et la droite.

---

## 11. Résumé de la validation

Cette intégration a été validée en jeu sur :

- NEFARAM 17.3.6 ;
- NEFARAM 17.3.7 ;
- NEFARAM 17.3.8 ;
- Skyrim AE 1.6.1170.

Dans la configuration testée, TK Dodge fonctionnait avec la pile de combat NEFARAM, notamment MCO, TDM, Precision, IFrame Generator et Pandora. Les modifications de combat, d'animations, de commandes ou de comportements ajoutées par l'utilisateur peuvent modifier le résultat et doivent être testées séparément.

### Liste de contrôle finale

- [ ] Les six composants requis sont installés dans l'ordre documenté.
- [ ] TK Dodge RE utilise les sélections FOMOD documentées.
- [ ] TK Dodge NG est sous TK Dodge RE.
- [ ] Seule la copie NG gagnante de `TK Dodge RE.ini` est modifiée.
- [ ] La valeur `StepDodge` choisie correspond au style d'esquive voulu.
- [ ] Au maximum un remplacement d'animations facultatif est activé.
- [ ] La pile d'esquive complète est au-dessus de Pandora Output.
- [ ] `TK Dodge RE / Ultimate Combat` est activé dans Pandora.
- [ ] `TK Dodge Standalone` est activé dans Pandora.
- [ ] Pandora a été régénéré.
- [ ] Les animations de base ont passé le test en jeu complet avant l'ajout d'un remplacement.
- [ ] Le test dans les quatre directions réussit toujours après une mise à jour de NEFARAM.

---

## Référence interne

Pour l'historique de maintenance et la source française nettoyée, consultez [NEFARAM — Guide TK Dodge](../../../06%20-%20GAMEPLAY/TK-DODGE/NEFARAM_Guide_TK_Dodge_FR.md).
