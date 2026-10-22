# LL Integration 0.8 — Technical Review & Adoption Protocol

> **Status:** tool candidate / not part of Skyrim runtime  
> **Target workflow:** NEFARAM-Rhiven 17.3.8 maintenance under MO2  
> **Documented version:** **0.8 beta**  
> **Source:** user-supplied LoversLab description  
> **Category:** external workflow / browser ↔ native bridge ↔ MO2/Vortex integration  
> **Scope:** usefulness assessment, security/privacy review, MO2 safety, download-path validation, metadata workflow, update checks, voice-pack matching and rollback

---

## 1. Purpose

**LL Integration 0.8** is not a Skyrim gameplay mod.

It is a local integration tool intended to connect:

1. a supported web browser;
2. a local native bridge/application;
3. Mod Organizer 2 or Vortex.

Its stated objective is to capture supported mod archive downloads, preserve source metadata locally, and make LoversLab / external-source mods easier to:

- identify;
- relink to their source page;
- manage;
- update;
- import into the mod manager.

For NEFARAM-Rhiven, the primary interest is therefore **maintenance of the large LoversLab-heavy MO2 installation**, not in-game functionality.

---

## 2. Beta status

The supplied description explicitly labels version 0.8 as a **beta release**.

The author states that:

- the tool is primarily built for their own workflow;
- it is shared because it may help others;
- bugs will be tracked / fixed when possible;
- individual support for every environment is not guaranteed.

### Rhiven implication

Treat LL Integration as **experimental infrastructure**, even if its feature set is attractive.

Do not deploy it directly into the only working MO2 configuration without first testing:

- browser extension behavior;
- native bridge;
- active-instance detection;
- downloads path;
- MO2 plugin integration;
- metadata writes;
- update checks.

---

## 3. Game compatibility

The tool is listed under Skyrim SE because that is where it was developed and tested first, but the supplied description states that the tool itself is **not Skyrim-specific**.

### MO2

The author expects MO2 support to work with other games when:

- MO2 downloads are available;
- MO2 mod metadata is available.

Confirmed by the author so far:

- Skyrim Special Edition;
- Oblivion.

### Vortex

Vortex support is newer and more dependent on the game's staging/deployment model.

For NEFARAM-Rhiven, **MO2 is the only relevant path**.

Vortex functionality should therefore be ignored during first adoption.

---

## 4. Browser integration

The supplied description lists support for:

- Firefox;
- Opera / Chromium.

This is especially relevant to the current Rhiven workflow because both Firefox and Opera are used locally.

Documented browser-side features include:

- capturing LoversLab archive downloads;
- exporting LoversLab cookies locally for MO2 update checks;
- capturing archives from manually armed external pages;
- optional always-on-top floating capture controls;
- follow mode that can retarget capture when browsing between active tabs;
- Dwemer Mods download capture;
- possible future additional sources.

### Rhiven concern

Cookie export is a sensitive capability.

Before adoption, verify exactly:

- where exported cookies are stored;
- whether they are plaintext;
- which domains/cookies are exported;
- which local process can access them;
- whether the browser extension requests broader permissions than required;
- how cookies are deleted / refreshed;
- whether update checking still works after manual cookie revocation.

---

## 5. MO2 integration

The documented MO2 integration adds:

- **Tools > LL Integration**;
- source-page links for installed mods;
- a right-click command to open linked source pages;
- source metadata stored inside MO2 `meta.ini`;
- update checks for linked LoversLab mods;
- installed-mod-folder opening;
- editing / purging bad source links;
- Voice Finder workflows.

### Important design advantage

The source metadata is stored in **MO2 `meta.ini`**, which the author says avoids creating mod-file conflicts.

For Rhiven this is desirable because it keeps source tracking outside the game-data conflict graph.

### Required test

Confirm that:

- only expected `meta.ini` fields change;
- no mod contents are rewritten;
- no MO2 separator/order information changes;
- no plugin/load-order changes occur;
- source links survive MO2 restart.

---

## 6. Download handling

The supplied description states that LL Integration can:

- copy supported browser downloads to the configured MO2 downloads folder;
- create local sidecar metadata;
- handle renamed archives using metadata / fingerprint matching;
- capture manually armed external downloads;
- support Dwemer Mods with local metadata.

