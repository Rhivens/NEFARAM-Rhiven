# Zaki Tattoos General — RTC / No Overlap (11/10/2026)

**Instance :** NEFARAM-Rhiven 17.3.7, MO2 `ELEANOR Stable`. **Statut :** installé, audit JSON statique ; test en jeu à faire.

## Installation observée
- `Zaki Tattoos General Pack SE - Rhiven` : 1.1.1, option **Full Pack** (841 entrées), textures hybrides **4K corps/pieds et 2K mains/visage**.
- Pas de plugin RaceMenu optionnel, ni extension 8K, ni Zaki Beast.
- `Zaki RTC Settings - Rhiven` placé après le pack ; preset `SKSE/Plugins/RapeTattoos/rTatsSettingsTemplate.json`. Il s'agit du JSON Rhiven corrigé avec la propriété `Group` (majuscule), malgré le nom d'origine conservé.
- `Rape Tats Continued 2.0.3 QoL Extension - Rhiven` chargé après RTC pour la fusion des fichiers JSON.

## Audit
- 841 clés de configuration Zaki General dans le preset Rhiven ; références complètes de textures `.dds` et affectations `Group`.
- `No Overlap for Rape Tattoo` est un **preset JSON** et non une extension de scripts. Version *Random*, dédiée au thème agressions et limitant logiquement les superpositions ; la configuration « Zaki Tattoos General » contient **528** clés Zaki (aucune clé étrangère). Les mêmes 528 figurent dans le `settings.json` principal No Overlap, accompagné de 254 clés Sexy Supplemental.
- Par comparaison avec le preset Zaki de 841 clés : **313 non couvertes** et environ **137 réaffectations substantielles de groupe** (161 différences si l'on compte la casse). No Overlap n'est **pas installé tel quel**, pour ne pas introduire un `settings.json` principal ou écraser une sélection déjà plus complète.
- Ne pas assimiler groupes `misc`, joues, poitrine et bras : les modifications No Overlap ne sont pas toutes vérifiées géométriquement. Exemple à contrôler : `Whore - RA.dds` classé `left arm` dans No Overlap.
- Le preset Zaki n'est **pas modifié directement** par les règles d'Eleanor.

## Contrôles restants
- [ ] Vérifier correspondance stricte des 841 clés avec le catalogue SlaveTats et les textures réellement installées.
- [ ] Tester `Test / Reload configs` dans le MCM RTC QoL ; consulter journaux.
- [ ] Vérifier en jeu les priorités des presets et les groupes inter-packs.
- [ ] Tester placements sur visage/corps, persistance des overlays et Fade Tattoos.

Voir [guide général](./README.md) et [preset Eleanor](./ELEANOR-RTC-SETTINGS.md).
