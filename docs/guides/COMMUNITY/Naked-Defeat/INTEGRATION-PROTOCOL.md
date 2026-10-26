# Protocole d’intégration — Naked Defeat dans NEFARAM-Rhiven

> **Statut :** projet / non appliqué  
> **Cible envisagée :** NEFARAM 17.3.8 stabilisé + nouvelle partie  
> **Version Naked Defeat étudiée :** 6.50 FULL

---

## 1. Objectif

Étudier puis valider une intégration de **Naked Defeat** dans NEFARAM-Rhiven en remplacement éventuel de **Practical Defeat**, sans casser le mécanisme global de défaite.

L’intégration doit préserver :

- **Acheron** comme couche centrale de détection / distribution de la défaite ;
- **Yamete Kudasai** pour les catégories où son comportement est plus adapté, notamment si les tests confirment son intérêt pour les créatures / animaux ;
- les protections d’Acheron contre certains soft-locks, quêtes et situations particulières ;
- la cohérence avec Simple Slavery++, ZaZ, SexLab, SLATE, SLAL et les autres dépendances déjà présentes dans NEFARAM.

---

## 2. Architecture cible provisoire

| Rôle | Mod |
|---|---|
| Détection / orchestration de la défaite | **Acheron** |
| Conséquence principale pour défaites humanoïdes | **Naked Defeat + Acheron Bridge** |
| Gestion complémentaire de certaines défaites, notamment créatures | **Yamete Kudasai** |
| Ancienne conséquence principale | **Practical Defeat — désactivé dans le profil de test** |
| Hub secondaire de conséquences / esclavage | **Simple Slavery++**, selon configuration retenue |

### Réglage Naked Defeat essentiel

Dans Naked Defeat :

`Defeat on Bleedout = OFF`

Le but est d’éviter que Naked Defeat et Acheron tentent de gérer le même bleedout.

> [!IMPORTANT]
> Cette architecture est une **hypothèse de travail** à vérifier en jeu. Les catégories et poids réellement enregistrés dans Acheron devront être observés avant de décider la répartition finale entre Naked Defeat et Yamete Kudasai.

---

## 3. Pourquoi ne pas conserver Practical Defeat en parallèle ?

Les retours disponibles indiquent que le problème n’est pas que Practical Defeat soit mauvais, mais que **Naked Defeat propose davantage de conséquences et de scénarios**.

Le risque d’un montage :

**Acheron + Practical Defeat + Naked Defeat + Yamete Kudasai**

est de multiplier les systèmes capables de répondre au même événement, avec des comportements difficiles à diagnostiquer.

Le premier profil de test devra donc viser une architecture simplifiée :

**Acheron + Naked Defeat + Yamete Kudasai**, sans Practical Defeat.

---

## 4. Préconditions

Avant installation :

- [ ] NEFARAM 17.3.8 migré et stabilisé.
- [ ] Nouveau snapshot du panneau gauche MO2.
- [ ] Nouveau snapshot du panneau droit / plugins.
- [ ] Audit des mods et patches liés à Practical Defeat.
- [ ] Audit des versions actuelles d’Acheron et Yamete Kudasai.
- [ ] Vérification de Simple Slavery++.
- [ ] Vérification des dépendances Naked Defeat déjà présentes.
- [ ] Création d’un profil MO2 séparé, par exemple `ELEANOR - Naked Defeat TEST`.
- [ ] Nouvelle partie dédiée aux tests.

> [!WARNING]
> Ne pas effectuer cette expérimentation sur le profil stable d’Eleanor ni sur une sauvegarde destinée à la partie réelle.

---

## 5. Audit des dépendances Naked Defeat

À comparer avec le build 17.3.8 réel :

### Strictes / principales

- SexLab compatible ;
- SexLab Utility Plus si utilisé ;
- ZaZ Animation Pack 8+ selon la documentation Naked Defeat ;
- OSL Aroused Reborn ou équivalent compatible ;
- powerofthree’s Papyrus Extender ;
- Scrab’s Papyrus Extender ;
- Mfg Fix NG.

