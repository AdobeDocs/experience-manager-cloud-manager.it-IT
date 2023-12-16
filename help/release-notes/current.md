---
title: Note sulla versione 2023.12.0
description: Queste sono le note sulla versione 2023.12.0 di Cloud Manager.
feature: Release Information
exl-id: 2d38abb1-cfc7-44a9-b303-b555e2827eea
source-git-commit: 2ac254508e4015fea21c4fcd087703ac5fbeeec6
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 63%

---


# Note sulla versione 2023.12.0 di Cloud Manager {#release-notes}

In questa pagina sono documentate le note sulla versione 2023.12.0 di [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Per le ultime note sulla versione di Cloud Manager in AEM as a Cloud Service, fai riferimento a [Cloud Manager nelle note sulla versione corrente di AEM as a Cloud Service.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/release-notes-cloud-manager/release-notes-cm-current.html?lang=it)

## Data di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] la versione 2023.12.0 di è il 14 dicembre 2023. La prossima versione è prevista per il 18 gennaio 2024.

## Novità {#what-is-new}

* Le [autorizzazioni personalizzate di Cloud Manager](/help/using/custom-permissions.md) consentono di creare nuovi profili di autorizzazioni personalizzati con autorizzazioni configurabili per limitare l’accesso a programmi, pipeline e ambienti per gli utenti di Cloud Manager.
* I rollout degli aggiornamenti di [ambiente di build](/help/getting-started/build-environment.md) che erano [annunciato e iniziato con la versione di ottobre di Cloud Manager](/help/release-notes/2023/2023-10-0.md) sono state completate.
   * È stato aggiunto il supporto per il nodo 18 per [pipeline front-end e full stack.](/help/overview/ci-cd-pipelines.md)
   * La versione secondaria di Java 8 è stata aggiornata a `jdk1.8.0_371`.
   * La versione secondaria di Java 11 è stata aggiornata a `jdk-11.0.20`.
   * Maven è stato aggiornato alla versione 3.8.8
      * Maven ora disabilita tutti gli elementi non sicuri `http://*` per impostazione predefinita.
      * [Adobe di consigli](/help/getting-started/build-environment.md#https-maven) Gli utenti aggiornano gli archivi Maven per utilizzare HTTPS invece di HTTP.
* L’immagine base del contenitore della build è stata aggiornata a Ubuntu 22.04.

## Programma per i primi utilizzatori {#early-adoption}

Partecipa al nostro programma per i primi utilizzatori e concediti la possibilità di testare alcune delle prossime funzionalità

### Porta il tuo GitHub personale {#byo-github}

Se utilizzi GitHub per gestire gli archivi, [ora puoi convalidare il codice direttamente all’interno degli archivi GitHub tramite Cloud Manager.](/help/managing-code/byo-github.md) Questa integrazione elimina la necessità di sincronizzare in modo coerente il codice con l’archivio Adobe e consente di verificare le richieste pull prima di unirle ai rami principali.

Se ti interessa testare questa nuova funzionalità e condividere il tuo feedback, invia un’e-mail a `Grp-CloudManager_BYOG@adobe.com` dall’indirizzo e-mail associato al tuo Adobe ID.
