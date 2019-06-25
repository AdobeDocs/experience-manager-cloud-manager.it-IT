---
title: Note sulla versione 2019.6.0
seo-title: Note sulla versione di AEM Cloud Manager per 2019.6.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.6.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni sulla versione 2019.6.0 di AEM Cloud Manager.
translation-type: tm+mt
source-git-commit: 7373f674b9804c83fad0871a74ef85280ea24962

---

# Release Notes for 2019.6.0 {#release-notes-for}

The [!UICONTROL Cloud Manager] 2019.6.0 Release adds new code quality rules and new Product Update wizard. Per ulteriori dettagli, seguite le sezioni riportate di seguito.

## Release Date {#release-date}

The Release Date for [!UICONTROL Cloud Manager] Version 2019.6.0 is June 20, 2019 .

## Novità {#whats-new}

* Procedura guidata Nuovo aggiornamento del prodotto per aiutare i clienti a eseguire correttamente un aggiornamento AEM. Refer to [Product Update Wizard](overview-productupdate-wizard.md) to learn more.
* Regole di qualità del codice che consentono di esaminare le strutture dei contenuti. Refer to [Custom Code Quality Rules](custom-code-quality-rules.md) for more information.
* La dimensione massima di un push git è stata portata a 1 GB.

## Bug Fixes {#bug-fixes}

* In alcuni casi, impossibile avviare pipeline a causa di un errore precedente.

## Problemi noti {#known-issues}

* Il download CSV di qualità del codice non viene sempre ordinato in base alla gravità.
* False positives may be reported by the *ConfigAndInstallShouldOnlyContainOsgiNodes* rule if OSGi configurations are placed in a nested folder under a *config* folder.
