---
title: Note sulla versione 2019.10.0
seo-title: Note sulla versione di AEM Cloud Manager per la versione 2019.10.0
description: Segui questa pagina per ottenere informazioni sulla versione 2019.10.0 di Cloud Manager.
seo-description: Segui questa pagina per ottenere informazioni su AEM Cloud Manager Release 2019.10.0.
translation-type: tm+mt
source-git-commit: 52c54568d8ab7b5091c25b3b65b4baa126bf61f5
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Note sulla versione 2019.10.0 {#release-notes-for}

La sezione seguente illustra le note generali sulla versione per la versione [!UICONTROL Cloud Manager] 2019.10.0 e aggiunge aggiornamenti ai passaggi di distribuzione e alla gestione della versione del progetto maven.
Seguite le sezioni riportate di seguito per ulteriori dettagli.

## Data di rilascio {#release-date}

La data di rilascio per la versione [!UICONTROL Cloud Manager] 2019.10.0 è il 10 ottobre 2019.

## Novità {#whats-new}

* Sono state rese più efficaci parti significative delle fasi di implementazione.
* Se appropriato, la versione del progetto Maven build ora incorporerà la versione del progetto in git.
* Al momento della creazione, sono disponibili nuove variabili di ambiente.
* Le tubazioni non di produzione possono essere eliminate dalla scheda sia nella pagina **Panoramica** che nell&#39;API.
* È disponibile un nuovo passaggio di approvazione opzionale immediatamente dopo il passaggio di distribuzione dell&#39;area di visualizzazione, ma prima del passaggio del test di protezione.
* Durante la configurazione di una pipeline CI/CD, è possibile saltare lo scollegamento e il collegamento delle istanze del dispatcher dal sistema di bilanciamento del carico per gli ambienti di sviluppo e di passaggio.
Per ulteriori informazioni, fare riferimento a **[Processo di distribuzione](deploying-code.md#deployment-process)**.
* L&#39;interfaccia CLI di Cloud Manager è stata incrementata per supportare l&#39;accesso ai log delle fasi di esecuzione.
* L&#39;API Cloud Manager ora supporta la modifica del ramo configurato di una pipeline.
* Le richieste eseguite durante il test delle prestazioni ora includono un token specifico ***CloudManagerTest*** nell&#39;agente utente.

## Correzioni di bug {#bug-fixes}

* Alcune delle schede della pagina **Overview** non erano allineate verticalmente correttamente.
* Alcune condizioni di errore non consentivano di contrassegnare correttamente le esecuzioni della pipeline e di impedire le successive esecuzioni.
