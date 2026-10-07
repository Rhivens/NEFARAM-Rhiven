# NEFARAM — Passer de l’ENB à Community Shaders avec NAT Effect 11

> **Guide nettoyé et réorganisé à partir des notes Discord / guide NEFARAM**
>
> **Portée du document :** la procédure source a été rédigée pour **NEFARAM 17.2.1**. Elle doit être revalidée avant application sur une version plus récente de NEFARAM. Les échanges Discord ont été supprimés ; seuls les détails techniques utiles ont été conservés.
>
> Version Word d'origine : [NEFARAM_Guide_ENB_vers_Community_Shaders_NAT_Effect_11.docx](./NEFARAM_Guide_ENB_vers_Community_Shaders_NAT_Effect_11.docx)

## 1. Objectif et principe

Cette procédure remplace l’ENB utilisé par NEFARAM par **Community Shaders (CS)** tout en conservant la possibilité d’utiliser un preset ENB via la fonctionnalité **Effects 11**.

La configuration de référence utilise **NAT Effect 11**, qui adapte à la fois le preset **NAT.ENB III** et le plugin météo NAT déjà présent dans NEFARAM.

L’intérêt principal est de conserver le post-traitement et les particle lights d’un preset ENB, tout en bénéficiant des fonctions propres à Community Shaders, notamment :

- Light Limit Fix
- Hair Specular
- les fonctions d’upscaling / frame generation prises en charge par CS

## 2. Corrections et points importants à appliquer dès le départ

- **Ne pas installer / réactiver KiLoader** : il est incompatible avec Effects 11.
- **Désactiver Sky Reflection Fix dans MO2** : cette fonction est intégrée à Community Shaders.
- **Désactiver PrivateProfileRedirector SE - Faster game start (INI file cacher)** : conflit signalé avec le plugin météo NAT.ENB III.
- La règle ancienne indiquant que Community Shaders devait être placé au-dessus de tous ses add-ons n’est plus considérée comme obligatoire dans le guide source.
- **Terrain Helper est déjà présent dans NEFARAM** ; ne pas le réinstaller.
- Le module **HDR** de Community Shaders n’est utile que sur un écran compatible HDR.

## 3. Étape 1 — Retirer les composants ENB incompatibles

### 3.1 Fichiers à retirer de `Nefaram\Game Root`

- `d3d11.dll`
- `d3dcompiler_46e.dll`

### 3.2 Mods à désactiver ou désinstaller dans MO2

- **KiLoader for Skyrim** — incompatible avec Effects 11.
- **ENB Anti-Aliasing - AMD FSR 3.1 - NVIDIA DLAA** — incompatible avec l’implémentation DLAA / DLSS / FSR / XeSS de Community Shaders.
- **ENB Frame Generation** — incompatible avec l’implémentation DLAA / DLSS / FSR / XeSS de Community Shaders.
- **ENB Input Disabler** — peut probablement rester actif, mais devient inutile sans les DLL ENB ; le désactiver simplifie le setup.
- **Enhanced Volumetric Lighting and Shadows (EVLaS)** — incompatible avec la fonctionnalité Sky Sync de Community Shaders.
- **Sky Reflection Fix** — fonction déjà intégrée à Community Shaders.
- **PrivateProfileRedirector SE - Faster game start (INI file cacher)** — conflit avec le plugin météo NAT.ENB III.

## 4. Étape 2 — Installer Community Shaders et ses composants

### 4.1 Community Shaders

Installer Community Shaders dans MO2 :

https://www.nexusmods.com/skyrimspecialedition/mods/86492

Consulter la liste **Additional Features** de la page Nexus pour les add-ons disponibles au moment de l’installation.

**Effects 11 est le seul add-on obligatoire pour cette procédure.**  
**Skylighting** est recommandé dans le guide source.

### 4.2 Effects 11 — Community Shaders

https://www.nexusmods.com/skyrimspecialedition/mods/179824

Installer **Effects 11**. C’est le composant qui permet d’utiliser de nombreux presets ENB sans charger les DLL ENB.

### 4.3 NAT.ENB III — preset uniquement

https://www.nexusmods.com/skyrimspecialedition/mods/27141

Télécharger manuellement uniquement :

**NAT.ENB - ENB PRESET v3.1.1C**

Ne pas télécharger le plugin météo :