### Fortement recommandées / fonctionnelles

- Devious Devices NG ;
- Bathing in Skyrim Renewed ;
- SLATE ;
- SLAL ;
- packs d’animations nécessaires aux scénarios activés.

### À contrôler particulièrement

- version exacte de ZaZ présente dans NEFARAM ;
- filtres ZaZ dans SexLab / SLU+ ;
- Action Log SLATE Nymra ;
- patches communautaires Naked Defeat ;
- éventuels fichiers de traduction ;
- règles d’écrasement MO2.

---

## 6. Phase A — intégration minimale

Objectif : tester uniquement la chaîne **Acheron → outcome Naked Defeat**, avant d’activer les systèmes complexes.

### Étapes

1. Dupliquer le profil NEFARAM 17.3.8 stable.
2. Désactiver **Practical Defeat** et uniquement ses composants / patches réellement dépendants.
3. Conserver **Acheron**.
4. Conserver **Yamete Kudasai**.
5. Installer **Naked Defeat 6.50 FULL**.
6. Installer son **Acheron Bridge**.
7. Installer / vérifier uniquement les prérequis manquants.
8. Dans Naked Defeat, mettre :
   - `Defeat on Bleedout = OFF`
9. Initialiser SexLab / Naked Defeat conformément à la documentation.
10. Sauvegarder puis recharger.
11. Ouvrir le MCM Acheron et relever :
    - les conséquences enregistrées ;
    - leurs catégories ;
    - leurs poids ;
    - les éventuelles exclusions.

### À ne pas activer immédiatement

Au premier passage, éviter d’empiler inutilement :

- Local Slavery complet ;
- nombreuses conséquences secondaires ;
- réglages expérimentaux ;
- multiples addons de défaite.

Le but est d’abord de prouver que le **dispatch Acheron** fonctionne proprement.

---

## 7. Phase B — protocole de tests de défaite

Chaque cas doit être testé sur une sauvegarde reproductible.

Pour chaque test, noter :

- lieu ;
- ennemi responsable ;
- catégorie Acheron observée si identifiable ;
- outcome sélectionné ;
- délai entre bleedout et début réel de la conséquence ;
- état du joueur après la scène ;
- capacité à sauvegarder / recharger ;
- retour au gameplay normal ;
- anomalies Papyrus éventuelles.

### Cas minimums

| # | Situation | Résultat attendu |
|---|---|---|
| 1 | Bandit humanoïde seul, extérieur | Acheron → Naked Defeat |
| 2 | Groupe de bandits, extérieur | Une seule conséquence cohérente |
| 3 | Humanoïde, intérieur / donjon | ND démarre sans soft-lock |
| 4 | Animal | Vérifier si YK prend correctement la main |
| 5 | Créature | Vérifier répartition ND / YK |
| 6 | Garde | Observer catégorie et outcome Acheron |
| 7 | Civil / NPC non hostile | Vérifier qu’aucune conséquence absurde ne part |
| 8 | Follower présent | Follower et joueur récupèrent correctement |
| 9 | Quête active | Aucun blocage de quête / contrôle |
| 10 | Défaite puis save/reload | État stable après rechargement |
| 11 | Deux défaites successives | Pas d’état résiduel ni double déclenchement |
| 12 | Fast travel / changement de cellule après conséquence | Aucun script bloqué |

### Tests supplémentaires

- intérieur très chargé ;
- combat avec plusieurs factions ;
- friendly fire ;
- follower custom framework ;
- ennemis non vanilla ;
- lieux où Acheron possède des protections / exclusions ;
- défaite pendant une scène ou un état spécial si cela peut arriver en gameplay réel.

---

## 8. Phase C — répartition Naked Defeat / Yamete Kudasai

Une fois la chaîne minimale stable :

