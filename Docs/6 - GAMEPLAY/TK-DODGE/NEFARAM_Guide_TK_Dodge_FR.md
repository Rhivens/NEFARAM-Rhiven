# NEFARAM — Guide TK Dodge

> Version Markdown du guide Word original : [NEFARAM_Guide_TK_Dodge_FR.docx](./NEFARAM_Guide_TK_Dodge_FR.docx)

## Ajouter TK Dodge à NEFARAM

*Guide FR nettoyé et réorganisé à partir du tutoriel Discord de Thoshy.*

**Version source :** mise à jour pour NEFARAM 17 (05/08/2026). Les échanges Discord ont été retirés du corps du guide ; seuls les détails utiles à l’installation, au réglage et au dépannage ont été conservés.

## 1. Objectif

Cette procédure ajoute une mécanique d’esquive à NEFARAM à l’aide de TK Dodge.

Deux packs d’animations optionnels sont proposés :

- Dynamic Dodge Animation
- Smooth Slip Dodge Animation

Ils sont incompatibles entre eux ; vous pouvez aussi ne choisir aucun des deux et conserver les animations par défaut de TK Dodge.

Le guide source indique une préférence légère pour **Dynamic Dodge Animation**, tandis que **Smooth Slip Dodge Animation** est apprécié pour son esquive glissée vers l’avant.

## 2. Point important concernant les fichiers INI

TK Dodge RE et TK Dodge NG contiennent tous les deux un fichier `TK Dodge RE.ini`.

Comme **TK Dodge NG doit être placé sous TK Dodge RE dans MO2**, le fichier INI contenu dans TK Dodge NG écrase celui de TK Dodge RE.

Il suffit donc de modifier le `TK Dodge RE.ini` situé dans le mod **TK Dodge NG**.

## 3. Organisation conseillée dans MO2

Pour garder la liste lisible, vous pouvez créer un séparateur dédié nommé par exemple :

- Dodge
- TK Dodge

Cette étape est optionnelle, mais pratique pour regrouper tous les composants liés à l’esquive.

## 4. Mods à installer

### 4.1 IFrame Generator RE AE Support

https://www.nexusmods.com/skyrimspecialedition/mods/82737

Framework utilisé par d’autres mods pour générer des frames d’invincibilité pendant certaines animations. Dans le contexte de TK Dodge, il permet à l’esquive de bénéficier d’une très courte fenêtre d’invulnérabilité.

### 4.2 TK Dodge For RE

https://www.nexusmods.com/skyrimspecialedition/mods/15309

Dans la section **Optional Files**, sélectionner uniquement :

- TK Dodge For RE

### 4.3 TK Dodge RE v0.55-rc3

https://www.nexusmods.com/skyrimspecialedition/mods/56956

Dans le FOMOD, sélectionner uniquement :

- Behavior edits for dodge only
- TK dodge standalone
- TK dodge standalone - Enable Sheathed Dodge
- TK dodge standalone - Cancel concentration spell when dodging
- TK dodge standalone - Forward dodge scurry fix

### 4.4 TK Dodge First Person 8 Ways Dodge

https://www.nexusmods.com/skyrimspecialedition/mods/56956

### 4.5 TK Dodge Animation Pandora Patch

https://www.nexusmods.com/skyrimspecialedition/mods/111788

### 4.6 TK Dodge NG

https://www.nexusmods.com/skyrimspecialedition/mods/115408

TK Dodge NG doit être placé **sous TK Dodge RE** dans le panneau gauche de MO2 afin que ses fichiers prennent la priorité.

## 5. Réglage Step Dodge (optionnel)

Si vous préférez une esquive par pas / déplacement latéral plutôt qu’une roulade, modifiez le fichier INI de TK Dodge NG.

1. Dans MO2, double-cliquez sur **TK Dodge NG**.
2. Vérifiez qu’il est placé sous TK Dodge RE.
3. Ouvrez l’onglet **INI Files**.
4. Modifiez le fichier `TK Dodge RE.ini` contenu dans TK Dodge NG :

   ```ini
   StepDodge = true
   ```

5. Enregistrez avec **Ctrl+S**.

Le `TK Dodge RE.ini` du mod TK Dodge RE peut rester à sa valeur précédente : il n’est pas lu lorsque la version contenue dans TK Dodge NG l’écrase.

## 6. Animations d’esquive optionnelles

Choisir **Dynamic Dodge Animation OU Smooth Slip Dodge Animation, jamais les deux**.

Vous pouvez également ne choisir aucun pack et utiliser les animations par défaut de TK Dodge.

### 6.1 Option A — Dynamic Dodge Animation

https://www.nexusmods.com/skyrimspecialedition/mods/79598

Dans le FOMOD, sélectionner :

- TK Dodge RE 0.55 rc3
- Sway

### 6.2 Option B — Smooth Slip Dodge Animation

https://www.nexusmods.com/skyrimspecialedition/mods/63660

Télécharger la version :

- Smooth Slip Dodge I TDM 360 movement users

