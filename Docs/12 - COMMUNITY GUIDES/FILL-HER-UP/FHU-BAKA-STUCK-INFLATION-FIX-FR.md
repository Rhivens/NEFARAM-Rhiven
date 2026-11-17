# Fill Her Up Baka Edition — Dépannage : inflation bloquée après interruption de scène

> **Type :** fiche de dépannage communautaire (message Discord NEFARAM communiqué le 17 novembre 2026)  
> **Configuration de référence Rhiven :** NEFARAM 17.3.8 · Fill Her Up Baka Edition **2.11V**  
> **État :** procédure **rapportée par un utilisateur**, **non reproduite / non validée sur NEFARAM-Rhiven**  
> **Usage :** **curatif uniquement**, en cas de symptômes identiques ; **ne rien modifier sur une sauvegarde saine**.
>
> **Source :** retour Discord intitulé « FIX for Stuck Fill Her Up (FHU) Inflation. » (texte communiqué dans la discussion de projet ; lien permanent du message non fourni).

## 1. Symptômes rapportés

Après une scène déclenchée par un autre mod (dans le témoignage : le **Loanshark de BaboDialogue**), un événement de remplissage forcé a interrompu incorrectement la fonction `Inflate()` de FHU.

Le personnage est resté membre de la faction technique **`inflaterAnimatingFaction`**. Cette appartenance sert d'indicateur d'animation/traitement en cours pour les contrôles FHU.

En jeu, le résultat ressemblait à une panne générale de FHU :

- plus de remplissage reconnu ;
- aucune nouvelle donnée de remplissage affichée pour le personnage ;
- commandes / opérations FHU sans effet ;
- **Reset Actors** dans FHU n'a pas suffi à réparer le blocage.

Un second symptôme peut se manifester après correction de la faction : **oscillation du morph** entre la valeur souhaitée et une autre valeur fixe pendant une inflation ou déflation. Le témoignage associe ce comportement à un script actif bloqué.

**Important :** un seul témoignage ne prouve pas que le problème affecte toutes les versions 2.11V ni que BaboDialogue est systématiquement en cause.

## 2. Avant toute intervention

1. **Quitter Skyrim** et faire une **copie externe** de la sauvegarde et de son co-save SKSE, si présent.
2. Identifier une sauvegarde antérieure à la scène problématique : **revenir à cette sauvegarde est généralement plus sûr** que modifier l'état Papyrus.
3. Ne jamais modifier `Eleanor_Start`, `NEFARAM_Start` ou une sauvegarde de référence.
4. Vérifier les symptômes et le plugin qui définit réellement la faction dans le **load order actif**. Le préfixe `XX` des commandes est **variable** ; ne pas réutiliser mécaniquement `66` de l'exemple Discord.
5. Pour une intervention sur sauvegarde avec ReSaver, ne modifier **que l'instance clairement identifiée comme concernée** ; éviter les nettoyages globaux et les « terminate » à l'aveugle.

## 3. Étape A — Vérifier la faction bloquée avec la console

Dans Skyrim, ouvrir la console sur une **copie de sauvegarde de test**.

Commande communiquée :

```text
player.getfactionrank XX0187C8
```

- Remplacer **`XX`** par l'index de chargement réel du plugin contenant `inflaterAnimatingFaction`, **après identification de la faction** dans xEdit ou dans l'installation active.
- Dans l'exemple Discord, la commande était `player.getfactionrank 660187C8` : **`66` n'est pas un identifiant universel**.
- Selon le témoignage, un résultat **0 ou supérieur** (souvent **1**) signale que le personnage est encore dans la faction. Une valeur négative indique normalement l'absence du personnage dans cette faction.

**Si l'appartenance est confirmée et le blocage correspond exactement aux symptômes**, le correctif rapporté est :

```text
player.removefromfaction XX0187C8
```

Tester FHU (inflation/déflation) puis enregistrer **une nouvelle sauvegarde distincte** et effectuer un rechargement. **S'arrêter ici si le mod fonctionne de nouveau.**

> **Vérification FormID :** `XX0187C8` est le FormID donné par le témoignage. Sa structure, son appartenance au bon plugin et son éventuelle forme ESL doivent être **confirmées localement** avant exécution ; ne pas supposer qu'un préfixe à deux chiffres convient dans tous les cas.

