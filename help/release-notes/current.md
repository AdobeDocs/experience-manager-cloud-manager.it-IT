---
title: Note sulla versione per Cloud Manager 2024.8.0
description: Scopri le note sulla versione di Cloud Manager 2024.8.0.
feature: Release Information
source-git-commit: dd764bb17127ba0a1e88e85592329cc9ddff42e3
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---


# Note sulla versione per Cloud Manager 2024.8.0 {#release-notes}

In questa pagina sono documentate le note sulla versione di [!UICONTROL Cloud Manager] 2024.8.0.

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/cloud-manager/current).

## Data di rilascio {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] 2024.8.0 è il 14 agosto 2024. La prossima versione è pianificata per il 14 settembre 2024.

## Novità {#what-is-new}

* Per le pipeline di sola fase e di sola produzione (disponibili come parte del [programma early adopter](#staging-production-only-pipelines)), è ora possibile eseguirle in [modalità emergenza,](/help/using/stage-prod-only.md#emergency-mode) ignorando il test della fase.

## Programma di adozione anticipata {#early-adoption}

Partecipa al programma di adozione anticipata di Adobe e hai la possibilità di testare alcune delle prossime funzionalità.

### Pipeline di sola staging e di sola produzione {#staging-production-only-pipelines}

Adobe è entusiasta di annunciare l&#39;introduzione del supporto per [pipeline solo di staging e solo di produzione](/help/using/stage-prod-only.md). Questa nuova funzione consente di suddividere le pipeline di distribuzione di produzione full stack in implementazioni più piccole e specializzate.

Se desideri testare questa funzione e fornire un feedback, invia un&#39;e-mail a `Grp-cloudmanager_splitpipelines@adobe.com` utilizzando l&#39;indirizzo e-mail associato al tuo Adobe ID.

## Correzioni di bug

* È stato risolto un raro problema a causa del quale i passaggi della pipeline venivano trovati in esecuzione dopo l’eliminazione della pipeline.
* La riesecuzione della pipeline ora funziona al primo tentativo, correggendo un raro problema in cui era necessario avviare una nuova esecuzione più volte.
* I passaggi di distribuzione pianificati per le pipeline full stack ora rispettano la data pianificata selezionata e non tornano a **Ora**.
* Gli stati delle attività di copia del contenuto non riuscite ora vengono rispecchiati correttamente e in rare circostanze non viene più visualizzato in modo errato lo stato `In Progress`.

## Problemi noti {#known-issues}

{{content-copy-known-issues}}
