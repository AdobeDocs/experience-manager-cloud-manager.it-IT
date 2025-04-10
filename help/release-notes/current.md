---
title: Note sulla versione 2025.4.0 di Cloud Manager
description: Ulteriori informazioni sulla versione 2025.4.0 di Cloud Manager su Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 8c99baba6fb41dd702c338ba727efc237a0f1a8d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 93%

---

# Note sulla versione di Cloud Manager 2025.4.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Ulteriori informazioni sulla versione di [!UICONTROL Cloud Manager] 2025.4.0 su Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio della versione 2025.4.0 di [!UICONTROL Cloud Manager] è il venerdì 10 aprile 2025.

La prossima versione è pianificata per il venerdì 8 maggio 2025.

<!--
## What's new {#what-is-new}

* 
-->


## Programma per i primi utilizzatori {#early-adoption}

Partecipa al programma Early Adoption di Cloud Manager per ottenere accesso esclusivo alle prossime funzionalità prima del rilascio generale.

Sono attualmente disponibili le seguenti opportunità di adozione anticipata:

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
### Self-service Service Pack updates for AMS Cloud Manager customers 

As part of the early adopters program, Adobe Managed Services Cloud Manager customers can now perform self-service service pack updates through the **Cloud Manager** user interface. This feature is currently available *only for development environments* and includes limited error reporting for failures.  

Customers can check for service pack updates on the **Program Overview** page under the **Environments** section (**three-dot menu**).

![Check for updates menu option](/help/release-notes/assets/check-for-updates-1.png)

![Update Service Pack dialog box](/help/release-notes/assets/check-for-updates-2.png)

The installation and upgrade process can be tracked on the **Activity** page. 

Once the process is complete, customers must **approve the execution** for the service pack upgrade to finalize successfully.

![Approve service page update](/help/release-notes/assets/check-for-updates-3.png)

If you are interested in testing this new feature and sharing your feedback, contact your Adobe Customer Success Engineer.

See also [Service Pack Updates for Development Environments - Early Adopter](/help/using/service-packs-environments.md).
-->


<!--
## Bug fixes {#bug-fixes}

* A

Known Issues {#known-issues}

* A -->
