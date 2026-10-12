# Skyrim SE / NEFARAM — Référentiel de sécurité des champs pour la traduction FR

> **État : brouillon évolutif (v0.3)** — à enrichir et vérifier sur des enregistrements réels avec xTranslator / xEdit avant toute automatisation.
>
> **Objectif :** traduire NEFARAM Rhiven Modded rapidement et avec un maximum de qualité, sans casser les plugins ni les scripts. La référence technique est **le mod original installé**.

## Légende

- **TRADUISIBLE** : contenu textuel destiné à être lu par le joueur ; conserver les balises, les variables et les contraintes du champ.
- **À CONTRÔLER** : la possibilité de traduire dépend du type d'enregistrement, de la valeur et de l'usage en jeu ; pas de traduction automatique aveugle.
- **NON TRADUISIBLE** : structure, identifiant ou donnée technique à préserver à l'identique.

**Important :** une signature telle que `FULL`, `DNAM` ou `VNAM` ne suffit **pas** à déterminer seule la sécurité. Toujours indiquer le **type de record parent** et, si besoin, le chemin complet du champ. `NPC_`, `DIAL` et `INFO` désignent des types de records, et non des champs librement traduisibles dans leur totalité.

## Référentiel initial

| Record parent | Champ / contenu | Classification | Traitement API | Règle |
|---|---|---|---|---|
| `NPC_` | `FULL` — PNJ vanilla | **TRADUISIBLE sous référence** | **API avec glossaire verrouillé** | Reprendre exactement la VF Bethesda si attestée ; sinon ne pas inventer. |
| `NPC_` | `FULL` — nom propre inédit | **À CONTRÔLER** | **EXCLURE de l'auto-traduction** | Conserver le nom original par défaut ; exception documentée. |
| `NPC_` | `FULL` — désignation générique | **TRADUISIBLE** | **API sous contrainte** | Traduire la fonction ; protéger noms propres de lieux, familles, factions. |
| `NPC_` | `EDID` | **NON TRADUISIBLE** | **EXCLURE** | Identifiant interne. |
| `DIAL` | Texte affiché (par ex. `FULL`, selon record) | **TRADUISIBLE** | **API autorisée** | Ne traduire que la chaîne visible, jamais le record entier. |
| `INFO` | Réplique affichée (`NAM1`, si présent) | **TRADUISIBLE** | **API autorisée** | Respecter contexte, variables, balises et marqueurs. |
| Tous | `EDID` | **NON TRADUISIBLE** | **EXCLURE** | Préserver à l'identique. |
| Tous | `CTDA` / conditions | **NON TRADUISIBLE** | **EXCLURE** | Logique de jeu. |
| Selon record | `FULL` / `DESC` | **À CONTRÔLER** | **API autorisée après identification** | Le contenu est souvent visible ; vérifier le record parent. |
| Selon record | `DNAM`, `VNAM` | **À CONTRÔLER** | **BLOQUÉ par défaut** | Autoriser seulement après validation du couple record/champ et du type de donnée. |
| Selon record | `VMAD` | **À CONTRÔLER — HAUT RISQUE** | **BLOQUÉ par défaut** | Propriétés Papyrus : textes visibles et clés techniques peuvent coexister. |
| `.pex` | Variables, propriétés, fonctions, identifiants | **NON TRADUISIBLE** | **EXCLURE** | Conserver strictement. |
| `.pex` | Notifications / messages littéraux | **À CONTRÔLER** | **API après validation de l'usage** | Confirmer que la chaîne est affichée, puis traduire exclusivement sa valeur. |
| `.pex` | Clés, états, animations, chemins, événements | **NON TRADUISIBLE** | **EXCLURE** | Même si cela ressemble à une phrase anglaise. |
| MCM | Libellés / aides visibles | **TRADUISIBLE** | **API autorisée après validation du format** | Préserver variables et balises de formatage. |
| MCM | Clés JSON, réglages, identifiants | **NON TRADUISIBLE** | **EXCLURE** | Préserver la structure. |

### Signification de « Traitement API »

