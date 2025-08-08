---
title: Note sulla versione 2025.8.0 di Cloud Manager
description: Ulteriori informazioni sulla versione 2025.8.0 di Cloud Manager su Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: a96bc45242ee6c6b06b4354756a67562150f385c
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 73%

---

# Note sulla versione di Cloud Manager 2025.8.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Ulteriori informazioni sulla versione di [!UICONTROL Cloud Manager] 2025.8.0 su Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio della versione 2025.8.0 di [!UICONTROL Cloud Manager] è il venerdì 7 agosto 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prossima versione è pianificata per il venerdì 4 settembre 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Novità {#what-is-new}



* **Pipeline di sola gestione temporanea e di sola produzione**

  Cloud Manager ora supporta le pipeline di sola staging e di sola produzione. Questa funzione consente di suddividere le distribuzioni di produzione full stack in pipeline più piccole e specifiche per uno scopo. <!-- This feature went into GA from Private beta in the June 5, 2025 CM release -->

  ![Finestra di dialogo Aggiungi pipeline non di produzione con il pulsante di opzione Codice full stack selezionato e l&#39;ambiente di staging selezionato](/help/release-notes/assets/add-non-production-pipeline.png)

  Consulta [Pipeline di sola fase e sola produzione](/help/using/stage-prod-only.md).

* **Pipeline preferite**

  In questa versione, Cloud Manager introduce la possibilità di fissare le pipeline preferite, consentendoti di contrassegnare specifiche pipeline come preferite in modo che vengano visualizzate nella parte superiore dell&#39;elenco nella pagina **Pipeline**. Questo miglioramento semplifica la ricerca e l’esecuzione delle pipeline a cui si accede di frequente. <!-- CMGR-68293 -->

  ![Pipeline contrassegnate come preferite](/help/release-notes/assets/pipeline-favorites.png) *Due pipeline contrassegnate come preferite.*

  Consulta [Contrassegnare le pipeline come preferite](/help/using/managing-pipelines.md#pipeline-favorites).


## Programmi Beta {#beta-program}

Partecipa ai programmi Beta di Cloud Manager per ottenere accesso esclusivo alle prossime funzionalità prima del rilascio generale.

Sono attualmente disponibili le seguenti opportunità:


### Porta il tuo Git (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Ora è possibile portare in Cloud Manager i propri archivi Git Azure DevOps, con supporto per i nuovi archivi Azure DevOps e gli archivi legacy VSTS (Visual Studio Team Services).

* Per chi usa Edge Delivery Services, l’archivio di cui è stato eseguito l’onboarding può essere utilizzato per sincronizzare e distribuire il codice del sito.
* Per chi usa AEM as a Cloud Service e Adobe Managed Services (AMS), l’archivio può essere collegato sia a pipeline full stack che front-end.

Verranno presto introdotti anche il supporto di ulteriori tipi di pipeline e la convalida di richieste pull tramite pipeline per la qualità del codice.

Consulta [Aggiungere archivi esterni in Cloud Manager](/help/managing-code/external-repositories.md).

![Finestra di dialogo Aggiungi archivio](/help/release-notes/assets/azure-repo.png)

Se ti interessa testare questa nuova funzione e condividere il tuo feedback, invia un’e-mail a [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) dall’indirizzo e-mail associato al tuo Adobe ID. Se ti trovi in una struttura di archivio privata/pubblica o aziendale, assicurati di specificare la piattaforma Git che desideri utilizzare.

#### Gestisci token di accesso{#manage-access-tokens}

Utilizza **Gestisci token di accesso** in Cloud Manager per visualizzare, rinominare ed eliminare i token di accesso associati agli archivi BYOG esterni, ad esempio GitHub Enterprise, GitLab, Bitbucket e Azure DevOps.

Consulta [Gestisci token di accesso](/help/managing-code/manage-access-tokens.md).

Se ti interessa testare questa nuova funzione e condividere il tuo feedback, invia un’e-mail a [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) dall’indirizzo e-mail associato al tuo Adobe ID.

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->


## Correzioni di bug {#bug-fixes}

Non sono state apportate correzioni di bug significativi nella versione di luglio di Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
