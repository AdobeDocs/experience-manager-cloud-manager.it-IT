---
title: Note sulla versione 2023.8.0
description: Queste sono le note sulla versione 2023.8.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: f930f12b5f50dd96a1677ff7a56cf0e92a400556
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 39%

---


# Note sulla versione 2023.8.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2023.8.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di pubblicazione della versione 2023.8.0 di [!UICONTROL Cloud Manager] è l’10 agosto 2023. La versione successiva è pianificata per il 7 settembre 2023.

## Novità {#what-is-new}

* Sono stati apportati miglioramenti per migliorare la comprensibilità e la visualizzazione dei messaggi di errore nell’interfaccia utente di Cloud Manager.

## Correzioni di bug {#bug-fixes}

* Casi non frequenti di [copia contenuto](/help/using/content-copy.md) i processi che si bloccano sono stati risolti.
* È stato risolto un problema di test temporaneo per i clienti che non utilizzano New Relic One.
* [Regole per la qualità del codice personalizzato](/help/using/custom-code-quality-rules.md) `SupportedRunmode` e `ImmutableMutableMixedPackage` sono stati rimossi da SonarQube in quanto si applicano solo agli as a Cloud Service AEM.
* Gli utenti non incontreranno più pipeline bloccate che sembrano in stato di esecuzione.
* Il **Ambienti** Il menu ora si chiude dopo aver attivato **[Copia contenuto](/help/using/content-copy.md)** modale.
* [Una riesecuzione della pipeline](/help/using/code-deployment.md#reexecute-deployment) non è più consentito se l’esecuzione precedente non ha un `commitId` impostato sullo stato della fase di build.
* Ora quando un utente fa clic su una pipeline in viene visualizzato un messaggio più comprensibile per i rari errori **Attività** o **Pipeline** schermi.
