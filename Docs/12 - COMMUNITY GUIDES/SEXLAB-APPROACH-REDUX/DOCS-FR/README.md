# SexLab Approach Redux 3.62 pour NEFARAM

> **Statut :** intégration technique validée ; la validation en jeu et le réglage à long terme restent dépendants de l'utilisateur
>
> **Version :** SexLab Approach Redux **3.62**
>
> **Périmètre :** installation, placement dans MO2, génération Pandora, initialisation du MCM, suivi de la compatibilité et tests fonctionnels

Ce guide communautaire explique comment ajouter SexLab Approach Redux 3.62 à une installation NEFARAM existante. L'intégration ne nécessite **aucun** patch personnalisé.

## Fonction de SexLab Approach Redux

SexLab Approach Redux ajoute des approches autonomes des PNJ et une couche sociale réactive. Les PNJ proches peuvent engager des conversations et des interactions sexuelles au lieu d'attendre que le joueur lance chaque rencontre. Les dialogues et comportements disponibles dépendent des conditions du mod, des traits de caractère, des relations, des réglages d'excitation et des intégrations activées.

Il s'agit principalement d'un système de dialogues et d'événements scriptés, et non d'une extension de worldspaces ou de lieux de quête. La principale préoccupation d'intégration concerne donc le timing et la propriété des événements plutôt que les conflits de paysage ou de navmesh.

## Approach et SLHH

SexLab Approach Redux ne fait **pas** doublon avec SLHH Expansion.

- **SexLab Approach Redux** se concentre sur les approches autonomes des PNJ, les interactions sociales et les dialogues ou événements sexuels.
- **SLHH Expansion** se concentre davantage sur le harcèlement et les rencontres agressives.

Les deux mods peuvent coexister, car leurs rôles sont complémentaires. Cependant, tous deux peuvent lancer des interactions autour du joueur ; des réglages imprudents peuvent donc produire trop d'événements, des forcegreets empilés, des dialogues concurrents ou des démarrages de scènes qui se chevauchent. Utilisez des probabilités prudentes et des temps de recharge significatifs, puis réglez les deux MCM ensemble avant de conclure à une incompatibilité.

## Prérequis et pile NEFARAM existante

SexLab Approach Redux nécessite l'écosystème habituel de SexLab et des animations. NEFARAM d'origine fournit déjà les principaux composants utilisés par Approach :

- SexLab Framework ;
- une pile compatible OSL/SLO Aroused ;
- Fuz Ro D-oh / Silent Voice ;
- la prise en charge de SLAL ;
- Baka Motion Data Pack ;
- Pandora Behaviour Engine.

NEFARAM d'origine contient également l'écosystème environnant pertinent, notamment :

- `[35 - Sexlab Content]` ;
- BaboDialogue et BaboDialogue Stability Patch ;
- SLHH Expansion ;
- SexLab Survival ;
- la pile Devious Devices ailleurs dans la liste ;
- d'autres systèmes de gameplay adulte et d'événements autonomes.

N'installez **pas** de copies en double des frameworks déjà fournis par NEFARAM. Confirmez les prérequis par rapport à votre version et profil NEFARAM actuels avant d'ajouter des fichiers facultatifs.

## Avant l'installation

1. Clonez votre profil MO2 fonctionnel.
2. Sauvegardez ou exportez l'ordre du panneau gauche de MO2 et celui des plugins dans le panneau droit.
3. Utilisez une sauvegarde de test jetable ou une nouvelle partie de test.
4. Écartez du profil de test les modifications expérimentales sans rapport.
5. Notez la sortie Pandora et l'état du MCM actuels afin de simplifier tout retour arrière.

## Placement dans MO2

Placez SexLab Approach Redux dans ou près de la section `[Sexlab Content]` de NEFARAM d'origine.

Appliquez des principes de placement relatif :

