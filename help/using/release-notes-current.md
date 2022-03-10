---
title: Note sulla versione 2022.3.0
description: Queste sono le note sulla versione per la versione 2022.3.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 4a5ddf3144ec50f1a7a4ac367b5c99bc9b486752
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 4%

---


# Note sulla versione per Cloud Manager versione 2022.3.0 {#release-notes}

Questa pagina documenta le note sulla versione per [!UICONTROL Cloud Manager] versione 2022.3.0.

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2022.3.0 è il 10 marzo 2022. La prossima versione è prevista per il 7 aprile 2022.

## Novità {#what-is-new}

* Le richieste HTTP in uscita dai test delle risorse verranno ora effettuate da un intervallo IP fisso.


## Correzioni di bug {#bug-fixes}

* La **Ignora modifiche di Load Balancer** impossibile disabilitare l&#39;opzione .
* La **Ignora modifiche di Load Balancer** l&#39;opzione non è stata visualizzata in Distribuzione sviluppo AMS **Modifica flusso di lavoro della pipeline**.
* Un sottoinsieme di archivi Git creati manualmente presentava un valore di nome errato che impediva l’efficacia della funzione di riutilizzo degli artefatti di generazione. I nomi di tali archivi sono stati modificati e gli utenti vedranno il nome corretto nell’API/interfaccia utente di Cloud Manager.
* Gli artefatti di generazione da pipeline non di produzione sono stati riutilizzati in modo inappropriato sulle pipeline di stack complete di produzione.
* Quando si aggiunge o si modifica una pipeline di qualità del codice, le opzioni per gestire gli errori di metrica non vengono più visualizzate.
* Alcune configurazioni impreviste di variabili della pipeline potrebbero causare nel passaggio di compilazione.
