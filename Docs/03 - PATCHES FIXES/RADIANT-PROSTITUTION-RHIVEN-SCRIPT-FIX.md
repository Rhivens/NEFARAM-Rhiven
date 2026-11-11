# Radiant Prostitution — Rhiven Script Fix V0.1

> **Atelier interne — NEFARAM-Rhiven 17.3.8**  
> Date : 11 novembre 2026  
> Auteur de l'intervention : Rhiven / Iris Modding Studio  
> **Statut : correctif compilé et installé ; premiers tests en jeu réussis ; validation du cas d'erreur initial encore à terminer.**

## 1. Pourquoi ce correctif existe

Sur le profil **Eleanor Stable 17.3.8** de NEFARAM, des lancements de scènes via **Radiant Prostitution** posaient problème dans certaines conditions. Le diagnostic s'est concentré sur les appels à **SexLab**, notamment :

- la vérification de disponibilité des acteurs (`ValidateActor`) ;
- l'ajout des acteurs dans un thread (`AddActor`) ;
- la création / initialisation d'un thread SexLab (`NewThread`) ;
- les situations où un acteur est déjà engagé dans une animation ou porte un état SexLab incompatible.

**Objectif de la V0.1 :** rendre le traitement de ces cas plus prudent et faciliter leur diagnostic, sans modifier le mod Radiant Prostitution d'origine.

> Ne pas confondre ce problème avec le **blocage des commandes d'Eleanor après certaines scènes non consenties**. L'enquête sur ce second incident pointe notamment vers les routines de fin de scène de SexLab Approach ; aucun lien causal avec le patch Radiant n'est démontré.

## 2. Périmètre du patch

| Élément | Valeur |
|---|---|
| Type | Remplacement ciblé d'un script Papyrus compilé |
| Script | `Scripts/mf_handler.pex` |
| Source de travail | `Source/Scripts/mf_handler.psc` |
| Mod MO2 | `Rhiven - Radiant Prostitution Fix` |
| Version atelier | V0.1 |
| Plugin ESP/ESL | **Aucun** |
| Script original | Conservé dans le mod Radiant Prostitution |

La V0.1 est une **modification du script `mf_handler`** ; elle n'est pas une mise à jour officielle de Radiant Prostitution. Le détail ligne par ligne doit être établi à partir du **diff exact des deux sources** avant toute publication technique affirmant les branches modifiées.

### Fichiers validés à l'assemblage

- Original `mf_handler.pex` : **37 203 octets** ;
- Version compilée V0.1 : **38 356 octets** ;
- Compilation Bethesda Papyrus : **0 erreur, 0 avertissement ; 1 réussite, 0 échec**.

La différence de taille confirme la présence d'un binaire distinct, **pas à elle seule la correction du problème**.

## 3. Installation et priorité MO2

Ordre vérifié dans le panneau gauche de MO2 :

```text
2591  Radiant Prostitution
2592  Radiant Prostitution - FR
2593  Rhiven - Radiant Prostitution Fix
```

Le patch est placé **après** le mod principal et la traduction française.

Dans l'onglet **Conflicts** de MO2 :

- `Rhiven - Radiant Prostitution Fix` **écrase** `Radiant Prostitution` pour `Scripts/mf_handler.pex` ;
- aucun mod ne semble ensuite écraser le fichier fourni par le correctif.

**Attention :** cet ordre concerne la **priorité de fichiers du panneau gauche**, pas la position d'un ESP dans le panneau droit.

## 4. Compilation : pourquoi une méthode isolée était nécessaire

### Difficultés rencontrées

Les tentatives initiales avec **Papyrus Compiler App** (interface utilisée : version 2025.1) et l'environnement complet NEFARAM provoquaient une avalanche d'erreurs de dépendances (notamment dans de nombreux scripts sans rapport avec Radiant Prostitution).

Le répertoire source global du jeu contenait environ **14 301 scripts `.psc`**. Compiler contre tous ces fichiers faisait intervenir des scripts de mods tiers non nécessaires à `mf_handler`.

