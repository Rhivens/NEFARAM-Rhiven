# Animations — OAR et configuration Eleanor

**Validation initiale :** NEFARAM-Rhiven 17.3.7 · profil MO2 `ELEANOR Stable` · configuration active validée en jeu le 11/10/2026.  
**Baseline actuelle :** NEFARAM-Rhiven 17.3.8 · profil `Eleanor Stable 17.3.8`. La configuration a été conservée pendant la migration et validée après plusieurs tests en jeu sans problème observé.

**Statut : VALIDÉ sur la configuration actuelle.** Les éventuelles anomalies rares de locomotion, d'entrave, de combat ou de transition découvertes pendant la partie définitive seront traitées au cas par cas comme du dépannage normal de gros modpack ; elles ne constituent plus une validation en attente dans la roadmap.

## 1. Choix final

| Fonction | Configuration retenue |
|---|---|
| Idles féminins | **Seamless Varied Feminine Idles**, fourni dans NEFARAM |
| Gulan0 Female Random Idle v1.0 / v2.0 | **DÉCOCHÉS** dans MO2, conservés pour essais futurs |
| Gulan0 OAR Settings - Rhiven (idles) | **DÉCOCHÉ**, archive des réglages personnalisés |
| Marche / course / sprint | **Gulan0 Walk-Run-Sprint OAR-player v1.1**, actif et ciblé joueur |
| Course | Fichiers **originaux** de Gulan0, sans `female_run_Update` |
| Sprint | `female Sprint Revised Version`, fichier `mt_sprintforward.hkx` uniquement |
| Priorité OAR Gulan0 locomotion | **1000002**, sauvegardée en `user.json` |

**Pourquoi les idles Gulan0 sont-ils décochés ?** Comparaison en jeu et découverte d'anciennes notes NEFARAM V16 : l'utilisateur préférait déjà **Seamless Varied Feminine Idles** aux idles Gulan0. NEFARAM récent intègre désormais Seamless. Les archives Gulan0 V1 + V2 restent présentes pour un éventuel mélange sélectif, sans fournir de fichiers au jeu tant qu'elles sont décochées.

## 2. Mods MO2 et organisation

Bloc d'animations du **panneau gauche** (noms observés ; les noms peuvent être renommés sans changer les fichiers) :

- `Gulan0-Female Random Idle 1.0 - Rhiven - DECOCHE` — inactif.
- `Gulan0-Female Random Idle 2.0 - Rhiven - DECOCHE` — inactif.
- `Gulan0 OAR Settings - Rhiven - DECOCHE` — inactif.
- `Gulan0 - Walk-Run-Sprint- OAR-player - Rhiven` — actif.
- `Gulan0 - Female-run-Update OAR - Rhiven` — **actif mais renommage conseillé** : ne contient plus les cinq fichiers de mise à jour de course ; il ne conserve que le sprint révisé.
- `Gulan0 Walk Run Sprint OAR Settings - Rhiven` — actif.

La sélection `player only` est portée par les conditions OAR ; la présence de sous-mods féminin et masculin dans l'archive locomotion ne signifie **pas** diffusion aux PNJ.

## 3. OAR — configuration et priorités

**Open Animation Replacer 3.2.0**. Ouvrir l'interface en jeu avec **Maj + O**, puis sélectionner le joueur `00000014` dans « Evaluate for reference ».

### Locomotion active : `Gulan0_walk_run_sprint → Gulan0_female`

- Priorité auteur : `2`.
- Priorité Rhiven : **`1000002`**.
- Conditions : `NOT IsChild`, `IsFemale`, `IsActorBase(Skyrim.esm, 00000007)` (base du personnage joueur).
- Sous-mod masculin d'origine conservé, non applicable au personnage féminin testé.
- Comportements observés dans **Animation Log** après la modification : Gulan0 remplace `MT_WalkForward`, `MT_RunForward` et `MT_SprintForward`.
- Avant modification, des remplacements hérités DAR `Legacy / 1000001` gagnaient pour la marche et la course. Ils restent **inchangés** pour leurs autres usages.
- Le contrôle visible du sous-mod Legacy `1000001` montrait notamment : pas d'arme dégainée, sexe féminin, exclusions liées aux effets de rampement/amputation, etc. Ne pas le désactiver globalement.

**Important :** la priorité `1000002` est un choix local validé pour ces trois animations, et non une priorité universelle à appliquer à tous les sous-mods OAR. Les animations conditionnelles spécialisées peuvent avoir d'autres priorités ; garder leurs règles intactes.

### Idles alternatifs archivés : `Gulan0-Idle action → Idle action`

Si réactivés plus tard :
- V1 et V2 sont complémentaires et utilisent une bibliothèque commune de variantes ; dans MO2, seuls deux `config.json` étaient écrasés et aucun HKX entre V1/V2.
- Priorité originale `100007` ; priorité de test Rhiven **`900009`**, supérieure aux huit submods Seamless (`900001` à `900008`).
- Conditions : joueur féminin adulte via `IsActorBase(Skyrim.esm, 00000007)`.
- `Variant Mode: Random`; `Replace on loop` actif ; `Blend between variants` et `Reset random on loop or echo` désactivés.
- L'ancien `user.json` archivé enregistre **62 variantes HKX désactivées** (`disabled: true`).
- Les idles Gulan0 avaient été confirmés fonctionnels dans le journal OAR, mais écartés **par préférence visuelle**, pas à cause d'un dysfonctionnement.
- `Gulan0 Idle Action Expand` optionnel non intégré : l'auteur signale un tremblement de caméra possible sur `mt_idle25_d`, `mt_idle26_d`, `mt_idle27_d`.

