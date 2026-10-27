# Lakeview Manor - As It Should Be

Ce guide décrit l'installation sûre et l'ordre de construction Hearthfire à respecter pour **Lakeview Manor - As It Should Be** dans une configuration NEFARAM.

Le mod modifie la maison principale de Lakeview Manor et, selon les choix effectués dans le FOMOD, sa cave et ses extérieurs. Il repose sur un état de construction Hearthfire précis : l'ordre de construction de la maison de base, des ailes, du mobilier et des éléments de la cave est donc important. Du mobilier supplémentaire ou des ailes différentes peuvent désynchroniser l'état de construction vanilla de l'agencement attendu par le mod.

> **Avertissement — modification communautaire :** sauvegardez votre profil NEFARAM et créez une sauvegarde nommée avant toute installation ou construction. Ne testez pas cette procédure pour la première fois sur votre unique sauvegarde de longue durée.

## Prérequis et précautions

Avant de commencer :

- utilisez un gestionnaire de mods et lisez chaque option du FOMOD ;
- créez une sauvegarde nommée avant toute construction à Lakeview et, si possible, copiez-la hors du dossier actif des sauvegardes ;
- terminez les quêtes préalables données par le Jarl de Falkreath ;
- achetez le terrain de Lakeview Manor ;
- évitez de construire du mobilier supplémentaire avant les étapes de transformation exigées par le mod ;
- si Lakeview est déjà largement construit dans la sauvegarde actuelle, ne supposez pas que cette procédure puisse reconstruire ou annuler ces choix sans risque ;
- n'utilisez le patch de compatibilité facultatif Creation Club Fishing que si CC Fishing est présent et si le patch s'applique à votre configuration.

Si vous n'avez jamais construit de maison Hearthfire, l'auteur du mod conseille de vous entraîner d'abord : construisez la maison vanilla complète et ses ailes pour comprendre le système, puis revenez à la sauvegarde nommée créée avant cet essai.

## Branches d'installation

Le FOMOD propose deux fichiers principaux indépendants l'un de l'autre, ainsi que des fichiers facultatifs. Suivez la branche de construction correspondant à votre installation.

### `LKVM Main House`

Cette branche couvre la refonte de la maison principale. Suivez les étapes 1 à 11 ci-dessous, puis les étapes 12 à 14 pour la cave et les extérieurs lorsque ces éléments font partie de votre installation.

### `LKVM Cellar and Exterior`

S'il s'agit du seul fichier principal installé, ignorez les étapes de construction de la maison principale et passez directement aux étapes 12 à 14.

L'instantané d'ordre de chargement Rhiven regroupe les fichiers Lakeview dans sa zone existante dédiée aux maisons. Considérez cela comme une référence de placement propre à NEFARAM/Rhiven, et non comme l'obligation de créer ou de copier un nom de séparateur personnalisé. Préservez l'ordre relatif pertinent des fichiers correspondant à vos choix FOMOD et déterminez leur placement dans le panneau droit à partir des conflits réels.

## Procédure de construction de l'auteur

Suivez exactement cet ordre.

1. Créez une sauvegarde nommée et, de préférence, sauvegardez-en une copie.
2. Téléchargez et installez le mod avec votre gestionnaire de mods. Laissez le FOMOD vous guider dans la sélection des deux fichiers principaux indépendants et des éventuels fichiers facultatifs.
3. Achetez le terrain de Lakeview si vous ne le possédez pas encore. Terminez d'abord les quêtes préalables du Jarl de Falkreath.
4. Rendez-vous à Lakeview.
5. Sélectionnez la branche correcte :
   - si `LKVM Main House` est installé, poursuivez avec les étapes 6 à 11 ;
   - si seul `LKVM Cellar and Exterior` est installé, passez aux étapes 12 à 14.
6. Activez la Drafting Table et construisez `Small House Layout`. Activez ensuite le Carpenter's Workbench et construisez tous ses éléments structurels, y compris les murs et le sol.
7. Répétez la procédure de construction pour :
   - `Main Hall`
   - `East Wing – Kitchen`
   - `North Wing – Alchemy Laboratory`
   - `West Wing – Bedroom`
8. Revenez à la Drafting Table et sélectionnez `remodel house into entryway`.
9. Entrez dans la maison.
10. Sur l'établi de la chambre, construisez uniquement :
    - `Child's Bed & Chest x 2`
    - `Double Bed`

    > **NE CONSTRUISEZ RIEN D'AUTRE SUR L'ÉTABLI DE LA CHAMBRE.**

