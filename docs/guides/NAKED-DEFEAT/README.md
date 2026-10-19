# Naked Defeat — Documentation & projet d’intégration

Ce dossier centralise la documentation et le chantier d’intégration de **Naked Defeat AE/SE 6.50 FULL** dans **NEFARAM-Rhiven**.

L’objectif n’est pas d’ajouter Naked Defeat « par-dessus » le système actuel, mais d’étudier un remplacement propre de **Practical Defeat** sur une **nouvelle partie**, avec **Acheron** conservé comme gestionnaire central de la défaite et **Yamete Kudasai** maintenu lorsque son comportement est préférable.

## Fichiers

- [Naked-Defeat-AE-FR.md](Naked-Defeat-AE-FR.md) — documentation française de référence, optimisée pour lecture rapide et recherche.
- [Naked-Defeat-AE-FR.docx](Naked-Defeat-AE-FR.docx) — version Word illustrée / lisible humain.
- [INTEGRATION-PROTOCOL.md](INTEGRATION-PROTOCOL.md) — architecture cible, étapes d’intégration, protocole de test et critères de validation.

## Statut

**Étude / préparation uniquement.**

Aucune intégration définitive ne doit être réalisée avant :

1. la migration et la stabilisation de **NEFARAM 17.3.8** ;
2. l’audit du panneau gauche et du panneau droit MO2 du profil final ;
3. l’identification précise des composants et patches dépendant de Practical Defeat ;
4. la création d’un profil MO2 de test dédié.

## Principe directeur

> **Acheron décide de la défaite. Naked Defeat reçoit une conséquence. Yamete Kudasai reste disponible pour les catégories où il apporte une meilleure couverture.**

Le point central à surveiller sera donc la **distribution des outcomes Acheron** et leurs poids, pas seulement les options internes de Naked Defeat.