**NAT.ENB - ESP WEATHER PLUGIN v3.1.1C - Fixed**

car il est déjà fourni par NEFARAM.

Extraire l’archive et copier dans `Nefaram\Game Root` le contenu du dossier :

`0-INSTALL MAIN FILES FIRST`

Accepter l’écrasement des fichiers si Windows le demande.

Ne pas copier les variantes de qualité (**LOW / MEDIUM / etc.**) : leur `enbseries.ini` sera de toute façon remplacé par NAT Effect 11.

### 4.4 NAT Effect 11

https://www.nexusmods.com/skyrimspecialedition/mods/186575

Télécharger manuellement **NAT Effect 11 Preset**, extraire l’archive puis copier :

- le dossier `enbseries`
- le fichier `enbseries.ini`

dans `Nefaram\Game Root`.

Accepter l’écrasement.

Télécharger également **NAT Effect 11 Plugins** et l’installer normalement via MO2.

### 4.5 ISL Helper SKSE

https://www.nexusmods.com/skyrimspecialedition/mods/179132

Pré-requis indiqué pour Lux CS.

### 4.6 Light Placer

https://www.nexusmods.com/skyrimspecialedition/mods/127557

Déjà présent dans NEFARAM selon le guide source.

La recommandation est de le mettre à jour vers la version la plus récente compatible avec le setup.

### 4.7 Lux CS

https://www.nexusmods.com/skyrimspecialedition/mods/153919

Dans le FOMOD, sélectionner :

- **Effect 11**
- **Lux Orbis Tweaks**

## 5. Étape 3 — Placement dans MO2

### 5.1 Panneau gauche

Activer les nouveaux mods installés.

Le guide source recommande de les laisser **en bas du panneau gauche**.

La remarque ancienne imposant que Community Shaders soit placé au-dessus de tous ses add-ons a été annulée par l’auteur du guide.

### 5.2 Panneau droit / plugins

Placer les nouveaux plugins sous `_NEFARAM_LoadScreen.esp` mais avant `Synthesis_3.esp`.

Le point sensible est **`Lux CS - Bulbs.esp`**, qui modifie de nombreuses cellules et worldspaces : il doit rester avant les plugins Synthesis et avant DynDOLOD / Occlusion afin de ne pas écraser les records acoustiques transférés ni les modifications de worldspace générées.

Ordre de référence donné par le guide :

```text
_NEFERAM_SexDialogue.esp
_NEFARAM_LoadScreen.esp
Lux CS - Bulbs.esp
Lux Orbis CS.esp
NAT-CS.ENB.esp
Synthesis_0.esp
Synthesis_1.esp
Synthesis_2.esp
Synthesis_3.esp
Synthesis_4.esp
_NEFARAM_____AFTERSynthesis_____.esp
DynDOLOD.esp
Occlusion.esp
```

## 6. Premier lancement et réglages

1. Lancer Skyrim avec la nouvelle pile Community Shaders.
2. Lors du premier lancement, définir la touche d’ouverture du menu Community Shaders. Le guide recommande de conserver **END** si elle est libre.
3. Dans le menu CS : **General > Keybindings**, modifier **Overlay Toggle Key** si elle est encore sur **F10**.
4. **F10 est déjà utilisé par OBody** pour le menu de presets ; choisir une autre touche, par exemple **PageDown** ou une touche du pavé numérique.
5. Utiliser **F11** en jeu pour afficher les touches déjà réservées par les autres mods.

## 7. Réglages NAT Effect 11

Dans le menu principal de Community Shaders (**END** par défaut), ouvrir l’onglet **Effects 11**.

Les réglages se rapprochent de ceux d’un preset ENB.

Le retour inclus dans le guide indique que l’intérieur est satisfaisant avec les valeurs par défaut, mais que les extérieurs peuvent être trop lumineux.

Réglage recommandé dans le document :

`enbeffect.fx > Technique > NAT: Natural (Cold & Harsh)`

Ce réglage est présenté comme un bon compromis pour les extérieurs tout en conservant des intérieurs corrects.

## 8. Utiliser un autre preset ENB avec Effects 11

Effects 11 peut fonctionner avec d’autres presets ENB.

Le guide cite notamment :

- Silent Horizons 2
- Pi-Cho
- Rudy
- Kauz

Procédure générale :

