---
title: Note sulla versione 2024.3.0
description: Queste sono le note sulla versione 2024.3.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 22730ba281f7c1c4720158a3a813c56b815a0af1
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 93%

---


# Note sulla versione 2024.3.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2024.3.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di pubblicazione della versione 2024.3.0 di [!UICONTROL Cloud Manager] è il 14 marzo 2024. La prossima versione è prevista per l’11 aprile 2024.

## Novità {#what-is-new}

* I dettagli, comprese le informazioni IP/DNS (FQDN) dei server verdi, sono ora visualizzati nell’interfaccia utente di Cloud Manager.

## Programma per i primi utilizzatori {#early-adoption}

Partecipa al nostro programma per i primi utilizzatori e concediti la possibilità di testare alcune delle prossime funzionalità

### Porta il tuo GitHub personale {#byo-github}

Se utilizzi GitHub per gestire gli archivi, [ora puoi convalidare il codice direttamente all’interno degli archivi GitHub tramite Cloud Manager.](/help/managing-code/byo-github.md) Questa integrazione elimina la necessità di sincronizzare in modo coerente il codice con l’archivio Adobe e consente di verificare le richieste pull prima di unirle ai rami principali. Questa funzionalità è esclusiva di GitHub pubblico. Il supporto per GitHub self-hosted non è disponibile.

Se ti interessa testare questa nuova funzionalità e condividere il tuo feedback, invia un’e-mail a `Grp-CloudManager_BYOG@adobe.com` dall’indirizzo e-mail associato al tuo Adobe ID.

## Correzioni di bug {#bug-fixes}

* È stato corretto un errore che si verificava quando i registri appropriati non venivano generati durante la fase di test delle prestazioni quando la metrica del tasso di errore non riusciva.
* Una logica migliorata all’interno del servizio di test delle prestazioni con il compito di rilevare l’assenza di una pagina sul sito (404) ora garantisce una distribuzione più fluida e ininterrotta.
