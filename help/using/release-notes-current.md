---
title: Note sulla versione 2021.12.0
description: These are the release notes for Cloud Manager release 2021.12.0.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 61f2d1e0882b752d1a1d5e62f9c028aa71941efe
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 3%

---

# Release Notes for Cloud Manager Release 2021.12.0 {#release-notes}

The following section outlines the general Release Notes for [!UICONTROL Cloud Manager] release 2021.12.0.

>[!NOTE]
>
>For the latest release notes for Cloud Manager in AEM as a Cloud Service, refer to [Cloud Manager in AEM as a Cloud Service&#39;s current release notes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2021.12.0 è il 16 dicembre 2021. La prossima versione è prevista per gennaio 2022.

## Novità {#whats-new}

* The commit hash, which is already visible in the UI, is now also provided in the API.
* La pagina Attività ora include un pop-over per l’esecuzione delle pipeline che fornisce un riepilogo dei dettagli della pipeline a colpo d’occhio.
* Sono stati aggiunti aggiornamenti per includere ulteriori dettagli presentati nella pagina Attività .
* La scheda Informazioni in Cloud Manager ora include l’accesso rapido alle guide API e alle risorse associate.
* Un utente con il ruolo di gestione distribuzione può ora avviare la procedura guidata per la creazione di progetti/rami per un archivio senza rami dal menu azione nella pagina repository.
* Deployment Manager, che si trova nel flusso di lavoro di aggiunta o modifica della pipeline, ora viene informato su come creare un ramo o un progetto se l’archivio selezionato non dispone di rami.
* In the Edit Production Pipeline window, when there is more than one stage environment for production, a dropdown for environment selection is available.
* La versione dell’Archetipo di progetto AEM utilizzato da Cloud Manager è stata aggiornata alla versione 32.

## Correzioni di bug {#bug-fixes}

* Full stack production pipelines remain named &quot;Production Pipeline&quot; even when the user inputs a different name in the name field.
