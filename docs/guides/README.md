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
