---
title: Note sulla versione 2024.5.0
description: Queste sono le note sulla versione 2024.5.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 395fe2a42fc2d6413dff38c9e4620c62039f87e2
workflow-type: ht
source-wordcount: '287'
ht-degree: 100%

---


# Note sulla versione 2024.5.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2024.5.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di pubblicazione della versione 2024.5.0 di [!UICONTROL Cloud Manager] è il 9 maggio 2024. La prossima versione è prevista per il 6 giugno 2024.

## Novità {#what-is-new}

* Il passaggio di audit del contenuto ora viene ignorato quando una pipeline è in esecuzione in [modalità emergenza.](/help/using/code-deployment.md#emergency-pipeline)

## Programma per i primi utilizzatori {#early-adoption}

Partecipa al nostro programma per i primi utilizzatori e concediti la possibilità di testare alcune delle prossime funzionalità

### Pipeline solo di staging e solo di produzione {#staging-production-only-pipelines}

È stato introdotto il supporto per le [pipeline solo di staging e solo di produzione](/help/using/stage-prod-only.md), che consente di suddividere le pipeline di distribuzione di produzione full stack in distribuzioni più piccole e specializzate.

Se ti interessa testare questa nuova funzionalità e condividere il feedback, invia un’e-mail a `Grp-cloudmanager_splitpipelines@adobe.com` dall’indirizzo e-mail associato all’Adobe ID.

### Porta il tuo GitHub personale {#byo-github}

Se utilizzi GitHub per gestire gli archivi, [ora puoi convalidare il codice direttamente all’interno degli archivi GitHub tramite Cloud Manager.](/help/managing-code/byo-github.md) Questa integrazione elimina la necessità di sincronizzare in modo coerente il codice con l’archivio Adobe e consente di verificare le richieste pull prima di unirle ai rami principali. Questa funzionalità è esclusiva di GitHub pubblico. Il supporto per GitHub self-hosted non è disponibile.

Se ti interessa testare questa nuova funzionalità e condividere il tuo feedback, invia un’e-mail a `Grp-CloudManager_BYOG@adobe.com` dall’indirizzo e-mail associato al tuo Adobe ID.

## Correzioni di bug {#bug-fixes}

* È stato corretto un bug a causa del quale Cloud Manager riutilizzava gli artefatti con hash del commit errato.
