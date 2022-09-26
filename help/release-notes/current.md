---
title: Note sulla versione 2022.9.0
description: Queste sono le note sulla versione per la versione 2022.9.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: e74d386d0b2d50a7e276bb7ead7594ef448742ae
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 4%

---


# Note sulla versione per Cloud Manager versione 2022.9.0 {#release-notes}

Questa pagina documenta le note sulla versione per [!UICONTROL Cloud Manager] versione 2022.9.0.

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2022.9.0 è l’8 settembre 2022. La prossima versione è prevista per il 6 ottobre 2022.

## Novità {#what-is-new}

* Supporto di Cloud Manager per il ridimensionamento automatico orizzontale per più aree.
* Nuova scheda Pagina di benvenuto personalizzata per gli utenti che hanno solo un ruolo utente di Cloud Manager che li guida su come navigare AEM ambienti e accesso limitato ai programmi.
* I clienti che non dispongono di alcun ruolo di Cloud Manager non potranno accedere ai dettagli del programma. Tuttavia, possono passare ai punti finali di authoring dalla pagina di destinazione di CM.
* Elimina gli errori della pipeline derivanti da tentativi non riusciti grazie alla creazione di una maggiore resilienza.

## Correzioni di bug {#bug-fixes}

* È stato migliorato il feedback dei clienti sulla build delle app AEM dei clienti quando maven si trova ad affrontare problemi di connettività ai repository privati.
* In rari casi, quando il sistema di controllo dello stato di salute non è in grado di recuperare un punteggio di integrità valido, non verrà attivato un evento di scalabilità automatica.