11. Revenez à la Drafting Table à l'extérieur et désactivez tous les établis.
12. Construisez la cave. Entrez-y et construisez uniquement :
    - `Child Practice Dummy`

    > **NE CONSTRUISEZ RIEN D'AUTRE DANS LA CAVE.**

13. Sortez de la cave et désactivez son établi.
14. Construisez `Animal Pen`, `Garden`, `Apiary` et `Stable` si ces éléments ne l'ont pas déjà été.

## Procédure de test sûre

1. Conservez intactes la sauvegarde nommée antérieure à la construction et sa copie.
2. Effectuez toute la séquence de construction sur une copie de test ou une sauvegarde dont la récupération est garantie.
3. Vérifiez l'extérieur de la maison, l'entrée, l'intérieur principal et le mobilier prévu.
4. Vérifiez la cave et le mannequin d'entraînement requis.
5. Vérifiez l'enclos, le jardin, le rucher et l'écurie lorsqu'ils sont construits.
6. Si le patch facultatif CC Fishing est actif, vérifiez également l'intégration Fishing concernée.
7. Entrez dans la maison et la cave, puis ressortez-en ; sauvegardez ensuite, quittez complètement le jeu et rechargez avant de reprendre une partie normale.

Ne considérez pas une première entrée réussie comme une validation complète. Examinez attentivement l'agencement construit avant de conserver ce résultat pour une partie longue.

## Dépannage

### Les mauvaises ailes ont été sélectionnées

La procédure de l'auteur exige précisément les ailes Kitchen, Alchemy Laboratory et Bedroom. Arrêtez le test et revenez à la sauvegarde nommée antérieure à la construction au lieu de supposer qu'une autre combinaison d'ailes est prise en charge.

### Du mobilier supplémentaire a été construit dans la chambre

La consigne relative à la chambre est volontairement restrictive. Revenez à la sauvegarde nommée antérieure à la construction et répétez la procédure en ne construisant que les deux ensembles `Child's Bed & Chest` et le `Double Bed`.

### Des objets supplémentaires ont été construits dans la cave

La consigne relative à la cave est elle aussi volontairement restrictive. Revenez à la sauvegarde nommée antérieure à la construction et ne construisez que le `Child Practice Dummy` dans la cave.

### Les établis n'ont pas été désactivés

Revenez à l'étape correspondante si l'état de la sauvegarde actuelle le permet encore : désactivez tous les établis extérieurs après les étapes de la maison principale, puis celui de la cave après en être sorti. Si l'état est incertain, revenez à la sauvegarde de secours et recommencez proprement toute la séquence.

### La cave a été mal construite

N'ajoutez pas d'autres objets dans l'espoir de la corriger. Comparez l'état de la sauvegarde aux étapes 12 et 13, puis revenez à la sauvegarde nommée antérieure à la construction si l'état requis ne peut pas être confirmé.

### Le mod a été installé alors que la maison était déjà largement construite

Ce guide n'établit aucune procédure de conversion sûre pour une Lakeview Manor existante déjà largement construite. Conservez cette sauvegarde intacte, testez le mod depuis une sauvegarde antérieure à la construction ou jetable et consultez la documentation de l'auteur avant toute tentative de migration.

### L'agencement semble toujours incorrect

Vérifiez la branche installée, les ailes sélectionnées, les deux étapes restrictives relatives au mobilier, la désactivation des établis et tout patch de compatibilité facultatif applicable à votre configuration. N'inventez pas de commandes console correctives et ne continuez pas à ajouter du mobilier : revenez en arrière et reproduisez d'abord la séquence documentée.

## Statut de validation

### Procédure de l'auteur

La séquence de construction et les deux restrictions strictes concernant le mobilier proviennent de la procédure de l'auteur du mod.

### Tests du mainteneur

Le mainteneur a personnellement suivi et validé cette séquence exacte dans deux environnements Skyrim distincts :

- **Nolvus**
- **NEFARAM 16**

Il s'agit d'une confirmation pratique utile de la procédure, et non d'une garantie universelle pour tous les ordres de chargement, tous les états de sauvegarde ou toutes les personnalisations ultérieures de NEFARAM 17.x. Effectuez des tests sûrs dans votre propre environnement avant de poursuivre une partie longue.

## Référence interne

Pour les notes d'intégration Rhiven maintenues, la pile exacte de fichiers locaux et le statut de la version actuelle, consultez :

[Documentation interne de Lakeview Manor - As It Should Be](../../../07%20-%20HOMES/LAKEVIEW-MANOR-AS-IT-SHOULD-BE.md)
