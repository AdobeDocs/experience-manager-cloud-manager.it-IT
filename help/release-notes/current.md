---
title: Note sulla versione 2025.9.0 di Cloud Manager
description: Ulteriori informazioni sulla versione 2025.9.0 di Cloud Manager su Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
source-git-commit: 24ec1d82f9a700b57cd74c2c83c8d9d00b8bece1
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 72%

---

# Note sulla versione di Cloud Manager 2025.9.0 su Adobe Managed Services {#release-notes}

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Ulteriori informazioni sulla versione di [!UICONTROL Cloud Manager] 2025.9.0 su Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio della versione 2025.9.0 di [!UICONTROL Cloud Manager] è il venerdì 4 settembre 2025.

<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prossima versione è pianificata per il venerdì 2 ottobre 2025.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->


## Novità {#what-is-new}

* **È stato aggiunto il supporto per Azure DevOps (archivi privati)**

  Gli aggiornamenti della documentazione includono passaggi di configurazione per acquisire un Git personalizzato con Azure DevOps e la convalida delle richieste di pull. Vedi [Aggiungere archivi esterni in Cloud Manager](/help/managing-code/external-repositories.md).

* **Estensione del supporto Git personalizzato (BYOG) alle pipeline di configurazione (archivi privati)**

  Cloud Manager ora supporta le pipeline di configurazione con archivi privati su GitHub, Bitbucket, Azure DevOps e GitLab. Questo sostegno accelera ulteriormente il ciclo di sviluppo. Consulta ![Controlli della richiesta di pull per archivi privati](/help/managing-code/github-check-config.md).

## Programmi Beta {#beta-program}

Partecipa ai programmi Beta di Cloud Manager per ottenere accesso esclusivo alle prossime funzionalità prima del rilascio generale.

Sono attualmente disponibili le seguenti opportunità:


### Integra il tuo Git personale (BYOG) {#gitlab-bitbucket-azure-vsts}

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

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->

## Correzioni di bug {#bug-fixes}

Non sono state apportate correzioni di bug significativi nella versione di agosto di Cloud Manager.

<!--
Known Issues {#known-issues}

* A -->