Supported archive types:

- `.7z`;
- `.zip`;
- `.rar`.

### Rhiven primary risk

The active MO2 instance / downloads folder must be identified correctly.

A tool that writes a valid LoversLab archive into the **wrong MO2 instance** is not catastrophic, but it creates confusing maintenance problems.

Therefore first tests must use:

- a harmless small archive;
- a temporary download folder if possible;
- explicit verification of the active MO2 instance;
- explicit verification of the resulting archive path;
- explicit verification of sidecar metadata.

---

## 7. Manual source links

LL Integration can create manual links for:

- already installed mods;
- multipart archives;
- external downloads;
- old mods;
- manually installed mods;
- renamed archives.

External/manual links are documented as fixed/manual links and are not automatically fetched for updates.

### Rhiven usefulness

This is particularly relevant because the Rhiven build contains many:

- LoversLab files with inconsistent archive names;
- older archives;
- voice packs;
- external downloads;
- manually renamed files;
- mod variants / patches.

Manual links could help normalize provenance without renaming or reorganizing the actual mod folders.

---

## 8. Update manager

The supplied description documents an update manager able to:

- check linked LoversLab mods for updates;
- download update archives into the active MO2 downloads folder;
- detect already-downloaded updates;
- assist the MO2 install / replace process.

The author explicitly states that update installation remains **user-controlled** and does not silently replace mods.

Available modes:

- Manual install;
- Download only;
- Assisted install;
- Skip updates.

### Rhiven policy

For the first adoption phase:

- use **Download only** or **Manual install**;
- do **not** use Assisted install until the workflow has been validated;
- never let an update replace an existing Rhiven-customized mod without manual version / file / translation audit.

This is especially important for:

- translated mods;
- patched scripts;
- customized INIs;
- mods with Rhiven-specific overrides;
- mods that were manually migrated during 17.3.7 → 17.3.8.

---

## 9. File-pattern matching

The tool documents improved matching for:

- non-standard archive names;
- renamed archives;
- version markers such as:
  - `{version}`;
  - `{v}`;
  - `<version>`;
  - `<v>`.

It also includes a Pattern Help function.

### Rhiven usefulness

This may be valuable for LoversLab archives whose filenames are inconsistent or manually renamed.

Test with:

1. untouched original archive;
2. manually renamed archive;
3. archive containing version in unusual syntax;
4. multipart archive;
5. voice-pack archive.

Record any false matches.

---

## 10. Active MO2 instance support

The tool claims improved tracking of:

- the active MO2 instance;
- the active MO2 downloads folder;
- shared integration paths between the plugin and native app.

This is one of the most important features for the Rhiven environment.

### Mandatory validation

Before adoption:

- [ ] start only the NEFARAM MO2 instance;
- [ ] confirm LL Integration reports the expected MO2 executable;
- [ ] confirm the expected downloads path;
- [ ] download a harmless test archive;
- [ ] confirm it lands in the intended NEFARAM downloads folder;
- [ ] close MO2;
- [ ] reopen and verify persistence;
- [ ] if another MO2 instance exists, deliberately switch and verify the integration follows the active instance correctly.

No real update workflow should be enabled before this passes.

---

## 11. Voice Finder

The Voice Finder can:

- scan LoversLab-linked base mods for missing voice packs;
- detect likely DBVO / DVO / IDTV / Voice Pack / VoiceFiles-style mods;
- compare base-mod names against voice packs using scoring;
- fetch user-provided LoversLab voice-source pages;
- browse available voice downloads;
- manually choose candidates;
- manually bind voice packs to base mods;
- override Base Mod / Voice Pack classification;
- save manual matches, false matches, ignored mods and classification overrides;
- filter/sort installed voice-like mods.

### Rhiven usefulness

This is potentially one of the most valuable features because the current build contains many:

- base LoversLab mods;
- separate voice packs;
- generic voice packs;
- manually named voice mods.

### Required caution

Automatic name scoring can be wrong.

Voice Finder should be treated as **discovery assistance**, not authoritative matching.

Never install/replace a voice pack solely because the score says it matches.

---

## 12. Installation paths — MO2 workflow

