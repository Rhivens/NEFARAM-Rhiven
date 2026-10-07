# NEFARAM - Installation du Creation Kit via MO2

> Version Markdown du guide Word original : [NEFARAM_Guide_Installation_Creation_Kit_MO2_FR.docx](./NEFARAM_Guide_Installation_Creation_Kit_MO2_FR.docx)

## Installer le Creation Kit dans NEFARAM via MO2

*Adaptation NEFARAM 2026 d'un ancien guide Nolvus.*

**Conclusion de l'analyse :** le principe du guide Nolvus reste valable, mais plusieurs étapes sont devenues obsolètes. Pour un NEFARAM actuel, il ne faut pas appliquer automatiquement les anciens manifests Steam, le downgrade du Creation Kit vers 1.6.438 ni l'ancienne pile SSE CreationKit Fixes. La méthode moderne consiste d'abord à vérifier la version du Game Root, puis à utiliser le Creation Kit actuel si le runtime NEFARAM est compatible.

## 1. Ce qui est transposable du guide Nolvus

- Le Creation Kit doit être lancé depuis MO2 afin qu'il voie le système de fichiers virtuel et les plugins actifs.
- L'AppID Steam du Creation Kit reste `1946180`.
- Le binaire `CreationKit.exe` doit être lancé avec comme dossier de travail le dossier racine du jeu utilisé par la modlist.
- Dans NEFARAM, le dossier équivalent au « STOCK GAME » de Nolvus est :

  ```text
  C:\JEUX\NEFARAM\Game Root
  ```

- Il est préférable d'isoler clairement les fichiers du Creation Kit et de conserver une méthode reproductible.

## 2. Ce qu'il ne faut pas reprendre tel quel de l'ancien guide

- Ne pas utiliser par défaut les anciens manifests Steam indiqués dans le guide Nolvus.
- Ne pas downgrader automatiquement `CreationKit.exe` vers la branche 1.6.438.
- Ne pas considérer SSE CreationKit Fixes 3.2 / FaceFXWrapper comme la solution principale moderne.
- Ne pas recopier aveuglément les chemins Nolvus ; NEFARAM utilise son propre Game Root.

L'ancien guide était construit pour une combinaison précise de Nolvus et d'une ancienne version du Creation Kit. Le Creation Kit et ses outils de correction ont beaucoup évolué depuis.

## 3. Pré-vérification obligatoire avant installation

Avant de copier quoi que ce soit dans NEFARAM, vérifier la version exacte du runtime Skyrim utilisé dans :

```text
C:\JEUX\NEFARAM\Game Root\SkyrimSE.exe
```

Sous Windows : **clic droit sur SkyrimSE.exe → Propriétés → Détails → Version du produit**.

Si le Game Root NEFARAM utilise Skyrim 1.6.1170, la documentation moderne du Creation Kit indique que la version actuelle du CK peut être utilisée sans downgrade spécial. Si le runtime NEFARAM est différent, suspendre l'installation et adapter la procédure avant de poursuivre.

## 4. Installation recommandée pour NEFARAM

### 4.1 Installer le Creation Kit depuis Steam

1. Dans Steam, afficher également les logiciels / outils si nécessaire.
2. Rechercher « Skyrim Special Edition: Creation Kit ».
3. Installer le Creation Kit dans l'installation Skyrim Steam normale, pas directement dans NEFARAM.
4. Lancer le Creation Kit une première fois depuis Steam si Steam l'exige, puis le fermer.

### 4.2 Copier le Creation Kit dans le Game Root NEFARAM

Avant cette étape, effectuer une sauvegarde ou au minimum une liste des fichiers ajoutés. Le but est de pouvoir retirer proprement le Creation Kit sans toucher au cœur de NEFARAM.

Depuis le dossier Skyrim Steam dans lequel le Creation Kit a été installé, copier les fichiers du Creation Kit vers :

```text
C:\JEUX\NEFARAM\Game Root
```

Les fichiers concernés comprennent au minimum `CreationKit.exe` et les fichiers / dossiers fournis avec le Creation Kit. Ne remplacez pas des fichiers du Game Root NEFARAM sans vérifier leur provenance et leur version.

## 5. Creation Kit Platform Extended (recommandé)

Pour un environnement moddé lourd comme NEFARAM, **Creation Kit Platform Extended (CKPE)** est aujourd'hui la solution moderne à privilégier pour améliorer stabilité, compatibilité et performances du Creation Kit.

https://www.nexusmods.com/skyrimspecialedition/mods/71371

La branche actuelle de CKPE prend en charge plusieurs versions du Creation Kit, y compris les versions récentes. Choisir la variante correspondant au processeur : version normale pour les CPU avec AVX2 ; variante « No AVX2 » uniquement pour les processeurs anciens.

CKPE possède également sa propre Address Library pour le Creation Kit. Suivre les prérequis de la version CKPE choisie et ne pas confondre cette Address Library avec celle utilisée par SKSE dans Skyrim.

## 6. Ajouter Creation Kit dans MO2

Dans **Mod Organizer 2 → Executables → Add / Edit** :