Pour obtenir le step dodge avec Smooth Slip Dodge Animation, le réglage `StepDodge = true` doit être appliqué dans le `TK Dodge RE.ini` situé dans TK Dodge NG, comme décrit plus haut.

## 7. Placement dans le panneau gauche MO2

Une fois tous les composants installés, sélectionner le séparateur TK Dodge (si vous en avez créé un) ainsi que les mods ajoutés, depuis **IFrame Generator RE AE Support** jusqu’au pack d’animations choisi.

Dans MO2 :

**Clic droit → Send to... → Separator... → Late Loaders**

Ces mods doivent se trouver **au-dessus de Pandora Output** ; c’est la raison du placement dans le bloc Late Loaders.

## 8. Régénération Pandora

Ouvrir Pandora puis vérifier que les deux options suivantes sont activées :

- TK Dodge RE / Ultimate Combat
- TK Dodge Standalone

Lancer ensuite la génération avec Pandora.

Si tout est correctement installé, TK Dodge est prêt à être testé en jeu.

## 9. Dépannage — problèmes relevés dans les échanges Discord

### 9.1 T-pose ou esquive latérale cassée

Si le personnage passe en T-pose lors des esquives latérales, ou si l’animation semble se jouer sur place :

- Vérifier que Pandora Output est placé sous TK Dodge et TK Dodge For RE.
- Vérifier que Pandora est à jour.
- Vérifier les chemins configurés dans Pandora.
- Vérifier que **TK Dodge RE / Ultimate Combat** est coché dans Pandora.
- Vérifier surtout que **TK Dodge Standalone** est également coché.
- Si nécessaire, réinstaller TK Dodge RE et reprendre les options FOMOD du guide.

Un cas rapporté a été résolu simplement en réinstallant TK Dodge RE : l’option TK Dodge Standalone avait été décochée par erreur.

### 9.2 Step Dodge ne fonctionne pas et le personnage roule encore

- Vérifier que `StepDodge = true` a été modifié dans le fichier INI de TK Dodge NG, pas seulement dans celui de TK Dodge RE.
- Le fichier INI de TK Dodge RE est écrasé par celui de TK Dodge NG ; sa valeur n’a donc pas d’effet dans cette configuration.

### 9.3 Pas de MCM / touche d’esquive inactive

Les échanges montrent qu’une installation incomplète de TK Dodge NG peut conduire à une configuration non fonctionnelle.

Vérifiez en priorité que TK Dodge NG est bien installé et actif, puis reprenez l’ordre et la génération Pandora.

### 9.4 Esquive et double-cast Destruction

Le guide source indique qu’un test avec **Flames** dans les deux mains permettait l’esquive dans toutes les directions.

Un autre utilisateur ayant constaté un blocage a ensuite suspecté un problème de clavier / changement de langue Windows.

Aucune cause logicielle TK Dodge n’a été confirmée dans l’échange.

## 10. Mise à jour future de NEFARAM

Pour éviter que Wabbajack supprime les mods TK Dodge lors d’une mise à jour de la modlist, les échanges recommandent d’utiliser le préfixe **[NoDelete]** sur les éléments TK Dodge afin de les conserver.

Cela évite leur suppression, mais ne dispense pas de refaire les vérifications de placement des plugins/mods et, si nécessaire, de relancer Pandora après une mise à jour de NEFARAM.

## 11. Checklist d’installation

- [ ] IFrame Generator RE AE Support installé.
- [ ] TK Dodge For RE installé depuis Optional Files.
- [ ] TK Dodge RE v0.55-rc3 installé avec uniquement les options FOMOD recommandées.
- [ ] TK Dodge First Person 8 Ways Dodge installé.
- [ ] TK Dodge Animation Pandora Patch installé.
- [ ] TK Dodge NG installé sous TK Dodge RE dans MO2.
- [ ] `StepDodge = true` réglé dans le `TK Dodge RE.ini` de TK Dodge NG si le step dodge est souhaité.
- [ ] Un seul pack d’animations optionnel installé : Dynamic Dodge Animation OU Smooth Slip Dodge Animation.
- [ ] Le bloc TK Dodge est placé dans Late Loaders et reste au-dessus de Pandora Output.
- [ ] Pandora : TK Dodge RE / Ultimate Combat coché.
- [ ] Pandora : TK Dodge Standalone coché.
- [ ] Pandora régénéré sans erreur bloquante.
- [ ] Esquive testée en jeu dans plusieurs directions.
- [ ] Si une future mise à jour Wabbajack est prévue, envisager le préfixe [NoDelete] et refaire les vérifications après mise à jour.

## 12. Ordre logique résumé

1. IFrame Generator RE AE Support
2. TK Dodge For RE
3. TK Dodge RE v0.55-rc3
4. TK Dodge First Person 8 Ways Dodge
5. TK Dodge Animation Pandora Patch
6. TK Dodge NG
7. Dynamic Dodge Animation **OU** Smooth Slip Dodge Animation *(optionnel)*
8. Pandora Output *(en dessous du bloc TK Dodge)*
