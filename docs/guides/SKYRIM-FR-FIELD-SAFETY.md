# Skyrim SE / NEFARAM — Référentiel de sécurité des champs pour la traduction FR

> **État : brouillon évolutif (v0.2)** — à enrichir et vérifier sur des enregistrements réels avec xTranslator / xEdit avant toute automatisation.
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

## À compléter

- Matrice détaillée par **record parent + sous-record** : `QUST`, `BOOK`, `MESG`, `ACTI`, `MGEF`, `SPEL`, `PERK`, etc.
- Comportement réel des filtres et verrous de la version installée de xTranslator.
- Règles spécialisées pour les noms de lieux, les livres, les rangs, les factions, les dialogues et les MCM.
- Dictionnaire Skyrim FR (terminologie Bethesda et termes propres aux mods), avec sources et exceptions.
- Exemples vérifiés dans NEFARAM ; ne pas confondre les exemples fictifs ci-dessus avec des données réelles.

**Principe :** *une chaîne technique douteuse vaut mieux intacte qu'un script cassé en français.*
