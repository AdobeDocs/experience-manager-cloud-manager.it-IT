---
title: Note sulla versione 2022.5.0
description: Queste sono le note sulla versione per la versione 2022.5.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 0ddfd152cb15731882d198d043dd8897b5073ab4
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 46%

---


# Note sulla versione per Cloud Manager versione 2022.5.0 {#release-notes}

Questa pagina documenta le note sulla versione per [!UICONTROL Cloud Manager] versione 2022.5.0.

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2022.5.0 è il 5 maggio 2022. La prossima versione è prevista per il 9 giugno 2022.

## Novità {#what-is-new}

Per accedere al registro dell’ambiente di AEM è possibile utilizzare il ruolo Sviluppatore .

## Correzioni di bug {#bug-fixes}

* Un sottoinsieme di archivi Git creati manualmente presentava un valore di nome errato che impediva l’efficacia della funzione di riutilizzo degli artefatti di build. I nomi di tali archivi sono stati modificati e gli utenti vedranno il nome corretto nell’API/interfaccia utente di Cloud Manager.
* Gli artefatti di build da pipeline non di produzione venivano riutilizzati in modo inappropriato sulle pipeline full stack di produzione.
* Quando si aggiunge o si modifica una pipeline di qualità del codice, le opzioni per gestire gli errori di metrica non vengono più visualizzate.
* Alcune configurazioni impreviste delle variabili della pipeline potrebbero causare errori nel passaggio di compilazione.