The supplied description gives the following normal MO2 setup:

1. extract the installer archive;
2. run `LLIntegrationInstaller.exe`;
3. select `ModOrganizer.exe`;
4. select the MO2 downloads folder;
5. restart MO2.

There is also an experimental installer that adds a direct toolbar button.

### Rhiven choice

Use the **normal installer only**.

Do **not** use the experimental toolbar installer initially.

The author explicitly notes that the toolbar hook sits outside the official MO2 plugin API and could break after MO2 updates.

The supported path is:

`Tools > LL Integration`

---

## 13. Firefox setup

Documented procedure:

1. extract the Firefox extension archive;
2. install the signed `.xpi`;
3. restart Firefox;
4. log into LoversLab;
5. open LL Integration popup;
6. export cookies.

### Rhiven preference

Firefox is the preferred browser for first testing because:

- the extension is documented as signed;
- Opera approval is still pending;
- Opera requires manual unpacked-extension loading.

Do not test both browsers at once.

Validate Firefox first.

---

## 14. Opera / Chromium setup

The supplied description states that Opera-store approval is pending.

Current setup requires:

- extracting the extension to a permanent folder;
- enabling Developer Mode;
- using **Load unpacked**;
- restarting Opera;
- logging into LoversLab;
- exporting cookies.

### Rhiven decision

**Do not use the Opera extension during first adoption.**

Reason:

- unpacked developer-mode extensions create additional maintenance / trust surface;
- Firefox already provides a supported signed-extension path;
- there is no need to validate two browser channels simultaneously.

Opera can be tested later only if Firefox integration is unsatisfactory.

---

## 15. External downloads

LL Integration can manually arm capture on external pages such as:

- Patreon;
- SubscribeStar;
- Mega;
- Google Drive;
- similar pages.

Workflow:

1. open source page;
2. activate archive capture;
3. download archive;
4. cancel capture afterward.

These links are stored as manual links.

### Rhiven rule

Use this only when the source relationship is unambiguous.

For pages containing multiple unrelated archives, verify the captured archive/source association manually before accepting metadata.

---

## 16. Privacy claims

The supplied description claims that:

- data is stored locally;
- no analytics are used;
- no telemetry is used;
- no cloud sync is used;
- no remote account is required;
- source code is open source.

These are positive design claims, but they should still be verified from the repository / privacy policy before adoption because the tool handles:

- browser extension permissions;
- local native messaging / bridge;
- LoversLab cookies;
- filesystem writes;
- MO2 metadata;
- downloads.

### Required privacy audit

Before installing:

- [ ] read the published privacy policy;
- [ ] inspect browser extension permissions;
- [ ] inspect native messaging host configuration;
- [ ] identify cookie storage location;
- [ ] identify metadata / sidecar storage locations;
- [ ] verify no unexpected external endpoints;
- [ ] confirm update checks only contact intended source sites;
- [ ] confirm logs do not expose session cookies.

---

## 17. Security / trust audit

Because LL Integration spans browser + native executable + MO2 plugin, it has a larger trust surface than a normal MO2 Python plugin.

Before adoption:

- [ ] verify repository ownership / release source;
- [ ] download only from the official source;
- [ ] compare release archive with repository / release documentation where possible;
- [ ] scan executables / extension package with local security tools;
- [ ] inspect browser permissions;
- [ ] inspect MO2 plugin files;
- [ ] inspect native bridge registration;
- [ ] check whether the installer modifies PATH, registry or browser native-messaging configuration;
- [ ] document uninstall procedure;
- [ ] prepare a backup of MO2 config / plugin folder before installation.

---

## 18. First test protocol

Create a controlled test using one harmless LoversLab mod/archive.

### Stage A — browser capture

- [ ] click a normal LoversLab archive download;
- [ ] confirm browser download completes;
- [ ] confirm LL Integration notices it;
- [ ] verify archive is copied to the expected MO2 downloads folder;
- [ ] verify no duplicate unexpected copy remains if that matters to storage policy.

### Stage B — metadata

- [ ] inspect sidecar metadata;
- [ ] inspect MO2 `meta.ini`;
- [ ] verify source URL;
- [ ] verify mod/file title;
- [ ] verify version detection;
- [ ] verify renamed-archive handling.

