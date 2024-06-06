---
title: Note sulla versione 2024.6.0
description: Queste sono le note sulla versione 2024.6.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: a41ea35cb685d4e88e016bc887eb2465963747e1
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 48%

---


# Note sulla versione 2024.6.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2024.6.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2024.6.0 di è il 6 giugno 2024. La prossima versione è pianificata per l’11 luglio 2024.

## Novità {#what-is-new}

* Ora puoi [utilizzare i propri archivi GitHub](/help/managing-code/private-repositories.md) come origini per pipeline full stack e front-end.
   * Inoltre, puoi sfruttare gli archivi GitHub con [sottomoduli Git,](/help/managing-code/git-submodules.md) offre un controllo avanzato sulle pipeline generate automaticamente utilizzate per la convalida delle richieste di pull e consente di definire i comportamenti per le metriche cruciali durante la fase di scansione del codice.
   * [Puoi anche scegliere](/help/managing-code/github-check-config.md) per mantenere la cronologia dei rapporti su GitHub, assegna un nome alla pipeline e imposta le variabili della pipeline in base alle tue esigenze.
* Sono state aggiunte nuove regole OakPal al [Analisi della qualità del codice di Cloud Manager.](/help/using/custom-code-quality-rules.md#oakpal-ui-content-package)
   * Ogni nuova regola aggiunta a partire da giugno 2024 è una modifica continua.
   * Ti invitiamo a risolvere questi problemi il prima possibile, poiché queste nuove regole causeranno un errore delle pipeline a partire dalla versione di agosto 2024 di Cloud Manager.

## Programma per i primi utilizzatori {#early-adoption}

Partecipa al nostro programma per i primi utilizzatori e concediti la possibilità di testare alcune delle prossime funzionalità

### Pipeline solo di staging e solo di produzione {#staging-production-only-pipelines}

È stato introdotto il supporto per le [pipeline solo di staging e solo di produzione](/help/using/stage-prod-only.md), che consente di suddividere le pipeline di distribuzione di produzione full stack in distribuzioni più piccole e specializzate.

Se ti interessa testare questa nuova funzionalità e condividere il feedback, invia un’e-mail a `Grp-cloudmanager_splitpipelines@adobe.com` dall’indirizzo e-mail associato all’Adobe ID.
