# Skyrim SE / NEFARAM — Référentiel de sécurité des champs pour la traduction FR

> **État : brouillon évolutif (v0.1)** — à enrichir et vérifier sur des enregistrements réels avec xTranslator / xEdit avant toute automatisation.
>
> **Objectif :** traduire NEFARAM Rhiven Modded rapidement et avec un maximum de qualité, sans casser les plugins ni les scripts. La référence technique est **le mod original installé**.

## Légende

- **TRADUISIBLE** : contenu textuel destiné à être lu par le joueur ; conserver les balises, les variables et les contraintes du champ.
- **À CONTRÔLER** : la possibilité de traduire dépend du type d'enregistrement, de la valeur et de l'usage en jeu ; pas de traduction automatique aveugle.
- **NON TRADUISIBLE** : structure, identifiant ou donnée technique à préserver à l'identique.

**Important :** une signature telle que `FULL`, `DNAM` ou `VNAM` ne suffit **pas** à déterminer seule la sécurité. Toujours indiquer le **type de record parent** et, si besoin, le chemin complet du champ. `NPC_`, `DIAL` et `INFO` désignent des types de records, et non des champs librement traduisibles dans leur totalité.

## Référentiel initial

| Record parent | Champ / contenu | Classification | Règle |
|---|---|---|---|
| `NPC_` | `FULL` — nom propre d'un PNJ vanilla | **TRADUISIBLE sous référence** | Reprendre exactement le nom officiel de la VF Bethesda si une correspondance existe ; ne pas inventer de traduction. |
| `NPC_` | `FULL` — nom propre d'un nouveau PNJ de mod | **À CONTRÔLER** | **Conserver le nom d'origine par défaut** (ex. `Elara Stone`), sauf choix de localisation explicitement établi et cohérent avec le mod. |
| `NPC_` | `FULL` — désignation générique / fonction | **TRADUISIBLE** | Traduire le rôle ou titre (ex. `Guard of Castle Something` → `Garde du château de Something`), mais protéger les noms propres contenus dans la désignation. |
| `NPC_` | `EDID` | **NON TRADUISIBLE** | Identifiant interne, pas un nom affiché à traduire. |
| `DIAL` | Texte affiché (par ex. champ `FULL`, selon record) | **TRADUISIBLE** | Traduire uniquement la chaîne destinée au joueur ; préserver le reste du record. |
| `INFO` | Réplique affichée (souvent `NAM1`) | **TRADUISIBLE** | Traduire le dialogue en contexte, préserver variables, balises et marqueurs. |
| Tous | `EDID` | **NON TRADUISIBLE** | Préserver intégralement. |
| Tous | `CTDA` / données de conditions | **NON TRADUISIBLE** | Logique de fonctionnement, pas de texte à localiser directement. |
| Selon record | `FULL` / `DESC` | **À CONTRÔLER** | Habituellement du texte visible, mais vérifier le sens et le record parent. |
| Selon record | `DNAM`, `VNAM` | **À CONTRÔLER** | Sous-records aux fonctions variables ; jamais classer globalement « safe » ou « non-safe » sans contexte. |
| Selon record | `VMAD` | **À CONTRÔLER — HAUT RISQUE** | Contient des propriétés Papyrus ; certaines valeurs sont des textes visibles, d'autres des clés/identifiants indispensables. |
| Fichiers `.pex` | Identifiants internes, noms de variables, fonctions, propriétés | **NON TRADUISIBLE** | Conserver strictement ; exploiter les protections du traducteur. |
| Fichiers `.pex` | Littéraux de notification / boîte de dialogue | **À CONTRÔLER** | Peut être traduit si confirmé comme texte présenté au joueur ; inspecter les usages ambigus. |
| Fichiers `.pex` | Chaînes littérales servant de clés, états, noms d'animation, chemins ou événements | **NON TRADUISIBLE** | Ne pas modifier même si ces chaînes ressemblent à de l'anglais ordinaire. |
| MCM | Libellés, descriptions et aides visibles | **TRADUISIBLE** | Suivre le format du MCM concerné, sans modifier les clés techniques. |
| MCM | Identifiants de réglages, clés JSON, variables | **NON TRADUISIBLE** | Préserver la structure et les identifiants. |

## Cas de référence : nom des PNJ (`NPC_ / FULL`)

Une même catégorie de champ peut contenir **deux sortes d'information** :

1. **Identité propre** : le nom d'un personnage — ne pas traduire automatiquement. Si le PNJ est issu du jeu officiel, utiliser la nomenclature française officielle de Skyrim ; si le personnage est ajouté par un mod et n'a pas d'équivalent français attesté, conserver par défaut son nom original.
2. **Désignation générique** : un métier, une fonction, un rang ou un titre — traduire le descriptif, mais **ne pas altérer les noms propres** incorporés (lieux, familles, factions).

Exemples **fictifs** (illustratifs, non extraits d'un mod) :

| EN | FR suggéré | Justification |
|---|---|---|
| `Elara Stone` | `Elara Stone` | PNJ inédit : nom propre conservé. |
| `Castle Blackthorn Guard` | `Garde du château de Blackthorn` | Désignation générique traduite ; lieu fictif conservé. |
| `Whiterun Guard` | `Garde de Blancherive` | Désignation générique + toponyme officiel en VF. |

**Exception :** les pseudonymes descriptifs, titres honorifiques, appellations narratives et noms ayant une VF explicitement attestée peuvent nécessiter une traduction — à documenter au cas par cas.

## Méthode Rhiven

1. Chercher une traduction FR existante pour la **bonne version**, examiner son contenu et privilégier les traductions DSD lorsqu'elles sont fiables et couvrent le besoin.
2. Sinon, travailler avec **xTranslator** sur les fichiers originaux ; utiliser le filtrage par type de champ. Évaluer un export DSD uniquement si fiable et simple.
3. Utiliser l'**API OpenAI** et un prompt Skyrim ciblé, associés à un dictionnaire personnel séparé de Fallout 4.
4. Protéger les noms propres, termes Bethesda, marqueurs, scripts et champs sensibles ; relire prioritairement les cas ambigus.
5. Effectuer des tests en jeu ; conserver la traduction comme mod MO2 distinct dès que possible.

## À compléter

- Matrice détaillée par **record parent + sous-record** : `QUST`, `BOOK`, `MESG`, `ACTI`, `MGEF`, `SPEL`, `PERK`, etc.
- Comportement réel des filtres et verrous de la version installée de xTranslator.
- Règles spécialisées pour les noms de lieux, les livres, les rangs, les factions, les dialogues et les MCM.
- Dictionnaire Skyrim FR (terminologie Bethesda et termes propres aux mods), avec sources et exceptions.
- Exemples vérifiés dans NEFARAM ; ne pas confondre les exemples fictifs ci-dessus avec des données réelles.

**Principe :** *une chaîne technique douteuse vaut mieux intacte qu'un script cassé en français.*
