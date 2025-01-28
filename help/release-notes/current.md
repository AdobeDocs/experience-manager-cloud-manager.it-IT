---
title: Note sulla versione 2025.1.0 di Cloud Manager
description: Ulteriori informazioni sulla versione 2025.1.0 di Cloud Manager su Adobe Managed Services.
feature: Release Information
exlid: 669b1f2d8fc68526eb091e0f93f70ab93033d193
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: ca9a07354ff8316f531840a42d6ecdda5c072b9b
workflow-type: ht
source-wordcount: '196'
ht-degree: 100%

---

# Note sulla versione di Cloud Manager 2025.1.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Ulteriori informazioni sulla versione di [!UICONTROL Cloud Manager] 2025.1.0 su Adobe Managed Services.

>[!NOTE]
>
>Consulta le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

La data di pubblicazione della versione 2025.1.0 di [!UICONTROL Cloud Manager] è il 22 gennaio 2024.

La prossima pubblicazione è pianificata per il 13 febbraio 2025.

## Novità {#what-is-new}

**Regole di qualità del codice - Aggiornamento di SonarQube:** la qualità del codice di Cloud Manager inizierà a utilizzare SonarQube Server 9.9 con la versione 2025.2.0 di Cloud Manager, pianificata per il 13 febbraio 2025.

Per prepararti, le regole SonarQube aggiornate sono ora disponibili in [Regole per la qualità del codice](/help/using/code-quality-testing.md#code-quality-testing-step).

Puoi “verificare in anticipo” le nuove regole impostando la seguente variabile di testo della pipeline (vedi la schermata seguente):

`CM_BUILD_IMAGE_OVERRIDE` = `self-service-build:sonar-99-upgrade-java17or21`

Inoltre, imposta la variabile seguente per garantire che il passaggio di qualità del codice venga eseguito per lo stesso commit (normalmente ignorato per lo stesso `commitId`):

`CM_DISABLE_BUILD_REUSE` = `true`

![Pagina Configurazione variabili](/help/release-notes/assets/variables-config.png)

>[!NOTE]
>
>Adobe consiglia di creare una nuova pipeline CI/CD per la qualità del codice, configurata sullo stesso ramo della pipeline di produzione principale. Imposta le variabili appropriate *prima* della versione del 13 febbraio 2025 per convalidare che le nuove regole applicate non introducano blocchi.

<!-- ## Early adoption program {#early-adoption}

Be a part of Cloud Manager's early adoption program and have a chance to test upcoming features. -->


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
