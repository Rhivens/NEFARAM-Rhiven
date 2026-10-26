# Naked Defeat — Documentation & projet d’intégration

Ce dossier centralise la documentation et le chantier d’intégration de **Naked Defeat AE/SE 6.50 FULL** dans **NEFARAM-Rhiven 17.3.8**.

L’objectif retenu est maintenant un remplacement propre de l’ancien couple **Practical Defeat Reanimated / Yamete Kudasai** pour les conséquences Acheron, avec l’architecture suivante :

```text
Acheron
→ Acheron - Naked Defeat Bridge
→ Naked Defeat 6.50
→ Naked Defeat - Rhiven Fix
```

## Téléchargement

- [Naked Defeat - Rhiven Fix.zip](Naked%20Defeat%20-%20Rhiven%20Fix.zip) — petit patch correctif Rhiven pour Naked Defeat 6.50.

Le ZIP contient le dossier MO2 `Naked Defeat - Rhiven Fix` avec :
- `Naked Defeat - Rhiven Fix.esp`
- `meta.ini`

Le plugin ne doit pas être fusionné dans `Naked Defeat.esp`. Il reste volontairement séparé pour conserver un correctif réversible et facile à auditer.

## Fichiers

- [Naked-Defeat-AE-FR.md](Naked-Defeat-AE-FR.md) — documentation française de référence.
- [Naked-Defeat-AE-FR.docx](Naked-Defeat-AE-FR.docx) — version Word illustrée / lisible humain.
- [INTEGRATION-PROTOCOL.md](INTEGRATION-PROTOCOL.md) — architecture cible, étapes d’intégration, protocole de test et critères de validation.
- [Guide de migration NEFARAM 17.3.8](../NAKED-DEFEAT-INTEGRATION.md) — procédure actuelle complète : Practical Defeat / Yamete Kudasai → Naked Defeat 6.50.

## Statut

**Intégration techniquement validée — tests in-game en cours.**

Déjà validé :
- audit xEdit du plugin principal ;
- `Naked Defeat - Rhiven Fix.esp` : **0 erreur / 5 records** ;
- Acheron Bridge : **0 erreur / 3 records** ;
- audit OAR Bowed / Crawl ;
- audit des chevauchements Yamete Kudasai / Practical Defeat ;
- ordre de plugins ;
- identification du problème Civilian Rape.

À confirmer en jeu :
- défaites répétées ;
- humanoïdes / créatures / follower ;
- sortie propre du bleedout Acheron ;
- retour des contrôles et libération des assaillants ;
- stabilité save / exit / reload.

## Réglage obligatoire actuel

Dans le MCM Naked Defeat :

> **`IndecencyRapeProb = 0`**

La branche Civilian Rape de Naked Defeat 6.50 référence une quête absente. Ne pas tenter de la reconstruire artificiellement.

## Principe directeur

> **Acheron décide de la défaite. Naked Defeat gère la conséquence.**

Pour cette architecture, **Yamete Kudasai et Practical Defeat restent désactivés** pendant les tests afin d’éviter une distribution concurrente des conséquences Acheron.
