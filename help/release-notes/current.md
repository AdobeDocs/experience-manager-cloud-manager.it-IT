---
title: Note sulla versione 2025.5.0 di Cloud Manager
description: Ulteriori informazioni sulla versione 2025.5.0 di Cloud Manager su Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 802844e15dc2b610e658e9fac4f0304f0ec878c6
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 96%

---

# Note sulla versione di Cloud Manager 2025.5.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Ulteriori informazioni sulla versione di [!UICONTROL Cloud Manager] 2025.5.0 su Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio della versione 2025.5.0 di [!UICONTROL Cloud Manager] è il venerdì 8 maggio 2025.

Nella versione di maggio di Cloud Manager non sono presenti nuove funzioni o correzioni di bug significativi.

La prossima versione è pianificata per l’venerdì 5 giugno 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

<!--
## What's new {#what-is-new}

* 
-->


## Programma per i primi utilizzatori {#early-adoption}

Partecipa al programma per i primi utilizzatori di Cloud Manager per ottenere un accesso esclusivo alle prossime funzioni prima del rilascio generale.

Le seguenti opportunità sono attualmente disponibili per i primi utilizzatori:

### Bring Your Own Git: ora con supporto per GitLab e Bitbucket {#gitlab-bitbucket}

La funzione **Bring Your Own Git** è stata estesa in modo da includere il supporto per archivi esterni come GitLab e Bitbucket. Questo nuovo supporto si aggiunge a quello già esistente per archivi GitHub privati ed aziendali. Quando aggiungi questi nuovi archivi, puoi anche collegarli direttamente alle pipeline. Puoi inoltre ospitare questi archivi sia su piattaforme cloud pubbliche sia all’interno della tua infrastruttura o del tuo cloud privato. Questa integrazione elimina anche la necessità di sincronizzare continuamente il codice con l’archivio Adobe e offre la possibilità di convalidare le richieste pull prima di unirle in un ramo principale.

Le pipeline che utilizzano archivi esterni (esclusi quelli ospitati da GitHub) e il **Trigger di implementazione** impostato su **Cambiamenti su Git** ora vengono avviate automaticamente.

Consulta [Aggiungere archivi esterni in Cloud Manager](/help/managing-code/external-repositories.md).

![Finestra di dialogo Aggiungi archivio](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Attualmente, i controlli di qualità predefiniti per il codice di richiesta pull sono esclusivi degli archivi ospitati in GitHub, ma è in preparazione un aggiornamento per estendere questa funzionalità anche ad altri fornitori Git.

Se ti interessa testare questa nuova funzione e condividere il tuo feedback, invia un’e-mail a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) dall’indirizzo e-mail associato al tuo Adobe ID. Se ti trovi in una struttura di archivio privata/pubblica o aziendale, assicurati di specificare la piattaforma Git che desideri utilizzare.

### Pipeline solo di staging e solo di produzione {#staging-production-only-pipelines}

Adobe annuncia l’introduzione del supporto per [pipeline solo di staging e solo di produzione](/help/using/stage-prod-only.md). Questa nuova funzione consente di suddividere le pipeline di distribuzione in produzione full stack in implementazioni più piccole e specializzate.

Se ti interessa testare questa nuova funzione e fornire un feedback, invia un’e-mail a [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) utilizzando l’indirizzo e-mail associato al tuo Adobe ID.


<!--
## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
