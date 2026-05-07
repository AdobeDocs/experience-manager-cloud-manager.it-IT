---
title: Note sulla versione per Cloud Manager 2026.5.0
description: Scopri la versione di Cloud Manager 2026.5.0 in Adobe Managed Services.
feature: Release Information
exl-id: cc1dc94b-129d-4de7-8e57-8fc5dcba7d9f
TQID: https://experienceleague.adobe.com/4zfTpSYuFwrJZ-oeL1SObT14v2Rd--Z1hKn5JllHAro
product_v2: id: c68cd75e-5bca-4bc3-a60e-9e183f816441id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
topic_v2: id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 0c2a9a946df6d5e1b0e4d5edb2715d8db98e9974
workflow-type: tm+mt
source-wordcount: 512
ht-degree: 15%

---


# Note sulla versione 2026.5.0 di Cloud Manager in Adobe Managed Services {#release-notes}

<!-- add "hold: true" to metadata above to be able to commit/merge to Main WITHOUT Publishig -->

<!-- RELEASE WIKI  https://wiki.corp.adobe.com/display/DMSArchitecture/Cloud+Manager+2025.04.0+Release -->

Scopri la versione di [!UICONTROL Cloud Manager] 2026.5.0 in Adobe Managed Services.

Consulta anche le [note sulla versione corrente di Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/it/docs/experience-manager-cloud-service/content/release-notes/home).

## Date di pubblicazione {#release-date}

La data di rilascio per [!UICONTROL Cloud Manager] 2026.5.0 è giovedì 7 maggio 2026.
<!-- There are no significant new features or bug fixes in the May Cloud Manager release. -->

La prossima versione pianificata è giovedì 4 giugno 2026.

<!-- SAVE FOR FUTURE POSSIBLE USE There are no significant new features or bug fixes in the May Cloud Manager release. -->

## Novità {#what-is-new}

Non vi sono nuove funzioni significative nella versione di maggio 2026 di Cloud Manager su AMS.

## Programmi Beta {#beta-program}

Partecipa al programma Beta privato di Cloud Manager per ottenere un accesso esclusivo alle funzioni in arrivo prima del rilascio generale.

>[!IMPORTANT]
>
>I rilasci di Beta possono contenere difetti e vengono forniti &quot;COSÌ COME SONO&quot; senza alcuna garanzia. Adobe non ha alcun obbligo di mantenere, correggere, aggiornare, modificare o altrimenti supportare (tramite i servizi di supporto Adobe o in altro modo) le versioni beta. Adobe consiglia ai clienti di prestare attenzione e di non affidarsi al corretto funzionamento o alle prestazioni delle versioni beta o a qualsiasi documentazione o materiale di accompagnamento. Le funzioni e le API in versione beta sono soggette a modifiche senza preavviso. Di conseguenza, qualsiasi utilizzo delle versioni beta è interamente a rischio del cliente.

Sono attualmente disponibili le seguenti opportunità di programma beta:

### Pipeline a livello web per AEM Managed Services {#web-tier-pipelines}

Cloud Manager ora supporta le pipeline dedicate a livello web per i programmi AMS, consentendo ai team di distribuire configurazioni a livello web e Dispatcher indipendentemente dalle distribuzioni full stack. Questo consente un’iterazione più rapida sulle modifiche a livello web, riducendo al contempo le esecuzioni di pipeline complete non necessarie. Quando viene configurata una pipeline a livello web, le pipeline full stack ignorano automaticamente la distribuzione a livello web per tale ambiente per evitare conflitti di distribuzione. La rimozione della pipeline a livello web ripristina automaticamente il comportamento di distribuzione predefinito.

Per partecipare al Beta, contatta il tuo Customer Success Engineer di Adobe per ulteriori informazioni.

### Build più veloci con il caching dei moduli {#quick-build-cm-pipelines}

Un nuovo modello di build compila solo i moduli modificati (anziché l’intero archivio) utilizzando il caching a livello di modulo per ridurre i tempi della build. Si applica alle pipeline di qualità del codice e full stack.

![Finestra di dialogo Modifica pipeline non di produzione che mostra le due opzioni Strategia di compilazione, Build completa e Build avanzata](/help/release-notes/assets/non-production-pipeline-edit.png)
*Finestra di dialogo Modifica pipeline non di produzione che mostra le due opzioni della strategia di compilazione, Build completa e Build avanzata.*

Nella finestra di dialogo **Aggiungi/Modifica pipeline**, nella scheda **Codice Source**, una nuova sezione **Strategia di compilazione** consente di scegliere una delle seguenti opzioni di compilazione:

* **Build completa**: crea tutti i moduli nell&#39;archivio a ogni esecuzione.
* **Smart Build**: crea solo i moduli che sono cambiati dall&#39;ultimo commit, riducendo così il tempo di compilazione complessivo.

Consulta [Aggiungere una pipeline non di produzione](/help/using/non-production-pipelines.md#add-non-production-pipeline) e [Informazioni sull&#39;utilizzo di Smart Build in una pipeline non di produzione](/help/using/non-production-pipelines.md#about-smart-build).

Puoi controllare quali pipeline utilizzano **Smart Build**. Durante la versione beta, questa opzione viene visualizzata solo per le pipeline **Qualità codice** e **Distribuzione codice full stack sviluppo**.

Per partecipare a Beta, invia un&#39;e-mail a [beta_quickbuild_cmpipelines@adobe.com](mailto:beta_quickbuild_cmpipelines@adobe.com) con il tuo ID organizzazione Adobe e l&#39;ID programma.

<!-- You can deactivate incremental builds at the pipeline level by setting the property `CM_BUILD_DISABLE_MODULE_CACHING` to `true` (effective during the `BUILD` step). For how to add pipeline variables, see [Pipeline variables](/help/getting-started/build-environment.md#pipeline-variables). -->

## Correzioni di bug {#bug-fixes}

Non vi sono correzioni di bug significativi nella versione di maggio 2026 di Cloud Manager su AMS.

<!--
Known Issues {#known-issues}

* A 
-->
