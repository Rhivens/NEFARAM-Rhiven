# Item Vault - Plugin Explorer

## Statut

**Installé, retenu et validé en jeu** sur NEFARAM-Rhiven 17.3.8.

## Rôle

Item Vault sert d'explorateur complet de la load order : navigation et recherche par items ou plugins, accès aux NPC et sorts, actions directes, téléportation, inventaires, kits et aperçu 3D.

## Intégration observée

- Installation sans ESP et sans conflit de fichiers MO2 observé ; intégration composée de SKSE et d'assets.
- Ouverture immédiate sur la load order Rhiven, avec environ **46 831 items répartis sur 466 plugins** lors du test documenté.
- Recherche globale et par plugin validée avec `Phoenix Katana - Eleanor`, retrouvé via `Rhiven_Eleanor_Katana.esp`.

## Place dans l'outillage

- **Item Vault** est l'explorateur complet retenu.
- **AddItemMenu** reste actif comme outil rapide et familier.
- `Modex 3.0.2 - Rhiven` et son patch ont été désactivés pendant la comparaison sans créer de master manquant. Ils restent installés temporairement comme retour arrière jusqu'à confirmation de leur inutilité pendant les premières heures de la partie définitive.