Autre difficulté observée : les paramètres régionaux Windows français, avec **virgule décimale**, ont occasionné des erreurs de valeurs par défaut sur certaines dépendances. Pour la compilation, le séparateur décimal Windows a été temporairement réglé sur `.`.

**À faire après la session de développement : restaurer `,` dans les paramètres régionaux Windows (`intl.cpl`).**

### Solution retenue

Utiliser directement le compilateur Bethesda avec **un ensemble réduit de sources**, en isolant les interfaces nécessaires :

```text
C:\JEUX\NEFARAM\
├── PapyrusBuild\
│   ├── IsolatedSources\
│   │   ├── SkyrimBase\
│   │   └── CompileInterfaces\
│   ├── TestOutput\
│   └── ReadyForMO2\
└── mods\
    ├── Rhiven - Radiant Prostitution Fix\
    │   ├── Source\Scripts\mf_handler.psc
    │   └── Scripts\mf_handler.pex
    └── Rhiven - Papyrus Compile Sources - TEST\
        └── Source\Scripts\
```

- `SkyrimBase` : sélection minimale d'environ **39 sources Papyrus de base** et du fichier de flags ;
- `Rhiven - Papyrus Compile Sources - TEST` : **137 fichiers PSC** de dépendances et interfaces nécessaires à la compilation ;
- `CompileInterfaces` : interfaces de compilation ciblées **à ne jamais déployer** ;
- `TestOutput` : sortie du compilateur ;
- `ReadyForMO2` : dossier de préparation du patch MO2.

### Commande PowerShell validée

```powershell
$compiler = "C:\JEUX\NEFARAM\Game Root\Papyrus Compiler\PapyrusCompiler.exe"
$patch = "C:\JEUX\NEFARAM\mods\Rhiven - Radiant Prostitution Fix\Source\Scripts"
$libs = "C:\JEUX\NEFARAM\mods\Rhiven - Papyrus Compile Sources - TEST\Source\Scripts"
$base = "C:\JEUX\NEFARAM\PapyrusBuild\IsolatedSources\SkyrimBase"
$interfaces = "C:\JEUX\NEFARAM\PapyrusBuild\IsolatedSources\CompileInterfaces"
$output = "C:\JEUX\NEFARAM\PapyrusBuild\TestOutput"
$flags = Join-Path $base "TESV_Papyrus_Flags.flg"

& $compiler "mf_handler.psc" `
    "-i=$patch;$interfaces;$libs;$base" `
    "-o=$output" `
    "-f=$flags"
```

La commande compile **uniquement `mf_handler.psc`**. Ne pas utiliser `-all` pour ce correctif.

### Cas particulier : interface SLO Aroused NG

Le script réel `slaFrameworkScr.psc` entraîne de nombreuses dépendances supplémentaires. Pour compiler `mf_handler` sans reconstruire SLO Aroused NG, une **interface de compilation provisoire** a été créée dans `CompileInterfaces` :

```papyrus
Scriptname slaFrameworkScr extends Quest
; Compile-only interface - NEVER DEPLOY

Int Function GetActorExposure(Actor who)
    Return 0
EndFunction

Int Function UpdateActorExposure(Actor who, Int exposureDelta, String debugMessage = "")
    Return 0