1. télécharger le preset ;
2. l’extraire manuellement ;
3. copier ses fichiers de preset, souvent `enbseries`, `enblocal.ini` et `enbseries.ini`, dans `Nefaram\Game Root`.

> **Important :** ne pas installer / réactiver KiLoader, même si un preset le liste comme prérequis. Le guide indique qu’il ne fonctionne pas avec Effects 11.

Si un autre preset est utilisé à la place de NAT Effect 11, désactiver **NAT Effect 11** dans MO2 afin d’éviter un empilement incohérent.

## 9. Option alternative issue des échanges Discord : Bottled Shaders

Les échanges Discord mentionnent une alternative appelée **Bottled Shaders**, décrite comme un fork / package AIO de Community Shaders.

Selon les participants, cette version intègre directement plusieurs plugins CS, dont Effects 11, et peut simplifier l’installation.

> Cette alternative n’appartient pas à la procédure principale. Elle est issue de retours Discord et peut nécessiter l’accès à un build récent via le Discord **The Cistern**. La procédure source officielle décrite plus haut vise la version Nexus de Community Shaders.

Informations techniques conservées des échanges :

- Avec Bottled Shaders, supprimer Community Shaders et ses plugins séparés avant d’activer l’AIO.
- Conserver NAT Effect 11 si l’on souhaite continuer à utiliser ce preset.
- Le développeur de ce fork est présenté dans les échanges comme le créateur d’Effects 11.
- Les captures Discord montrent un bloc MO2 regroupant :
  - ISL Helper SKSE
  - ENB Extender and Helper
  - Lux CS Patch
  - Bottled Shaders
  - NAT III ENB
  - NAT Effect 11 Plugins / Preset
  - plusieurs composants terrain

## 10. Notes de compatibilité et dépannage

- Le guide ne couvre pas les builds bêta Community Shaders provenant de Discord (**Jiaye, Bottle ou autres**), sauf la note alternative ci-dessus.
- Lors d’un changement de build Community Shaders, supprimer le **shader cache** situé dans `SKSE Output` pour réduire les risques de problèmes.
- Le guide estime qu’il n’est pas nécessaire de supprimer le shader cache lors d’un simple changement de preset ENB, uniquement lors d’un changement de build CS.
- Certains presets dérivés de Silent Horizons peuvent dépendre de KiLoader ; cela entre en conflit avec Effects 11.
- Les échanges Discord indiquent qu’un **SH2 Shader Core** peut être utilisé dans certains scénarios, mais qu’il serait en grande partie écrasé par NAT Effect 11. Ce point n’est pas présenté comme nécessaire dans la procédure principale.

## 11. Checklist de validation

- [ ] Les DLL ENB incompatibles ont été retirées du Game Root.
- [ ] KiLoader, ENB AA, ENB Frame Generation, EVLaS, Sky Reflection Fix et PrivateProfileRedirector ont été désactivés selon la procédure.
- [ ] Community Shaders et Effects 11 sont installés.
- [ ] Le preset NAT.ENB III a été copié dans Game Root.
- [ ] NAT Effect 11 Preset a écrasé les fichiers attendus dans Game Root.
- [ ] NAT Effect 11 Plugins est installé dans MO2.
- [ ] ISL Helper SKSE et Lux CS sont installés.
- [ ] Lux CS FOMOD : Effect 11 + Lux Orbis Tweaks sélectionnés.
- [ ] Les nouveaux plugins sont placés avant Synthesis / DynDOLOD / Occlusion selon l’ordre de référence.
- [ ] La touche Overlay Toggle de Community Shaders n’entre pas en conflit avec OBody F10.
- [ ] Le jeu démarre sans erreur bloquante.
- [ ] Les intérieurs et extérieurs ont été contrôlés visuellement.
- [ ] Le shader cache a été nettoyé uniquement si un changement de build Community Shaders le justifiait.

## 12. Résumé de la procédure

1. Retirer les composants ENB incompatibles.
2. Installer Community Shaders + Effects 11.
3. Installer le preset NAT.ENB III puis NAT Effect 11.
4. Ajouter ISL Helper et Lux CS.
5. Positionner correctement les plugins avant Synthesis / DynDOLOD / Occlusion.
6. Régler les raccourcis et l’éclairage en jeu.
7. Valider visuellement avant de conserver la configuration.