- conservez le mod avec les autres contenus SexLab plutôt que de copier une position absolue d'un autre profil ;
- gardez ses frameworks requis actifs et placés plus tôt dans le panneau gauche ;
- inspectez les fichiers qui gagnent chaque conflit MO2 ;
- préservez dans le panneau droit tout ordre master-avant-dépendant requis ;
- placez uniquement les fichiers de compatibilité pertinents après les composants qu'ils doivent prendre en charge.

La position exacte peut changer avec l'évolution de NEFARAM ; utilisez le séparateur d'origine et préservez les relations entre frameworks, contenu, fichiers de compatibilité et sortie générée.

## Procédure d'installation

1. Installez **SexLab Approach Redux 3.62** avec MO2.
2. Inspectez la structure de l'archive, le plugin activé, les scripts, animations, données JSON et fichiers MCM.
3. Examinez tous les conflits MO2 et vérifiez les masters du plugin.
4. N'installez que les fichiers de compatibilité facultatifs correspondant aux systèmes réellement présents et activés dans votre profil.
5. Assurez-vous que l'actuel `SLAppAutoMCM.json` de la version 3.62 obtient le résultat de conflit prévu ; ne restaurez pas automatiquement un ancien preset généré.
6. Exécutez Pandora.
7. Ne lancez Skyrim qu'après la fin sans erreur bloquante de Pandora.
8. Commencez avec des fréquences et probabilités prudentes plutôt qu'avec des réglages agressifs.

## Pandora

NEFARAM utilise **Pandora, et non FNIS**, pour ce workflow.

Relancez Pandora après avoir installé SexLab Approach Redux, car la prise en charge des animations et comportements fait partie du processus d'intégration. Confirmez que le bon profil MO2 est actif, générez la sortie, examinez le résultat pour repérer les erreurs bloquantes et ne lancez le jeu qu'après une passe Pandora réussie.

Si vous ajoutez, supprimez ou modifiez ensuite des paquets de comportements ou d'animations associés, régénérez Pandora.

## Audit xEdit et avertissement connu

`SexLab Approach.esp` a été contrôlé avec **SSEEdit 4.1.5**.

- **Records traités :** 5 546
- **Résultat :** un groupe d'avertissements/erreurs
- **Quête concernée :** `SLApproachAskForSex2Quest "SLApproachAsktoOtherQuest" [QUST:xx012AFD]`
- **Fragment concerné :** `SLApp_QF_AskForSex2Quest_04012AFD`

Le fragment contient trois références d'alias VMAD orphelines :

```text
Alias_initialActor -> Alias[0]
Alias_PlayerRef    -> Alias[2]
Alias_TargetActor  -> Alias[3]
```

La section **Aliases** actuelle de la quête est vide.

Ne nettoyez **pas** automatiquement le plugin et ne modifiez pas ce VMAD/fragment à l'aveugle. Considérez-le comme un avertissement structurel connu, probablement hérité d'une ancienne structure de quête, et testez spécifiquement en jeu la branche `AskForSex2` / ask-other.

L'avertissement n'empêche pas le chargement du plugin, l'enregistrement du MCM ni l'affichage des réglages actuels de la version 3.62. Il impose un test ciblé en jeu ; il ne prouve pas qu'une réparation non étayée doit être inventée.

## Initialisation propre du MCM

La version 3.62 fournit un fichier `SLAppAutoMCM.json` vide. Il a été validé comme état d'initialisation propre lorsqu'il gagnait son conflit MO2 face à un ancien fichier dans `SKSE Output`.

Avec ce fichier 3.62 propre actif :

- le MCM s'est enregistré correctement ;
- toutes les pages se sont chargées ;
- aucun champ vide n'a été observé ;
- les nouvelles options comme `OnlyinTown` et `Sex CoolTime` sont apparues ;
- les options de compatibilité pour SLHH, BaboDialogue, FillHerUp, SexLab Survival et DDI étaient présentes.

Ne restaurez ou n'importez pas aveuglément un ancien preset généré. Laissez d'abord la version 3.62 s'initialiser proprement et confirmez que chaque page et champ est disponible.

