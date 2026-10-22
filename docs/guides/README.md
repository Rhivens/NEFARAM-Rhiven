# Guides NEFARAM

Ce dossier regroupe les **guides pratiques et procédures techniques** liés à la personnalisation et à la maintenance de **NEFARAM-Rhiven**.

Contrairement aux fiches numérotées du dossier `docs/`, qui documentent directement l'état du build personnel NEFARAM-Rhiven, les fichiers présents ici sont des **guides autonomes** pouvant servir de procédure de référence.

## Guides disponibles

### ENB → Community Shaders avec NAT Effect 11

Document Word réorganisé et nettoyé à partir d'un guide NEFARAM et d'échanges Discord utiles.

Le document couvre notamment :

- la suppression des composants ENB incompatibles ;
- l'installation de Community Shaders et Effects 11 ;
- l'utilisation de NAT.ENB III avec NAT Effect 11 ;
- les composants complémentaires comme ISL Helper SKSE et Lux CS ;
- le placement conseillé dans MO2, panneau gauche et panneau droit ;
- les conflits de touches avec OBody ;
- les réglages de base de Community Shaders / Effects 11 ;
- les précautions liées à KiLoader, EVLaS, Sky Reflection Fix et PrivateProfileRedirector ;
- une section séparée sur l'alternative Bottled Shaders ;
- une checklist finale de validation.

Le document d'origine contenait plusieurs captures et échanges Discord. Les discussions ont été supprimées dans la version finale ; seuls les détails techniques utiles ont été conservés. Des placeholders indiquent les emplacements où les captures peuvent être réinsérées manuellement.

**Fichier :**

[NEFARAM_Guide_ENB_vers_Community_Shaders_NAT_Effect_11.docx](NEFARAM_Guide_ENB_vers_Community_Shaders_NAT_Effect_11.docx)

> **Attention :** la procédure source avait été rédigée pour une version antérieure de NEFARAM. Avant toute application sur le build actuel, les versions, prérequis et éventuels changements du load order doivent être revalidés.

## Convention

Les futurs guides techniques peuvent être ajoutés dans ce dossier lorsqu'ils décrivent une procédure réutilisable, par exemple :

- migration d'un système graphique ;
- remplacement d'un framework ;
- procédure de génération ou de régénération ;
- configuration complexe d'un outil ;
- procédure de diagnostic ou de dépannage.

Les modifications spécifiques au build courant doivent continuer à être documentées dans les fiches principales du dossier `docs/` et dans le `CHANGELOG.md`.

## Chantier PAMA — Prison Alternative

Un chantier dédié documente l'intégration progressive de l'écosystème **PAMA / Prison Alternative** dans NEFARAM-Rhiven : architecture, dépendances, compatibilités, risques de navmesh, ordre MO2 provisoire et protocole de test.

**Dossier :** [PAMA/README.md](PAMA/README.md)

> Statut actuel : audit terminé, intégration et tests à venir.

## Animations — OAR / Eleanor

- [**Guide OAR / Gulan0 / Seamless — réglages Rhiven**](ANIMATIONS/README.md) : priorités, fichier `user.json`, configuration finale Player Only, correctif sprint et diagnostic des remplacements Legacy DAR.

## Chantier Naked Defeat

Un dossier dédié regroupe la documentation **Naked Defeat AE/SE 6.50 FULL** et le protocole prévu pour étudier son intégration à NEFARAM-Rhiven en remplacement éventuel de **Practical Defeat**, tout en conservant **Acheron** comme gestionnaire central et **Yamete Kudasai** pour les cas où il reste pertinent.

**Dossier :** [NAKED-DEFEAT/README.md](NAKED-DEFEAT/README.md)

> Statut actuel : documentation consolidée, architecture cible définie, intégration réelle reportée après stabilisation de NEFARAM 17.3.8.


## Animal Mansion Reborn 1.8

Documentation de référence pour une éventuelle intégration future de **Animal Mansion Reborn 1.8** dans NEFARAM-Rhiven.

- [Guide FR illustré (Word)](Animal_Mansion_Reborn_1.8_Guide_FR_Rhiven.docx)
- [Technical Reference EN (Markdown)](Animal_Mansion_Reborn_1.8_Technical_Reference_EN.md)

> Le document Word est destiné à la lecture humaine ; le fichier Markdown sert de référence technique rapide pour les futurs audits de compatibilité, l’intégration MO2/xEdit et le diagnostic.


## RennasRanch 0.3.0

A dedicated integration protocol is available for **RennasRanch 0.3.0**, built around the **Secluded Valley** worldspace.

Source: https://www.loverslab.com/files/file/45943-rennasranch/

**File:** [PONYPLAY-SECLUDED-VALLEY-INTEGRATION.md](PONYPLAY-SECLUDED-VALLEY-INTEGRATION.md)

The protocol covers dependency verification, MO2 isolation, Pandora, BodySlide, xEdit, Falkreath/worldspace compatibility, LOD generation, scripted-scene interference, tether/cart/contraption regression tests, Papyrus monitoring, save/reload validation and rollback.

> Planned order: stabilize NEFARAM 17.3.8 → validate Animal Mansion Reborn → validate this ponyplay mod → then tackle Naked Defeat.


## SexLab Approach Redux 3.61

A dedicated integration protocol is available for **SexLab Approach Redux 3.61**.

**File:** [SEXLAB-APPROACH-REDUX-INTEGRATION.md](SEXLAB-APPROACH-REDUX-INTEGRATION.md)

The protocol focuses on autonomous NPC approaches, MCM tuning, coexistence with SLHH Expansion and BaboDialogue, overlap with SexLab Survival / TDF Aroused Rape / Dangerous Nights, defeat-state protection, Papyrus monitoring and save/reload validation.

> Historical note: Fabien recalls probably having used SexLab Approach Redux in an older NEFARAM v16 setup; this remains to be verified against an archived v16 load order.


## Public Whore Comments 1.7

A dedicated integration study is available for **Public Whore Comments 1.7**.

**File:** [PUBLIC-WHORE-COMMENTS-INTEGRATION.md](PUBLIC-WHORE-COMMENTS-INTEGRATION.md)

The study covers Public Whore dependency checks, arousal-framework verification, SLSF Fame Comments coexistence, comment-frequency tuning, spouse behavior, SexLab-scene comments, first-person thoughts, save/reload validation and rollback.

> Current verdict: promising candidate. Structural risk appears low to medium, but comment-density / immersion spam must be tested carefully.


## SLSF Fame Comments Reloaded 1.3 SE

A dedicated reference and integration-tuning sheet is available for **SLSF Fame Comments Reloaded 1.3 SE**.

**File:** [SLSF-FAME-COMMENTS-RELOADED-INTEGRATION.md](SLSF-FAME-COMMENTS-RELOADED-INTEGRATION.md)

The document records the fact that Fame Comments Reloaded is already present in the active NEFARAM-Rhiven baseline, documents its SLSF Reloaded fame/event architecture, follower and spouse systems, Jarl warning/bounty behavior, voice-pack checks, MCM tuning, Public Whore Comments coexistence and future SexLab Approach regression testing.

> Current verdict: retained baseline component; final MCM tuning and regression validation required.