## 4. Correctifs HKX locomotion

Archive principale : [Gulan0 Animations Walk-run-sprinting rework](https://www.nexusmods.com/skyrimspecialedition/mods/164743), version `Gulan0_walk_run_sprint-OAR-player`.

- `female_run_Update` (01/08/2026) : **écarté après comparaison visuelle**. Il remplaçait `mt_runforward.hkx`, `mt_runforwardleft.hkx`, `mt_runforwardright.hkx`, `mt_runleft.hkx`, `mt_runright.hkx`. L'utilisateur préfère les courses d'origine.
- `female Sprint Revised Version` : **retenu**. Ajuste le mouvement des épaules, des coudes et des mains ; contient uniquement `mt_sprintforward.hkx`.

Le mod MO2 de correctif doit contenir uniquement :

```text
meshes/actors/character/animations/OpenAnimationReplacer/
  Gulan0_walk_run_sprint/
    Gulan0_walk run sprint Submod 1/
      female/
        mt_sprintforward.hkx
```

**Contrôle attendu dans MO2 → Conflicts → Advanced : un conflit gagnant** contre le `mt_sprintforward.hkx` du mod principal. Lors de l'essai provisoire avec l'update de course, six conflits gagnants avaient été validés ; après retour aux animations originales, cinq ont été volontairement retirés.

## 5. Persistance des réglages — MO2 / SKSE Output

NEFARAM utilise le mod de sorties **`SKSE Output`**. Après **User Mode → Save submod config (User)**, OAR peut y écrire le fichier de personnalisation.

Chemin de configuration **locomotion** :

```text
meshes/actors/character/animations/OpenAnimationReplacer/
  Gulan0_walk_run_sprint/
    Gulan0_walk run sprint Submod 1/
      user.json
```

Ce `user.json` (vérifié) définit la priorité `1000002` et conserve les conditions joueur/féminin/adulte. Il a été copié dans `Gulan0 Walk Run Sprint OAR Settings - Rhiven`, placé après le mod principal. Vérifier le fichier gagnant dans MO2 après toute nouvelle sauvegarde depuis OAR : ne pas laisser une copie plus récente dans `SKSE Output` écraser silencieusement l'override Rhiven.

Pour les **idles Gulan0 archivés**, l'équivalent est :

```text
meshes/actors/character/animations/OpenAnimationReplacer/
  Gulan0-Idle action/
    Idle action/
      user.json
```

Après modification en jeu : sauvegarder le **sous-mod** avec `Save submod config (User)`, et non seulement le mod parent. Les configurations OAR ne dépendent pas de la sauvegarde Skyrim ; elles pourront être réutilisées lors de la partie définitive démarrée depuis `NEFARAM_Start`, si les mods MO2 et leurs fichiers de configuration sont conservés.

## 6. Procédure de diagnostic OAR réutilisable

1. **Inspect Mode** : vérifier le sous-mod, la priorité, les conditions et les fichiers HKX.
2. Sélectionner le joueur `00000014` dans « Evaluate for reference ».
3. **Animation Log** : provoquer l'action, lire `Mod`, `Submod`, `Clip` et le chemin effectivement gagné ; `Show trace` sert au diagnostic des règles candidates.
4. Ne pas confondre **priorité MO2** (fichier gagnant sur disque virtuel) et **priorité OAR** (remplacement d'animation gagnant en jeu).
5. **User Mode** : ajuster la règle ciblée ; **Save submod config (User)** ; ranger le `user.json` dans un mod personnel.
6. Relancer Skyrim pour confirmer la persistance ; comparer visuellement avant de figer.

L'avertissement OAR `Detected mods sharing the same priority` concernait notamment des sous-mods de **DeviousFollowers**, **Amputator** et **XPMSE** à priorité maximale `2147483647`. Ce constat **ne prouve pas de conflit fonctionnel** ; aucune modification préventive n'a été effectuée.

## 7. Bilan et réserves

- **Confirmé en jeu :** idles Gulan0 (lors du test), puis Seamless retenu ; remplacement Gulan0 de marche, course et sprint ; conditions Player Only ; fonctionnement du réglage de priorité OAR.
- **Confirmé sur fichiers :** six HKX du patch provisoire correctement superposés au mod principal ; puis décision finale de ne garder que le correctif sprint.
- **Suivi non bloquant :** si une anomalie apparaît sur une transition particulière, un état d'entrave, le combat, une posture avec arme ou une scène rare, la diagnostiquer au cas par cas avec OAR et les fichiers gagnants.
- **Aucun changement** aux règles de DeviousFollowers, Amputator, XPMSE ou autres anciens packs DAR.

## 8. Sources

- [Gulan0 Female Random Idle v1](https://www.nexusmods.com/skyrimspecialedition/mods/165916)
- [Gulan0 Female Random Idle v2](https://www.nexusmods.com/skyrimspecialedition/mods/185003)
- [Gulan0 Walk / Run / Sprint](https://www.nexusmods.com/skyrimspecialedition/mods/164743)

Document construit à partir de l'inspection des JSON fournis, des captures MO2/OAR 3.2.0 et des tests en jeu effectués sur NEFARAM-Rhiven 17.3.7.