### Stage C — MO2

- [ ] open `Tools > LL Integration`;
- [ ] verify linked source;
- [ ] test right-click “open source page”;
- [ ] edit a test link;
- [ ] purge a deliberately wrong test link;
- [ ] restart MO2 and confirm persistence.

### Stage D — update check

- [ ] perform update check without auto-install;
- [ ] verify detected version;
- [ ] use Download Only if an update exists;
- [ ] confirm no installed mod is changed.

---

## 19. Already-installed mod linking

The supplied description recommends re-downloading an archive after LL Integration is installed, then reinstalling/replacing the mod so metadata can attach automatically.

### Rhiven warning

Do **not** mass-reinstall the current LoversLab stack merely to populate metadata.

That would create unnecessary risk.

Preferred strategy:

1. use manual links for important existing mods;
2. attach automatic metadata naturally when a future update is actually downloaded;
3. progressively improve coverage over time;
4. never disturb a stable installed mod solely for provenance metadata.

---

## 20. Update workflow policy for Rhiven

If LL Integration is adopted, use this policy:

### Safe default

- update detection: **enabled**;
- automatic replacement: **never**;
- update mode: **Download only** or **Manual install**;
- install decision: manual, one mod at a time.

### Before any update

Always check:

- current Rhiven version;
- translation;
- custom patch;
- scripts;
- MCM changes;
- FOMOD differences;
- plugin changes;
- compatibility with NEFARAM 17.3.8;
- whether the update is save-compatible.

LL Integration may tell us **that** an update exists.

It does not decide whether Rhiven **should install it**.

---

## 21. Failure / rollback procedure

If the tool behaves incorrectly:

1. stop browser capture;
2. close MO2;
3. disable/uninstall the browser extension;
4. disable/remove the MO2 plugin;
5. stop/remove the native bridge;
6. restore backed-up MO2 configuration if needed;
7. remove erroneous sidecar metadata only after identifying its location;
8. verify the MO2 downloads folder manually;
9. verify no mod contents were modified;
10. launch MO2 without LL Integration and confirm the baseline remains intact.

No Skyrim save cleaning is relevant because this tool is outside the runtime.

---

## 22. Adoption criteria

LL Integration 0.8 can be retained in the Rhiven workflow if:

- [ ] official repository / release source is verified;
- [ ] privacy / extension permissions are acceptable;
- [ ] Firefox capture works reliably;
- [ ] cookies are stored in an acceptable local form/location;
- [ ] correct MO2 instance is always detected;
- [ ] downloads always land in the intended folder;
- [ ] `meta.ini` changes are limited to intended source metadata;
- [ ] no mod-data conflict is introduced;
- [ ] manual source linking works;
- [ ] renamed-archive matching is reliable enough;
- [ ] update checks do not modify installed mods;
- [ ] Voice Finder is useful without producing excessive false matches;
- [ ] uninstall/rollback is straightforward;
- [ ] no unexpected network / telemetry behavior is observed.

---

## 23. Current decision

**VERY INTERESTING TOOL CANDIDATE — test in isolation before adoption.**

### Strong advantages for Rhiven

- LoversLab-heavy modlist;
- source links currently require manual memory/documentation;
- many separate voice packs;
- inconsistent / renamed archives;
- manual update audits;
- multiple external-source mods;
- MO2-centric workflow;
- local metadata rather than game-data files;
- update installation remains user-controlled.

### Main concerns

1. **beta status**;
2. browser-extension permissions;
3. handling / storage of LoversLab cookies;
4. native bridge trust surface;
5. correct MO2-instance detection;
6. risk of writing downloads to the wrong folder;
7. false source / voice-pack matching;
8. assisted-install workflow should remain disabled until fully understood.

### Recommended first deployment

- Firefox only;
- normal MO2 installer;
- no experimental toolbar;
- one harmless test archive;
- update mode = **Download only**;
- no bulk relinking;
- no mass reinstall;
- no automatic replacement.

**Roadmap verdict:** **TOOL CANDIDATE — HIGH POTENTIAL VALUE / MEDIUM OPERATIONAL RISK / NO SKYRIM RUNTIME RISK.**