- **Title :** Creation Kit
- **Binary :**

  ```text
  C:\JEUX\NEFARAM\Game Root\CreationKit.exe
  ```

- **Start in :**

  ```text
  C:\JEUX\NEFARAM\Game Root
  ```

- **Arguments :** laisser vide
- Cocher **Override Steam AppID** et saisir :

  ```text
  1946180
  ```

L'option « Force load libraries » figurait dans le guide Nolvus historique. Ne l'activer que si la configuration actuelle de MO2 / CKPE l'exige explicitement ; elle ne doit pas être considérée comme obligatoire par défaut.

## 7. Premier lancement

1. Lancer Creation Kit depuis MO2, jamais directement depuis l'Explorateur pour le travail sur NEFARAM.
2. Vérifier que la fenêtre principale du Creation Kit s'ouvre correctement.
3. Si CKPE est installé, terminer son assistant d'initialisation au premier lancement.
4. Les avertissements lors du chargement des masters Bethesda sont fréquents ; « Yes to All » est généralement attendu pour les fichiers vanilla.
5. Fermer le Creation Kit après ce premier test réussi.

Les anciens guides indiquent parfois que le Creation Kit extrait des milliers de scripts au premier lancement. Les procédures modernes peuvent gérer ces scripts différemment ; ne supprimez ni ne déplacez des scripts au hasard si un message apparaît.

## 8. Validation spécifique à NEFARAM

Avant de considérer l'installation comme validée :

- Creation Kit démarre depuis MO2.
- Le sélecteur **File > Data** affiche les masters Skyrim et les plugins visibles dans le profil **ELEANOR Stable**.
- Un plugin de test peut être chargé sans erreur bloquante.
- Le Creation Kit ne modifie pas le load order simplement parce qu'il a été lancé.
- Aucun fichier inattendu n'apparaît dans MO2 Overwrite après un simple lancement / fermeture.
- Si des fichiers sont générés, les identifier et les isoler dans un mod dédié avant toute utilisation réelle.

## 9. Si NEFARAM n'utilise pas Skyrim 1.6.1170

Ne pas appliquer automatiquement l'ancien downgrade Nolvus. La méthode moderne recommandée est alors de gérer le Creation Kit comme un ensemble de fichiers séparé et de choisir une version du CK compatible avec le runtime et les plugins actuels, éventuellement via Steam Depot.

Dans ce cas, utiliser la documentation moderne du Creation Kit pour sélectionner la version appropriée et, si nécessaire, CKPE pour permettre à un ancien Creation Kit de lire les headers de plugins modernes.

Le guide Nolvus utilisait les commandes Steam Depot et un patcher de downgrade adaptés à son époque. Ces identifiants ne doivent être réutilisés que si leur pertinence pour notre runtime NEFARAM a été confirmée.

## 10. Dépannage

### 10.1 Creation Kit semble démarrer mais aucune fenêtre n'apparaît

Sur les installations gérées manuellement ou avec une version de Skyrim différente de la dernière version Steam, une version incorrecte de `steam_api64.dll` peut empêcher le Creation Kit de s'ouvrir. Vérifier la méthode d'installation et la version utilisée.

### 10.2 Message indiquant qu'un MASTERFILE est trop récent

Ce problème peut apparaître avec un ancien Creation Kit face aux headers de plugins modernes. Creation Kit Platform Extended est précisément conçu pour améliorer cette compatibilité.

### 10.3 Warnings au chargement des masters

Des warnings sont normaux lors du chargement des masters Bethesda. S'ils n'empêchent pas l'ouverture du CK, ils ne signifient pas nécessairement que l'installation est défectueuse.

## 11. Checklist NEFARAM

- [ ] Version de `C:\JEUX\NEFARAM\Game Root\SkyrimSE.exe` vérifiée.
- [ ] Creation Kit installé depuis Steam dans l'installation Skyrim normale.
- [ ] Fichiers CK copiés de manière contrôlée vers le Game Root NEFARAM.
- [ ] Creation Kit Platform Extended installé si retenu.
- [ ] Pré-requis CKPE / CK Address Library vérifiés.
- [ ] Exécutable Creation Kit ajouté dans MO2.
- [ ] Binary = `C:\JEUX\NEFARAM\Game Root\CreationKit.exe`
- [ ] Start in = `C:\JEUX\NEFARAM\Game Root`
- [ ] Override Steam AppID = `1946180`
- [ ] Premier lancement effectué depuis MO2.
- [ ] **File > Data** voit correctement les masters et plugins du profil.
- [ ] MO2 Overwrite contrôlé après le premier lancement.

## 12. Sources et adaptation

Cette fiche a été créée à partir de l'ancien guide « Installing the Creation Kit for NOLVUS », puis adaptée au contexte NEFARAM actuel. Les parties historiques Nolvus (Steam Depot précis, downgrade 1.6.438, ancienne pile SSE CreationKit Fixes) ont été conservées comme référence d'analyse mais ne sont pas retenues comme procédure par défaut.

Documentation moderne consultée :

- https://www.nexusmods.com/skyrimspecialedition/articles/12296
- https://www.nexusmods.com/skyrimspecialedition/mods/71371