## Preset NEFARAM historique

Un ancien preset généré a été identifié à cet emplacement :

```text
SKSE Output/SKSE/Plugins/BakaFactory/SLAppAutoMCM.json
```

Il s'identifie comme `NEFARAM - 263`, version `2`. Considérez-le uniquement comme une trace du comportement historique, **pas** comme un preset directement importable dans la version 3.62.

Ce preset privilégiait une densité d'approches moyenne à élevée et activait plusieurs intégrations, mais il précède des réglages plus récents tels que `OnlyinTown` et `Sex CoolTime`. L'importer aveuglément peut laisser de nouvelles options indéfinies ou reporter des choix de densité d'événements inadaptés au profil actuel.

## Première stratégie MCM recommandée

Partez des valeurs par défaut propres de la version 3.62 et établissez une boucle d'approche de base stable avant d'étendre les fonctionnalités.

- Conservez une fréquence et une probabilité d'approches prudentes.
- Utilisez des temps de recharge significatifs.
- Activez les intégrations volontairement, une par une.
- Examinez explicitement `OnlyinTown` et `Sex CoolTime`.
- Examinez Unique Actor, les exigences de relation et les seuils d'excitation du joueur/des PNJ.
- Évitez d'activer simultanément tous les événements ou catégories d'acteurs facultatifs.
- N'enregistrez un nouveau preset qu'après avoir testé la configuration actuelle.

L'objectif est une interaction occasionnelle et adaptée au contexte, non une file continue d'événements de PNJ.

## Notes de compatibilité et d'interaction

Les systèmes suivants méritent une surveillance ciblée. Leur présence ne prouve pas à elle seule une incompatibilité.

### SLHH Expansion

Approach et SLHH ont des rôles complémentaires, mais peuvent tous deux lancer des interactions. Surveillez les démarrages simultanés, dialogues empilés, sélections d'acteurs en double, blocages des commandes ou le déclenchement d'un système avant que l'autre ait libéré le joueur.

### BaboDialogue

BaboDialogue appartient au même écosystème d'interactions plus large. Surveillez les forcegreets répétés, boucles de dialogue, conflits de packages et demandes de scènes trop rapprochées.

### Devious Devices

Si les options liées à DDI sont activées, vérifiez la détection des dispositifs, les conditions de dialogue, le comportement d'équipement/déverrouillage et la restauration propre de l'état du joueur après les scènes. N'activez ces options qu'une fois le système d'approche de base stable.

### SexLab Survival

SexLab Survival peut ajouter ses propres événements contextuels et pressions sociales. Testez les approches pendant le gameplay Survival normal et peu après ses événements. Ajustez les temps de recharge avant de conclure à un conflit ferme.

### Autres systèmes autonomes

TDF SexLab Aroused Rape, SL Dangerous Nights, les piles de défaite et les systèmes d'événements aléatoires peuvent également se disputer les commandes du joueur, les dialogues, la réservation des acteurs ou la propriété des scènes. Surveillez-les comme sources possibles de chevauchement plutôt que comme incompatibilités certaines.

## Conseils sur la densité des événements

Le principal risque pratique est le déclenchement rapproché de plusieurs systèmes autonomes. Symptômes typiques :

- forcegreets ou fenêtres de dialogue empilés ;
- démarrage d'une scène alors qu'un autre système contrôle encore le joueur ;
- réservation du même PNJ par plusieurs systèmes ;
- commandes non restaurées ;
- PNJ bloqués dans un package d'approche ;
- événements répétés immédiatement après la fin du précédent.

Avant de conclure à une incompatibilité, réduisez les probabilités ou la fréquence, augmentez les temps de recharge, restreignez les contextes et activez les intégrations par étapes. Testez un seul changement à la fois afin que la source de tout chevauchement reste identifiable.

## Liste de contrôle de validation en jeu

Testez les points suivants sur le profil et la sauvegarde jetables :

