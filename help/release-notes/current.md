---
title: Note sulla versione 2023.11.0
description: Queste sono le note sulla versione 2023.11.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 264c7ffcbc9e10903880a511a4ca605be666f7e8
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 88%

---


# Note sulla versione 2023.11.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2023.11.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di pubblicazione della versione 2023.11.0 di [!UICONTROL Cloud Manager] è il 14 novembre 2023. La prossima versione è pianificata per il 7 dicembre 2023.

## Novità {#what-is-new}

* [La pagina Dettagli di esecuzione della pipeline](/help/using/managing-pipelines.md#view-details) mostrerà ora tutti i passaggi di esecuzione di una pipeline insieme a quelli inattivi non ancora avviati.
* Su entrambe le pagine **[Attività](/help/using/managing-pipelines.md#activity)** e **[Pipeline](/help/using/managing-pipelines.md#pipelines)**, quando si fa clic su una pipeline con stato in esecuzione, è ora disponibile un riepilogo dell’esecuzione della pipeline.
* È stata aggiunta una nuova sezione **Durata** alla [pagina Dettagli della pipeline](/help/using/managing-pipelines.md#view-details), che include la durata media del passaggio della pipeline in base alla tendenza storica per quel programma.
* Il giorno [pagina di esecuzione della pipeline,](/help/using/managing-pipelines.md#activity-window) i passaggi completati ora visualizzano la durata
* Lo [strumento Copia contenuto](/help/using/content-copy.md) di Cloud Manager consente agli utenti di copiare contenuto modificabile su richiesta dagli ambienti di produzione AEM 6.x in hosting AMS in ambienti inferiori, a scopo di test.
* Esecuzioni che [riutilizzare gli artefatti di build](/help/getting-started/project-setup.md#build-artifact-reuse) mostrerà ora il collegamento all’esecuzione che ha inizialmente creato tali artefatti.
* Opzione da selezionare **Errori di metriche importanti** può ora essere configurato per [pipeline di qualità del codice](/help/using/non-production-pipelines.md) anche.

## Programma per i primi utilizzatori {#early-adoption}

Partecipa al nostro programma per i primi utilizzatori e concediti la possibilità di testare alcune delle prossime funzionalità

### Porta il tuo GitHub personale {#byo-github}

Se utilizzi GitHub per gestire gli archivi, [ora puoi convalidare il codice direttamente all’interno degli archivi GitHub tramite Cloud Manager.](/help/managing-code/byo-github.md) Questa integrazione elimina la necessità di sincronizzare in modo coerente il codice con l’archivio Adobe e consente di verificare le richieste pull prima di unirle ai rami principali.

Se ti interessa testare questa nuova funzionalità e condividere il tuo feedback, invia un’e-mail a `Grp-CloudManager_BYOG@adobe.com` dall’indirizzo e-mail associato al tuo Adobe ID.

### Autorizzazioni personalizzate {#custom-permissions}

Le [autorizzazioni personalizzate di Cloud Manager](/help/using/custom-permissions.md) consentono di creare nuovi profili di autorizzazioni personalizzati con autorizzazioni configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.

Se ti interessa testare questa nuova funzione e condividere il tuo feedback, invia un’e-mail `Grp-CloudManager_ams_custompermissions@adobe.com` dall’indirizzo e-mail associato al tuo Adobe ID.
