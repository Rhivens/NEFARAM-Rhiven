# Chantier PAMA — Prison Alternative / NEFARAM-Rhiven

> **Statut : préparation / audit avant installation**
>
> Ce document centralise le chantier d'intégration du bloc PAMA dans NEFARAM-Rhiven.  
> Aucun ordre de plugins définitif n'est considéré comme validé tant que les conflits de cellules/navmeshes et les tests en jeu n'ont pas été réalisés.

## Objectif

Remplacer/améliorer le système de prison actuellement peu satisfaisant de NEFARAM par une architecture PAMA cohérente, tout en conservant les systèmes existants lorsque c'est possible.

Le chantier vise à intégrer :

1. **Pama´s Deadly Furniture (scripts) 34.5 - Revision 2**
2. **Prison Alternative - A modular Prison System 2.0.3**
3. **Pama Sovngarde Aftermath 1.0.0**
4. **Prison Alternative - Punishment Pack 1.3.0**
5. **Prison Alternative - Outdoor Event Pack 1.3**
6. **Bad Ends Revived: Windhelm 1.3.0**
7. **Bad Ends Revived: Riften 1.3.2**
8. **Bad Ends Revived: Solitude 1.8.0 (Revision 2)**
9. **Orkish Bounty Hunters 0.4**

## Architecture fonctionnelle envisagée

```text
Pama's Deadly Furniture
        ↓
Prison Alternative
        ↓
Pama Sovngarde Aftermath
        ↓
Punishment Pack / Outdoor Event Pack / Bad Ends
        ↓
Orkish Bounty Hunters
```

- **Deadly Furniture** fournit la couche technique des dispositifs létaux/non létaux.
- **Prison Alternative** est le framework carcéral central et le registre des événements.
- **Sovngarde Aftermath** fournit une continuité de jeu après certaines exécutions PAMA.
- **Punishment / Outdoor / Bad Ends** ajoutent les événements carcéraux et régionaux.
- **Orkish Bounty Hunters** agit comme générateur dynamique d'arrestations et de transferts vers la prison.

## Dépendances déjà présentes dans NEFARAM-Rhiven

À ce stade, le build contient déjà les briques importantes suivantes :

- SKSE
- SkyUI
- SexLab Framework
- ZaZ Animation Pack
- powerofthree's Papyrus Extender
- Pandora
- ConsoleUtil Extended
- Acheron - Death Alternative
- Practical Defeat Reanimated
- Devious Devices
- Troubles of Heroine
- Simple Slavery / Simple Slavery Rebuild

## Dépendance à ajouter / traiter comme quasi-obligatoire

### Next-Gen Decapitations

Fortement recommandé par Pama´s Deadly Furniture et requis par Pama Sovngarde Aftermath.

Le retour Discord NEFARAM confirme également que ce correctif est utilisé pour supprimer des CTD liés aux décapitations.

Configuration demandée par Sovngarde Aftermath :

```ini
[Misc]
iCanBeResurrected = 2
bAdvancedNPCMaintenance = 0
```

Objectif : permettre la restauration correcte de la tête du joueur après une décapitation suivie d'un passage par Sovngarde.

## Ordre MO2 gauche provisoire

Ordre de travail proposé, à confirmer pendant l'installation :

1. Pama´s Deadly Furniture (scripts)
2. Prison Alternative - A modular Prison System
3. Pama Sovngarde Aftermath
4. Prison Alternative - Punishment Pack
5. Prison Alternative - Outdoor Event Pack
6. Bad Ends Revived: Windhelm
7. Bad Ends Revived: Riften
8. Bad Ends Revived: Solitude
9. Orkish Bounty Hunters

Cet ordre reflète les couches fonctionnelles et les dépendances.  
Il **ne doit pas être recopié aveuglément dans le panneau droit**.

## Compatibilités et risques connus

### Devious Devices

PAMA considère DD comme une **soft incompatibility** dans plusieurs modules.

La simple présence de DD peut être tolérée, mais les problèmes deviennent beaucoup plus probables si le joueur porte des restraints DD pendant une arrestation, une incarcération ou une scène PAMA.

**Règle de test : aucun dispositif DD équipé pendant les premiers tests PAMA.**

### Devious Cursed Loot

À considérer comme **non compatible** avec ce chantier.

Ne pas l'ajouter au build PAMA.

### Defeat mods / Acheron

Prison Alternative indique que les defeat mods peuvent coexister, avec une préférence pour les déclenchements basés sur le **bleedout** plutôt que sur un seuil de santé.

Orkish Bounty Hunters emploie son propre système de poison/KO scripté afin d'éviter de concurrencer directement les defeat frameworks.

Sovngarde Aftermath n'est pas un combat defeat mod et est conçu pour être appelé explicitement par les systèmes PAMA.

**Test obligatoire :** vérifier que les morts/défaites de combat ordinaires restent gérées par Acheron et que les exécutions PAMA basculent correctement vers Sovngarde Aftermath.

### Random Sex mods

Plusieurs modules PAMA indiquent que des mods lançant des scènes aléatoires peuvent interrompre ou casser les scènes PAMA.

À contrôler dans les MCM existants pendant les tests.

### Fill Her Up Baka

Outdoor Event Pack signale qu'une déflation survenant au mauvais moment peut provoquer une anomalie visuelle dans les animations.

Pas de dommage persistant annoncé, mais test spécifique à prévoir.

## Risques de cellules / navmeshes

### Windhelm — priorité élevée

Bad Ends Revived: Windhelm modifie notamment :

- `CandleheartHallExterior`
- `WindhelmBridge3`

Le build NEFARAM-Rhiven contient déjà **Capital Windhelm Expansion** avec plusieurs correctifs de navmesh/collision.

