---
title: Note sulla versione 2021.11.0
description: Segui questa pagina per ottenere informazioni sulla versione 2021.11.0 di Cloud Manager
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 6852df51d4b9b4947f1d5ce0b5a284bef94d0589
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 3%

---

# Note sulla versione 2021.11.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione di [!UICONTROL Cloud Manager] Versione 2021.11.0.

>[!NOTE]
>Fai riferimento a [Note sulla versione corrente](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/release-notes-cloud-manager/release-notes-cm-current.html?lang=en#getting-access) per visualizzare le ultime note sulla versione per Cloud Manager in AEM as a Cloud Service.

## Data di pubblicazione {#release-date}

Data di rilascio per [!UICONTROL Cloud Manager] La versione 2021.11.0 è il 4 novembre 2021.
La prossima versione è prevista per il 16 dicembre 2021.

## Novità {#whats-new}

* L’ID del commit Git verrà ora visualizzato nei dettagli di esecuzione della pipeline, facilitando il tracciamento del codice generato.

* La `x-request-id` l&#39;intestazione di risposta è ora visibile in API Playground on [www.adobe.io](https://www.adobe.io/). Questa intestazione è utile quando si inviano problemi di assistenza clienti per la risoluzione dei problemi.

* In qualità di utente, vedo la scheda Pipeline con tubazioni zero che mi forniscono la guida appropriata.

* È ora disponibile una nuova pagina Attività in cui è possibile visualizzare le attività come la pipeline e le esecuzioni di codice insieme ai relativi dettagli associati. Nel tempo, le attività elencate in questa pagina si espanderanno nell’ambito insieme ai dettagli forniti.

* È ora disponibile una nuova pagina Pipelines con un puntatore di stato al passaggio del mouse per una facile visualizzazione del riepilogo dei dettagli. Le esecuzioni della pipeline possono essere visualizzate insieme ai relativi dettagli associati.

* L’API Edit Pipeline ora supporta l’impostazione dei percorsi di annullamento della validità e scaricamento del dispatcher.

* L’API Edit Pipeline ora supporta la modifica dell’ambiente utilizzato nelle fasi di distribuzione.

* È stata introdotta un&#39;ottimizzazione nel processo di scansione OakPal per i pacchetti di grandi dimensioni.

* Il file CSV del problema qualità conterrà ora la marca temporale per ogni problema di qualità.

* Il pulsante Gestisci nella pagina Ambienti non sarà più visibile nell’interfaccia utente di .

## Correzioni di bug {#bug-fixes}

* Alcune configurazioni di build non ortodosse hanno comportato la memorizzazione di file non necessari nella cache degli artefatti Maven della pipeline, causando un I/O di rete estranea all’avvio e all’arresto del contenitore di build.

* L’API di Pipeline PATCH non riesce se la fase di distribuzione non esiste.

* La `ClientlibProxyResourceCheck` la regola di qualità generava falsi problemi positivi in presenza di librerie client con percorsi di base comuni.

* Il messaggio di errore quando è stato raggiunto il numero massimo di archivi non specifica il motivo dell&#39;errore.

* In rari casi, le pipeline non riuscivano a causa di una gestione inappropriata dei tentativi di alcuni codici di risposta.
