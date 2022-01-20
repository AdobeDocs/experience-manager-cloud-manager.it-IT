---
title: Note sulla versione 2022.01.0
description: Queste sono le note sulla versione per la versione 2022.01.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: ebbbbdca2bfd834bc3dc0ff06ffb318df42713ee
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 6%

---

# Note sulla versione per Cloud Manager versione 2021.12.0 {#release-notes}

La sezione seguente illustra le note generali sulla versione di [!UICONTROL Cloud Manager] versione 2022.01.0.

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2022.01.0 è il 20 gennaio 2022. La prossima versione è prevista per il 10 febbraio 2022.

## Novità {#whats-new}

* Cloud Manager [evita di ricostruire la base di codice quando rileva che viene utilizzato lo stesso commit git](/help/using/setting-up-project.md#build-artifact-reuse) in più esecuzioni di pipeline di stack complete.
* Al momento della generazione di una password git, verrà visualizzata la data di scadenza.

## Correzioni di bug {#bug-fixes}

* Sono stati risolti i casi non frequenti di errori di pipeline falsi positivi.
* Per i programmi con un solo archivio, nella schermata di esecuzione della pipeline viene ora visualizzato il nome dell’archivio.