- **API autorisée** : envoyer seulement la valeur textuelle extraite, jamais les octets techniques ni l'enregistrement complet ; préserver les marqueurs.
- **API sous contrainte / avec glossaire verrouillé** : fournir les noms officiels et noms propres protégés, puis vérifier la sortie.
- **API après validation** : exclu du traitement par lot tant que son usage réel n'a pas été confirmé.
- **BLOQUÉ par défaut** : aucune traduction automatique sans décision explicite documentée sur un couple *record parent + champ* (et au besoin sa valeur).
- **EXCLURE** : ne jamais transmettre comme texte à traduire et ne jamais modifier via traduction.

**Principe de sécurité :** un filtre d'interface et un prompt ne garantissent pas la protection binaire. Contrôler le résultat et maintenir une copie intacte du mod original ; une chaîne visible peut contenir des références techniques.

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

## Inventaire complémentaire — records et sous-records (v0.3)

Cette section est construite à partir de la liste fournie par Rhiven, avec des **règles prudentes de localisation**, et non une validation exhaustive des définitions binaires. Elle sépare volontairement les **types de records** des **sous-records**. Les signatures homonymes peuvent varier selon le record parent et les versions du jeu.

### En-tête du plugin `TES4`

| Sous-record ou donnée | Usage général | Traduction | Traitement API |
|---|---|---|---|
| `HEDR` | Version de format, compteurs, prochain FormID | **NON TRADUISIBLE** | **EXCLURE** |
| `CNAM` | Auteur du plugin | **NON TRADUISIBLE** (métadonnée conservée) | **EXCLURE** |
| `SNAM` | Description du plugin, lorsqu'elle est présente | **À CONTRÔLER** (métadonnée) | **BLOQUÉ par défaut** |
| `MAST` | Noms des fichiers maîtres | **NON TRADUISIBLE** | **EXCLURE** |
| `DATA` associé à `MAST` | Données techniques | **NON TRADUISIBLE** | **EXCLURE** |
| `ONAM` | Références d'enregistrements surchargés (selon format) | **NON TRADUISIBLE** | **EXCLURE** |
| `INTV`, `MODV`, `MREG`, `EFSF`, `EFSI`, `OBNK`, `OBNM` | Signatures mentionnées dans la liste de travail, à confirmer pour Skyrim SE | **NON TRADUISIBLE / PRÉSENCE À CONFIRMER** | **EXCLURE** |
| `FULL` dans `TES4` | Mentionné dans la liste initiale ; sens et présence à vérifier | **À CONTRÔLER — PAS D'AUTOMATISME** | **BLOQUÉ par défaut** |

**Note :** ne pas généraliser la valeur HEDR 0.94 donnée pour LE. Les en-têtes de plugins Skyrim SE peuvent utiliser notamment 1.70 et 1.71. `ONAM` n'est pas une « table ESL fixe de 16 384 FormIDs » dans sa définition générale.

### Sous-records communs — règles par défaut

| Signature | Sens indiqué dans la liste initiale | Traduction | Traitement API |
|---|---|---|---|
| `EDID` | Editor ID | **NON TRADUISIBLE** | **EXCLURE** |
| `FULL` | Nom affiché | **À CONTRÔLER** (nom propre / générique / VF officielle) | **API avec règles de noms** |
| `MODL`, `MODT`, `MODS` | Modèle et textures / chemins ou références | **NON TRADUISIBLE** | **EXCLURE** |
| `KSIZ`, `KWDA` | Nombre et références de keywords | **NON TRADUISIBLE** | **EXCLURE** |
| `DATA`, `OBND`, `ABDT`, `ENAM` | Données structurées, volumes, enchantements, etc. | **NON TRADUISIBLE par défaut** (préciser parent) | **EXCLURE** |
| `SCNA`, `CDTA` | Données de scripts/conditions selon le record ; détail à vérifier | **NON TRADUISIBLE par défaut** | **EXCLURE** |
| `XXXX` | Indicateur de taille étendue d'un sous-record | **NON TRADUISIBLE** | **EXCLURE** |