- [ ] Un PNJ lance une approche autonome.
- [ ] Le dialogue commence et se termine proprement.
- [ ] Le PNJ retrouve ensuite son IA normale.
- [ ] Les commandes du joueur sont restaurées.
- [ ] Sauvegarder, quitter complètement et recharger reste sûr.
- [ ] Aucun accueil ou dialogue répété en boucle n'apparaît.
- [ ] Approach ne prend pas simultanément le contrôle avec SLHH, BaboDialogue ou un autre système autonome.
- [ ] La branche `AskForSex2` / ask-other fonctionne malgré l'avertissement xEdit documenté.
- [ ] Le comportement reste raisonnable dans une ville très peuplée.
- [ ] Le comportement reste raisonnable dans une auberge.
- [ ] Les approches extérieures fonctionnent sans état IA persistant.
- [ ] Une zone peu peuplée ne produit pas de polling anormal ni de spam d'événements.

Ne considérez pas une scène réussie comme une validation complète. Répétez les événements, changez de lieu et testez la sauvegarde/le rechargement après des interactions terminées.

## Dépannage

### Les approches manquent ou sont défectueuses

Vérifiez les frameworks requis, les masters du plugin, la sortie Pandora, l'enregistrement du MCM, les conditions, les temps de recharge et l'éligibilité des acteurs. Confirmez que le contexte de test satisfait réellement les règles configurées.

### Trop d'événements

Réduisez la fréquence et la probabilité des approches, augmentez les temps de recharge, utilisez `OnlyinTown` ou d'autres limites contextuelles si approprié et désactivez les catégories d'événements facultatives jusqu'à stabilisation de la boucle de base.

### Les événements s'empilent ou se font concurrence

Réduisez les chevauchements avec SLHH, BaboDialogue, SexLab Survival, les systèmes de défaite et les autres mods d'événements autonomes. Réactivez les intégrations une par une et laissez suffisamment de temps entre les événements.

### Le MCM contient des champs manquants ou étranges

Assurez-vous que le fichier vide `SLAppAutoMCM.json` de la version 3.62 gagne face à tout ancien fichier généré dans `SKSE Output`. N'importez pas aveuglément le preset historique de version 2. Laissez le MCM actuel s'initialiser proprement.

### xEdit signale l'avertissement VMAD connu

Ne le nettoyez pas automatiquement et ne reconstruisez pas les alias sans preuve faisant autorité. Testez en jeu la branche `AskForSex2` / ask-other et surveillez le dialogue, la scène et la récupération qui en résultent.

### Un PNJ ou le joueur reste bloqué

Cessez d'utiliser la sauvegarde concernée comme sauvegarde stable. Reproduisez le problème sur le profil jetable, réduisez les systèmes autonomes voisins et identifiez le mod qui contrôle encore le dialogue, les commandes, le package de l'acteur ou la scène. Revenez au profil de test précédent si une récupération propre ne peut pas être établie.

## Statut de validation et avertissement

Les points suivants sont validés pour SexLab Approach Redux 3.62 dans l'intégration NEFARAM documentée :

- installation technique ;
- examen des conflits de fichiers MO2 ;
- disponibilité des frameworks requis dans NEFARAM ;
- workflow Pandora propre ;
- initialisation propre du MCM avec le JSON vide fourni ;
- affichage correct des réglages actuels et des options de compatibilité ;
- documentation de l'unique avertissement xEdit connu.

La validation complète en jeu, les rares cas limites, la longévité des sauvegardes et le réglage de la coexistence à long terme dépendent toujours des systèmes activés et choix MCM de chaque utilisateur. Ce guide ne revendique pas une compatibilité universelle.

> **Aucun patch personnalisé n'est requis pour cette intégration.**

## Référence technique interne

Pour l'audit détaillé et le protocole de test, consultez le [document interne d'intégration de SexLab Approach Redux](../../../06%20-%20GAMEPLAY/SEXLAB%20APPROACH%20REDUX/SEXLAB-APPROACH-REDUX-INTEGRATION.md).
