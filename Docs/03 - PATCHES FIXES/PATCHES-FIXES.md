# Atelier Rhiven — Patches & fixes

Cette fiche est notre **aide-mémoire technique d’atelier** pour les correctifs spécifiques à **NEFARAM-Rhiven**.

Elle n’a pas vocation à être un guide communautaire. Elle conserve les détails utiles à la fabrication, à la maintenance et au diagnostic de nos patches : origine du conflit, records ou fichiers modifiés, gagnants retenus, ordre de chargement, validation xEdit / en jeu et logique de rollback.

> **Règle d’atelier :** ne jamais modifier directement un mod source lorsqu’un override Rhiven ciblé permet de corriger proprement le problème.

---

## 1. Archives de patches conservées dans ce dossier

Les ZIP présents dans ce dossier sont les **copies atelier / sources de référence** des correctifs Rhiven.

### 1.1 Naked Defeat - Rhiven Fix

**Archive :** `Naked Defeat - Rhiven Fix.zip`  
**Plugin :** `Naked Defeat - Rhiven Fix.esp`  
**Cible :** Naked Defeat 6.50

#### Pourquoi nous l’avons créé

L’audit xEdit de `Naked Defeat.esp` a remonté plusieurs warnings. La majorité correspondait à d’anciens restes de développement, branches inutilisées ou records non démontrés comme actifs : nous les avons volontairement laissés tranquilles.

Quatre records étaient en revanche clairement mal formés et pouvaient être corrigés sans toucher à l’architecture du mod.

#### Records corrigés

**ARMA — chaînes de poignets**

- `nade_WristChains_L`
- `nade_WristChains_R`

Les deux records contenaient dans `Additional Races` des entrées invalides de type `REFR`, pointant vers des références placées de balcon de grotte au lieu de records `RACE`.

**Correction :**
- suppression uniquement de ces entrées invalides ;
- aucune autre donnée ARMA modifiée.

**WEAP — armes Naked Defeat**

- `nade_BoneMace`
- `nade_Stick`

Les deux records contenaient un champ `CRDT - Critical Data > Effect` mal formé avec zéro octet de données.

La copie en override dans le patch a permis à xEdit de normaliser proprement le champ vers :

`NULL - Null Reference [00000000]`

**Correction :**
- aucune modification des stats, modèles ou paramètres de gameplay des armes ;
- uniquement normalisation du champ CRDT invalide.

#### Ordre de chargement retenu

```text
Naked Defeat.esp
Naked Defeat - Rhiven Fix.esp
Acheron - Naked Defeat Bridge.esp
```

Le Rhiven Fix doit charger **après Naked Defeat** afin que ses quatre corrections gagnent.

#### Validation

- xEdit Check for Errors :
  - **5 records traités**
  - **0 erreur**
- cœur gameplay Naked Defeat validé en jeu ;
- playtest étendu toujours en cours.

#### Note d’atelier

Ne pas utiliser ce patch comme prétexte pour « nettoyer » automatiquement les autres warnings Naked Defeat. Notre règle reste :

> **On ne corrige qu’un record dont le défaut est identifié, compris et justifié.**

---

### 1.2 PAMA - Windhelm Navmesh Patch - Rhiven

**Archive :** `PAMA - Windhelm Navmesh Patch - Rhiven.zip`  
**Plugin :** `PAMA - Windhelm Navmesh Patch - Rhiven.esp`  
**Type :** ESP avec flag ESL

#### Cibles

- Bad Ends Revived: Windhelm
- `PrisonAlternative_Executions_WindHelm.esp`
- WindhelmSSE / Exterior NavMesh Fixes
- Capital Windhelm Expansion
- intégration Skyrim Sewers associée

#### Pourquoi nous l’avons créé

Bad Ends Windhelm réintroduisait des données de navmesh anciennes / proches du vanilla par-dessus les corrections modernes déjà présentes dans NEFARAM-Rhiven.

Le problème ne venait donc pas du fonctionnement PAMA lui-même, mais du fait que son plugin tardif redevenait gagnant sur des navmeshes que notre stack Windhelm avait déjà corrigés.

#### Records concernés

- `000FC117` — `WindhelmBridge04`
  - gagnant retenu : `WindhelmSSE - Exterior NavMesh Fixes.esp`

- `0004B66C` — `WindhelmCandlehearthHallExterior`
  - gagnant retenu : `CapitalWindhelmExpansion - SkyrimSewers.esp`

#### Méthode de fabrication