**Attention :** la limite ordinaire d'un champ taille de sous-record est de 65 535 octets, pas 255 ; `XXXX` permet une taille étendue. Il ne faut pas confondre cela avec d'autres contraintes du format.

### Familles de records répertoriées

Les signatures ci-dessous sont des **conteneurs**, pas des autorisations de traduction. Les champs affichables qu'ils contiennent peuvent être traités selon la matrice principale. Éviter toute traduction automatique de **tous les sous-records** d'une famille.

| Famille | Types cités dans l'inventaire | Règle API |
|---|---|---|
| Objets / équipements | `WEAP`, `ARMO`, `ALCH`, `AMMO`, `MISC`, `INGR`, `KEYM`, `BOOK`, `SPEL`, `ENCH`, `MGEF`, `SLGM`, `SCRL`, `PROJ` | **Champs textuels uniquement**, avec glossaire |
| PNJ et apparence | `NPC_`, `ACHR`, `ACRE`, `RACE`, `OTFT`, `CLAS`, `PACK`, `CSTY`, `EYES`, `HAIR`, `HDPT` | **Champs textuels uniquement**, protéger les noms propres |
| Monde et environnement | `CELL`, `WRLD`, `LCTN`, `REGN`, `WTHR`, `CLMT`, `REFR`, `ACTI`, `DOOR`, `FURN`, `TREE`, `FLOR`, `GRAS`, `LAND`, `LTEX`, `NAVM`, `LIGH`, `LGTM`, `LSCR` | **Champs textuels uniquement**, noms de lieux à contrôler |
| Quêtes / dialogues | `QUST`, `SMBN`, `SMEN`, `SMQN`, `DIAL`, `DLBR`, `INFO`, `DLVW`, `MESG`, `SCEN` | **Textes affichés uniquement**, jamais conditions ou liens internes |
| Gameplay et autres systèmes | `GMST`, `GLOB`, `FLST`, `LVLI`, `LVLN`, `LVSP`, `PERK`, `ASPC`, `ECZN`, `HAZD`, `PHZD`, `PGRE`, `RELA`, `FACT`, `KYWD`, `ASTP`, `MOVT`, `MATT`, `MUSC`, `VTYP`, `WATR`, `CAMS`, `CPTH`, `AACT`, `IDLE`, `ANIO`, `SPGD`, `RFCT`, `EFSH`, `EXPLO`, `IPCT`, `IPDS`, `FSTP`, `FSTS`, `SOUN`, `MUST`, `SNDR`, `SNCT`, `REVB`, `SOPM`, `SHOU`, `WOOP`, `IMGS`, `IMAD`, `TXST`, `COLL`, `ARTO`, `NOTE`, `COBJ`, `MSTT`, `STAT`, `APPAR`, `TACT`, `DOBJ` | **Bloqué par défaut**, sauf champs textuels identifiés dans un record précis |

Certaines signatures de cette liste peuvent être issues de nomenclatures multi-jeux ou anciennes : **ne pas présumer de leur présence dans un plugin Skyrim SE** sans confirmation dans xEdit.

### Sources techniques de contrôle

- [Bethesda Modding Library — plugin file structure](https://baddogskyrim.github.io/BethesdaLibrary/file-formats/plugins/)
- [esp-parser — TES4 record](https://esp-parser.readthedocs.io/en/latest/api/records/TES4.html)
- [Nexus — format d'en-tête HEDR Skyrim SE](https://www.nexusmods.com/skyrimspecialedition/articles/9691)

## À compléter

- Matrice détaillée par **record parent + sous-record** : `QUST`, `BOOK`, `MESG`, `ACTI`, `MGEF`, `SPEL`, `PERK`, etc.
- Comportement réel des filtres et verrous de la version installée de xTranslator.
- Règles spécialisées pour les noms de lieux, les livres, les rangs, les factions, les dialogues et les MCM.
- Dictionnaire Skyrim FR (terminologie Bethesda et termes propres aux mods), avec sources et exceptions.
- Exemples vérifiés dans NEFARAM ; ne pas confondre les exemples fictifs ci-dessus avec des données réelles.

**Principe :** *une chaîne technique douteuse vaut mieux intacte qu'un script cassé en français.*
