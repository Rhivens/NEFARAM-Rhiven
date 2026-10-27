# Beeing Female NG pour NEFARAM

> **Statut : intégration technique validée sur une configuration basée sur NEFARAM 17.3.x.**
>
> La validation en jeu du cycle complet, de la grossesse et de l'accouchement dépend toujours des réglages de l'utilisateur et n'est pas revendiquée par ce guide.

Ce guide décrit une méthode prudente pour utiliser **Beeing Female NG 3.6.0** comme système principal de fertilité de NEFARAM, avec **Fertility Adventures Redux**. Il conserve l'architecture NEFARAM d'origine comme base de référence et évite d'ajouter un système d'acteurs enfants.

---

## 1. Ce que cette pile remplace

NEFARAM d'origine inclut **Fertility Mode** comme système de fertilité facultatif sous :

```text
[OPTIONAL MODS]
```

Lorsque vous utilisez la pile de ce guide, gardez **Fertility Mode désactivé**. L'exécuter avec Beeing Female NG dupliquerait le rôle de système de fertilité et sort du cadre validé.

La pile de remplacement est :

```text
Fertility Adventures Redux
Beeing Female NG 3.6.0
Beeing Female NG HUD Re-Alignment addon    # facultatif
Labor Animations - OAR
```

---

## 2. Base de référence NEFARAM

L'installation NEFARAM d'origine contient déjà les principaux composants de l'écosystème utilisés par cette intégration :

- SexLab Framework
- SkyUI
- PapyrusUtil
- Address Library
- powerofthree's Papyrus Extender
- Spell Perk Item Distributor (SPID)
- SlaveTats / SlaveTatsNG
- Bathing in Skyrim Renewed
- SexLab Fill Her Up Baka Edition (FHU)
- Milk Mod Economy (MME)
- Simple Children
- Pandora Behaviour Engine
- P.A.I.A
- P.A.I.A Expansion (Pregnancy and Inflation animations)

Ce guide suppose que l'installation NEFARAM normale est déjà opérationnelle. Il ne remplace pas les instructions générales d'installation et de validation de NEFARAM.

---

## 3. Avant l'installation

Avant de modifier la pile de fertilité :

1. clonez si possible votre profil MO2 actuel ;
2. sauvegardez l'ordre du panneau gauche de MO2 ;
3. sauvegardez l'ordre de chargement des plugins ;
4. choisissez une sauvegarde de test sûre et jetable ;
5. confirmez que l'entrée **Fertility Mode** d'origine reste désactivée.

Effectuez la configuration initiale et les contrôles en jeu sur la sauvegarde de test avant de poursuivre une longue partie.

---

## 4. Placement dans MO2

Installez la nouvelle pile sous le séparateur NEFARAM d'origine :

```text
[41 - Added Mods]
├─ Fertility Adventures Redux
├─ Beeing Female NG 3.6.0
├─ Beeing Female NG HUD Re-Alignment addon    # facultatif
└─ Labor Animations - OAR
```

Il s'agit d'un agencement relatif, non d'une prescription de positions absolues exactes. Les installations NEFARAM peuvent différer après personnalisation.

NEFARAM d'origine contient déjà une ancienne entrée **Labor Animations (Open Animation Replacer)** dans `[24 - Animations]`. Dans l'intégration validée, cette ancienne entrée a été désactivée et remplacée par la nouvelle entrée **Labor Animations - OAR**, installée avec la pile Beeing Female dans `[41 - Added Mods]`. Il s'agit d'un remplacement : n'activez et n'exécutez pas les deux entrées Labor Animations ensemble.

Règles importantes :

- gardez **Fertility Mode** désactivé dans `[39 - OPTIONAL MODS]` ;
- gardez Fertility Adventures Redux et Beeing Female NG ensemble dans `[41 - Added Mods]` ;
- gardez l'ancienne entrée **Labor Animations (Open Animation Replacer)** désactivée et la nouvelle **Labor Animations - OAR** activée ;
- placez l'addon HUD facultatif après Beeing Female NG afin que ses presets HUD supplémentaires soient disponibles ;
- laissez les patchs P.A.I.A de Beeing Female NG gagner leurs conflits de configuration OAR pertinents.

Ne déplacez ni ne réinstallez les mods de base P.A.I.A existants uniquement pour cette intégration. Ils appartiennent déjà à la pile d'animations NEFARAM d'origine.

---

## 5. Choix du FOMOD de Beeing Female NG

### Sélections validées

Sélectionnez :

- **Open Animation Replacer**
- **Fertility Adventures Redux patch**
- **SPID item distribution**
- **P.A.I.A base patch**
- **P.A.I.A Expansion patch**
- **SlaveTats womb / birth-count tattoo packs**