1. relever toutes les catégories / poids dans Acheron ;
2. déterminer si ND et YK se chevauchent ;
3. ajuster **les poids Acheron** plutôt que de laisser deux systèmes se disputer arbitrairement le même événement ;
4. viser, si les tests le confirment :
   - **humanoïdes → Naked Defeat** ;
   - **créatures / animaux → Yamete Kudasai** ;
5. retester les mêmes cas.

> [!NOTE]
> Cette répartition n’est pas encore validée. Elle reprend la logique rencontrée dans plusieurs installations Acheron/Practical Defeat/YK, adaptée ici avec Naked Defeat à la place de Practical Defeat.

---

## 9. Phase D — Local Slavery et Simple Slavery++

Seulement après validation du mécanisme de défaite de base.

Questions à trancher :

- Local Slavery Naked Defeat doit-il être un outcome principal ?
- Simple Slavery++ doit-il rester un hub alternatif ?
- Les deux peuvent-ils coexister avec des probabilités clairement séparées ?
- Quels mods de destination sont déjà présents dans NEFARAM ?

### Test recommandé

Commencer avec :

- Local Slavery Naked Defeat activé ;
- Simple Slavery++ conservé comme **outcome distinct** ;
- probabilités faibles / contrôlées ;
- tests sur nouvelle sauvegarde dédiée.

---

## 10. Contrôles après chaque scénario

Après chaque conséquence :

- [ ] le joueur peut bouger ;
- [ ] caméra normale ;
- [ ] inventaire cohérent ;
- [ ] followers cohérents ;
- [ ] aucune faction temporaire anormale ;
- [ ] aucune invulnérabilité résiduelle ;
- [ ] aucun bleedout permanent ;
- [ ] aucune scène SexLab bloquée ;
- [ ] sauvegarde possible ;
- [ ] rechargement possible ;
- [ ] Acheron prêt pour une nouvelle défaite ;
- [ ] Naked Defeat ne conserve pas un événement actif ;
- [ ] Yamete Kudasai ne démarre pas en parallèle sans raison.

---

## 11. Logs et diagnostic

En cas d’anomalie, conserver :

- `Papyrus.0.log` ;
- capture du MCM Acheron ;
- capture du MCM Naked Defeat ;
- capture du MCM Yamete Kudasai ;
- panneau droit MO2 ;
- load order du profil de test ;
- description exacte du scénario de reproduction.

Pour un problème de scène Naked Defeat, noter également le délai entre le bleedout et le démarrage de la scène.

---

## 12. Critères de validation

L’intégration ne sera considérée comme suffisamment sûre pour la vraie partie d’Eleanor que si :

- aucun double déclenchement ND / YK / autre framework n’est observé ;
- Practical Defeat peut rester absent sans fonction essentielle perdue ;
- les défaites humanoïdes sont fiables ;
- les défaites créatures / animaux sont cohérentes ;
- les cas de quêtes / lieux sensibles ne soft-lockent pas ;
- plusieurs défaites successives sont possibles ;
- save/reload reste fiable ;
- aucune dégradation progressive de la stabilité n’est observée ;
- Local Slavery et/ou Simple Slavery++ sont clairement séparés et testés.

---

## 13. Plan de retour arrière

Le profil de test étant séparé et la partie étant neuve :

1. ne jamais réutiliser la sauvegarde de test pour la partie stable ;
2. conserver le profil NEFARAM 17.3.8 stable intact ;
3. en cas d’échec, abandonner le profil de test plutôt que tenter de nettoyer les scripts ;
4. revenir à l’architecture NEFARAM validée avec Practical Defeat.

---

## 14. État actuel des connaissances

### Confirmé par la documentation Naked Defeat

- Naked Defeat possède un **Acheron Bridge**.
- Avec le bridge, `Defeat on Bleedout` doit être désactivé pour éviter le doublon de gestion.
- Naked Defeat dispose de nombreuses conséquences supplémentaires, dont Local Slavery.

