---
title: Note sulla versione 2024.10.0 di Cloud Manager
description: Queste sono le note sulla versione 2024.10.0 di Cloud Manager.
feature: Release Information
source-git-commit: 74e8f7c0f3896e0e33a02b62c003db322c0d50d8
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 27%

---

# Note sulla versione 2024.10.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2024.10.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le note sulla versione più recenti di Cloud Manager in AEM as a Cloud Service, consulta [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current)



## Data di pubblicazione {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

La data di rilascio per [!UICONTROL Cloud Manager] 2024.10.0 è il 3 ottobre 2024.

La prossima versione è prevista per il venerdì 14 novembre 2024.



## Novità {#what-is-new}

* <!-- BOTH CS & AMS --> La versione dell’Archetipo AEM utilizzato in Cloud Manager è ora aggiornata alla versione 26. Vedi [https://github.com/adobe/aem-project-archetype/releases](https://github.com/adobe/aem-project-archetype/releases)
<!-- (CMGR-59817) -->



## Programma per i primi utilizzatori {#early-adoption}

Partecipa al programma di adozione anticipata di Cloud Manager e prova le prossime funzionalità.

### Porta il tuo Git - ora con supporto per GitLab e Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La funzionalità **Porta il tuo Git** è stata espansa per includere il supporto per archivi esterni come GitLab e Bitbucket. Questo nuovo supporto si aggiunge a quello già esistente per gli archivi GitHub privati ed aziendali. Quando aggiungi questi nuovi repository, puoi anche collegarli direttamente alle pipeline. Puoi ospitare questi archivi su piattaforme cloud pubbliche o all’interno del cloud o dell’infrastruttura privata. Questa integrazione elimina anche la necessità di una sincronizzazione costante del codice con l’archivio Adobe e consente di convalidare le richieste pull prima di unirle in un ramo principale.

Vedi [Aggiungere archivi esterni in Cloud Manager](/help/managing-code/external-repositories.md).

![Finestra di dialogo Aggiungi archivio](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Attualmente, i controlli predefiniti per la qualità del codice di richiesta di pull sono esclusivi per gli archivi ospitati da GitHub, ma è in corso un aggiornamento per estendere questa funzionalità ad altri fornitori Git.

Se ti interessa testare questa nuova funzionalità e condividere i tuoi commenti, invia un&#39;e-mail a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) dal tuo indirizzo e-mail associato al tuo Adobe ID. Assicurati di includere la piattaforma Git da utilizzare e se ti trovi in una struttura di archivio privata/pubblica o aziendale.

### Pipeline solo di staging e solo di produzione {#staging-production-only-pipelines}

L&#39;Adobe annuncia l&#39;introduzione del supporto per [pipeline di sola gestione temporanea e di sola produzione](/help/using/stage-prod-only.md). Questa nuova funzione consente di suddividere le pipeline di distribuzione in produzione full stack in implementazioni più piccole e specializzate.

Se desideri testare questa funzione e fornire un feedback, invia un&#39;e-mail a [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) dal tuo indirizzo e-mail associato al tuo Adobe ID.

<!-- ## Bug fixes

* text
-->

<!-- Known Issues {#known-issues}

 -->
