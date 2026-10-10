# Tatouages — architecture et API de développement

**Projet :** NEFARAM-Rhiven 17.3.7 · **Statut :** fiche technique évolutive, intégration et tests fonctionnels en cours.

Objectif : conserver les interfaces utiles pour de futurs mods Papyrus exploitant les tatouages, sans confondre mécanismes documentés, hypothèses et tests réalisés.

## 1. Composants et responsabilités

| Composant | Fonction |
| --- | --- |
| SlaveTats SE + SlaveTats NG | Gestion des tatouages et overlays ; socle déjà présent dans NEFARAM |
| Rape Tattoos Continued (RTC) 2.0.3 | Déclenchement / choix / application de tatouages, notamment après des événements SexLab |
| Fade Tattoos Continued 2.1.0 | Suivi de tatouages temporaires et disparition progressive ; gestion manuelle via MCM |
| Packs SlaveTats (Alpia Scribbles, Zaki…) | Textures et catalogue de tatouages ; ne constituent pas le moteur de déclenchement |
| No Overlap for Rape Tattoo | Candidat : examiner les configurations fournies avant de décider d'une installation ou d'une adaptation |
| Remove Your Tats SE | Candidat optionnel : mécanisme de retrait de tatouages ; non indispensable au fonctionnement du duo RTC/Fade |

RTC et Fade Continued remplacent leurs anciennes versions respectives : ne pas installer leurs originaux en parallèle.

**Dépendances annoncées pour RTC :** SlaveTats et ses prérequis, Fade Tattoos (Continued ou original), SexLab, powerofthree's Papyrus Extender (testé par l'auteur à partir de 5.5.0). ZaZ est facultatif pour la catégorisation des personnages dans `zbfFactionSlave`. Version de Papyrus Extender déclarée dans le NEFARAM actuel : **6.5.2** ; compatibilité effective à valider en jeu.

## 2. Flux fonctionnel documenté

1. Un événement SexLab éligible peut déclencher RTC, suivant les paramètres MCM et un tirage aléatoire.
2. RTC sélectionne les tatouages autorisés, en respectant notamment groupes, probabilités, catégories d'acteurs, couleurs, permanence et limites d'overlays.
3. RTC applique les tatouages via l'écosystème SlaveTats et synchronise les overlays.
4. Pour les marques temporaires, Fade Tattoos prend en charge leur suivi et leur disparition selon la durée configurée.

RTC permet des réglages distincts **joueur / PNJ / esclave ZaZ**. **Attention :** si le joueur appartient à `zbfFactionSlave`, les paramètres « esclave ZaZ » s'appliquent aussi à lui.

Les tatouages RTC groupés sont limités à **un tatouage par groupe configuré**. Groupes spéciaux :
- `(unassigned)` : pas de limite de groupe, mais les limites d'overlays s'appliquent ;
- `(excluded)` : RTC ne sélectionne jamais cette entrée.

Ce regroupement est **logique**, pas une détection géométrique automatique des superpositions de textures.

## 3. API RTC à réutiliser dans de futurs mods

Les interfaces ci-dessous sont celles **explicitement documentées par l'auteur de RTC 2.0.3**. À tester sur l'instance actuelle avant toute publication d'un nouveau mod.

### Appels directs Papyrus

La quête RTC se trouve dans `RapeTattoos.esp`, FormID local `0x000D62`. L'appel suppose que le script ait obtenu la référence à la quête et son script `rapeTattoosQuest`.

```papyrus
rapeTattoosQuest.doTattooAction()
; Un tatouage aléatoire sur le joueur, avec les règles MCM.

rapeTattoosQuest.doTattooActionFor(target, count)
; target : Actor ; count : Int optionnel (1 par défaut).
```

**Important :** ce bloc illustre la signature documentée, **pas** un exemple autonome compilable : il reste à résoudre la référence au script et à vérifier les types réels dans les sources RTC.

L'argument `count` permet de demander plusieurs tatouages avec une synchronisation groupée, plutôt que de répéter des appels unitaires.

### ModEvents (préférables pour une intégration souple)

Compatibilité ancienne API, un tatouage joueur :

```papyrus
SendModEvent("RapeTattoos_addTattoo")
```

Nouvelle API RTC V2, acteur et nombre explicites :

```papyrus
int handle = ModEvent.Create("RapeTattoos_addTattooV2")
if handle
    ModEvent.PushForm(handle, target) ; target est une référence Actor
    ModEvent.PushInt(handle, count)   ; count est un int
    ModEvent.Send(handle)
endif
```

L'événement demande l'opération à RTC ; la sélection reste soumise à sa logique et à sa configuration. Prévoir une stratégie lorsque RTC n'est pas installé (l'envoi d'un ModEvent n'est pas une garantie de traitement).

RTC annonce préserver `doTattooAction`, `doTattooActionFor` et `RapeTattoos_addTattoo` pour les mods hérités. Ne pas présumer de la compatibilité d'autres API internes non documentées.

## 4. JSON, configuration et sauvegarde