- copie en override des navmeshes modernes corrects ;
- ajout explicite de `PrisonAlternative_Executions_WindHelm.esp` comme master ;
- aucun remodelage manuel du navmesh ;
- le patch sert uniquement à **rétablir les bons gagnants** après Bad Ends Windhelm.

#### Ordre de chargement

Le patch doit charger :
- après Bad Ends Windhelm ;
- après les plugins sources dont il reprend les navmeshes ;
- suffisamment tard pour conserver le résultat final voulu.

#### Validation

- xEdit Check for Errors :
  - **7 records traités**
  - **0 erreur**
- validation structurelle terminée ;
- surveillance du pathing longue durée maintenue pendant la vraie partie.

#### Logique de maintenance

Ne pas déplacer tout le bloc PAMA uniquement pour régler ces deux conflits : cela risquerait d’en créer ailleurs. Ce patch localise précisément le problème.

---

### 1.3 PAMA - NEFARAM ZaZ Ankle Chains Patch - Rhiven

**Archive :** `PAMA - NEFARAM ZaZ Ankle Chains Patch - Rhiven.zip`  
**Type :** override de fichier, sans ESP

#### Cibles

- Bad Ends Revived: Windhelm
- `NEFARAM Patches`
- ZaZ Animation Pack

#### Fichier concerné

`meshes\ZaZ-UltimateDataPack\ZaZ - HDT\ZaZAnkleChainsRagdolls_1.nif`

#### Pourquoi nous l’avons créé

Bad Ends Windhelm fournit sa propre copie du mesh de chaînes de chevilles ZaZ.

Comme notre bloc PAMA est volontairement placé tard dans MO2, cette copie ancienne devenait gagnante et écrasait la version déjà corrigée / adaptée par `NEFARAM Patches`.

#### Correction

Nous avons repris la version gagnante correcte provenant de `NEFARAM Patches` et l’avons placée dans un mod Rhiven dédié chargé après Bad Ends Windhelm.

#### Effet exact

Le patch ne modifie :
- aucun script ;
- aucun plugin ;
- aucun record xEdit.

Il impose uniquement la bonne version de :

`ZaZAnkleChainsRagdolls_1.nif`

dans le système de conflits de fichiers MO2.

#### Ordre MO2

`PAMA - NEFARAM ZaZ Ankle Chains Patch - Rhiven` doit charger après Bad Ends Windhelm afin de gagner ce conflit de mesh.

#### Validation

- conflit MO2 vérifié ;
- version NEFARAM restaurée comme gagnante ;
- statut : **correctif structurel appliqué**.

---

### 1.4 PAMA - Solitude Location Patch - Rhiven

**Archive :** `PAMA - Solitude Location Patch - Rhiven.zip`  
**Plugin :** `PAMA - Solitude Location Patch - Rhiven.esp`  
**Type :** patch minimal ESP avec flag ESL

#### Cible

- Bad Ends Revived: Solitude 1.8.0 Revision 2

#### Pourquoi nous l’avons créé

Dans `SolitudeWorld`, le record gagnant PAMA de :

`SolitudeOrigin [00037EE9]`

perdait l’information :

`XLCN - Location = SolitudeLocation [00018A5A]`

Nous voulions conserver les données de cellule apportées par PAMA **sans perdre l’appartenance à Solitude**.

#### Correction exacte

Le patch :
- copie le record gagnant PAMA de `SolitudeOrigin [00037EE9]` ;
- restaure uniquement :
  - `XLCN - Location = SolitudeLocation [00018A5A]`
- laisse les autres données PAMA de la cellule intactes.

#### Pourquoi nous n’avons pas fait de patch navmesh à Solitude

PAMA et `Animal_Research.esp` touchent le navmesh `000CAD79`, mais leurs zones réellement utilisées sont spatialement distinctes.

Le pathing observé en jeu fonctionnait correctement : Saffron quittait l’auberge, marchait à l’extérieur, utilisait son marker contre le mur puis rentrait normalement.

Décision :

> **Ne pas fusionner des navmeshes qui fonctionnent déjà.**

Un merge navmesh aurait ajouté du risque sans symptôme réel à corriger.

#### Validation

- xEdit Check for Errors :
  - **17 records traités**
  - **0 erreur**
- pathing Solitude observé en jeu : **OK**
- patch conservé uniquement pour le XLCN manquant.

---

### 1.5 PAMA - Falkreath LAND - Rhiven Fix

