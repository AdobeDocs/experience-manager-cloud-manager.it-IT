---
title: Note sulla versione 2024.8.0 di Cloud Manager
description: Queste sono le note sulla versione 2024.8.0 di Cloud Manager.
feature: Release Information
source-git-commit: 5ced643fabe0a670e456cbea72f9da8196ac774a
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 28%

---


# Note sulla versione per Cloud Manager 2024.8.0 {#release-notes}

In questa pagina sono documentate le note sulla versione 2024.8.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Data di pubblicazione {#release-date}

La data di pubblicazione della versione 2024.8.0 di [!UICONTROL Cloud Manager] è il giovedì 14 agosto 2024. La prossima versione è prevista per il 14 settembre 2024.

## Novità {#what-is-new}

* Per le pipeline di sola fase e di sola produzione (disponibili come parte del [programma early adopter](#staging-production-only-pipelines)), è ora possibile eseguirle in [modalità emergenza,](/help/using/stage-prod-only.md#emergency-mode) ignorando il test della fase.

## Programma per i primi utilizzatori {#early-adoption}

Partecipa al programma di adozione anticipata di Cloud Manager e prova alcune delle prossime funzionalità.

### Pipeline di sola staging e di sola produzione {#staging-production-only-pipelines}

Adobe è entusiasta di annunciare l&#39;introduzione del supporto per [pipeline solo di staging e solo di produzione](/help/using/stage-prod-only.md). Questa nuova funzione consente di suddividere le pipeline di distribuzione di produzione full stack in implementazioni più piccole e specializzate.

Se desideri testare questa funzione e fornire un feedback, invia un&#39;e-mail a `Grp-cloudmanager_splitpipelines@adobe.com` utilizzando l&#39;indirizzo e-mail associato al tuo Adobe ID.

## Correzioni di bug

* È stato risolto un raro problema a causa del quale i passaggi della pipeline rimanevano in esecuzione dopo l’eliminazione della pipeline.
* La riesecuzione della pipeline ora funziona al primo tentativo, correggendo un raro problema in cui era necessario avviare una nuova esecuzione più volte.
* I passaggi di distribuzione pianificati per le pipeline full stack ora rispettano la data pianificata selezionata e non tornano a **Ora**.
* Gli stati delle attività di copia del contenuto non riuscite ora vengono rispecchiati correttamente e in rare circostanze non viene più visualizzato in modo errato lo stato `In Progress`.

## Problemi noti {#known-issues}

{{content-copy-known-issues}}