### Confirmé par les retours NEFARAM / communauté recueillis

- plusieurs utilisateurs ont fait fonctionner Naked Defeat dans une installation NEFARAM via Acheron ;
- des utilisateurs récents préfèrent Naked Defeat à Practical Defeat pour sa richesse fonctionnelle ;
- des retours plus anciens signalaient des problèmes de priorité entre Naked Defeat, Practical Defeat et Yamete Kudasai ;
- ces retours renforcent l’intérêt d’une architecture simplifiée et d’un audit précis des weights Acheron.

### À vérifier dans notre build

- catégories Acheron exactes enregistrées par Naked Defeat 6.50 ;
- catégories exactes de Yamete Kudasai ;
- poids par défaut ;
- patches actuellement présents dans NEFARAM 17.3.8 ;
- compatibilité réelle avec les versions de ZaZ / SexLab / SLU+ du build final.

---

## 15. Décision provisoire

**Ne pas intégrer maintenant.**

Le chantier est préparé pour être repris **après stabilisation de NEFARAM 17.3.8**, sur profil MO2 dédié et nouvelle partie.

Architecture de départ retenue pour les futurs tests :

**Acheron + Naked Defeat 6.50 + Acheron Bridge + Yamete Kudasai**

avec :

**Practical Defeat désactivé**  
**Naked Defeat → Defeat on Bleedout = OFF**

La répartition finale des outcomes sera décidée uniquement après observation réelle des catégories et weights Acheron.


---

## 16. Sources techniques de référence

### Dépôt crajjjj — Naked Defeat

**GitHub :** https://github.com/crajjjj/Naked-Defeat-5-26

Ce dépôt est une source technique particulièrement importante pour le chantier d’intégration. Malgré son nom historique `Naked-Defeat-5-26`, il a continué à évoluer jusqu’à des versions **6.46.x** et contient des correctifs détaillés autour de la chaîne :

**Acheron defeat → Naked Defeat → punishment / furniture / whipping → release**

Les points documentés dans son changelog qui devront être comparés à Naked Defeat 6.50 incluent notamment :

- restauration centralisée de l’état joueur / Acheron après release, abort ou Unstuck ;
- restauration correcte du bleedout recovery ;
- remise à zéro de `PlayerDownAlready` après certains départs Acheron avortés ;
- limitation des waits ragdoll pouvant provoquer un blocage ;
- nettoyage des états résiduels des whippers lors d’un abort ;
- correction du deuxième assaillant Acheron ;
- correction des classifications erronées de type de défaite dues au friendly fire ou aux NPC lointains ;
- rafraîchissement des followers au chargement, avec prise en compte de **Nether’s Follower Framework** ;
- possibilité, dans certains cas de mort accidentelle et selon les réglages, de laisser la main à **Acheron / vanilla** plutôt que de forcer Naked Defeat.

> [!WARNING]
> Ce dépôt ne doit **pas** être appliqué tel quel sur Naked Defeat 6.50. La branche publique la plus récente observée cible une base 6.46.x et contient également des adaptations spécifiques **SexLab P+**. La documentation 6.50 indique qu’une partie des correctifs de crajjjj est progressivement intégrée upstream.
>
> Son intérêt pour NEFARAM-Rhiven est donc principalement **documentaire et comparatif** : chaque correction importante devra être vérifiée dans 6.50 avant de conclure qu’elle manque encore.

### Audit futur à réaliser

Lors de la reprise du chantier :

1. comparer le changelog / les commits crajjjj avec les scripts de Naked Defeat 6.50 ;
2. classer chaque correctif en :
   - **intégré en 6.50** ;
   - **intégré différemment** ;
   - **toujours absent** ;
   - **obsolète / non applicable** ;
3. utiliser cette comparaison pour compléter le protocole de test Acheron et les cas NFF / followers ;
4. ne créer un patch Rhiven que si un correctif réellement nécessaire manque encore dans la version utilisée.