## 4. Étape B — Script `sr_inflatethread` bloqué (ReSaver)

**À n'envisager que si**, après l'étape A, le personnage oscille entre deux états de morph pendant une inflation / déflation **et** qu'un examen de la sauvegarde confirme un thread FHU suspect.

Le message Discord propose la procédure suivante :

1. Quitter Skyrim et lancer **ReSaver / FallrimTools** via MO2 (la publication mentionne **Java 8** pour son environnement ; vérifier les exigences de la version de ReSaver effectivement installée).
2. Ouvrir **la copie de la sauvegarde défectueuse**, pas l'original.
3. Rechercher `sr_inflatethread` avec le champ de recherche / filtre.
4. Inspecter les instances trouvées ; si l'instance responsable est **identifiée sans ambiguïté**, utiliser **clic droit → Terminate** sur l'élément correspondant, puis confirmer.
5. Sur ce même élément, utiliser **Find Owner**.
6. Dans l'objet propriétaire identifié, passer la variable booléenne **`running`** à **`false`**.
7. Utiliser **File → Save As** pour enregistrer sous **un autre nom**, dans le dossier des sauvegardes du profil NEFARAM de test.
8. Recharger dans Skyrim, tester plusieurs cycles inflation/déflation, puis sauvegarder et recharger pour vérifier la persistance.

**Ne pas faire :** terminer tous les threads Papyrus, effacer arbitrairement des instances FHU, nettoyer automatiquement les unattached instances / undefined elements, ou enregistrer par-dessus la seule sauvegarde saine.

> La procédure Discord emploie « terminate » sur le dossier `sr_inflatethread`. L'interface de ReSaver et le type exact des éléments sélectionnés pouvant varier, **vérifier soigneusement la cible et le propriétaire**, et ne jamais appliquer la commande à un ensemble d'instances non identifiées.

## 5. Validation après réparation

- [ ] FHU enregistre à nouveau les événements de remplissage.
- [ ] Inflation et déflation fonctionnent sans oscillation.
- [ ] Les valeurs affichées et les morphs correspondent aux actions.
- [ ] Une nouvelle sauvegarde peut être rechargée sans retour du blocage.
- [ ] Une scène normale et une scène externe représentative ne provoquent pas de nouveau blocage.
- [ ] Pas de répétition manifeste d'erreurs FHU dans les journaux disponibles.

Si le problème revient ou si un état interne devient incohérent, **revenir à la sauvegarde d'avant l'incident** plutôt que multiplier les modifications ReSaver.

## 6. Application au projet NEFARAM-Rhiven

- **Fill Her Up Baka Edition 2.11V + traduction FR : conservés.** Plusieurs jours de tests en jeu par Rhiven sans anomalie observée.
- **SLIF classique / NG : non installé actuellement.** Le correctif décrit concerne surtout une **faction d'état** et un **script Papyrus** bloqués, et ne démontre pas un besoin d'installer SLIF NG.
- L'origine évoquée (**BaboDialogue Loanshark**) est **un exemple de déclencheur**, pas une incompatibilité confirmée.
- **Aucune manipulation préventive** sur les sauvegardes actuelles ; conserver cette fiche comme solution de secours si les mêmes symptômes apparaissent un jour.

## 7. Statut et limites

| Élément | Statut |
|---|---|
| Texte de dépannage Discord | Retranscrit et structuré |
| Faction `inflaterAnimatingFaction` | Signalée comme cause dans le témoignage |
| FormID `XX0187C8` | Fourni par Discord ; **à vérifier sur l'installation active** |
| Script `sr_inflatethread` / variable `running` | Procédure communautaire ; **à confirmer sur la copie de la sauvegarde** |
| Reproduction sur NEFARAM-Rhiven 17.3.8 / Baka 2.11V | **Non réalisée** |
| Confirmation d'un correctif officiel par l'auteur | **Non établie** |

---

*Fiche conservatoire : priorité à la sauvegarde originale, à la vérification des identifiants et à un retour arrière sûr. Ne jamais transformer un dépannage circonstanciel en opération d'entretien systématique.*