Ces choix correspondent aux composants déjà présents dans l'écosystème NEFARAM d'origine.

### Options ignorées pendant la validation

Ne sélectionnez pas les options suivantes pour reproduire la configuration validée à faible complexité :

- **FMR-Immersive Effects**
- **RS Children child actors**
- **Creature child actors**

Ces options ne faisaient pas partie de la validation technique et ne doivent pas être considérées comme des ajouts requis.

---

## 6. Conseils relatifs au système d'enfants

NEFARAM d'origine utilise **Simple Children**, et non RS Children. Aucune migration vers RS Children ou un autre système d'acteurs enfants n'est nécessaire pour cette configuration.

Pour le chemin validé le moins complexe, définissez le résultat de l'accouchement sur :

```text
Gem
```

Cela préserve la boucle de grossesse et d'accouchement sans introduire d'acteurs enfants persistants. N'installez pas l'addon d'enfants créatures sauf si vous souhaitez délibérément construire et tester cette couche supplémentaire actuellement non validée.

---

## 7. Première configuration MCM recommandée

Utilisez les valeurs suivantes comme point de départ prudent, puis ne les ajustez qu'une fois l'intégration de base stable :

| Réglage | Valeur initiale recommandée | Notes |
|---|---|---|
| Player pregnancy | Enabled | Fait partie de la politique validée |
| NPC pregnancy | Disabled | Réduit la complexité initiale ; ce n'est pas une exigence universelle |
| Visual scaling type | BodyMorph | Configuration validée |
| BodyMorph profile | CBBE 3BA | Configuration validée |
| Birth output | Gem | Évite l'ajout d'un système d'acteurs enfants |
| Creature conception | Choix de l'utilisateur | Reste dépendant des tests et n'a pas été finalisé |

Les probabilités de grossesse et la durée du cycle n'ont pas été finalisées pendant la validation technique. Choisissez-les pour votre propre partie uniquement après avoir confirmé la stabilité du système de base.

### Coexistence des BodyMorph

Beeing Female NG, SexLab Fill Her Up Baka Edition et Milk Mod Economy peuvent tous appliquer des modifications BodyMorph. Commencez avec des amplitudes de morph prudentes dans leurs MCM et testez le résultat combiné.

**Inflation Framework NG n'est pas requis.** Il n'a été envisagé que comme solution de réserve si un problème reproductible de coexistence des morphs ne pouvait pas être résolu par le réglage des MCM natifs.

---

## 8. Régénération de Pandora

Relancez et régénérez **Pandora Behaviour Engine** après l'installation de Beeing Female NG et après le remplacement de l'ancienne entrée Labor Animations par **Labor Animations - OAR**, car ces deux changements affectent les animations. Si les deux modifications sont effectuées lors de la même passe d'installation, réalisez une seule régénération complète de Pandora une fois les deux en place. Avant la régénération, Beeing Female NG peut signaler ses animations comme incompatibles.

Pendant la génération, confirmez que Pandora détecte :

```text
FNIS_BeeingFemale_List
```

Après la génération et le redémarrage du jeu, ouvrez la page System de Beeing Female NG et vérifiez :

```text
BeeingFemale Animations = COMPATIBLE
```

Ne considérez pas l'installation comme prête pour les animations tant que ce statut n'est pas affiché.

---

## 9. Réalignement facultatif du HUD

Beeing Female NG 3.6.0 inclut ces fichiers de configuration HUD :

```text
BeeingFemale/HUD/default.ini
BeeingFemale/HUD/LeftOver.ini
```

L'addon facultatif HUD Re-Alignment ajoute les presets **Align1** à **Align6**. Leur structure a été comparée aux INI HUD de Beeing Female NG 3.6.0.

L'addon est facultatif et aucun preset précis n'est imposé par ce guide. Choisissez celui qui convient le mieux à votre propre agencement HUD après un test en jeu.

---

## 10. Notes de compatibilité et de conflits

### P.A.I.A

**P.A.I.A** et **P.A.I.A Expansion (Pregnancy and Inflation animations)** font déjà partie de la pile d'animations NEFARAM d'origine. Sélectionnez leurs patchs Beeing Female NG dans le FOMOD et laissez ces patchs gagner les conflits de configuration OAR pertinents.

### SlaveTats

NEFARAM inclut déjà **SlaveTats / SlaveTatsNG**. Les packs de tatouages du ventre et de compteur de naissances de Beeing Female NG ont été sélectionnés dans la configuration validée.

### Bathing in Skyrim

Beeing Female NG a correctement détecté l'intégration **Bathing in Skyrim** existante pendant la validation technique.

### FHU et MME

