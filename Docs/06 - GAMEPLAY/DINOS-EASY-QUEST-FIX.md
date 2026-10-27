# Dino's Easy Quest Fix

## Statut

**Installé, retenu et validé en jeu** sur NEFARAM-Rhiven 17.3.8.

## Rôle

Dino's Easy Quest Fix fournit un MCM d'assistance et de diagnostic pour les quêtes actives. Il affiche notamment la quête, le stage courant, le texte associé, l'objectif actif et le prochain stage disponible, avec une commande permettant d'avancer au stage suivant.

Le mod ne remplace pas une analyse complète avec `sqs`, `sqv`, xEdit ou Papyrus lorsqu'une quête est réellement cassée.

## Intégration observée

- Prérequis déjà présents dans la baseline : SKSE64, Address Library et SkyUI.
- Installation dans `43 - Added Mods SFW`, sans conflit de fichiers MO2 observé.
- Plugin `DinosEasyQuestFix.esp` actif et flaggé ESL.
- L'archive contient les sources Papyrus ainsi que les sources du composant SKSE/native.
- Le MCM a correctement listé les quêtes actives et leurs informations de stage pendant le test en jeu.

## Règle d'usage

Créer une sauvegarde manuelle avant tout avancement forcé. N'utiliser `Advance to next stage` qu'après identification du blocage, car sauter un stage peut éviter des récompenses, scripts ou branches nécessaires.