EndFunction
```

Ces fonctions existent dans la version inspectée de SLO Aroused NG, mais y sont marquées **deprecated**. L'interface artificielle ne sert **qu'à résoudre les signatures au moment de compiler**. Au lancement du jeu, le `mf_handler.pex` utilise normalement le **vrai script installé par SLO Aroused NG**.

> **INTERDICTION DE DÉPLOYER le `slaFrameworkScr.psc` artificiel ou un `slaFrameworkScr.pex` généré à partir de lui.** Cela remplacerait la logique réelle d'exposition par des fonctions factices et risquerait de casser d'autres mods.

Même principe pour les bibliothèques artificielles de `Rhiven - Papyrus Compile Sources - TEST` : **elles restent dans l'atelier, jamais dans le patch de jeu**.

## 5. Déploiement : isolation et retour arrière

Seul le **`Scripts/mf_handler.pex` compilé** doit prendre le dessus sur le script original dans MO2.

Chemin du fichier déployé :

```text
C:\JEUX\NEFARAM\mods\Rhiven - Radiant Prostitution Fix\Scripts\mf_handler.pex
```

Le mod principal `Radiant Prostitution` et sa traduction `Radiant Prostitution - FR` restent intacts.

**Rollback :** décocher uniquement `Rhiven - Radiant Prostitution Fix` dans le panneau gauche MO2, puis relancer le jeu sur une sauvegarde de test appropriée. Cela restaure la priorité des fichiers antérieurs ; **cela ne garantit pas** l'absence d'effets persistants dans une sauvegarde ayant déjà exécuté le script modifié.

## 6. Validation en jeu — journal du 11 novembre 2026

| Test | Résultat | Limite |
|---|---|---|
| Compilation `mf_handler.psc` | ✅ 0 erreur / 0 avertissement | Valide la syntaxe et les dépendances de compilation |
| Conflit MO2 | ✅ Patch gagnant | Vérification du fichier servi au jeu |
| Scène consentie Radiant n°1 | ✅ OK | Parcours normal |
| Scène consentie Radiant n°2 | ✅ OK | Parcours normal |
| Scène non consentie par un autre mod | ⚠️ Eleanor bloquée après la scène | **Non attribuée à Radiant** |
| Cas cible : acteur déjà occupé / refus SexLab | ⏳ À reproduire et vérifier | **Critère de validation principal encore ouvert** |

### Incidents parallèles à ne pas confondre

1. **Blocage des contrôles après une autre scène SexLab** : `enableplayercontrols` n'a pas suffi ; la récupération est passée par le Debug Menu. Des erreurs `None` sont présentes dans les routines de SexLab Approach. Investigation distincte.
2. **CTD du 11/11/2026 à 01:48:21** : exception `EXCEPTION_ACCESS_VIOLATION` dans `nvwgf2umx.dll` (pile d'appels NVIDIA). Mise à jour du pilote NVIDIA puis retour réussi dans la même cellule ; crash **non reproduit**, sans cause définitive établie.
3. **Public Whore / SexLab / autres erreurs Papyrus** : événements observés pendant la même session mais non reliés de manière démontrée à notre patch.

## 7. Travaux restants avant validation finale

- [ ] Reproduire **le cas initial d'échec de lancement** de scène Radiant avec un acteur déjà occupé ;
- [ ] Contrôler les traces `ValidateActor`, `AddActor`, `NewThread` et le comportement de récupération ;
- [ ] Vérifier que Radiant ne reste pas bloqué sur une quête ou un état d'interaction après un refus SexLab ;
- [ ] Comparer précisément source originale / source corrigée pour documenter les lignes V0.1 modifiées ;
- [ ] Tester sur une sauvegarde dédiée et conserver la sauvegarde de référence intacte ;
- [ ] À la fin des tests, désactiver la journalisation `Papyrus.0.log` et les notifications/debug activés dans le MCM SexLab ;
- [ ] Restaurer le **séparateur décimal Windows français `,`** si ce n'est pas déjà fait ;
- [ ] Préparer, si souhaité, un ZIP du **patch runtime uniquement**, séparé des fichiers de compilation.

## 8. Règles pour toute version ultérieure

1. Conserver le script original et les sauvegardes de référence.
2. Travailler dans un mod MO2 **séparé**.
3. Ne compiler que le script ciblé avec des dépendances contrôlées.
4. Ne jamais confondre une interface factice **compile-only** avec un script runtime.
5. Noter la version de NEFARAM, du script source et des dépendances si elles évoluent.
6. Ne qualifier un bug de **corrigé** qu'après reproduction du symptôme initial puis test réussi de la correction.

---

*Document de traçabilité technique Rhiven / Iris Modding Studio. La V0.1 est un correctif personnel en cours de validation, et non un correctif officiel ou une garantie de compatibilité générale.*
