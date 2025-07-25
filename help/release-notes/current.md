---
title: Note sulla versione 2025.7.0 di Cloud Manager
description: Ulteriori informazioni sulla versione 2025.7.0 di Cloud Manager su Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: a1f023b8ecc6fcae97832c5f3fad6bb8ae79ced1
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 69%

---

# Note sulla versione di Cloud Manager 2025.7.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Ulteriori informazioni sulla versione di [!UICONTROL Cloud Manager] 2025.7.0 su Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio della versione 2025.7.0 di [!UICONTROL Cloud Manager] è il venerdì 10 luglio 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prossima versione è pianificata per il 7 agosto 2025.

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


## Programmi Alpha/Beta {#beta-program}

Partecipa ai programmi alfa e beta di Cloud Manager per ottenere accesso esclusivo alle prossime funzionalità prima del loro rilascio generale.

Sono attualmente disponibili le seguenti opportunità:


### Bring Your Own Git: ora con supporto per GitLab e Bitbucket {#gitlab-bitbucket}

La funzionalità **Bring Your Own Git** (BYOG) è stata espansa per includere il supporto per archivi esterni, come GitLab e Bitbucket. Questo nuovo supporto si aggiunge a quello già esistente per archivi GitHub privati ed aziendali. Quando aggiungi questi nuovi archivi, puoi anche collegarli direttamente alle pipeline. Puoi inoltre ospitare questi archivi sia su piattaforme cloud pubbliche sia all’interno della tua infrastruttura o del tuo cloud privato. Questa integrazione elimina anche la necessità di sincronizzare continuamente il codice con l’archivio Adobe e offre la possibilità di convalidare le richieste pull prima di unirle in un ramo principale.

Le pipeline che utilizzano archivi esterni (esclusi quelli ospitati da GitHub) e il **Trigger di implementazione** impostato su **Cambiamenti su Git** ora vengono avviate automaticamente.

Consulta [Aggiungere archivi esterni in Cloud Manager](/help/managing-code/external-repositories.md).

![Finestra di dialogo Aggiungi archivio](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Attualmente, i controlli di qualità predefiniti per il codice di richiesta pull sono esclusivi degli archivi ospitati in GitHub, ma è in preparazione un aggiornamento per estendere questa funzionalità anche ad altri fornitori Git.

Se ti interessa testare questa nuova funzione e condividere il tuo feedback, invia un’e-mail a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) dall’indirizzo e-mail associato al tuo Adobe ID. Se ti trovi in una struttura di archivio privata/pubblica o aziendale, assicurati di specificare la piattaforma Git che desideri utilizzare.

#### Gestisci token di accesso{#access-tokens}

Utilizza **Gestisci token di accesso** con BYOG per visualizzare, rinominare ed eliminare i token di accesso associati agli archivi Git esterni, quali GitHub Enterprise, GitLab, Bitbucket e Azure DevOps.

Consulta [Gestisci token di accesso](/help/managing-code/manage-access-tokens.md).

Se ti interessa testare questa nuova funzione e condividere il tuo feedback, invia un’e-mail a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) dall’indirizzo e-mail associato al tuo Adobe ID. Se ti trovi in una struttura di archivio privata/pubblica o aziendale, assicurati di specificare la piattaforma Git che desideri utilizzare.


## Correzioni di bug {#bug-fixes}

Non sono state apportate correzioni di bug significativi nella versione di luglio di Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