**Avant validation :**

- ouvrir le load order complet dans xEdit ;
- vérifier les cellules et navmeshes modifiés ;
- ne pas appliquer automatiquement la recommandation "plugin PAMA tout en bas" ;
- créer un patch dédié si nécessaire.

### Riften — priorité élevée

Bad Ends Revived: Riften prévient explicitement des conflits possibles avec les city overhauls.

Le build contient **Riften of Reverie**.

**Avant validation :**

- inspection xEdit ;
- contrôle des placements ;
- test navmesh/NPC en jeu ;
- décision de load order seulement après vérification.

### Solitude — priorité moyenne

Le module ajoute des éléments physiques sur la plaza et dans les zones utilisées par ses événements.

Prévoir une inspection visuelle et de navigation en jeu.

## Protocole d'installation et de test

### Phase 1 — installation technique

- installer le bloc sur le profil de test ;
- installer/configurer Next-Gen Decapitations ;
- régénérer Pandora ;
- lancer une save de test adaptée.

### Phase 2 — démarrage sécurisé

Réglages initiaux :

- **Prison Alternative Lethality : OFF**
- **Deadly Furniture : mode non létal**
- aucun DD équipé

Dans le MCM Prison Alternative :

- contrôler le registre des Events ;
- vérifier que chaque événement apparaît une seule fois ;
- si nécessaire : Clear Registry puis Register Events ;
- aucun doublon accepté.

### Phase 3 — tests par couche

1. Deadly Furniture dans `coc pamaTestZone`
2. Prison Alternative de base
3. Punishment Pack
4. Outdoor Event Pack
5. Bad Ends Windhelm
6. Bad Ends Riften
7. Bad Ends Solitude
8. Orkish Bounty Hunters
9. interactions avec followers
10. interactions avec Acheron / Practical Defeat
11. interactions avec Fill Her Up
12. contrôle des scènes susceptibles d'être interrompues par d'autres mods

### Phase 4 — létalité réelle

Après validation des tests non létaux :

- activer Lethality ;
- tester une exécution PAMA ;
- vérifier l'appel de Sovngarde Aftermath ;
- vérifier le retour en Tamriel ;
- vérifier la restauration correcte après décapitation ;
- contrôler l'absence d'interception parasite par Acheron.

## Modules PAMA évalués mais non retenus dans le cœur du chantier

### Pama´s Permanent Crucifixes 2.0

Optionnel.  
Standalone, persistance forte des victimes, aucun rôle nécessaire dans Prison Alternative.

### Pama´s Interactive Beatup Module 2.9

Optionnel.  
Framework léger de punition/whipping via ModEvents, mais non nécessaire au système carcéral.

### Pama´s Interactive Gallows 3.0

Optionnel.  
Gibet autonome avec fonctions létales/non létales, mais largement redondant avec Deadly Furniture pour le besoin actuel.

### Furniture Alignment Correction for NPC´s (No esp) 4.0.0

Ressource technique intéressante, sans ESP, mais inutile seule.  
À conserver comme outil potentiel si un furniture précis présente un problème d'alignement.

## Documents sources à ajouter

Les fiches Markdown détaillées de chaque mod seront ajoutées au chantier afin de conserver :

- description et version exacte ;
- prérequis ;
- installation ;
- incompatibilités ;
- notes de configuration ;
- informations utiles issues des pages LoversLab ;
- observations spécifiques à NEFARAM-Rhiven.

Structure prévue :

```text
docs/guides/PAMA/
├── README.md
├── mods/
│   ├── Prison-Alternative-2.0.3.md
│   ├── Pamas-Deadly-Furniture-34.5-R2.md
│   ├── Pama-Sovngarde-Aftermath-1.0.0.md
│   ├── Punishment-Pack-1.3.0.md
│   ├── Outdoor-Event-Pack-1.3.md
│   ├── Bad-Ends-Windhelm-1.3.0.md
│   ├── Bad-Ends-Riften-1.3.2.md
│   ├── Bad-Ends-Solitude-1.8.0-R2.md
│   └── Orkish-Bounty-Hunters-0.4.md
└── optional/
    ├── Permanent-Crucifixes-2.0.md
    ├── Interactive-Beatup-Module-2.9.md
    ├── Interactive-Gallows-3.0.md
    └── Furniture-Alignment-Correction-4.0.0.md
```

## État du chantier

- [x] Lecture des fiches principales
- [x] Sélection du cœur PAMA
- [x] Identification des addons optionnels
- [x] Première architecture fonctionnelle
- [x] Première proposition d'ordre MO2 gauche
- [x] Identification des risques DD / DCL / defeat / random scenes
- [x] Identification des conflits potentiels Windhelm / Riften / Solitude
- [x] Identification de Next-Gen Decapitations comme dépendance technique importante
- [ ] Ajouter les fiches Markdown sources
- [ ] Installer le bloc
- [ ] Vérifier les conflits xEdit
- [ ] Définir le load order droit définitif
- [ ] Configurer les MCM
- [ ] Régénérer Pandora
- [ ] Tester en mode non létal
- [ ] Tester les exécutions létales + Sovngarde
- [ ] Valider le bloc
- [ ] Reporter les mods retenus dans `docs/03-MODS-ADDED.md`
- [ ] Reporter les tests dans `docs/08-TESTING.md`
- [ ] Ajouter l'intégration au `CHANGELOG.md`

---

**Principe du chantier :** intégrer PAMA comme un écosystème cohérent, sans casser les systèmes existants de NEFARAM-Rhiven et sans imposer un remplacement inutile de l'architecture déjà fonctionnelle.