**Archive :** `PAMA - Falkreath LAND - Rhiven Fix.zip`  
**Plugin :** `Falkreath LAND - Rhiven Fix.esp`  
**Type :** ESPFE / ESL

#### Symptôme

Trou / cassure visible dans le terrain à l’entrée de Falkreath.

#### Zone exacte

- Worldspace : `Tamriel`
- cellule : **-9, -22**
- CELL : `00009C81`
- LAND : `0000AC81`

#### Cause réelle

Après inspection de la chaîne de conflits LAND, le gagnant tardif problématique était :

`PaOutdoorEventPack.esp`

Il réintroduisait un état LAND incorrect après la chaîne de compatibilité moderne.

Important pour notre mémoire :

> **Le trou n’était pas causé par Animal Mansion Reborn.**
>
> **Il ne provenait pas non plus du cœur PAMA lui-même.**
>
> La cause précise était l’override LAND de `PaOutdoorEventPack.esp`.

#### Correction retenue

Le bon état final du LAND était déjà présent dans :

`Northern Roads - COTN Falkreath - LFFGM patch.esp`

Nous avons donc :
1. copié `LAND 0000AC81` comme override dans un plugin Rhiven séparé ;
2. conservé les données du patch Northern Roads / COTN Falkreath / LFFGM ;
3. placé le Rhiven Fix après `PaOutdoorEventPack.esp`.

Aucun autre LAND ou CELL n’a été ajouté inutilement au patch.

#### Validation en jeu

- retour à l’entrée de Falkreath ;
- trou de terrain disparu ;
- continuité du terrain restaurée ;
- correctif **validé en jeu**.

#### Générations

Aucun rerun nécessaire de :
- Synthesis ;
- xLODGen ;
- TexGen ;
- DynDOLOD.

Le correctif est suffisamment localisé pour ne pas justifier une nouvelle génération de la chaîne LOD déjà validée.

#### Autre observation

Un second petit raccord terrain en forêt, cellule `Tamriel -16,-26`, a été observé puis accepté tel quel. Il n’a pas justifié de second patch.

---

## 2. Autres correctifs / configurations Rhiven à retenir

Ces éléments ne correspondent pas forcément à un ZIP présent dans ce dossier, mais ils font partie de notre historique de corrections et restent utiles comme aide-mémoire.

### 2.1 Terrain Helper — configuration générée

- **Mod :** `Terrain Helper - Generated INI - Rhiven`
- **Fichier :** `Shaders\Features\TerrainHelper.ini`
- **Origine :** fichier généré dans MO2 Overwrite
- **Action :** déplacé dans un mod dédié
- **Pourquoi :** conserver Overwrite propre et rendre la configuration générée réversible / traçable.

---

### 2.2 EBT / Just Blood — séparation du sang corporel

- **Cibles :** Enhanced Blood Textures 4.0 + Just Blood - Dirt and Blood Lite
- **Patch :** `EBT - Just Blood Body Patch - Rhiven`
- **Problème :** EBT et Just Blood peuvent tous deux appliquer des effets de sang sur les acteurs.
- **Architecture retenue :**
  - **EBT = environnement**
  - **Just Blood = acteurs**
- **Correction :** neutraliser le sang corporel EBT et laisser Just Blood gérer les acteurs.
- **Placement :** le patch doit gagner après EBT dans le panneau gauche MO2.
- **Statut :** **VALIDÉ**
- **Plugin :** aucun ESP ajouté.

---

### 2.3 Bathing in Skyrim Renewed / Widget Addon

- **Cibles :** Widget Addon 1.7.2 + Bathing in Skyrim Renewed 2.7.11
- **Problème :** le Widget Addon original cible l’ancien Bathing in Skyrim.
- **Correction retenue :** utiliser l’option de compatibilité Widget Addon du FOMOD BiSR.
- **Placement :** Widget Addon au-dessus de BiSR afin que les fichiers Renewed gagnent.
- **Statut historique :** validé.
- **État actuel :** le Widget Addon a ensuite été retiré de la couche d’affichage finale au profit de **Needs Widget AIO** ; conserver cette note uniquement comme historique de compatibilité.

---

### 2.4 Wash Me / ConsoleUtil

- **Cible :** Bathing in Skyrim - Wash Me - Renewed
- **Question initiale :** installer ou non ConsoleUtilSSE NG recommandé en option.
- **Décision :** ne pas l’installer, NEFARAM utilisant déjà `ConsoleUtil Extended`.
- **Pourquoi :** éviter deux implémentations ConsoleUtil concurrentes.
- **Statut :** **VALIDÉ**.