**SexLab Fill Her Up Baka Edition** et **Milk Mod Economy** peuvent coexister dans le même environnement, mais les amplitudes BodyMorph finales n'ont pas été établies. Réglez prudemment les trois systèmes avant d'envisager un autre système de morphs.

---

## 11. Liste de contrôle de validation en jeu

Sur une sauvegarde de test jetable, confirmez tous les points suivants :

- [ ] Beeing Female NG apparaît dans le MCM.
- [ ] Beeing Female NG s'initialise correctement.
- [ ] La compatibilité SexLab est détectée.
- [ ] La compatibilité Bathing in Skyrim est détectée.
- [ ] La distribution des objets de Beeing Female fonctionne.
- [ ] L'ancienne entrée `Labor Animations (Open Animation Replacer)` est désactivée et `Labor Animations - OAR` est activée.
- [ ] Pandora a détecté `FNIS_BeeingFemale_List` pendant la régénération.
- [ ] La page System de Beeing Female NG indique que ses animations sont **COMPATIBLE**.
- [ ] Aucune erreur console bloquante de Beeing Female NG n'est observée.
- [ ] L'agencement HUD choisi reste lisible et n'obstrue pas le reste de l'interface.
- [ ] Les modifications de morph restent raisonnables lorsque Beeing Female NG, FHU et MME sont sollicités.
- [ ] Un test complet de cycle, grossesse et accouchement réussit avant d'utiliser cette configuration pour une longue partie.

Les neuf premiers points ont été confirmés pendant la validation technique. Les préférences HUD, le réglage final des morphs et l'intégralité du gameplay de grossesse/accouchement dépendent toujours de l'utilisateur et de sa configuration.

---

## 12. Dépannage

### Beeing Female ou les animations d'accouchement manquent ou sont incompatibles

Confirmez que l'ancienne entrée **Labor Animations (Open Animation Replacer)** dans `[24 - Animations]` est désactivée et que la nouvelle **Labor Animations - OAR** dans `[41 - Added Mods]` est activée. Relancez ensuite Pandora, confirmez qu'il détecte `FNIS_BeeingFemale_List`, redémarrez le jeu et vérifiez de nouveau la page System de Beeing Female NG.

### Le MCM de Beeing Female NG manque

Laissez au jeu le temps de terminer l'enregistrement des MCM, puis actualisez si nécessaire leur enregistrement par les moyens habituels déjà disponibles dans votre configuration. Ne poursuivez pas la configuration tant que le menu n'apparaît pas.

### Les morphs du ventre ou du corps paraissent excessifs ou incohérents

Réduisez d'abord les amplitudes BodyMorph dans Beeing Female NG, FHU et MME. Refaites un test avant d'ajouter un autre système de morphs.

### Des problèmes d'acteurs enfants apparaissent

Revenez au résultat d'accouchement **Gem** et évitez les options RS Children ou enfants créatures, sauf si vous configurez et testez volontairement une pile distincte d'acteurs enfants.

### Deux systèmes de fertilité semblent actifs

Vérifiez `[39 - OPTIONAL MODS]` et confirmez que l'entrée **Fertility Mode** d'origine est toujours désactivée.

### Les animations P.A.I.A ne se comportent pas comme prévu

Confirmez que les deux options de patch P.A.I.A ont été sélectionnées dans le FOMOD de Beeing Female NG et que les fichiers de patch Beeing Female NG gagnent leurs conflits de configuration OAR pertinents. Régénérez ensuite Pandora.

---

## 13. Périmètre de validation et avertissement

Les éléments suivants ont été validés techniquement :

- initialisation de Beeing Female NG ;
- enregistrement du MCM ;
- détection de la compatibilité SexLab ;
- détection de la compatibilité Bathing in Skyrim ;
- distribution des objets Beeing Female ;
- intégration de Pandora ;
- absence d'erreur console bloquante de Beeing Female NG.

Les éléments suivants n'ont pas été finalisés ou entièrement validés en jeu :

- probabilités de grossesse ;
- durée du cycle ;
- politique de fertilité des créatures ;
- amplitudes BodyMorph finales ;
- réglage de la coexistence FHU/MME ;
- preset HUD définitif ;
- test complet d'une grossesse et d'un accouchement en jeu.

Considérez ce guide comme une base d'intégration technique validée, et non comme un preset de gameplay universel. Finalisez les choix et tests restants sur une sauvegarde jetable avant de les appliquer à une longue partie.

---

## 14. Référence de travail

Pour les notes techniques à l'origine de ce guide communautaire, consultez le [dossier interne d'intégration du système de fertilité](../../../06%20-%20GAMEPLAY/BEEING%20FEMALE%20NG/12-FERTILITY-SYSTEM.md).