RTC stocke sa configuration utilisateur à l'emplacement annoncé par l'auteur :

```text
Documents/My Games/Skyrim Special Edition/JCUser/rTats/
  settings.json
  colorConfig.json
```

- `settings.json` : associations de tatouages aux groupes et autres réglages RTC.
- `colorConfig.json` : configuration personnalisée des couleurs / lumières suivant le mode sélectionné.
- La configuration des groupes peut passer par le bouton MCM **Load Tattoo Config Pages**, qui évite de charger systématiquement un catalogue potentiellement très volumineux.
- Des exemples de configuration de couleurs sont fournis par RTC dans `rapeTattoos/colorConfigs/` (avec README).
- Sauvegarder le dossier `JCUser/rTats` **séparément du profil MO2** lorsque l'on fige les réglages ; vérifier les droits d'écriture en cas de non-persistance.

**Packs Alpia : à auditer.** Identifier les JSON réellement livrés et leur destination, comparer leurs clés au format attendu par RTC 2.0.3, rechercher doublons, exclusions, chemins morts et risque d'écrasement de la configuration utilisateur. Ne pas inventer ni fusionner des JSON avant examen.

## 5. Compatibilités et précautions

- **Incompatibilités explicitement signalées par RTC :** SlaveTats Performance Patch (Sejra) ; Monoman's Rape Tattoos Tweaked.
- **SlaveTats NG / PAH Diary Of Mine :** conflit historique `Scripts/SlaveTatsMCMMenu.pex`. Deux versions inspectées ; différences constatées, mais aucune anomalie reproductible établie. **Ne pas changer la priorité gagnante de PAH sans test ciblé.**
- **Overlays RaceMenu :** limites par zone dans `SKSE/Plugins/skee.ini` (`[Overlays/Body]`, `Hands`, `Feet`, `Face`). Mesurer les besoins avant toute augmentation ; davantage d'emplacements peut accroître le coût des synchronisations SlaveTats.
- **JContainers :** vérifier que les fichiers de version correcte gagnent dans MO2 ; un mod tiers peut embarquer une copie obsolète.
- **Raccourcis :** RTC documente `Y` (événement de test) et `N` (ajout de marques) en mode debug. `N` est également utilisé par Fitting Room dans la configuration en cours : laisser le debug RTC désactivé pendant la partie.
- **MCM debug :** le mode debug de RTC peut produire beaucoup de notifications / traces ; ne pas le conserver actif en jeu normal.
- **Priorité MO2 :** bloc des ajouts à la fin de `[35 - SexLab Content]`, sous `Advanced Nudity Detection`. Vérifier les conflits fichier par fichier ; la position à elle seule ne démontre pas la compatibilité fonctionnelle.
- **Saves :** les mises à niveau depuis l'ancien RTC sont déconseillées en cours de partie sans procédure adaptée ; la partie définitive NEFARAM-Rhiven démarrera depuis sa baseline prévue.

## 6. Checklist de validation technique

- [ ] Contrôler les masters, fichiers gagnants MO2 et erreurs xEdit de RTC/Fade.
- [ ] Inspecter les packs Alpia et Zaki et les JSON livrés ; compléter cette fiche avec les formats **réellement observés**.
- [ ] Vérifier le `skee.ini` gagnant et ses limites effectives.
- [ ] Tester une application RTC sur sauvegarde jetable, puis la synchronisation et le rechargement.
- [ ] Tester l'expiration Fade, la gestion des tatouages verrouillés et les paramètres joueur/PNJ/ZaZ.
- [ ] Tester les ModEvents et `doTattooActionFor(target, count)` sur une petite quantité.
- [ ] Contrôler la persistance des réglages JSON après fermeture et réouverture du jeu.
- [ ] En cas de souci, inspecter les logs Papyrus et les éventuels conflits SlaveTats/JContainers, **sans modifier à l'aveugle** les scripts NEFARAM.

## 7. Sources de référence

- [Rape Tattoos Continued 2.0.3](https://www.loverslab.com/files/file/27999-rape-tattoos-continued/) — fiche auteur, sections « For Modders », « Configuring tattoo groups », « Compatibility » et « Troubleshooting ».
- [Fade Tattoos Continued 2.1.0](https://www.loverslab.com/files/file/27994-fade-tattoos-continued/) — fiche auteur.
- [No Overlap for Rape Tattoo](https://www.loverslab.com/files/file/45084-no-overlap-for-rape-tattoo/) — à analyser.
- [Alpia Scribbles SlaveTats Pack](https://www.loverslab.com/files/file/30951-alpia-scribbles-slavetats-pack/) — à analyser.
- [Zaki Tattoo Pack](https://www.loverslab.com/files/file/26261-zaki-tattoo-pack-lese/) — à analyser.
- [Remove Your Tats SE](https://www.loverslab.com/files/file/31435-remove-your-tats-se/) — optionnel.

**Principe de maintenance :** documenter les interfaces publiques et les configurations réellement éprouvées ; garder les adaptations Rhiven isolées et réversibles.
