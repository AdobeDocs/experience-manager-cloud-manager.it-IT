---
title: Note sulla versione 2024.11.0 di Cloud Manager
description: Scopri la versione di Cloud Manager 2024.11.0.
feature: Release Information
source-git-commit: 4c22de9fa675edcd743d7acce6c7a1def8efa414
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 65%

---

# Note sulla versione 2024.11.0 di Cloud Manager {#release-notes}

Scopri la versione di [!UICONTROL Cloud Manager] 2024.11.0.

>[!NOTE]
>
>Consulta le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di rilascio {#release-date}

<!-- SAVE FOR FUTURE POSSIBLE USE No notable bugs or features for the September release of Cloud Manager. -->

La data di rilascio per [!UICONTROL Cloud Manager] 2024.11.0 è il 7 novembre 2024.

La prossima versione pianificata è il 5 dicembre 2024.

## Novità {#what-is-new}

* Quando le pagine vengono reindirizzate a un altro dominio durante il test delle prestazioni, i risultati del test per tali pagine vengono esclusi, in quanto non rappresentano con precisione le prestazioni effettive. <!-- (CMGR-5637) -->

## Programma per i primi utilizzatori {#early-adoption}

Partecipa al programma per i primi utilizzatori di Cloud Manger e concediti la possibilità di testare le prossime funzionalità.

### Bring Your Own Git: ora con supporto per GitLab e Bitbucket {#gitlab-bitbucket}

<!-- BOTH CS & AMS -->

La funzionalità **Bring Your Own Git** è stata estesa in modo da includere il supporto per archivi esterni come GitLab e Bitbucket. Questo nuovo supporto si aggiunge a quello già esistente per archivi GitHub privati ed aziendali. Quando aggiungi questi nuovi archivi, puoi anche collegarli direttamente alle pipeline. Puoi inoltre ospitare questi archivi sia su piattaforme cloud pubbliche sia all’interno della tua infrastruttura o del tuo cloud privato. Questa integrazione elimina anche la necessità di sincronizzare continuamente il codice con l’archivio Adobe e offre la possibilità di convalidare le richieste pull prima di unirle in un ramo principale.

Consulta [Aggiungere archivi esterni in Cloud Manager](/help/managing-code/external-repositories.md).

![Finestra di dialogo Aggiungi archivio](/help/release-notes/assets/repositories-add-release-notes.png)

>[!NOTE]
>
>Attualmente, i controlli di qualità predefiniti per il codice di richiesta pull sono esclusivi degli archivi ospitati in GitHub, ma è in preparazione un aggiornamento per estendere questa funzionalità anche ad altri fornitori Git.

Se ti interessa testare questa nuova funzione e condividere il tuo feedback, invia un’e-mail a [Grp-CloudManager_BYOG@adobe.com](mailto:Grp-CloudManager_BYOG@adobe.com) dall’indirizzo e-mail associato al tuo Adobe ID. Se ti trovi in una struttura di archivio privata/pubblica o aziendale, assicurati di specificare la piattaforma Git che desideri utilizzare.

### Pipeline solo di staging e solo di produzione {#staging-production-only-pipelines}

Adobe annuncia l’introduzione del supporto per [pipeline solo di staging e solo di produzione](/help/using/stage-prod-only.md). Questa nuova funzione consente di suddividere le pipeline di distribuzione in produzione full stack in implementazioni più piccole e specializzate.

Se ti interessa testare questa nuova funzione e fornire un feedback, invia un’e-mail a [Grp-cloudmanager_splitpipelines@adobe.com](mailto:Grp-cloudmanager_splitpipelines@adobe.com) utilizzando l’indirizzo e-mail associato al tuo Adobe ID.

## Correzioni di bug

* Ora viene risolto un bug in AEM Cloud Manager che causava un errore &quot;403&quot; durante gli aggiornamenti dello stato per le operazioni di copia del contenuto. Questo problema, attribuito a un indirizzo IP di ingresso non configurato correttamente, impediva la propagazione dello stato e causava la visualizzazione indefinita di alcune attività di copia dei contenuti, che richiedevano l’annullamento manuale. La correzione ora garantisce la corretta generazione di rapporti sullo stato e un’esecuzione più fluida delle attività di copia del contenuto. <!-- (CMGR-62739) -->
* Un aggiornamento recente ha risolto un problema in SonarQube a causa del quale in alcuni casi non venivano rilevate password hardcoded. La correzione ora include un controllo pattern espanso e si allinea agli standard di rilevamento predefiniti in SonarQube. <!-- CMGR-62682 -->

<!-- Known Issues {#known-issues}

* A -->
