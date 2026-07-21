---
title: Note sulla versione per Cloud Manager 2026.7.0
description: Scopri la versione di Cloud Manager 2026.7.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2:
  - id: c68cd75e-5bca-4bc3-a60e-9e183f816441
  - id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2:
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 3b9ef92a96dab9c1f4b93466d8a2d15185b5864f
workflow-type: tm+mt
source-wordcount: 390
ht-degree: 10%

---


# Note sulla versione 2026.7.0 di Cloud Manager in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Scopri la versione di [!UICONTROL Cloud Manager] 2026.6.0 in Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] 2026.7.0 è giovedì 9 luglio 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prossima versione pianificata è giovedì 6 agosto 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novità {#what-is-new}

<!-- There are no significant new features in the June 2026 Cloud Manager on AMS release. -->

* **Prestazioni di compilazione migliorate con il caching dei moduli**
Un nuovo modello di build compila solo i moduli modificati (anziché l’intero archivio) utilizzando la memorizzazione nella cache a livello di modulo per migliorare le prestazioni di build. Si applica alle pipeline di produzione. Puoi controllare quali pipeline di produzione utilizzano **Smart Build**.

  Per ulteriori informazioni, consulta:

  * [Informazioni sull&#39;utilizzo di Smart Build in una pipeline di produzione](/help/using/production-pipelines.md#about-smart-build) e [Informazioni sull&#39;utilizzo di Smart Build in una pipeline non di produzione](/help/using/non-production-pipelines.md#about-smart-build)
  * [Aggiungi una pipeline di produzione](/help/using/production-pipelines.md#adding-production-pipeline) e [Aggiungi una pipeline non di produzione](/help/using/non-production-pipelines.md#add-non-production-pipeline).

## Programmi Beta {#beta-program}

Per avere accesso esclusivo alle prossime funzionalità prima del rilascio generale, partecipa ai programmi beta di Cloud Manager.

>[!IMPORTANT]
>
>I rilasci di Beta contengono difetti e vengono forniti &quot;COSÌ COME SONO&quot; senza alcuna garanzia. Adobe non ha alcun obbligo di mantenere, correggere, aggiornare, modificare o altrimenti supportare (tramite i servizi di supporto Adobe o in altro modo) le versioni beta. I clienti utilizzano le versioni beta a proprio rischio e pericolo. Non fare affidamento sul corretto funzionamento o sulle prestazioni delle versioni beta, o su documentazione o materiali di accompagnamento. Le funzioni e le API in versione beta sono soggette a modifiche senza preavviso. Qualsiasi utilizzo delle versioni beta è interamente a rischio del cliente.

Sono attualmente disponibili le seguenti opportunità di programma beta:

### Pipeline a livello web per AEM Managed Services {#web-tier-pipelines}

Cloud Manager ora supporta le pipeline dedicate a livello web per i programmi AMS, consentendo ai team di distribuire configurazioni a livello web e Dispatcher indipendentemente dalle distribuzioni full stack. Questo consente un’iterazione più rapida sulle modifiche a livello web, riducendo al contempo le esecuzioni di pipeline complete non necessarie. Quando viene configurata una pipeline a livello web, le pipeline full stack ignorano automaticamente la distribuzione a livello web per tale ambiente per evitare conflitti di distribuzione. La rimozione della pipeline a livello web ripristina automaticamente il comportamento di distribuzione predefinito.

Per partecipare al Beta, contatta il tuo Customer Success Engineer di Adobe per ulteriori informazioni.




## Correzioni di bug {#bug-fixes}

Non vi sono correzioni di bug significativi nella versione di luglio 2026 di Cloud Manager su AMS.

<!--
Known Issues {#known-issues}

* A 
-->
