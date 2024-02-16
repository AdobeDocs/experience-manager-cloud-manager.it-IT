---
title: Note sulla versione 2024.2.0
description: Queste sono le note sulla versione 2024.2.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: cc87246503ab63d6dd60c691f15fc4759fcf6939
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 61%

---


# Note sulla versione 2024.2.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2024.2.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2024.2.0 di è il 15 febbraio 2024. La prossima versione è prevista per il 16 marzo 2024.

## Novità {#what-is-new}

* Come parte di [distribuzione,](/help/using/code-deployment.md) la cache di Dispatcher è stata svuotata in corrispondenza del **Allega Dispatcher** passaggio. Per consentirti di verificare le modifiche su ciascun nodo prima di allegarlo al load balancer dell’applicazione, dopo aver distribuito il codice a un determinato editore, ora puoi testare le modifiche direttamente dal Dispatcher associato prima di allegarlo al load balancer.
* [L’ambiente di build](/help/getting-started/build-environment.md) è stato aggiornato alle versioni Maven 3.9.4 e JDK jdk-11.0.22 e jdk1.8.0_401.

## Programma per i primi utilizzatori {#early-adoption}

Partecipa al nostro programma per i primi utilizzatori e concediti la possibilità di testare alcune delle prossime funzionalità

### Porta il tuo GitHub personale {#byo-github}

Se utilizzi GitHub per gestire gli archivi, [ora puoi convalidare il codice direttamente all’interno degli archivi GitHub tramite Cloud Manager.](/help/managing-code/byo-github.md) Questa integrazione elimina la necessità di sincronizzare in modo coerente il codice con l’archivio Adobe e consente di verificare le richieste pull prima di unirle ai rami principali. Questa funzionalità è esclusiva di GitHub pubblico. Il supporto per GitHub self-hosted non è disponibile.

Se ti interessa testare questa nuova funzionalità e condividere il tuo feedback, invia un’e-mail a `Grp-CloudManager_BYOG@adobe.com` dall’indirizzo e-mail associato al tuo Adobe ID.

## Correzioni di bug {#bug-fixes}

* Il JDK dei contenitori di build è stato aggiornato a una versione che risolve [JDK-8313765.](https://bugs.openjdk.org/browse/JDK-8313765)
§