---
title: Note sulla versione 2024.12.0 di Cloud Manager
description: Scopri la versione di Cloud Manager Adobe 2024.12.0 su Managed Services.
feature: Release Information
exl-id: 811567af-66c9-4c1f-ae9e-60603b70ef80
source-git-commit: e266a4192e2a897f142a6c83ae5766483946320d
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 75%

---

# Note sulla versione per Cloud Manager Adobe 2024.12.0 su Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2024.12.0+Release -->

Scopri la versione di [!UICONTROL Cloud Manager] 2024.12.0 su Adobe Managed Services.

>[!NOTE]
>
>Consulta le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

La data di pubblicazione della versione 2024.12.0 di [!UICONTROL Cloud Manager] è il venerdì 5 dicembre 2024.

La prossima versione pianificata è il venerdì 23 gennaio 2025.

<!-- ## What's new {#what-is-new} -->

<!-- * The AEM Code Quality step now uses SonarQube 9.9 Server, replacing the older 7.4 version. This upgrade brings additional security, performance, and code quality checks, offering more comprehensive analysis and coverage for your projects. --> <!-- CMGR-45683 -->

## Programma per i primi utilizzatori {#early-adoption}

Partecipa al programma per i primi utilizzatori di Cloud Manger e concediti la possibilità di testare le prossime funzionalità.

### Bring Your Own Git: ora con supporto per GitLab e Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La funzionalità **Porta il tuo Git** è stata espansa per includere il supporto per archivi esterni, come GitLab e Bitbucket. Questo nuovo supporto si aggiunge a quello già esistente per archivi GitHub privati ed aziendali. Quando aggiungi questi nuovi archivi, puoi anche collegarli direttamente alle pipeline. Puoi inoltre ospitare questi archivi sia su piattaforme cloud pubbliche sia all’interno della tua infrastruttura o del tuo cloud privato. Questa integrazione elimina anche la necessità di sincronizzare continuamente il codice con l’archivio Adobe e offre la possibilità di convalidare le richieste pull prima di unirle in un ramo principale.

Le pipeline che utilizzano archivi esterni (esclusi quelli ospitati da GitHub) e il **Trigger di distribuzione** impostato su **Su modifiche Git** ora vengono avviate automaticamente.

Consulta [Aggiungere archivi esterni in Cloud Manager](/help/managing-code/external-repositories.md).

![Finestra di dialogo Aggiungi archivio](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Attualmente, i controlli di qualità predefiniti per il codice di richiesta pull sono esclusivi degli archivi ospitati in GitHub, ma è in preparazione un aggiornamento per estendere questa funzionalità anche ad altri fornitori Git.

Se ti interessa testare questa nuova funzione e condividere il tuo feedback, invia un’e-mail a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) dall’indirizzo e-mail associato al tuo Adobe ID. Se ti trovi in una struttura di archivio privata/pubblica o aziendale, assicurati di specificare la piattaforma Git che desideri utilizzare.


<!-- ## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
