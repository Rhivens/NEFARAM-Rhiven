# NEFARAM-Rhiven — Étude préliminaire d’intégration de Naked Defeat 6.51

> **Statut : OUVERTE — DESCRIPTION DU PATCH ATTENDUE — COMPATIBILITÉ NON ÉVALUÉE**
>
> Cette fiche prépare l’étude du patch **Naked Defeat 6.51** dans NEFARAM-Rhiven.
>
> Elle ne décrit pas le contenu du patch, ne suppose aucune modification technique et ne valide aucune compatibilité. Ces éléments seront renseignés uniquement après réception de la description, du changelog et, si nécessaire, des fichiers à auditer.
>
> Les documents consacrés à Naked Defeat 6.50 restent inchangés et constituent la référence de départ.

---

## 1. Objet de la fiche

Cette fiche distincte doit permettre de :

- conserver la configuration 6.50 validée comme point de comparaison ;
- enregistrer la description exacte du patch 6.51 lorsqu’elle sera fournie ;
- identifier les fichiers, scripts, plugins, réglages et dépendances concernés ;
- déterminer si le patch modifie l’architecture Acheron → Bridge → Naked Defeat ;
- vérifier si le correctif Rhiven 6.50 reste nécessaire, doit être adapté ou devient obsolète ;
- préparer les contrôles statiques et les essais en jeu ;
- produire un verdict documenté sans modifier prématurément les guides existants.

Cette fiche n’autorise aucune installation sur le profil stable et ne remplace pas le guide d’intégration 6.50.

---

## 2. Référence actuelle avant étude de la 6.51

### Environnement documenté pour la 6.50

- **NEFARAM 17.3.8**
- Skyrim AE runtime **1.6.1170**
- Acheron **1.11.3**
- Naked Defeat **6.50**
- Mod Organizer 2
- xEdit / SSEEdit **4.1.5f**
- Open Animation Replacer
- Pandora Behaviour Engine+
- profil de test : `Eleanor 17.3.8 - Naked Defeat`

### Architecture de référence

```text
Acheron
├─ Simple Recover
├─ Diary of Mine Extension
└─ Acheron - Naked Defeat Bridge
   └─ Naked Defeat 6.50
      └─ Naked Defeat - Rhiven Fix
```

Flux de référence :

> **Acheron → Acheron - Naked Defeat Bridge → Naked Defeat**

Ordre interne documenté :

> **Naked Defeat.esp → Naked Defeat - Rhiven Fix.esp → Acheron - Naked Defeat Bridge.esp**

### État 6.50 à préserver comme témoin

- Yamete Kudasai est entièrement désactivé.
- Practical Defeat Reanimated et son voicepack sont désactivés.
- OAR Bowed est actif et OAR Crawl est désactivé.
- le Bridge Acheron a passé son contrôle statique ;
- le Rhiven Fix corrige quatre enregistrements et a passé son contrôle xEdit ;
- `IndecencyRapeProb = 0` est obligatoire dans la configuration 6.50 documentée en raison de la quête Civilian Rape absente ;
- les tests humanoïde, créature, récupération du bleedout, événements répétés et sauvegarde/rechargement ont été validés ;
- le test avec follower, le réglage MCM final et le verdict définitif pour le profil stable restent ouverts ;
- les observations Bathing in Skyrim / Golden Shower restent considérées comme mineures et non bloquantes.

> Ces résultats appartiennent à la **6.50 uniquement**. Ils ne doivent pas être transférés automatiquement à la 6.51.

---

## 3. Informations attendues sur le patch 6.51

Les éléments suivants doivent être fournis ou obtenus avant toute conclusion :

- [ ] description exacte du patch ;
- [ ] changelog complet ;
- [ ] source et nom exact du téléchargement ;
- [ ] nature du paquet : patch incrémental, remplacement complet ou autre ;
- [ ] version de Naked Defeat requise comme base ;
- [ ] instructions officielles d’installation et de mise à jour ;
- [ ] compatibilité annoncée avec les sauvegardes existantes ;
- [ ] nécessité éventuelle d’une nouvelle partie ou d’une procédure particulière ;
- [ ] nécessité éventuelle de relancer FNIS ou Pandora ;
- [ ] dépendances ajoutées, supprimées ou mises à jour ;
- [ ] fichiers ajoutés, supprimés ou remplacés ;
- [ ] plugins ESP/ESL/ESM concernés ;
- [ ] scripts Papyrus concernés ;
- [ ] modifications OAR, animations, sons, JSON, MCM ou SLATE ;
- [ ] correctifs communautaires intégrés, remplacés ou rendus incompatibles ;
- [ ] incompatibilités et limitations connues.