---

### 2.5 Pandora — correction du chemin d’output

- **Outil :** Pandora Behaviour Engine
- **Problème :** le dossier de sortie pointait directement vers `Game Root\Data`.
- **Correction :**
  - Output Folder :
    `C:\JEUX\NEFARAM\mods\Pandora Output`
  - Skyrim Data :
    `C:\JEUX\NEFARAM\Game Root\Data`
- **Règle :** l’output pointe vers la racine du mod MO2 `Pandora Output`, pas vers `meshes` ni un sous-dossier.
- **Statut :** **VALIDÉ**.

---

### 2.6 Armures Eleanor — correctif d’enchantement à la demande

- **Cible :** pièces bikini / skimpy réellement rencontrées comme non enchantables.
- **Principe :** ne pas installer un correctif global spéculatif.
- **Méthode :**
  1. ouvrir le plugin source dans xEdit ;
  2. localiser le record `ARMO` concerné ;
  3. le copier comme override dans le patch personnel Rhiven ;
  4. ajouter uniquement le keyword d’enchantement manquant, en se basant sur une pièce équivalente fonctionnelle ;
  5. charger le patch après le plugin source ;
  6. tester en jeu.
- **Règle :** ne jamais éditer directement le plugin d’armure.
- **Statut :** **À LA DEMANDE**.

---

### 2.7 OMNOMS / O.S.H.I.T — Object Impact Framework

- **Cibles :** OMNOMS 1.3.0 + O.S.H.I.T + Object Impact Framework
- **Fichier :** `SKSE\Plugins\ObjectImpactFramework\OSHIT-OIF.json`
- **Problème :** la configuration O.S.H.I.T pouvait rendre les Mimics destructibles à l’impact, ce qui pouvait casser l’état Mimic/conteneur et rendre le loot inaccessible.
- **Correction :** activer le `OSHIT Patch` d’OMNOMS et laisser sa version de `OSHIT-OIF.json` gagner.
- **Priorité gauche observée :** TNTR → EET → O.S.H.I.T → OMNOMS → Deadly Bear Trap → Watch Your Step.
- **Règle :** OMNOMS doit rester sous O.S.H.I.T pour ce fichier précis.
- **Validation structurelle :** **OK**
- **Validation longue durée :** à surveiller pendant la partie réelle.

---

### 2.8 OMNOMS — distribution SkyPatcher

- **Framework :** `SkyPatcher - AE - Rhiven`
- **Distribution activée :**
  - Magic Vendors
  - Spell Tomes
- **Distribution désactivée :**
  - General Vendors
- **But :** distribuer le scroll `Banish Mimic` sans ajouter une distribution trop large.
- **Statut :** initialisation validée ; acquisition réelle à surveiller en jeu.

---

## 3. Méthode générale de fabrication d’un patch Rhiven

Quand un nouveau conflit est identifié :

1. **Identifier le symptôme réel** en jeu ou dans l’audit.
2. **Tracer le winning override** jusqu’au record ou fichier responsable.
3. Déterminer si le bon résultat existe déjà dans un plugin antérieur.
4. Préférer un **override minimal** au déplacement massif du load order.
5. Ne copier que les records nécessaires.
6. Ne jamais éditer directement le mod source si un patch séparé suffit.
7. Si possible, utiliser ESPFE / ESL pour ne pas consommer un slot lourd.
8. Lancer xEdit Check for Errors sur le patch.
9. Tester le symptôme initial en jeu.
10. Noter ici :
    - cause ;
    - record / fichier ;
    - gagnant retenu ;
    - placement ;
    - validation ;
    - besoin ou non de régénérer Synthesis / Pandora / BodySlide / LOD.
11. Conserver une archive atelier propre du patch quand il mérite d’être réutilisé ou publié.

---

## 4. Gabarit pour les prochains patches

### Nom du patch

- **Cibles :**
- **Symptôme :**
- **Cause identifiée :**
- **Plugin / fichier fautif :**
- **Records / fichiers concernés :**
- **Gagnant retenu :**
- **Correction appliquée :**
- **Type de patch :** ESP / ESPFE / ESL / fichiers seuls / config
- **Ordre de chargement :**
- **Validation xEdit :**
- **Validation en jeu :**
- **Régénérations nécessaires :**
- **Rollback :**
- **Notes d’atelier :**