Aucune case de cette section ne doit être validée par déduction à partir de la 6.50.

---

## 4. Périmètre de l’audit futur

### 4.1 Comparaison des paquets

- [ ] inventorier l’archive 6.51 ;
- [ ] comparer l’arborescence avec la 6.50 ;
- [ ] identifier les fichiers nouveaux, modifiés et supprimés ;
- [ ] vérifier les règles d’écrasement dans MO2 ;
- [ ] contrôler les scripts, configurations, JSON, sons et animations concernés ;
- [ ] confirmer si le paquet doit remplacer ou compléter l’installation 6.50.

### 4.2 Audit plugin et xEdit

- [ ] lancer Check for Errors sur les plugins concernés ;
- [ ] comparer les enregistrements modifiés avec la 6.50 ;
- [ ] vérifier les masters et les nouveaux FormID ;
- [ ] vérifier les VMAD, quêtes, aliases, scènes, packages et dialogues touchés ;
- [ ] rechercher les références manquantes ou mal typées ;
- [ ] vérifier si les quatre corrections du Rhiven Fix sont intégrées nativement ;
- [ ] vérifier si le Rhiven Fix crée de nouveaux conflits avec la 6.51 ;
- [ ] réexaminer la propriété `qst2` et la fonction Civilian Rape ;
- [ ] définir un nouvel ordre de chargement uniquement si les résultats l’exigent.

### 4.3 Audit Acheron et récupération

- [ ] confirmer que le Bridge reste compatible ;
- [ ] vérifier l’événement `StartNakedDefeatExternal` et le passage des assaillants ;
- [ ] vérifier la prise en charge des assaillants multiples ;
- [ ] vérifier `RescueActor`, `ReleaseActor` et les états Acheron ;
- [ ] confirmer la sortie correcte du bleedout ;
- [ ] confirmer la libération des assaillants et l’absence de pacification permanente ;
- [ ] vérifier qu’aucun second système de défaite ne reprend l’événement.

### 4.4 Audit animations et comportements

- [ ] vérifier les modifications OAR ;
- [ ] comparer les conditions et priorités des paquets Bowed et Crawl ;
- [ ] confirmer si la règle **Bowed actif / Crawl désactivé** reste applicable ;
- [ ] déterminer si une régénération Pandora est nécessaire ;
- [ ] vérifier les éventuelles modifications FNIS ;
- [ ] vérifier SLATE et le tag d’Action Log attendu.

### 4.5 Audit MCM et dépendances

- [ ] relever les nouvelles options MCM ;
- [ ] relever les options supprimées ou renommées ;
- [ ] réévaluer `IndecencyRapeProb = 0` ;
- [ ] contrôler SexLab / SLU+ / SexLab P+ ;
- [ ] contrôler ZaZ Animation Pack ;
- [ ] contrôler les Papyrus Extenders ;
- [ ] contrôler Devious Devices NG, Bathing in Skyrim et Simple Slavery ;
- [ ] contrôler les patches communautaires présents dans le profil.

---

## 5. Règles de décision

### Porte A — Documentation reçue

La description et les instructions du patch sont disponibles et suffisamment précises pour déterminer son périmètre.

### Porte B — Audit statique terminé

Les différences de fichiers, plugins, scripts, OAR et dépendances ont été contrôlées. Les conflits éventuels sont identifiés et documentés.

### Porte C — Profil de test prêt

La 6.51 est installée uniquement sur un profil MO2 dédié ou cloné, avec sauvegarde de la configuration 6.50 et possibilité de retour arrière.

### Porte D — Tests en jeu terminés

Les scénarios concernés par le patch ainsi que les tests de non-régression sont exécutés sans état bloqué ni corruption de la chaîne Acheron.

### Porte E — Documentation finalisée

Le verdict, les réglages, l’ordre de chargement, les limites et la procédure de rollback sont consignés. Les guides 6.50 ne sont modifiés que si une mise à jour documentaire séparée est décidée.

> La compatibilité ne pourra être déclarée qu’après le passage des portes applicables. La présence d’une version 6.51 ou le succès d’un seul lancement en jeu ne constituent pas une validation.

---

## 6. Plan de tests préliminaire

Le détail sera adapté au changelog 6.51. Le socle minimal de non-régression est :

### Avant le test

- [ ] profil MO2 dédié ou cloné ;
- [ ] sauvegarde de test jetable ;
- [ ] sauvegarde de l’ordre de chargement 6.50 ;
- [ ] sauvegarde des réglages MCM pertinents ;
- [ ] archive 6.50 et Rhiven Fix conservés pour rollback ;
- [ ] absence de Practical Defeat et Yamete Kudasai dans la chaîne active ;
- [ ] état OAR et Pandora consigné.

### Cas minimaux

- [ ] défaite par humanoïde ;
- [ ] défaite par créature ;
- [ ] défaite avec follower ;
- [ ] assaillants correctement transmis par le Bridge ;
- [ ] scène Naked Defeat lancée et terminée ;
- [ ] sortie correcte du bleedout Acheron ;
- [ ] retour normal des contrôles ;
- [ ] assaillants libérés et non pacifiés de façon permanente ;
- [ ] stripping et conséquences d’inventaire ;
- [ ] absence d’animation bloquée ;
- [ ] plusieurs défaites dans la même session ;
- [ ] sauvegarde après un événement terminé ;
- [ ] fermeture complète du jeu ;
- [ ] rechargement et poursuite normale de la partie ;
- [ ] test ciblé de chaque fonction modifiée par la 6.51.

### Cas complémentaires selon le contenu du patch

- [ ] Local Slavery ;
- [ ] whipping ;
- [ ] capture game ;
- [ ] foreplay et sélection de scénarios ;
- [ ] transitions blur ;
- [ ] Bathing in Skyrim / Golden Shower ;
- [ ] SLATE / Action Log ;
- [ ] OAR Bowed / Crawl ;
- [ ] autres cas explicitement cités dans le changelog.

---

## 7. Sécurité et rollback

Jusqu’au verdict final :

- conserver l’installation 6.50 et ses archives ;
- conserver le Rhiven Fix sans le fusionner dans le plugin principal ;
- ne pas supprimer l’ESP d’une sauvegarde existante sans instruction vérifiée ;
- ne pas installer la 6.51 directement sur le profil stable ;
- ne pas nettoyer automatiquement les avertissements xEdit ;
- ne pas modifier les enregistrements sans symptôme ou preuve technique ;
- sauvegarder la liste des mods, l’ordre des plugins et la sortie Pandora ;
- restaurer la chaîne 6.50 si un test bloque la récupération, les contrôles, les acteurs ou la sauvegarde.

---

## 8. État de l’étude

### Préparation terminée

- [x] guide d’intégration 6.50 relu ;
- [x] référence Markdown 6.50 relue ;
- [x] document Word source 6.50 relu ;
- [x] architecture et décisions 6.50 consignées ;
- [x] fiche 6.51 créée séparément ;
- [x] périmètre d’audit préparé ;
- [x] plan de tests de non-régression préparé.

### En attente

- [ ] description du patch 6.51 ;
- [ ] changelog 6.51 ;
- [ ] fichiers ou lien de téléchargement à auditer ;
- [ ] instructions d’installation / mise à jour ;
- [ ] audit comparatif 6.50 → 6.51 ;
- [ ] audit xEdit et scripts ;
- [ ] décision sur le Rhiven Fix ;
- [ ] décision sur `IndecencyRapeProb` ;
- [ ] décision sur OAR et Pandora ;
- [ ] tests en jeu ;
- [ ] verdict de compatibilité ;
- [ ] décision de mise à jour des documents existants.

---

## 9. Verdict provisoire

> **AUCUN VERDICT DE COMPATIBILITÉ À CE STADE**
>
> La configuration Naked Defeat 6.50 documentée reste la seule référence validée pour NEFARAM-Rhiven. La 6.51 est placée en étude préliminaire jusqu’à réception de sa description et achèvement des audits nécessaires.

---

*Fiche d’étude préliminaire — NEFARAM-Rhiven.*
